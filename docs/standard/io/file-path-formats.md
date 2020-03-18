---
title: Windows sistemlerinde dosya yolu biçimleri
ms.date: 06/06/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O, long paths
- long paths
- path formats, Windows
ms.openlocfilehash: b3510be5d417b555d2db163636eac5ce0c0779e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77628052"
---
# <a name="file-path-formats-on-windows-systems"></a>Windows sistemlerinde dosya yolu biçimleri

<xref:System.IO> Ad alanındaki türlerin çoğunun üyeleri, dosya `path` sistemi kaynağına mutlak veya göreli bir yol belirtmenize olanak tanıyan bir parametre içerir. Bu yol daha sonra [Windows dosya sistemi API'lerine](/windows/desktop/fileio/file-systems)geçirilir. Bu konu, Windows sistemlerinde kullanabileceğiniz dosya yollarının biçimlerini tartışır.

## <a name="traditional-dos-paths"></a>Geleneksel DOS yolları

Standart bir DOS yolu üç bileşenden oluşabilir:

- Bir ses veya sürücü harfi ardından`:`birim ayırıcı ( ).
- Dizin adı. [Dizin ayırıcı karakteri](<xref:System.IO.Path.DirectorySeparatorChar>) iç içe gelen dizin hiyerarşisi içindeki alt dizinleri ayırır.
- İsteğe bağlı dosya adı. [Dizin ayırıcı karakteri](<xref:System.IO.Path.DirectorySeparatorChar>) dosya yolunu ve dosya adını ayırır.

Üç bileşenin tümü de varsa, yol mutlaktır. Ses veya sürücü harfi belirtilmemişse ve dizin adı [dizin ayırıcı karakteriyle](<xref:System.IO.Path.DirectorySeparatorChar>)başlarsa, yol geçerli sürücünün kökünden göreli olur. Aksi takdirde, yol geçerli dizine göredir. Aşağıdaki tabloda bazı olası dizin ve dosya yolları gösterilmektedir.

|Yol  |Açıklama  |
| -- | -- |
| `C:\Documents\Newsletters\Summer2018.pdf` | C sürücüsünün kökünden mutlak bir dosya yolu: |
| `\Program Files\Custom Utilities\StringFinder.exe` | Geçerli sürücünün kökünden mutlak bir yol. |
| `2018\January.xlsx` | Geçerli dizinin alt dizininde dosyaya göreli bir yol. |
| `..\Publications\TravelBrochure.pdf` | Geçerli dizinin eş olduğu bir dizinde dosyaya göreli bir yol. |
| `C:\Projects\apilibrary\apilibrary.sln` | C sürücüsünün kökünden bir dosyaya giden mutlak yol: |
| `C:Projects\apilibrary\apilibrary.sln` | C'nin geçerli dizininden göreli bir yol: sürücü. |

> [!IMPORTANT]
> Son iki yol arasındaki farka dikkat edin. Her ikisi de isteğe bağlı birim belirticisini (C: her iki durumda da) belirtir, ancak ilki belirtilen birimin köküyle başlar, ikincisi ise belirti vermez. Sonuç olarak, ilk sürücü C kök dizininden mutlak bir yoldur:, ikinci sürücü C:. İlk amaçlanan ikinci formun kullanımı, Windows dosya yollarını içeren hataların ortak bir kaynağıdır.

<xref:System.IO.Path.IsPathFullyQualified%2A?displayProperty=nameWthType> Bir dosya yolunun tam olarak nitelikli olup olmadığını (diğer bir şekilde, yol geçerli dizinden bağımsızdır ve geçerli dizin değiştiğinde değişmez) yöntemi çağırarak belirleyebilirsiniz. Bu tür bir yolun göreli dizin`.` `..`bölümlerini (ve) içerebileceğini ve çözümlenmiş yolun her zaman aynı konumu işaret ediyorsa tam olarak nitelikli olabileceğini unutmayın.

Aşağıdaki örnekte mutlak ve göreli yollar arasındaki fark gösterin. D:\FY2018\ dizininin var olduğunu ve D:\ için geçerli bir dizini ayarlamadığınızı varsayar. örneği çalıştırmadan önce komut isteminden.

[!code-csharp[absolute-and-relative-paths](~/samples/snippets/standard/io/file-names/cs/paths.cs)]
[!code-vb[absolute-and-relative-paths](~/samples/snippets/standard/io/file-names/vb/paths.vb)]

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="unc-paths"></a>UNC yolları

Ağ kaynaklarına erişmek için kullanılan evrensel adlandırma kuralı (UNC) yolları aşağıdaki biçime sahiptir:

- Bir sunucu veya ana bilgisayar adı, hangi tarafından prefaced \\ \\olduğunu . Sunucu adı Bir NetBIOS makine adı veya IP/FQDN adresi olabilir (IPv4 ve v6 desteklenir).
- Ev sahibi adından \\' olarak ayrılan bir paylaşım adı Birlikte, sunucu ve paylaşım adı hacmini oluşturan.
- Dizin adı. [Dizin ayırıcı karakteri](<xref:System.IO.Path.DirectorySeparatorChar>) iç içe gelen dizin hiyerarşisi içindeki alt dizinleri ayırır.
- İsteğe bağlı dosya adı. [Dizin ayırıcı karakteri](<xref:System.IO.Path.DirectorySeparatorChar>) dosya yolunu ve dosya adını ayırır.

Unc yollarından bazıları şunlardır:

|Yol  |Açıklama  |
| -- | -- |
| `\\system07\C$\` | C kök dizini: sürücü `system07`. |
| `\\Server2\Share\Test\Foo.txt` | \\Server2\\Share biriminin \\Test dizinindeki Foo.txt dosyası.|

UNC yolları her zaman tam nitelikli olmalıdır. Bunlar göreli dizin segmentleri `..`içerebilir (ve`.` ), ancak bunlar tam nitelikli bir yolun parçası olmalıdır. Göreli yolları yalnızca sürücü mektubuna bir UNC yolunu eşleyerek kullanabilirsiniz.

## <a name="dos-device-paths"></a>DOS cihaz yolları

Windows işletim sistemi, dosyalar da dahil olmak üzere tüm kaynakları işaret eden birleşik bir nesne modeline sahiptir. Bu nesne yollarına konsol penceresinden erişilebilir ve eski DOS ve UNC yollarının eşlendirilen sembolik bağlantılardan oluşan özel bir klasör aracılığıyla Win32 katmanına maruz kalır. Bu özel klasöre DOS aygıt yolu sözdizimi aracılığıyla erişilir:

`\\.\C:\Test\Foo.txt`
`\\?\C:\Test\Foo.txt`

Sürücüyü sürücü harfiyle tanımlamaya ek olarak, ses GUID'ini kullanarak bir birimi tanımlayabilirsiniz. Bu formu alır:

`\\.\Volume{b75e2c83-0000-0000-0000-602f00000000}\Test\Foo.txt`
`\\?\Volume{b75e2c83-0000-0000-0000-602f00000000}\Test\Foo.txt`

> [!NOTE]
> DOS aygıt yolu sözdizimi,.NET Core 1.1 ve .NET Framework 4.6.2 ile başlayan Windows'da çalışan .NET uygulamalarında desteklenir.

DOS aygıt yolu aşağıdaki bileşenlerden oluşur:

- Yolu DOS aygıt`\\.\` yolu `\\?\`olarak tanımlayan aygıt yolu belirtici (veya),

   > [!NOTE]
   > .NET `\\?\` Core'un tüm sürümlerinde ve .NET Framework sürümü4.6.2 ile başlayan tüm sürümlerde desteklenir.

- "Gerçek" aygıt nesnesine sembolik bir bağlantı (C: bir sürücü adı durumunda veya Volume{b75e2c83-0000-0000-602f00000000} bir ses GUID durumunda).

   DoS aygıt yolunun aygıt yolu belirticiden sonraki ilk bölümü ses düzeyini veya sürücüyü tanımlar. (Örneğin, `\\?\C:\` ve `\\.\BootPartition\`.)

   Uncs için, şaşırtıcı değil, denir belirli bir `UNC`bağlantı vardır. Örnek:

  `\\.\UNC\Server\Share\Test\Foo.txt`
  `\\?\UNC\Server\Share\Test\Foo.txt`

    Aygıt UNC'leri için sunucu/paylaşım bölümü hacmi oluşturur. Örneğin, `\\?\server1\e:\utilities\\filecomparer\`sunucu/paylaşım bölümünde server1\utilities olduğunu. Bu, göreli dizin <xref:System.IO.Path.GetFullPath(System.String,System.String)?displayProperty=nameWithType> segmentleri gibi bir yöntemi ararken önemlidir; hacmi geçmek hiçbir zaman mümkün değildir.

DOS cihaz yolları tanımı gereği tamamen niteliklidir. Göreli dizin`.` bölümlerine ( ve `..`) izin verilmez. Geçerli dizinler hiçbir zaman kullanımlarına girmez.

## <a name="example-ways-to-refer-to-the-same-file"></a>Örnek: Aynı dosyaya başvurma yolları

Aşağıdaki örnek, <xref:System.IO> ad alanında API'leri kullanırken bir dosyaya başvurma yollarından bazılarını göstermektedir. Örnek, bir <xref:System.IO.FileInfo> nesneyi anında kullanır <xref:System.IO.FileInfo.Name> <xref:System.IO.FileInfo.Length> ve dosya adını ve dosyanın uzunluğunu görüntülemek için nesneyi ve özelliklerini kullanır.

[!code-csharp[referring-to-the-same-file](~/samples/snippets/standard/io/file-names/cs/file-refs.cs)]
[!code-vb[referring-to-the-same-file](~/samples/snippets/standard/io/file-names/vb/file-refs.vb)]

## <a name="path-normalization"></a>Yol normalleştirme

Windows API'lerine geçirilen yolların hemen hemen hepsi normalleştirildi. Normalleştirme sırasında, Windows aşağıdaki adımları gerçekleştirir:

- Yolu tanımlar.
- Geçerli dizini kısmen nitelikli (göreli) yollara uygular.
- Canonicalizes bileşen ve dizin ayırıcıları.
- Göreli dizin bileşenlerini (geçerli`.` dizin ve `..` üst dizini için) değerlendirir.
- Belirli karakterleri kırpar.

Bu normalleştirme örtülü olarak gerçekleşir, ancak <xref:System.IO.Path.GetFullPath%2A?displayProperty=nameWithType> [getfullpathname() işlevine](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea)bir çağrı yıstıran yöntemi arayarak bunu açıkça yapabilirsiniz. Windows [GetFullPathName() işlevini](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) doğrudan P/Invoke kullanarak da arayabilirsiniz.

### <a name="identifying-the-path"></a>Yolu tanımlama

Yol normalleştirmedeki ilk adım, yol türünü tanımlamaktır. Yollar birkaç kategoriden birine girer:

- Bunlar cihaz yollarıdır; diğer bir şey, onlar iki ayırıcı ve bir`\\?` `\\.`soru işareti veya dönem (veya) ile başlar.
- Bunlar UNC yolları; diğer bir soru işareti veya dönem olmadan iki ayırıcı ile başlar.
- Onlar tam nitelikli DOS yolları vardır; diğer bir şey, bir sürücü harfi, bir birim ayırıcı`C:\`ve bir bileşen ayırıcı ( ) ile başlar.
- Eski bir aygıt`CON`belirlerler ( , `LPT1`).
- Bunlar geçerli sürücünün köküne göredir; yani, tek bir bileşen ayırıcı`\`( ) ile başlar.
- Bunlar, belirli bir sürücünün geçerli dizine göredir; diğer bir şey, bir sürücü harfi, bir birim ayırıcı`C:`ve hiçbir bileşen ayırıcı ( ) ile başlar.
- Bunlar geçerli dizine göredir; başka bir şey ile başlar`temp\testfile.txt`( ).

Yol türü, geçerli bir dizinin bir şekilde uygulanıp uygulanmayacağını belirler. Ayrıca yolun "kök" ne olduğunu belirler.

### <a name="handling-legacy-devices"></a>Eski aygıtları işleme

`CON`Yol, önceden `COM1` `LPT1`bekletilip `\\.\` döndürülerek bir aygıt yoluna dönüştürülür.

Eski bir aygıt adı ile başlayan bir yol, <xref:System.IO.Path.GetFullPath(System.String)?displayProperty=nameWithType> yöntemtarafından her zaman eski bir aygıt olarak yorumlanır. Örneğin, DOS aygıt yolu `CON.TXT` `\\.\CON`için , ve DOS `COM1.TXT\file1.txt` `\\.\COM1`aygıt yolu için .

### <a name="applying-the-current-directory"></a>Geçerli dizini uygulama

Bir yol tam olarak nitelikli değilse, Windows geçerli dizini uygular. UNC'ler ve aygıt yolları geçerli dizin uygulanmaz. Ne ayırıcı C ile tam\\bir sürücü yok: .

Yol tek bir bileşen ayırıcısıyla başlarsa, geçerli dizinden gelen sürücü uygulanır. Örneğin, dosya yolu ve `\utilities` geçerli dizin `C:\temp\`ise, normalleştirme üretir. `C:\utilities`

Yol bir sürücü harfi, birim ayırıcısı ve bileşen ayırıcısı ile başlarsa, belirtilen sürücü için komut kabuğundan son geçerli dizin kümesi uygulanır. Son geçerli dizini ayarlanmadıysa, sürücü tek başına uygulanır. Örneğin, dosya `D:sources`yolu , geçerli dizin `C:\Documents\`, ve sürücü D son geçerli `D:\sources\`dizini: `D:\sources\sources`oldu , sonuç . Bu "sürücü göreli" yolları program ve komut dosyası mantık hataları ortak bir kaynaktır. Bir harf ve iki nokta üst üste başlayan bir yolun göreceli olmadığını varsayarsak doğru değildir.

Yol ayırıcıdan başka bir şeyle başlarsa, geçerli sürücü ve geçerli dizin uygulanır. Örneğin, yol ve `filecompare` geçerli dizin ise, `C:\utilities\`sonuç `C:\utilities\filecompare\`.

> [!IMPORTANT]
> Geçerli dizin işlem başına bir ayar olduğundan, çok iş parçacığı uygulamaları (yani, çoğu uygulamalar) göreli yollar tehlikelidir. Herhangi bir iş parçacığı geçerli dizini herhangi bir zamanda değiştirebilir. .NET Core 2.1 ile başlayarak, göreli bir yoldan mutlak bir yol ve çözümlemek istediğiniz temel yoldan (geçerli dizin) mutlak bir yol almak için <xref:System.IO.Path.GetFullPath(System.String,System.String)?displayProperty=nameWithType> yöntemi arayabilirsiniz.

### <a name="canonicalizing-separators"></a>Kanonihale ayırıcılar

Tüm ileri eğik çizgiler (`/`) standart Windows ayırıcı,`\`arka eğik çizgi ( dönüştürülür. Varsa, ilk iki kesikleri izleyen bir dizi kesik tek bir kesik halinde çökertilir.

### <a name="evaluating-relative-components"></a>Bağıl bileşenlerin değerlendirilmesi

Yol işlenirken, tek veya çift periyotlu (veya)`.` oluşan bileşenler `..`veya segmentler değerlendirilir:

- Geçerli dizine atıfta bulunduğundan, tek bir dönem için geçerli kesim kaldırılır.

- Çift dönem için, çift dönem üst dizine atıfta bulunduğundan, geçerli kesim ve üst kesim kaldırılır.

   Üst dizinler yalnızca yolun kökünü geçmiyorsa kaldırılır. Yolun kökü yolun türüne bağlıdır. DOS yolları`C:\`için sürücü ( ) ( ) UNC'ler için sunucu/paylaşım (`\\Server\Share`),`\\?\` `\\.\`ve aygıt yolları için aygıt yolu önekidir ( veya ).

### <a name="trimming-characters"></a>Karakterleri kırpma

Ayırıcıların ve daha önce kaldırılan göreli kesimlerin çalıştırmalarıyla birlikte, normalleştirme sırasında bazı ek karakterler kaldırılır:

- Bir kesim tek bir dönemde sona ererse, bu dönem kaldırılır. (Bir önceki adımda tek veya çift periyot lu bir kesim normale döndürültürür. Üç veya daha fazla dönemden oluşan bir kesim normalleştirilemez ve aslında geçerli bir dosya/dizin adıdır.)

- Yol bir ayırıcıda bitmiyorsa, tüm son daki dönemler ve boşluklar (U+0020) kaldırılır. Son kesim yalnızca tek veya çift dönemse, yukarıdaki göreli bileşenler kuralına girer.

   Bu kural, boşluktan sonra bir iz ayırıcı ekleyerek bir dizin adı oluşturabileceğiniz anlamına gelir.

   > [!IMPORTANT]
   > Hiçbir **zaman** bir dizin veya dosya adı ile bir izleme alanı ile oluşturmamalısınız. İzleyen boşluklar bir dizine erişmemi zorlaştırabilir veya imkansız hale getirebilir ve uygulamalar genellikle dizinleri veya adları sondaki boşlukları içeren dosyaları işlemeye çalışırken başarısız olur.

## <a name="skipping-normalization"></a>Normalleştirme atlama

Normalde, Windows API'sine geçirilen herhangi bir yol (etkili bir şekilde) [GetFullPathName işlevine](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) aktarılır ve normale aktarılır. Önemli bir özel durum vardır: dönem yerine soru işaretiyle başlayan aygıt yolu. Yol tam olarak `\\?\` (kanonik geri tepme nin kullanımına dikkat edin) ile başlamadıkça, normalleştirilmiştir.

Neden normalleşmeyi atlamak isteyesin ki? Üç temel nedeni vardır:

1. Normalde kullanılamayan ancak yasal olan yollara erişmek için. Örneğin, başka bir `hidden.`şekilde erişilen bir dosya veya dizin mümkün değildir.

1. Zaten normale döndüyseniz normalleştirmeyi atlayarak performansı artırmak için.

1. Yalnızca .NET Framework'de, `MAX_PATH` 259 karakterden büyük yollara izin vermek için yol uzunluğunu denetlemeyi atlamak için. Çoğu API'ler, bazı istisnalar dışında buna izin verir.

> [!NOTE]
> .NET Core uzun yolları örtülü olarak işler `MAX_PATH` ve bir denetim gerçekleştirmez. Çek `MAX_PATH` yalnızca .NET Framework için geçerlidir.

Normalleştirme ve maksimum yol denetimleri atlama iki aygıt yolu sözdizimi arasındaki tek fark; aksi takdirde aynıdır. "Normal" uygulamalarla başa çıkmak için kolayca zor yollar oluşturabileceğinizden, normalleştirmeyi atlayarak dikkatli olun.

`\\?\` [GetFullPathName işlevine](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea)açıkça geçerseniz, yollar hala normalize edilir.

[GetFullPathName'e](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) `MAX_PATH` karakterden daha fazla yol `\\?\`iletebilirsiniz. Windows'un işleyebilir maksimum dize boyutuna kadar rasgele uzunluk yolları destekler.

## <a name="case-and-the-windows-file-system"></a>Büyük/küçük harf ve Windows dosya sistemi

Windows dosya sisteminin Windows olmayan kullanıcılarının ve geliştiricilerin kafa karıştırıcı bulduğu bir özelliği, yol ve dizin adlarının büyük/küçük harf duyarsız olmasıdır. Diğer bir arada, dizin ve dosya adları oluşturulduklarında kullanılan dizelerin kasasını yansıtır. Örneğin, yöntem arama

```csharp
Directory.Create("TeStDiReCtOrY");
```

```vb
Directory.Create("TeStDiReCtOrY")
```

TeStDiReCtOrY adında bir dizin oluşturur. Bir dizin veya dosyayı büyük/küçük harf değiştirmek için yeniden adlarsanız, dizin veya dosya adı yeniden adlandırdığınızda kullanılan dizenin büyük/küçük harflerini yansıtır. Örneğin, aşağıdaki kod test.txt adlı bir dosyayı Test.txt olarak yeniden adlandırır:

[!code-csharp[case-and-renaming](~/samples/snippets/standard/io/file-names/cs/rename.cs)]
[!code-vb[case-and-renaming](~/samples/snippets/standard/io/file-names/vb/rename.vb)]

Ancak, dizin ve dosya adı karşılaştırmaları büyük/küçük harf duyarsızdır. "test.txt" adlı bir dosyayı ararsanız, .NET dosya sistemi API'leri karşılaştırmada durumu yoksayılsın. Test.txt, TEST. TXT, test edin. TXT ve alt ve küçük harflerin diğer kombinasyonları "test.txt" ile eşleşir.
