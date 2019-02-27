---
title: Windows sistemlerde dosya yolu biçimleri
ms.date: 06/28/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O, long paths
- long paths
- path formats, Windows
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ecaae9e1af359ead1c15a9e431eac21e41040efe
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56835830"
---
# <a name="file-path-formats-on-windows-systems"></a>Windows sistemlerde dosya yolu biçimleri

Çoğu içindeki türlerin üyelerini <xref:System.IO> ad alanı içeren bir `path` mutlak veya göreli bir yol için bir dosya sistemi kaynak belirtmenize olanak sağlar. parametre. Bu yolu geçirilerek [Windows dosya sistemi API'ları](/windows/desktop/fileio/file-systems). Bu konuda Windows sistemlerinde kullanabilirsiniz dosya yolları için biçimleri açıklanır.

## <a name="traditional-dos-paths"></a>Geleneksel DOS yolları

Standart bir DOS yol üç bileşeni oluşabilir:

- Bir birim veya sürücü harfini izleyen tarafından toplu ayırıcı (`:`).
- Bir dizin adı. [Dizin ayırıcı karakterde](<xref:System.IO.Path.DirectorySeparatorChar>) iç içe geçmiş dizin sıradüzeni içinde alt dizinler ayırır.
- İsteğe bağlı bir dosya adı. [Dizin ayırıcı karakterde](<xref:System.IO.Path.DirectorySeparatorChar>) dosya yolu ve dosya adını ayırır.

Üç bileşen mevcut olması durumunda, mutlak bir yoludur. Birim veya sürücü harfi yok belirtilirse ve dizin adları ile başlayan [dizin ayırıcı karakterde](<xref:System.IO.Path.DirectorySeparatorChar>), geçerli sürücüsünün kökünden göreli yoludur. Aksi takdirde, geçerli dizine göreli yoludur. Aşağıdaki tabloda, bazı olası dizin ve dosya yolları gösterilmektedir.

|Yol  |Açıklama  |
| -- | -- |
| `C:\Documents\Newsletters\Summer2018.pdf` | C: sürücüsünün kökünden bir mutlak dosya yolu |
| `\Program Files\Custom Utilities\StringFinder.exe` | Geçerli sürücüsünün kökünden mutlak bir yol. |
| `2018\January.xlsx` | Geçerli dizininin bir alt dosyaya göreli yol. |
| `..\Publications\TravelBrochure.pdf` | Geçerli dizin eşdüzeyde bir dizindeki dosya için göreli bir yol. |
| `C:\Projects\apilibrary\apilibrary.sln` | Bir dosya için mutlak bir yol C: sürücüsünün kökünden |
| `C:Projects\apilibrary\apilibrary.sln` | Geçerli dizininden C: sürücüsünün göreli bir yol. |

> [!IMPORTANT]
> Son iki yolu arasındaki farka dikkat edin. Hem isteğe bağlı bir birim tanımlayıcısı (her iki durumda da C:) belirtin, ancak ikinci desteklemez ilk belirtilen birimin kökündeki ile başlar. Sonuç olarak, ikinci bir göreli yol geçerli dizininden C: sürücüsünün bilgileriyse mutlak bir yol kök dizininden C: sürücüsünün davranıştır. Windows dosya yolları ilgili hatalar ortak bir kaynağı ilk istendiğinde ikinci formu kullanın.

Bir dosya yolu tam olup olmadığını belirleyebilir (diğer bir deyişle, bu yolun geçerli dizine bağımsızdır ve geçerli dizine değiştiğinde değiştirmez) çağırarak <xref:System.IO.Path.IsPathFullyQualified%2A?displayProperty=nameWthType> yöntemi. Böyle bir yol göreli directory parçaları dahil edebileceğinizi unutmayın (`.` ve `..`) ve çözümlenen yol her zaman aynı konuma işaret ediyorsa yine de tam olarak nitelenmiş olmalıdır.

Aşağıdaki örnek, mutlak ve göreli yolları arasındaki farkı gösterir. D:\FY2018\ dizinin var olduğundan ve, herhangi bir geçerli dizin için D:\ Komut İstemi'nden örneği çalıştırmadan önce ayarlamasını yapmadığınızı fark olduğunu varsayar.

[!code-csharp[absolute-and-relative-paths](~/samples/snippets/standard/io/file-names/cs/paths.cs)]
[!code-vb[absolute-and-relative-paths](~/samples/snippets/standard/io/file-names/vb/paths.vb)]

## <a name="unc-paths"></a>UNC yolu

Ağ kaynaklarına erişmek için kullanılan, Evrensel Adlandırma Kuralı (UNC) yollarını, aşağıdaki biçime sahiptir:

- Tarafından başında bir sunucu veya ana bilgisayar adı \\ \\. Sunucu adı, NetBIOS makine adı veya IP/FQDN adresi (IPv4 v6 desteklenir gibi iyi) olabilir.
- Ana bilgisayar adına göre ayrılmış olan bir paylaşım adı \\. Birlikte, sunucu ve Paylaşım adı birimi yavaşça olun.
- Bir dizin adı. [Dizin ayırıcı karakterde](<xref:System.IO.Path.DirectorySeparatorChar>) iç içe geçmiş dizin sıradüzeni içinde alt dizinler ayırır.
- İsteğe bağlı bir dosya adı. [Dizin ayırıcı karakterde](<xref:System.IO.Path.DirectorySeparatorChar>) dosya yolu ve dosya adını ayırır.

UNC yolu bazı örnekleri şunlardır:

|Yol  |Açıklama  |
| -- | -- |
| `\\system07\C$\` | C: kök dizinine sürücü üzerinde `system07`. |
| `\\Server2\Share\Test\Foo.txt` | Test dizini Foo.txt dosyasında \\ \\Sunucu2\\birim paylaşın.|

UNC yollarını her zaman tam olarak nitelenmiş olmalıdır. Göreli directory parçaları dahil edebilirsiniz (`.` ve `..`), ancak bunlar tam nitelenmiş bir yol bir parçası olmalıdır. Göreli yollar yalnızca bir UNC yolu bir sürücü harfi ile eşleştirerek kullanabilirsiniz.

## <a name="dos-device-paths"></a>DOS cihaz yolları

Windows işletim sistemi dosyaları dahil tüm kaynakları işaret eden bir birleşik nesne modeline sahiptir. Bu nesne yolları konsol penceresinden erişebilir ve Win32 katmana eski DOS ve UNC yollarını eşlendiğine simgesel bağlantıların özel bir klasör aracılığıyla sunulur. Bu özel klasör olan DOS aygıtı yolu sözdizimi erişilen biri:

`\\.\C:\Test\Foo.txt`  
`\\?\C:\Test\Foo.txt`

> [!NOTE]
> DOS aygıtı yolu sözdizimi .NET Framework 4.6.2 ve .NET Core 1.1 ile başlayarak Windows üzerinde çalışan .NET uygulamalarında desteklenir.

DOS aygıtı yolu aşağıdaki bileşenlerden oluşur:

- Cihaz yolu tanımlayıcısı (`\\.\` veya `\\?\`), yolun bir DOS aygıtı yol olarak tanımlar.

   > [!NOTE]
   > `\\?\` Tüm sürümlerinde .NET Core ve .NET Framework 4.6.2 sürümünden itibaren desteklenir.
   
- Sembolik bağlantıyı "gerçek" cihaz nesnesine (Bu durumda C:).

   İlk cihaz yolu tanımlayıcısı sonraki DOS aygıtı yol kesimi toplu veya sürücü tanımlar. (Örneğin, `\\?\C:\` ve `\\.\BootPartition\`.)

   Edilebileceği çağrılır belirli bir bağlantı için UNC `UNC`. Örneğin:

  `\\.\UNC\Server\Share\Test\Foo.txt`  
  `\\?\UNC\Server\Share\Test\Foo.txt`

    Cihaz UNC paylaşımı/bölümü forms olan birim. Örneğin, `\\?\server1\e:\utilities\\filecomparer\`, server1\utilities paylaşımı/bölümüdür. Bir yöntemi gibi çağrılırken bu önemlidir <xref:System.IO.Path.GetFullPath(System.String,System.String)?displayProperty=nameWithType> göreli directory bölümleri ile; hiçbir zaman birimi gitmek mümkündür. 

DOS cihaz yolları tanımına göre tam. Göreli directory parçaları (`.` ve `..`) izin verilmez. Geçerli dizin, hiçbir zaman kendi kullanımlarına girin.

## <a name="example-ways-to-refer-to-the-same-file"></a>Örnek: Aynı dosyaya başvurmak için yollar

Aşağıdaki örnek, başvurabilirsiniz bir dosyaya API'leri kullanırken yollardan bazılarını göstermektedir <xref:System.IO> ad alanı. Örnek bir <xref:System.IO.FileInfo> nesne ve kullanımları onun <xref:System.IO.FileInfo.Name> ve <xref:System.IO.FileInfo.Length> dosya adı ve dosya uzunluğunu görüntülemek için özellikler.

[!code-csharp[referring-to-the-same-file](~/samples/snippets/standard/io/file-names/cs/file-refs.cs)]
[!code-vb[referring-to-the-same-file](~/samples/snippets/standard/io/file-names/vb/file-refs.vb)]

## <a name="path-normalization"></a>Yol normalleştirme

Neredeyse tüm yolları Windows API'lerine geçirilen normalleştirilir. Normalleştirme sırasında Windows aşağıdaki adımları gerçekleştirir:

- Yolunu tanımlar.
- Geçerli dizin kısmen nitelenmiş (göreli) yollara uygular.
- Bileşen ve dizin ayırıcı canonicalizes.
- Göreli dizini bileşenlerini değerlendirir (`.` geçerli dizin için ve `..` üst dizini için).
- Belirli karakterlerin kırpar.

Bu normalleştirme örtük olarak gerçekleşir, ancak bunu açıkça çağırarak yapabilirsiniz <xref:System.IO.Path.GetFullPath%2A?displayProperty=nameWithType> yöntemine bir çağrı sarılır [GetFullPathName() işlevi](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea). Windows de çağırabilirsiniz [GetFullPathName() işlevi](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) P/Invoke kullanarak doğrudan.

### <a name="identifying-the-path"></a>Yolun tanımlama

İlk adımda yolu normalleştirme yol türünü tanımlamak için kullanılır. Yolları birkaç kategoriden birine girer:

- Cihaz yolları oldukları; diğer bir deyişle, bunlar iki ayırıcıları ve bir soru işareti veya nokta ile başlayan (`\\?` veya `\\.`).
- UNC yollarını oldukları; diğer bir deyişle, bir soru işareti veya dönem olmadan iki ayırıcı ile başlar. 
- Bunlar tam DOS yollardır; diğer bir deyişle, bunlar bir sürücü harfi, bir birim ayracı ve bileşen ayırıcı ile başlar (`C:\`).
- Bunlar eski bir cihaza atamak (`CON`, `LPT1`).
- Geçerli sürücüsünün köküne göreli oldukları; diğer bir deyişle, bunlar bir tek bileşen ayırıcı ile başlar (`\`).
- Belirtilen sürücü geçerli dizine göreli oldukları; diğer bir deyişle, bunlar bir sürücü harfi, bir birim ayracı ve bileşen ayırıcı ile başlar (`C:`).
- Geçerli dizinine göreli oldukları; diğer bir deyişle, bunlar başka bir şey ile başlar (`temp\testfile.txt`).

Yol türü, geçerli bir dizin şekilde uygulanmış olup olmadığını belirler. Yolun "Kök" ne olduğunu belirler.

### <a name="handling-legacy-devices"></a>Eski cihazları işleme

Yolun eski bir DOS aygıtı gibi olup olmadığını `CON`, `COM1`, veya `LPT1`, cihaz yola eklenerek dönüştürülür `\\.\` ve döndürülen. 

Eski cihaz adları ile başlayan yol her zaman eski bir cihaz tarafından yorumlanan <xref:System.IO.Path.GetFullPath(System.String)?displayProperty=nameWithType> yöntemi. Örneğin, DOS aygıtı yolunu `CON.TXT` olduğu `\\.\CON`ve DOS aygıtı yolunu `COM1.TXT\file1.txt` olduğu `\\.\COM1`.

### <a name="applying-the-current-directory"></a>Geçerli dizine uygulanıyor

Bir yol tam değilse, Windows geçerli dizin için geçerlidir. UNC ve cihaz yolları uygulanan geçerli dizin yok. Tam bir sürücü C: ayırıcısıyla diğerinden mu\\.

Yolun bir tek bileşen ayırıcı ile başlarsa, geçerli dizin sürücüden uygulanır. Örneğin, dosya yolu ise `\utilities` ve geçerli dizin `C:\temp\`, normalleştirme üretir `C:\utilities`.

Yolun bir sürücü harfi, birim ayırıcı ve bileşen ayırıcı ile başlarsa, komut kabuğundan belirtilen sürücü için ayarlanmış son geçerli dizine uygulanır. Son geçerli dizin ayarlanmadı, tek başına sürücü uygulanır. Örneğin, dosya yolu ise `D:sources`, geçerli dizin `C:\Documents\`, ve D: sürücüsü son geçerli dizinde `D:\sources\`, sonuç `D:\sources\sources`. Bu "göreli sürücü" yolları program ve betik mantık hataları ortak bir kaynaktır. Bir harf ve bir iki nokta üst üste ile başlayan yol göreli değil varsayarak açıkça doğru değil.

Yol ayırıcı dışında bir şey ile başlarsa, geçerli bir sürücü ve geçerli dizinde uygulanır. Örneğin, yol ise `filecompare` ve geçerli dizin `C:\utilities\`, sonuç `C:\utilities\filecompare\`.

> [!IMPORTANT]
> İşlem içi ayarı geçerli dizin olduğu için göreli yolların tehlikeli birden çok iş parçacıklı uygulamalar (diğer bir deyişle, çoğu uygulamalar). Herhangi bir iş parçacığı geçerli dizin dilediğiniz zaman değiştirebilirsiniz. .NET Core 2.1 ile başlayarak, çağırabilirsiniz <xref:System.IO.Path.GetFullPath(System.String,System.String)?displayProperty=nameWithType> mutlak bir yol göreli bir yol ve karşı çözümlemek istediğiniz temel yolu (geçerli dizin) almak için yöntemi. 

### <a name="canonicalizing-separators"></a>Ayırıcılar standart hale getirme

Tüm İleri eğik çizgi (`/`) standart Windows ayırıcı ters eğik çizgi dönüştürülür (`\`). Varsa, bir dizi izleyin ilk iki eğik çizgi, eğik çizgi daraltılmış tek bir eğik çizgi.

### <a name="evaluating-relative-components"></a>Göreli bileşenleri değerlendiriliyor

Yolun işlendiğinde, tüm bileşenleri veya tek bir veya iki nokta oluşan parçalarını (`.` veya `..`) değerlendirilir: 

- Geçerli dizine başvurduğundan tek bir dönem için geçerli kesime kaldırılır.

- İki nokta üst dizine başvurduğundan çift bir dönem için geçerli kesime ve üst segment, kaldırılır.

   Üst dizinlerin, yolun kökü değillerse yalnızca kaldırılır. Yol kök yolunun türüne bağlıdır. Sürücü harfi (`C:\`) DOS yolları, sunucu/paylaşımı için UNC (`\\Server\Share`) ve cihaz yolları cihaz yol ön eki (`\\?\` veya `\\.\`).

### <a name="trimming-characters"></a>Karakterleri kırpma

Ayırıcılar ve daha önce kaldırılmış göreli kesimleri çalıştırılan yanı sıra bazı ek karakterler normalleştirme sırasında kaldırılır:

- Bir segmenti tek nokta ile bitiyorsa, bu süre kaldırılır. (Tek veya çift nokta bir parçası, önceki adımda normalleştirilmiştir. Üç veya daha fazla nokta bir segmentini Normalleştirilmemiş ve aslında bir geçerli dosya/dizin addır.)

- Yolun bir ayırıcı sonlanmıyor, nokta ve boşluk tüm sondaki (U + 0020) kaldırılır. Son segmenti yalnızca tek veya çift nokta ise, yukarıdaki göreli bileşenleri kural altında döner. 

   Bu kural, bir dizin adı boşluk ile sonda ayırıcı sonra boşluk ekleyerek oluşturabileceğiniz anlamına gelir.  

   > [!IMPORTANT]
   > Yapmanız gerekenler **hiçbir zaman** bir dizin veya dosya adı, boşluk ile oluşturun. Sondaki boşlukları bunu karmaşık hale getirebilir veya erişmek mümkün olmayan bir dizin ve uygulamaları sık dizinleri ve dosyaları, adları boşluk içerir işlemeye çalışırken başarısız.

## <a name="skipping-normalization"></a>Normalleştirme atlanıyor

Normalde, bir Windows API'ye geçirilen herhangi bir yola (etkin) geçirilen [GetFullPathName işlevi](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) ve normalleştirilmiş. Önemli bir istisna vardır: bir dönem yerine bir soru işareti ile başlayan bir cihaz yolu. Tam olarak ile başlayan yol sürece `\\?\` (normalleştirilmiş Not kurallı ters eğik çizgi kullanımı).

Neden normalleştirme atlamak istiyorsunuz? Üç ana nedeni vardır:

1. Normalde kullanılamaz ancak yasal yola erişim almak için. Bir dosya veya dizin adında `hidden.`, örneğin, herhangi bir şekilde erişmek mümkün değildir. 

1. Zaten normalleştirilmiş, normalleştirme atlayarak performansını artırmak için.

1. .NET Framework ile ilgili atlamak için yalnızca `MAX_PATH` 259 karakterden uzun yollar izin vermek yol uzunluğu olup olmadığını denetleyin. Çoğu API'ler, bazı istisnalar izin verir.

> [!NOTE]
> .NET core uzun yollar örtük olarak işler ve gerçekleştirmez bir `MAX_PATH` denetleyin. `MAX_PATH` Denetim, yalnızca .NET Framework için geçerlidir.

Normalleştirme ve en fazla yol denetimleri atlanıyor iki cihaz yolu sözdizimleri arasındaki tek fark, Aksi takdirde birbirinin aynıdır. Normalleştirme, uğraşmanız "normal" uygulamalar için zor olan yollar kolayca oluşturabilirsiniz olduğundan atlanıyor ile dikkat edin.

İle başlayan yollar `\\?\` açıkça bunları geçirirseniz hala normalleştirilmiş [GetFullPathName işlevi](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea).

Yolları için Not birden fazla `MAX_PATH` karakterin [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) olmadan `\\?\`. Bu rastgele uzunluktaki yollar Windows işleyebileceği maksimum dize boyutu kadar destekler.

## <a name="case-and-the-windows-file-system"></a>Windows dosya sistemi ve servis talebi

Windows olmayan kullanıcılara ve geliştiricilere, karmaşık bulma Windows dosya sisteminin bir yaný yoludur ve dizin adları büyük/küçük harfe duyarsızdır. Diğer bir deyişle, dizin ve dosya adları büyük/küçük harf oluşturulduğunda kullanılan dizelerin yansıtır. Örneğin, yöntem çağrısı

```csharp
Directory.Create("TeStDiReCtOrY");
```

```vb
Directory.Create("TeStDiReCtOrY")
```

TeStDiReCtOrY adlı bir dizin oluşturur. Bir dizin veya dosya kasasının değiştirmek için yeniden adlandırırsanız, dizin veya dosya adı, yeniden adlandırdığınızda kullanılan dize durumunu yansıtır. Örneğin, aşağıdaki kod, test.txt Test.txt için adlı bir dosyayı yeniden adlandırır:

[!code-csharp[case-and-renaming](~/samples/snippets/standard/io/file-names/cs/rename.cs)]
[!code-vb[case-and-renaming](~/samples/snippets/standard/io/file-names/vb/rename.vb)]

Ancak, dizin ve dosya adı karşılaştırmalar büyük küçük harf duyarlıdır. "Test.txt" adlı bir dosya için arama yaparsanız, dosya sistemi API'yi .NET karşılaştırma durumda yoksayın. Test.txt, TEST. TXT, test. TXT ve büyük ve küçük harfler, herhangi bir birleşimini "test.txt" eşleşir.
