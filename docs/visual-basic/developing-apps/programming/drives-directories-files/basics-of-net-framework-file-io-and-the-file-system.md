---
title: Dosya Sistemi ve .NET Framework Dosyası G/Ç ile İlgili Temel Bilgiler (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- file access, file I/O in Visual Basic
- file attributes, determining
- streams, fundamental operations
- file permissions
- streams
- streams, definition
ms.assetid: 49d837c0-cf28-416f-8606-4d83d7b479ef
ms.openlocfilehash: 365c3b8f0aa107f7106e0c83d1fa60de6f4903f2
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57674568"
---
# <a name="basics-of-net-framework-file-io-and-the-file-system-visual-basic"></a>Dosya Sistemi ve .NET Framework Dosyası G/Ç ile İlgili Temel Bilgiler (Visual Basic)

Sınıflar <xref:System.IO> ad alanı, sürücüler, dosyalar ve dizinler ile çalışmak için kullanılır.

<xref:System.IO> Ad alanı içerir <xref:System.IO.File> ve <xref:System.IO.Directory> sağlayan sınıflar [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] dosyalar ve dizinler yöneten işlevselliği. Nedeni bu nesnelerin yöntemleri statik veya paylaşılan üyeler, bunları doğrudan sınıfının bir örneğini ilk oluşturma olmadan kullanabilirsiniz. Bu sınıf ile ilişkili olan <xref:System.IO.FileInfo> ve <xref:System.IO.DirectoryInfo> kullanıcıları için tanıdık gelecektir sınıflarını `My` özelliği. Bu sınıfların kullanmak için tam adları nitelemeniz veya gerekir uygun ad alanlarını dahil ederek içeri aktarma `Imports` başında bir deyim etkilenen kod. Daha fazla bilgi için [Imports deyimi (.NET Namespace ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).

> [!NOTE]
> Bu diğer konulara bölümünde kullanım `My.Computer.FileSystem` yerine nesne `System.IO` sürücüsü, dosyalar ve dizinler ile çalışmak için sınıflar. `My.Computer.FileSystem` Nesne öncelikle Visual Basic programlarda kullanmak için tasarlanmıştır. `System.IO` sınıflar, destekleyen herhangi bir dilde kullanıma yöneliktir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], Visual Basic dahil.

## <a name="definition-of-a-stream"></a>Bir Stream tanımı

[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Okuma ve dosyalara yazma desteklemek üzere akışları kullanır. Bir akışı, sahip olduğu bir başlangıç ve bitiş tarihi ve burada stream'de geçerli konum bir imleç gösterir bitişik veri tek boyutlu bir dizi olarak düşünebilirsiniz.

![İmleç akışında geçerli konumunu gösterir. ](../../../../visual-basic/developing-apps/programming/drives-directories-files/media/filestream.gif "FILESTREAM")

## <a name="stream-operations"></a>Stream işlemleri

İş akışında yer alan verileri, bellek, bir dosya ya da bir TCP/IP yuva gelebilir. Akışlar için uygulanabilir temel işlemler vardır:

- **Okuma**. Bir akıştan bir dize veya bayt dizisi gibi bir veri yapısı içine bir akıştan veri aktarma okuyabilirsiniz.

- **Yazma**. Akışa bir veri kaynağından veri aktarırken bir akışa yazabilirsiniz.

- **Aramayı**. Sorgu ve akışta, konumu değiştirebilirsiniz.

Daha fazla bilgi için [oluşturma akışları](../../../../standard/io/composing-streams.md).

## <a name="types-of-streams"></a>Akış türleri

İçinde [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], bir akış tarafından temsil edilen <xref:System.IO.Stream> diğer akışlar için soyut sınıf forms sınıfı. Bir örneğini doğrudan oluşturamazsınız <xref:System.IO.Stream> sınıfı, ancak bunu uygulayan sınıflardan birini kullanmanız gerekir.

Birçok tür akış vardır, ancak dosya giriş/çıkış ile (g/ç) çalışma amacıyla, en önemli türleri <xref:System.IO.FileStream> okuma ve dosyalara yazmak için bir yol sağlayan bir sınıf ve <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> dosyaları oluşturmak için bir yol sağlar sınıfını ve Yalıtılmış Depolama dizinleri. Dosya g/ç ile çalışırken kullanılabilir diğer akışlar şunlardır:

- <xref:System.IO.BufferedStream>

- <xref:System.Security.Cryptography.CryptoStream>

- <xref:System.IO.MemoryStream>

- <xref:System.Net.Sockets.NetworkStream>.

Aşağıdaki tabloda stream ile yaygın olarak gerçekleştirilen görevlerdir listelenmektedir:

|Bitiş|Bkz. |
|---|---|
|İçin bir veri dosyasını okuma ve yazma|[Nasıl yapılır: Okuma ve yeni oluşturulan veri dosyasına yazma](../../../../standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)|
|Bir dosyadan metin okuma|[Nasıl yapılır: Bir dosyadan metin okuma](../../../../standard/io/how-to-read-text-from-a-file.md)|
|Bir dosyaya metin yazma|[Nasıl yapılır: Bir dosyaya metin yazma](../../../../standard/io/how-to-write-text-to-a-file.md)|
|Dizeden karakterleri okuma|[Nasıl yapılır: Dizeden karakterleri okuma](../../../../standard/io/how-to-read-characters-from-a-string.md)|
|Bir dizeye karakter yazma|[Nasıl yapılır: Bir dizeye karakter yazma](../../../../standard/io/how-to-write-characters-to-a-string.md)|
|Verileri şifrele|[Veri Şifreleme](../../../../standard/security/encrypting-data.md)|
|Verilerin şifresini|[Verilerin Şifresini Çözme](../../../../standard/security/decrypting-data.md)|

## <a name="file-access-and-attributes"></a>Dosya erişimi ve öznitelikler

Nasıl dosyaları, açık olan paylaşılan oluşturulduğunu ve Denetim <xref:System.IO.FileAccess>, <xref:System.IO.FileMode>, ve <xref:System.IO.FileShare> Oluşturucuları tarafından kullanılan bayrak içeren sabit listeleri <xref:System.IO.FileStream> sınıfı. Örneğin, açtığınızda veya yeni bir <xref:System.IO.FileStream>, <xref:System.IO.FileMode> numaralandırma, dosya ekleme için açılıp açılmayacağını belirtilen dosya yoksa, dosyanın üzerine olmadığını yeni dosya oluşturulduğunda olup olmadığını belirlemek için ve benzeri sağlar.

<xref:System.IO.FileAttributes> Dosya özgü bilgileri toplamayı etkinleştirir. <xref:System.IO.FileAttributes> Sıkıştırılmış şifrelenmiş, gizli, salt okunur olup, bir arşiv, bir dizin, bir sistem dosyası veya geçici bir dosya gibi depolanan dosya özniteliklerini sabit listesi döndürür.

Aşağıdaki tabloda dosya erişimi ile dosya öznitelikleri arasındaki görevleri listeler:

|Bitiş|Bkz. |
|---|---|
|Açın ve bir günlük dosyasına metin Ekle|[Nasıl yapılır: Açın ve bir günlük dosyasına Ekle](../../../../standard/io/how-to-open-and-append-to-a-log-file.md)|
|Bir dosyanın özniteliklerini belirleme|<xref:System.IO.FileAttributes>|

## <a name="file-permissions"></a>Dosya izinleri

İle dosyalara ve dizinlere erişimi denetleme yapılabilir <xref:System.Security.Permissions.FileIOPermission> sınıfı. Bu, varsayılan özel bir yerel kullanıcı hesabı bağlamında çalıştırma kapsamında oluşturulan ASPNET adlı Web Forms ile çalışan geliştiriciler için özellikle önemlidir olabilir [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] ve [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] yüklemeleri. Bu tür bir uygulama isteklerini erişimi, bir kaynağa ASPNET kullanıcı hesabının izinlerini kullanıcı, bir Web uygulamasından bir dosyaya yazma gibi eylemleri gerçekleştirmesini önleyebilen sınırlıdır. Daha fazla bilgi için bkz. <xref:System.Security.Permissions.FileIOPermission>.

## <a name="isolated-file-storage"></a>Yalıtılmış dosya depolama

Burada kullanıcı veya kod gerekli izinlere sahip olmayabilir dosyalarıyla çalışırken oluşturulan çözmekte girişimi yalıtılmış depolamadır. Yalıtılmış Depolama her kullanıcı bir veya daha fazla depoları tutabilen bir veri bölmesi atar. Depoları birbirinden kullanıcı ve derlemeye göre yalıtılmış olabilir. Yalnızca kullanıcı ve bir depo oluşturulduğuna derleme erişimi vardır. Bir depolama tam sanal dosya sistemi olarak görev yapar; bir depo içinde oluşturabilir ve dizinleri ve dosyaları işleme.

Aşağıdaki tabloda, genellikle yalıtılmış dosya depolama ile ilişkili görevleri listeler.

|Bitiş|Bkz. |
|---|---|
|Bir yalıtılmış depolama oluşturma|[Nasıl yapılır: Yalıtılmış depolama için depoları alma](../../../../standard/io/how-to-obtain-stores-for-isolated-storage.md)|
|Yalıtılmış depoları numaralandırma|[Nasıl yapılır: Yalıtılmış depolama için depoları numaralandırma](../../../../standard/io/how-to-enumerate-stores-for-isolated-storage.md)|
|Bir yalıtılmış depolama Sil|[Nasıl yapılır: Yalıtılmış depolamadaki depoları silme](../../../../standard/io/how-to-delete-stores-in-isolated-storage.md)|
|Yalıtılmış depolamada dosya veya dizin oluşturma|[Nasıl yapılır: Yalıtılmış depolamada dosya ve dizinler oluşturma](../../../../standard/io/how-to-create-files-and-directories-in-isolated-storage.md)|
|Yalıtılmış depolamada dosya bulma|[Nasıl yapılır: Yalıtılmış depolamada mevcut dosya ve dizinleri bulma](../../../../standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md)|
|Yalıtılmış depolamadaki dosyaya yazma veya okuma|[Nasıl yapılır: Okuma ve yalıtılmış depolamadaki dosyaları yazma](../../../../standard/io/how-to-read-and-write-to-files-in-isolated-storage.md)|
|Bir dosya veya dizin yalıtılmış depolamadaki Sil|[Nasıl yapılır: Dosya ve dizinleri yalıtılmış depolamadaki Sil](../../../../standard/io/how-to-delete-files-and-directories-in-isolated-storage.md)|

## <a name="file-events"></a>Dosya olayları

<xref:System.IO.FileSystemWatcher> Bileşen dosya ve dizinleri sisteminize veya ağ erişimi için kullandığınız herhangi bir bilgisayarda yapılan değişiklikleri izlemek üzere sağlar. Örneğin, bir dosya değiştirildiğinde, bir kullanıcı değişiklik gerçekleştikten bir uyarı göndermek isteyebilirsiniz. Değişiklikler olduğunda, bir veya daha fazla olay gerçekleşti, bir arabellek depolanan ve için teslim <xref:System.IO.FileSystemWatcher> işleme için bileşen.

## <a name="see-also"></a>Ayrıca bkz.

- [Akışlar Oluşturma](../../../../standard/io/composing-streams.md)
- [Dosya ve Akış G/Ç'si](../../../../standard/io/index.md)
- [Zaman Uyumsuz Dosya G/Ç](../../../../standard/io/asynchronous-file-i-o.md)
- [.NET Framework dosyası g/ç ve dosya sistemi (Visual Basic) de kullanılan sınıflar](../../../../visual-basic/developing-apps/programming/drives-directories-files/classes-used-in-net-framework-file-io-and-the-file-system.md)
