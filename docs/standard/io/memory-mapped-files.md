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
# <a name="memory-mapped-files"></a>Bellek Eşlemeli Dosyalar
Bellek eşlemeli dosya sanal bellekte bir dosyanın içeriğini içerir. Bu eşleme dosyası ve bellek alanı arasında okuyarak ve belleğe doğrudan yazma dosyasını değiştirmek birden çok işlemler de dahil olmak üzere bir uygulama sağlar. İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], yönetilen kod açıklandığı gibi bellek eşlemeli dosyalar access bellek eşlemeli dosyalar, yerel Windows işlevlerine aynı şekilde erişmek için kullanabileceğiniz [Managing Memory-Mapped dosyaları](https://msdn.microsoft.com/library/ms810613.aspx).  
  
 Bellek eşlemeli dosyalar iki tür vardır:  
  
-   Kalıcı bellek eşlemeli dosyalar  
  
     Bellek eşlemeli dosyalar, disk üzerindeki bir kaynak dosyayla ilişkili kalıcı dosyalarıdır. Son işlemi dosyasıyla çalışma sona erdiğinde, verileri diskteki kaynak dosyasına kaydedilir. Bu bellek eşlemeli dosyalar, son derece büyük kaynak dosyalarıyla çalışmak için uygundur.  
  
-   Bellek eşlemeli dosyalar olmayan kalıcı  
  
     Kalıcı olmayan bir diskte bir dosyayla ilişkili olmayan bellek eşlemeli dosyalar dosyalarıdır. Son işlemi dosyasıyla çalışma sona erdiğinde, veriler kaybolur ve atık toplama tarafından dosyayı geri. Bu dosyalar, işlemler arası iletişim (IPC) için paylaşılan bellek oluşturmak için uygundur.  
  
## <a name="processes-views-and-managing-memory"></a>İşlemler, görünümleri ve yönetme bellek  
 Bellek eşlemeli dosyalar birden çok süreçler arasında paylaşılabilir. İşlemler, dosyayı oluşturan işlem tarafından atanan ortak bir ad kullanarak aynı bellekle eşlenen dosyaya eşleyebilirsiniz.  
  
 Bellek eşlemeli bir dosyayla çalışmak için bellekle eşlenen dosyanın tamamı veya bir kısmını görünümünü oluşturmanız gerekir. Ayrıca, böylece eş zamanlı bellek oluşturma bellekle eşlenen dosya aynı parçası için birden çok görünüm oluşturabilirsiniz. Eşzamanlı kalması iki görünüm için aynı bellekle eşlenen dosyasından oluşturulacak sahiptirler.  
  
 Birden çok görünüm dosyanın kullanılabilir bellek (32-bit bilgisayarda 2 GB) eşleme için uygulamanın mantıksal bellek alanı boyuttan daha büyük olduğunda bu zorunlu olabilir.  
  
 İki tür görünüm vardır: akış erişim görünümü ve rasgele erişim görünümü. Sıralı erişim için bir dosya akışı erişim görünümlerini kullanın; Bu IPC ve kalıcı olmayan dosyalar için önerilir. Rasgele erişim görünümleri kalıcı dosyalarıyla çalışmak için tercih edilir.  
  
 Böylece dosyayı otomatik olarak sayfaları sayıya bölümlenmiş ve gerektiğinde erişilen bellek eşlemeli dosyalar işletim sisteminin bellek yöneticisi erişilir. Bellek yönetimi kendiniz işlemek gerekmez.  
  
 Çakışan aynı bellekle eşlenen dosyayı aynı anda görünümleri ve aşağıdaki çizimde nasıl birden çok işlem olabilir birden çok gösterir.  
  
 ![Bellek görülür&#45;dosya eşlenmiş. ] (../../../docs/standard/io/media/memmappersisted.png "MemMapPersisted")  
Birden çok ve görünümler bellekle eşlenen bir dosyaya çakışan  
  
## <a name="programming-with-memory-mapped-files"></a>Bellek eşlemeli dosyalar ile programlama  
 Aşağıdaki tabloda, bellekle eşlenen dosya nesneleri ve üyeleri kullanmak için bir kılavuz sağlar.  
  
|Görev|Yöntemleri veya özellikleri kullanmak için|  
|----------|----------------------------------|  
|Elde etmek için bir <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> kalıcı bellekle eşlenen dosyası disk üzerindeki bir dosyadan temsil eden nesne.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType> yöntem.|  
|Elde etmek için bir <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> (disk üzerindeki bir dosyayla ilişkili olmayan) bir kalıcı olmayan bellek eşlemeli dosyayı temsil eden nesne.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType> yöntem.<br /><br /> - veya -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType> yöntem.|  
|Elde etmek için bir <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> nesne varolan bellekle eşlenen bir dosyanın (kalıcı veya kalıcı olmayan).|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType> yöntem.|  
|Elde etmek için bir <xref:System.IO.UnmanagedMemoryStream> nesnesi için bellek eşlemeli dosyasına sırayla erişilen bir görünüm.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType> yöntem.|  
|Elde etmek için bir <xref:System.IO.UnmanagedMemoryAccessor> bellek eşlemeli için rasgele erişim görünümün lanı nesne.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType> yöntem.|  
|Elde etmek için bir <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> yönetilmeyen kod ile kullanılacak nesne.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType> özellik.<br /><br /> - veya -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> özellik.<br /><br /> - veya -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> özellik.|  
|Bir görünüm kadar bellek ayırma gecikme (yalnızca kalıcı olmayan dosyaları) oluşturulur.<br /><br /> (Geçerli sistem sayfa boyutu belirlemek için <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> özelliğini.)|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> yöntemiyle <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> değeri.<br /><br /> - veya -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> sahip yöntemleri bir <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> bir parametre olarak numaralandırması.|  
  
### <a name="security"></a>Güvenlik  
 Ele aşağıdaki yöntemleri kullanarak bir bellek eşlemeli dosyası oluşturduğunuzda, erişim hakları uygulayabileceğiniz bir <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> sabit bir parametre olarak:  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>  
  
 Kullanarak mevcut bir bellek eşlemeli dosyasını açmak için erişim haklarını belirtebilirsiniz <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> ele yöntemleri bir <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> bir parametre olarak.  
  
 Ayrıca, dahil edebileceğiniz bir <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> önceden tanımlanmış erişim kuralları içeren nesne.  
  
 Yeni veya değiştirilmiş erişim kuralları bellekle eşlenen bir dosyaya uygulanacak kullanmak <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> yöntemi. Erişim almak veya varolan bir dosyanın kurallardan denetlemek için kullanın <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> yöntemi.  
  
## <a name="examples"></a>Örnekler  
  
### <a name="persisted-memory-mapped-files"></a>Kalıcı bellek eşlemeli dosyalar  
 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> Yöntemleri disk üzerinde var olan bir dosyadan bellekle eşlenen bir dosya oluşturun.  
  
 Aşağıdaki örnek, son derece büyük bir dosya parçası bellekle eşlenen bir görünümünü oluşturur ve bir kısmı yönetir.  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/vb/program.vb#1)]  
  
 Aşağıdaki örnek, başka bir işlem için aynı bellekle eşlenen dosyasını açar.  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/vb/program.vb#1)]  
  
### <a name="non-persisted-memory-mapped-files"></a>Kalıcı olmayan bellek eşlemeli dosyalar  
 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> Ve <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> yöntemleri varolan bir dosyanın disk üzerinde eşlenmemiş bellekle eşlenen bir dosya oluşturun.  
  
 Boole değerleri bellekle eşlenen bir dosyaya yazmak üç ayrı işlemler (konsol uygulamaları), aşağıdaki örnekte oluşur. Aşağıdaki eylemler dizisi gerçekleşir:  
  
1.  `Process A` bellek eşlemeli dosyası oluşturur ve bir değer yazar.  
  
2.  `Process B` bellek eşlemeli dosyayı açar ve bir değer yazar.  
  
3.  `Process C` bellek eşlemeli dosyayı açar ve bir değer yazar.  
  
4.  `Process A` okur ve bellekle eşlenen dosyasından değerleri görüntüler.  
  
5.  Sonra `Process A` tamamlandı bellekle eşlenen dosyasıyla dosya atık toplama tarafından hemen iadesi.  
  
 Bu örneği çalıştırmak için aşağıdakileri yapın:  
  
1.  Uygulamaları derleme ve üç komut istemi penceresi açın.  
  
2.  İlk komut istemi penceresinde çalıştırın `Process A`.  
  
3.  İkinci komut istemi penceresinde çalıştırın `Process B`.  
  
4.  Geri dönüp `Process A` ve ENTER tuşuna basın.  
  
5.  Üçüncü komut istemi penceresinde çalıştırın `Process C`.  
  
6.  Geri dönüp `Process A` ve ENTER tuşuna basın.  
  
 Çıktısını `Process A` aşağıdaki gibidir:  
  
```  
Start Process B and press ENTER to continue.  
Start Process C and press ENTER to continue.  
Process A says: True  
Process B says: False  
Process C says: True  
```  
  
 **İşlem A**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/vb/program.vb#1)]  
  
 **İşlem B**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/vb/program.vb#1)]  
  
 **İşlem C**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/vb/program.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dosya ve Akış G/Ç'si](../../../docs/standard/io/index.md)
