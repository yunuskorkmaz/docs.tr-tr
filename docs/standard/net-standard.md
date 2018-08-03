---
title: .NET standard
description: .NET standart, kendi sürümleri ve bunu destekleyen .NET uygulamaları hakkında bilgi edinin.
author: mairaw
ms.author: mairaw
ms.date: 07/19/2018
ms.technology: dotnet-standard
ms.assetid: c044882c-af15-45f2-96d1-534557a5ee9b
ms.openlocfilehash: 8f4490edfc06fcc3ec06daffdb0966ac9ee72e23
ms.sourcegitcommit: e8dc507cfdaad504fc9d4c83d28d24569dcef91c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "36298181"
---
# <a name="net-standard"></a>.NET standard

[.NET Standard](https://github.com/dotnet/standard) bir resmi belirtimi .NET API'leri, tüm .NET uygulamalarında kullanılabilir olacak şekilde tasarlanmıştır. .NET Standard arkasında motivasyon büyük gerekmemesi .NET ekosisteminde oluşturabilirsiniz. [ECMA-335](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md) gerekmemesi için .NET uygulaması davranışı kurmaya devam eder ancak hiçbir benzer belirtimi .NET kitaplığı uygulamaları için .NET taban sınıfı kitaplıkları (BCL) için.

.NET Standard aşağıdaki temel senaryolara olanak tanır:

- Uygulama, iş yükünü bağımsız için BCL API tüm .NET uygulamaları için Tekdüzen kümesini tanımlar.
- Bu aynı API'leri kullanarak .NET uygulamaları arasında kullanılabilir taşınabilir kitaplıkları oluşturmak geliştiricilerin sağlar.
- Küçültür veya hatta yalnızca işletim sistemi API'leri için .NET API'lerini nedeniyle paylaşılan kaynağı koşullu derleme ortadan kaldırır.

Çeşitli .NET uygulamalarının .NET Standard belirli sürümlerini hedefler. Her .NET uygulama sürümü, desteklenen en yüksek .NET Standard sürüm geldiğini bir deyimi de önceki sürümlerini destekler bildirir. Örneğin, .NET Framework 4.6, .NET Standard sürümlerinde 1.0 1.3 aracılığıyla tanımlanan tüm API'leri sunan yani .NET Standard 1.3, uygular. Benzer şekilde, .NET Core 1.0 .NET standart 1.6 uygulayan sırasında .NET Framework 4.6.1 .NET Standard 1.4 uygular.

## <a name="net-implementation-support"></a>.NET uygulama desteği

Aşağıdaki tabloda her .NET Standard sürümünü destekleyen en düşük platform sürümleri listelenmiştir.

[!INCLUDE [net-standard-table](~/includes/net-standard-table.md)]

.NET platformlarını hedefleyebilen Standard'ın en yüksek sürümü bulmak için aşağıdaki adımları uygulayın:

1. Çalıştırmak istediğiniz .NET uygulaması gösteren satırı bulur.
2. Sağdan sola başlangıç sürümünüzü gösteren söz konusu satırdaki sütun bulunamıyor.
3. Sütun üst bilgisine hedef destekleyen .NET Standard sürümünü gösterir (ve alt .NET Standard sürümlerinden da bunu destekleyecek).
4. Hedeflemek istediğiniz her platform için bu işlemi yineleyin. Birden fazla hedef platformu varsa, aralarında daha küçük sürüm seçmeniz gerekir. Örneğin, .NET Framework 4.5 ve .NET Core 1.0 üzerinde çalıştırmak istiyorsanız, en yüksek .NET Standard sürümünü kullanabilirsiniz .NET standart 1.1 olur.

### <a name="which-net-standard-version-to-target"></a>Hangi .NET Standard sürümünü hedef

Bir .NET Standard sürümünü seçerken, bu dengeyi dikkate almanız gerekir:

- Daha yüksek sürüm daha fazla API'leri kullanabilirsiniz.
- Düşük sürüm, diğer platformlar, uygulayın.

Genel olarak, hedef öneririz *düşük* .NET Standard olası sürümü. En yüksek .NET Standard sürümünü hedef alabilirsiniz bulduktan sonra bu nedenle, şu adımları izleyin:

1. .NET Standard'ın sonraki alt sürümü hedef ve projenizi derleyin.
2. Proje başarıyla derlenirse, 1. adımı yineleyin. Aksi takdirde, daha yüksek bir sonraki sürüme yeniden hedefle ve sürümünü kullanmanız gerekir.

### <a name="net-standard-versioning-rules"></a>.NET standard sürüm oluşturma kuralları

İki birincil sürüm kuralları vardır:

- Eklenebilir: Mantıksal olarak eşmerkezli daireler .NET Standard sürümleri şunlardır: daha sonraki sürümler önceki sürümlerdeki tüm API'leri dahil edilip derecelendirilir. Sürümler arasında bozucu bir değişiklik bulunmamaktadır.
- Sabit: Bir kez aktarmalı, .NET Standard sürümleri dondurulmuş. Yeni API'leri, ilk .NET Core gibi belirli .NET uygulamalarında kullanılabilir. .NET Standard gözden geçirme panonun yeni API'leri tüm .NET uygulamaları için kullanılabilir olması gerektiğini inanırsa, bunlar yeni bir .NET Standard sürümde eklenir.

## <a name="specification"></a>Belirtimi

.NET Standard belirtimi standartlaştırılmış bir API kümesidir. Belirtimi, özellikle Microsoft (.NET Framework, .NET Core ve Mono içerir) ve Unity gibi .NET implementors tarafından korunur. Genel geri bildirim işlemi aracılığıyla yeni .NET Standard sürümlerini oluşturma işleminin parçası olarak kullanılan [GitHub](https://github.com/dotnet/standard).

### <a name="official-artifacts"></a>Resmi yapıtları

Resmi belirtimi, standart bir parçası olan API'leri tanımlayan .cs dosyalar kümesidir. [Ref directory](https://github.com/dotnet/standard/tree/master/netstandard/ref) içinde [dotnet/standart havuz](https://github.com/dotnet/standard) .NET standart API'lerini tanımlar.

[NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library) metapackage ([kaynak](https://github.com/dotnet/standard/blob/master/netstandard/pkg/NETStandard.Library.dependencies.props)) (kısmen) bir veya daha fazla .NET Standard sürümleri tanımlayan kitaplıkları açıklar.

Bir bileşen göz önünde bulundurulduğunda, ister `System.Runtime`, açıklar:

- .NET Standard (yalnızca kendi kapsamı) bölümü.
- .NET Standard, ilgili kapsam için birden çok sürümü.

Türetilmiş yapıtları daha kullanışlı okuma etkinleştirmek ve (örneğin, bir derleyici kullanarak) belirli bir geliştirici senaryolarını etkinleştirmek için sağlanır.

- [Markdown'da API listesi](https://github.com/dotnet/standard/tree/master/docs/versions)
- Başvuru bütünleştirilmiş kodları olarak dağıtılmış, [NuGet paketlerini](../core/packages.md) ve tarafından başvurulan [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library/) metapackage.

### <a name="package-representation"></a>Paket gösterimi

.NET Standard başvuru bütünleştirilmiş kodları için birincil dağıtım aracı [NuGet paketlerini](../core/packages.md). Uygulamaları çeşitli yollarla, her bir .NET uygulaması için uygun teslim edilir.

NuGet paketleri, bir veya daha fazla hedef [çerçeveleri](frameworks.md). .NET Standard paketleri ".NET Standard" çerçevesini hedefler. Standart .NET framework kullanarak hedef `netstandard` [TFM compact](frameworks.md) (örneğin, `netstandard1.4`). Bu çerçeve, birden çok çalışma zamanları üzerinde çalışması amaçlanmıştır kitaplıkları hedeflemelidir. En geniş kapsamlı API kümesi için hedef `netstandard2.0` kullanılabilir API'ler sayısı fazla 2.0 ve .NET standart 1.6 arasında iki katına olduğundan.

[ `NETStandard.Library` ](https://www.nuget.org/packages/NETStandard.Library/) Metapackage .NET Standard tanımlayan NuGet paketlerini kümesinin tamamını başvuruyor.  Hedeflenecek en yaygın yolu `netstandard` bu metapackage başvurarak olduğu. Açıklanır ve yaklaşık 40 .NET kitaplıkları ve .NET Standard tanımlayan ilişkili API'ler için erişim sağlar. Ek paketleri hedefleyen başvurabilirsiniz `netstandard` erişmek için ek API'ler.

### <a name="versioning"></a>Sürüm oluşturma

Belirtimi, tekil, ancak bir artımlı olarak büyüyen ve doğrusal olarak tutulan API kümesi değil. Standart ilk sürümü API'leri temel kümesini oluşturur. Sonraki sürümlerde, API'leri ekleyin ve önceki sürümleri tarafından tanımlanan API'leri devralır. Standart API kaldırmak için hiçbir yerleşik sağlama yoktur.

.NET standard herhangi bir .NET uygulamasına özel değildir ve bu çalışma zamanları herhangi birinin sürüm oluşturma düzeni eşleşmiyor.

API'leri eklenen herhangi birine (örneğin, .NET Framework, .NET Core ve Mono) uygulamaları belirtimine eklemek için temel nitelikte olması için özellikle düşündüğünüz varsa adayı olarak düşünülebilir. Yeni [.NET Standard sürümlerini](https://github.com/dotnet/standard/blob/master/docs/versions.md) .NET uygulama sürümleri, yeni bir .NET Standard PCL API'lerinden hedef olanak sağlayan temel alınarak oluşturulur. Sürüm oluşturma mekanizması daha ayrıntılı olarak açıklanan [.NET Core sürüm](../core/versions/index.md).

.NET standart sürüm kullanımı için önemlidir. Bir .NET Standard sürümünü göz önünde bulundurulduğunda, o aynı veya daha düşük sürümünü hedefleyen kitaplıklar kullanabilirsiniz. Aşağıdaki yaklaşımı, .NET standart PCLs, .NET Standard hedefleme için belirli kullanmaya yönelik iş akışı açıklanır.

- PCL için kullanılacak bir .NET Standard sürümünü seçin.
- Aynı .NET Standard sürümünü veya daha düşük bağımlı kitaplıkları kullanın.
- Daha yüksek bir .NET Standard sürümüne bağlıdır kitaplığa bulursanız, ya da aynı sürüme benimsemenizi veya bu kitaplığı kullanmamaya karar gerekir.

## <a name="targeting-net-standard"></a>.NET Standard hedefleme

Yapabilecekleriniz [.NET standart kitaplıkları yapı](../core/tutorials/libraries.md) bir birleşimi kullanılarak `netstandard` çerçevesi ve NETStandard.Library metapackage. Örneklerini gördüğünüz [.NET Core araçları ile .NET Standard hedefleyen](../core/packages.md).

## <a name="net-framework-compatibility-mode"></a>.NET framework uyumluluk modu

.NET Standard 2.0 ile başlayarak, .NET Framework uyumluluk modu sunulmuştur. Bu uyumluluk modu .NET Standard için derlendi gibi .NET Framework kitaplıkları başvurmak .NET Standard projelerine sağlar. .NET Framework kitaplıklarına başvuruda bulunan Windows Presentation Foundation (WPF) API'leri kullanan kitaplıkları gibi tüm projeler için çalışmaz.

Daha fazla bilgi için [.NET Framework uyumluluk modu](../core/porting/third-party-deps.md#net-framework-compatibility-mode).

## <a name="net-standard-libraries-and-visual-studio"></a>.NET standard kitaplıkları ve Visual Studio

Visual Studio'da .NET standart kitaplıkları oluşturmak için sahip olduğunuzdan emin olun [Visual Studio 2017 sürüm 15.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) veya daha sonra Windows üzerinde yüklü ya da [sürüm 7.1 Mac için Visual Studio](https://visualstudio.microsoft.com/vs/visual-studio-mac/) veya üzeri yüklü macOS.

Projelerinizde kitaplıkları .NET Standard 2.0 kullanabilir. gerekiyorsa, bunu Visual Studio 2015'te de yapabilirsiniz. Ancak, istemci 3.6 veya üzeri yüklü olan NuGet gerekir. NuGet istemci için Visual Studio 2015'ten indirebileceğiniz [NuGet indirir](https://www.nuget.org/downloads) sayfası.

## <a name="comparison-to-portable-class-libraries"></a>Taşınabilir sınıf kitaplıkları ile karşılaştırma

.NET standard ardılı olan [taşınabilir sınıf kitaplığı (PCL)](./cross-platform/cross-platform-development-with-the-portable-class-library.md). .NET Standard standart BCL puanlamalar ve büyük gerekmemesi sonucunda arasında .NET uygulamaları oluşturma taşınabilir kitaplıklar oluşturma deneyimini geliştirir. .NET Standard hedefleyen bir bir PCL veya bir ".NET Standard tabanlı PCL" kitaplıktır. Mevcut PCLs "profili tabanlı PCLs" dir.

.NET standard ve PCL profilleri benzer amacıyla oluşturulan ancak aynı zamanda anahtar bakımlardan ayrılır.

Benzerliklerin çözümlemesi yapılır:

- İkili kod paylaşmak için kullanılan API'ler tanımlayın.

Fark:

- PCL profilleri bağlandıkları mevcut platformlar tarafından tanımlanan sırada .NET standard seçkin API'leri kümesidir.
- .NET standard desteklerken PCL profilleri doğrusal olarak sürümleri.
- PCL profilleri .NET Standard platformu belirsiz modundayken Microsoft platformları temsil eder.

### <a name="pcl-compatibility"></a>PCL uyumluluğu

.NET standard PCL profilleri bir alt kümesi ile uyumludur. .NET standard 1.0, 1.1 ve 1.2 her çakışma PCL profilleri kümesi ile. Bu üst üste iki nedenden dolayı oluşturulmuştur:

- .NET Standard tabanlı PCLs profili tabanlı PCLs başvurmak etkinleştirin.
- .NET Standard tabanlı PCLs paketlenecek şekilde PCLs profili tabanlı etkinleştirin.

PCL uyumluluk profili tabanlı tarafından sağlanır [Microsoft.NETCore.Portable.Compatibility](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) NuGet paketi. Bu bağımlılık, profili tabanlı PCLs içeren NuGet paketleri başvururken gereklidir.

Profil tabanlı PCLs olarak paketlenmiş `netstandard` genellikle paketlenmiş profili tabanlı PCLs kullanmak daha kolaydır. `netstandard` paketleme, mevcut kullanıcıları ile uyumludur.

.NET Standard ile uyumlu olan PCL profilleri kümesine görebilirsiniz:

| PCL profilinin | .NET standard | PCL platformları
|:-----------:|:-------------:|------------------------------------------------------------------------------
| Profile7    | 1.1           | .NET framework 4.5, Windows 8
| Profile31   | 1.0           | Windows 8.1, Windows Phone Silverlight 8.1
| Profile32   | 1.2           | Windows 8.1, Windows Phone 8.1
| Profile44   | 1.2           | .NET framework 4.5.1, Windows 8.1
| Profile49   | 1.0           | .NET framework 4.5, Windows Phone Silverlight 8.
| Profile78   | 1.0           | .NET framework 4.5, Windows 8, Windows Phone Silverlight 8.
| Profile84   | 1.0           | Windows Phone 8.1, Windows Phone Silverlight 8.1
| Profile111  | 1.1           | .NET framework 4.5, Windows 8, Windows Phone 8.1
| Profile151  | 1.2           | .NET framework 4.5.1, Windows 8.1, Windows Phone 8.1
| Profile157  | 1.0           | Windows 8.1, Windows Phone 8.1, Windows Phone Silverlight 8.1
| Profile259  | 1.0           | .NET framework 4.5, Windows 8, Windows Phone 8.1, Windows Phone Silverlight 8.

## <a name="see-also"></a>Ayrıca bkz.

[.NET standard sürümleri](https://github.com/dotnet/standard/blob/master/docs/versions.md)
