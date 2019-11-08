---
title: PropertyPath XAML Sözdizimi
ms.date: 03/30/2017
helpviewer_keywords:
- PropertyPath object [WPF]
- XAML [WPF], PropertyPath object
ms.assetid: 0e3cdf07-abe6-460a-a9af-3764b4fd707f
ms.openlocfilehash: f9176e61915b6c5cc05f120eade69a6d19cc4e6a
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740787"
---
# <a name="propertypath-xaml-syntax"></a>PropertyPath XAML Sözdizimi

<xref:System.Windows.PropertyPath> nesnesi, <xref:System.Windows.PropertyPath> türünü değer olarak alan çeşitli özellikleri ayarlamak için karmaşık bir satır içi [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] söz dizimini destekler. Bu konu, bağlama ve animasyon sözdizimleri için uygulanan <xref:System.Windows.PropertyPath> sözdizimini belgeler.

<a name="where"></a>

## <a name="where-propertypath-is-used"></a>PropertyPath 'In kullanıldığı yer

<xref:System.Windows.PropertyPath>, birkaç [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] özelliği için kullanılan ortak bir nesnedir. Özellik yolu bilgilerini iletmek için ortak <xref:System.Windows.PropertyPath> kullanılmasına karşın, bir tür olarak <xref:System.Windows.PropertyPath> kullanıldığı her bir özellik alanının kullanımları değişir. Bu nedenle, sözdizimleri özellik başına temelinde belge oluşturmak daha pratik hale gelir.

Öncelikle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bir nesne veri kaynağının özelliklerine geçiş yapmak ve hedeflenen animasyonlar için hedef yolu belirtmek üzere <xref:System.Windows.PropertyPath> kullanır.

