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
ms.openlocfilehash: add109e285dfc435a3d4fd7753fb647e28a6a2fd
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706575"
---
# <a name="memory-mapped-files"></a>Bellek Eşlemeli Dosyalar
Bellek eşlemeli bir dosya, sanal bellekteki bir dosyanın içeriğini içerir. Bir dosya ve bellek alanı arasındaki bu eşleme, birden çok işlem dahil olmak üzere bir uygulamanın, dosyayı okuyup doğrudan belleğe yazarak değiştirmesini sağlar. .NET Framework 4 ' te başlayarak, yerel Windows işlevlerinin bellek eşlemeli dosyaları [yönetme](https://docs.microsoft.com/previous-versions/ms810613(v=msdn.10))bölümünde açıklandığı gibi, aynı şekilde bellek eşlemeli dosyalara erişmek için yönetilen kodu kullanabilirsiniz.  
  
 İki tür bellekle eşlenmiş dosya vardır:  
  
- Kalıcı bellekle eşlenen dosyalar  
  
     Kalıcı dosyalar, bir diskteki kaynak dosyayla ilişkili bellekle eşleştirilmiş dosyalardır. Son işlem dosyayla çalışmayı bitirdiğinde, veriler diskteki kaynak dosyasına kaydedilir. Bellek eşlemeli bu dosyalar, son derece büyük kaynak dosyalarıyla çalışmak için uygundur.  
  
- Kalıcı olmayan bellekle eşlenen dosyalar  
  
     Kalıcı olmayan dosyalar, bir diskte bulunan bir dosya ile ilişkilendirilmemiş bellekle eşleştirilmiş dosyalardır. Son işlem dosyayla çalışmayı bitirdiğinde, veriler kaybolur ve dosya çöp toplama tarafından geri kazanılır. Bu dosyalar, işlemler arası iletişimler (IPC) için paylaşılan bellek oluşturmak üzere uygundur.  
  
