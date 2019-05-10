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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bd1ced48847739318f22ec77b17a83a36fd36ee0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647765"
---
# <a name="memory-mapped-files"></a><span data-ttu-id="6fa0b-102">Bellek Eşlemeli Dosyalar</span><span class="sxs-lookup"><span data-stu-id="6fa0b-102">Memory-Mapped Files</span></span>
<span data-ttu-id="6fa0b-103">Bir bellek işlemeli dosya sanal bellekte bir dosyanın içeriğini içerir.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-103">A memory-mapped file contains the contents of a file in virtual memory.</span></span> <span data-ttu-id="6fa0b-104">Bu dosya ve bellek alanı eşlemesini okuma ve yazma doğrudan bellek tarafından dosyasını değiştirmek birden çok işlem dahil olmak üzere bir uygulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-104">This mapping between a file and memory space enables an application, including multiple processes, to modify the file by reading and writing directly to the memory.</span></span> <span data-ttu-id="6fa0b-105">İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], yönetilen kod bellek eşlemeli dosyalar açıklandığı gibi aynı şekilde access bellek eşlemeli dosyalar, yerel Windows işlevlerine erişmek için kullanabileceğiniz [Managing Memory-Mapped dosyaları](https://docs.microsoft.com/previous-versions/ms810613(v=msdn.10)).</span><span class="sxs-lookup"><span data-stu-id="6fa0b-105">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use managed code to access memory-mapped files in the same way that native Windows functions access memory-mapped files, as described in [Managing Memory-Mapped Files](https://docs.microsoft.com/previous-versions/ms810613(v=msdn.10)).</span></span>  
  
 <span data-ttu-id="6fa0b-106">Bellek eşlemeli dosyalar iki tür vardır:</span><span class="sxs-lookup"><span data-stu-id="6fa0b-106">There are two types of memory-mapped files:</span></span>  
  
- <span data-ttu-id="6fa0b-107">Kalıcı bellek eşlemeli dosyalar</span><span class="sxs-lookup"><span data-stu-id="6fa0b-107">Persisted memory-mapped files</span></span>  
  
     <span data-ttu-id="6fa0b-108">Disk üzerindeki bir kaynak dosyası ile ilişkili olan bellek eşlemeli dosyalar kalıcı dosyalarıdır.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-108">Persisted files are memory-mapped files that are associated with a source file on a disk.</span></span> <span data-ttu-id="6fa0b-109">Son işlem dosyasıyla çalışma tamamlandığında, veri kaynak dosyanın disk üzerinde kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-109">When the last process has finished working with the file, the data is saved to the source file on the disk.</span></span> <span data-ttu-id="6fa0b-110">Bu bellek eşlemeli dosyalar, son derece büyük bir kaynak dosyalarıyla çalışmak için uygundur.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-110">These memory-mapped files are suitable for working with extremely large source files.</span></span>  
  
- <span data-ttu-id="6fa0b-111">Kalıcı olmayan bellek eşlemeli dosyalar</span><span class="sxs-lookup"><span data-stu-id="6fa0b-111">Non-persisted memory-mapped files</span></span>  
  
     <span data-ttu-id="6fa0b-112">Kalıcı olmayan bir diskte bir dosyayla ilişkili olmayan bellek eşlemeli dosyalar dosyalarıdır.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-112">Non-persisted files are memory-mapped files that are not associated with a file on a disk.</span></span> <span data-ttu-id="6fa0b-113">Son işlem dosyasıyla çalışma tamamlandığında, veriler kaybolur ve dosyayı çöp toplamanın geri kazanılır.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-113">When the last process has finished working with the file, the data is lost and the file is reclaimed by garbage collection.</span></span> <span data-ttu-id="6fa0b-114">Bu dosyalar, işlemler arası iletişim (IPC) için paylaşılan belleği oluşturmak için uygundur.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-114">These files are suitable for creating shared memory for inter-process communications (IPC).</span></span>  
  
## <a name="processes-views-and-managing-memory"></a><span data-ttu-id="6fa0b-115">İşlemler, görünümler ve yönetme bellek</span><span class="sxs-lookup"><span data-stu-id="6fa0b-115">Processes, Views, and Managing Memory</span></span>  
 <span data-ttu-id="6fa0b-116">Bellek eşlemeli dosyalar birden çok süreçler arasında paylaşılabilir.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-116">Memory-mapped files can be shared across multiple processes.</span></span> <span data-ttu-id="6fa0b-117">İşlemler aynı bellek eşlemeli dosya için dosya oluşturduğunuz işlem tarafından atanan bir ortak adını kullanarak eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-117">Processes can map to the same memory-mapped file by using a common name that is assigned by the process that created the file.</span></span>  
  
 <span data-ttu-id="6fa0b-118">Bellek eşlemeli bir dosyayla çalışmak için tüm bellek eşlemeli dosya ya da bir kısmını bir görünüm oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-118">To work with a memory-mapped file, you must create a view of the entire memory-mapped file or a part of it.</span></span> <span data-ttu-id="6fa0b-119">Ayrıca, böylece eş zamanlı bellek oluşturma bellekle eşlenen dosya aynı parçası için birden çok görünüm oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-119">You can also create multiple views to the same part of the memory-mapped file, thereby creating concurrent memory.</span></span> <span data-ttu-id="6fa0b-120">Eşzamanlı kalmasını iki görünüm için bunlar aynı bellek eşlemeli dosyasından oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-120">For two views to remain concurrent, they have to be created from the same memory-mapped file.</span></span>  
  
 <span data-ttu-id="6fa0b-121">Birden çok görünüm dosya eşleme (32-bit bilgisayarda 2 GB) bellek için kullanılabilir bir uygulamanın mantıksal bellek alanı boyutundan büyükse, gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-121">Multiple views may also be necessary if the file is greater than the size of the application’s logical memory space available for memory mapping (2 GB on a 32-bit computer).</span></span>  
  
 <span data-ttu-id="6fa0b-122">Görünüm iki tür vardır: akış erişimi görünümü ve rastgele erişim görünümü.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-122">There are two types of views: stream access view and random access view.</span></span> <span data-ttu-id="6fa0b-123">Sıralı bir dosyasına erişimi Stream erişim görünümleri kullanma; Bu, IPC ve kalıcı olmayan dosyalar için önerilir.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-123">Use stream access views for sequential access to a file; this is recommended for non-persisted files and IPC.</span></span> <span data-ttu-id="6fa0b-124">Rastgele erişim görünümleri kalıcı dosyalarıyla çalışmak için tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-124">Random access views are preferred for working with persisted files.</span></span>  
  
 <span data-ttu-id="6fa0b-125">Dosya otomatik olarak bir dizi sayfa bölümlenmiş ve gerektiğinde erişilen bellek eşlemeli dosyalar işletim sisteminin bellek yöneticisi erişilir.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-125">Memory-mapped files are accessed through the operating system’s memory manager, so the file is automatically partitioned into a number of pages and accessed as needed.</span></span> <span data-ttu-id="6fa0b-126">Bellek yönetimi kendiniz işlemek zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-126">You do not have to handle the memory management yourself.</span></span>  
  
 <span data-ttu-id="6fa0b-127">Çakışan aynı anda aynı bellek eşlemeli dosya görünümleri ve aşağıdaki çizimde nasıl birden çok işlem olabilir birden çok gösterir.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-127">The following illustration shows how multiple processes can have multiple and overlapping views to the same memory-mapped file at the same time.</span></span>

 <span data-ttu-id="6fa0b-128">Aşağıdaki görüntüde, birden çok gösterir ve bir bellek işlemeli dosya görünümlerine çakışan:</span><span class="sxs-lookup"><span data-stu-id="6fa0b-128">The following image shows multiple and overlapped views to a memory-mapped file:</span></span>  
  
 ![Bellek görünümleri gösteren ekran görüntüsü&#45;dosya eşlenmiş.](./media/memory-mapped-files/memory-map-persist-file.png)  
  
## <a name="programming-with-memory-mapped-files"></a><span data-ttu-id="6fa0b-130">Bellek eşlemeli dosyalar ile programlama</span><span class="sxs-lookup"><span data-stu-id="6fa0b-130">Programming with Memory-Mapped Files</span></span>  
 <span data-ttu-id="6fa0b-131">Aşağıdaki tabloda, bellekle eşlenen dosya nesneleri ve üyeleri kullanmak için bir kılavuz sağlar.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-131">The following table provides a guide for using memory-mapped file objects and their members.</span></span>  
  
|<span data-ttu-id="6fa0b-132">Görev</span><span class="sxs-lookup"><span data-stu-id="6fa0b-132">Task</span></span>|<span data-ttu-id="6fa0b-133">Yöntemleri veya özellikleri kullanmak için</span><span class="sxs-lookup"><span data-stu-id="6fa0b-133">Methods or properties to use</span></span>|  
|----------|----------------------------------|  
|<span data-ttu-id="6fa0b-134">Elde etmek için bir <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> bir kalıcı bellek eşlemeli dosya diskte dosya temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-134">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object that represents a persisted memory-mapped file from a file on disk.</span></span>|<span data-ttu-id="6fa0b-135"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType> yöntem.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-135"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="6fa0b-136">Elde etmek için bir <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> (disk üzerindeki bir dosyayla ilişkili olmayan) bir kalıcı olmayan bellek eşlemeli dosya temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-136">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object that represents a non-persisted memory-mapped file (not associated with a file on disk).</span></span>|<span data-ttu-id="6fa0b-137"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType> yöntem.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-137"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType> method.</span></span><br /><br /> <span data-ttu-id="6fa0b-138">- veya -</span><span class="sxs-lookup"><span data-stu-id="6fa0b-138">- or -</span></span><br /><br /> <span data-ttu-id="6fa0b-139"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType> yöntem.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-139"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="6fa0b-140">Elde etmek için bir <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> nesne dosyasının mevcut bellek eşlemeli (kalıcı veya kalıcı olmayan).</span><span class="sxs-lookup"><span data-stu-id="6fa0b-140">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object of an existing memory-mapped file (either persisted or non-persisted).</span></span>|<span data-ttu-id="6fa0b-141"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType> yöntem.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-141"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="6fa0b-142">Elde etmek için bir <xref:System.IO.UnmanagedMemoryStream> nesne için bellek eşlemeli dosya sıralı olarak erişilen bir görünüm.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-142">To obtain a <xref:System.IO.UnmanagedMemoryStream> object for a sequentially accessed view to the memory-mapped file.</span></span>|<span data-ttu-id="6fa0b-143"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType> yöntem.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-143"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="6fa0b-144">Elde etmek için bir <xref:System.IO.UnmanagedMemoryAccessor> bellek eşlemeli rastgele erişim görünümüne lanı nesnesi.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-144">To obtain a <xref:System.IO.UnmanagedMemoryAccessor> object for a random access view to a memory-mapped fie.</span></span>|<span data-ttu-id="6fa0b-145"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType> yöntem.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-145"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="6fa0b-146">Elde etmek için bir <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> yönetilmeyen kod ile kullanılacak nesne.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-146">To obtain a <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> object to use with unmanaged code.</span></span>|<span data-ttu-id="6fa0b-147"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType> özellik.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-147"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType> property.</span></span><br /><br /> <span data-ttu-id="6fa0b-148">- veya -</span><span class="sxs-lookup"><span data-stu-id="6fa0b-148">- or -</span></span><br /><br /> <span data-ttu-id="6fa0b-149"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> özellik.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-149"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> property.</span></span><br /><br /> <span data-ttu-id="6fa0b-150">- veya -</span><span class="sxs-lookup"><span data-stu-id="6fa0b-150">- or -</span></span><br /><br /> <span data-ttu-id="6fa0b-151"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> özellik.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-151"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> property.</span></span>|  
|<span data-ttu-id="6fa0b-152">Bellek ayırma görünümü kadar gecikme (yalnızca kalıcı olmayan dosyaları) oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-152">To delay allocating memory until a view is created (non-persisted files only).</span></span><br /><br /> <span data-ttu-id="6fa0b-153">(Geçerli sistem sayfa boyutunu belirlemek için <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> özelliği.)</span><span class="sxs-lookup"><span data-stu-id="6fa0b-153">(To determine the current system page size, use the <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> property.)</span></span>|<span data-ttu-id="6fa0b-154"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> yöntemiyle <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> değeri.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-154"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> method with the <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> value.</span></span><br /><br /> <span data-ttu-id="6fa0b-155">- veya -</span><span class="sxs-lookup"><span data-stu-id="6fa0b-155">- or -</span></span><br /><br /> <span data-ttu-id="6fa0b-156"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> içeren yöntemlerin bir <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> parametre olarak numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-156"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> methods that have a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> enumeration as a parameter.</span></span>|  
  
### <a name="security"></a><span data-ttu-id="6fa0b-157">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="6fa0b-157">Security</span></span>  
 <span data-ttu-id="6fa0b-158">Alan aşağıdaki yöntemleri kullanarak bir bellek işlemeli dosya oluşturduğunuzda, erişim hakları uygulayabilirsiniz bir <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> parametre olarak numaralandırması:</span><span class="sxs-lookup"><span data-stu-id="6fa0b-158">You can apply access rights when you create a memory-mapped file, by using the following methods that take a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> enumeration as a parameter:</span></span>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="6fa0b-159">Kullanarak mevcut bir bellek işlemeli dosya açmak için erişim haklarını belirtebilirsiniz <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> ele yöntemleri bir <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> bir parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-159">You can specify access rights for opening an existing memory-mapped file by using the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> methods that take an <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> as a parameter.</span></span>  
  
 <span data-ttu-id="6fa0b-160">Ayrıca, dahil edebileceğiniz bir <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> önceden tanımlanmış erişim kuralları içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-160">In addition, you can include a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> object that contains predefined access rules.</span></span>  
  
 <span data-ttu-id="6fa0b-161">Bellek eşlemeli dosya yeni veya değiştirilmiş erişim kuralları uygulamak için <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-161">To apply new or changed access rules to a memory-mapped file, use the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> method.</span></span> <span data-ttu-id="6fa0b-162">Erişim almak veya mevcut bir dosyayı kurallardan denetim kullanın <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-162">To retrieve access or audit rules from an existing file, use the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="6fa0b-163">Örnekler</span><span class="sxs-lookup"><span data-stu-id="6fa0b-163">Examples</span></span>  
  
### <a name="persisted-memory-mapped-files"></a><span data-ttu-id="6fa0b-164">Kalıcı bellek eşlemeli dosyalar</span><span class="sxs-lookup"><span data-stu-id="6fa0b-164">Persisted Memory-Mapped Files</span></span>  
 <span data-ttu-id="6fa0b-165"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> Yöntemleri, disk üzerinde var olan bir dosyadan bir bellek işlemeli dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-165">The <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> methods create a memory-mapped file from an existing file on disk.</span></span>  
  
 <span data-ttu-id="6fa0b-166">Aşağıdaki örnek, bir bellek eşlemeli görünümünü son derece büyük bir dosya oluşturur ve bir kısmı yönetir.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-166">The following example creates a memory-mapped view of a part of an extremely large file and manipulates a portion of it.</span></span>  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/vb/program.vb#1)]  
  
 <span data-ttu-id="6fa0b-167">Aşağıdaki örnek, aynı bellek eşlemeli dosya başka bir işlem için açılır.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-167">The following example opens the same memory-mapped file for another process.</span></span>  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/vb/program.vb#1)]  
  
### <a name="non-persisted-memory-mapped-files"></a><span data-ttu-id="6fa0b-168">Kalıcı olmayan bellek eşlemeli dosyalar</span><span class="sxs-lookup"><span data-stu-id="6fa0b-168">Non-Persisted Memory-Mapped Files</span></span>  
 <span data-ttu-id="6fa0b-169"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> Ve <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> yöntemleri, var olan bir dosyanın disk üzerinde eşlenmemiş bellekle eşlenen bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-169">The <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> and <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> methods create a memory-mapped file that is not mapped to an existing file on disk.</span></span>  
  
 <span data-ttu-id="6fa0b-170">Aşağıdaki örnek, Boole değerleri bellekle eşlenen bir dosyaya yazma üç ayrı işlemler (konsol uygulamaları) oluşur.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-170">The following example consists of three separate processes (console applications) that write Boolean values to a memory-mapped file.</span></span> <span data-ttu-id="6fa0b-171">Aşağıdaki eylemler dizisini oluşur:</span><span class="sxs-lookup"><span data-stu-id="6fa0b-171">The following sequence of actions occur:</span></span>  
  
1. <span data-ttu-id="6fa0b-172">`Process A` bellek eşlemeli dosya oluşturur ve bir değer için yazar.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-172">`Process A` creates the memory-mapped file and writes a value to it.</span></span>  
  
2. <span data-ttu-id="6fa0b-173">`Process B` bellek eşlemeli dosya açılır ve bir değer için yazar.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-173">`Process B` opens the memory-mapped file and writes a value to it.</span></span>  
  
3. <span data-ttu-id="6fa0b-174">`Process C` bellek eşlemeli dosya açılır ve bir değer için yazar.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-174">`Process C` opens the memory-mapped file and writes a value to it.</span></span>  
  
4. <span data-ttu-id="6fa0b-175">`Process A` okur ve bellek eşlemeli dosya değerleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-175">`Process A` reads and displays the values from the memory-mapped file.</span></span>  
  
5. <span data-ttu-id="6fa0b-176">Sonra `Process A` tamamlandı bellekle eşlenen dosya ile dosya çöp toplamadan hemen iadesi.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-176">After `Process A` is finished with the memory-mapped file, the file is immediately reclaimed by garbage collection.</span></span>  
  
 <span data-ttu-id="6fa0b-177">Bu örneği çalıştırmak için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="6fa0b-177">To run this example, do the following:</span></span>  
  
1. <span data-ttu-id="6fa0b-178">Uygulamaları derlemek ve üç komut istemi penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-178">Compile the applications and open three Command Prompt windows.</span></span>  
  
2. <span data-ttu-id="6fa0b-179">İlk komut istemi penceresinde çalıştırın `Process A`.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-179">In the first Command Prompt window, run `Process A`.</span></span>  
  
3. <span data-ttu-id="6fa0b-180">İkinci komut istemi penceresinde çalıştırın `Process B`.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-180">In the second Command Prompt window, run `Process B`.</span></span>  
  
4. <span data-ttu-id="6fa0b-181">Geri dönüp `Process A` ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-181">Return to `Process A` and press ENTER.</span></span>  
  
5. <span data-ttu-id="6fa0b-182">Üçüncü komut istemi penceresinde çalıştırın `Process C`.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-182">In the third Command Prompt window, run `Process C`.</span></span>  
  
6. <span data-ttu-id="6fa0b-183">Geri dönüp `Process A` ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-183">Return to `Process A` and press ENTER.</span></span>  
  
 <span data-ttu-id="6fa0b-184">Çıkışı `Process A` aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="6fa0b-184">The output of `Process A` is as follows:</span></span>  
  
```  
Start Process B and press ENTER to continue.  
Start Process C and press ENTER to continue.  
Process A says: True  
Process B says: False  
Process C says: True  
```  
  
 <span data-ttu-id="6fa0b-185">**Bir işlem**</span><span class="sxs-lookup"><span data-stu-id="6fa0b-185">**Process A**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/vb/program.vb#1)]  
  
 <span data-ttu-id="6fa0b-186">**İşlem B**</span><span class="sxs-lookup"><span data-stu-id="6fa0b-186">**Process B**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/vb/program.vb#1)]  
  
 <span data-ttu-id="6fa0b-187">**İşlem C**</span><span class="sxs-lookup"><span data-stu-id="6fa0b-187">**Process C**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="6fa0b-188">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6fa0b-188">See also</span></span>

- [<span data-ttu-id="6fa0b-189">Dosya ve Akış G/Ç'si</span><span class="sxs-lookup"><span data-stu-id="6fa0b-189">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