<xref:System.Windows.Setter.Property%2A?displayProperty=nameWithType> gibi bazı stil ve Şablon Özellikleri, <xref:System.Windows.PropertyPath>benzer nitelikli bir özellik adı alır. Ancak bu, doğru bir <xref:System.Windows.PropertyPath>değildir; Bunun yerine, <xref:System.Windows.DependencyProperty>için tür dönüştürücüsüyle birlikte WPF [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcisi tarafından etkinleştirilen nitelikli bir *sahip. Özellik* dizesi biçimi kullanımı.

<a name="databinding_s"></a>

## <a name="propertypath-for-objects-in-data-binding"></a>Veri bağlamada nesneler için PropertyPath

Veri bağlama, herhangi bir bağımlılık özelliğinin hedef değerini bağlayabileceğiniz bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özelliğidir. Ancak, bu tür bir veri bağlamasının kaynağı bir bağımlılık özelliği olmalıdır; Bu, geçerli veri sağlayıcısı tarafından tanınan herhangi bir özellik türü olabilir. Özellik yolları özellikle, ortak dil çalışma zamanı (CLR) nesnelerinden ve bunların özelliklerinden bağlama kaynakları almak için kullanılan <xref:System.Windows.Data.ObjectDataProvider>için kullanılır.

XML 'e veri bağlamanın, <xref:System.Windows.Data.Binding><xref:System.Windows.Data.Binding.Path%2A> kullanmadığı için <xref:System.Windows.PropertyPath>kullanmadığını unutmayın. Bunun yerine, <xref:System.Windows.Data.Binding.XPath%2A> kullanır ve verilerin XML Belge Nesne Modeli (DOM) geçerli XPath sözdizimini belirtirsiniz. <xref:System.Windows.Data.Binding.XPath%2A> Ayrıca bir dize olarak belirtilir, ancak burada belgelenmemiştir; bkz. [XMLDataProvider ve XPath sorgularını kullanarak XML verilerine bağlama](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).

Veri bağlamada Özellik yollarını anlamak için bir anahtar, bağlamayı tek bir özellik değerine hedefleyebilir veya bunun yerine listeleri veya koleksiyonları alan hedef özelliklere bağlayabilirsiniz. Koleksiyonlar bağlıyorsanız, koleksiyonda kaç veri öğesi olduğuna bağlı olarak genişletilecek bir <xref:System.Windows.Controls.ListBox> bağlama için, özellik yolunuzdaki tek tek koleksiyon öğeleri değil koleksiyon nesnesine başvurması gerekir. Veri bağlama altyapısı, veri kaynağı olarak kullanılan koleksiyonla otomatik olarak bağlama hedefi türüne eşleşir ve bir <xref:System.Windows.Controls.ListBox> öğeler dizisiyle doldurma gibi davranışa neden olur.

<a name="singlecurrent"></a>

### <a name="single-property-on-the-immediate-object-as-data-context"></a>Veri bağlamı olarak acil nesnedeki tek özellik

```xml
<Binding Path="propertyName" .../>
```

*PropertyName* , <xref:System.Windows.Data.Binding.Path%2A> kullanımı için geçerli <xref:System.Windows.FrameworkElement.DataContext%2A> bir özelliğin adı olacak şekilde çözümlenmelidir. Bağlamanız kaynağı Güncelleştir, bu özellik okuma/yazma olmalıdır ve kaynak nesne değişebilir olmalıdır.

<a name="singleindex"></a>

### <a name="single-indexer-on-the-immediate-object-as-data-context"></a>Veri bağlamı olarak acil nesnedeki tek Dizin Oluşturucu

```xml
<Binding Path="[key]" .../>
```

`key`, bir sözlük veya karma tabloya yazılan dizin ya da bir dizinin tamsayı dizini olmalıdır. Ayrıca, anahtarın değeri, uygulandığı özelliği doğrudan bağlanabilir bir tür olmalıdır. Örneğin, dize anahtarlarını ve dize değerlerini içeren bir karma tablo, bir <xref:System.Windows.Controls.TextBox>metne bağlamak için bu şekilde kullanılabilir. Ya da anahtar bir koleksiyona veya alt dizine işaret ediyorsa, bu söz dizimini bir hedef koleksiyon özelliğine bağlamak için kullanabilirsiniz. Aksi takdirde, `<Binding Path="[key].propertyName" .../>`gibi bir sözdizimi aracılığıyla belirli bir özelliğe başvurmanız gerekir.

Gerekirse dizinin türünü belirtebilirsiniz. Dizinli özellik yolunun bu yönü hakkında ayrıntılı bilgi için bkz. <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>.

<a name="multipleindirect"></a>

### <a name="multiple-property-indirect-property-targeting"></a>Birden çok Özellik (dolaylı Özellik hedefleme)

```xml
<Binding Path="propertyName.propertyName2" .../>
```

`propertyName`, geçerli <xref:System.Windows.FrameworkElement.DataContext%2A>bir özelliğin adı olacak şekilde çözümlenmelidir. `propertyName` ve `propertyName2` yol özellikleri, bir ilişkide bulunan herhangi bir özellik olabilir. burada `propertyName2`, `propertyName`değeri olan türde olan bir özelliktir.

<a name="singleattached"></a>

### <a name="single-property-attached-or-otherwise-type-qualified"></a>Tek özellik, bağlı veya başka türlü tür nitelikli

```xml
<object property="(ownerType.propertyName)" .../>
```

Parantezler bir <xref:System.Windows.PropertyPath> bu özelliğin kısmi bir nitelik kullanılarak oluşturulması gerektiğini gösterir. Uygun bir eşleme ile türü bulmak için bir XML ad alanı kullanabilir. `ownerType`, her derlemedeki <xref:System.Windows.Markup.XmlnsDefinitionAttribute> bildirimleri aracılığıyla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcinin erişebileceği türleri arar. Çoğu uygulamanın, `http://schemas.microsoft.com/winfx/2006/xaml/presentation` ad alanına eşlenmiş varsayılan XML ad alanı vardır. bu nedenle, ön ek genellikle yalnızca bu ad alanı dışında özel türler veya türler için gereklidir.  `propertyName`, `ownerType`var olan bir özelliğin adı olacak şekilde çözümlenmelidir. Bu sözdizimi genellikle aşağıdaki durumlardan biri için kullanılır:

- Yol, belirtilen hedef türüne sahip olmayan bir stil veya şablondaki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] belirtilir. Nitelikli olmayan bir kullanım genellikle bunun dışındaki durumlar için geçerli değildir, çünkü stil dışı, şablon dışı durumlarda özellik bir tür değil bir örnekte bulunur.

- Özelliği iliştirilmiş bir özelliktir.

- Statik bir özelliğe bağlanıyor.

Görsel taslak hedefi olarak kullanılmak üzere `propertyName` olarak belirtilen özellik bir <xref:System.Windows.DependencyProperty>olmalıdır.

<a name="sourcetraversal"></a>

### <a name="source-traversal-binding-to-hierarchies-of-collections"></a>Kaynak geçişi (koleksiyonların hiyerarşilerine bağlama)

```xml
<object Path="propertyName/propertyNameX" .../>
```

