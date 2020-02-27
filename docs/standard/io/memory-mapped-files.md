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
ms.openlocfilehash: 7d80099fcfcba58cd863004ba7faf0bafa3abd09
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628026"
---
# <a name="memory-mapped-files"></a><span data-ttu-id="aaef2-102">Bellek Eşlemeli Dosyalar</span><span class="sxs-lookup"><span data-stu-id="aaef2-102">Memory-Mapped Files</span></span>
<span data-ttu-id="aaef2-103">Bellek eşlemeli bir dosya, sanal bellekteki bir dosyanın içeriğini içerir.</span><span class="sxs-lookup"><span data-stu-id="aaef2-103">A memory-mapped file contains the contents of a file in virtual memory.</span></span> <span data-ttu-id="aaef2-104">Bir dosya ve bellek alanı arasındaki bu eşleme, birden çok işlem dahil olmak üzere bir uygulamanın, dosyayı okuyup doğrudan belleğe yazarak değiştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="aaef2-104">This mapping between a file and memory space enables an application, including multiple processes, to modify the file by reading and writing directly to the memory.</span></span> <span data-ttu-id="aaef2-105">.NET Framework 4 ' te başlayarak, yerel Windows işlevlerinin bellek eşlemeli dosyaları [yönetme](https://docs.microsoft.com/previous-versions/ms810613(v=msdn.10))bölümünde açıklandığı gibi, aynı şekilde bellek eşlemeli dosyalara erişmek için yönetilen kodu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aaef2-105">Starting with the .NET Framework 4, you can use managed code to access memory-mapped files in the same way that native Windows functions access memory-mapped files, as described in [Managing Memory-Mapped Files](https://docs.microsoft.com/previous-versions/ms810613(v=msdn.10)).</span></span>  
  
 <span data-ttu-id="aaef2-106">İki tür bellekle eşlenmiş dosya vardır:</span><span class="sxs-lookup"><span data-stu-id="aaef2-106">There are two types of memory-mapped files:</span></span>  
  
- <span data-ttu-id="aaef2-107">Kalıcı bellekle eşlenen dosyalar</span><span class="sxs-lookup"><span data-stu-id="aaef2-107">Persisted memory-mapped files</span></span>  
  
     <span data-ttu-id="aaef2-108">Kalıcı dosyalar, bir diskteki kaynak dosyayla ilişkili bellekle eşleştirilmiş dosyalardır.</span><span class="sxs-lookup"><span data-stu-id="aaef2-108">Persisted files are memory-mapped files that are associated with a source file on a disk.</span></span> <span data-ttu-id="aaef2-109">Son işlem dosyayla çalışmayı bitirdiğinde, veriler diskteki kaynak dosyasına kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="aaef2-109">When the last process has finished working with the file, the data is saved to the source file on the disk.</span></span> <span data-ttu-id="aaef2-110">Bellek eşlemeli bu dosyalar, son derece büyük kaynak dosyalarıyla çalışmak için uygundur.</span><span class="sxs-lookup"><span data-stu-id="aaef2-110">These memory-mapped files are suitable for working with extremely large source files.</span></span>  
  
- <span data-ttu-id="aaef2-111">Kalıcı olmayan bellekle eşlenen dosyalar</span><span class="sxs-lookup"><span data-stu-id="aaef2-111">Non-persisted memory-mapped files</span></span>  
  
     <span data-ttu-id="aaef2-112">Kalıcı olmayan dosyalar, bir diskte bulunan bir dosya ile ilişkilendirilmemiş bellekle eşleştirilmiş dosyalardır.</span><span class="sxs-lookup"><span data-stu-id="aaef2-112">Non-persisted files are memory-mapped files that are not associated with a file on a disk.</span></span> <span data-ttu-id="aaef2-113">Son işlem dosyayla çalışmayı bitirdiğinde, veriler kaybolur ve dosya çöp toplama tarafından geri kazanılır.</span><span class="sxs-lookup"><span data-stu-id="aaef2-113">When the last process has finished working with the file, the data is lost and the file is reclaimed by garbage collection.</span></span> <span data-ttu-id="aaef2-114">Bu dosyalar, işlemler arası iletişimler (IPC) için paylaşılan bellek oluşturmak üzere uygundur.</span><span class="sxs-lookup"><span data-stu-id="aaef2-114">These files are suitable for creating shared memory for inter-process communications (IPC).</span></span>  
  
