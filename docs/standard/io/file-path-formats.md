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
ms.openlocfilehash: 258cf59fb8383fe131f4a0e78dac6189e1d9c91e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337669"
---
# <a name="file-path-formats-on-windows-systems"></a>Windows sistemlerinde dosya yolu biçimleri

<xref:System.IO> ad alanındaki birçok türün üyeleri, bir dosya sistemi kaynağına mutlak veya göreli bir yol belirtmenize olanak tanıyan bir `path` parametresi içerir. Bu yol daha sonra [Windows dosya sistemi API 'lerine](/windows/desktop/fileio/file-systems)geçirilir. Bu konuda, Windows sistemlerinde kullanabileceğiniz dosya yollarının biçimleri ele alınmaktadır.

## <a name="traditional-dos-paths"></a>Geleneksel DOS yolları

Standart bir DOS yolu üç bileşenden oluşabilir:

- Birim veya sürücü harfi, ardından birim ayırıcısı (`:`).
- Bir dizin adı. [Dizin ayırıcı karakteri](<xref:System.IO.Path.DirectorySeparatorChar>) , iç içe geçmiş Dizin hiyerarşisindeki alt dizinleri ayırır.
- İsteğe bağlı bir dosya adı. [Dizin ayırıcı karakteri](<xref:System.IO.Path.DirectorySeparatorChar>) dosya yolunu ve dosya adını ayırır.

Üç bileşen varsa, yol mutlak olur. Birim veya sürücü harfi belirtilmemişse ve dizin adı [dizin ayırıcı karakteriyle](<xref:System.IO.Path.DirectorySeparatorChar>)başlıyorsa, yol geçerli sürücünün kökünden görelidir. Aksi takdirde, yol geçerli dizine göre değişir. Aşağıdaki tabloda bazı olası dizin ve dosya yolları gösterilmektedir.

|Yol  |Açıklama  |
| -- | -- |
| `C:\Documents\Newsletters\Summer2018.pdf` | C sürücüsünün kökünden mutlak bir dosya yolu: |
| `\Program Files\Custom Utilities\StringFinder.exe` | Geçerli sürücünün kökünden mutlak bir yol. |
| `2018\January.xlsx` | Geçerli dizinin bir alt dizinindeki bir dosyanın göreli yolu. |
| `..\Publications\TravelBrochure.pdf` | Geçerli dizinin eşi olan dizindeki dosyanın göreli yolu. |
| `C:\Projects\apilibrary\apilibrary.sln` | C sürücüsünün kökünden bir dosyanın mutlak yolu: |
| `C:Projects\apilibrary\apilibrary.sln` | C: sürücüsünün geçerli dizininden göreli bir yol. |

> [!IMPORTANT]
> Son iki yol arasındaki farkı dikkate alın. Her ikisi de isteğe bağlı birim belirticisini (C: her iki durumda) belirtir, ancak ilki belirtilen birimin köküyle başlar, ikincisi ise değildir. Sonuç olarak, ilki C sürücüsünün kök dizinindeki mutlak bir yoldur, ikincisi ise C: sürücüsündeki geçerli dizinden göreli bir yoldur. İlki Windows dosya yollarını içeren yaygın bir hata kaynağı olduğunda ikinci formun kullanılması.

Bir dosya yolunun tam nitelikli olup olmadığını (yani, yolun geçerli dizinden bağımsız olduğunu ve geçerli dizin değiştiğinde değişmediğini) <xref:System.IO.Path.IsPathFullyQualified%2A?displayProperty=nameWthType> yöntemini çağırarak belirleyebilirsiniz. Böyle bir yolun göreli Dizin segmentlerini (`.` ve `..`) içerebildiğini ve çözümlenen yolun her zaman aynı konuma işaret ettiğini unutmayın.

Aşağıdaki örnek mutlak ve göreli yollar arasındaki farkı gösterir. Dizin \ saat 2018\ ' un var olduğunu ve D:\ için geçerli bir dizin belirlemediğinizi varsayar. komut isteminden örneği çalıştırın.

[!code-csharp[absolute-and-relative-paths](~/samples/snippets/standard/io/file-names/cs/paths.cs)]
[!code-vb[absolute-and-relative-paths](~/samples/snippets/standard/io/file-names/vb/paths.vb)]

## <a name="unc-paths"></a>UNC yolları

Ağ kaynaklarına erişmek için kullanılan evrensel adlandırma kuralı (UNC) yolları aşağıdaki biçimdedir:

- \\\\tarafından önceden ortaya çıkacak sunucu veya ana bilgisayar adı. Sunucu adı bir NetBIOS makine adı veya IP/FQDN adresi (IPv4 ve V6 desteklenir) olabilir.
- \\tarafından ana bilgisayar adından ayrılan bir paylaşma adı. Birlikte, sunucu ve paylaşımın adı birimi oluşturun.
- Bir dizin adı. [Dizin ayırıcı karakteri](<xref:System.IO.Path.DirectorySeparatorChar>) , iç içe geçmiş Dizin hiyerarşisindeki alt dizinleri ayırır.
- İsteğe bağlı bir dosya adı. [Dizin ayırıcı karakteri](<xref:System.IO.Path.DirectorySeparatorChar>) dosya yolunu ve dosya adını ayırır.

Aşağıda, UNC yollarının bazı örnekleri verilmiştir:

|Yol  |Açıklama  |
| -- | -- |
| `\\system07\C$\` | `system07`üzerindeki C: sürücüsünün kök dizini. |
| `\\Server2\Share\Test\Foo.txt` | \\\\\\test dizinindeki foo. txt dosyası.|

UNC yollarının her zaman tam olarak nitelenmiş olması gerekir. Bunlara göreli Dizin kesimleri (`.` ve `..`) dahil edebilirler, ancak bunların tam nitelikli bir yolun parçası olması gerekir. Yalnızca bir UNC yolunu bir sürücü harfine eşleyerek göreli yolları kullanabilirsiniz.

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

- Yolu bir DOS cihaz yolu olarak tanımlayan cihaz yolu Belirleyicisi (`\\.\` veya `\\?\`).

   > [!NOTE]
   > `\\?\` tüm .NET Core sürümlerinde .NET Framework ve 4.6.2 sürümünden itibaren desteklenir.

- "Gerçek" cihaz nesnesine (bir sürücü adı veya birim GUID 'SI olması durumunda {b75e2c83-0000-0000-0000-602f00000000} birimi) sembolik bir bağlantı.

   Cihaz yolu belirticisinden sonra DOS cihaz yolunun ilk segmenti birimi veya sürücüyü tanımlar. (Örneğin, `\\?\C:\` ve `\\.\BootPartition\`.)

   UNCs 'Ler için, `UNC`olarak adlandırılan belirli bir bağlantı vardır. Örneğin:

  `\\.\UNC\Server\Share\Test\Foo.txt`
  `\\?\UNC\Server\Share\Test\Foo.txt`

    Cihaz UNCs için, sunucu/paylaşma bölümü birimi oluşturur. Örneğin, `\\?\server1\e:\utilities\\filecomparer\`, sunucu/paylaşma bölümü server1\utilities. Göreli Dizin kesimlerine sahip <xref:System.IO.Path.GetFullPath(System.String,System.String)?displayProperty=nameWithType> gibi bir yöntemi çağırırken bu çok önemlidir; birimin ötesinde gezinmek hiçbir şekilde mümkün değildir.

DOS cihaz yolları tanımına göre tam olarak nitelenir. Göreli Dizin kesimlerine (`.` ve `..`) izin verilmez. Geçerli dizinler, kullanımlarına hiçbir şekilde girmez.

## <a name="example-ways-to-refer-to-the-same-file"></a>Örnek: aynı dosyaya başvurmanın yolları

Aşağıdaki örnek, <xref:System.IO> ad alanında API 'Leri kullanırken bir dosyaya başvurmak için kullanabileceğiniz bazı yolları göstermektedir. Örnek, bir <xref:System.IO.FileInfo> nesnesini örnekleyen ve dosyanın dosya adını ve uzunluğunu göstermek için <xref:System.IO.FileInfo.Name> ve <xref:System.IO.FileInfo.Length> özelliklerini kullanır.

[!code-csharp[referring-to-the-same-file](~/samples/snippets/standard/io/file-names/cs/file-refs.cs)]
[!code-vb[referring-to-the-same-file](~/samples/snippets/standard/io/file-names/vb/file-refs.vb)]

## <a name="path-normalization"></a>Yol normalleştirme

Windows API 'Lerine geçirilen neredeyse tüm yollar normalleştirilir. Normalleştirme sırasında, Windows aşağıdaki adımları gerçekleştirir:

- Yolu tanımlar.
- Geçerli dizini kısmen nitelenmiş (göreli) yollara uygular.
- Canonicalizes bileşeni ve Dizin ayırıcıları.
- Göreli Dizin bileşenlerini değerlendirir (geçerli dizin için`.` ve üst dizin için `..`).
- Belirli karakterleri kırpar.

Bu normalleştirme örtük bir şekilde gerçekleşir, ancak [GetFullPathName () işlevine](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea)yapılan çağrıyı sarmalayan <xref:System.IO.Path.GetFullPath%2A?displayProperty=nameWithType> yöntemini çağırarak bunu açıkça yapabilirsiniz. Ayrıca, P/Invoke kullanarak doğrudan Windows [GetFullPathName () işlevini](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) çağırabilirsiniz.

### <a name="identifying-the-path"></a>Yolu tanımlama

Yol normalleştirmede ilk adım yolun türünü tanımlar. Yollar birkaç kategoriden birinde yer almalıdır:

- Bunlar cihaz yollardır; diğer bir deyişle, iki ayırıcıya ve soru işareti ya da nokta (`\\?` ya da `\\.`) ile başlarlar.
- Bunlar UNC yollardır; diğer bir deyişle, bir soru işareti veya dönem olmadan iki ayırıcıya başlarlar.
- Bunlar tamamen nitelikli DOS yollarıdır; diğer bir deyişle, bir sürücü harfi, bir birim ayırıcısı ve bir bileşen ayırıcısı (`C:\`) ile başlar.
- Eski bir cihaz (`CON`, `LPT1`) tasarlarlar.
- Bunlar geçerli sürücünün köküne görelidir; diğer bir deyişle, tek bir bileşen ayırıcısı (`\`) ile başlar.
- Bunlar, belirtilen sürücünün geçerli dizinine göre belirlenir; diğer bir deyişle, bir sürücü harfi, bir birim ayırıcısı ve bileşen ayırıcısı (`C:`) ile başlar.
- Bunlar geçerli dizine göre değişir; diğer bir deyişle, başka bir şeyle (`temp\testfile.txt`) başlarlar.

Yolun türü, geçerli bir dizinin bir biçimde uygulanıp uygulanmadığı belirler. Ayrıca, yolun "kökünün" ne olduğunu da belirler.

### <a name="handling-legacy-devices"></a>Eski cihazları işleme

Yol, `CON`, `COM1`veya `LPT1`gibi eski bir DOS cihazından, ön bekleyen `\\.\` tarafından bir cihaz yoluna dönüştürülür ve döndürülür.

Eski cihaz adı ile başlayan bir yol <xref:System.IO.Path.GetFullPath(System.String)?displayProperty=nameWithType> yöntemi tarafından her zaman eski bir cihaz olarak yorumlanır. Örneğin, `CON.TXT` için DOS cihaz yolu `\\.\CON`ve `COM1.TXT\file1.txt` DOS cihaz yolu `\\.\COM1`.

### <a name="applying-the-current-directory"></a>Geçerli dizin uygulanıyor

Bir yol tam nitelikli değilse, Windows geçerli dizini bu dizine uygular. UNCs ve cihaz yollarına geçerli dizin uygulanmaz. , Ayırıcısı C:\\olan tam bir sürücü yapmaz.

Yol tek bir bileşen ayırıcısıyla başlıyorsa, geçerli dizindeki sürücü uygulanır. Örneğin, dosya yolu `\utilities` ve geçerli dizin `C:\temp\`, normalleştirme `C:\utilities`üretir.

Yol bir sürücü harfi, birim ayırıcısı ve bileşen ayırıcısı ile başlıyorsa, belirtilen sürücü için komut kabuğundan ayarlanan son geçerli dizin uygulanır. Son geçerli dizin ayarlanmamışsa, tek başına sürücü uygulanır. Örneğin, dosya yolu `D:sources`, geçerli dizin `C:\Documents\`ve D: sürücüsündeki son geçerli dizin `D:\sources\`, sonuç ise `D:\sources\sources`. Bu "sürücü göreli" yolları, yaygın olarak kullanılan bir program ve betik mantığı hataları kaynağıdır. Bir harf ile başlayan bir yolun ve iki nokta üst üste doğru olmadığını varsayarsak

Yol, ayırıcı dışında bir şeyle başlıyorsa, geçerli sürücü ve geçerli dizin uygulanır. Örneğin, yol `filecompare` ve geçerli dizin `C:\utilities\`, sonuç `C:\utilities\filecompare\`olur.

> [!IMPORTANT]
> Geçerli dizin işlem başına bir ayar olduğundan, göreli yollar çok iş parçacıklı uygulamalarda (yani, çoğu uygulama) tehlikelidir. Herhangi bir iş parçacığı herhangi bir zamanda geçerli dizini değiştirebilir. .NET Core 2,1 ' den itibaren, bir göreli yol ve kendisine karşı çözümlemek istediğiniz temel yol (geçerli dizin) için bir mutlak yol almak üzere <xref:System.IO.Path.GetFullPath(System.String,System.String)?displayProperty=nameWithType> yöntemini çağırabilirsiniz.

### <a name="canonicalizing-separators"></a>Standart hale getirme ayırıcılar

Tüm eğik çizgiler (`/`), standart Windows ayırıcısına dönüştürülür, ters eğik çizgi (`\`). Varsa, ilk iki eğik çizgiyi izleyen eğik çizgi serileri tek eğik çizgi olarak daraltılır.

### <a name="evaluating-relative-components"></a>Göreli bileşenleri değerlendirme

Yol işlendiğinde, tek veya çift dönemden (`.` veya `..`) oluşan tüm bileşenler veya segmentler değerlendirilir:

- Tek bir dönem için geçerli kesim, geçerli dizine başvurduğundan kaldırılır.

- Çift dönem için, çift nokta üst dizine başvurduğundan, geçerli segment ve üst kesim kaldırılır.

   Üst dizinler yalnızca yolun kökünü geçmemişse kaldırılır. Yolun kökü, yol türüne bağlıdır. DOS yolları için sürücü (`C:\`), UNCs için sunucu/paylaşma (`\\Server\Share`) ve cihaz yolları için cihaz yolu ön eki (`\\?\` veya `\\.\`).

### <a name="trimming-characters"></a>Karakterleri kırpma

Daha önce kaldırılan ayırıcıların ve göreli parçaların çalıştırılmalarının yanı sıra, normalleştirme sırasında bazı ek karakterler kaldırılır:

- Bir segment tek bir dönemde sona ererse bu süre kaldırılır. (Tek veya çift dönemin bir segmenti, önceki adımda normalleştirilmelidir. Üç veya daha fazla dönemin bir segmenti normalleştirilmez ve aslında geçerli bir dosya/dizin adıdır.)

- Yol bir ayırıcıda sonlanmazsa, tüm sondaki noktalar ve boşluklar (U + 0020) kaldırılır. Son segment yalnızca tek veya çift bir nokta ise, yukarıdaki ilgili bileşenler kuralının altına girer.

   Bu kural, boşluktan sonra sondaki bir ayırıcı ekleyerek sonunda boşluk olan bir dizin adı oluşturabileceğiniz anlamına gelir.

   > [!IMPORTANT]
   > Sonunda boşluk olan bir dizin veya dosya **adı oluşturmanız gerekir** . Sondaki boşluklar, bir dizine erişmek zor veya olanaksız hale gelir ve uygulamalar genellikle boşluklar içeren dizinleri veya dosyaları işlemeye çalışırken başarısız olur.

## <a name="skipping-normalization"></a>Normalleştirme atlanıyor

Normalde, bir Windows API 'sine geçirilen tüm yol, [GetFullPathName işlevine](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) ve normalleştirilmesine geçirilir. Önemli bir özel durum vardır: bir dönem yerine soru işaretiyle başlayan bir cihaz yolu. Yol `\\?\` ile tamamen başlıyorsa (kurallı ters eğik çizginin kullanımını aklınızda bulunur), normalleştirilmelidir.

Neden normalleştirmeyi atlamak istiyorsunuz? Üç önemli neden vardır:

1. Normalde kullanılamayan ancak geçerli olan yollara erişim sağlamak için. `hidden.`adlı bir dosya veya dizin, örneğin, başka bir şekilde erişim imkansızdır.

1. Zaten normalleştirdiyseniz normalleştirmeyi atlayarak performansı artırmak için.

1. Yalnızca .NET Framework, 259 karakterden daha büyük yollara izin vermek üzere yol uzunluğu denetimini `MAX_PATH` atlamak için. Çoğu API, bazı özel durumlarla birlikte buna izin verir.

> [!NOTE]
> .NET Core, uzun yolları örtük olarak işler ve `MAX_PATH` denetimi gerçekleştirmez. `MAX_PATH` denetimi yalnızca .NET Framework uygulanır.

Normalleştirme atlama ve en yüksek yol denetimleri, iki cihaz yolu sözdizimleri arasındaki tek farktır; Aksi halde özdeş. "Normal" uygulamalar için zor olan yolları kolayca oluşturabildiklerinden, normalleştirmeyi atlama konusunda dikkatli olun.

`\\?\` ile başlayan yollar, bunları [GetFullPathName işlevine](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea)açıkça geçirdiğinizde normalleştirmeye devam eder.

`\\?\`olmadan [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) 'e `MAX_PATH` karakterden daha fazla yol geçirebilirsiniz. Windows 'un işleyebileceği en büyük dize boyutuna kadar rastgele uzunluk yollarını destekler.

## <a name="case-and-the-windows-file-system"></a>Büyük/küçük harf ve Windows dosya sistemi

Windows dosya sisteminin, Windows olmayan kullanıcılar ve geliştiricilerin kafa karıştırıcı olduğunu fark eden, yol ve dizin adlarının büyük/küçük harfe duyarlı olduğunu belirtir. Diğer bir deyişle, dizin ve dosya adları, oluşturulduklarında kullanılan dizelerin büyük küçük harflerini yansıtır. Örneğin, yöntem çağrısı

```csharp
Directory.Create("TeStDiReCtOrY");
```

```vb
Directory.Create("TeStDiReCtOrY")
```

TeStDiReCtOrY adlı bir dizin oluşturur. Bir dizini veya dosyayı durumunu değiştirmek için yeniden adlandırırsanız, dizin veya dosya adı, yeniden adlandırdığınızda kullanılan dize durumunu yansıtır. Örneğin, aşağıdaki kod test. txt adlı dosyayı test. txt öğesine yeniden adlandırır:

[!code-csharp[case-and-renaming](~/samples/snippets/standard/io/file-names/cs/rename.cs)]
[!code-vb[case-and-renaming](~/samples/snippets/standard/io/file-names/vb/rename.vb)]

Bununla birlikte, dizin ve dosya adı karşılaştırmaları büyük/küçük harfe duyarlıdır. "Test. txt" adlı bir dosyayı arıyorsanız, .NET dosya sistemi API 'Leri karşılaştırmayla ilgili büyük/küçük harf durumunu yoksayar. Test. txt, TEST. TXT, test. TXT ve büyük ve küçük harflerin diğer birleşimleri "test. txt" ile eşleşir.
