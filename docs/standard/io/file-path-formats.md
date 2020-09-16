---
title: Windows sistemlerinde dosya yolu biçimleri
description: Bu makalede geleneksel DOS yolları, DOS cihaz yolları ve evrensel adlandırma kuralı (UNC) yolları gibi Windows sistemlerinde dosya yolu biçimleri hakkında bilgi edinin.
ms.date: 06/06/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O, long paths
- long paths
- path formats, Windows
ms.openlocfilehash: 36ecbe763ed47e95d9339d1d748b3faab100c15e
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679605"
---
# <a name="file-path-formats-on-windows-systems"></a>Windows sistemlerinde dosya yolu biçimleri

Ad alanındaki türlerin birçok üyesi, <xref:System.IO> `path` bir dosya sistemi kaynağına mutlak veya göreli bir yol belirtmenize imkan tanıyan bir parametre içerir. Bu yol daha sonra [Windows dosya sistemi API 'lerine](/windows/desktop/fileio/file-systems)geçirilir. Bu konuda, Windows sistemlerinde kullanabileceğiniz dosya yollarının biçimleri ele alınmaktadır.

## <a name="traditional-dos-paths"></a>Geleneksel DOS yolları

Standart bir DOS yolu üç bileşenden oluşabilir:

- Birim veya sürücü harfi, ardından birim ayırıcısı ( `:` ).
- Bir dizin adı. [Dizin ayırıcı karakteri](<xref:System.IO.Path.DirectorySeparatorChar>) , iç içe geçmiş Dizin hiyerarşisindeki alt dizinleri ayırır.
- İsteğe bağlı bir dosya adı. [Dizin ayırıcı karakteri](<xref:System.IO.Path.DirectorySeparatorChar>) dosya yolunu ve dosya adını ayırır.

Üç bileşen varsa, yol mutlak olur. Birim veya sürücü harfi belirtilmemişse ve dizin adı [dizin ayırıcı karakteriyle](<xref:System.IO.Path.DirectorySeparatorChar>)başlıyorsa, yol geçerli sürücünün kökünden görelidir. Aksi takdirde, yol geçerli dizine göre değişir. Aşağıdaki tabloda bazı olası dizin ve dosya yolları gösterilmektedir.

|Yol  |Description  |
| -- | -- |
| `C:\Documents\Newsletters\Summer2018.pdf` | Sürücü kökünden mutlak bir dosya yolu `C:` . |
| `\Program Files\Custom Utilities\StringFinder.exe` | Geçerli sürücünün kökünden mutlak bir yol. |
| `2018\January.xlsx` | Geçerli dizinin bir alt dizinindeki bir dosyanın göreli yolu. |
| `..\Publications\TravelBrochure.pdf` | Geçerli dizinin eşi olan dizindeki dosyanın göreli yolu. |
| `C:\Projects\apilibrary\apilibrary.sln` | Sürücünün kökünden bir dosyanın mutlak yolu `C:` . |
| `C:Projects\apilibrary\apilibrary.sln` | Sürücünün geçerli dizininden göreli bir yol `C:` . |

> [!IMPORTANT]
> Son iki yol arasındaki farkı dikkate alın. Her ikisi de isteğe bağlı birim tanımlayıcısını ( `C:` her iki durumda) belirtir, ancak ilki belirtilen birimin köküyle başlar, ikincisi ise. Sonuç olarak, ilki sürücünün kök dizinindeki mutlak bir yoldur `C:` , ikincisi ise geçerli sürücü dizininden göreli bir yoldur `C:` . İlki Windows dosya yollarını içeren yaygın bir hata kaynağı olduğunda ikinci formun kullanılması.

Yöntemi çağırarak bir dosya yolunun tam nitelikli olup olmadığını (yani yol geçerli dizinden bağımsız olduğunu ve geçerli dizin değiştiğinde değiştirmediğini) belirleyebilirsiniz <xref:System.IO.Path.IsPathFullyQualified%2A?displayProperty=nameWithType> . Bu tür bir yolun göreli Dizin kesimleri ( `.` ve) içerebildiğini `..` ve çözümlenen yol her zaman aynı konuma işaret ediyorsa tam nitelikli olduğunu unutmayın.

Aşağıdaki örnek mutlak ve göreli yollar arasındaki farkı gösterir. Dizinin `D:\FY2018\` var olduğunu ve `D:\` örneği çalıştırmadan önce komut isteminden geçerli bir dizin belirlemediğinizi varsayar.

[!code-csharp[absolute-and-relative-paths](~/samples/snippets/standard/io/file-names/cs/paths.cs)]
[!code-vb[absolute-and-relative-paths](~/samples/snippets/standard/io/file-names/vb/paths.vb)]

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="unc-paths"></a>UNC yolları

Ağ kaynaklarına erişmek için kullanılan evrensel adlandırma kuralı (UNC) yolları aşağıdaki biçimdedir:

- Tarafından önceden ortaya çıkacak sunucu veya ana bilgisayar adı `\\` . Sunucu adı bir NetBIOS makine adı veya IP/FQDN adresi (IPv4 ve V6 desteklenir) olabilir.
- Tarafından ana bilgisayar adından ayrılan bir paylaşma adı `\` . Birlikte, sunucu ve paylaşımın adı birimi oluşturun.
- Bir dizin adı. [Dizin ayırıcı karakteri](<xref:System.IO.Path.DirectorySeparatorChar>) , iç içe geçmiş Dizin hiyerarşisindeki alt dizinleri ayırır.
- İsteğe bağlı bir dosya adı. [Dizin ayırıcı karakteri](<xref:System.IO.Path.DirectorySeparatorChar>) dosya yolunu ve dosya adını ayırır.

Aşağıda, UNC yollarının bazı örnekleri verilmiştir:

|Yol  |Description  |
| -- | -- |
| `\\system07\C$\` | `C:`Üzerindeki sürücünün kök dizini `system07` . |
| `\\Server2\Share\Test\Foo.txt` | `Foo.txt`Birimin test dizinindeki dosya `\\Server2\Share` .|

UNC yollarının her zaman tam olarak nitelenmiş olması gerekir. Bunlara göreli Dizin kesimleri ( `.` ve) dahil edebilirler `..` , ancak bunların tam nitelikli bir yolun parçası olması gerekir. Yalnızca bir UNC yolunu bir sürücü harfine eşleyerek göreli yolları kullanabilirsiniz.

## <a name="dos-device-paths"></a>DOS cihaz yolları

Windows işletim sistemi, dosyalar dahil olmak üzere tüm kaynaklara işaret eden birleştirilmiş bir nesne modeline sahiptir. Bu nesne yollarına konsol penceresinden erişilebilir ve eski DOS ve UNC yollarının eşlendiği özel bir sembolik bağlantı klasörü aracılığıyla Win32 katmanına açıktır. Bu özel klasöre, aşağıdakilerden biri olan DOS cihaz yolu sözdizimi kullanılarak erişilir:

`\\.\C:\Test\Foo.txt`
`\\?\C:\Test\Foo.txt`

Bir sürücüyü sürücü harfine göre tanımlamaya ek olarak, birim GUID 'sini kullanarak bir birimi belirleyebilirsiniz. Bu formu alır:

`\\.\Volume{b75e2c83-0000-0000-0000-602f00000000}\Test\Foo.txt`
`\\?\Volume{b75e2c83-0000-0000-0000-602f00000000}\Test\Foo.txt`

> [!NOTE]
> DOS cihaz yolu sözdizimi, .NET Core 1,1 ve .NET Framework 4.6.2 ile başlayan Windows üzerinde çalışan .NET uygulamalarında desteklenir.

DOS cihaz yolu aşağıdaki bileşenlerden oluşur:

- `\\.\` `\\?\` Yolu bir DOS cihaz yolu olarak tanımlayan cihaz yolu Belirleyicisi (veya).

   > [!NOTE]
   > , `\\?\` .NET Core 'un tüm sürümlerinde ve sürümü 4.6.2 ile başlayarak .NET Framework desteklenir.

- "Gerçek" cihaz nesnesine (bir sürücü adı veya birim GUID 'SI olması durumunda {b75e2c83-0000-0000-0000-602f00000000} birimi) sembolik bir bağlantı.

   Cihaz yolu belirticisinden sonra DOS cihaz yolunun ilk segmenti birimi veya sürücüyü tanımlar. (Örneğin, `\\?\C:\` ve `\\.\BootPartition\` .)

   Bilinen UNCs 'Ler için belirli bir bağlantı vardır, ancak bu alınmaz `UNC` . Örnek:

  `\\.\UNC\Server\Share\Test\Foo.txt`
  `\\?\UNC\Server\Share\Test\Foo.txt`

    Cihaz UNCs için, sunucu/paylaşma bölümü birimi oluşturur. Örneğin, ' de, `\\?\server1\e:\utilities\\filecomparer\` sunucu/paylaşma bölümü `server1\utilities` . Bu, göreli Dizin kesimlerinde olduğu gibi bir yöntemi çağırırken önemli bir yöntemdir <xref:System.IO.Path.GetFullPath(System.String,System.String)?displayProperty=nameWithType> ; birim geçmiş bir zaman içinde gezinmek mümkün değildir.

DOS cihaz yolları tanımına göre tam olarak nitelenir. Göreli Dizin kesimlerine ( `.` ve `..` ) izin verilmez. Geçerli dizinler, kullanımlarına hiçbir şekilde girmez.

## <a name="example-ways-to-refer-to-the-same-file"></a>Örnek: aynı dosyaya başvurmanın yolları

Aşağıdaki örnekte, ad alanındaki API 'Leri kullanırken bir dosyaya başvurabileceğiniz bazı yollar gösterilmektedir <xref:System.IO> . Örnek, bir nesneyi örnekleyen <xref:System.IO.FileInfo> ve <xref:System.IO.FileInfo.Name> <xref:System.IO.FileInfo.Length> dosya adını ve dosyanın uzunluğunu göstermek için ve özelliklerini kullanır.

[!code-csharp[referring-to-the-same-file](~/samples/snippets/standard/io/file-names/cs/file-refs.cs)]
[!code-vb[referring-to-the-same-file](~/samples/snippets/standard/io/file-names/vb/file-refs.vb)]

## <a name="path-normalization"></a>Yol normalleştirme

Windows API 'Lerine geçirilen neredeyse tüm yollar normalleştirilir. Normalleştirme sırasında, Windows aşağıdaki adımları gerçekleştirir:

- Yolu tanımlar.
- Geçerli dizini kısmen nitelenmiş (göreli) yollara uygular.
- Canonicalizes bileşeni ve Dizin ayırıcıları.
- Göreli Dizin bileşenlerini değerlendirir ( `.` geçerli dizin ve `..` üst dizin için).
- Belirli karakterleri kırpar.

Bu normalleştirme örtük bir şekilde gerçekleşir, ancak <xref:System.IO.Path.GetFullPath%2A?displayProperty=nameWithType>  [GetFullPathName () işlevine](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea)yapılan çağrıyı sarmalayan yöntemini çağırarak açıkça yapabilirsiniz. Ayrıca, P/Invoke kullanarak doğrudan Windows [GetFullPathName () işlevini](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) çağırabilirsiniz.

### <a name="identify-the-path"></a>Yolu tanımla

Yol normalleştirmede ilk adım yolun türünü tanımlar. Yollar birkaç kategoriden birinde yer almalıdır:

- Bunlar cihaz yollardır; diğer bir deyişle, iki ayırıcıya da bir soru işareti ya da nokta ( `\\?` veya) ile başlarlar `\\.` .
- Bunlar UNC yollardır; diğer bir deyişle, bir soru işareti veya dönem olmadan iki ayırıcıya başlarlar.
- Bunlar tamamen nitelikli DOS yollarıdır; diğer bir deyişle, bir sürücü harfi, bir birim ayırıcısı ve bir bileşen ayırıcısı () ile başlar `C:\` .
- Eski bir cihaz ( `CON` ,) tasarlarlar `LPT1` .
- Bunlar geçerli sürücünün köküne görelidir; diğer bir deyişle, tek bir bileşen ayırıcısı () ile başlar `\` .
- Bunlar, belirtilen sürücünün geçerli dizinine göre belirlenir; diğer bir deyişle, bir sürücü harfi, bir birim ayırıcısı ve bileşen ayırıcısı () ile başlar `C:` .
- Bunlar geçerli dizine göre değişir; diğer bir deyişle, başka bir şeyle ( `temp\testfile.txt` ) başlar.

Yolun türü, geçerli bir dizinin bir biçimde uygulanıp uygulanmadığı belirler. Ayrıca, yolun "kökünün" ne olduğunu da belirler.

### <a name="handle-legacy-devices"></a>Eski cihazları işle

Yol, veya gibi eski bir DOS cihazından, `CON` `COM1` `LPT1` ön bekleyen ve döndürülen bir cihaz yoluna dönüştürülür `\\.\` .

Eski cihaz adı ile başlayan bir yol, her zaman yöntemi tarafından eski bir cihaz olarak yorumlanır <xref:System.IO.Path.GetFullPath(System.String)?displayProperty=nameWithType> . Örneğin, için DOS cihaz yolu `CON.TXT` `\\.\CON` ve için DOS cihaz yolu `COM1.TXT\file1.txt` `\\.\COM1` .

### <a name="apply-the-current-directory"></a>Geçerli dizini Uygula

Bir yol tam nitelikli değilse, Windows geçerli dizini bu dizine uygular. UNCs ve cihaz yollarına geçerli dizin uygulanmaz. Ayırıcı ile tam bir sürücü yapmaz `C:\` .

Yol tek bir bileşen ayırıcısıyla başlıyorsa, geçerli dizindeki sürücü uygulanır. Örneğin, dosya yolu `\utilities` ve geçerli dizin ise, `C:\temp\` normalleştirme üretir `C:\utilities` .

Yol bir sürücü harfi, birim ayırıcısı ve bileşen ayırıcısı ile başlıyorsa, belirtilen sürücü için komut kabuğundan ayarlanan son geçerli dizin uygulanır. Son geçerli dizin ayarlanmamışsa, tek başına sürücü uygulanır. Örneğin, dosya yolu, `D:sources` geçerli dizin `C:\Documents\` ve D: sürücüsündeki son geçerli dizin ise, `D:\sources\` sonuç olur `D:\sources\sources` . Bu "sürücü göreli" yolları, yaygın olarak kullanılan bir program ve betik mantığı hataları kaynağıdır. Bir harf ile başlayan bir yolun ve iki nokta üst üste doğru olmadığını varsayarsak

Yol, ayırıcı dışında bir şeyle başlıyorsa, geçerli sürücü ve geçerli dizin uygulanır. Örneğin, yol `filecompare` ve geçerli dizin ise, `C:\utilities\` sonuç olur `C:\utilities\filecompare\` .

> [!IMPORTANT]
> Geçerli dizin işlem başına bir ayar olduğundan, göreli yollar çok iş parçacıklı uygulamalarda (yani, çoğu uygulama) tehlikelidir. Herhangi bir iş parçacığı herhangi bir zamanda geçerli dizini değiştirebilir. .NET Core 2,1 ' den itibaren, <xref:System.IO.Path.GetFullPath(System.String,System.String)?displayProperty=nameWithType> bir göreli yol ve kendisine karşı çözümlemek istediğiniz temel yol (geçerli dizin) için mutlak bir yol almak üzere yöntemini çağırabilirsiniz.

### <a name="canonicalize-separators"></a>Canonicalize ayırıcılar

Tüm eğik çizgiler ( `/` ), ters eğik çizgi () ile standart Windows ayırıcısına dönüştürülür `\` . Varsa, ilk iki eğik çizgiyi izleyen eğik çizgi serileri tek eğik çizgi olarak daraltılır.

### <a name="evaluate-relative-components"></a>Göreli bileşenleri değerlendir

Yol işlendiğinde, tek veya çift nokta (veya) tarafından oluşturulan bileşenler veya segmentler `.` `..` değerlendirilir:

- Tek bir dönem için geçerli kesim, geçerli dizine başvurduğundan kaldırılır.

- Çift dönem için, çift nokta üst dizine başvurduğundan, geçerli segment ve üst kesim kaldırılır.

   Üst dizinler yalnızca yolun kökünü geçmemişse kaldırılır. Yolun kökü, yol türüne bağlıdır. DOS yolları için sürücü ( `C:\` ), UNCs için sunucu/paylaşma ( `\\Server\Share` ) ve cihaz yolları için cihaz yolu ön eki ( `\\?\` veya `\\.\` ).

### <a name="trim-characters"></a>Kırpma karakterleri

Daha önce kaldırılan ayırıcıların ve göreli parçaların çalıştırılmalarının yanı sıra, normalleştirme sırasında bazı ek karakterler kaldırılır:

- Bir segment tek bir dönemde sona ererse bu süre kaldırılır. (Tek veya çift dönemin bir segmenti, önceki adımda normalleştirilmelidir. Üç veya daha fazla dönemin bir segmenti normalleştirilmez ve aslında geçerli bir dosya/dizin adıdır.)

- Yol bir ayırıcıda sonlanmazsa, tüm sondaki noktalar ve boşluklar (U + 0020) kaldırılır. Son segment yalnızca tek veya çift bir nokta ise, yukarıdaki ilgili bileşenler kuralının altına girer.

   Bu kural, boşluktan sonra sondaki bir ayırıcı ekleyerek sonunda boşluk olan bir dizin adı oluşturabileceğiniz anlamına gelir.

   > [!IMPORTANT]
   > Sonunda boşluk olan bir dizin veya dosya **adı oluşturmanız gerekir** . Sondaki boşluklar, bir dizine erişmek zor veya olanaksız hale gelir ve uygulamalar genellikle boşluklar içeren dizinleri veya dosyaları işlemeye çalışırken başarısız olur.

## <a name="skip-normalization"></a>Normalleştirme atlayın

Normalde, bir Windows API 'sine geçirilen tüm yol, [GetFullPathName işlevine](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) ve normalleştirilmesine geçirilir. Önemli bir özel durum vardır: bir dönem yerine soru işaretiyle başlayan bir cihaz yolu. Yol tam olarak ile başlatılmadığı takdirde `\\?\` (kurallı ters eğik çizginin kullanımını aklınızda), normalleştirilmelidir.

Neden normalleştirmeyi atlamak istiyorsunuz? Üç önemli neden vardır:

1. Normalde kullanılamayan ancak geçerli olan yollara erişim sağlamak için. Örneğin, adlı bir dosya veya dizin, `hidden.` başka bir şekilde erişim imkansızdır.

1. Zaten normalleştirdiyseniz normalleştirmeyi atlayarak performansı artırmak için.

1. Yalnızca .NET Framework, `MAX_PATH` 259 karakterden daha büyük yollara izin vermek için yol uzunluğu denetimini atlamak için. Çoğu API, bazı özel durumlarla birlikte buna izin verir.

> [!NOTE]
> .NET Core, uzun yolları örtülü olarak işler ve bir `MAX_PATH` denetim gerçekleştirmez. `MAX_PATH`Onay yalnızca .NET Framework için geçerlidir.

Normalleştirme atlama ve en yüksek yol denetimleri, iki cihaz yolu sözdizimleri arasındaki tek farktır; Aksi halde özdeş. "Normal" uygulamalar için zor olan yolları kolayca oluşturabildiklerinden, normalleştirmeyi atlama konusunda dikkatli olun.

Öğesini `\\?\` [GetFullPathName işlevine](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea)açıkça geçirirseniz, ile başlayan yollar yine de normalleştirilmelidir.

Karakterden daha fazla karakter yolunu, `MAX_PATH` olmadan [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) 'e geçirebilirsiniz `\\?\` . Windows 'un işleyebileceği en büyük dize boyutuna kadar rastgele uzunluk yollarını destekler.

## <a name="case-and-the-windows-file-system"></a>Büyük/küçük harf ve Windows dosya sistemi

Windows dosya sisteminin, Windows olmayan kullanıcılar ve geliştiricilerin kafa karıştırıcı olduğunu fark eden, yol ve dizin adlarının büyük/küçük harfe duyarlı olduğunu belirtir. Diğer bir deyişle, dizin ve dosya adları, oluşturulduklarında kullanılan dizelerin büyük küçük harflerini yansıtır. Örneğin, yöntem çağrısı

```csharp
Directory.Create("TeStDiReCtOrY");
```

```vb
Directory.Create("TeStDiReCtOrY")
```

TeStDiReCtOrY adlı bir dizin oluşturur. Bir dizini veya dosyayı durumunu değiştirmek için yeniden adlandırırsanız, dizin veya dosya adı, yeniden adlandırdığınızda kullanılan dize durumunu yansıtır. Örneğin, aşağıdaki kod, Test.txt test.txt adlı bir dosyayı yeniden adlandırır:

[!code-csharp[case-and-renaming](~/samples/snippets/standard/io/file-names/cs/rename.cs)]
[!code-vb[case-and-renaming](~/samples/snippets/standard/io/file-names/vb/rename.vb)]

Bununla birlikte, dizin ve dosya adı karşılaştırmaları büyük/küçük harfe duyarlıdır. "test.txt" adlı bir dosyayı arıyorsanız, .NET dosya sistemi API 'Leri karşılaştırmayla ilgili büyük/küçük harf durumunu yoksayar. "Test.txt", "TEST.TXT", "test.TXT" ve büyük ve küçük harflerin diğer birleşimi "test.txt" ile eşleşir.
