---
title: Dosya Sistemi ve .NET Framework Dosyası G/Ç ile ilgili Temel Bilgiler
ms.date: 07/20/2015
helpviewer_keywords:
- file access, file I/O in Visual Basic
- file attributes, determining
- streams, fundamental operations
- file permissions
- streams
- streams, definition
ms.assetid: 49d837c0-cf28-416f-8606-4d83d7b479ef
ms.openlocfilehash: 5d60d0089d042c0be343c741c26de0b4b7778d6d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348941"
---
# <a name="basics-of-net-framework-file-io-and-the-file-system-visual-basic"></a>Dosya Sistemi ve .NET Framework Dosyası G/Ç ile İlgili Temel Bilgiler (Visual Basic)

<xref:System.IO> Ad alanındaki sınıflar sürücülerle, dosyalarla ve dizinlerle çalışmak için kullanılır.

Ad <xref:System.IO> alanı, <xref:System.IO.File> dosyaları <xref:System.IO.Directory> ve dizinleri manipüle eden .NET Framework işlevini sağlayan ve sınıfları içerir. Bu nesnelerin yöntemleri statik veya paylaşılan üyeler olduğundan, bunları önce sınıfın bir örneğini oluşturmadan doğrudan kullanabilirsiniz. Bu sınıflarla ilişkili <xref:System.IO.FileInfo> <xref:System.IO.DirectoryInfo> olan ve `My` özelliğin kullanıcılarına tanıdık gelecek olan sınıflar dır. Bu sınıfları kullanmak için, etkilenen kodun başına `Imports` deyimi(ler) ekleyerek adları tam olarak nitelemeniz veya uygun ad alanlarını almanız gerekir. Daha fazla bilgi [için, Bkz. İçerme Bildirimi (.NET Ad Alanı ve Türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).

> [!NOTE]
> Bu bölümdeki diğer `My.Computer.FileSystem` konular, `System.IO` sürücüler, dosyalar ve dizinlerle çalışmak için sınıflar yerine nesneyi kullanır. Nesne `My.Computer.FileSystem` öncelikle Visual Basic programlarında kullanılmak üzere tasarlanmıştır. `System.IO`sınıflar Visual Basic de dahil olmak üzere .NET Framework'u destekleyen herhangi bir dil tarafından kullanılmak üzere tasarlanmıştır.

## <a name="definition-of-a-stream"></a>Bir Akımın Tanımı

.NET Framework, dosyalardan okuma ve yazmayı desteklemek için akışlar kullanır. Bir akışı, başlangıcı ve sonu olan ve imlecin akıştaki geçerli konumu gösterdiği tek boyutlu bir bitişik veri kümesi olarak düşünebilirsiniz.

![İmleç dosya akışındaki geçerli konumu gösterir.](./media/basics-of-net-framework-file-io-and-the-file-system/filestream-cursor-position.gif)

## <a name="stream-operations"></a>Akış İşlemleri

Akışta bulunan veriler bellekten, dosyadan veya TCP/IP yuvasından gelebilir. Akışlar, bunlara uygulanabilecek temel işlemlere sahiptir:

- **Okuma**. Akıştan, akıştan verileri bir dize veya bayt dizisi gibi bir veri yapısına aktararak okuyabilirsiniz.

- **Yazma**. Bir veri kaynağından akışına veri aktarımı, bir akış akışın içine yazabilirsiniz.

- **Aradığınız**. Akıştaki konumunuz sorgulayabilir ve değiştirebilirsiniz.

Daha fazla bilgi için [Bkz.](../../../../standard/io/composing-streams.md)

## <a name="types-of-streams"></a>Akış Türleri

.NET Framework'de, bir akış, <xref:System.IO.Stream> diğer tüm akışlar için soyut sınıfı oluşturan sınıf tarafından temsil edilir. Sınıfın bir örneğini <xref:System.IO.Stream> doğrudan oluşturamazsınız, ancak uyguladığı sınıflardan birini kullanmanız gerekir.

Birçok akış türü vardır, ancak dosya girişi/çıktısı (I/O) ile çalışmak amacıyla, <xref:System.IO.FileStream> en önemli türler dosyalardan okuma ve yazma nın <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> bir yolunu sağlayan sınıf ve yalıtılmış depolama alanında dosya ve dizin oluşturmanın bir yolunu sağlayan sınıftır. Dosya G/Ç ile çalışırken kullanılabilecek diğer akışlar şunlardır:

- <xref:System.IO.BufferedStream>

- <xref:System.Security.Cryptography.CryptoStream>

- <xref:System.IO.MemoryStream>

- <xref:System.Net.Sockets.NetworkStream>.

Aşağıdaki tabloda, akışla sık karşılaşılan görevler listelenir:

|Alıcı|Bkz.|
|---|---|
|Veri dosyasını okuma ve yazma|[Nasıl yapılır: Yeni Oluşturulan bir Veri Dosyasını Okuma ve Dosyaya Yazma](../../../../standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)|
|Dosyadaki metni okuma|[Nasıl yapılır: Dosyadan Metin Okuma](../../../../standard/io/how-to-read-text-from-a-file.md)|
|Dosyaya metin yazma|[Nasıl yapılır: Bir Dosyaya Metin Yazma](../../../../standard/io/how-to-write-text-to-a-file.md)|
|Karakterleri dizeden okuma|[Nasıl yapılır: Dizeden Karakterleri Okuma](../../../../standard/io/how-to-read-characters-from-a-string.md)|
|Karakterleri bir dize yazma|[Nasıl yapılır: Bir Dizeye Karakter Yazma](../../../../standard/io/how-to-write-characters-to-a-string.md)|
|Verileri şifreleme|[Veri Şifreleme](../../../../standard/security/encrypting-data.md)|
|Verilerin şifresini çözme|[Verilerin Şifresini Çözme](../../../../standard/security/decrypting-data.md)|

## <a name="file-access-and-attributes"></a>Dosya Erişimi ve Öznitelikler

Dosyaların nasıl oluşturulduğunu, açıldığını <xref:System.IO.FileAccess>ve <xref:System.IO.FileMode> <xref:System.IO.FileShare> <xref:System.IO.FileStream> sınıfın oluşturucuları tarafından kullanılan bayrakları içeren , , ve sayısallaştırmalarla paylaşıldığını denetleyebilirsiniz. Örneğin, yeni <xref:System.IO.FileStream>bir , numaralandırma <xref:System.IO.FileMode> açtığınızda veya oluşturduğunuzda numaralandırma, dosyanın ek ekibe açılıp açılmadığını, belirtilen dosya yoksa yeni bir dosya oluşturulup oluşturulmadığını, dosyanın üzerine yazıp yazmadığını vb. belirtmenize olanak tanır.

Numaralandırma, <xref:System.IO.FileAttributes> dosyaya özgü bilgilerin toplanmasını sağlar. Numaralandırma, <xref:System.IO.FileAttributes> dosyanın sıkıştırılmış, şifrelenmiş, gizli, salt okunur, arşiv, dizin, sistem dosyası veya geçici bir dosya olması gibi depolanan özniteliklerini döndürür.

Aşağıdaki tabloda dosya erişimi ve dosya öznitelikleri içeren görevler listelenir:

|Alıcı|Bkz.|
|---|---|
|Günlük dosyasına metin açma ve ekle|[Nasıl yapılır: Günlük Dosyasını Açma ve Sonuna Ekleme](../../../../standard/io/how-to-open-and-append-to-a-log-file.md)|
|Dosyanın özniteliklerini belirleme|<xref:System.IO.FileAttributes>|

## <a name="file-permissions"></a>Dosya İzinleri

Dosyalara ve dizinlere erişimi denetleme <xref:System.Security.Permissions.FileIOPermission> sınıfıyla yapılabilir. Bu, varsayılan olarak ASP.NET ve .NET Framework yüklemelerinin bir parçası olarak oluşturulan ASPNET adlı özel bir yerel kullanıcı hesabı bağlamında çalışan Web Formları ile çalışan geliştiriciler için özellikle önemli olabilir. Böyle bir uygulama bir kaynağa erişim istediğinde, ASPNET kullanıcı hesabının sınırlı izinleri vardır ve bu da kullanıcının bir Web uygulamasından bir dosyaya yazma gibi eylemleri gerçekleştirmesini engelleyebilir. Daha fazla bilgi için bkz. <xref:System.Security.Permissions.FileIOPermission>.

## <a name="isolated-file-storage"></a>Yalıtılmış Dosya Depolama

Yalıtılmış depolama, kullanıcının veya kodun gerekli izinlerden yoksun olabileceği dosyalarla çalışırken oluşturulan sorunları çözme girişimidir. Yalıtılmış depolama, her kullanıcıya bir veya daha fazla depo tutabilen bir veri bölmesi atar. Mağazalar kullanıcı ve montaj tarafından birbirinden izole edilebilir. Yalnızca mağaza yı oluşturan kullanıcı ve derleme, bu mağazaya erişebilir. Bir mağaza, dizinler ve dosyalar oluşturup işleyebilirsiniz bir mağaza içinde tam bir sanal dosya sistemi gibi davranır.

Aşağıdaki tabloda, sık sık yalıtılmış dosya depolamaile ilişkili görevler listelenir.

|Alıcı|Bkz.|
|---|---|
|Yalıtılmış bir mağaza oluşturma|[Nasıl yapılır: Yalıtılmış Depolama için Depoları Alma](../../../../standard/io/how-to-obtain-stores-for-isolated-storage.md)|
|İzole mağazaları sayısal|[Nasıl yapılır: Yalıtılmış Depolama için Depoları Numaralandırma](../../../../standard/io/how-to-enumerate-stores-for-isolated-storage.md)|
|Yalıtılmış bir depoyu silme|[Nasıl yapılır: Yalıtılmış Depolamadaki Depoları Silme](../../../../standard/io/how-to-delete-stores-in-isolated-storage.md)|
|Yalıtılmış depolama alanında dosya veya dizin oluşturma|[Nasıl yapılır: Yalıtılmış Depolamada Dosya ve Dizinler Oluşturma](../../../../standard/io/how-to-create-files-and-directories-in-isolated-storage.md)|
|Yalıtılmış depolama alanında dosya bulma|[Nasıl yapılır: Yalıtılmış Depolamada Mevcut Dosya ve Dizinleri Bulma](../../../../standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md)|
|Yalıtılmış depolama alanında dosyadan okuma veya yazma|[Nasıl yapılır: Yalıtılmış Depolamadaki Dosyaları Okuma ve Yazma](../../../../standard/io/how-to-read-and-write-to-files-in-isolated-storage.md)|
|Yalıtılmış depolama alanında bir dosyayı veya dizini silme|[Nasıl yapılır: Yalıtılmış Depolamadaki Dosya ve Dizinleri Silme](../../../../standard/io/how-to-delete-files-and-directories-in-isolated-storage.md)|

## <a name="file-events"></a>Dosya Etkinlikleri

Bileşen, <xref:System.IO.FileSystemWatcher> sisteminizdeki veya ağ erişimine sahip olduğunuz herhangi bir bilgisayarda dosya ve dizindeğişiklikleri için izlemenize olanak tanır. Örneğin, bir dosya değiştirilirse, kullanıcıya değişikliğin gerçekleştiğine dair bir uyarı göndermek isteyebilirsiniz. Değişiklikler oluştuğunda, bir veya daha fazla olay yükseltilir, arabellekte depolanır ve işlenmek üzere <xref:System.IO.FileSystemWatcher> bileşene teslim edilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Akışlar Oluşturma](../../../../standard/io/composing-streams.md)
- [Dosya ve Akış G/Ç'si](../../../../standard/io/index.md)
- [Zaman Uyumsuz Dosya G/Ç](../../../../standard/io/asynchronous-file-i-o.md)
- [Dosya Sistemi ve .NET Framework Dosyası G/Ç'de Kullanılan Sınıflar (Visual Basic)](../../../../visual-basic/developing-apps/programming/drives-directories-files/classes-used-in-net-framework-file-io-and-the-file-system.md)
