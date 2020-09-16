---
title: Bellek Eşlemeli Dosyalar
description: Sanal bellekte dosya içeriğini içeren ve uygulamaların dosyayı doğrudan belleğe yazarak değiştirmesine izin veren, .NET 'teki bellek eşlemeli dosyaları keşfedelim.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- memory-mapped files
- inter-process communication
ms.assetid: a483d1b5-64aa-45b6-86ef-11b859f7f02e
ms.openlocfilehash: 74d821aff8308618f7c0efeb1b453db8214b877e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555952"
---
# <a name="memory-mapped-files"></a>Bellek Eşlemeli Dosyalar
Bellek eşlemeli bir dosya, sanal bellekteki bir dosyanın içeriğini içerir. Bir dosya ve bellek alanı arasındaki bu eşleme, birden çok işlem dahil olmak üzere bir uygulamanın, dosyayı okuyup doğrudan belleğe yazarak değiştirmesini sağlar. .NET Framework 4 ' te başlayarak, yerel Windows işlevlerinin bellek eşlemeli dosyaları [yönetme](/previous-versions/ms810613(v=msdn.10))bölümünde açıklandığı gibi, aynı şekilde bellek eşlemeli dosyalara erişmek için yönetilen kodu kullanabilirsiniz.  
  
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
  
 ![Bir bellek&#45;eşlenmiş dosyanın görünümlerini gösteren ekran görüntüsü.](./media/memory-mapped-files/memory-map-persist-file.png)  
  
## <a name="programming-with-memory-mapped-files"></a>Bellek eşlemeli dosyalarla programlama  
 Aşağıdaki tabloda, bellek eşlemeli dosya nesnelerini ve bunların üyelerini kullanmaya yönelik bir kılavuz verilmiştir.  
  
|Görev|Kullanılacak yöntemler veya Özellikler|  
|----------|----------------------------------|  
|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile>Diskteki bir dosyanın kalıcı bir bellek eşlemeli dosyasını temsil eden bir nesne elde etmek için.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType> yöntemidir.|  
|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile>Kalıcı olmayan bir bellek eşlemeli dosyayı temsil eden bir nesne almak için (diskteki bir dosya ile ilişkilendirilmemiş).|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType> yöntemidir.<br /><br /> - veya -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType> yöntemidir.|  
|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile>Var olan bir bellek eşlemeli dosyanın bir nesnesini almak için (kalıcı veya kalıcı olmayan).|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType> yöntemidir.|  
|<xref:System.IO.UnmanagedMemoryStream>Sıralı olarak erişilen bir görünüm için bir nesneyi bellek eşlemeli dosyaya almak için.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType> yöntemidir.|  
|<xref:System.IO.UnmanagedMemoryAccessor>Rastgele erişim görünümü için bir nesneyi bellek eşlemeli bir dosyasına almak için.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType> yöntemidir.|  
|<xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle>Yönetilmeyen kodla kullanılacak bir nesne elde etmek için.|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType> özelliði.<br /><br /> - veya -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> özelliði.<br /><br /> - veya -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> özelliði.|  
|Bir görünüm oluşturuluncaya kadar bellek ayırmayı geciktirmek için (yalnızca kalıcı olmayan dosyalar).<br /><br /> (Geçerli sistem sayfa boyutunu anlamak için, <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> özelliğini kullanın.)|<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> değeri olan Yöntem <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> .<br /><br /> - veya -<br /><br /> <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A><xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions>parametre olarak sabit listesi olan Yöntemler.|  
  
### <a name="security"></a>Güvenlik  
 Bir sabit listesini parametre olarak alan aşağıdaki yöntemleri kullanarak, bellek eşlemeli bir dosya oluştururken erişim hakları uygulayabilirsiniz <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> :  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>  
  
 Bir <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> parametre olarak alan yöntemleri kullanarak, var olan bir bellek eşlemeli dosyayı açmaya yönelik erişim hakları belirtebilirsiniz <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> .  
  
 Ayrıca, <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> önceden tanımlanmış erişim kuralları içeren bir nesne ekleyebilirsiniz.  
  
 Bellek eşlemeli bir dosyaya yeni veya değiştirilmiş erişim kuralları uygulamak için <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> yöntemini kullanın. Var olan bir dosyadan erişim veya denetim kuralları almak için <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> yöntemini kullanın.  
  
## <a name="examples"></a>Örnekler  
  
### <a name="persisted-memory-mapped-files"></a>Kalıcı bellekle eşlenen dosyalar  
 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A>Yöntemler diskte var olan bir dosyadan bellek eşlemeli bir dosya oluşturur.  
  
 Aşağıdaki örnek, son derece büyük bir dosyanın bir bölümünün bellek eşlemeli bir görünümünü oluşturur ve bir kısmını yönetir.  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/vb/program.vb#1)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

 Aşağıdaki örnek, başka bir işlem için aynı bellek eşlemeli dosyayı açar.  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/vb/program.vb#1)]  
  
### <a name="non-persisted-memory-mapped-files"></a>Kalıcı olmayan bellekle eşlenen dosyalar  
 <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A>Ve <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> yöntemleri, diskte var olan bir dosyayla eşlenmemiş bir bellek eşlemeli dosya oluşturur.  
  
 Aşağıdaki örnek, bellek eşlemeli bir dosyaya Boole değerleri yazan üç ayrı işlem (konsol uygulaması) içerir. Aşağıdaki eylem sırası oluşur:  
  
1. `Process A` bellekle eşlenen dosyayı oluşturur ve ona bir değer yazar.  
  
2. `Process B` bellekle eşlenen dosyayı açar ve bir değer yazar.  
  
3. `Process C` bellekle eşlenen dosyayı açar ve bir değer yazar.  
  
4. `Process A` bellek eşlemeli dosyadaki değerleri okur ve görüntüler.  
  
5. `Process A`Bellek eşlemeli dosyayla bittikten sonra, dosya çöp toplama tarafından hemen geri kazanılır.  
  
 Bu örneği çalıştırmak için şunları yapın:  
  
1. Uygulamaları derleyin ve üç komut Istemi penceresi açın.  
  
2. İlk komut Istemi penceresinde komutunu çalıştırın `Process A` .  
  
3. İkinci komut Istemi penceresinde komutunu çalıştırın `Process B` .  
  
4. Öğesine dönüp `Process A` ENTER tuşuna basın.  
  
5. Üçüncü komut Istemi penceresinde komutunu çalıştırın `Process C` .  
  
6. Öğesine dönüp `Process A` ENTER tuşuna basın.  
  
 Çıkışı aşağıdaki gibidir `Process A` :  
  
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

- [Dosya ve akış g/ç](index.md)
