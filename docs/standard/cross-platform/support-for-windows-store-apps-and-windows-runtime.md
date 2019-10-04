---
title: Windows Mağazası uygulamaları ve Windows Çalışma Zamanı için .NET Framework desteği
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
ms.openlocfilehash: 2f46d21123ecfda4bd336edbbd79fabf01e002a4
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835337"
---
# <a name="net-framework-support-for-windows-store-apps-and-windows-runtime"></a>Windows Mağazası uygulamaları ve Windows Çalışma Zamanı için .NET Framework desteği

.NET Framework 4,5 Windows Çalışma Zamanı bir dizi yazılım geliştirme senaryosunu destekler. Bu senaryolar üç kategoriye ayrılır:

- [Veya Visual Basic C# kullanan Windows Mağazası uygulamaları için yol haritası](https://docs.microsoft.com/previous-versions/windows/apps/br229583(v=win.10))bölümünde açıklandığı gibi XAML denetimleriyle [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamaları geliştirme, [Windows Mağazası UYGULAMALARıNA yönelik](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)) [Nasıl TOS (XAML)](https://docs.microsoft.com/previous-versions/windows/apps/br229566(v=win.10))ve .net hakkında genel bakış.

- .NET Framework ile oluşturduğunuz [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalarında kullanılmak üzere sınıf kitaplıkları geliştirme.

- ' De paketlenmiş Windows Çalışma Zamanı bileşenleri geliştirme. Windows Çalışma Zamanı destekleyen herhangi bir programlama dili tarafından kullanılabilen WinMD dosyaları. Örneğin, [ve Visual Basic ' de C# Windows çalışma zamanı bileşenleri oluşturma](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)konusuna bakın.

Bu konuda, .NET Framework üç kategori için sağladığı destek özetlenmektedir ve Windows Çalışma Zamanı bileşenlere yönelik senaryolar açıklanmaktadır. İlk bölüm, .NET Framework ve Windows Çalışma Zamanı arasındaki ilişki hakkında temel bilgileri içerir ve yardım sisteminde ve IDE 'de karşılaşabileceğiniz bazı odlıtıes 'leri açıklar. [İkinci bölümde](#WindowsRuntimeComponents) Windows çalışma zamanı bileşenleri geliştirmeye yönelik senaryolar açıklanmaktadır.

## <a name="the-basics"></a>Temel bilgiler

.NET Framework, daha önce [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] sağlayarak ve Windows Çalışma Zamanı kendisini destekleyerek listelenen üç geliştirme senaryosunu destekler.

- [.NET Framework ve Windows çalışma zamanı ad alanları](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)#net-framework-and-windows-runtime-namespaces) .NET Framework sınıf kitaplıklarının kolaylaştırılmış bir görünümünü sağlar ve yalnızca [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamaları ve Windows çalışma zamanı bileşenleri oluşturmak için kullanabileceğiniz türleri ve üyeleri içerir.

  - @No__t-0 uygulaması veya Windows Çalışma Zamanı bileşeni geliştirmek için Visual Studio 'Yu (Visual Studio 2012 veya üzeri) kullandığınızda, bir başvuru derlemeleri kümesi yalnızca ilgili türleri ve üyeleri görmenizi sağlar.

  - Bu kolaylaştırılmış API kümesi, .NET Framework içinde çoğaltılan özelliklerin veya yinelenen Windows Çalışma Zamanı özelliklerinin kaldırılmasına göre basitleştirilmiştir. Örneğin, koleksiyon türlerinin yalnızca genel sürümlerini içerir ve XML belge nesne modeli Windows Çalışma Zamanı XML API kümesi tarafından da ortadan kalkar.

  - Yalnızca işletim sistemi API 'sini sardığı özellikler de kaldırılır, çünkü Windows Çalışma Zamanı yönetilen koddan kolayca çağrı yapılır.

  @No__t-0 hakkında daha fazla bilgi edinmek için bkz. [Windows Mağazası uygulamalarına yönelik .NET genel bakış](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)). API seçim işlemi hakkında bilgi edinmek için .NET blogdaki [Metro stili uygulamalar için .net](https://devblogs.microsoft.com/dotnet/net-for-metro-style-apps/) başlığına bakın.

- [Windows çalışma zamanı](/uwp/api/) , [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamaları oluşturmaya yönelik kullanıcı arabirimi öğelerini sağlar ve işletim sistemi özelliklerine erişim sağlar. .NET Framework gibi Windows Çalışma Zamanı, C# ve Visual Basic derleyicilerinin .NET Framework sınıf kitaplıklarını kullandıkları gibi Windows çalışma zamanı kullanmasını sağlayan meta verilere sahiptir. .NET Framework, bazı farkları gizleyerek Windows Çalışma Zamanı kullanmayı kolaylaştırır:

  - Olay işleyicilerini ekleme ve kaldırma deseni gibi .NET Framework ve Windows Çalışma Zamanı arasındaki programlama desenleriyle ilgili bazı farklılıklar gizlidir. .NET Framework modelini kullanmanız yeterlidir.

  - Yaygın olarak kullanılan türlerde bazı farklılıklar (örneğin, ilkel türler ve koleksiyonlar) gizlidir. .NET Framework türünü, bu makalenin ilerleyen kısımlarında [IDE 'de görünür olan farklılıklar](#DifferencesVisibleInIDE)bölümünde anlatıldığı gibi kullanmanız yeterlidir.

Çoğu zaman, Windows Çalışma Zamanı için .NET Framework desteği saydamdır. Sonraki bölümde, yönetilen kod ve Windows Çalışma Zamanı arasındaki bazı görünür farklılıklar ele alınmaktadır.

<a name="AboutReferenceDocumentation"></a>

### <a name="the-net-framework-and-the-windows-runtime-reference-documentation"></a>.NET Framework ve Windows Çalışma Zamanı başvuru belgeleri

Windows Çalışma Zamanı ve .NET Framework belge kümeleri birbirinden farklıdır. Bir tür veya üye üzerindeki Yardımı göstermek için F1 tuşuna basarsanız, uygun kümeden başvuru belgeleri görüntülenir. Ancak [Windows çalışma zamanı başvuruya](/uwp/api/) göz atadıysanız, Puzzling görünen örneklerle karşılaşabilirsiniz:

- @No__t-0 arabirimi gibi konularda Visual Basic veya C#için bildirim söz dizimi yoktur. Bunun yerine, söz dizimi bölümünün üzerinde bir Note (Bu durumda, ".NET: Bu arabirim System. Collections. Generic. IEnumerable @ no__t-0T >") üzerinde görünür. Bunun nedeni, .NET Framework ve Windows Çalışma Zamanı farklı arabirimlere benzer işlevler sağlamaktır. Ayrıca, davranış farklılıkları vardır: `IIterable`, Numaralandırıcı döndürmek için <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> yöntemi yerine `First` yöntemine sahiptir. Ortak bir görevi yerine getirmenin farklı bir yolunu öğrenmeye zorlamak yerine .NET Framework, yönetilen kodunuzun bildiğiniz türü kullanacak şekilde görünmesini sağlayarak Windows Çalışma Zamanı destekler. IDE 'de `IIterable` arabirimini görmezsiniz ve bu nedenle, Windows Çalışma Zamanı başvuru belgelerinde onunla karşılaşacağınız tek yol doğrudan bu belgelerde gezinmelidir.

- @No__t-0 belgelerinde yakından ilgili bir sorun görülmektedir: parametre türleri farklı diller için farklı görünüyor. Ve C# Visual Basic için parametre türleri <xref:System.String?displayProperty=nameWithType> ve <xref:System.Uri?displayProperty=nameWithType> ' dir. Bunun nedeni, .NET Framework kendi `String` ve `Uri` türlerine sahip olması ve bu tür yaygın olarak kullanılan türler için, .NET Framework kullanıcılarına şeyler yaparken farklı bir yöntem öğrenmeyi zorlamaktır. IDE 'de .NET Framework, karşılık gelen Windows Çalışma Zamanı türlerini gizler.

- @No__t-0 yapısı gibi birkaç durumda .NET Framework, aynı ada ancak daha fazla işlevselliğe sahip bir tür sağlar. Örneğin, bir Oluşturucu ve özellik konuları kümesi `GridLength` ile ilişkilendirilir, ancak yalnızca Visual Basic ve C# üyeleri yönetilen kodda kullanılabilir olduğundan söz dizimi blokları vardır. Windows Çalışma Zamanı, yapılar yalnızca alanlara sahiptir. Windows Çalışma Zamanı yapısı, eşdeğer işlevselliği sağlamak için bir yardımcı sınıfı <xref:Windows.UI.Xaml.GridLengthHelper> gerektirir. Yönetilen kodu yazarken IDE 'de bu yardımcı sınıfı görmezsiniz.

- IDE 'de Windows Çalışma Zamanı türler <xref:System.Object?displayProperty=nameWithType> ' dan türeme görünür. @No__t-0 ' dan devralınan üyelere sahip oldukları gibi görünürler (<xref:System.Object.ToString%2A?displayProperty=nameWithType> gibi). Bu Üyeler, türlerin gerçekten <xref:System.Object> ' dan Devralındığı ve Windows Çalışma Zamanı türlerinin <xref:System.Object> ' e yayınlanmasının gerektiği gibi çalışır. Bu işlevsellik, Windows Çalışma Zamanı için .NET Framework sağladığı desteğin bir parçasıdır. Ancak, Windows Çalışma Zamanı başvuru belgelerindeki türleri görüntülediğinizde, böyle bir üye görünmez. Bu belirgin devralınan üyelere yönelik belgeler <xref:System.Object?displayProperty=nameWithType> başvuru belgeleriyle sağlanır.

<a name="DifferencesVisibleInIDE"></a>

### <a name="differences-that-are-visible-in-the-ide"></a>IDE 'de görünür olan farklılıklar

JavaScript kullanarak Windows için derlenmiş bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulaması için uygulama mantığını sağlamak C# üzere içinde yazılmış Windows çalışma zamanı bileşeni kullanma gibi daha gelişmiş programlama senaryolarında, bu farklar IDE 'de ve belgelerde görünür. Bileşeniniz JavaScript 'e `IDictionary<int, string>` ' ı döndürdüğünde ve JavaScript hata ayıklayıcısında buna baktığınızda, JavaScript Windows Çalışma Zamanı türünü kullandığından, `IMap<int, string>` ' in yöntemlerini görürsünüz. İki dilde farklı şekilde görüntülenen bazı yaygın olarak kullanılan koleksiyon türleri aşağıdaki tabloda gösterilmiştir:

|Windows Çalışma Zamanı türü|Karşılık gelen .NET Framework türü|
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

Windows Çalışma Zamanı, `IMap<K, V>` ve `IMapView<K, V>` `IKeyValuePair` kullanılarak tekrarlandırılır. Bunları yönetilen koda geçirdiğinizde, `IDictionary<TKey, TValue>` ve `IReadOnlyDictionary<TKey, TValue>` olarak görünürler, doğal olarak `System.Collections.Generic.KeyValuePair<TKey, TValue>` kullanarak bunları numaralandırın.

Arabirimlerin yönetilen kodda görünme yöntemi, bu arabirimleri uygulayan türlerin görünme şeklini etkiler. Örneğin `PropertySet` sınıfı, yönetilen kodda `IDictionary<TKey, TValue>` olarak görünen `IMap<K, V>` uygular. `PropertySet` `IMap<K, V>` yerine 1 @no__t uygulamış gibi görünür, bu nedenle yönetilen kodda @no__t sözlüklerde .NET Framework-4 yöntemi gibi davranan bir `Add` yöntemine sahip olduğu görülüyor. @No__t-0 yöntemine sahip görünmüyor.

Windows Çalışma Zamanı bileşeni oluşturmak için .NET Framework kullanma hakkında daha fazla bilgi ve JavaScript ile böyle bir bileşeni nasıl kullanacağınızı gösteren bir anlatım için, bkz. [ve Visual Basic üzerinde C# Windows çalışma zamanı bileşenleri oluşturma](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).

### <a name="primitive-types"></a>İlkel türler

Yönetilen kodda Windows Çalışma Zamanı doğal kullanımını etkinleştirmek için .NET Framework temel türler, kodunuzda Windows Çalışma Zamanı temel türler yerine görünür. .NET Framework, `Int32` yapısı gibi basit türler `Int32.TryParse` yöntemi gibi birçok yararlı özellik ve yönteme sahiptir. Buna karşılık, Windows Çalışma Zamanı ilkel türler ve yapılar yalnızca alanlara sahiptir. Yönetilen kodda temel elemanlar kullandığınızda, bunlar .NET Framework gibi görünürler ve normalde yaptığınız gibi .NET Framework türlerinin özelliklerini ve yöntemlerini kullanabilirsiniz. Aşağıdaki listede bir Özet verilmiştir:

- Windows Çalışma Zamanı temel elemanlar için `Int32`, `Int64`, `Single`, `Double`, `Boolean`, `String` (Unicode karakterlerinden oluşan sabit bir koleksiyon), `Enum`, `UInt32`, `UInt64` ve `Guid`, 0 ad alanında aynı adın türünü kullanır.

- @No__t-0 için `System.Byte` kullanın.

- @No__t-0 için `System.Char` kullanın.

- @No__t-0 arabirimi için `System.Object` ' i kullanın.

- @No__t-0 için, bir `System.Int32` üyesi olan bir yapı kullanın.

Arabirim türlerinde olduğu gibi, bu gösterimi yalnızca, .NET Framework projeniz JavaScript kullanılarak oluşturulan [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] bir uygulama tarafından kullanılan Windows Çalışma Zamanı bir bileşen olduğunda görürsünüz.

Yönetilen kodda .NET Framework eşdeğerleri olarak görünen diğer temel, yaygın olarak kullanılan Windows Çalışma Zamanı türleri, <xref:System.DateTimeOffset?displayProperty=nameWithType> yapısı olarak yönetilen kodda görünen `Windows.Foundation.DateTime` yapısını ve <xref:System.TimeSpan?displayProperty=nameWithType> olarak görünen @no__t 2 yapısını içerir yapısı.

### <a name="other-differences"></a>Diğer farklılıklar

Birkaç durumda, .NET Framework türlerin kodunuzda Windows Çalışma Zamanı türler yerine görünmesini, sizin de eylemde bulunması gerekir. Örneğin, <xref:Windows.Foundation.Uri?displayProperty=nameWithType> sınıfı .NET Framework kodda <xref:System.Uri?displayProperty=nameWithType> olarak görünür. <xref:System.Uri?displayProperty=nameWithType> göreli bir URI 'ye izin verir, ancak <xref:Windows.Foundation.Uri?displayProperty=nameWithType> mutlak bir URI gerektirir. Bu nedenle, bir Windows Çalışma Zamanı yöntemine bir URI geçirdiğinizde mutlak olduğundan emin olmanız gerekir. Bkz. [WINDOWS çalışma zamanı URI 'Yi geçirme](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md).

<a name="WindowsRuntimeComponents"></a>

## <a name="scenarios-for-developing-windows-runtime-components"></a>Windows Çalışma Zamanı bileşenleri geliştirmeye yönelik senaryolar

Yönetilen Windows Çalışma Zamanı bileşenleri için desteklenen senaryolar aşağıdaki genel ilkelere bağlıdır:

- .NET Framework kullanılarak oluşturulan Windows Çalışma Zamanı bileşenleri diğer Windows Runtimelibraries hiçbir görünür fark içermez. Örneğin, yönetilen kod kullanarak yerel bir Windows Çalışma Zamanı bileşenini yeniden uygularsanız, iki bileşen outwardly olarak ayırt edilemez. Bileşeninizin yönetilen kodda yazıldığı olgu, bu kodun kendisi tarafından yönetilen kodu olsa bile, onu kullanan koda görünmez. Ancak, dahili olarak, bileşeniniz doğru yönetilen koddur ve ortak dil çalışma zamanı (CLR) üzerinde çalıştırılır.

- Bileşenler, uygulama mantığını, [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] Kullanıcı arabirimi denetimlerini veya her ikisini de uygulayan türler içerebilir.

  > [!NOTE]
  > UI öğelerini uygulama mantığınızdan ayırmak iyi bir uygulamadır. Ayrıca, JavaScript ve HTML kullanarak Windows için oluşturulmuş bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamasındaki [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] Kullanıcı arabirimi denetimlerini kullanamazsınız.

- Bir bileşen [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulaması veya birden fazla çözüme ekleyebileceğiniz yeniden kullanılabilir bir bileşen için Visual Studio çözümü içindeki bir proje olabilir.

  > [!NOTE]
  > Bileşeniniz yalnızca veya Visual Basic ile C# kullanılacaksa, bunu Windows çalışma zamanı bir bileşen yapmak için bir neden yoktur. Bunun yerine sıradan bir .NET Framework sınıf kitaplığı yaparsanız, ortak API yüzeyini Windows Çalışma Zamanı türlerine kısıtlamak zorunda kalmazsınız.

- Windows Çalışma Zamanı <xref:Windows.Foundation.Metadata.VersionAttribute> özniteliğini kullanarak yeniden kullanılabilir bileşenlerin sürümlerini, hangi türlerin (ve bir tür içindeki hangi üyelerin) farklı sürümlere eklendiğini belirlemek için serbest bırakabilirsiniz.

- Bileşeninizdeki türler Windows Çalışma Zamanı türlerinden türetilebilir. Denetimler <xref:Windows.UI.Xaml.Controls.Primitives> ad alanındaki temel denetim türlerinden veya <xref:Windows.UI.Xaml.Controls.Button> gibi daha fazla tamamlanmış denetimden türetilebilir.

  > [!IMPORTANT]
  > @No__t-0 ve .NET Framework 4,5 ' den başlayarak, bir yönetilen Windows Çalışma Zamanı bileşenindeki tüm ortak türlerin mühürlenmesi gerekir. Başka bir Windows Çalışma Zamanı bileşenindeki bir tür onlardan türetilemez. Bileşeninize polimorfik davranış sağlamak istiyorsanız, bir arabirim oluşturabilir ve bunu polimorfik türlerde uygulayabilirsiniz.

- Bileşeninizdeki ortak türlerin tüm parametreleri ve dönüş türleri Windows Çalışma Zamanı türler olmalıdır (bileşeninizin tanımladığı Windows Çalışma Zamanı türler dahil).

Aşağıdaki bölümlerde yaygın senaryolar örnekleri sağlanmaktadır.

### <a name="application-logic-for-a-includewin8_appname_longincludeswin8-appname-long-mdmd-app-with-javascript"></a>JavaScript ile [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulaması için uygulama mantığı

JavaScript kullanarak Windows için [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulaması geliştirirken, uygulama mantığının bazı bölümlerinin yönetilen kodda daha iyi performans veya geliştirilmesine daha kolay olduğunu fark edebilirsiniz. JavaScript .NET Framework sınıf kitaplıklarını doğrudan kullanamaz, ancak sınıf kitaplığını a yapabilirsiniz. WinMD dosyası. Bu senaryoda Windows Çalışma Zamanı bileşeni uygulamanın ayrılmaz bir parçasıdır, bu nedenle sürüm öznitelikleri sağlamak mantıklı değildir.

### <a name="reusable-includewin8_appname_longincludeswin8-appname-long-mdmd-ui-controls"></a>Yeniden kullanılabilir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] UI denetimleri

Bir dizi ilgili Kullanıcı arabirimi denetimini yeniden kullanılabilir bir Windows Çalışma Zamanı bileşende paketleyebilir. Bileşen kendi kendine pazarlama yapabilir veya oluşturduğunuz uygulamalarda bir öğe olarak kullanılabilir. Bu senaryoda, uyumluluğu geliştirmek için Windows Çalışma Zamanı <xref:Windows.Foundation.Metadata.VersionAttribute> özniteliğini kullanmak mantıklı olur.

### <a name="reusable-application-logic-from-existing-net-framework-apps"></a>Mevcut .NET Framework uygulamalardan yeniden kullanılabilir uygulama mantığı

Yönetilen kodu, mevcut masaüstü uygulamalarınızdan tek başına Windows Çalışma Zamanı bileşeni olarak paketleyebilir. Bu, bileşeni, veya JavaScript kullanılarak C++ oluşturulan [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalarında ve C# veya Visual Basic oluşturulan @no__t 2 uygulamalarında kullanmanıza olanak sağlar. Kod için birden çok yeniden kullanım senaryosu varsa, sürüm oluşturma bir seçenektir.

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Windows Mağazası uygulamalarına yönelik .NET genel bakış](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140))|@No__t-0 uygulamaları ve Windows RuntimeComponents oluşturmak için kullanabileceğiniz .NET Framework türlerini ve üyelerini açıklar. (Windows Geliştirme Merkezi 'nde.)|
|[Veya Visual Basic kullanarak C# Windows Mağazası uygulamaları için yol haritası](https://docs.microsoft.com/previous-versions/windows/apps/br229583(v=win.10))|Birçok hızlı başlangıç konusu, kılavuz ve en iyi yöntem dahil olmak üzere veya Visual Basic C# kullanarak [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamaları geliştirmeye başlamanıza yardımcı olacak temel kaynakları sağlar. (Windows Geliştirme Merkezi 'nde.)|
|[Nasıl yapılır (XAML)](https://docs.microsoft.com/previous-versions/windows/apps/br229566(v=win.10))|Birçok hızlı başlangıç konusu, kılavuz ve en iyi yöntem dahil olmak üzere veya Visual Basic C# kullanarak [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamaları geliştirmeye başlamanıza yardımcı olacak temel kaynakları sağlar. (Windows Geliştirme Merkezi 'nde.)|
|[Ve Visual Basic içinde C# Windows çalışma zamanı bileşenleri oluşturma](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)|.NET Framework kullanarak Windows Çalışma Zamanı bileşenin nasıl oluşturulduğunu açıklar, JavaScript kullanarak Windows için oluşturulan [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamasının bir parçası olarak nasıl kullanılacağını açıklar ve Visual Studio ile birlikte nasıl hata ayıklaması yapılacağını açıklar. (Windows Geliştirme Merkezi 'nde.)|
|[Windows Çalışma Zamanı başvurusu](/uwp/api/)|Windows Çalışma Zamanı için başvuru belgeleri. (Windows Geliştirme Merkezi 'nde.)|
|[Windows Çalışma Zamanı URI geçirme](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md)|Yönetilen koddan Windows Çalışma Zamanı bir URI geçirdiğinizde ortaya çıkabilecek bir sorunu ve bunu nasıl önleyebileceğinizi açıklar.|