Bu söz dizimi, hiyerarşik bir veri kaynağı nesnesi içinde gezinmek için kullanılır ve hiyerarşide art arda/karakterlerle birlikte birden çok adım desteklenir. Geçerli kayıt işaretçisi konumuna ait kaynak çapraz geçiş hesapları, verilerin görünümünün kullanıcı arabirimiyle eşitlenmesi tarafından belirlenir. Hiyerarşik veri kaynağı nesneleriyle bağlama ve Veri bağlamada geçerli kayıt işaretçisinin kavramı ile ilgili ayrıntılar için bkz. hiyerarşik veri veya [veri bağlamaya genel bakış](../../../desktop-wpf/data/data-binding-overview.md) [Ile ana ayrıntı modelini kullanma](../data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md) .

> [!NOTE]
> Superficially, bu söz dizimi XPath olarak benzerdir. XML veri kaynağına bağlamak için doğru bir XPath ifadesi <xref:System.Windows.Data.Binding.Path%2A> değer olarak kullanılmaz ve bunun yerine birbirini dışlayan <xref:System.Windows.Data.Binding.XPath%2A> özelliği için kullanılmalıdır.

### <a name="collection-views"></a>Koleksiyon Görünümleri

Adlandırılmış bir koleksiyon görünümüne başvurmak için, koleksiyon görünümü adının önüne karma karakteri (`#`) ekleyin.

### <a name="current-record-pointer"></a>Geçerli kayıt Işaretçisi

Bir koleksiyon görünümü veya ana ayrıntı veri bağlama senaryosunda geçerli kayıt işaretçisine başvurmak için, yol dizesini eğik çizgiyle (`/`) başlatın. Eğik çizgiden sonraki tüm yol, geçerli kayıt işaretçisinden başlayarak gönderilir.

### <a name="multiple-indexers"></a>Çoklu Dizin oluşturucular

```xaml
<object Path="[index1,index2...]" .../>
```

veya

```xaml
<object Path="propertyName[index,index2...]" .../>
```

Belirli bir nesne birden çok dizin oluşturucuyu destekliyorsa, bu dizin oluşturucular, bir diziye başvuran sözdizimine benzer şekilde sırayla belirlenebilir. Söz konusu nesne, geçerli bağlam ya da birden çok dizin nesnesi içeren bir özelliğin değeri olabilir.

Varsayılan olarak, Dizin Oluşturucu değerleri, temel alınan nesnenin özellikleri kullanılarak yazılır. Gerekirse dizinin türünü belirtebilirsiniz. Dizin oluşturucular yazma hakkında daha fazla bilgi için bkz. <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>.

<a name="mixing"></a>

### <a name="mixing-syntaxes"></a>Sözdizimleri karıştırma

Yukarıda gösterilen sözdizimlerinin her biri birbirine bağlanabilir. Örneğin, aşağıda, <xref:System.Windows.Media.SolidColorBrush> nesnelerin piksel kılavuz dizisini içeren bir `ColorGrid` özelliğinin belirli bir x, y rengine bir özellik yolu oluşturan örnek verilmiştir:

```xml
<Rectangle Fill="{Binding ColorGrid[20,30].SolidColorBrushResult}" .../>
```

### <a name="escapes-for-property-path-strings"></a>Özellik yolu dizeleri için çıkar

Belirli iş nesneleri için, özellik yolu dizesinin doğru ayrıştırılacak bir kaçış sırası gerektirdiği bir durum ile karşılaşabilirsiniz. Bu karakterlerin çoğunda genellikle iş nesnesini tanımlamak için kullanılan dillerde benzer adlandırma etkileşimi sorunları olduğundan, kaçış gereksinimi nadir olmalıdır.

- Dizin oluşturucular ([]) içinde, giriş işareti karakteri (^) sonraki karakteri çıkar.

- XML dil tanımına özel olan belirli karakterleri (XML varlıkları kullanarak) atlamanız gerekir. "&" Karakterinden kaçınmak için `&` kullanın. ">" Bitiş etiketini atlamak için `>` kullanın.

