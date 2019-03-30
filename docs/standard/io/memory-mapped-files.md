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
ms.openlocfilehash: ebd54afb312de0796b5a96b3d41f1e98dd97bd1b
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58654360"
---
# <a name="memory-mapped-files"></a>Bellek Eşlemeli Dosyalar
Bir bellek işlemeli dosya sanal bellekte bir dosyanın içeriğini içerir. Bu dosya ve bellek alanı eşlemesini okuma ve yazma doğrudan bellek tarafından dosyasını değiştirmek birden çok işlem dahil olmak üzere bir uygulama sağlar. İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], yönetilen kod bellek eşlemeli dosyalar açıklandığı gibi aynı şekilde access bellek eşlemeli dosyalar, yerel Windows işlevlerine erişmek için kullanabileceğiniz [Managing Memory-Mapped dosyaları](https://docs.microsoft.com/previous-versions/ms810613(v=msdn.10)).  
  
 Bellek eşlemeli dosyalar iki tür vardır:  
  
-   Kalıcı bellek eşlemeli dosyalar  
  
     Disk üzerindeki bir kaynak dosyası ile ilişkili olan bellek eşlemeli dosyalar kalıcı dosyalarıdır. Son işlem dosyasıyla çalışma tamamlandığında, veri kaynak dosyanın disk üzerinde kaydedilir. Bu bellek eşlemeli dosyalar, son derece büyük bir kaynak dosyalarıyla çalışmak için uygundur.  
  
-   Kalıcı olmayan bellek eşlemeli dosyalar  
  
     Kalıcı olmayan bir diskte bir dosyayla ilişkili olmayan bellek eşlemeli dosyalar dosyalarıdır. Son işlem dosyasıyla çalışma tamamlandığında, veriler kaybolur ve dosyayı çöp toplamanın geri kazanılır. Bu dosyalar, işlemler arası iletişim (IPC) için paylaşılan belleği oluşturmak için uygundur.  
  
## <a name="processes-views-and-managing-memory"></a>İşlemler, görünümler ve yönetme bellek  
 Bellek eşlemeli dosyalar birden çok süreçler arasında paylaşılabilir. İşlemler aynı bellek eşlemeli dosya için dosya oluşturduğunuz işlem tarafından atanan bir ortak adını kullanarak eşleyebilirsiniz.  
  
 Bellek eşlemeli bir dosyayla çalışmak için tüm bellek eşlemeli dosya ya da bir kısmını bir görünüm oluşturmanız gerekir. Ayrıca, böylece eş zamanlı bellek oluşturma bellekle eşlenen dosya aynı parçası için birden çok görünüm oluşturabilirsiniz. Eşzamanlı kalmasını iki görünüm için bunlar aynı bellek eşlemeli dosyasından oluşturulması gerekir.  
  
 Birden çok görünüm dosya eşleme (32-bit bilgisayarda 2 GB) bellek için kullanılabilir bir uygulamanın mantıksal bellek alanı boyutundan büyükse, gerekli olabilir.  
  
 Görünüm iki tür vardır: akış erişimi görünümü ve rastgele erişim görünümü. Sıralı bir dosyasına erişimi Stream erişim görünümleri kullanma; Bu, IPC ve kalıcı olmayan dosyalar için önerilir. Rastgele erişim görünümleri kalıcı dosyalarıyla çalışmak için tercih edilir.  
  
 Dosya otomatik olarak bir dizi sayfa bölümlenmiş ve gerektiğinde erişilen bellek eşlemeli dosyalar işletim sisteminin bellek yöneticisi erişilir. Bellek yönetimi kendiniz işlemek zorunda değildir.  
  
 Çakışan aynı anda aynı bellek eşlemeli dosya görünümleri ve aşağıdaki çizimde nasıl birden çok işlem olabilir birden çok gösterir.

 Aşağıdaki görüntüde, birden çok gösterir ve bir bellek işlemeli dosya görünümlerine çakışan:  
  
 ![Bellek görünümleri gösteren ekran görüntüsü&#45;dosya eşlenmiş.](./media/memory-mapped-files/memory-map-persist-file.png)  
  
## <a name="programming-with-memory-mapped-files"></a>Bellek eşlemeli dosyalar ile programlama  
 Aşağıdaki tabloda, bellekle eşlenen dosya nesneleri ve üyeleri kullanmak için bir kılavuz sağlar.  
  
|Görev|Yöntemleri veya özellikleri kullanmak için|  
|----------|----------------------------------|  
|Elde etmek için bir <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> bir kalıcı bellek eşlemeli dosya diskte dosya temsil eden nesne.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType> yöntem.|  
|Elde etmek için bir <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> (disk üzerindeki bir dosyayla ilişkili olmayan) bir kalıcı olmayan bellek eşlemeli dosya temsil eden nesne.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType> yöntem.<br /><br /> - veya -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType> yöntem.|  
|Elde etmek için bir <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> nesne dosyasının mevcut bellek eşlemeli (kalıcı veya kalıcı olmayan).|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType> yöntem.|  
|Elde etmek için bir <xref:System.IO.UnmanagedMemoryStream> nesne için bellek eşlemeli dosya sıralı olarak erişilen bir görünüm.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType> yöntem.|  
|Elde etmek için bir <xref:System.IO.UnmanagedMemoryAccessor> bellek eşlemeli rastgele erişim görünümüne lanı nesnesi.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType> yöntem.|  
|Elde etmek için bir <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> yönetilmeyen kod ile kullanılacak nesne.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType> özellik.<br /><br /> - veya -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> özellik.<br /><br /> - veya -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> özellik.|  
|Bellek ayırma görünümü kadar gecikme (yalnızca kalıcı olmayan dosyaları) oluşturulur.<br /><br /> (Geçerli sistem sayfa boyutunu belirlemek için <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> özelliği.)|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> yöntemiyle <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> değeri.<br /><br /> - veya -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> içeren yöntemlerin bir <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> parametre olarak numaralandırması.|  
  
### <a name="security"></a>Güvenlik  
 Alan aşağıdaki yöntemleri kullanarak bir bellek işlemeli dosya oluşturduğunuzda, erişim hakları uygulayabilirsiniz bir <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> parametre olarak numaralandırması:  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>  
  
 Kullanarak mevcut bir bellek işlemeli dosya açmak için erişim haklarını belirtebilirsiniz <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> ele yöntemleri bir <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> bir parametre olarak.  
  
 Ayrıca, dahil edebileceğiniz bir <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> önceden tanımlanmış erişim kuralları içeren nesne.  
  
 Bellek eşlemeli dosya yeni veya değiştirilmiş erişim kuralları uygulamak için <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> yöntemi. Erişim almak veya mevcut bir dosyayı kurallardan denetim kullanın <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> yöntemi.  
  
## <a name="examples"></a>Örnekler  
  
### <a name="persisted-memory-mapped-files"></a>Kalıcı bellek eşlemeli dosyalar  
 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> Yöntemleri, disk üzerinde var olan bir dosyadan bir bellek işlemeli dosya oluşturun.  
  
 Aşağıdaki örnek, bir bellek eşlemeli görünümünü son derece büyük bir dosya oluşturur ve bir kısmı yönetir.  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/vb/program.vb#1)]  
  
 Aşağıdaki örnek, aynı bellek eşlemeli dosya başka bir işlem için açılır.  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/vb/program.vb#1)]  
  
### <a name="non-persisted-memory-mapped-files"></a>Kalıcı olmayan bellek eşlemeli dosyalar  
 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> Ve <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> yöntemleri, var olan bir dosyanın disk üzerinde eşlenmemiş bellekle eşlenen bir dosya oluşturun.  
  
 Aşağıdaki örnek, Boole değerleri bellekle eşlenen bir dosyaya yazma üç ayrı işlemler (konsol uygulamaları) oluşur. Aşağıdaki eylemler dizisini oluşur:  
  
1.  `Process A` bellek eşlemeli dosya oluşturur ve bir değer için yazar.  
  
2.  `Process B` bellek eşlemeli dosya açılır ve bir değer için yazar.  
  
3.  `Process C` bellek eşlemeli dosya açılır ve bir değer için yazar.  
  
4.  `Process A` okur ve bellek eşlemeli dosya değerleri görüntüler.  
  
5.  Sonra `Process A` tamamlandı bellekle eşlenen dosya ile dosya çöp toplamadan hemen iadesi.  
  
 Bu örneği çalıştırmak için aşağıdakileri yapın:  
  
1.  Uygulamaları derlemek ve üç komut istemi penceresi açın.  
  
2.  İlk komut istemi penceresinde çalıştırın `Process A`.  
  
3.  İkinci komut istemi penceresinde çalıştırın `Process B`.  
  
4.  Geri dönüp `Process A` ve ENTER tuşuna basın.  
  
5.  Üçüncü komut istemi penceresinde çalıştırın `Process C`.  
  
6.  Geri dönüp `Process A` ve ENTER tuşuna basın.  
  
 Çıkışı `Process A` aşağıdaki gibidir:  
  
```  
Start Process B and press ENTER to continue.  
Start Process C and press ENTER to continue.  
Process A says: True  
Process B says: False  
Process C says: True  
```  
  
 **Bir işlem**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/vb/program.vb#1)]  
  
 **İşlem B**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/vb/program.vb#1)]  
  
 **İşlem C**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/vb/program.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dosya ve Akış G/Ç'si](../../../docs/standard/io/index.md)