## <a name="processes-views-and-managing-memory"></a><span data-ttu-id="aaef2-115">Belleği işleme, görüntüleme ve yönetme</span><span class="sxs-lookup"><span data-stu-id="aaef2-115">Processes, Views, and Managing Memory</span></span>  
 <span data-ttu-id="aaef2-116">Bellek eşlemeli dosyalar, birden çok işlem arasında paylaşılabilir.</span><span class="sxs-lookup"><span data-stu-id="aaef2-116">Memory-mapped files can be shared across multiple processes.</span></span> <span data-ttu-id="aaef2-117">İşlemler, dosyayı oluşturan işlem tarafından atanan ortak bir ad kullanarak aynı bellek eşlemeli dosyayla eşlenir.</span><span class="sxs-lookup"><span data-stu-id="aaef2-117">Processes can map to the same memory-mapped file by using a common name that is assigned by the process that created the file.</span></span>  
  
 <span data-ttu-id="aaef2-118">Bellek eşlemeli bir dosyayla çalışmak için, tüm bellek eşlemeli dosyanın veya bunun bir kısmının görünümünü oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="aaef2-118">To work with a memory-mapped file, you must create a view of the entire memory-mapped file or a part of it.</span></span> <span data-ttu-id="aaef2-119">Ayrıca, bellek eşlemeli dosyanın aynı kısmına birden fazla görünüm de oluşturabilirsiniz, böylece eşzamanlı bellek oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="aaef2-119">You can also create multiple views to the same part of the memory-mapped file, thereby creating concurrent memory.</span></span> <span data-ttu-id="aaef2-120">İki görünümün eşzamanlı kalması için aynı bellek eşlemeli dosyadan oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="aaef2-120">For two views to remain concurrent, they have to be created from the same memory-mapped file.</span></span>  
  
 <span data-ttu-id="aaef2-121">Dosya, bellek eşleme için kullanılabilir (32 bitlik bir bilgisayarda 2 GB) uygulamanın mantıksal bellek alanının boyutundan fazlaysa, birden çok görünüm de gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="aaef2-121">Multiple views may also be necessary if the file is greater than the size of the application’s logical memory space available for memory mapping (2 GB on a 32-bit computer).</span></span>  
  
 <span data-ttu-id="aaef2-122">İki tür görünüm vardır: akış erişim görünümü ve rastgele erişim görünümü.</span><span class="sxs-lookup"><span data-stu-id="aaef2-122">There are two types of views: stream access view and random access view.</span></span> <span data-ttu-id="aaef2-123">Bir dosyaya sıralı erişim için akış erişim görünümlerini kullanın; kalıcı olmayan dosyalar ve IPC için bu önerilir.</span><span class="sxs-lookup"><span data-stu-id="aaef2-123">Use stream access views for sequential access to a file; this is recommended for non-persisted files and IPC.</span></span> <span data-ttu-id="aaef2-124">Kalıcı dosyalarla çalışmaya yönelik rastgele erişim görünümleri tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="aaef2-124">Random access views are preferred for working with persisted files.</span></span>  
  
 <span data-ttu-id="aaef2-125">Bellek eşlemeli dosyalara işletim sisteminin bellek Yöneticisi üzerinden erişilir, bu nedenle dosya otomatik olarak bir dizi sayfaya bölümlenir ve gerektiğinde erişilir.</span><span class="sxs-lookup"><span data-stu-id="aaef2-125">Memory-mapped files are accessed through the operating system’s memory manager, so the file is automatically partitioned into a number of pages and accessed as needed.</span></span> <span data-ttu-id="aaef2-126">Bellek yönetimini kendiniz işlemek zorunda değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="aaef2-126">You do not have to handle the memory management yourself.</span></span>  
  
 <span data-ttu-id="aaef2-127">Aşağıdaki çizimde, birden çok işlemin aynı anda aynı bellek eşlemeli dosya için birden çok ve çakışan görünümler bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="aaef2-127">The following illustration shows how multiple processes can have multiple and overlapping views to the same memory-mapped file at the same time.</span></span>

 <span data-ttu-id="aaef2-128">Aşağıdaki görüntüde, bellek eşlemeli bir dosya için birden çok ve çakışan görünümler gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="aaef2-128">The following image shows multiple and overlapped views to a memory-mapped file:</span></span>  
  
 ![Bellek&#45;eşlemeli bir dosyanın görünümlerini gösteren ekran görüntüsü.](./media/memory-mapped-files/memory-map-persist-file.png)  
  
## <a name="programming-with-memory-mapped-files"></a><span data-ttu-id="aaef2-130">Bellek eşlemeli dosyalarla programlama</span><span class="sxs-lookup"><span data-stu-id="aaef2-130">Programming with Memory-Mapped Files</span></span>  
 <span data-ttu-id="aaef2-131">Aşağıdaki tabloda, bellek eşlemeli dosya nesnelerini ve bunların üyelerini kullanmaya yönelik bir kılavuz verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="aaef2-131">The following table provides a guide for using memory-mapped file objects and their members.</span></span>  
  
|<span data-ttu-id="aaef2-132">Görev</span><span class="sxs-lookup"><span data-stu-id="aaef2-132">Task</span></span>|<span data-ttu-id="aaef2-133">Kullanılacak yöntemler veya Özellikler</span><span class="sxs-lookup"><span data-stu-id="aaef2-133">Methods or properties to use</span></span>|  
|----------|----------------------------------|  
|<span data-ttu-id="aaef2-134">Diskteki bir dosyanın kalıcı bellek eşlemeli bir dosyasını temsil eden bir <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> nesnesi elde etmek için.</span><span class="sxs-lookup"><span data-stu-id="aaef2-134">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object that represents a persisted memory-mapped file from a file on disk.</span></span>|<span data-ttu-id="aaef2-135"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="aaef2-135"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="aaef2-136">Kalıcı olmayan bir bellek eşlemeli dosyayı temsil eden bir <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> nesnesi elde etmek için (diskteki bir dosya ile ilişkilendirilmemiş).</span><span class="sxs-lookup"><span data-stu-id="aaef2-136">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object that represents a non-persisted memory-mapped file (not associated with a file on disk).</span></span>|<span data-ttu-id="aaef2-137"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="aaef2-137"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType> method.</span></span><br /><br /> <span data-ttu-id="aaef2-138">veya</span><span class="sxs-lookup"><span data-stu-id="aaef2-138">- or -</span></span><br /><br /> <span data-ttu-id="aaef2-139"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="aaef2-139"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="aaef2-140">Mevcut bir bellek eşlemeli dosyanın <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> nesnesini almak için (kalıcı veya kalıcı olmayan).</span><span class="sxs-lookup"><span data-stu-id="aaef2-140">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object of an existing memory-mapped file (either persisted or non-persisted).</span></span>|<span data-ttu-id="aaef2-141"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="aaef2-141"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="aaef2-142">Sıralı olarak erişilen bir görünüm için bellek eşlemeli dosyaya <xref:System.IO.UnmanagedMemoryStream> nesne almak için.</span><span class="sxs-lookup"><span data-stu-id="aaef2-142">To obtain a <xref:System.IO.UnmanagedMemoryStream> object for a sequentially accessed view to the memory-mapped file.</span></span>|<span data-ttu-id="aaef2-143"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="aaef2-143"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="aaef2-144">Bellek eşlemeli bir dosyasına rastgele erişim görünümü için <xref:System.IO.UnmanagedMemoryAccessor> nesnesi elde etmek için.</span><span class="sxs-lookup"><span data-stu-id="aaef2-144">To obtain a <xref:System.IO.UnmanagedMemoryAccessor> object for a random access view to a memory-mapped fie.</span></span>|<span data-ttu-id="aaef2-145"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="aaef2-145"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="aaef2-146">Yönetilmeyen kod ile kullanmak üzere bir <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> nesnesi elde etmek için.</span><span class="sxs-lookup"><span data-stu-id="aaef2-146">To obtain a <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> object to use with unmanaged code.</span></span>|<span data-ttu-id="aaef2-147"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="aaef2-147"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType> property.</span></span><br /><br /> <span data-ttu-id="aaef2-148">veya</span><span class="sxs-lookup"><span data-stu-id="aaef2-148">- or -</span></span><br /><br /> <span data-ttu-id="aaef2-149"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="aaef2-149"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> property.</span></span><br /><br /> <span data-ttu-id="aaef2-150">veya</span><span class="sxs-lookup"><span data-stu-id="aaef2-150">- or -</span></span><br /><br /> <span data-ttu-id="aaef2-151"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="aaef2-151"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> property.</span></span>|  
|<span data-ttu-id="aaef2-152">Bir görünüm oluşturuluncaya kadar bellek ayırmayı geciktirmek için (yalnızca kalıcı olmayan dosyalar).</span><span class="sxs-lookup"><span data-stu-id="aaef2-152">To delay allocating memory until a view is created (non-persisted files only).</span></span><br /><br /> <span data-ttu-id="aaef2-153">(Geçerli sistem sayfa boyutunu anlamak için <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> özelliğini kullanın.)</span><span class="sxs-lookup"><span data-stu-id="aaef2-153">(To determine the current system page size, use the <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> property.)</span></span>|<span data-ttu-id="aaef2-154"><xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> değerine sahip <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="aaef2-154"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> method with the <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> value.</span></span><br /><br /> <span data-ttu-id="aaef2-155">veya</span><span class="sxs-lookup"><span data-stu-id="aaef2-155">- or -</span></span><br /><br /> <span data-ttu-id="aaef2-156">parametre olarak <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> numaralandırması olan Yöntemler <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A>.</span><span class="sxs-lookup"><span data-stu-id="aaef2-156"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> methods that have a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> enumeration as a parameter.</span></span>|  
  
### <a name="security"></a><span data-ttu-id="aaef2-157">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="aaef2-157">Security</span></span>  
 <span data-ttu-id="aaef2-158">Bir parametre olarak <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> numaralandırması alan aşağıdaki yöntemleri kullanarak, bellek eşlemeli bir dosya oluştururken erişim hakları uygulayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="aaef2-158">You can apply access rights when you create a memory-mapped file, by using the following methods that take a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> enumeration as a parameter:</span></span>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="aaef2-159">Bir <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> parametresi olarak alan <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> yöntemlerini kullanarak, var olan bir bellek eşlemeli dosyayı açmak için erişim hakları belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aaef2-159">You can specify access rights for opening an existing memory-mapped file by using the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> methods that take an <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> as a parameter.</span></span>  
  
 <span data-ttu-id="aaef2-160">Ayrıca, önceden tanımlanmış erişim kuralları içeren bir <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> nesnesi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aaef2-160">In addition, you can include a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> object that contains predefined access rules.</span></span>  
  
 <span data-ttu-id="aaef2-161">Bellek eşlemeli bir dosyaya yeni veya değiştirilmiş erişim kuralları uygulamak için <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="aaef2-161">To apply new or changed access rules to a memory-mapped file, use the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> method.</span></span> <span data-ttu-id="aaef2-162">Var olan bir dosyadan erişim veya denetim kuralları almak için <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="aaef2-162">To retrieve access or audit rules from an existing file, use the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="aaef2-163">Örnekler</span><span class="sxs-lookup"><span data-stu-id="aaef2-163">Examples</span></span>  
  
### <a name="persisted-memory-mapped-files"></a><span data-ttu-id="aaef2-164">Kalıcı bellekle eşlenen dosyalar</span><span class="sxs-lookup"><span data-stu-id="aaef2-164">Persisted Memory-Mapped Files</span></span>  
 <span data-ttu-id="aaef2-165"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> yöntemleri, diskteki mevcut bir dosyadan bellek eşlemeli bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="aaef2-165">The <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> methods create a memory-mapped file from an existing file on disk.</span></span>  
  
 <span data-ttu-id="aaef2-166">Aşağıdaki örnek, son derece büyük bir dosyanın bir bölümünün bellek eşlemeli bir görünümünü oluşturur ve bir kısmını yönetir.</span><span class="sxs-lookup"><span data-stu-id="aaef2-166">The following example creates a memory-mapped view of a part of an extremely large file and manipulates a portion of it.</span></span>  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/vb/program.vb#1)]  
 
[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

 <span data-ttu-id="aaef2-167">Aşağıdaki örnek, başka bir işlem için aynı bellek eşlemeli dosyayı açar.</span><span class="sxs-lookup"><span data-stu-id="aaef2-167">The following example opens the same memory-mapped file for another process.</span></span>  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/vb/program.vb#1)]  
  
### <a name="non-persisted-memory-mapped-files"></a><span data-ttu-id="aaef2-168">Kalıcı olmayan bellekle eşlenen dosyalar</span><span class="sxs-lookup"><span data-stu-id="aaef2-168">Non-Persisted Memory-Mapped Files</span></span>  
 <span data-ttu-id="aaef2-169"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> ve <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> yöntemleri, diskteki mevcut bir dosyayla eşlenmemiş bir bellek eşlemeli dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="aaef2-169">The <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> and <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> methods create a memory-mapped file that is not mapped to an existing file on disk.</span></span>  
  
 <span data-ttu-id="aaef2-170">Aşağıdaki örnek, bellek eşlemeli bir dosyaya Boole değerleri yazan üç ayrı işlem (konsol uygulaması) içerir.</span><span class="sxs-lookup"><span data-stu-id="aaef2-170">The following example consists of three separate processes (console applications) that write Boolean values to a memory-mapped file.</span></span> <span data-ttu-id="aaef2-171">Aşağıdaki eylem sırası oluşur:</span><span class="sxs-lookup"><span data-stu-id="aaef2-171">The following sequence of actions occur:</span></span>  
  
1. <span data-ttu-id="aaef2-172">`Process A`, bellek eşlemeli dosyayı oluşturur ve ona bir değer yazar.</span><span class="sxs-lookup"><span data-stu-id="aaef2-172">`Process A` creates the memory-mapped file and writes a value to it.</span></span>  
  
2. <span data-ttu-id="aaef2-173">`Process B` bellek eşlemeli dosyayı açar ve bir değer yazar.</span><span class="sxs-lookup"><span data-stu-id="aaef2-173">`Process B` opens the memory-mapped file and writes a value to it.</span></span>  
  
3. <span data-ttu-id="aaef2-174">`Process C` bellek eşlemeli dosyayı açar ve bir değer yazar.</span><span class="sxs-lookup"><span data-stu-id="aaef2-174">`Process C` opens the memory-mapped file and writes a value to it.</span></span>  
  
4. <span data-ttu-id="aaef2-175">`Process A`, bellek eşlemeli dosyadaki değerleri okur ve görüntüler.</span><span class="sxs-lookup"><span data-stu-id="aaef2-175">`Process A` reads and displays the values from the memory-mapped file.</span></span>  
  
5. <span data-ttu-id="aaef2-176">Bellek eşlemeli dosyayla `Process A` sona erdikten sonra, dosya çöp toplama tarafından hemen geri kazanılır.</span><span class="sxs-lookup"><span data-stu-id="aaef2-176">After `Process A` is finished with the memory-mapped file, the file is immediately reclaimed by garbage collection.</span></span>  
  
 <span data-ttu-id="aaef2-177">Bu örneği çalıştırmak için şunları yapın:</span><span class="sxs-lookup"><span data-stu-id="aaef2-177">To run this example, do the following:</span></span>  
  
1. <span data-ttu-id="aaef2-178">Uygulamaları derleyin ve üç komut Istemi penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="aaef2-178">Compile the applications and open three Command Prompt windows.</span></span>  
  
2. <span data-ttu-id="aaef2-179">İlk komut Istemi penceresinde `Process A`' yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="aaef2-179">In the first Command Prompt window, run `Process A`.</span></span>  
  
3. <span data-ttu-id="aaef2-180">İkinci komut Istemi penceresinde `Process B`' yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="aaef2-180">In the second Command Prompt window, run `Process B`.</span></span>  
  
4. <span data-ttu-id="aaef2-181">`Process A` dönün ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="aaef2-181">Return to `Process A` and press ENTER.</span></span>  
  
5. <span data-ttu-id="aaef2-182">Üçüncü komut Istemi penceresinde `Process C`' yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="aaef2-182">In the third Command Prompt window, run `Process C`.</span></span>  
  
6. <span data-ttu-id="aaef2-183">`Process A` dönün ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="aaef2-183">Return to `Process A` and press ENTER.</span></span>  
  
 <span data-ttu-id="aaef2-184">`Process A` çıkışı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="aaef2-184">The output of `Process A` is as follows:</span></span>  
  
```console  
Start Process B and press ENTER to continue.  
Start Process C and press ENTER to continue.  
Process A says: True  
Process B says: False  
Process C says: True  
```  
  
 <span data-ttu-id="aaef2-185">**İşlem A**</span><span class="sxs-lookup"><span data-stu-id="aaef2-185">**Process A**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/vb/program.vb#1)]  
  
 <span data-ttu-id="aaef2-186">**İşlem B**</span><span class="sxs-lookup"><span data-stu-id="aaef2-186">**Process B**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/vb/program.vb#1)]  
  
 <span data-ttu-id="aaef2-187">**İşlem C**</span><span class="sxs-lookup"><span data-stu-id="aaef2-187">**Process C**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="aaef2-188">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aaef2-188">See also</span></span>

- [<span data-ttu-id="aaef2-189">Dosya ve Akış G/Ç'si</span><span class="sxs-lookup"><span data-stu-id="aaef2-189">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