- Bir işaretleme uzantısını işlemek için WPF XAML ayrıştırıcı davranışına özel olan karakterlerin kaçış (ters eğik çizgi `\`) karakterlerini kullanmanız gerekir.

  - Ters eğik çizgi (`\`), kaçış karakteridir.

  - Eşittir işareti (`=`) özellik değerinden özellik adını ayırır.

  - Virgül (`,`) özellikleri ayırır.

  - Sağ kaşlı ayraç (`}`), biçimlendirme uzantısının sonu.

> [!NOTE]
> Teknik olarak, bu kaçış bir film şeridi özellik yolu için de çalışır, ancak genellikle var olan WPF nesneleri için nesne modellerinden geçiş yapmanız ve kaçışın gereksiz olması gerekir.

<a name="databinding_sa"></a>

## <a name="propertypath-for-animation-targets"></a>Animasyon hedefleri için PropertyPath

Bir animasyonun Target özelliği bir <xref:System.Windows.Freezable> ya da ilkel tür alan bir Dependency özelliği olmalıdır. Ancak, bir türdeki hedeflenen özellik ve son animasyon özelliği farklı nesnelerde bulunabilir. Animasyonlar için, özellik değerlerindeki nesne özelliği ilişkilerinin geçişi yaparak adlandırılmış animasyon hedefi nesnesinin özelliği ve amaçlanan hedef animasyon özelliği arasındaki bağlantıyı tanımlamak için bir özellik yolu kullanılır.

<a name="general"></a>

### <a name="general-object-property-considerations-for-animations"></a>Genel nesne-animasyonlar için özellik konuları

Genel olarak animasyon kavramları hakkında daha fazla bilgi için bkz. görsel taslaklara [genel bakış](../graphics-multimedia/storyboards-overview.md) ve [animasyona genel bakış](../graphics-multimedia/animation-overview.md).

Değer türü veya hareketlendirilen özellik bir <xref:System.Windows.Freezable> türü ya da ilkel olmalıdır. Yolu Başlatan özelliği, belirtilen <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> türünde var olan bir bağımlılık özelliğinin adı olacak şekilde çözümlenmelidir.

Zaten dondurulmuş olan bir <xref:System.Windows.Freezable> hareketlendirmek için kopyalamayı desteklemek amacıyla, <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> tarafından belirtilen nesnenin <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement> türetilmiş bir sınıf olması gerekir.

<a name="singlestepanim"></a>

### <a name="single-property-on-the-target-object"></a>Hedef nesnedeki tek özellik

```xml
<animation Storyboard.TargetProperty="propertyName" .../>
```

`propertyName`, belirtilen <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> türünde bulunan bir bağımlılık özelliğinin adı olacak şekilde çözümlenmelidir.

<a name="indirectanim"></a>

### <a name="indirect-property-targeting"></a>Dolaylı Özellik hedefleme

```xml
<animation Storyboard.TargetProperty="propertyName.propertyName2" .../>
```

`propertyName`, belirtilen <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> türünde var olan bir <xref:System.Windows.Freezable> değer türü ya da ilkel olan bir özellik olmalıdır.

`propertyName2`, `propertyName`değeri olan nesnede bulunan Dependency özelliğinin adı olmalıdır. Diğer bir deyişle, `propertyName2` `propertyName` <xref:System.Windows.DependencyProperty.PropertyType%2A>tür üzerinde bir bağımlılık özelliği olarak bulunmalıdır.

Uygulanan stiller ve şablonlar nedeniyle animasyonların dolaylı olarak hedeflenmesi gerekir. Bir animasyonu hedeflemek için, hedef nesnede bir <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> gerekir ve bu ad [x:Name](../../xaml-services/x-name-directive.md) veya <xref:System.Windows.FrameworkElement.Name%2A>tarafından oluşturulur. Şablon ve stil öğelerinin adları da olabilir, ancak bu adlar yalnızca stilin ve şablonun namescope içinde geçerlidir. (Şablonlar ve stiller, uygulama biçimlendirmesi ile ad kapsamları 'yi paylaşıyorsa, adlar benzersiz olamaz. Stiller ve şablonlar, örnekler arasında tam olarak paylaşılır ve yinelenen adları yeniden işlenir.) Bu nedenle, hareketlendirmek isteyebileceğiniz bir öğenin tek tek özellikleri bir stil veya şablondan geldiyse, bir stil şablonundan olmayan adlandırılmış bir öğe örneğiyle başlamanız ve sonra özelliğe ulaşmak için stil veya şablon görsel ağacını hedeflemek gerekir animasyon uygulamak istiyorsunuz.

Örneğin, bir <xref:System.Windows.Controls.Panel> <xref:System.Windows.Controls.Panel.Background%2A> özelliği, bir tema şablonundan gelen tamamen bir <xref:System.Windows.Media.Brush> (aslında bir <xref:System.Windows.Media.SolidColorBrush>). Bir <xref:System.Windows.Media.Brush> tamamen hareketlendirmek için, bir BrushAnimation olması gerekir (büyük olasılıkla her <xref:System.Windows.Media.Brush> türü için bir tane) ve böyle bir tür yoktur. Fırçaya animasyon uygulamak için, bunun yerine belirli bir <xref:System.Windows.Media.Brush> türünün özelliklerine animasyon uygulayabilirsiniz. Bir <xref:System.Windows.Media.Animation.ColorAnimation> uygulamak için <xref:System.Windows.Media.SolidColorBrush> <xref:System.Windows.Media.SolidColorBrush.Color%2A> ' den almanız gerekir. Bu örnek için özellik yolu `Background.Color`olacaktır.

<a name="attachedanim"></a>

### <a name="attached-properties"></a>Ekli Özellikler

```xml
<animation Storyboard.TargetProperty="(ownerType.propertyName)" .../>
```

Parantezler bir <xref:System.Windows.PropertyPath> bu özelliğin kısmi bir nitelik kullanılarak oluşturulması gerektiğini gösterir. Türü bulmak için bir XML ad alanı kullanabilir. `ownerType`, her derlemedeki <xref:System.Windows.Markup.XmlnsDefinitionAttribute> bildirimleri aracılığıyla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcinin erişebileceği türleri arar. Çoğu uygulamanın, `http://schemas.microsoft.com/winfx/2006/xaml/presentation` ad alanına eşlenmiş varsayılan XML ad alanı vardır. bu nedenle, ön ek genellikle yalnızca bu ad alanı dışında özel türler veya türler için gereklidir. `propertyName`, `ownerType`var olan bir özelliğin adı olacak şekilde çözümlenmelidir. `propertyName` olarak belirtilen özellik bir <xref:System.Windows.DependencyProperty>olmalıdır. (Tüm [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Ekli Özellikler bağımlılık özellikleri olarak uygulanır, bu nedenle bu sorun yalnızca özel Ekli Özellikler için sorun olabilir.)

