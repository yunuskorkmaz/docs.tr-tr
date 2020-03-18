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
# <a name="memory-mapped-files"></a>Bellek Eşlemeli Dosyalar
Bellek eşlenen bir dosya, sanal bellekteki bir dosyanın içeriğini içerir. Bir dosya ve bellek alanı arasındaki bu eşleme, birden çok işlem de dahil olmak üzere bir uygulamanın, doğrudan belleğe okuyarak ve yazarak dosyayı değiştirmesini sağlar. .NET Framework 4'ten başlayarak, bellek eşlenen dosyalara erişmek için yönetilen kodu, yerel Windows işlevlerinin [Bellek Eşlenen Dosyaları Yönetme'de](https://docs.microsoft.com/previous-versions/ms810613(v=msdn.10))açıklandığı gibi bellek eşlenen dosyalara eriştiği şekilde kullanabilirsiniz.  
  
 Bellek eşlenen iki tür dosya vardır:  
  
- Kalıcı bellek eşlenen dosyalar  
  
     Kalıcı dosyalar, diskteki bir kaynak dosyayla ilişkili bellek eşlenen dosyalardır. Son işlem dosyayla çalışmayı tamamladığında, veriler diskteki kaynak dosyaya kaydedilir. Bu bellek eşlenen dosyalar son derece büyük kaynak dosyaları ile çalışmak için uygundur.  
  
- Kalıcı olmayan bellek eşlenen dosyalar  
  
     Kalıcı olmayan dosyalar, diskteki bir dosyayla ilişkilendirilmeyen bellek eşlenen dosyalardır. Son işlem dosyayla çalışmayı tamamladığında, veriler kaybolur ve dosya çöp toplama tarafından geri alınır. Bu dosyalar, süreçler arası iletişim (IPC) için paylaşılan bellek oluşturmak için uygundur.  
  
## <a name="processes-views-and-managing-memory"></a>Süreçler, Görünümler ve Bellek Yönetimi  
 Bellek eşlenen dosyalar birden çok işlem arasında paylaşılabilir. İşlemler, dosyayı oluşturan işlem tarafından atanan ortak bir ad kullanarak aynı bellek eşlenen dosyayla eşlenebilir.  
  
 Bellek eşlenen bir dosyayla çalışmak için, bellek eşlenen dosyanın tamamının veya bir bölümünün görünümünü oluşturmanız gerekir. Ayrıca, bellek eşlenen dosyanın aynı bölümüne birden çok görünüm oluşturarak eşzamanlı bellek oluşturabilirsiniz. İki görünümün eşzamanlı kalması için, aynı bellek eşlenen dosyadan oluşturulması gerekir.  
  
 Dosya, uygulamanın bellek eşlemi için kullanılabilir mantıksal bellek alanının boyutundan büyükse (32 bit bilgisayarda 2 GB) birden çok görünüm de gerekebilir.  
  
 İki tür görünüm vardır: akış erişim görünümü ve rasgele erişim görünümü. Bir dosyaya sıralı erişim için akış erişim görünümlerini kullanın; bu, kalıcı olmayan dosyalar ve IPC için önerilir. Kalıcı dosyalarla çalışmak için rasgele erişim görünümleri tercih edilir.  
  
 Bellek eşlenen dosyalara işletim sisteminin bellek yöneticisi aracılığıyla erişilir, böylece dosya otomatik olarak birkaç sayfaya bölünür ve gerektiğinde erişilir. Bellek yönetimini kendiniz halletmek zorunda değilsin.  
  
 Aşağıdaki resimde, birden çok işlemde aynı bellek eşlenen dosyada birden çok ve çakışan görünümnasıl olabilir.

 Aşağıdaki resim, bellek eşlenen bir dosyaya birden çok ve üst üste gelen görünümleri gösterir:  
  
 ![Eşlenen bir&#45;bellekte görünümleri gösteren ekran görüntüsü.](./media/memory-mapped-files/memory-map-persist-file.png)  
  
## <a name="programming-with-memory-mapped-files"></a>Bellek Eşlenen Dosyalarla Programlama  
 Aşağıdaki tablo, bellek eşlenen dosya nesnelerini ve üyelerini kullanmak için bir kılavuz sağlar.  
  
|Görev|Kullanılacak yöntemler veya özellikler|  
|----------|----------------------------------|  
|Diskteki <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> bir dosyadan kalıcı bellek eşlenen dosyayı temsil eden bir nesne elde etmek için.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>Yöntem.|  
|Kalıcı olmayan <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> bellek eşlenen dosyayı temsil eden bir nesne elde etmek için (diskteki bir dosyayla ilişkili değildir).|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>Yöntem.<br /><br /> - veya -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>Yöntem.|  
|Varolan <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> bellek eşlenen bir dosyanın nesnesini elde etmek için (kalıcı veya kalıcı olmayan).|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType>Yöntem.|  
|Bellek eşlenen dosyaya sırayla erişilen bir görünüm için bir <xref:System.IO.UnmanagedMemoryStream> nesne elde etmek için.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType>Yöntem.|  
|Bellek eşlenen fie rasgele bir erişim görünümü için bir <xref:System.IO.UnmanagedMemoryAccessor> nesne elde etmek için.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType>Yöntem.|  
|Yönetilmeyen <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> kodla kullanılacak bir nesne elde etmek için.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType>Özellik.<br /><br /> - veya -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType>Özellik.<br /><br /> - veya -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType>Özellik.|  
|Bir görünüm oluşturulana kadar bellek ayırmayı geciktirmek için (yalnızca kalıcı olmayan dosyalar).<br /><br /> (Geçerli sistem sayfa boyutunu belirlemek <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> için özelliği kullanın.)|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A><xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> değeri ile yöntem.<br /><br /> - veya -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A>parametre olarak <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> numaralandırma yöntemleri.|  
  
### <a name="security"></a>Güvenlik  
 Bir parametre olarak numaralandırma almak <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> aşağıdaki yöntemleri kullanarak, bellek eşlenen bir dosya oluştururken erişim haklarını uygulayabilirsiniz:  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>  
  
 Parametre <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> olarak alan yöntemleri kullanarak varolan bellek eşlenen bir dosyayı açmak için erişim haklarını belirtebilirsiniz.  
  
 Ayrıca, önceden tanımlanmış <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> erişim kuralları içeren bir nesne ekleyebilirsiniz.  
  
 Bellek eşlenen bir dosyaya yeni veya değiştirilmiş erişim <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> kuralları uygulamak için yöntemi kullanın. Varolan bir dosyadan erişim veya denetim <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> kuralları almak için yöntemi kullanın.  
  
## <a name="examples"></a>Örnekler  
  
### <a name="persisted-memory-mapped-files"></a>Kalıcı Bellek Eşlenen Dosyalar  
 Yöntemler, <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> diskteki varolan bir dosyadan bellek eşlenen bir dosya oluşturur.  
  
 Aşağıdaki örnek, son derece büyük bir dosyanın bir bölümünün bellek eşlenmiş görünümünü oluşturur ve bir bölümünü manipüle eder.  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/vb/program.vb#1)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

 Aşağıdaki örnek, başka bir işlem için aynı bellek eşlenen dosyayı açar.  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/vb/program.vb#1)]  
  
### <a name="non-persisted-memory-mapped-files"></a>Kalıcı Olmayan Bellek Eşlenen Dosyalar  
 Ve <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> yöntemler, diskteki varolan bir dosyaya eşlenmemiş bellek eşlenmiş bir dosya oluşturur.  
  
 Aşağıdaki örnek, bellek eşlenen bir dosyaya Boolean değerlerini yazan üç ayrı işlemden (konsol uygulamaları) oluşur. Aşağıdaki eylem sırası oluşur:  
  
1. `Process A`bellek eşlenen dosyayı oluşturur ve bir değer yazar.  
  
2. `Process B`bellek eşlenen dosyayı açar ve bir değer yazar.  
  
3. `Process C`bellek eşlenen dosyayı açar ve bir değer yazar.  
  
4. `Process A`bellek eşlenen dosyadaki değerleri okur ve görüntüler.  
  
5. Bellek `Process A` eşlenen dosya ile tamamlandıktan sonra, dosya hemen çöp toplama tarafından geri alınır.  
  
 Bu örneği çalıştırmak için aşağıdakileri yapın:  
  
1. Uygulamaları derleyin ve üç Komut İstemi penceresi açın.  
  
2. İlk Komut İstemi penceresinde `Process A`çalıştırın.  
  
3. İkinci Komut İstemi penceresinde `Process B`çalıştırın.  
  
4. Geri `Process A` dön ve ENTER tuşuna basın.  
  
5. Üçüncü Komut İstemi penceresinde, çalıştırın. `Process C`  
  
6. Geri `Process A` dön ve ENTER tuşuna basın.  
  
 Çıktıaşağıdaki `Process A` gibidir:  
  
```console  
Start Process B and press ENTER to continue.  
Start Process C and press ENTER to continue.  
Process A says: True  
Process B says: False  
Process C says: True  
```  
  
 **Süreç A**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/vb/program.vb#1)]  
  
 **Süreç B**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/vb/program.vb#1)]  
  
 **İşlem C**  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/vb/program.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dosya ve Akış G/Ç'si](../../../docs/standard/io/index.md)
