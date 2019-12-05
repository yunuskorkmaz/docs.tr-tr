---
title: Windows Mağazası Uygulamaları ve Windows Çalışma Zamanı için .NET Framework Desteği
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- Windows Store apps, .NET Framework support for
- Windows Runtime, .NET Framework support for
- .NET for Windows Store apps
- .NET Framework, and Windows Store apps
- .NET Framework, and Windows Runtime
ms.assetid: 6fa7d044-ae12-4c54-b8ee-50915607a565
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dd7e045bf54b09fe2a229efefc0218eb3f2f731a
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802758"
---
# <a name="net-framework-support-for-windows-store-apps-and-windows-runtime"></a>Windows Mağazası Uygulamaları ve Windows Çalışma Zamanı için .NET Framework Desteği

.NET Framework 4,5 Windows Çalışma Zamanı bir dizi yazılım geliştirme senaryosunu destekler. Bu senaryolar üç kategoriye ayrılır:

- [Veya Visual Basic kullanarak C# Windows Mağazası uygulamaları için yol haritası](https://docs.microsoft.com/previous-versions/windows/apps/br229583(v=win.10))bölümünde açıklandığı gibi XAML denetimleriyle Windows 8. x Mağazası uygulamaları geliştirme, [Windows Mağazası UYGULAMALARıNA yönelik](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)) [Nasıl TOS (XAML)](https://docs.microsoft.com/previous-versions/windows/apps/br229566(v=win.10))ve .net hakkında genel bakış.

- .NET Framework ile oluşturduğunuz Windows 8. x Mağaza uygulamalarında kullanılmak üzere sınıf kitaplıkları geliştirme.

- ' De paketlenmiş Windows Çalışma Zamanı bileşenleri geliştirme. Windows Çalışma Zamanı destekleyen herhangi bir programlama dili tarafından kullanılabilen WinMD dosyaları. Örneğin, [ve Visual Basic ' de C# Windows çalışma zamanı bileşenleri oluşturma](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)konusuna bakın.

Bu konuda, .NET Framework üç kategori için sağladığı destek özetlenmektedir ve Windows Çalışma Zamanı bileşenlere yönelik senaryolar açıklanmaktadır. İlk bölüm, .NET Framework ve Windows Çalışma Zamanı arasındaki ilişki hakkında temel bilgileri içerir ve yardım sisteminde ve IDE 'de karşılaşabileceğiniz bazı odlıtıes 'leri açıklar. [İkinci bölümde](#WindowsRuntimeComponents) Windows çalışma zamanı bileşenleri geliştirmeye yönelik senaryolar açıklanmaktadır.

## <a name="the-basics"></a>Temeller

.NET Framework, Windows 8. x Mağazası uygulamaları için .NET sağlayarak ve Windows Çalışma Zamanı kendisini destekleyerek daha önce listelenen üç geliştirme senaryosunu destekler.

- [.NET Framework ve Windows çalışma zamanı ad alanları](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)#net-framework-and-windows-runtime-namespaces) , .NET Framework sınıf kitaplıklarının kolaylaştırılmış bir görünümünü sağlar ve yalnızca Windows 8. x Mağaza uygulamaları ve Windows çalışma zamanı bileşenleri oluşturmak için kullanabileceğiniz türleri ve üyeleri içerir.

  - Bir Windows 8. x mağaza uygulaması veya Windows Çalışma Zamanı bileşeni geliştirmek için Visual Studio 'Yu (Visual Studio 2012 veya üzeri) kullandığınızda, bir başvuru derlemeleri kümesi yalnızca ilgili türleri ve üyeleri görmenizi sağlar.

  - Bu kolaylaştırılmış API kümesi, .NET Framework içinde çoğaltılan özelliklerin veya yinelenen Windows Çalışma Zamanı özelliklerinin kaldırılmasına göre basitleştirilmiştir. Örneğin, koleksiyon türlerinin yalnızca genel sürümlerini içerir ve XML belge nesne modeli Windows Çalışma Zamanı XML API kümesi tarafından da ortadan kalkar.

  - Yalnızca işletim sistemi API 'sini sardığı özellikler de kaldırılır, çünkü Windows Çalışma Zamanı yönetilen koddan kolayca çağrı yapılır.

  Windows 8. x Mağazası uygulamaları için .NET hakkında daha fazla bilgi edinmek için bkz. [Windows Mağazası uygulamalarına genel bakış](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)). API seçim işlemi hakkında bilgi edinmek için .NET blogdaki [Metro stili uygulamalar için .net](https://devblogs.microsoft.com/dotnet/net-for-metro-style-apps/) başlığına bakın.

- [Windows çalışma zamanı](/uwp/api/) , Windows 8. x Mağazası uygulamaları oluşturmaya yönelik kullanıcı arabirimi öğelerini sağlar ve işletim sistemi özelliklerine erişim sağlar. .NET Framework gibi Windows Çalışma Zamanı, C# ve Visual Basic derleyicilerinin .NET Framework sınıf kitaplıklarını kullandıkları gibi Windows çalışma zamanı kullanmasını sağlayan meta verilere sahiptir. .NET Framework, bazı farkları gizleyerek Windows Çalışma Zamanı kullanmayı kolaylaştırır:

  - Olay işleyicilerini ekleme ve kaldırma deseni gibi .NET Framework ve Windows Çalışma Zamanı arasındaki programlama desenleriyle ilgili bazı farklılıklar gizlidir. Sadece .NET Framework desenini kullanın.

  - Yaygın olarak kullanılan türlerdeki bazı farklılıklar (örneğin, ilkel türler ve koleksiyonlar) gizlidir. .NET Framework türünü, bu makalenin ilerleyen kısımlarında [IDE 'de görünür olan farklılıklar](#DifferencesVisibleInIDE)bölümünde anlatıldığı gibi kullanmanız yeterlidir.

Çoğu zaman, Windows Çalışma Zamanı için .NET Framework desteği saydamdır. Sonraki bölümde, yönetilen kod ve Windows Çalışma Zamanı arasındaki bazı görünür farklılıklar ele alınmaktadır.

<a name="AboutReferenceDocumentation"></a>

### <a name="the-net-framework-and-the-windows-runtime-reference-documentation"></a>.NET Framework ve Windows Çalışma Zamanı başvuru belgeleri

Windows Çalışma Zamanı ve .NET Framework belge kümeleri birbirinden farklıdır. Eğer bir tür veya üyede Yardım'ı görüntülemek için F1'e basarsanız, uygun kümeden başvuru belgeleri görüntülenir. Ancak [Windows çalışma zamanı başvuruya](/uwp/api/) göz atadıysanız, Puzzling görünen örneklerle karşılaşabilirsiniz:

- <xref:Windows.Foundation.Collections.IIterable%601> arabirimi gibi konularda Visual Basic veya C#için bildirim söz dizimi yoktur. Bunun yerine, söz dizimi bölümünün üzerinde bir Note (Bu durumda, ".NET: Bu arabirim System. Collections. Generic. IEnumerable\<T >") gösterilir. Bunun nedeni, .NET Framework ve Windows Çalışma Zamanı farklı arabirimlere benzer işlevler sağlamaktır. Ayrıca, davranışsal farklılıklar da bulunur: numaralandırıcıyı döndürmek için `IIterable`, bir `First` yöntemi yerine bir <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> yöntemine sahiptir. Ortak bir görevi yerine getirmenin farklı bir yolunu öğrenmeye zorlamak yerine .NET Framework, yönetilen kodunuzun bildiğiniz türü kullanacak şekilde görünmesini sağlayarak Windows Çalışma Zamanı destekler. IDE 'de `IIterable` arabirimini görmezsiniz ve bu nedenle, Windows Çalışma Zamanı başvuru belgelerinde onunla karşılaşacağınız tek yol doğrudan bu belgelerde gezinmelidir.

- <xref:Windows.Web.Syndication.SyndicationFeed.%23ctor(System.String,System.String,Windows.Foundation.Uri)> belgelerde yakından ilgili bir sorun görülmektedir: parametre türleri farklı diller için farklı görünüyor. C# ve Visual Basic için, parametre türleri <xref:System.String?displayProperty=nameWithType> ve <xref:System.Uri?displayProperty=nameWithType>'dir. Yine bu durum, .NET Framework kendi `String` ve `Uri` türlerine sahip olduğu içindir ve bunun gibi yaygın şekilde kullanılan türler için .NET Framework kullanıcılarını bunu yapmak üzere farklı bir yol öğrenmeye zorlamak anlamsızdır. IDE 'de .NET Framework, karşılık gelen Windows Çalışma Zamanı türlerini gizler.

- <xref:Windows.UI.Xaml.GridLength> yapısı gibi birkaç durumda .NET Framework, aynı ada ancak daha fazla işlevselliğe sahip bir tür sağlar. Örneğin, bir yapıcı ve özellik konuları kümesi `GridLength` ile ilişkilidir, ancak üyeler yalnızca yönetilen kodda mevcut olduğundan sadece Visual Basic ve #C için söz dizimi blokları vardır. Windows Çalışma Zamanı, yapılar yalnızca alanlara sahiptir. Windows Çalışma Zamanı yapısı, eşdeğer işlevselliği sağlamak için bir yardımcı sınıfı <xref:Windows.UI.Xaml.GridLengthHelper>gerektirir. Yönetilen kodu yazarken bu yardımcı sınıfını IDE'de görmezsiniz.

- IDE 'de, Windows Çalışma Zamanı türler <xref:System.Object?displayProperty=nameWithType>türetmeye görünür. <xref:System.Object> gibi, <xref:System.Object.ToString%2A?displayProperty=nameWithType>'den devralınan üyelere sahip oldukları görünür. Bu Üyeler, türlerin gerçekten <xref:System.Object>Devralındığı ve Windows Çalışma Zamanı türlerinin <xref:System.Object>olarak yayınlanmasının gerektiği gibi çalışır. Bu işlevsellik, Windows Çalışma Zamanı için .NET Framework sağladığı desteğin bir parçasıdır. Ancak, Windows Çalışma Zamanı başvuru belgelerindeki türleri görüntülediğinizde, böyle bir üye görünmez. Görünen bu devralınmış üyelere ait belgeler, <xref:System.Object?displayProperty=nameWithType> başvuru belgeleri tarafından sağlanır.

<a name="DifferencesVisibleInIDE"></a>

### <a name="differences-that-are-visible-in-the-ide"></a>IDE içerisinde Görünür Farklar

JavaScript kullanarak Windows için oluşturulan bir Windows 8. x Mağazası uygulaması için uygulama C# mantığını sağlamak üzere içinde yazılmış bir Windows çalışma zamanı bileşeni kullanma gibi daha gelişmiş programlama senaryolarında, bu farklar IDE 'de ve belgelerde görünür. Bileşeniniz JavaScript 'e bir `IDictionary<int, string>` döndürdüğünde ve JavaScript hata ayıklayıcısında buna baktığınızda, JavaScript Windows Çalışma Zamanı türünü kullandığından, `IMap<int, string>` yöntemlerini görürsünüz. Aşağıdaki tabloda, iki dilde farklı olarak görüntülenen yaygın şekilde kullanılan bazı koleksiyon türleri gösterilmiştir:

|Windows Çalışma Zamanı türü|İlgili .NET Framework türü|
|--------------------------------------------------------------|---------------------------------------|
|`IIterable<T>`|`IEnumerable<T>`|
|`IIterator<T>`|`IEnumerator<T>`|
|`IVector<T>`|`IList<T>`|
|`IVectorView<T>`|`IReadOnlyList<T>`|
|`IMap<K, V>`|`IDictionary<TKey, TValue>`|
|`IMapView<K, V>`|`IReadOnlyDictionary<TKey, TValue>`|
|`IBindableIterable`|`IEnumerable`|
|`IBindableVector`|`IList`|
|`Windows.UI.Xaml.Data.INotifyPropertyChanged`|`System.ComponentModel.INotifyPropertyChanged`|
|`Windows.UI.Xaml.Data.PropertyChangedEventHandler`|`System.ComponentModel.PropertyChangedEventHandler`|
|`Windows.UI.Xaml.Data.PropertyChangedEventArgs`|`System.ComponentModel.PropertyChangedEventArgs`|

Windows Çalışma Zamanı, `IMap<K, V>` ve `IMapView<K, V>` `IKeyValuePair`kullanılarak tekrarlandırılır. Bunları yönetilen koda geçirdiğinizde `IDictionary<TKey, TValue>` ve `IReadOnlyDictionary<TKey, TValue>` olarak görünürler, bu nedenle doğal olarak bunları numaralandırmak için `System.Collections.Generic.KeyValuePair<TKey, TValue>`'i kullanın.

Arabirimlerin yönetilen kodda görüntülenme şekli, bu arabirimlerin uygulanma şeklini etkiler. Örneğin, `PropertySet` sınıfı, yönetilen kodda `IMap<K, V>` olarak görünen `IDictionary<TKey, TValue>`'i uygular. `PropertySet`, `IDictionary<TKey, TValue>` yerine `IMap<K, V>`'i uyguluyormuş gibi görünür, bu nedenle yönetilen kodda, .NET Framework sözlüklerinde `Add` yöntemi gibi davranan bir `Add` yöntemine sahipmiş gibi görünür. Bir `Insert` yöntemine sahipmiş gibi görünmez.

Windows Çalışma Zamanı bileşeni oluşturmak için .NET Framework kullanma hakkında daha fazla bilgi ve JavaScript ile böyle bir bileşeni nasıl kullanacağınızı gösteren bir anlatım için, bkz. [ve Visual Basic üzerinde C# Windows çalışma zamanı bileşenleri oluşturma](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).

### <a name="primitive-types"></a>İlkel Türler

Yönetilen kodda Windows Çalışma Zamanı doğal kullanımını etkinleştirmek için .NET Framework temel türler, kodunuzda Windows Çalışma Zamanı temel türler yerine görünür. .NET Framework'te, `Int32` yapısı gibi ilkel türler, `Int32.TryParse` yöntemi gibi birçok yararlı özellik ve yönteme sahiptir. Buna karşılık, Windows Çalışma Zamanı ilkel türler ve yapılar yalnızca alanlara sahiptir. Yönetilen kodda ilkelleri kullandığınızda, .NET Framework türleri gibi görünürler ve normalde yaptığınız gibi .NET Framework türlerinin özellik ve yöntemlerini kullanabilirsiniz. Aşağıdaki liste bir özet sağlar:

- Windows Çalışma Zamanı temel elemanlar `Int32`, `Int64`, `Single`, `Double`, `Boolean`, `String` (Unicode karakterlerinden oluşan sabit bir koleksiyon), `Enum`, `UInt32`, `UInt64`ve `Guid`için `System` ad alanındaki aynı adın türünü kullanın.

- `UInt8` için `System.Byte`'i kullanın.

- `Char16` için `System.Char`'i kullanın.

- `IInspectable` arabirimi için `System.Object`'i kullanın.

- `HRESULT` için, bir `System.Int32` üyesi olan bir yapı kullanın.

Arabirim türlerinde olduğu gibi, bu gösterimi kanıtı yalnızca, .NET Framework projeniz JavaScript kullanılarak oluşturulan bir Windows 8. x mağaza uygulaması tarafından kullanılan bir Windows Çalışma Zamanı bileşendir.

Yönetilen kodda .NET Framework eşdeğerleri olarak görünen diğer temel, yaygın olarak kullanılan Windows Çalışma Zamanı türleri, <xref:System.DateTimeOffset?displayProperty=nameWithType> yapısı olarak görüntülenen `Windows.Foundation.DateTime` yapısını ve `Windows.Foundation.TimeSpan` yapısı olarak görünen <xref:System.TimeSpan?displayProperty=nameWithType> yapısını içerir.

### <a name="other-differences"></a>Diğer Farklar

Birkaç durumda, .NET Framework türlerin kodunuzda Windows Çalışma Zamanı türler yerine görünmesini, sizin de eylemde bulunması gerekir. Örneğin, <xref:Windows.Foundation.Uri?displayProperty=nameWithType> sınıfı .NET Framework kodda <xref:System.Uri?displayProperty=nameWithType> olarak görünür. <xref:System.Uri?displayProperty=nameWithType> göreli bir URI 'ye izin verir, ancak <xref:Windows.Foundation.Uri?displayProperty=nameWithType> mutlak bir URI gerektirir. Bu nedenle, bir Windows Çalışma Zamanı yöntemine bir URI geçirdiğinizde mutlak olduğundan emin olmanız gerekir. Bkz. [WINDOWS çalışma zamanı URI 'Yi geçirme](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md).

<a name="WindowsRuntimeComponents"></a>

## <a name="scenarios-for-developing-windows-runtime-components"></a>Windows Çalışma Zamanı Bileşenleri Geliştirme Senaryoları

Yönetilen Windows Çalışma Zamanı bileşenleri için desteklenen senaryolar aşağıdaki genel ilkelere bağlıdır:

- .NET Framework kullanılarak oluşturulan Windows Çalışma Zamanı bileşenleri diğer Windows Runtimelibraries hiçbir görünür fark içermez. Örneğin, yönetilen kod kullanarak yerel bir Windows Çalışma Zamanı bileşenini yeniden uygularsanız, iki bileşen outwardly olarak ayırt edilemez. Kodun kendisi yönetilen kod olsa bile bileşeninizin yönetilen kodda yazıldığı gerçeği, bunu kullanan kod için görünmezdir. Ancak, dahili olarak, kodunuz doğru yönetilen koddur ve ortak dil çalışma zamanı (CLR) üzerinde çalışır.

- Bileşenler, uygulama mantığı, Windows 8. x Mağazası UI denetimleri veya her ikisini de uygulayan türler içerebilir.

  > [!NOTE]
  > UI öğelerini uygulama mantığından ayırmak iyi bir yöntemdir. Ayrıca, JavaScript ve HTML kullanarak Windows için oluşturulmuş bir Windows 8. x Mağazası uygulamasında Windows 8. x Mağazası Kullanıcı arabirimi denetimlerini kullanamazsınız.

- Bir bileşen, bir Windows 8. x Mağazası uygulaması için Visual Studio çözümü içindeki bir proje veya birden fazla çözüme ekleyebileceğiniz yeniden kullanılabilir bir bileşen olabilir.

  > [!NOTE]
  > Bileşeniniz yalnızca veya Visual Basic ile C# kullanılacaksa, bunu Windows çalışma zamanı bir bileşen yapmak için bir neden yoktur. Bunun yerine sıradan bir .NET Framework sınıf kitaplığı yaparsanız, ortak API yüzeyini Windows Çalışma Zamanı türlerine kısıtlamak zorunda kalmazsınız.

- Windows Çalışma Zamanı <xref:Windows.Foundation.Metadata.VersionAttribute> özniteliğini kullanarak yeniden kullanılabilir bileşenlerin sürümlerini, hangi türlerin (ve bir tür içindeki hangi üyelerin) farklı sürümlere eklendiğini belirlemek için serbest bırakabilirsiniz.

- Bileşeninizdeki türler Windows Çalışma Zamanı türlerinden türetilebilir. Denetimler <xref:Windows.UI.Xaml.Controls.Primitives> ad alanındaki temel denetim türlerinden veya <xref:Windows.UI.Xaml.Controls.Button>gibi daha fazla tamamlanmış denetimden türetilebilir.

  > [!IMPORTANT]
  > Windows 8 ve .NET Framework 4,5 ' den başlayarak, yönetilen bir Windows Çalışma Zamanı bileşenindeki tüm ortak türler mühürlenmelidir. Başka bir Windows Çalışma Zamanı bileşenindeki bir tür onlardan türetilemez. Eğer bileşeninizde polimorfik davranış sağlamak istiyorsanız, bir arabirim oluşturabilir ve bu arabirimi polimorfik türlere uygulayabilirsiniz.

- Bileşeninizdeki ortak türlerin tüm parametreleri ve dönüş türleri Windows Çalışma Zamanı türler olmalıdır (bileşeninizin tanımladığı Windows Çalışma Zamanı türler dahil).

Aşağıdaki bölümler ortak senaryo örneklerini sağlar.

### <a name="application-logic-for-a-windows-8x-store-app-with-javascript"></a>JavaScript ile Windows 8. x Mağazası uygulaması için uygulama mantığı

JavaScript kullanarak Windows için bir Windows 8. x Mağazası uygulaması geliştirirken, uygulama mantığının bazı bölümlerinin yönetilen kodda daha iyi performans veya geliştirme için daha kolay olduğunu fark edebilirsiniz. JavaScript, .NET Framework sınıf kitaplıklarını doğrudan kullanamaz, ancak bir .WinMD dosyasını sınıf kitaplığı yapabilirsiniz. Bu senaryoda Windows Çalışma Zamanı bileşeni uygulamanın ayrılmaz bir parçasıdır, bu nedenle sürüm öznitelikleri sağlamak mantıklı değildir.

### <a name="reusable-windows-8x-store-ui-controls"></a>Yeniden kullanılabilir Windows 8. x Mağazası Kullanıcı arabirimi denetimleri

Bir dizi ilgili Kullanıcı arabirimi denetimini yeniden kullanılabilir bir Windows Çalışma Zamanı bileşende paketleyebilir. Bileşen kendi üzerinde pazarlanabilir veya kendi oluşturduğunuz uygulamalarda bir öğe olarak kullanılabilir. Bu senaryoda, uyumluluğu geliştirmek için Windows Çalışma Zamanı <xref:Windows.Foundation.Metadata.VersionAttribute> özniteliğini kullanmak mantıklı olur.

### <a name="reusable-application-logic-from-existing-net-framework-apps"></a>Varolan .NET Framework Uygulamalarından Yeniden Kullanılabilir Uygulama Mantığı

Yönetilen kodu, mevcut masaüstü uygulamalarınızdan tek başına Windows Çalışma Zamanı bileşeni olarak paketleyebilir. Bu, bileşeni veya JavaScript kullanılarak C++ oluşturulan Windows 8. x Mağaza uygulamalarında ve C# veya Visual Basic oluşturulan Windows 8. x Mağaza uygulamalarında bileşenini kullanmanıza olanak sağlar. Kod için birden çok yeniden kullanılabilir senaryo varsa sürümleme bir seçenektir.

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Windows Mağazası uygulamalarına yönelik .NET genel bakış](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140))|Windows 8. x Mağazası uygulamaları ve Windows RuntimeComponents oluşturmak için kullanabileceğiniz .NET Framework türlerini ve üyelerini açıklar. (Windows Geliştirme Merkezi'nde.)|
|[Veya Visual Basic kullanarak C# Windows Mağazası uygulamaları için yol haritası](https://docs.microsoft.com/previous-versions/windows/apps/br229583(v=win.10))|Birçok hızlı başlangıç konusu, kılavuz ve en iyi yöntem dahil, veya Visual Basic kullanarak C# Windows 8. x Mağazası uygulamaları geliştirmeye başlamanıza yardımcı olacak önemli kaynaklar sağlar. (Windows Geliştirme Merkezi'nde.)|
|[Nasıl yapılır (XAML)](https://docs.microsoft.com/previous-versions/windows/apps/br229566(v=win.10))|Birçok hızlı başlangıç konusu, kılavuz ve en iyi yöntem dahil, veya Visual Basic kullanarak C# Windows 8. x Mağazası uygulamaları geliştirmeye başlamanıza yardımcı olacak önemli kaynaklar sağlar. (Windows Geliştirme Merkezi'nde.)|
|[Ve Visual Basic içinde C# Windows çalışma zamanı bileşenleri oluşturma](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)|.NET Framework kullanarak bir Windows Çalışma Zamanı bileşeni oluşturmayı açıklar, JavaScript kullanarak Windows için oluşturulmuş bir Windows 8. x mağaza uygulamasının parçası olarak nasıl kullanılacağını açıklar ve Visual Studio ile birlikte nasıl hata ayıklaması yapılacağını açıklar. (Windows Geliştirme Merkezi'nde.)|
|[Windows Çalışma Zamanı başvurusu](/uwp/api/)|Windows Çalışma Zamanı için başvuru belgeleri. (Windows Geliştirme Merkezi'nde.)|
|[URI'yı Windows Çalışma Zamanı'na Geçirme](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md)|Yönetilen koddan Windows Çalışma Zamanı bir URI geçirdiğinizde ortaya çıkabilecek bir sorunu ve bunu nasıl önleyebileceğinizi açıklar.|
