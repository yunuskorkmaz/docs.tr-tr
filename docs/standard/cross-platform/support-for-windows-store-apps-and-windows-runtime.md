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
ms.openlocfilehash: 750bddce508a72c6aaac659feac90b7c17e53137
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708411"
---
# <a name="net-framework-support-for-windows-store-apps-and-windows-runtime"></a>Windows Mağazası Uygulamaları ve Windows Çalışma Zamanı için .NET Framework Desteği

  [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], [!INCLUDE[wrt](../../../includes/wrt-md.md)] ile birlikte çok sayıda yazılım geliştirme senaryosunu destekler. Bu senaryolar üç kategoriye ayrılır:

-   Geliştirme [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] XAML denetimleriyle içinde anlatıldığı gibi uygulamalar [C# veya Visual Basic kullanarak yol haritası için Windows Store apps](https://docs.microsoft.com/previous-versions/windows/apps/br229583(v=win.10)), [nasıl tos (XAML)](https://docs.microsoft.com/previous-versions/windows/apps/br229566(v=win.10)), ve [.NET için Windows Store uygulamalarına genel bakış ](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)).

-   .NET Framework ile birlikte oluşturduğunuz [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalarında kullanılmak üzere sınıf kütüphaneleri geliştirme.

-   
  [!INCLUDE[wrt](../../../includes/wrt-md.md)]'i destekleyen tüm programlama dilleri tarafından kullanabilen, .WinMD dosyalarında paketlenmiş [!INCLUDE[wrt](../../../includes/wrt-md.md)] Bileşenleri geliştirme. Örneğin, [C# ve Visual Basic'te Windows çalışma zamanı bileşenleri oluşturma](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).

 Bu konu, .NET Framework'ün üç kategorinin tümü için sağladığı desteği ve [!INCLUDE[wrt](../../../includes/wrt-md.md)] Bileşenleri için senaryoları açıklar. İlk bölüm .NET Framework ve [!INCLUDE[wrt](../../../includes/wrt-md.md)] arasındaki temel ilişki hakkındaki temel bilgileri içerir ve Yardım sistemi ve IDE'de karşılaşabileceğiniz bazı farklılıkları açıklar. [İkinci bölüm](#WindowsRuntimeComponents) geliştirme senaryolarını anlatır [!INCLUDE[wrt](../../../includes/wrt-md.md)] bileşenleri.

## <a name="the-basics"></a>Temeller
 .NET Framework, [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]'i sağlayarak ve [!INCLUDE[wrt](../../../includes/wrt-md.md)]'i destekleyerek daha önce listelenen üç geliştirme senaryosunu destekler.

-   [.NET framework ve Windows çalışma zamanı ad alanları](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)#net-framework-and-windows-runtime-namespaces) .NET Framework sınıf kitaplıkları kütüphanesi görünümü sağlar ve yalnızca türleri ve oluşturmak için kullanabileceğiniz üyeleri içerir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalar ve [!INCLUDE[wrt](../../../includes/wrt-md.md)] bileşenleri.

    -   Geliştirme için Visual Studio (Visual Studio 2012 veya üzeri) kullandığınızda bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulama veya [!INCLUDE[wrt](../../../includes/wrt-md.md)] bileşeni, başvuru bütünleştirilmiş kodları kümesi sağlar, yalnızca ilgili türleri ve üyeleri görürsünüz.

    -   Bu basitleştirilmiş API kümesi, .NET Framework'te veya yinelenen [!INCLUDE[wrt](../../../includes/wrt-md.md)] özelliklerindeki yinelenen özelliklerin kaldırılmasıyla basitleştirilir. Örneğin, yalnızca koleksiyon türlerinin genel sürümlerini içerir ve XML belge nesne modeli, [!INCLUDE[wrt](../../../includes/wrt-md.md)]XML API kümesi için kaldırılır.

    -   
  [!INCLUDE[wrt](../../../includes/wrt-md.md)] öğesini yönetilen koddan çağırmak kolay olduğundan, yalnızca işletim sistemi API'sini sarmalayan özellikler de kaldırılır.

     Hakkında daha fazla bilgi edinmek için [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], bkz: [.NET için Windows Store uygulamalarına genel bakış](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)). API seçim işlemi hakkında bilgi için bkz [Metro style apps için .NET](https://devblogs.microsoft.com/dotnet/net-for-metro-style-apps/) .NET blog girişi.

-   [Windows çalışma zamanı](/uwp/api/) kullanıcı arabirimi öğeleri için yapı sağlar. [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalar ve işletim sistemi özelliklerine erişim sağlar. .NET Framework gibi [!INCLUDE[wrt](../../../includes/wrt-md.md)], C# ve Visual Basic derleyicilerinin [!INCLUDE[wrt](../../../includes/wrt-md.md)] öğesini .NET Framework sınıf kütüphanelerini kullandığı şekilde kullanmasını sağlayan meta verilere sahiptir. .NET Framework bazı farklılıkları gizleyerek [!INCLUDE[wrt](../../../includes/wrt-md.md)] kullanımını kolaylaştırır:

    -   Olay işleyicileri ekleme ve kaldırma desenleri gibi .NET Framework ve [!INCLUDE[wrt](../../../includes/wrt-md.md)] arasındaki bazı programlama deseni farklılıkları gizlidir. Sadece .NET Framework desenini kullanın.

    -   Yaygın olarak kullanılan türlerdeki bazı farklılıklar (örneğin, ilkel türler ve koleksiyonlar) gizlidir. Yalnızca .NET Framework türü bölümünde açıklandığı gibi kullandığınız [görünür farklar IDE'de](#DifferencesVisibleInIDE), bu makalenin ilerleyen bölümlerinde.

 
  [!INCLUDE[wrt](../../../includes/wrt-md.md)] için .NET Framework desteği çoğu zaman saydamdır. Sonraki bölümde, yönetilebilir kod ve [!INCLUDE[wrt](../../../includes/wrt-md.md)] arasındakı bazı belirgin farklar anlatılır.

<a name="AboutReferenceDocumentation"></a>
### <a name="the-net-framework-and-the-includewrtincludeswrt-mdmd-reference-documentation"></a>.NET Framework ve [!INCLUDE[wrt](../../../includes/wrt-md.md)] Başvuru Belgeleri
 Windows çalışma zamanı ve .NET Framework belge kümeleri ayrıdır. Eğer bir tür veya üyede Yardım'ı görüntülemek için F1'e basarsanız, uygun kümeden başvuru belgeleri görüntülenir. Ancak, göz atarsanız [Windows çalışma zamanı başvurusu](/uwp/api/) , kafa karıştırıcı örneklerle karşılaşabilirsiniz:

-   Gibi konular <xref:Windows.Foundation.Collections.IIterable%601> arabirimi Visual Basic veya C# için bildirim sözdizimi zorunda kalmaz. Bunun yerine, söz dizimi bölümünün üstünde bir not görünür (Bu durumda ".NET: Bu arabirim System.Collections.Generic.IEnumerable görünür\<T > "). Bunun nedeni .NET Framework ve [!INCLUDE[wrt](../../../includes/wrt-md.md)]'in farklı arabirimlerle aynı işlevselliği sağlamasıdır. Ayrıca, davranışsal farklılıklar da bulunur: numaralandırıcıyı döndürmek için `IIterable`, bir `First` yöntemi yerine bir <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> yöntemine sahiptir. Ortak bir görevi gerçekleştirmek için farklı bir yol öğrenmenizi zorlamak yerine .NET Framework, aşina olduğunuz türü kullanmak için yönetilen kodunuzun görüntülenmesini sağlayarak [!INCLUDE[wrt](../../../includes/wrt-md.md)]'i destekler. IDE'de `IIterable` arabirimini göremezsiniz, bu nedenle [!INCLUDE[wrt](../../../includes/wrt-md.md)] başvuru belgelerinde bu arabirimle karşılaşabileceğiniz tek yol doğrudan bu belgelere göz atmaktır.

-   <xref:Windows.Web.Syndication.SyndicationFeed.%23ctor(System.String,System.String,Windows.Foundation.Uri)> Belgeleri, yakından ilgili bir sorunu gösterir: Parametre türleri farklı diller için farklı görünüyor. C# ve Visual Basic için, parametre türleri <xref:System.String?displayProperty=nameWithType> ve <xref:System.Uri?displayProperty=nameWithType>'dir. Yine bu durum, .NET Framework kendi `String` ve `Uri` türlerine sahip olduğu içindir ve bunun gibi yaygın şekilde kullanılan türler için .NET Framework kullanıcılarını bunu yapmak üzere farklı bir yol öğrenmeye zorlamak anlamsızdır. IDE'de .NET Framework, ilgili [!INCLUDE[wrt](../../../includes/wrt-md.md)] türlerini gizler.

-   Bazı durumlarda, gibi <xref:Windows.UI.Xaml.GridLength> yapısı, .NET Framework, bir tür ile aynı ada ancak daha fazla işlevsellik sağlar. Örneğin, bir yapıcı ve özellik konuları kümesi `GridLength` ile ilişkilidir, ancak üyeler yalnızca yönetilen kodda mevcut olduğundan sadece Visual Basic ve #C için söz dizimi blokları vardır. 
  [!INCLUDE[wrt](../../../includes/wrt-md.md)]'de, yapılar sadece alanlara sahiptir. [!INCLUDE[wrt](../../../includes/wrt-md.md)] Yapısı gerektirir yardımcı bir sınıf <xref:Windows.UI.Xaml.GridLengthHelper>, eşdeğer bir işlevselliği sağlamak için. Yönetilen kodu yazarken bu yardımcı sınıfını IDE'de görmezsiniz.

-   IDE'de, [!INCLUDE[wrt](../../../includes/wrt-md.md)] türlerinin <xref:System.Object?displayProperty=nameWithType>'den türediği görünür. 
  <xref:System.Object> gibi, <xref:System.Object.ToString%2A?displayProperty=nameWithType>'den devralınan üyelere sahip oldukları görünür. Bu üyeler, türler gerçekten <xref:System.Object>'den devralınmış gibi işler ve [!INCLUDE[wrt](../../../includes/wrt-md.md)] türleri, <xref:System.Object>'e yayımlanabilir. Bu işlevsellik, .NET Framework'ün [!INCLUDE[wrt](../../../includes/wrt-md.md)] için sağladığı desteğin bir parçasıdır. Ancak, eğer [!INCLUDE[wrt](../../../includes/wrt-md.md)] başvuru belgelerindeki türleri görüntülerseniz, bu üyeler görünmez. Görünen bu devralınmış üyelere ait belgeler, <xref:System.Object?displayProperty=nameWithType> başvuru belgeleri tarafından sağlanır.

<a name="DifferencesVisibleInIDE"></a>
### <a name="differences-that-are-visible-in-the-ide"></a>IDE içerisinde Görünür Farklar
 JavaScript kullanarak Windows için oluşturulan bir [!INCLUDE[wrt](../../../includes/wrt-md.md)] uygulamasına ait uygulama mantığını sağlamak amacıyla C#'de yazılmış bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] bileşenini kullanma gibi daha gelişmiş programlama senaryolarında bu gibi farklılıklar belgelerin yanı sıra IDE'de de görünür. Bileşeniniz JavaScript'e bir `IDictionary<int, string>` döndürdüğünde ve JavaScript hata ayıklayıcısında buna baktığınızda, JavaScript `IMap<int, string>` türünü kullandığından [!INCLUDE[wrt](../../../includes/wrt-md.md)] yöntemlerini görürsünüz. Aşağıdaki tabloda, iki dilde farklı olarak görüntülenen yaygın şekilde kullanılan bazı koleksiyon türleri gösterilmiştir:

|[!INCLUDE[wrt](../../../includes/wrt-md.md)] Türü|İlgili .NET Framework türü|
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

 
  [!INCLUDE[wrt](../../../includes/wrt-md.md)]'da, `IMap<K, V>` ve `IMapView<K, V>`, `IKeyValuePair` kullanılarak yinelenir. Bunları yönetilen koda geçirdiğinizde `IDictionary<TKey, TValue>` ve `IReadOnlyDictionary<TKey, TValue>` olarak görünürler, bu nedenle doğal olarak bunları numaralandırmak için `System.Collections.Generic.KeyValuePair<TKey, TValue>`'i kullanın.

 Arabirimlerin yönetilen kodda görüntülenme şekli, bu arabirimlerin uygulanma şeklini etkiler. Örneğin, `PropertySet` sınıfı, yönetilen kodda `IMap<K, V>` olarak görünen `IDictionary<TKey, TValue>`'i uygular. `PropertySet`, `IDictionary<TKey, TValue>` yerine `IMap<K, V>`'i uyguluyormuş gibi görünür, bu nedenle yönetilen kodda, .NET Framework sözlüklerinde `Add` yöntemi gibi davranan bir `Add` yöntemine sahipmiş gibi görünür. Bir `Insert` yöntemine sahipmiş gibi görünmez.

 Oluşturmak için .NET Framework kullanma hakkında daha fazla bilgi için bir [!INCLUDE[wrt](../../../includes/wrt-md.md)] bileşeni ve JavaScript ile benzer bir bileşeni kullanmayı gösteren bir anlatım [C# ve Visual Basic'te Windows çalışma zamanı bileşenleri oluşturma](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).

### <a name="primitive-types"></a>İlkel Türler
 Yönetilen kodda [!INCLUDE[wrt](../../../includes/wrt-md.md)]'ın doğal kullanımını etkinleştirmek için, kodunuzda [!INCLUDE[wrt](../../../includes/wrt-md.md)] ilkel türleri yerine .NET Framework ilkel türleri görünür. .NET Framework'te, `Int32` yapısı gibi ilkel türler, `Int32.TryParse` yöntemi gibi birçok yararlı özellik ve yönteme sahiptir. Bunun tersine, [!INCLUDE[wrt](../../../includes/wrt-md.md)]'deki ilkel türler ve yapılar yalnızca alanlara sahiptir. Yönetilen kodda ilkelleri kullandığınızda, .NET Framework türleri gibi görünürler ve normalde yaptığınız gibi .NET Framework türlerinin özellik ve yöntemlerini kullanabilirsiniz. Aşağıdaki liste bir özet sağlar:

-   
  [!INCLUDE[wrt](../../../includes/wrt-md.md)] ilkelleri olan `Int32`, `Int64`, `Single`, `Double`, `Boolean`, `String` (Unicode karakterlerin sabit bir koleksiyonu), `Enum`, `UInt32`, `UInt64` ve `Guid` için, `System` ad alanında aynı ada sahip türü kullanın.

-   
  `UInt8` için `System.Byte`'i kullanın.

-   
  `Char16` için `System.Char`'i kullanın.

-   
  `IInspectable` arabirimi için `System.Object`'i kullanın.

-   
  `HRESULT` için, bir `System.Int32` üyesi olan bir yapı kullanın.

 Arabirim türlerinde olduğu gibi, bu sunumun kanıtını görmek istediğiniz tek zaman.NET Framework projenizin, Javascript kullanılarak oluşturulmuş bir [!INCLUDE[wrt](../../../includes/wrt-md.md)] uygulaması tarafından kullanılan bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] bileşeni olduğu zamandır.

 Diğer temel, yaygın şekilde kullanılan [!INCLUDE[wrt](../../../includes/wrt-md.md)] türleri, .NET Framework eşdeğerleri yönetilen kodda `Windows.Foundation.DateTime` yapısı olarak görünen <xref:System.DateTimeOffset?displayProperty=nameWithType> yapısını ve `Windows.Foundation.TimeSpan` yapısı olarak görünen <xref:System.TimeSpan?displayProperty=nameWithType> yapısını içeriyormuş gibi görünür.

### <a name="other-differences"></a>Diğer Farklar
 Birkaç durumda, .NET Framework türlerinin kodunuzda [!INCLUDE[wrt](../../../includes/wrt-md.md)] türleri yerine görünmesi gerçeği, sizin eyleminizi gerektirir. Örneğin, <xref:Windows.Foundation.Uri?displayProperty=nameWithType> sınıfı olarak görünür <xref:System.Uri?displayProperty=nameWithType> .NET Framework kodunda. <xref:System.Uri?displayProperty=nameWithType> bir göreli URİ'yi sağlar ancak <xref:Windows.Foundation.Uri?displayProperty=nameWithType> bir mutlak URI gerektirir. Bu nedenle, bir [!INCLUDE[wrt](../../../includes/wrt-md.md)] yöntemine bir URI gönderdiğinizde, bunun mutlak olduğundan emin olmanız gerekir. (Bkz [Windows çalışma zamanı için bir URI geçirme](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md).)

<a name="WindowsRuntimeComponents"></a>
## <a name="scenarios-for-developing-windows-runtime-components"></a>Windows Çalışma Zamanı Bileşenleri Geliştirme Senaryoları
 Yönetilen [!INCLUDE[wrt](../../../includes/wrt-md.md)] Bileşenleri için desteklenen senaryolar aşağıdaki genel ilkelere bağlıdır:

-   [!INCLUDE[wrt](../../../includes/wrt-md.md)] .NET Framework kullanılarak oluşturulan bileşenleri yüklü hiçbir belirgin farklar diğer [!INCLUDE[wrt](../../../includes/wrt-md.md)]kitaplıkları. Örneğin, yönetilen kod kullanarak yerel bir [!INCLUDE[wrt](../../../includes/wrt-md.md)] bileşenini yeniden uyguladığınızda, iki bileşen dıştan ayırt edilemezler. Kodun kendisi yönetilen kod olsa bile bileşeninizin yönetilen kodda yazıldığı gerçeği, bunu kullanan kod için görünmezdir. Ancak, dahili olarak, kodunuz doğru yönetilen koddur ve ortak dil çalışma zamanı (CLR) üzerinde çalışır.

-   Bileşenler, uygulama mantığını uygulayan türleri, [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] UI denetimlerini veya her ikisi içerebilir.

    > [!NOTE]
    >  UI öğelerini uygulama mantığından ayırmak iyi bir yöntemdir. Ayrıca, JavaScript ve HTML kullanılarak Windows için oluşturulmuş bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamasında [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] UI denetimlerini kullanamazsınız.

-   Bir bileşen, bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamaya ait bir Visual Studio çözümü içinde bir proje veya çoklu çözümlere ekleyebileceğiniz yeniden kullanılabilir bir bileşen olabilir.

    > [!NOTE]
    >  Eğer bileşeniniz sadece C# veya Visual Basic ile kullanılacaksa, onu bir [!INCLUDE[wrt](../../../includes/wrt-md.md)] bileşeni yapmaya gerek yoktur. Eğer bunun yerine onu sıradan bir .NET Framework sınıf kitaplığı yaparsanız, ortak API yüzeyini [!INCLUDE[wrt](../../../includes/wrt-md.md)] türleriyle sınırlamak zorunda değilsiniz.

-   Yeniden kullanılabilir bileşenlerin sürümlerini kullanarak yayınlamadan [!INCLUDE[wrt](../../../includes/wrt-md.md)] <xref:Windows.Foundation.Metadata.VersionAttribute> hangi türlerin (ve bir tür içinde hangi üyelerin) tanımlamak için öznitelik farklı sürümlerde eklendi.

-   Bileşeninizdeki türler [!INCLUDE[wrt](../../../includes/wrt-md.md)] türlerinden türeyebilir. Denetimleri alanındaki ilkel denetim türlerinden türeyebilir <xref:Windows.UI.Xaml.Controls.Primitives> ad alanı veya denetimler gibi daha tamamlanmış <xref:Windows.UI.Xaml.Controls.Button>.

    > [!IMPORTANT]
    >  
  [!INCLUDE[win8](../../../includes/win8-md.md)] ve [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ile başlayarak, yönetilen bir [!INCLUDE[wrt](../../../includes/wrt-md.md)] bileşenindeki tüm ortak türlerin mühürlenmesi gerekir. Başka bir [!INCLUDE[wrt](../../../includes/wrt-md.md)] bileşenindeki bir tür onlardan türeyemez. Eğer bileşeninizde polimorfik davranış sağlamak istiyorsanız, bir arabirim oluşturabilir ve bu arabirimi polimorfik türlere uygulayabilirsiniz.

-   Bileşeninizin genel türlerindeki tüm parametre ve dönüş türlerinin, [!INCLUDE[wrt](../../../includes/wrt-md.md)] türleri olması gerekir (bileşeninizin tanımladığı [!INCLUDE[wrt](../../../includes/wrt-md.md)] türleri dahil).

 Aşağıdaki bölümler ortak senaryo örneklerini sağlar.

### <a name="application-logic-for-a-includewin8appnamelongincludeswin8-appname-long-mdmd-app-with-javascript"></a>JavaScript olan bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] Uygulaması için Uygulama Mantığı
 JavaScript kullanarak Windows için bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulaması geliştirdiğinizde, uygulama mantığının bazı kısımlarının yönetilen kodda daha iyi çalıştığını veya daha kolay geliştirildiğini fark edebilirsiniz. JavaScript, .NET Framework sınıf kitaplıklarını doğrudan kullanamaz, ancak bir .WinMD dosyasını sınıf kitaplığı yapabilirsiniz. Bu senaryoda [!INCLUDE[wrt](../../../includes/wrt-md.md)] bileşeni, uygulamanın ayrılmaz bir parçasıdır, bu nedenle sürüm özniteliklerinin sağlanması mantıksızdır.

### <a name="reusable-includewin8appnamelongincludeswin8-appname-long-mdmd-ui-controls"></a>Yeniden Kullanılabilir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] UI Denetimleri
 İlgili bir UI denetimleri kümesini, yeniden kullanılabilir bir [!INCLUDE[wrt](../../../includes/wrt-md.md)] bileşeninde paketleyebilirsiniz. Bileşen kendi üzerinde pazarlanabilir veya kendi oluşturduğunuz uygulamalarda bir öğe olarak kullanılabilir. Bu senaryoda, kullanılacak mantıklı [!INCLUDE[wrt](../../../includes/wrt-md.md)] <xref:Windows.Foundation.Metadata.VersionAttribute> uyumluluğu artırmak için özniteliği.

### <a name="reusable-application-logic-from-existing-net-framework-apps"></a>Varolan .NET Framework Uygulamalarından Yeniden Kullanılabilir Uygulama Mantığı
 Varolan masaüstü uygulamalarınızdan gelen yönetilen kodu, tek başına bir [!INCLUDE[wrt](../../../includes/wrt-md.md)] bileşeni olarak paketleyebilirsiniz. Bu, bileşeni, C++ veya Virtual Basic kullanılarak oluşturulan [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]  uygulamalarının yanı sıra C# veya JavaScript kullanılarak oluşturulan [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalarında da kullanmanızı sağlar. Kod için birden çok yeniden kullanılabilir senaryo varsa sürümleme bir seçenektir.

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[.NET için Windows Store uygulamalarına genel bakış](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140))|.NET Framework türlerini ve oluşturmak için kullanabileceğiniz üyeleri açıklar [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalar ve [!INCLUDE[wrt](../../../includes/wrt-md.md)]bileşenleri. (Windows Geliştirme Merkezi'nde.)|
|[C# veya Visual Basic kullanan Windows Store uygulamaları için yol haritası](https://docs.microsoft.com/previous-versions/windows/apps/br229583(v=win.10))|Bir çok Hızlı Başlangıç konuları, kılavuzlar ve en iyi yöntemleri dahil olmak üzere C# veya Visual Basic kullanarak [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamaları geliştirmeye başlamanıza yardımcı olan anahtar kaynaklar sağlar. (Windows Geliştirme Merkezi'nde.)|
|[Nasıl yapılır makaleleri (XAML)](https://docs.microsoft.com/previous-versions/windows/apps/br229566(v=win.10))|Bir çok Hızlı Başlangıç konuları, kılavuzlar ve en iyi yöntemleri dahil olmak üzere C# veya Visual Basic kullanarak [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamaları geliştirmeye başlamanıza yardımcı olan anahtar kaynaklar sağlar. (Windows Geliştirme Merkezi'nde.)|
|[C# ve Visual Basic'te Windows çalışma zamanı bileşenleri oluşturma](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)|.NET Framework kullanarak bir [!INCLUDE[wrt](../../../includes/wrt-md.md)] bileşeninin nasıl oluşturulacağını anlatır, JavaScript kullanarak Windows için oluşturulan bir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamasının parçası olarak bu bileşenin nasıl kullanılacağını açıklar ve Visual Studio ile kombinasyonda nasıl hata ayıklama yapılacağını anlatır. (Windows Geliştirme Merkezi'nde.)|
|[Windows çalışma zamanı başvurusu](/uwp/api/)|
  [!INCLUDE[wrt](../../../includes/wrt-md.md)]'e ait başvuru belgeleri. (Windows Geliştirme Merkezi'nde.)|
|[URI'yı Windows Çalışma Zamanı'na Geçirme](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md)|Yönetilen koddan gelen bir URI'yi [!INCLUDE[wrt](../../../includes/wrt-md.md)]'e gönderdiğinizde oluşabilecek bir sorunu ve bunun nasıl önleneceğini açıklar.|
