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
ms.openlocfilehash: a51d8d77318685e4a4c8b90a793f2946de4a792b
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025542"
---
# <a name="net-framework-support-for-windows-store-apps-and-windows-runtime"></a>Windows Mağazası Uygulamaları ve Windows Çalışma Zamanı için .NET Framework Desteği
.NET Framework 4.5, Windows çalışma zamanı ile yazılım geliştirme senaryosunu destekler. Bu senaryolar üç kategoriye ayrılır:

- Geliştirme [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] XAML denetimleriyle içinde anlatıldığı gibi uygulamalar [C# veya Visual Basic kullanarak yol haritası için Windows Store apps](https://docs.microsoft.com/previous-versions/windows/apps/br229583(v=win.10)), [nasıl tos (XAML)](https://docs.microsoft.com/previous-versions/windows/apps/br229566(v=win.10)), ve [.NET için Windows Store uygulamalarına genel bakış ](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)).

- .NET Framework ile birlikte oluşturduğunuz [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalarında kullanılmak üzere sınıf kütüphaneleri geliştirme.

- İçinde paketlenmiş, Windows çalışma zamanı bileşenleri geliştirme. WinMD dosyası Windows çalışma zamanını destekleyen tüm programlama dilleri tarafından kullanılabilir. Örneğin, [C# ve Visual Basic'te Windows çalışma zamanı bileşenleri oluşturma](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).

 Bu konuda, .NET Framework üç kategorinin tümü için sağlar ve Windows çalışma zamanı bileşenleri için senaryoları açıklar desteği açıklanmaktadır. İlk bölüm .NET Framework ve Windows çalışma zamanı arasındaki ilişki hakkında temel bilgileri içerir ve Yardım sistemi ve IDE'de karşılaşabileceğiniz bazı farklılıkları açıklar. [İkinci bölüm](#WindowsRuntimeComponents) Windows çalışma zamanı bileşenleri geliştirme senaryolarını anlatır.

## <a name="the-basics"></a>Temeller
 .NET Framework sağlayarak daha önce listelenen üç geliştirme senaryosunu destekler [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], Windows Runtime destekleyerek.

- [.NET framework ve Windows çalışma zamanı ad alanları](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)#net-framework-and-windows-runtime-namespaces) .NET Framework sınıf kitaplıkları kütüphanesi görünümü sağlar ve yalnızca türleri ve oluşturmak için kullanabileceğiniz üyeleri içerir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamaları ve Windows çalışma zamanı bileşenleri.

    - Geliştirme için Visual Studio (Visual Studio 2012 veya üzeri) kullandığınızda bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama veya bir Windows çalışma zamanı bileşeni, başvuru bütünleştirilmiş kodları kümesi sağlar, yalnızca ilgili türleri ve üyeleri görürsünüz.

    - Bu Basitleştirilmiş API kümesi Basitleştirilmiş daha fazla .NET Framework içinde yinelenen ya da Windows çalışma zamanı yinelenen özelliklerin kaldırma işlemi sunar. Örneğin, yalnızca koleksiyon türlerinin genel sürümlerini içerir ve XML belge nesne modeli yerine Windows çalışma zamanı XML API elenir ayarlayın.

    - Windows çalışma zamanı yönetilen koddan çağırmak kolay olduğundan, yalnızca işletim sistemi API'sini sarmalayan özellikler de kaldırılır.

     Hakkında daha fazla bilgi edinmek için [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], bkz: [.NET için Windows Store uygulamalarına genel bakış](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)). API seçim işlemi hakkında bilgi için bkz [Metro style apps için .NET](https://devblogs.microsoft.com/dotnet/net-for-metro-style-apps/) .NET blog girişi.

- [Windows çalışma zamanı](/uwp/api/) kullanıcı arabirimi öğeleri için yapı sağlar. [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalar ve işletim sistemi özelliklerine erişim sağlar. .NET Framework gibi Windows çalışma zamanı sağlayan meta veri olan C# ve Visual Basic derleyicileri, .NET Framework kullandıkları şekilde Windows çalışma zamanı kullanmak için sınıf kitaplıkları. .NET Framework bazı farklılıkları gizleyerek Windows çalışma zamanı kullanmak daha kolay hale getirir:

    - Programlama modelleri arasında .NET Framework ve Windows çalışma zamanı, ekleme ve kaldırma olay işleyicileri, düzen gibi bazı farklılıkları gizlidir. Sadece .NET Framework desenini kullanın.

    - Yaygın olarak kullanılan türlerdeki bazı farklılıklar (örneğin, ilkel türler ve koleksiyonlar) gizlidir. Yalnızca .NET Framework türü bölümünde açıklandığı gibi kullandığınız [görünür farklar IDE'de](#DifferencesVisibleInIDE), bu makalenin ilerleyen bölümlerinde.

 Windows çalışma zamanı için .NET Framework desteği çoğu zaman saydamdır. Sonraki bölümde bazı yönetilen kod ve Windows çalışma zamanı arasında belirgin farklar açıklanmaktadır.

<a name="AboutReferenceDocumentation"></a>
### <a name="the-net-framework-and-the-windows-runtime-reference-documentation"></a>.NET Framework ve Windows çalışma zamanı başvurusu belgeleri
 Windows çalışma zamanı ve .NET Framework belge kümeleri ayrıdır. Eğer bir tür veya üyede Yardım'ı görüntülemek için F1'e basarsanız, uygun kümeden başvuru belgeleri görüntülenir. Ancak, göz atarsanız [Windows çalışma zamanı başvurusu](/uwp/api/) , kafa karıştırıcı örneklerle karşılaşabilirsiniz:

- Gibi konular <xref:Windows.Foundation.Collections.IIterable%601> arabirimi Visual Basic veya C# için bildirim sözdizimi zorunda kalmaz. Bunun yerine, söz dizimi bölümünün üstünde bir not görünür (Bu durumda ".NET: Bu arabirim System.Collections.Generic.IEnumerable görünür\<T > "). .NET Framework ve Windows çalışma zamanı farklı arabirimlerle benzer işlevler sağlayan olmasıdır. Ayrıca, davranışsal farklılıklar da bulunur: numaralandırıcıyı döndürmek için `IIterable`, bir `First` yöntemi yerine bir <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> yöntemine sahiptir. Ortak bir görevi gerçekleştirmek için farklı bir yol öğrenmenizi zorlamak yerine .NET Framework Windows çalışma zamanı yönetilen kodunuzun görüntülenmesini aşina olduğunuz türü kullanmak için yaparak destekler. Göremezsiniz `IIterable` arabirim IDE'de ve bu nedenle karşılaşacağınız, Windows çalışma zamanı başvuru belgelerinde tek yolu bu belgeleri doğrudan göz atarak.

- <xref:Windows.Web.Syndication.SyndicationFeed.%23ctor(System.String,System.String,Windows.Foundation.Uri)> Belgeleri, yakından ilgili bir sorunu gösterir: Parametre türleri farklı diller için farklı görünüyor. C# ve Visual Basic için, parametre türleri <xref:System.String?displayProperty=nameWithType> ve <xref:System.Uri?displayProperty=nameWithType>'dir. Yine bu durum, .NET Framework kendi `String` ve `Uri` türlerine sahip olduğu içindir ve bunun gibi yaygın şekilde kullanılan türler için .NET Framework kullanıcılarını bunu yapmak üzere farklı bir yol öğrenmeye zorlamak anlamsızdır. IDE'de .NET Framework karşılık gelen Windows çalışma zamanı türleri gizler.

- Bazı durumlarda, gibi <xref:Windows.UI.Xaml.GridLength> yapısı, .NET Framework, bir tür ile aynı ada ancak daha fazla işlevsellik sağlar. Örneğin, bir yapıcı ve özellik konuları kümesi `GridLength` ile ilişkilidir, ancak üyeler yalnızca yönetilen kodda mevcut olduğundan sadece Visual Basic ve #C için söz dizimi blokları vardır. Windows çalışma zamanı'nda yapılar yalnızca alanlara sahiptir. Yardımcı bir sınıf, Windows çalışma zamanı yapısı gerektirir <xref:Windows.UI.Xaml.GridLengthHelper>, eşdeğer bir işlevselliği sağlamak için. Yönetilen kodu yazarken bu yardımcı sınıfını IDE'de görmezsiniz.

- IDE içinde Windows çalışma zamanı türleri türetin görünmesini <xref:System.Object?displayProperty=nameWithType>. <xref:System.Object> gibi, <xref:System.Object.ToString%2A?displayProperty=nameWithType>'den devralınan üyelere sahip oldukları görünür. Bu üyeleri türleri gerçekten den devralınmış gibi çalışması <xref:System.Object>, ve Windows çalışma zamanı türleri yayımlanabilir <xref:System.Object>. Bu işlevsellik, .NET Framework Windows çalışma zamanı için sağladığı desteğin bir parçasıdır. Ancak, Windows çalışma zamanı başvuru belgelerindeki türleri görüntülerseniz, bu tür bir üye görüntülenir. Görünen bu devralınmış üyelere ait belgeler, <xref:System.Object?displayProperty=nameWithType> başvuru belgeleri tarafından sağlanır.

<a name="DifferencesVisibleInIDE"></a>
### <a name="differences-that-are-visible-in-the-ide"></a>IDE içerisinde Görünür Farklar
 Daha gelişmiş programlama senaryolarında dilinde yazılmış bir Windows çalışma zamanı bileşeni kullanma gibi C# ait uygulama mantığını sağlamak için bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] JavaScript kullanarak Windows için oluşturulan bir uygulamayı, bu farklara IDE'de de görünür belgeleri. Bileşeniniz döndürdüğünde bir `IDictionary<int, string>` ve JavaScript için JavaScript hata ayıklayıcıda bakmak, yöntemlerini görürsünüz `IMap<int, string>` çünkü Windows çalışma zamanı türü JavaScript kullanır. Aşağıdaki tabloda, iki dilde farklı olarak görüntülenen yaygın şekilde kullanılan bazı koleksiyon türleri gösterilmiştir:

|Windows çalışma zamanı türü|İlgili .NET Framework türü|
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

 Windows çalışma zamanı `IMap<K, V>` ve `IMapView<K, V>` kullanılarak yinelenir `IKeyValuePair`. Bunları yönetilen koda geçirdiğinizde `IDictionary<TKey, TValue>` ve `IReadOnlyDictionary<TKey, TValue>` olarak görünürler, bu nedenle doğal olarak bunları numaralandırmak için `System.Collections.Generic.KeyValuePair<TKey, TValue>`'i kullanın.

 Arabirimlerin yönetilen kodda görüntülenme şekli, bu arabirimlerin uygulanma şeklini etkiler. Örneğin, `PropertySet` sınıfı, yönetilen kodda `IMap<K, V>` olarak görünen `IDictionary<TKey, TValue>`'i uygular. `PropertySet`, `IDictionary<TKey, TValue>` yerine `IMap<K, V>`'i uyguluyormuş gibi görünür, bu nedenle yönetilen kodda, .NET Framework sözlüklerinde `Add` yöntemi gibi davranan bir `Add` yöntemine sahipmiş gibi görünür. Bir `Insert` yöntemine sahipmiş gibi görünmez.

 Bir Windows çalışma zamanı bileşeni ve JavaScript ile benzer bir bileşeni kullanmayı gösteren bir anlatım oluşturmak için .NET Framework kullanma hakkında daha fazla bilgi için bkz. [Windows çalışma zamanı bileşenleri oluşturma C# ve Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).

### <a name="primitive-types"></a>İlkel Türler
 Yönetilen kod içinde Windows çalışma zamanı'nın doğal kullanımını etkinleştirmek için kodunuzdaki Windows çalışma zamanı ilkel türleri yerine .NET Framework ilkel türleri görünür. .NET Framework'te, `Int32` yapısı gibi ilkel türler, `Int32.TryParse` yöntemi gibi birçok yararlı özellik ve yönteme sahiptir. Bunun aksine, temel eleman türleri ve Windows çalışma zamanı yapılar yalnızca alanlara sahiptir. Yönetilen kodda ilkelleri kullandığınızda, .NET Framework türleri gibi görünürler ve normalde yaptığınız gibi .NET Framework türlerinin özellik ve yöntemlerini kullanabilirsiniz. Aşağıdaki liste bir özet sağlar:

- Windows çalışma zamanı temelleri için `Int32`, `Int64`, `Single`, `Double`, `Boolean`, `String` (sabit bir koleksiyonu Unicode karakterleri), `Enum`, `UInt32`, `UInt64`, ve `Guid`, aynı adı kullanın `System` ad alanı.

- `UInt8` için `System.Byte`'i kullanın.

- `Char16` için `System.Char`'i kullanın.

- `IInspectable` arabirimi için `System.Object`'i kullanın.

- `HRESULT` için, bir `System.Int32` üyesi olan bir yapı kullanın.

 Arabirim türlerinde olduğu bu sunumun kanıtını görmek yalnızca bir kez zaman.NET Framework projenizin tarafından kullanılan bir Windows çalışma zamanı bileşeni olduğu gibi bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] JavaScript kullanılarak oluşturulmuş.

 Kendi .NET Framework eşdeğerleri yönetilen kodda görünen diğer temel, yaygın olarak kullanılan Windows çalışma zamanı türleri `Windows.Foundation.DateTime` yönetilen kodda görünen yapısı <xref:System.DateTimeOffset?displayProperty=nameWithType> yapısını ve `Windows.Foundation.TimeSpan` yapısı, hangi görünür <xref:System.TimeSpan?displayProperty=nameWithType> yapısı.

### <a name="other-differences"></a>Diğer Farklar
 Bazı durumlarda, .NET Framework türlerinin kodunuzda Windows çalışma zamanı türleri yerine görünen olgu sizin eyleminizi gerektirir. Örneğin, <xref:Windows.Foundation.Uri?displayProperty=nameWithType> sınıfı olarak görünür <xref:System.Uri?displayProperty=nameWithType> .NET Framework kodunda. <xref:System.Uri?displayProperty=nameWithType> bir göreli URİ'yi sağlar ancak <xref:Windows.Foundation.Uri?displayProperty=nameWithType> bir mutlak URI gerektirir. Bu nedenle, bir Windows çalışma zamanı yöntemine bir URI başarıyla sonuçlandıktan sonra bunun mutlak olduğundan emin olmalısınız. (Bkz [Windows çalışma zamanı için bir URI geçirme](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md).)

<a name="WindowsRuntimeComponents"></a>
## <a name="scenarios-for-developing-windows-runtime-components"></a>Windows Çalışma Zamanı Bileşenleri Geliştirme Senaryoları
 Yönetilen Windows çalışma zamanı bileşenleri için desteklenen senaryolar aşağıdaki genel ilkelere bağlıdır:

- .NET Framework kullanılarak oluşturulan bir Windows çalışma zamanı bileşenleri diğer Windows Runtimelibraries gelen hiçbir belirgin farklar sahip. Örneğin, yerel bir Windows çalışma zamanı bileşeni yönetilen kod kullanarak yeniden uygularsanız, iki bileşeni ayırt edilemezler. Kodun kendisi yönetilen kod olsa bile bileşeninizin yönetilen kodda yazıldığı gerçeği, bunu kullanan kod için görünmezdir. Ancak, dahili olarak, kodunuz doğru yönetilen koddur ve ortak dil çalışma zamanı (CLR) üzerinde çalışır.

- Bileşenler, uygulama mantığını uygulayan türleri, [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] UI denetimlerini veya her ikisi içerebilir.

    > [!NOTE]
    >  UI öğelerini uygulama mantığından ayırmak iyi bir yöntemdir. Ayrıca, JavaScript ve HTML kullanılarak Windows için oluşturulmuş bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamasında [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] UI denetimlerini kullanamazsınız.

- Bir bileşen, bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamaya ait bir Visual Studio çözümü içinde bir proje veya çoklu çözümlere ekleyebileceğiniz yeniden kullanılabilir bir bileşen olabilir.

    > [!NOTE]
    >  Bileşeniniz sadece ile kullanılacaksa C# veya Visual Basic'te Windows çalışma zamanı bileşeni yapmaya gerek yoktur. Sıradan bir .NET Framework sınıf kitaplığı yerine değişiklik yaparsanız, ortak API yüzeyini Windows çalışma zamanı türleriyle sınırlamak zorunda değilsiniz.

- Windows çalışma zamanı'nı kullanarak yeniden kullanılabilir bileşenlerin sürümlerini yayınlamadan <xref:Windows.Foundation.Metadata.VersionAttribute> hangi türlerin (ve bir tür içinde hangi üyelerin) tanımlamak için öznitelik farklı sürümlerde eklendi.

- Bileşeninizdeki türler, Windows çalışma zamanı türleri türetebilirsiniz. Denetimleri alanındaki ilkel denetim türlerinden türeyebilir <xref:Windows.UI.Xaml.Controls.Primitives> ad alanı veya denetimler gibi daha tamamlanmış <xref:Windows.UI.Xaml.Controls.Button>.

    > [!IMPORTANT]
    >  İle başlayarak [!INCLUDE[win8](../../../includes/win8-md.md)] ve .NET Framework 4.5, yönetilen bir Windows çalışma zamanı bileşeni tüm ortak türlerin mühürlenmesi gerekir. Başka bir Windows çalışma zamanı bileşeni tür bunlardan türetilemez. Eğer bileşeninizde polimorfik davranış sağlamak istiyorsanız, bir arabirim oluşturabilir ve bu arabirimi polimorfik türlere uygulayabilirsiniz.

- Bileşeninizin genel türlerindeki tüm parametre ve dönüş türlerinin, Windows çalışma zamanı türleri (bileşeninizin tanımladığı Windows çalışma zamanı türleri dahil) olmalıdır.

 Aşağıdaki bölümler ortak senaryo örneklerini sağlar.

### <a name="application-logic-for-a-includewin8appnamelongincludeswin8-appname-long-mdmd-app-with-javascript"></a>JavaScript olan bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] Uygulaması için Uygulama Mantığı
 JavaScript kullanarak Windows için bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulaması geliştirdiğinizde, uygulama mantığının bazı kısımlarının yönetilen kodda daha iyi çalıştığını veya daha kolay geliştirildiğini fark edebilirsiniz. JavaScript, .NET Framework sınıf kitaplıklarını doğrudan kullanamaz, ancak bir .WinMD dosyasını sınıf kitaplığı yapabilirsiniz. Bu senaryoda, Windows çalışma zamanı bileşeni uygulama ayrılmaz bir parçası olduğundan, sürüm özniteliklerinin sağlanması mantıksızdır.

### <a name="reusable-includewin8appnamelongincludeswin8-appname-long-mdmd-ui-controls"></a>Yeniden Kullanılabilir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] UI Denetimleri
 Yeniden kullanılabilir bir Windows çalışma zamanı bileşeni ilgili UI denetimleri kümesini paketleyebilirsiniz. Bileşen kendi üzerinde pazarlanabilir veya kendi oluşturduğunuz uygulamalarda bir öğe olarak kullanılabilir. Bu senaryoda, Windows çalışma zamanı kullanmak için mantıklı <xref:Windows.Foundation.Metadata.VersionAttribute> uyumluluğu artırmak için özniteliği.

### <a name="reusable-application-logic-from-existing-net-framework-apps"></a>Varolan .NET Framework Uygulamalarından Yeniden Kullanılabilir Uygulama Mantığı
 Varolan Masaüstü uygulamalarınızdan yönetilen kod bir tek başına Windows çalışma zamanı bileşeni olarak paketleyebilirsiniz. Bu, bileşeni, C++ veya Visual Basic kullanılarak oluşturulan [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]  uygulamalarının yanı sıra C# veya JavaScript kullanılarak oluşturulan [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalarında da kullanmanızı sağlar. Kod için birden çok yeniden kullanılabilir senaryo varsa sürümleme bir seçenektir.

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[.NET için Windows Store uygulamalarına genel bakış](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140))|.NET Framework türlerini ve oluşturmak için kullanabileceğiniz üyeleri açıklar [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamaları ve Windows RuntimeComponents. (Windows Geliştirme Merkezi'nde.)|
|[C# veya Visual Basic kullanan Windows Store uygulamaları için yol haritası](https://docs.microsoft.com/previous-versions/windows/apps/br229583(v=win.10))|Bir çok Hızlı Başlangıç konuları, kılavuzlar ve en iyi yöntemleri dahil olmak üzere C# veya Visual Basic kullanarak [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamaları geliştirmeye başlamanıza yardımcı olan anahtar kaynaklar sağlar. (Windows Geliştirme Merkezi'nde.)|
|[Nasıl yapılır makaleleri (XAML)](https://docs.microsoft.com/previous-versions/windows/apps/br229566(v=win.10))|Bir çok Hızlı Başlangıç konuları, kılavuzlar ve en iyi yöntemleri dahil olmak üzere C# veya Visual Basic kullanarak [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamaları geliştirmeye başlamanıza yardımcı olan anahtar kaynaklar sağlar. (Windows Geliştirme Merkezi'nde.)|
|[C# ve Visual Basic'te Windows çalışma zamanı bileşenleri oluşturma](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)|.NET Framework kullanarak bir Windows çalışma zamanı bileşeni oluşturma işlemini açıklar, bir parçası olarak kullanmayı açıklar bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama JavaScript kullanarak Windows için oluşturulan ve hata ayıklama Visual Studio ile kombinasyonda nasıl açıklar. (Windows Geliştirme Merkezi'nde.)|
|[Windows çalışma zamanı başvurusu](/uwp/api/)|Windows çalışma zamanı için başvuru belgeleri. (Windows Geliştirme Merkezi'nde.)|
|[URI'yı Windows Çalışma Zamanı'na Geçirme](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md)|Yönetilen koddan bir URI'yı Windows çalışma zamanı ve bunun nasıl önleneceğini başarılı olduğunda oluşabilecek bir sorunu açıklar.|