<a name="indexanim"></a>

### <a name="indexers"></a>Dizin Oluşturucular

```xml
<animation Storyboard.TargetProperty="propertyName.propertyName2[index].propertyName3" .../>
```

Çoğu bağımlılık özellikleri veya <xref:System.Windows.Freezable> türleri bir dizin oluşturucuyu desteklemez. Bu nedenle, bir animasyon yolundaki dizin oluşturucunun tek kullanımı, adlandırılmış hedefte zinciri Başlatan özelliği ile son animasyonlu özelliği arasında bir ara konumda bulunur. Belirtilen sözdiziminde, `propertyName2`. Örneğin, ara Özellik `RenderTransform.Children[1].Angle`gibi bir özellik yolunda <xref:System.Windows.Media.TransformGroup>gibi bir Koleksiyonsa, Dizin Oluşturucu kullanımı gerekli olabilir.

<a name="ppincode"></a>

## <a name="propertypath-in-code"></a>Kodda PropertyPath

<xref:System.Windows.PropertyPath>için kod kullanımı, <xref:System.Windows.PropertyPath>oluşturma da dahil olmak üzere <xref:System.Windows.PropertyPath>başvuru konusunda belgelenmiştir.

Genel olarak, <xref:System.Windows.PropertyPath> bağlama kullanımları ve en basit animasyon kullanımları için bir tane olmak üzere iki farklı Oluşturucu kullanmak üzere tasarlanmıştır ve bir tane karmaşık animasyon kullanımları içindir. Nesnenin dize olduğu, kullanımları bağlama için <xref:System.Windows.PropertyPath.%23ctor%28System.Object%29> imzasını kullanın. Nesnenin bir <xref:System.Windows.DependencyProperty>olduğu tek adımlı animasyon yolları için <xref:System.Windows.PropertyPath.%23ctor%28System.Object%29> imzasını kullanın. Karmaşık animasyonlar için <xref:System.Windows.PropertyPath.%23ctor%28System.String%2CSystem.Object%5B%5D%29> imzasını kullanın. Bu ikinci Oluşturucu ilk parametre için bir belirteç dizesi ve bir özellik yolu ilişkisi tanımlamak için belirteç dizesindeki pozisyonları dolduran nesne dizisi kullanır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.PropertyPath>
- [Veri Bağlamaya Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [Görsel Taslaklara Genel Bakış](../graphics-multimedia/storyboards-overview.md)
