---
title: Bellek Eşlemeli Dosyalar
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- memory-mapped files
- inter-process communication
ms.assetid: a483d1b5-64aa-45b6-86ef-11b859f7f02e
ms.openlocfilehash: 004da94bc7345bdc294562f0e1bedf6f1735adec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159721"
---
# <a name="memory-mapped-files"></a><span data-ttu-id="165b9-102">Bellek Eşlemeli Dosyalar</span><span class="sxs-lookup"><span data-stu-id="165b9-102">Memory-Mapped Files</span></span>
<span data-ttu-id="165b9-103">Bellek eşlenen bir dosya, sanal bellekteki bir dosyanın içeriğini içerir.</span><span class="sxs-lookup"><span data-stu-id="165b9-103">A memory-mapped file contains the contents of a file in virtual memory.</span></span> <span data-ttu-id="165b9-104">Bir dosya ve bellek alanı arasındaki bu eşleme, birden çok işlem de dahil olmak üzere bir uygulamanın, doğrudan belleğe okuyarak ve yazarak dosyayı değiştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="165b9-104">This mapping between a file and memory space enables an application, including multiple processes, to modify the file by reading and writing directly to the memory.</span></span> <span data-ttu-id="165b9-105">.NET Framework 4'ten başlayarak, bellek eşlenen dosyalara erişmek için yönetilen kodu, yerel Windows işlevlerinin [Bellek Eşlenen Dosyaları Yönetme'de](https://docs.microsoft.com/previous-versions/ms810613(v=msdn.10))açıklandığı gibi bellek eşlenen dosyalara eriştiği şekilde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="165b9-105">Starting with the .NET Framework 4, you can use managed code to access memory-mapped files in the same way that native Windows functions access memory-mapped files, as described in [Managing Memory-Mapped Files](https://docs.microsoft.com/previous-versions/ms810613(v=msdn.10)).</span></span>  
  
 <span data-ttu-id="165b9-106">Bellek eşlenen iki tür dosya vardır:</span><span class="sxs-lookup"><span data-stu-id="165b9-106">There are two types of memory-mapped files:</span></span>  
  
- <span data-ttu-id="165b9-107">Kalıcı bellek eşlenen dosyalar</span><span class="sxs-lookup"><span data-stu-id="165b9-107">Persisted memory-mapped files</span></span>  
  
     <span data-ttu-id="165b9-108">Kalıcı dosyalar, diskteki bir kaynak dosyayla ilişkili bellek eşlenen dosyalardır.</span><span class="sxs-lookup"><span data-stu-id="165b9-108">Persisted files are memory-mapped files that are associated with a source file on a disk.</span></span> <span data-ttu-id="165b9-109">Son işlem dosyayla çalışmayı tamamladığında, veriler diskteki kaynak dosyaya kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="165b9-109">When the last process has finished working with the file, the data is saved to the source file on the disk.</span></span> <span data-ttu-id="165b9-110">Bu bellek eşlenen dosyalar son derece büyük kaynak dosyaları ile çalışmak için uygundur.</span><span class="sxs-lookup"><span data-stu-id="165b9-110">These memory-mapped files are suitable for working with extremely large source files.</span></span>  
  
- <span data-ttu-id="165b9-111">Kalıcı olmayan bellek eşlenen dosyalar</span><span class="sxs-lookup"><span data-stu-id="165b9-111">Non-persisted memory-mapped files</span></span>  
  
     <span data-ttu-id="165b9-112">Kalıcı olmayan dosyalar, diskteki bir dosyayla ilişkilendirilmeyen bellek eşlenen dosyalardır.</span><span class="sxs-lookup"><span data-stu-id="165b9-112">Non-persisted files are memory-mapped files that are not associated with a file on a disk.</span></span> <span data-ttu-id="165b9-113">Son işlem dosyayla çalışmayı tamamladığında, veriler kaybolur ve dosya çöp toplama tarafından geri alınır.</span><span class="sxs-lookup"><span data-stu-id="165b9-113">When the last process has finished working with the file, the data is lost and the file is reclaimed by garbage collection.</span></span> <span data-ttu-id="165b9-114">Bu dosyalar, süreçler arası iletişim (IPC) için paylaşılan bellek oluşturmak için uygundur.</span><span class="sxs-lookup"><span data-stu-id="165b9-114">These files are suitable for creating shared memory for inter-process communications (IPC).</span></span>  
  
## <a name="processes-views-and-managing-memory"></a><span data-ttu-id="165b9-115">Süreçler, Görünümler ve Bellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="165b9-115">Processes, Views, and Managing Memory</span></span>  
 <span data-ttu-id="165b9-116">Bellek eşlenen dosyalar birden çok işlem arasında paylaşılabilir.</span><span class="sxs-lookup"><span data-stu-id="165b9-116">Memory-mapped files can be shared across multiple processes.</span></span> <span data-ttu-id="165b9-117">İşlemler, dosyayı oluşturan işlem tarafından atanan ortak bir ad kullanarak aynı bellek eşlenen dosyayla eşlenebilir.</span><span class="sxs-lookup"><span data-stu-id="165b9-117">Processes can map to the same memory-mapped file by using a common name that is assigned by the process that created the file.</span></span>  
  
 <span data-ttu-id="165b9-118">Bellek eşlenen bir dosyayla çalışmak için, bellek eşlenen dosyanın tamamının veya bir bölümünün görünümünü oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="165b9-118">To work with a memory-mapped file, you must create a view of the entire memory-mapped file or a part of it.</span></span> <span data-ttu-id="165b9-119">Ayrıca, bellek eşlenen dosyanın aynı bölümüne birden çok görünüm oluşturarak eşzamanlı bellek oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="165b9-119">You can also create multiple views to the same part of the memory-mapped file, thereby creating concurrent memory.</span></span> <span data-ttu-id="165b9-120">İki görünümün eşzamanlı kalması için, aynı bellek eşlenen dosyadan oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="165b9-120">For two views to remain concurrent, they have to be created from the same memory-mapped file.</span></span>  
  
 <span data-ttu-id="165b9-121">Dosya, uygulamanın bellek eşlemi için kullanılabilir mantıksal bellek alanının boyutundan büyükse (32 bit bilgisayarda 2 GB) birden çok görünüm de gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="165b9-121">Multiple views may also be necessary if the file is greater than the size of the application’s logical memory space available for memory mapping (2 GB on a 32-bit computer).</span></span>  
  
 <span data-ttu-id="165b9-122">İki tür görünüm vardır: akış erişim görünümü ve rasgele erişim görünümü.</span><span class="sxs-lookup"><span data-stu-id="165b9-122">There are two types of views: stream access view and random access view.</span></span> <span data-ttu-id="165b9-123">Bir dosyaya sıralı erişim için akış erişim görünümlerini kullanın; bu, kalıcı olmayan dosyalar ve IPC için önerilir.</span><span class="sxs-lookup"><span data-stu-id="165b9-123">Use stream access views for sequential access to a file; this is recommended for non-persisted files and IPC.</span></span> <span data-ttu-id="165b9-124">Kalıcı dosyalarla çalışmak için rasgele erişim görünümleri tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="165b9-124">Random access views are preferred for working with persisted files.</span></span>  
  
 <span data-ttu-id="165b9-125">Bellek eşlenen dosyalara işletim sisteminin bellek yöneticisi aracılığıyla erişilir, böylece dosya otomatik olarak birkaç sayfaya bölünür ve gerektiğinde erişilir.</span><span class="sxs-lookup"><span data-stu-id="165b9-125">Memory-mapped files are accessed through the operating system’s memory manager, so the file is automatically partitioned into a number of pages and accessed as needed.</span></span> <span data-ttu-id="165b9-126">Bellek yönetimini kendiniz halletmek zorunda değilsin.</span><span class="sxs-lookup"><span data-stu-id="165b9-126">You do not have to handle the memory management yourself.</span></span>  
  
 <span data-ttu-id="165b9-127">Aşağıdaki resimde, birden çok işlemde aynı bellek eşlenen dosyada birden çok ve çakışan görünümnasıl olabilir.</span><span class="sxs-lookup"><span data-stu-id="165b9-127">The following illustration shows how multiple processes can have multiple and overlapping views to the same memory-mapped file at the same time.</span></span>

 <span data-ttu-id="165b9-128">Aşağıdaki resim, bellek eşlenen bir dosyaya birden çok ve üst üste gelen görünümleri gösterir:</span><span class="sxs-lookup"><span data-stu-id="165b9-128">The following image shows multiple and overlapped views to a memory-mapped file:</span></span>  
  
 ![Eşlenen bir&#45;bellekte görünümleri gösteren ekran görüntüsü.](./media/memory-mapped-files/memory-map-persist-file.png)  
  
## <a name="programming-with-memory-mapped-files"></a><span data-ttu-id="165b9-130">Bellek Eşlenen Dosyalarla Programlama</span><span class="sxs-lookup"><span data-stu-id="165b9-130">Programming with Memory-Mapped Files</span></span>  
 <span data-ttu-id="165b9-131">Aşağıdaki tablo, bellek eşlenen dosya nesnelerini ve üyelerini kullanmak için bir kılavuz sağlar.</span><span class="sxs-lookup"><span data-stu-id="165b9-131">The following table provides a guide for using memory-mapped file objects and their members.</span></span>  
  
|<span data-ttu-id="165b9-132">Görev</span><span class="sxs-lookup"><span data-stu-id="165b9-132">Task</span></span>|<span data-ttu-id="165b9-133">Kullanılacak yöntemler veya özellikler</span><span class="sxs-lookup"><span data-stu-id="165b9-133">Methods or properties to use</span></span>|  
|----------|----------------------------------|  
|<span data-ttu-id="165b9-134">Diskteki <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> bir dosyadan kalıcı bellek eşlenen dosyayı temsil eden bir nesne elde etmek için.</span><span class="sxs-lookup"><span data-stu-id="165b9-134">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object that represents a persisted memory-mapped file from a file on disk.</span></span>|<span data-ttu-id="165b9-135"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>Yöntem.</span><span class="sxs-lookup"><span data-stu-id="165b9-135"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="165b9-136">Kalıcı olmayan <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> bellek eşlenen dosyayı temsil eden bir nesne elde etmek için (diskteki bir dosyayla ilişkili değildir).</span><span class="sxs-lookup"><span data-stu-id="165b9-136">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object that represents a non-persisted memory-mapped file (not associated with a file on disk).</span></span>|<span data-ttu-id="165b9-137"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>Yöntem.</span><span class="sxs-lookup"><span data-stu-id="165b9-137"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType> method.</span></span><br /><br /> <span data-ttu-id="165b9-138">- veya -</span><span class="sxs-lookup"><span data-stu-id="165b9-138">- or -</span></span><br /><br /> <span data-ttu-id="165b9-139"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>Yöntem.</span><span class="sxs-lookup"><span data-stu-id="165b9-139"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="165b9-140">Varolan <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> bellek eşlenen bir dosyanın nesnesini elde etmek için (kalıcı veya kalıcı olmayan).</span><span class="sxs-lookup"><span data-stu-id="165b9-140">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object of an existing memory-mapped file (either persisted or non-persisted).</span></span>|<span data-ttu-id="165b9-141"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType>Yöntem.</span><span class="sxs-lookup"><span data-stu-id="165b9-141"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="165b9-142">Bellek eşlenen dosyaya sırayla erişilen bir görünüm için bir <xref:System.IO.UnmanagedMemoryStream> nesne elde etmek için.</span><span class="sxs-lookup"><span data-stu-id="165b9-142">To obtain a <xref:System.IO.UnmanagedMemoryStream> object for a sequentially accessed view to the memory-mapped file.</span></span>|<span data-ttu-id="165b9-143"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType>Yöntem.</span><span class="sxs-lookup"><span data-stu-id="165b9-143"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="165b9-144">Bellek eşlenen fie rasgele bir erişim görünümü için bir <xref:System.IO.UnmanagedMemoryAccessor> nesne elde etmek için.</span><span class="sxs-lookup"><span data-stu-id="165b9-144">To obtain a <xref:System.IO.UnmanagedMemoryAccessor> object for a random access view to a memory-mapped fie.</span></span>|<span data-ttu-id="165b9-145"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType>Yöntem.</span><span class="sxs-lookup"><span data-stu-id="165b9-145"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="165b9-146">Yönetilmeyen <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> kodla kullanılacak bir nesne elde etmek için.</span><span class="sxs-lookup"><span data-stu-id="165b9-146">To obtain a <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> object to use with unmanaged code.</span></span>|<span data-ttu-id="165b9-147"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType>Özellik.</span><span class="sxs-lookup"><span data-stu-id="165b9-147"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType> property.</span></span><br /><br /> <span data-ttu-id="165b9-148">- veya -</span><span class="sxs-lookup"><span data-stu-id="165b9-148">- or -</span></span><br /><br /> <span data-ttu-id="165b9-149"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType>Özellik.</span><span class="sxs-lookup"><span data-stu-id="165b9-149"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> property.</span></span><br /><br /> <span data-ttu-id="165b9-150">- veya -</span><span class="sxs-lookup"><span data-stu-id="165b9-150">- or -</span></span><br /><br /> <span data-ttu-id="165b9-151"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType>Özellik.</span><span class="sxs-lookup"><span data-stu-id="165b9-151"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> property.</span></span>|  
|<span data-ttu-id="165b9-152">Bir görünüm oluşturulana kadar bellek ayırmayı geciktirmek için (yalnızca kalıcı olmayan dosyalar).</span><span class="sxs-lookup"><span data-stu-id="165b9-152">To delay allocating memory until a view is created (non-persisted files only).</span></span><br /><br /> <span data-ttu-id="165b9-153">(Geçerli sistem sayfa boyutunu belirlemek <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> için özelliği kullanın.)</span><span class="sxs-lookup"><span data-stu-id="165b9-153">(To determine the current system page size, use the <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> property.)</span></span>|<span data-ttu-id="165b9-154"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A><xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> değeri ile yöntem.</span><span class="sxs-lookup"><span data-stu-id="165b9-154"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> method with the <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> value.</span></span><br /><br /> <span data-ttu-id="165b9-155">- veya -</span><span class="sxs-lookup"><span data-stu-id="165b9-155">- or -</span></span><br /><br /> <span data-ttu-id="165b9-156"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A>parametre olarak <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> numaralandırma yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="165b9-156"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> methods that have a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> enumeration as a parameter.</span></span>|  
  
### <a name="security"></a><span data-ttu-id="165b9-157">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="165b9-157">Security</span></span>  
 <span data-ttu-id="165b9-158">Bir parametre olarak numaralandırma almak <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> aşağıdaki yöntemleri kullanarak, bellek eşlenen bir dosya oluştururken erişim haklarını uygulayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="165b9-158">You can apply access rights when you create a memory-mapped file, by using the following methods that take a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> enumeration as a parameter:</span></span>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="165b9-159">Parametre <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> olarak alan yöntemleri kullanarak varolan bellek eşlenen bir dosyayı açmak için erişim haklarını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="165b9-159">You can specify access rights for opening an existing memory-mapped file by using the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> methods that take an <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> as a parameter.</span></span>  
  
 <span data-ttu-id="165b9-160">Ayrıca, önceden tanımlanmış <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> erişim kuralları içeren bir nesne ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="165b9-160">In addition, you can include a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> object that contains predefined access rules.</span></span>  
  
 <span data-ttu-id="165b9-161">Bellek eşlenen bir dosyaya yeni veya değiştirilmiş erişim <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> kuralları uygulamak için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="165b9-161">To apply new or changed access rules to a memory-mapped file, use the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> method.</span></span> <span data-ttu-id="165b9-162">Varolan bir dosyadan erişim veya denetim <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> kuralları almak için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="165b9-162">To retrieve access or audit rules from an existing file, use the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="165b9-163">Örnekler</span><span class="sxs-lookup"><span data-stu-id="165b9-163">Examples</span></span>  
  
### <a name="persisted-memory-mapped-files"></a><span data-ttu-id="165b9-164">Kalıcı Bellek Eşlenen Dosyalar</span><span class="sxs-lookup"><span data-stu-id="165b9-164">Persisted Memory-Mapped Files</span></span>  
 <span data-ttu-id="165b9-165">Yöntemler, <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> diskteki varolan bir dosyadan bellek eşlenen bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="165b9-165">The <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> methods create a memory-mapped file from an existing file on disk.</span></span>  
  
 <span data-ttu-id="165b9-166">Aşağıdaki örnek, son derece büyük bir dosyanın bir bölümünün bellek eşlenmiş görünümünü oluşturur ve bir bölümünü manipüle eder.</span><span class="sxs-lookup"><span data-stu-id="165b9-166">The following example creates a memory-mapped view of a part of an extremely large file and manipulates a portion of it.</span></span>  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/vb/program.vb#1)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

 <span data-ttu-id="165b9-167">Aşağıdaki örnek, başka bir işlem için aynı bellek eşlenen dosyayı açar.</span><span class="sxs-lookup"><span data-stu-id="165b9-167">The following example opens the same memory-mapped file for another process.</span></span>  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/vb/program.vb#1)]  
  
### <a name="non-persisted-memory-mapped-files"></a><span data-ttu-id="165b9-168">Kalıcı Olmayan Bellek Eşlenen Dosyalar</span><span class="sxs-lookup"><span data-stu-id="165b9-168">Non-Persisted Memory-Mapped Files</span></span>  
 <span data-ttu-id="165b9-169">Ve <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> yöntemler, diskteki varolan bir dosyaya eşlenmemiş bellek eşlenmiş bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="165b9-169">The <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> and <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> methods create a memory-mapped file that is not mapped to an existing file on disk.</span></span>  
  
 <span data-ttu-id="165b9-170">Aşağıdaki örnek, bellek eşlenen bir dosyaya Boolean değerlerini yazan üç ayrı işlemden (konsol uygulamaları) oluşur.</span><span class="sxs-lookup"><span data-stu-id="165b9-170">The following example consists of three separate processes (console applications) that write Boolean values to a memory-mapped file.</span></span> <span data-ttu-id="165b9-171">Aşağıdaki eylem sırası oluşur:</span><span class="sxs-lookup"><span data-stu-id="165b9-171">The following sequence of actions occur:</span></span>  
  
1. <span data-ttu-id="165b9-172">`Process A`bellek eşlenen dosyayı oluşturur ve bir değer yazar.</span><span class="sxs-lookup"><span data-stu-id="165b9-172">`Process A` creates the memory-mapped file and writes a value to it.</span></span>  
  
2. <span data-ttu-id="165b9-173">`Process B`bellek eşlenen dosyayı açar ve bir değer yazar.</span><span class="sxs-lookup"><span data-stu-id="165b9-173">`Process B` opens the memory-mapped file and writes a value to it.</span></span>  
  
3. <span data-ttu-id="165b9-174">`Process C`bellek eşlenen dosyayı açar ve bir değer yazar.</span><span class="sxs-lookup"><span data-stu-id="165b9-174">`Process C` opens the memory-mapped file and writes a value to it.</span></span>  
  
4. <span data-ttu-id="165b9-175">`Process A`bellek eşlenen dosyadaki değerleri okur ve görüntüler.</span><span class="sxs-lookup"><span data-stu-id="165b9-175">`Process A` reads and displays the values from the memory-mapped file.</span></span>  
  
5. <span data-ttu-id="165b9-176">Bellek `Process A` eşlenen dosya ile tamamlandıktan sonra, dosya hemen çöp toplama tarafından geri alınır.</span><span class="sxs-lookup"><span data-stu-id="165b9-176">After `Process A` is finished with the memory-mapped file, the file is immediately reclaimed by garbage collection.</span></span>  
  
 <span data-ttu-id="165b9-177">Bu örneği çalıştırmak için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="165b9-177">To run this example, do the following:</span></span>  
  
1. <span data-ttu-id="165b9-178">Uygulamaları derleyin ve üç Komut İstemi penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="165b9-178">Compile the applications and open three Command Prompt windows.</span></span>  
  
2. <span data-ttu-id="165b9-179">İlk Komut İstemi penceresinde `Process A`çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="165b9-179">In the first Command Prompt window, run `Process A`.</span></span>  
  
3. <span data-ttu-id="165b9-180">İkinci Komut İstemi penceresinde `Process B`çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="165b9-180">In the second Command Prompt window, run `Process B`.</span></span>  
  
4. <span data-ttu-id="165b9-181">Geri `Process A` dön ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="165b9-181">Return to `Process A` and press ENTER.</span></span>  
  
5. <span data-ttu-id="165b9-182">Üçüncü Komut İstemi penceresinde, çalıştırın. `Process C`</span><span class="sxs-lookup"><span data-stu-id="165b9-182">In the third Command Prompt window, run `Process C`.</span></span>  
  
6. <span data-ttu-id="165b9-183">Geri `Process A` dön ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="165b9-183">Return to `Process A` and press ENTER.</span></span>  
  
 <span data-ttu-id="165b9-184">Çıktıaşağıdaki `Process A` gibidir:</span><span class="sxs-lookup"><span data-stu-id="165b9-184">The output of `Process A` is as follows:</span></span>  
  
```console  
Start Process B and press ENTER to continue.  
Start Process C and press ENTER to continue.  
Process A says: True  
Process B says: False  
Process C says: True  
```  
  
 <span data-ttu-id="165b9-185">**Süreç A**</span><span class="sxs-lookup"><span data-stu-id="165b9-185">**Process A**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/vb/program.vb#1)]  
  
 <span data-ttu-id="165b9-186">**Süreç B**</span><span class="sxs-lookup"><span data-stu-id="165b9-186">**Process B**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/vb/program.vb#1)]  
  
 <span data-ttu-id="165b9-187">**İşlem C**</span><span class="sxs-lookup"><span data-stu-id="165b9-187">**Process C**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="165b9-188">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="165b9-188">See also</span></span>

- [<span data-ttu-id="165b9-189">Dosya ve Akış G/Ç'si</span><span class="sxs-lookup"><span data-stu-id="165b9-189">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
