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
ms.openlocfilehash: 1cf2d7f36dbfffe1c86e32eec5137840837612f4
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208513"
---
# <a name="memory-mapped-files"></a><span data-ttu-id="90dbc-102">Bellek Eşlemeli Dosyalar</span><span class="sxs-lookup"><span data-stu-id="90dbc-102">Memory-Mapped Files</span></span>
<span data-ttu-id="90dbc-103">Bellek eşlemeli dosya sanal bellekte bir dosyanın içeriğini içerir.</span><span class="sxs-lookup"><span data-stu-id="90dbc-103">A memory-mapped file contains the contents of a file in virtual memory.</span></span> <span data-ttu-id="90dbc-104">Bu eşleme dosyası ve bellek alanı arasında okuyarak ve belleğe doğrudan yazma dosyasını değiştirmek birden çok işlemler de dahil olmak üzere bir uygulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="90dbc-104">This mapping between a file and memory space enables an application, including multiple processes, to modify the file by reading and writing directly to the memory.</span></span> <span data-ttu-id="90dbc-105">İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], yönetilen kod açıklandığı gibi bellek eşlemeli dosyalar access bellek eşlemeli dosyalar, yerel Windows işlevlerine aynı şekilde erişmek için kullanabileceğiniz [Managing Memory-Mapped dosyaları](https://msdn.microsoft.com/library/ms810613.aspx).</span><span class="sxs-lookup"><span data-stu-id="90dbc-105">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use managed code to access memory-mapped files in the same way that native Windows functions access memory-mapped files, as described in [Managing Memory-Mapped Files](https://msdn.microsoft.com/library/ms810613.aspx).</span></span>  
  
 <span data-ttu-id="90dbc-106">Bellek eşlemeli dosyalar iki tür vardır:</span><span class="sxs-lookup"><span data-stu-id="90dbc-106">There are two types of memory-mapped files:</span></span>  
  
-   <span data-ttu-id="90dbc-107">Kalıcı bellek eşlemeli dosyalar</span><span class="sxs-lookup"><span data-stu-id="90dbc-107">Persisted memory-mapped files</span></span>  
  
     <span data-ttu-id="90dbc-108">Bellek eşlemeli dosyalar, disk üzerindeki bir kaynak dosyayla ilişkili kalıcı dosyalarıdır.</span><span class="sxs-lookup"><span data-stu-id="90dbc-108">Persisted files are memory-mapped files that are associated with a source file on a disk.</span></span> <span data-ttu-id="90dbc-109">Son işlemi dosyasıyla çalışma sona erdiğinde, verileri diskteki kaynak dosyasına kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="90dbc-109">When the last process has finished working with the file, the data is saved to the source file on the disk.</span></span> <span data-ttu-id="90dbc-110">Bu bellek eşlemeli dosyalar, son derece büyük kaynak dosyalarıyla çalışmak için uygundur.</span><span class="sxs-lookup"><span data-stu-id="90dbc-110">These memory-mapped files are suitable for working with extremely large source files.</span></span>  
  
-   <span data-ttu-id="90dbc-111">Bellek eşlemeli dosyalar olmayan kalıcı</span><span class="sxs-lookup"><span data-stu-id="90dbc-111">Non-persisted memory-mapped files</span></span>  
  
     <span data-ttu-id="90dbc-112">Kalıcı olmayan bir diskte bir dosyayla ilişkili olmayan bellek eşlemeli dosyalar dosyalarıdır.</span><span class="sxs-lookup"><span data-stu-id="90dbc-112">Non-persisted files are memory-mapped files that are not associated with a file on a disk.</span></span> <span data-ttu-id="90dbc-113">Son işlemi dosyasıyla çalışma sona erdiğinde, veriler kaybolur ve atık toplama tarafından dosyayı geri.</span><span class="sxs-lookup"><span data-stu-id="90dbc-113">When the last process has finished working with the file, the data is lost and the file is reclaimed by garbage collection.</span></span> <span data-ttu-id="90dbc-114">Bu dosyalar, işlemler arası iletişim (IPC) için paylaşılan bellek oluşturmak için uygundur.</span><span class="sxs-lookup"><span data-stu-id="90dbc-114">These files are suitable for creating shared memory for inter-process communications (IPC).</span></span>  
  
## <a name="processes-views-and-managing-memory"></a><span data-ttu-id="90dbc-115">İşlemler, görünümleri ve yönetme bellek</span><span class="sxs-lookup"><span data-stu-id="90dbc-115">Processes, Views, and Managing Memory</span></span>  
 <span data-ttu-id="90dbc-116">Bellek eşlemeli dosyalar birden çok süreçler arasında paylaşılabilir.</span><span class="sxs-lookup"><span data-stu-id="90dbc-116">Memory-mapped files can be shared across multiple processes.</span></span> <span data-ttu-id="90dbc-117">İşlemler, dosyayı oluşturan işlem tarafından atanan ortak bir ad kullanarak aynı bellekle eşlenen dosyaya eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="90dbc-117">Processes can map to the same memory-mapped file by using a common name that is assigned by the process that created the file.</span></span>  
  
 <span data-ttu-id="90dbc-118">Bellek eşlemeli bir dosyayla çalışmak için bellekle eşlenen dosyanın tamamı veya bir kısmını görünümünü oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="90dbc-118">To work with a memory-mapped file, you must create a view of the entire memory-mapped file or a part of it.</span></span> <span data-ttu-id="90dbc-119">Ayrıca, böylece eş zamanlı bellek oluşturma bellekle eşlenen dosya aynı parçası için birden çok görünüm oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="90dbc-119">You can also create multiple views to the same part of the memory-mapped file, thereby creating concurrent memory.</span></span> <span data-ttu-id="90dbc-120">Eşzamanlı kalması iki görünüm için aynı bellekle eşlenen dosyasından oluşturulacak sahiptirler.</span><span class="sxs-lookup"><span data-stu-id="90dbc-120">For two views to remain concurrent, they have to be created from the same memory-mapped file.</span></span>  
  
 <span data-ttu-id="90dbc-121">Birden çok görünüm dosyanın kullanılabilir bellek (32-bit bilgisayarda 2 GB) eşleme için uygulamanın mantıksal bellek alanı boyuttan daha büyük olduğunda bu zorunlu olabilir.</span><span class="sxs-lookup"><span data-stu-id="90dbc-121">Multiple views may also be necessary if the file is greater than the size of the application’s logical memory space available for memory mapping (2 GB on a 32-bit computer).</span></span>  
  
 <span data-ttu-id="90dbc-122">İki tür görünüm vardır: akış erişim görünümü ve rasgele erişim görünümü.</span><span class="sxs-lookup"><span data-stu-id="90dbc-122">There are two types of views: stream access view and random access view.</span></span> <span data-ttu-id="90dbc-123">Sıralı erişim için bir dosya akışı erişim görünümlerini kullanın; Bu IPC ve kalıcı olmayan dosyalar için önerilir.</span><span class="sxs-lookup"><span data-stu-id="90dbc-123">Use stream access views for sequential access to a file; this is recommended for non-persisted files and IPC.</span></span> <span data-ttu-id="90dbc-124">Rasgele erişim görünümleri kalıcı dosyalarıyla çalışmak için tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="90dbc-124">Random access views are preferred for working with persisted files.</span></span>  
  
 <span data-ttu-id="90dbc-125">Böylece dosyayı otomatik olarak sayfaları sayıya bölümlenmiş ve gerektiğinde erişilen bellek eşlemeli dosyalar işletim sisteminin bellek yöneticisi erişilir.</span><span class="sxs-lookup"><span data-stu-id="90dbc-125">Memory-mapped files are accessed through the operating system’s memory manager, so the file is automatically partitioned into a number of pages and accessed as needed.</span></span> <span data-ttu-id="90dbc-126">Bellek yönetimi kendiniz işlemek gerekmez.</span><span class="sxs-lookup"><span data-stu-id="90dbc-126">You do not have to handle the memory management yourself.</span></span>  
  
 <span data-ttu-id="90dbc-127">Çakışan aynı bellekle eşlenen dosyayı aynı anda görünümleri ve aşağıdaki çizimde nasıl birden çok işlem olabilir birden çok gösterir.</span><span class="sxs-lookup"><span data-stu-id="90dbc-127">The following illustration shows how multiple processes can have multiple and overlapping views to the same memory-mapped file at the same time.</span></span>  
  
 <span data-ttu-id="90dbc-128">![Bellek görülür&#45;dosya eşlenmiş. ] (../../../docs/standard/io/media/memmappersisted.png "MemMapPersisted")</span><span class="sxs-lookup"><span data-stu-id="90dbc-128">![Shows views to a memory&#45;mapped file.](../../../docs/standard/io/media/memmappersisted.png "MemMapPersisted")</span></span>  
<span data-ttu-id="90dbc-129">Birden çok ve görünümler bellekle eşlenen bir dosyaya çakışan</span><span class="sxs-lookup"><span data-stu-id="90dbc-129">Multiple and overlapped views to a memory-mapped file</span></span>  
  
## <a name="programming-with-memory-mapped-files"></a><span data-ttu-id="90dbc-130">Bellek eşlemeli dosyalar ile programlama</span><span class="sxs-lookup"><span data-stu-id="90dbc-130">Programming with Memory-Mapped Files</span></span>  
 <span data-ttu-id="90dbc-131">Aşağıdaki tabloda, bellekle eşlenen dosya nesneleri ve üyeleri kullanmak için bir kılavuz sağlar.</span><span class="sxs-lookup"><span data-stu-id="90dbc-131">The following table provides a guide for using memory-mapped file objects and their members.</span></span>  
  
|<span data-ttu-id="90dbc-132">Görev</span><span class="sxs-lookup"><span data-stu-id="90dbc-132">Task</span></span>|<span data-ttu-id="90dbc-133">Yöntemleri veya özellikleri kullanmak için</span><span class="sxs-lookup"><span data-stu-id="90dbc-133">Methods or properties to use</span></span>|  
|----------|----------------------------------|  
|<span data-ttu-id="90dbc-134">Elde etmek için bir <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> kalıcı bellekle eşlenen dosyası disk üzerindeki bir dosyadan temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="90dbc-134">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object that represents a persisted memory-mapped file from a file on disk.</span></span>|<span data-ttu-id="90dbc-135"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType> yöntem.</span><span class="sxs-lookup"><span data-stu-id="90dbc-135"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="90dbc-136">Elde etmek için bir <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> (disk üzerindeki bir dosyayla ilişkili olmayan) bir kalıcı olmayan bellek eşlemeli dosyayı temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="90dbc-136">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object that represents a non-persisted memory-mapped file (not associated with a file on disk).</span></span>|<span data-ttu-id="90dbc-137"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType> yöntem.</span><span class="sxs-lookup"><span data-stu-id="90dbc-137"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType> method.</span></span><br /><br /> <span data-ttu-id="90dbc-138">- veya -</span><span class="sxs-lookup"><span data-stu-id="90dbc-138">- or -</span></span><br /><br /> <span data-ttu-id="90dbc-139"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType> yöntem.</span><span class="sxs-lookup"><span data-stu-id="90dbc-139"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="90dbc-140">Elde etmek için bir <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> nesne varolan bellekle eşlenen bir dosyanın (kalıcı veya kalıcı olmayan).</span><span class="sxs-lookup"><span data-stu-id="90dbc-140">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object of an existing memory-mapped file (either persisted or non-persisted).</span></span>|<span data-ttu-id="90dbc-141"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType> yöntem.</span><span class="sxs-lookup"><span data-stu-id="90dbc-141"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="90dbc-142">Elde etmek için bir <xref:System.IO.UnmanagedMemoryStream> nesnesi için bellek eşlemeli dosyasına sırayla erişilen bir görünüm.</span><span class="sxs-lookup"><span data-stu-id="90dbc-142">To obtain a <xref:System.IO.UnmanagedMemoryStream> object for a sequentially accessed view to the memory-mapped file.</span></span>|<span data-ttu-id="90dbc-143"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType> yöntem.</span><span class="sxs-lookup"><span data-stu-id="90dbc-143"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="90dbc-144">Elde etmek için bir <xref:System.IO.UnmanagedMemoryAccessor> bellek eşlemeli için rasgele erişim görünümün lanı nesne.</span><span class="sxs-lookup"><span data-stu-id="90dbc-144">To obtain a <xref:System.IO.UnmanagedMemoryAccessor> object for a random access view to a memory-mapped fie.</span></span>|<span data-ttu-id="90dbc-145"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType> yöntem.</span><span class="sxs-lookup"><span data-stu-id="90dbc-145"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="90dbc-146">Elde etmek için bir <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> yönetilmeyen kod ile kullanılacak nesne.</span><span class="sxs-lookup"><span data-stu-id="90dbc-146">To obtain a <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> object to use with unmanaged code.</span></span>|<span data-ttu-id="90dbc-147"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType> özellik.</span><span class="sxs-lookup"><span data-stu-id="90dbc-147"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType> property.</span></span><br /><br /> <span data-ttu-id="90dbc-148">- veya -</span><span class="sxs-lookup"><span data-stu-id="90dbc-148">- or -</span></span><br /><br /> <span data-ttu-id="90dbc-149"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> özellik.</span><span class="sxs-lookup"><span data-stu-id="90dbc-149"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> property.</span></span><br /><br /> <span data-ttu-id="90dbc-150">- veya -</span><span class="sxs-lookup"><span data-stu-id="90dbc-150">- or -</span></span><br /><br /> <span data-ttu-id="90dbc-151"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> özellik.</span><span class="sxs-lookup"><span data-stu-id="90dbc-151"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> property.</span></span>|  
|<span data-ttu-id="90dbc-152">Bir görünüm kadar bellek ayırma gecikme (yalnızca kalıcı olmayan dosyaları) oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="90dbc-152">To delay allocating memory until a view is created (non-persisted files only).</span></span><br /><br /> <span data-ttu-id="90dbc-153">(Geçerli sistem sayfa boyutu belirlemek için <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> özelliğini.)</span><span class="sxs-lookup"><span data-stu-id="90dbc-153">(To determine the current system page size, use the <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> property.)</span></span>|<span data-ttu-id="90dbc-154"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> yöntemiyle <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> değeri.</span><span class="sxs-lookup"><span data-stu-id="90dbc-154"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> method with the <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> value.</span></span><br /><br /> <span data-ttu-id="90dbc-155">- veya -</span><span class="sxs-lookup"><span data-stu-id="90dbc-155">- or -</span></span><br /><br /> <span data-ttu-id="90dbc-156"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> sahip yöntemleri bir <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> bir parametre olarak numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="90dbc-156"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> methods that have a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> enumeration as a parameter.</span></span>|  
  
### <a name="security"></a><span data-ttu-id="90dbc-157">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="90dbc-157">Security</span></span>  
 <span data-ttu-id="90dbc-158">Ele aşağıdaki yöntemleri kullanarak bir bellek eşlemeli dosyası oluşturduğunuzda, erişim hakları uygulayabileceğiniz bir <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> sabit bir parametre olarak:</span><span class="sxs-lookup"><span data-stu-id="90dbc-158">You can apply access rights when you create a memory-mapped file, by using the following methods that take a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> enumeration as a parameter:</span></span>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="90dbc-159">Kullanarak mevcut bir bellek eşlemeli dosyasını açmak için erişim haklarını belirtebilirsiniz <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> ele yöntemleri bir <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> bir parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="90dbc-159">You can specify access rights for opening an existing memory-mapped file by using the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> methods that take an <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> as a parameter.</span></span>  
  
 <span data-ttu-id="90dbc-160">Ayrıca, dahil edebileceğiniz bir <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> önceden tanımlanmış erişim kuralları içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="90dbc-160">In addition, you can include a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> object that contains predefined access rules.</span></span>  
  
 <span data-ttu-id="90dbc-161">Yeni veya değiştirilmiş erişim kuralları bellekle eşlenen bir dosyaya uygulanacak kullanmak <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="90dbc-161">To apply new or changed access rules to a memory-mapped file, use the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> method.</span></span> <span data-ttu-id="90dbc-162">Erişim almak veya varolan bir dosyanın kurallardan denetlemek için kullanın <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="90dbc-162">To retrieve access or audit rules from an existing file, use the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="90dbc-163">Örnekler</span><span class="sxs-lookup"><span data-stu-id="90dbc-163">Examples</span></span>  
  
### <a name="persisted-memory-mapped-files"></a><span data-ttu-id="90dbc-164">Kalıcı bellek eşlemeli dosyalar</span><span class="sxs-lookup"><span data-stu-id="90dbc-164">Persisted Memory-Mapped Files</span></span>  
 <span data-ttu-id="90dbc-165"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> Yöntemleri disk üzerinde var olan bir dosyadan bellekle eşlenen bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="90dbc-165">The <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> methods create a memory-mapped file from an existing file on disk.</span></span>  
  
 <span data-ttu-id="90dbc-166">Aşağıdaki örnek, son derece büyük bir dosya parçası bellekle eşlenen bir görünümünü oluşturur ve bir kısmı yönetir.</span><span class="sxs-lookup"><span data-stu-id="90dbc-166">The following example creates a memory-mapped view of a part of an extremely large file and manipulates a portion of it.</span></span>  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/vb/program.vb#1)]  
  
 <span data-ttu-id="90dbc-167">Aşağıdaki örnek, başka bir işlem için aynı bellekle eşlenen dosyasını açar.</span><span class="sxs-lookup"><span data-stu-id="90dbc-167">The following example opens the same memory-mapped file for another process.</span></span>  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/vb/program.vb#1)]  
  
### <a name="non-persisted-memory-mapped-files"></a><span data-ttu-id="90dbc-168">Kalıcı olmayan bellek eşlemeli dosyalar</span><span class="sxs-lookup"><span data-stu-id="90dbc-168">Non-Persisted Memory-Mapped Files</span></span>  
 <span data-ttu-id="90dbc-169"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> Ve <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> yöntemleri varolan bir dosyanın disk üzerinde eşlenmemiş bellekle eşlenen bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="90dbc-169">The <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> and <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> methods create a memory-mapped file that is not mapped to an existing file on disk.</span></span>  
  
 <span data-ttu-id="90dbc-170">Boole değerleri bellekle eşlenen bir dosyaya yazmak üç ayrı işlemler (konsol uygulamaları), aşağıdaki örnekte oluşur.</span><span class="sxs-lookup"><span data-stu-id="90dbc-170">The following example consists of three separate processes (console applications) that write Boolean values to a memory-mapped file.</span></span> <span data-ttu-id="90dbc-171">Aşağıdaki eylemler dizisi gerçekleşir:</span><span class="sxs-lookup"><span data-stu-id="90dbc-171">The following sequence of actions occur:</span></span>  
  
1.  <span data-ttu-id="90dbc-172">`Process A` bellek eşlemeli dosyası oluşturur ve bir değer yazar.</span><span class="sxs-lookup"><span data-stu-id="90dbc-172">`Process A` creates the memory-mapped file and writes a value to it.</span></span>  
  
2.  <span data-ttu-id="90dbc-173">`Process B` bellek eşlemeli dosyayı açar ve bir değer yazar.</span><span class="sxs-lookup"><span data-stu-id="90dbc-173">`Process B` opens the memory-mapped file and writes a value to it.</span></span>  
  
3.  <span data-ttu-id="90dbc-174">`Process C` bellek eşlemeli dosyayı açar ve bir değer yazar.</span><span class="sxs-lookup"><span data-stu-id="90dbc-174">`Process C` opens the memory-mapped file and writes a value to it.</span></span>  
  
4.  <span data-ttu-id="90dbc-175">`Process A` okur ve bellekle eşlenen dosyasından değerleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="90dbc-175">`Process A` reads and displays the values from the memory-mapped file.</span></span>  
  
5.  <span data-ttu-id="90dbc-176">Sonra `Process A` tamamlandı bellekle eşlenen dosyasıyla dosya atık toplama tarafından hemen iadesi.</span><span class="sxs-lookup"><span data-stu-id="90dbc-176">After `Process A` is finished with the memory-mapped file, the file is immediately reclaimed by garbage collection.</span></span>  
  
 <span data-ttu-id="90dbc-177">Bu örneği çalıştırmak için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="90dbc-177">To run this example, do the following:</span></span>  
  
1.  <span data-ttu-id="90dbc-178">Uygulamaları derleme ve üç komut istemi penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="90dbc-178">Compile the applications and open three Command Prompt windows.</span></span>  
  
2.  <span data-ttu-id="90dbc-179">İlk komut istemi penceresinde çalıştırın `Process A`.</span><span class="sxs-lookup"><span data-stu-id="90dbc-179">In the first Command Prompt window, run `Process A`.</span></span>  
  
3.  <span data-ttu-id="90dbc-180">İkinci komut istemi penceresinde çalıştırın `Process B`.</span><span class="sxs-lookup"><span data-stu-id="90dbc-180">In the second Command Prompt window, run `Process B`.</span></span>  
  
4.  <span data-ttu-id="90dbc-181">Geri dönüp `Process A` ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="90dbc-181">Return to `Process A` and press ENTER.</span></span>  
  
5.  <span data-ttu-id="90dbc-182">Üçüncü komut istemi penceresinde çalıştırın `Process C`.</span><span class="sxs-lookup"><span data-stu-id="90dbc-182">In the third Command Prompt window, run `Process C`.</span></span>  
  
6.  <span data-ttu-id="90dbc-183">Geri dönüp `Process A` ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="90dbc-183">Return to `Process A` and press ENTER.</span></span>  
  
 <span data-ttu-id="90dbc-184">Çıktısını `Process A` aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="90dbc-184">The output of `Process A` is as follows:</span></span>  
  
```  
Start Process B and press ENTER to continue.  
Start Process C and press ENTER to continue.  
Process A says: True  
Process B says: False  
Process C says: True  
```  
  
 <span data-ttu-id="90dbc-185">**İşlem A**</span><span class="sxs-lookup"><span data-stu-id="90dbc-185">**Process A**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/vb/program.vb#1)]  
  
 <span data-ttu-id="90dbc-186">**İşlem B**</span><span class="sxs-lookup"><span data-stu-id="90dbc-186">**Process B**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/vb/program.vb#1)]  
  
 <span data-ttu-id="90dbc-187">**İşlem C**</span><span class="sxs-lookup"><span data-stu-id="90dbc-187">**Process C**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="90dbc-188">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="90dbc-188">See Also</span></span>  
 [<span data-ttu-id="90dbc-189">Dosya ve Akış G/Ç'si</span><span class="sxs-lookup"><span data-stu-id="90dbc-189">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
