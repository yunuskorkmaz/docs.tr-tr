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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348941"
---
# <a name="basics-of-net-framework-file-io-and-the-file-system-visual-basic"></a>Dosya Sistemi ve .NET Framework Dosyası G/Ç ile İlgili Temel Bilgiler (Visual Basic)

<xref:System.IO> ad alanındaki sınıflar, sürücüler, dosyalar ve dizinler ile çalışmak için kullanılır.

<xref:System.IO> ad alanı, dosyaları ve dizinleri işleyen .NET Framework işlevselliği sağlayan <xref:System.IO.File> ve <xref:System.IO.Directory> sınıflarını içerir. Bu nesnelerin yöntemleri statik veya paylaşılan Üyeler olduğundan, bunları önce sınıfın bir örneğini oluşturmadan doğrudan kullanabilirsiniz. Bu sınıflarla ilişkili, `My` özelliğin kullanıcılarına tanıdık olacak <xref:System.IO.FileInfo> ve <xref:System.IO.DirectoryInfo> sınıflarıdır. Bu sınıfları kullanmak için, etkilenen kodun başına `Imports` deyimleriyle birlikte adları tam olarak nitelemeniz veya uygun ad alanlarını içeri aktarmanız gerekir. Daha fazla bilgi için bkz. [Imports açıklaması (.net ad alanı ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).

> [!NOTE]
> Bu bölümdeki diğer konular, sürücüler, dosyalar ve dizinler ile çalışmak için `System.IO` sınıfları yerine `My.Computer.FileSystem` nesnesini kullanır. `My.Computer.FileSystem` nesne öncelikle Visual Basic programlarında kullanılmak üzere tasarlanmıştır. `System.IO` sınıfları, Visual Basic dahil .NET Framework destekleyen herhangi bir dil tarafından kullanılmaya yöneliktir.

## <a name="definition-of-a-stream"></a>Akışın tanımı

.NET Framework, dosyaları okumayı ve dosyalara yazmayı desteklemek için akışları kullanır. Bir akışı, başlangıcı ve bitişi olan ve imlecin akıştaki geçerli konumu gösterdiği bir ardışık veri kümesi olarak düşünebilirsiniz.

![İmleç, FILESTREAM içindeki geçerli konumu gösterir.](./media/basics-of-net-framework-file-io-and-the-file-system/filestream-cursor-position.gif)

## <a name="stream-operations"></a>Akış Işlemleri

Akışta bulunan veriler bellekten, bir dosyadan veya TCP/IP yuvalarından gelebilir. Akışlar, bunlara uygulanabilen temel işlemlere sahiptir:

- **Okunuyor**. Akıştan bir dize veya bayt dizisi gibi bir veri yapısına veri aktarımı yapabilirsiniz.

- **Yazma**. Bir akışa yazabilir, verileri bir veri kaynağından akışa aktarabilirsiniz.

- **Aranıyor**. Akıştaki konumunuzu sorgulayabilir ve değiştirebilirsiniz.

Daha fazla bilgi için bkz. [akış oluşturma](../../../../standard/io/composing-streams.md).

## <a name="types-of-streams"></a>Akış türleri

.NET Framework bir akış, diğer tüm akışlar için soyut sınıfı oluşturan <xref:System.IO.Stream> sınıfı tarafından temsil edilir. <xref:System.IO.Stream> sınıfının bir örneğini doğrudan oluşturamazsınız, ancak uyguladığı sınıflardan birini kullanmanız gerekir.

Birçok tür akış vardır ancak dosya girişi/çıkışı (g/ç) ile çalışma amaçları için en önemli türler, dosyaları okuma ve yazma ve yalıtılmış depolamada dosya ve dizin oluşturmak için bir yol sağlayan <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> sınıfı olan <xref:System.IO.FileStream> sınıfıdır. Dosya g/ç ile çalışırken kullanılabilecek diğer akışlar şunlardır:

- <xref:System.IO.BufferedStream>

- <xref:System.Security.Cryptography.CryptoStream>

- <xref:System.IO.MemoryStream>

- <xref:System.Net.Sockets.NetworkStream>.

Aşağıdaki tabloda, bir akışta yaygın olarak gerçekleştirilen görevler listelenmiştir:

|Bitiş|Bkz.|
|---|---|
|Veri dosyasına okuma ve yazma|[Nasıl yapılır: Yeni Oluşturulan bir Veri Dosyasını Okuma ve Dosyaya Yazma](../../../../standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)|
|Dosyadan metin oku|[Nasıl yapılır: Dosyadan Metin Okuma](../../../../standard/io/how-to-read-text-from-a-file.md)|
|Bir dosyaya metin yaz|[Nasıl yapılır: Bir Dosyaya Metin Yazma](../../../../standard/io/how-to-write-text-to-a-file.md)|
|Dizeden karakterleri okuma|[Nasıl yapılır: Dizeden Karakterleri Okuma](../../../../standard/io/how-to-read-characters-from-a-string.md)|
|Bir dizeye karakter yazma|[Nasıl yapılır: Bir Dizeye Karakter Yazma](../../../../standard/io/how-to-write-characters-to-a-string.md)|
|Verileri şifreleme|[Veri Şifreleme](../../../../standard/security/encrypting-data.md)|
|Verilerin şifresini çözme|[Verilerin Şifresini Çözme](../../../../standard/security/decrypting-data.md)|

## <a name="file-access-and-attributes"></a>Dosya erişimi ve öznitelikleri

<xref:System.IO.FileStream> sınıfının oluşturucuları tarafından kullanılan bayrakları içeren <xref:System.IO.FileAccess>, <xref:System.IO.FileMode>ve <xref:System.IO.FileShare> Numaralandırmalarla dosyaların nasıl oluşturulduğunu, açılacağını ve paylaşıldığını denetleyebilirsiniz. Örneğin, yeni bir <xref:System.IO.FileStream>açtığınızda veya oluşturduğunuzda, <xref:System.IO.FileMode> numaralandırması dosyanın ekleme için açılıp açılmadığını, belirtilen dosya mevcut değilse yeni bir dosyanın oluşturulup oluşturulmadığını, dosyanın üzerine yazılıp yazılmayacağını belirtmenize izin verir.

<xref:System.IO.FileAttributes> numaralandırması, dosyaya özgü bilgilerin toplanmasında izin vermez. <xref:System.IO.FileAttributes> numaralandırması, sıkıştırılmış, şifreli, gizli, salt okunurdur, arşiv, dizin, sistem dosyası veya geçici bir dosya gibi dosyanın depolanmış özniteliklerini döndürür.

Aşağıdaki tabloda dosya erişimi ve dosya öznitelikleri içeren görevler listelenmiştir:

|Bitiş|Bkz.|
|---|---|
|Açın ve bir günlük dosyasına metin ekleyin|[Nasıl yapılır: Günlük Dosyasını Açma ve Sonuna Ekleme](../../../../standard/io/how-to-open-and-append-to-a-log-file.md)|
|Bir dosyanın özniteliklerini belirleme|<xref:System.IO.FileAttributes>|

## <a name="file-permissions"></a>Dosya Izinleri

Dosya ve dizinlere erişimin denetlenmesi <xref:System.Security.Permissions.FileIOPermission> sınıfıyla yapılabilir. Bu, varsayılan olarak, ASP.NET ve .NET Framework yüklemelerinin bir parçası olarak oluşturulan ASPNET adlı özel bir yerel kullanıcı hesabı bağlamında çalıştırılan Web Forms ile çalışan geliştiriciler için özellikle önemli olabilir. Böyle bir uygulama bir kaynağa erişim istediğinde, ASPNET Kullanıcı hesabının sınırlı izinleri vardır ve bu, kullanıcının bir Web uygulamasından bir dosyaya yazma gibi eylemler gerçekleştirmesini engelleyebilir. Daha fazla bilgi için bkz. <xref:System.Security.Permissions.FileIOPermission>.

## <a name="isolated-file-storage"></a>Yalıtılmış dosya depolaması

Yalıtılmış depolama, Kullanıcı veya kodun gerekli izinlere sahip olabileceği dosyalarla çalışırken oluşturulan sorunları çözmeye çalışır. Yalıtılmış depolama, her kullanıcıya bir veya daha fazla mağaza içerebilen bir veri bölmesi atar. Depolar, Kullanıcı ve derleme tarafından birbirinden yalıtılmış. Yalnızca bir depoyu oluşturan kullanıcı ve derlemeye erişimi vardır. Bir mağaza, sanal dosya sistemi olarak çalışır — bir mağaza içinde dizin ve dosya oluşturabilir ve yönetebilirsiniz.

Aşağıdaki tabloda, yalıtılmış dosya depolama ile yaygın olarak ilişkili görevler listelenmiştir.

|Bitiş|Bkz.|
|---|---|
|Yalıtılmış mağaza oluşturma|[Nasıl yapılır: Yalıtılmış Depolama için Depoları Alma](../../../../standard/io/how-to-obtain-stores-for-isolated-storage.md)|
|Yalıtılmış depoları listeleme|[Nasıl yapılır: Yalıtılmış Depolama için Depoları Numaralandırma](../../../../standard/io/how-to-enumerate-stores-for-isolated-storage.md)|
|Yalıtılmış bir depoyu silme|[Nasıl yapılır: Yalıtılmış Depolamadaki Depoları Silme](../../../../standard/io/how-to-delete-stores-in-isolated-storage.md)|
|Yalıtılmış depolamada bir dosya veya dizin oluşturma|[Nasıl yapılır: Yalıtılmış Depolamada Dosya ve Dizinler Oluşturma](../../../../standard/io/how-to-create-files-and-directories-in-isolated-storage.md)|
|Yalıtılmış depolamada dosya bulma|[Nasıl yapılır: Yalıtılmış Depolamada Mevcut Dosya ve Dizinleri Bulma](../../../../standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md)|
|Yalıtılmış depolamada bir dosyadan okuma veya yazma|[Nasıl yapılır: Yalıtılmış Depolamadaki Dosyaları Okuma ve Yazma](../../../../standard/io/how-to-read-and-write-to-files-in-isolated-storage.md)|
|Yalıtılmış depolamada bir dosyayı veya dizini silme|[Nasıl yapılır: Yalıtılmış Depolamadaki Dosya ve Dizinleri Silme](../../../../standard/io/how-to-delete-files-and-directories-in-isolated-storage.md)|

## <a name="file-events"></a>Dosya olayları

<xref:System.IO.FileSystemWatcher> bileşeni, sisteminizdeki veya ağ erişiminizin olduğu herhangi bir bilgisayardaki dosya ve dizinlerdeki değişiklikler için izlemenize olanak sağlar. Örneğin, bir dosya değiştirilirse, kullanıcının değişikliğin gerçekleştiğinden ilgili bir uyarı göndermek isteyebilirsiniz. Değişiklikler gerçekleştiğinde, bir veya daha fazla olay tetiklenir, bir arabellekte depolanır ve işlemek için <xref:System.IO.FileSystemWatcher> bileşenine geçirir.

## <a name="see-also"></a>Ayrıca bkz.

- [Akışlar Oluşturma](../../../../standard/io/composing-streams.md)
- [Dosya ve Akış G/Ç'si](../../../../standard/io/index.md)
- [Zaman Uyumsuz Dosya G/Ç](../../../../standard/io/asynchronous-file-i-o.md)
- [.NET Framework dosya g/ç 'de kullanılan sınıflar ve dosya sistemi (Visual Basic)](../../../../visual-basic/developing-apps/programming/drives-directories-files/classes-used-in-net-framework-file-io-and-the-file-system.md)
