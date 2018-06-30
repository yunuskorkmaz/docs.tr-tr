---
title: Windows sistemlerine dosya yolu biçimleri
ms.date: 06/28/2018
ms.technology: dotnet-standard
ms.topic: article
helpviewer_keywords:
- I/O, long paths
- long paths
- path formats, Windows
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a5fccf5ea86469f14963fad8e7d2af0f7c68d2df
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106941"
---
# <a name="file-path-formats-on-windows-systems"></a>Windows sistemlerine dosya yolu biçimleri

Birçok türlerini üyeleri <xref:System.IO> ad alanı içeren bir `path` mutlak veya göreli bir yol için bir dosya sistemi kaynak belirtmenize olanak sağlar. parametre. Bu yol sonra geçirilir [Windows dosya sysem API'leri](https://msdn.microsoft.com/library/windows/desktop/aa364407(v=vs.85).aspx). Bu konu Windows sistemlerinde kullanabileceğiniz dosya yolları için biçimleri açıklanmıştır.

## <a name="traditional-dos-paths"></a>Geleneksel DOS yolları

Standart bir DOS yolu üç bileşenden oluşabilir:

- Bir birim veya sürücü harfini izleyen tarafından Birim Ayırıcı (`:`).
- Bir dizin adı. [Dizin ayırıcı karakterde](<xref:System.IO.Path.DirectorySeparatorChar>) iç içe geçmiş dizin hiyerarşisi içinde alt dizinler ayırır.
- İsteğe bağlı bir dosya adı. [Dizin ayırıcı karakterde](<xref:System.IO.Path.DirectorySeparatorChar>) dosyası yolu ve dosya adı ayırır.

Her üç bileşenin varsa, mutlak bir yoludur. Birim veya sürücü harfi yok belirtilirse ve dizin adlarını başlıyorsa [dizin ayırıcı karakterde](<xref:System.IO.Path.DirectorySeparatorChar>), geçerli sürücüsünün kökünden göreli bir yoludur. Aksi takdirde, geçerli dizine göreli yoludur. Aşağıdaki tabloda bazı olası dizin ve dosya yollarını gösterir.

|Yol  |Açıklama  |
| -- | -- |
| `C:\Documents\Newsletters\Summer2018.pdf` | C: sürücüsünün kökünden mutlak bir dosya yolu |
| `\Program Files\Custom Utilities\StringFinder.exe` | Geçerli sürücüsünün kökünden mutlak bir yol. |
| `2018\January.xlsx` | Geçerli dizinin alt dizindeki bir dosya için göreli bir yol. |
| `..\Publications\TravelBrochure.pdf` | Eş geçerli dizinin bir dizindeki dosyayı göreli yolu. |
| `C:\Projects\apilibrary\apilibrary.sln` | Bir dosya için mutlak bir yol C: sürücüsünün kökünden |
| `C:Projects\apilibrary\apilibrary.sln` | Geçerli dizindeki C: sürücüsünün göreli bir yol. |

> [!IMPORTANT]
> Son iki yolu arasındaki farkı unutmayın. Hem isteğe bağlı bir birim tanımlayıcısı (C:) her iki durumda belirtin, ancak ikinci'nin almadığı ilk belirtilen birim kök ile başlar. Buna karşın ikinci geçerli dizininden C: sürücüsü, göreli bir yol, ilk C: sürücüsünün kök dizininin mutlak bir yol sonucudur. Windows dosya yolları ilgili hatalar ortak bir kaynağı ilk amaçlanan ikinci formu kullanın.

Bir dosya yolu tam olup olmadığını belirleyebilirsiniz (diğer bir deyişle, bu yolun geçerli dizinin bağımsızdır ve geçerli dizin değiştiğinde değiştirmez) çağırarak <xref:System.IO.Path.IsPathFullyQualified%2A?displayProperty=nameWthType> yöntemi. Böyle bir yol göreceli dizin kesimleri içerebilir Not (`.` ve `..`) ve çözümlenen yol her zaman aynı konuma işaret ediyorsa hala tam olarak nitelenmiş olmalıdır.

Aşağıdaki örnek mutlak ve göreli yolları arasındaki fark gösterilmektedir. D:\FY2018\ dizin var olduğunu ve geçerli sürümünüzde herhangi bir dizin için D:\ komut isteminden örneği çalıştırmadan önce ayarladığınız henüz varsayar.

[!code-csharp[absolute-and-relative-paths](~/samples/snippets/standard/io/file-names/cs/paths.cs)]
[!code-vb[absolute-and-relative-paths](~/samples/snippets/standard/io/file-names/vb/paths.vb)]

## <a name="unc-paths"></a>UNC yolları

Ağ kaynaklarına erişmek için kullanılan Evrensel Adlandırma Kuralı (UNC) yolları, aşağıdaki biçime sahiptir:

- İle başlayan bir sunucu veya ana bilgisayar adı \\ \\. Sunucu adı, NetBIOS makine adı veya bir IP/FQDN adresi (IPv4 v6 desteklenir olarak iyi) olabilir.
- Ana bilgisayar adına göre gelen ayrılmış bir paylaşım adı \\. Birlikte, sunucu ve Paylaşım adı birimi yavaşça olun.
- Bir dizin adı. [Dizin ayırıcı karakterde](<xref:System.IO.Path.DirectorySeparatorChar>) iç içe geçmiş dizin hiyerarşisi içinde alt dizinler ayırır.
- İsteğe bağlı bir dosya adı. [Dizin ayırıcı karakterde](<xref:System.IO.Path.DirectorySeparatorChar>) dosyası yolu ve dosya adı ayırır.

UNC yolu bazı örnekleri şunlardır:

|Yol  |Açıklama  |
| -- | -- |
| `\\system07\C$\` | Kök dizin c: sürücüsü `system07`. |
| `\\Server2\Share\Test\Foo.txt` | Test dizininin Foo.txt dosyasında \\ \\Sunucu2\\paylaşmak birim.|

UNC yolları her zaman tam olarak nitelenmiş olmalıdır. Göreli dizin kesimleri içerebilir (`.` ve `..`), ancak bunlar tam nitelenmiş bir yol bir parçası olmalıdır. Bir UNC yolu yalnızca bir sürücü harfine eşleyerek göreli yollar kullanabilirsiniz.

## <a name="dos-device-paths"></a>DOS aygıtı yolları

Windows işletim sistemi dosyaları dahil olmak üzere tüm kaynaklara işaret eden bir birleşik nesne modeli içerir. Bu nesne yolları konsol penceresinden erişilebilir olduğundan ve özel bir klasör eski DOS ve UNC yolları eşlendiği sembolik bağlantılar aracılığıyla Win32 katman sunulur. Bu özel klasör olan DOS aygıtı yolu söz dizimi erişilen biri:

`\\.\C:\Test\Foo.txt`  
`\\?\C:\Test\Foo.txt`

> [!NOTE]
> DOS aygıtı yolu sözdizimi, .NET Core 1.1 ve .NET Framework 4.6.2 ile başlayarak Windows üzerinde çalışan .NET uygulamaları üzerinde desteklenir.

DOS aygıtı yolu aşağıdaki bileşenlerden oluşur:

- Aygıt yolu tanımlayıcısı (`\\.\` veya `\\?\`), yolun bir DOS aygıtı yolu olarak tanımlar.

   > [!NOTE]
   > `\\?\` .NET Core'nin tüm sürümleri ve .NET Framework 4.6.2 sürümünden başlayarak desteklenir.
   
- Sembolik bağlantıyı "gerçek" cihaz nesnesine (Bu durumda C:).

   DOS aygıtı yolu aygıt yolu belirleyici sonra ilk kesimi birime veya sürücüye tanımlar. (Örneğin, `\\?\C:\` ve `\\.\BootPartition\`.)

   Çağrılan, edilebileceği, belirli bir bağlantı UNC için `UNC`. Örneğin:

      `\\.\UNC\Server\Share\Test\Foo.txt`
      `\\?\UNC\Server\Share\Test\Foo.txt`

    Cihaz UNC forms sunucu/paylaşımı bölümüdür birim. Örneğin, `\\?\server1\e:\utilities\\filecomparer\`, server1\utilities paylaşımı/bölümüdür. Bu yöntem gibi çağırırken önemli <xref:System.IO.Path.GetFullPath(System.String,System.String)?displayProperty=nameWithType> göreceli dizin kesimleri ile; hiçbir zaman birim gitmek mümkündür. 

DOS aygıtı yolları tanımına göre tam. Göreli dizin kesimleri (`.` ve `..`) izin verilmez. Geçerli dizin hiçbir zaman kullanımları girin.

## <a name="example-ways-to-refer-to-the-same-file"></a>Örnek: yolları aynı dosyasına bakın

Aşağıdaki örnek, başvurabilirsiniz bir dosyaya API'leri kullanırken yollardan bazılarını gösterilmektedir <xref:System.IO> ad alanı. Örnek başlatır bir <xref:System.IO.FileInfo> nesne ve kullandığı kendi <xref:System.IO.FileInfo.Name> ve <xref:System.IO.FileInfo.Length> dosya adı ve dosya uzunluğu görüntülemek için özellikler.

[!code-csharp[referring-to-the-same-file](~/samples/snippets/standard/io/file-names/cs/file-refs.cs)]
[!code-vb[referring-to-the-same-file](~/samples/snippets/standard/io/file-names/vb/file-refs.vb)]

## <a name="path-normalization"></a>Yol normalleştirme

Windows API'ları için geçirilen neredeyse tüm yolları normalleştirilmiş. Normalleştirme sırasında Windows aşağıdaki adımları gerçekleştirir:

- Yolun tanımlar.
- Geçerli dizin kısmen nitelenmiş (göreli) yollar için geçerlidir.
- Bileşen ve dizin ayırıcı canonicalizes.
- Göreli dizin bileşenleri değerlendirir (`.` geçerli dizin için ve `..` üst dizini için).
- Belirli karakterler kırpar.

Bu normalleştirme örtük olarak gerçekleşir, ancak açıkça çağırarak bunu yapabilirsiniz <xref:System.IO.Path.GetFullPath%2A?displayProperty=nameWithType> yapılan bir çağrı sarmalar yöntemi [GetFullPathName() işlevi](https://msdn.microsoft.com/library/windows/desktop/aa364963(v=vs.85).aspx). Ayrıca, Windows çağırabilirsiniz [GetFullPathName() işlevi](https://msdn.microsoft.com/library/windows/desktop/aa364963(v=vs.85).aspx) P/Invoke kullanarak doğrudan. Ayrıca, çağırabilirsiniz 

### <a name="identifying-the-path"></a>Yolun tanımlama

İlk adımda yolu normalleştirme yol türünü tanımlamak için kullanılır. Yolları birkaç kategoriden ayrılır:

- Cihaz yollar oldukları; diğer bir deyişle, bunlar iki ayırıcılar ve bir soru işareti veya süre ile başlar (`\\?` veya `\\.`).
- UNC yollarını oldukları; diğer bir deyişle, bir soru işareti veya dönem olmadan iki Ayırıcılı başlayın. 
- Tam olarak nitelenmiş DOS yollar oldukları; diğer bir deyişle, bunlar bir sürücü harfi, bir birim ayırıcı ve bileşen ayırıcı ile başlar (`C:\`).
- Eski aygıt belirleme (`CON`, `LPT1`).
- Geçerli sürücüsünün köküne göre oldukları; diğer bir deyişle, bunlar tek bileşen ayırıcı ile başlayan (`\`).
- Belirtilen sürücü geçerli dizine göreli oldukları; diğer bir deyişle, bunlar bir sürücü harfi, bir birim ayırıcı ve bileşen ayırıcı ile başlar (`C:`).
- Geçerli dizine göreli oldukları; diğer bir deyişle, bunlar başka bir şey ile başlayan (`temp\testfile.txt`).

Yol türü geçerli bir dizin herhangi bir yolla uygulanmış olup olmadığını belirler. Yolun "root" nedir belirler.

### <a name="handling-legacy-devices"></a>Eski cihazların işleme

Yolun eski bir DOS aygıtı gibi olup olmadığını `CON`, `COM1`, veya `LPT1`, cihaz yola eklenerek dönüştürülür `\\.\` ve döndürülen. 

Eski aygıt adı ile başlayan bir yolu her zaman bir eski aygıt tarafından yorumlanan <xref:System.IO.Path.GetFullPath(System.String)?displayProperty=nameWithType> yöntemi. Örneğin, DOS aygıtı yolunu `CON.TXT` olan `\\.\CON`ve DOS aygıtı yolunu `COM1.TXT\file1.txt` olan `\\.\COM1`.

### <a name="applying-the-current-directory"></a>Geçerli dizin uygulama

Yol tam değilse, Windows geçerli dizin için geçerlidir. UNC ve aygıt yolları uygulanan geçerli dizin yok. Tam bir sürücü C: ayırıcı ile mu\\.

Yolun tek bileşen ayırıcı ile başlarsa, geçerli dizin sürücüsünden uygulanır. Örneğin, dosya yolunu ise `\utilities` ve geçerli dizin olduğu `C:\temp\`, normalleştirme üretir `C:\utilities`.

Belirtilen sürücü komut kabuğu kümeden son geçerli dizin yolu bir sürücü harfi, birim ayırıcı ve bileşen ayırıcı ile başlarsa, uygulanır. Son geçerli dizin ayarlı değil, tek başına sürücü uygulanır. Örneğin, dosya yolunu ise `D:sources`, geçerli dizin olduğu `C:\Documents\`, ve D: sürücüdeki son geçerli dizine `D:\sources\`, sonuç `D:\sources\sources`. Bu "göreli sürücü" yolları program ve komut dosyası mantık hataları ortak bir kaynaktır. Bir harf ve bir noktalı virgül ile başlayan göreli değil varsayılarak açıkça doğru değil.

Yolun bir ayırıcı dışında bir şey ile başlarsa, geçerli sürücü ve geçerli dizinde uygulanır. Örneğin, yol ise `filecompare` ve geçerli dizin olduğu `C:\utilities\`, sonuç `C:\utilities\filecompare\`.

> [!IMPORTANT]
> İşlem başına ayarı geçerli dizin olduğu için göreli yolların birden çok iş parçacıklı uygulamalar (diğer bir deyişle, çoğu uygulamaları) tehlikeli. Hiçbir iş parçacığı geçerli dizin dilediğiniz zaman değiştirebilirsiniz. .NET Core 2.1 ile başlayarak, çağırabilirsiniz <xref:System.IO.Path.GetFullPath(System.String,System.String)?displayProperty=nameWithType> göreli bir yol ve karşı çözümlemek istediğiniz temel yolu (geçerli dizin) mutlak bir yol almak için yöntemi. 

### <a name="canonicalizing-separators"></a>Ayırıcılar standart hale getirme

Tüm eğik (`/`) standart Windows ayırıcı ters eğik çizgi dönüştürülür (`\`). Varsa, ilk iki eğik çizgi izleyin eğik çizgi bir dizi daraltılmış tek bir eğik çizgi.

### <a name="evaluating-relative-components"></a>Göreli bileşenleri değerlendirme

Yolun işlendi olarak tüm bileşenleri veya tek bir veya iki nokta oluşan kesimleri (`.` veya `..`) değerlendirilir: 

- Geçerli dizine başvurduğu beri tek bir dönem için geçerli segment kaldırılmıştır.

- İki nokta üst dizine başvuruyor beri çift bir dönem için geçerli kesime ve üst kesimi, kaldırılır.

   Yolun kök değillerse üst dizinler yalnızca kaldırılır. Yolun kökü yol türüne bağlıdır. Sürücüdür (`C:\`) DOS yolları, sunucu/paylaşımı için UNC (`\\Server\Share`) ve aygıt yolları cihaz yolunu önekini (`\\?\` veya `\\.\`).

### <a name="trimming-characters"></a>Karakterleri kırpma

Ayırıcılar ve daha önce kaldırılan göreli kesimleri çalıştığında birlikte, bazı ek karakterleri normalleştirme sırasında kaldırılır:

- Tek bir dönemde bir segment sona ererse, bu süre kaldırılır. (Tek veya çift nokta bir parçası önceki adımda normalleştirilmiş. Üç veya daha çok nokta kesimini Normalleştirilmemiş ve gerçekte geçerli dosya/dizin adıdır.)

- Yol ayırıcı sona ermez, süreleri ve alanları tüm boşlukları (U + 0020) kaldırılır. Son segmenti yalnızca tek veya çift nokta ise, yukarıda göreli bileşenleri kural altında yer alır. 

   Bu kural, bir dizin adı bir boşluk ile sonunda ayırıcı sonra boşluk ekleyerek oluşturabileceğiniz anlamına gelir.  

   > [!IMPORTANT]
   > Yapmanız gerekenler **hiçbir zaman** bir dizin veya dosya adı bir boşluk ile oluşturun. Sondaki boşlukları zorlaştırabilir veya erişimini olanaksız bir dizin ve uygulamalar genellikle dizinleri ve dosyaları adları boşluk içerir işlemeye çalışırken başarısız.

## <a name="skipping-normalization"></a>Normalleştirme atlanıyor

Normalde, bir Windows API'si geçirilen herhangi bir yol (etkin) için geçirilen [GetFullPathName işlevi](https://msdn.microsoft.com/library/windows/desktop/aa364963(v=vs.85).aspx) ve normalleştirilmiş. Önemli bir istisna vardır: bir süre yerine bir soru işaretiyle başlayan aygıt yolu. Yol tam olarak ile başlayan sürece `\\?\` (normalleştirilmiş Not kurallı ters eğik çizgi kullanın).

Neden normalleştirme atlamak istiyor? Üç ana nedeni vardır:

1. Normalde kullanılamaz ancak yasal yolları erişmek için. Bir dosya veya dizin adlı `hidden.`, örneğin, başka bir şekilde erişmek için mümkün değildir. 

1. Zaten normalleştirilmiş varsa normalleştirme atlayarak performansını artırmak için.

1. Atlamak için .NET Framework yalnızca üzerinde `MAX_PATH` 259 karakterden daha büyük olan yollar için izin vermek yol uzunluğu denetle. Çoğu API'ler Bu, bazı istisnalar izin verir.

> [!NOTE]
> .NET core yapmaz ve uzun yolları örtük olarak işler bir `MAX_PATH` denetleyin. `MAX_PATH` Yalnızca .NET Framework uygular.

Normalleştirme ve en fazla yol denetimleri atlanıyor iki cihaz yolu sözdizimleri arasındaki tek fark olan; Aksi takdirde aynı. Uğraşmanız "normal" uygulamalar için zor olan yollar kolayca oluşturabilirsiniz normalleştirme atlanıyor ile dikkat edin.

İle başlayan yollar `\\?\` bunları açıkça başarılı olursa hala normalleştirilmiş [GetFullPathName işlevi](https://msdn.microsoft.com/library/windows/desktop/aa364963(v=vs.85).aspx).

Yollarını yapabilecekleriniz Not birden fazla `MAX_PATH` karakterin [GetFullPathName](https://msdn.microsoft.com/library/windows/desktop/aa364963(v=vs.85).aspx) olmadan `\\?\`. Windows işleyebileceği maksimum dize boyutu kadar rasgele uzunlukta yolları destekler.

## <a name="case-and-the-windows-file-system"></a>Windows dosya sistemi ve servis talebi

Windows olmayan kullanıcıların ve geliştiricilerin kafa karıştırıcı Bul Windows dosya sistemi yaný bu yolu ve dizin adları büyük/küçük harfe duyarsızdır. Diğer bir deyişle, dizin ve dosya adları büyük/küçük harf oluşturulurken kullanılan dizelerin yansıtır. Örneğin, yöntem çağrısı

```csharp
Directory.Create(TeStDiReCtOrY);
```
TeStDiReCtOrY adlı bir dizin oluşturur. Bir dizin veya dosya kasasının değiştirmek için yeniden adlandırırsanız, dizin veya dosya adı onu yeniden adlandırdığınızda kullanılan dizesini durumunu yansıtır. Örneğin, aşağıdaki kodu sınama.txt sınama.txt adlı bir dosyayı yeniden adlandırır:

```csharp
using System;
using System.IO;

class Example
{
   public static void Main()
   {
      var fi = new FileInfo(@".\test.txt");
      fi.MoveTo(@".\Test.txt");
   }
}
``` 
```vb
Imports System.IO

Module Example
   Public Sub Main()
      Dim fi As New FileInfo(".\test.txt")
      fi.MoveTo(".\Test.txt")
   End Sub
End Module
```

Ancak, dizin ve dosya adı karşılaştırmaları büyük küçük harfe duyarsızdır. "Sınama.txt" adlı bir dosya için arama yaparsanız, .NET dosya sistemi API'leri karşılaştırma durumda yoksay. Sınama.txt, TEST. TXT, test. TXT ve büyük ve küçük harfler, herhangi bir birleşimini "sınama.txt" ile eşleşir.