## <a name="processes-views-and-managing-memory"></a>Belleği işleme, görüntüleme ve yönetme  
 Bellek eşlemeli dosyalar, birden çok işlem arasında paylaşılabilir. İşlemler, dosyayı oluşturan işlem tarafından atanan ortak bir ad kullanarak aynı bellek eşlemeli dosyayla eşlenir.  
  
 Bellek eşlemeli bir dosyayla çalışmak için, tüm bellek eşlemeli dosyanın veya bunun bir kısmının görünümünü oluşturmanız gerekir. Ayrıca, bellek eşlemeli dosyanın aynı kısmına birden fazla görünüm de oluşturabilirsiniz, böylece eşzamanlı bellek oluşturulabilir. İki görünümün eşzamanlı kalması için aynı bellek eşlemeli dosyadan oluşturulması gerekir.  
  
 Dosya, bellek eşleme için kullanılabilir (32 bitlik bir bilgisayarda 2 GB) uygulamanın mantıksal bellek alanının boyutundan fazlaysa, birden çok görünüm de gerekli olabilir.  
  
 İki tür görünüm vardır: akış erişim görünümü ve rastgele erişim görünümü. Bir dosyaya sıralı erişim için akış erişim görünümlerini kullanın; kalıcı olmayan dosyalar ve IPC için bu önerilir. Kalıcı dosyalarla çalışmaya yönelik rastgele erişim görünümleri tercih edilir.  
  
 Bellek eşlemeli dosyalara işletim sisteminin bellek Yöneticisi üzerinden erişilir, bu nedenle dosya otomatik olarak bir dizi sayfaya bölümlenir ve gerektiğinde erişilir. Bellek yönetimini kendiniz işlemek zorunda değilsiniz.  
  
 Aşağıdaki çizimde, birden çok işlemin aynı anda aynı bellek eşlemeli dosya için birden çok ve çakışan görünümler bulunabilir.

 Aşağıdaki görüntüde, bellek eşlemeli bir dosya için birden çok ve çakışan görünümler gösterilmektedir:  
  
 ![Bellek&#45;eşlemeli bir dosyanın görünümlerini gösteren ekran görüntüsü.](./media/memory-mapped-files/memory-map-persist-file.png)  
  
## <a name="programming-with-memory-mapped-files"></a>Bellek eşlemeli dosyalarla programlama  
 Aşağıdaki tabloda, bellek eşlemeli dosya nesnelerini ve bunların üyelerini kullanmaya yönelik bir kılavuz verilmiştir.  
  
|Görev|Kullanılacak yöntemler veya Özellikler|  
|----------|----------------------------------|  
|Diskteki bir dosyanın kalıcı bellek eşlemeli bir dosyasını temsil eden bir <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> nesnesi elde etmek için.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType> yöntemi.|  
|Kalıcı olmayan bir bellek eşlemeli dosyayı temsil eden bir <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> nesnesi elde etmek için (diskteki bir dosya ile ilişkilendirilmemiş).|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType> yöntemi.<br /><br /> - veya -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType> yöntemi.|  
|Mevcut bir bellek eşlemeli dosyanın <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> nesnesini almak için (kalıcı veya kalıcı olmayan).|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType> yöntemi.|  
|Sıralı olarak erişilen bir görünüm için bellek eşlemeli dosyaya <xref:System.IO.UnmanagedMemoryStream> nesne almak için.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType> yöntemi.|  
|Bellek eşlemeli bir dosyasına rastgele erişim görünümü için <xref:System.IO.UnmanagedMemoryAccessor> nesnesi elde etmek için.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType> yöntemi.|  
|Yönetilmeyen kod ile kullanmak üzere bir <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> nesnesi elde etmek için.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType> özelliği.<br /><br /> - veya -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> özelliği.<br /><br /> - veya -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> özelliği.|  
|Bir görünüm oluşturuluncaya kadar bellek ayırmayı geciktirmek için (yalnızca kalıcı olmayan dosyalar).<br /><br /> (Geçerli sistem sayfa boyutunu anlamak için <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> özelliğini kullanın.)|<xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> değerine sahip <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> yöntemi.<br /><br /> - veya -<br /><br /> parametre olarak <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> numaralandırması olan Yöntemler <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A>.|  
  
### <a name="security"></a>Güvenlik  
 Bir parametre olarak <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> numaralandırması alan aşağıdaki yöntemleri kullanarak, bellek eşlemeli bir dosya oluştururken erişim hakları uygulayabilirsiniz:  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>  
  
 Bir <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> parametresi olarak alan <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> yöntemlerini kullanarak, var olan bir bellek eşlemeli dosyayı açmak için erişim hakları belirtebilirsiniz.  
  
 Ayrıca, önceden tanımlanmış erişim kuralları içeren bir <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> nesnesi ekleyebilirsiniz.  
  
 Bellek eşlemeli bir dosyaya yeni veya değiştirilmiş erişim kuralları uygulamak için <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> yöntemini kullanın. Var olan bir dosyadan erişim veya denetim kuralları almak için <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> yöntemini kullanın.  
  
## <a name="examples"></a>Örnekler  
  
### <a name="persisted-memory-mapped-files"></a>Kalıcı bellekle eşlenen dosyalar  
 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> yöntemleri, diskteki mevcut bir dosyadan bellek eşlemeli bir dosya oluşturur.  
  
 Aşağıdaki örnek, son derece büyük bir dosyanın bir bölümünün bellek eşlemeli bir görünümünü oluşturur ve bir kısmını yönetir.  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/vb/program.vb#1)]  
  
 Aşağıdaki örnek, başka bir işlem için aynı bellek eşlemeli dosyayı açar.  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/vb/program.vb#1)]  
  
### <a name="non-persisted-memory-mapped-files"></a>Kalıcı olmayan bellekle eşlenen dosyalar  
 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> ve <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> yöntemleri, diskteki mevcut bir dosyayla eşlenmemiş bir bellek eşlemeli dosya oluşturur.  
  
 Aşağıdaki örnek, bellek eşlemeli bir dosyaya Boole değerleri yazan üç ayrı işlem (konsol uygulaması) içerir. Aşağıdaki eylem sırası oluşur:  
  
1. `Process A`, bellek eşlemeli dosyayı oluşturur ve ona bir değer yazar.  
  
2. `Process B` bellek eşlemeli dosyayı açar ve bir değer yazar.  
  
3. `Process C` bellek eşlemeli dosyayı açar ve bir değer yazar.  
  
4. `Process A`, bellek eşlemeli dosyadaki değerleri okur ve görüntüler.  
  
5. Bellek eşlemeli dosyayla `Process A` sona erdikten sonra, dosya çöp toplama tarafından hemen geri kazanılır.  
  
 Bu örneği çalıştırmak için şunları yapın:  
  
1. Uygulamaları derleyin ve üç komut Istemi penceresi açın.  
  
2. İlk komut Istemi penceresinde `Process A`' yi çalıştırın.  
  
3. İkinci komut Istemi penceresinde `Process B`' yi çalıştırın.  
  
4. `Process A` dönün ve ENTER tuşuna basın.  
  
5. Üçüncü komut Istemi penceresinde `Process C`' yi çalıştırın.  
  
6. `Process A` dönün ve ENTER tuşuna basın.  
  
 `Process A` çıkışı aşağıdaki gibidir:  
  
```console  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dosya ve Akış G/Ç'si](../../../docs/standard/io/index.md)
