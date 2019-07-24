---
title: PropertyPath XAML Sözdizimi
ms.date: 03/30/2017
helpviewer_keywords:
- PropertyPath object [WPF]
- XAML [WPF], PropertyPath object
ms.assetid: 0e3cdf07-abe6-460a-a9af-3764b4fd707f
ms.openlocfilehash: deebdb690a6ba831730701de2608089af2d6bdfd
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401665"
---
# <a name="propertypath-xaml-syntax"></a>PropertyPath XAML Sözdizimi

Nesnesi, <xref:System.Windows.PropertyPath> türü değer olarak alan [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] çeşitli özellikleri ayarlamak için karmaşık bir satır içi söz dizimini destekler. <xref:System.Windows.PropertyPath> Bu konu, <xref:System.Windows.PropertyPath> söz dizimini bağlama ve animasyon sözdizimleri için uygulanan olarak belgeler.

<a name="where"></a>

## <a name="where-propertypath-is-used"></a>PropertyPath 'In kullanıldığı yer

<xref:System.Windows.PropertyPath>, çeşitli [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] özelliklerde kullanılan ortak bir nesnedir. Özellik yolu bilgilerini iletmek <xref:System.Windows.PropertyPath> için ortak kullanılmasına karşın, türü olarak kullanılan her bir özellik <xref:System.Windows.PropertyPath> alanı için kullanımlar değişir. Bu nedenle, sözdizimleri özellik başına temelinde belge oluşturmak daha pratik hale gelir.

Öncelikle, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir <xref:System.Windows.PropertyPath> nesne veri kaynağının özelliklerine geçiş yapmak ve hedeflenen animasyonlar için hedef yolu belirtmek üzere nesne modeli yollarını anlatmak için kullanır.

Gibi <xref:System.Windows.Setter.Property%2A?displayProperty=nameWithType> bazı stil ve Şablon Özellikleri, superficially benzer bir <xref:System.Windows.PropertyPath>nitelenmiş Özellik adı alır. Ancak bu doğru <xref:System.Windows.PropertyPath>değildir; Bunun yerine, için <xref:System.Windows.DependencyProperty>tür dönüştürücüsüyle birlikte WPF [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcisi tarafından etkinleştirilen bir nitelenmiş *sahip. Özellik* dize biçimi kullanımı.

<a name="databinding_s"></a>

## <a name="propertypath-for-objects-in-data-binding"></a>Veri bağlamada nesneler için PropertyPath

Veri bağlama, herhangi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir bağımlılık özelliğinin hedef değerine bağlayabileceğiniz bir özelliktir. Ancak, bu tür bir veri bağlamasının kaynağı bir bağımlılık özelliği olmalıdır; Bu, geçerli veri sağlayıcısı tarafından tanınan herhangi bir özellik türü olabilir. Özellik yolları özellikle, <xref:System.Windows.Data.ObjectDataProvider>ortak dil çalışma zamanı (CLR) nesnelerinden ve bunların özelliklerinden bağlama kaynakları almak için kullanılan için kullanılır.

[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] ' De <xref:System.Windows.PropertyPath> kullanmadığı<xref:System.Windows.Data.Binding.Path%2A> için veri bağlamasının kullanmadığını unutmayın. <xref:System.Windows.Data.Binding> Bunun yerine, ' <xref:System.Windows.Data.Binding.XPath%2A> i kullanın ve verilerin [!INCLUDE[TLA#tla_xmldom](../../../../includes/tlasharptla-xmldom-md.md)] içinde geçerli XPath sözdizimini belirtin. <xref:System.Windows.Data.Binding.XPath%2A>aynı zamanda bir dize olarak belirtilir, ancak burada açıklanmamıştır; bkz. [XMLDataProvider ve XPath sorgularını kullanarak XML verilerine bağlama](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).

Veri bağlamada Özellik yollarını anlamak için bir anahtar, bağlamayı tek bir özellik değerine hedefleyebilir veya bunun yerine listeleri veya koleksiyonları alan hedef özelliklere bağlayabilirsiniz. Koleksiyonları bağlıyorsanız, <xref:System.Windows.Controls.ListBox> koleksiyonda kaç veri öğesi olduğuna bağlı olarak genişlendirilecektir ve sonra, özellik yolunuzda tek tek koleksiyon öğeleri değil koleksiyon nesnesine başvuru yapılmalıdır. Veri bağlama altyapısı, veri kaynağı olarak kullanılan koleksiyonla otomatik olarak bağlama hedefi türüne eşleşir ve bir <xref:System.Windows.Controls.ListBox> öğe dizisi ile birlikte doldurma gibi davranışa neden olur.

<a name="singlecurrent"></a>

### <a name="single-property-on-the-immediate-object-as-data-context"></a>Veri bağlamı olarak acil nesnedeki tek özellik

```xml
<Binding Path="propertyName" .../>
```

*PropertyName* , <xref:System.Windows.FrameworkElement.DataContext%2A> <xref:System.Windows.Data.Binding.Path%2A> kullanım için geçerli olan bir özelliğin adı olacak şekilde çözümlenmelidir. Bağlamanız kaynağı Güncelleştir, bu özellik okuma/yazma olmalıdır ve kaynak nesne değişebilir olmalıdır.

<a name="singleindex"></a>

### <a name="single-indexer-on-the-immediate-object-as-data-context"></a>Veri bağlamı olarak acil nesnedeki tek Dizin Oluşturucu

```xml
<Binding Path="[key]" .../>
```

`key`bir sözlüğe ya da karma tabloya veya bir dizinin tamsayı dizinine yazılan dizin olmalıdır. Ayrıca, anahtarın değeri, uygulandığı özelliği doğrudan bağlanabilir bir tür olmalıdır. Örneğin, dize anahtarlarını ve dize değerlerini içeren bir karma tablo, bir <xref:System.Windows.Controls.TextBox>için metne bağlamak üzere bu şekilde kullanılabilir. Ya da anahtar bir koleksiyona veya alt dizine işaret ediyorsa, bu söz dizimini bir hedef koleksiyon özelliğine bağlamak için kullanabilirsiniz. Aksi takdirde, gibi bir sözdizimi `<Binding Path="[key].propertyName" .../>`aracılığıyla belirli bir özelliğe başvurmanız gerekir.

Gerekirse dizinin türünü belirtebilirsiniz. Dizinli özellik yolunun bu yönü hakkında ayrıntılı bilgi için bkz <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>.

<a name="multipleindirect"></a>

### <a name="multiple-property-indirect-property-targeting"></a>Birden çok Özellik (dolaylı Özellik hedefleme)

```xml
<Binding Path="propertyName.propertyName2" .../>
```

`propertyName`geçerli <xref:System.Windows.FrameworkElement.DataContext%2A>bir özelliğin adı olacak şekilde çözümlenmelidir. Yol özellikleri `propertyName` ve `propertyName2` bir ilişkide var olan herhangi bir özellik olabilir, burada `propertyName2` değeri `propertyName`olan türde bir özelliktir.

<a name="singleattached"></a>

### <a name="single-property-attached-or-otherwise-type-qualified"></a>Tek özellik, bağlı veya başka türlü tür nitelikli

```xml
<object property="(ownerType.propertyName)" .../>
```

Parantez, içindeki <xref:System.Windows.PropertyPath> bu özelliğin kısmi bir nitelik kullanılarak oluşturulması gerektiğini gösterir. Uygun bir eşleme ile türü bulmak için bir XML ad alanı kullanabilir. Her derlemedeki <xref:System.Windows.Markup.XmlnsDefinitionAttribute> bildirimler aracılığıyla bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcinin erişebileceği aramatürleri.`ownerType` Çoğu uygulama, [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] ad alanına eşlenmiş varsayılan XML ad alanına sahiptir, bu nedenle bir ön ek genellikle yalnızca bu ad alanı dışında özel türler veya türler için gereklidir.  `propertyName`, `ownerType`üzerinde varolan bir özelliğin adı olacak şekilde çözümlenmelidir. Bu sözdizimi genellikle aşağıdaki durumlardan biri için kullanılır:

- Yol, belirtilen hedef türüne [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sahip olmayan bir stilde veya şablonda belirtilir. Nitelikli olmayan bir kullanım genellikle bunun dışındaki durumlar için geçerli değildir, çünkü stil dışı, şablon dışı durumlarda özellik bir tür değil bir örnekte bulunur.

- Özelliği iliştirilmiş bir özelliktir.

- Statik bir özelliğe bağlanıyor.

Görsel taslak hedefi olarak kullanılmak üzere, olarak `propertyName` belirtilen özelliği bir <xref:System.Windows.DependencyProperty>olmalıdır.

<a name="sourcetraversal"></a>

### <a name="source-traversal-binding-to-hierarchies-of-collections"></a>Kaynak geçişi (koleksiyonların hiyerarşilerine bağlama)

```xml
<object Path="propertyName/propertyNameX" .../>
```

Bu söz dizimi, hiyerarşik bir veri kaynağı nesnesi içinde gezinmek için kullanılır ve hiyerarşide art arda/karakterlerle birlikte birden çok adım desteklenir. Geçerli kayıt işaretçisi konumuna ait kaynak çapraz geçiş hesapları, verilerin görünümünün kullanıcı arabirimiyle eşitlenmesi tarafından belirlenir. Hiyerarşik veri kaynağı nesneleriyle bağlama ve Veri bağlamada geçerli kayıt işaretçisinin kavramı ile ilgili ayrıntılar için bkz. hiyerarşik veri veya [veri bağlamaya genel bakış](../data/data-binding-overview.md) [Ile ana ayrıntı modelini kullanma](../data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md) .

> [!NOTE]
> Superficially, bu söz dizimi [!INCLUDE[TLA2#tla_xpath](../../../../includes/tla2sharptla-xpath-md.md)]benzerdir. Bir [!INCLUDE[TLA2#tla_xpath](../../../../includes/tla2sharptla-xpath-md.md)] <xref:System.Windows.Data.Binding.Path%2A> <xref:System.Windows.Data.Binding.XPath%2A> veri kaynağına bağlamak için doğru bir ifade değer olarak kullanılmaz ve bunun yerine birbirini dışlayan özellik için kullanılmalıdır. [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]

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

Varsayılan olarak, Dizin Oluşturucu değerleri, temel alınan nesnenin özellikleri kullanılarak yazılır. Gerekirse dizinin türünü belirtebilirsiniz. Dizin oluşturucuyu yazma hakkında ayrıntılı bilgi için bkz <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>.

<a name="mixing"></a>

### <a name="mixing-syntaxes"></a>Sözdizimleri karıştırma

Yukarıda gösterilen sözdizimlerinin her biri birbirine bağlanabilir. Örneğin, aşağıdaki örnekte, bir piksel kılavuz `ColorGrid` <xref:System.Windows.Media.SolidColorBrush> dizisi içeren bir özelliğin belirli bir x, y rengine bir özellik yolu oluşturan örnek verilmiştir:

```xml
<Rectangle Fill="{Binding ColorGrid[20,30].SolidColorBrushResult}" .../>
```

### <a name="escapes-for-property-path-strings"></a>Özellik yolu dizeleri için çıkar

Belirli iş nesneleri için, özellik yolu dizesinin doğru ayrıştırılacak bir kaçış sırası gerektirdiği bir durum ile karşılaşabilirsiniz. Bu karakterlerin çoğunda genellikle iş nesnesini tanımlamak için kullanılan dillerde benzer adlandırma etkileşimi sorunları olduğundan, kaçış gereksinimi nadir olmalıdır.

- Dizin oluşturucular ([]) içinde, giriş işareti karakteri (^) sonraki karakteri çıkar.

- XML dil tanımına özel olan belirli karakterleri (XML varlıkları kullanarak) atlamanız gerekir. " `&` &" Karakterini atlamak için kullanın. " `>` >" Bitiş etiketini atlamak için kullanın.

- Biçimlendirme uzantısını işlemek için WPF XAML `\`ayrıştırıcı davranışına özel olan karakterleri (ters eğik çizgi kullanarak) atlamanız gerekir.

  - Ters eğik`\`çizgi (), kaçış karakteridir.

  - Eşittir işareti (`=`) özellik değerinden özellik adını ayırır.

  - Virgül (`,`) özellikleri ayırır.

  - Sağ küme ayracı (`}`), biçimlendirme uzantısının sonu.

> [!NOTE]
> Teknik olarak, bu kaçış bir film şeridi özellik yolu için de çalışır, ancak genellikle var olan WPF nesneleri için nesne modellerinden geçiş yapmanız ve kaçışın gereksiz olması gerekir.

<a name="databinding_sa"></a>

## <a name="propertypath-for-animation-targets"></a>Animasyon hedefleri için PropertyPath

Bir animasyonun Target özelliği <xref:System.Windows.Freezable> ya da bir temel türü alan bir Dependency özelliği olmalıdır. Ancak, bir türdeki hedeflenen özellik ve son animasyon özelliği farklı nesnelerde bulunabilir. Animasyonlar için, özellik değerlerindeki nesne özelliği ilişkilerinin geçişi yaparak adlandırılmış animasyon hedefi nesnesinin özelliği ve amaçlanan hedef animasyon özelliği arasındaki bağlantıyı tanımlamak için bir özellik yolu kullanılır.

<a name="general"></a>

### <a name="general-object-property-considerations-for-animations"></a>Genel nesne-animasyonlar için özellik konuları

Genel olarak animasyon kavramları hakkında daha fazla bilgi için bkz. görsel taslaklara [genel bakış](../graphics-multimedia/storyboards-overview.md) ve [animasyona genel bakış](../graphics-multimedia/animation-overview.md).

Değer türü veya hareketlendirilen özellik bir <xref:System.Windows.Freezable> tür ya da ilkel olmalıdır. Yolu Başlatan özelliği, belirtilen <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> türde var olan bir bağımlılık özelliğinin adı olacak şekilde çözümlenmelidir.

Zaten dondurulmuş olan <xref:System.Windows.Freezable> bir animasyon için kopyalamayı desteklemek amacıyla, tarafından <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> belirtilen nesnenin bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement> türetilmiş sınıf olması gerekir.

<a name="singlestepanim"></a>

### <a name="single-property-on-the-target-object"></a>Hedef nesnedeki tek özellik

```xml
<animation Storyboard.TargetProperty="propertyName" .../>
```

`propertyName`Belirtilen <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> türde var olan bir bağımlılık özelliğinin adı olacak şekilde çözümlenmelidir.

<a name="indirectanim"></a>

### <a name="indirect-property-targeting"></a>Dolaylı Özellik hedefleme

```xml
<animation Storyboard.TargetProperty="propertyName.propertyName2" .../>
```

`propertyName`<xref:System.Windows.Freezable> belirtilen<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> türde var olan bir değer türü veya temel öğe olan bir özellik olmalıdır.

`propertyName2`değeri olan nesnede bulunan Dependency özelliğinin adı olmalıdır `propertyName`. Diğer bir `propertyName2` `propertyName` deyişle,türündebirbağımlılık<xref:System.Windows.DependencyProperty.PropertyType%2A>özelliği olarak bulunmalıdır.

Uygulanan stiller ve şablonlar nedeniyle animasyonların dolaylı olarak hedeflenmesi gerekir. Bir animasyonu hedeflemek için, bir <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> hedef nesne üzerinde ve bu ad, [x:Name](../../xaml-services/x-name-directive.md) veya <xref:System.Windows.FrameworkElement.Name%2A>ile oluşturulur. Şablon ve stil öğelerinin adları da olabilir, ancak bu adlar yalnızca stilin ve şablonun namescope içinde geçerlidir. (Şablonlar ve stiller, uygulama biçimlendirmesi ile ad kapsamları 'yi paylaşıyorsa, adlar benzersiz olamaz. Stiller ve şablonlar, örnekler arasında tam olarak paylaşılır ve yinelenen adları yeniden işlenir.) Bu nedenle, hareketlendirmek isteyebileceğiniz bir öğenin tek tek özellikleri bir stil veya şablondan geldiyse, bir stil şablonundan olmayan adlandırılmış bir öğe örneğiyle başlamanız ve sonra özelliğe ulaşmak için stil veya şablon görsel ağacını hedeflemek gerekir animasyon uygulamak istiyorsunuz.

Örneğin, <xref:System.Windows.Controls.Panel.Background%2A> <xref:System.Windows.Media.Brush> öğesinin özelliği bir tema şablonundan gelen tamamlanmış bir şeydir (aslında <xref:System.Windows.Media.SolidColorBrush>a). <xref:System.Windows.Controls.Panel> <xref:System.Windows.Media.Brush> Tamamen hareketlendirmek için, bir BrushAnimation (muhtemelen her <xref:System.Windows.Media.Brush> tür için bir tane) olması gerekir ve böyle bir tür yoktur. Fırçaya animasyon uygulamak için, bunun yerine belirli <xref:System.Windows.Media.Brush> bir türün özelliklerine animasyon uygulayabilirsiniz. Burada uygulamak <xref:System.Windows.Media.SolidColorBrush.Color%2A> için ' den <xref:System.Windows.Media.SolidColorBrush> ' a <xref:System.Windows.Media.Animation.ColorAnimation> erişmeniz gerekir. Bu örnek `Background.Color`için özellik yolu olacaktır.

<a name="attachedanim"></a>

### <a name="attached-properties"></a>Ekli Özellikler

```xml
<animation Storyboard.TargetProperty="(ownerType.propertyName)" .../>
```

Parantez, içindeki <xref:System.Windows.PropertyPath> bu özelliğin kısmi bir nitelik kullanılarak oluşturulması gerektiğini gösterir. Türü bulmak için bir XML ad alanı kullanabilir. Her derlemedeki <xref:System.Windows.Markup.XmlnsDefinitionAttribute> bildirimler aracılığıyla bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcinin erişebileceği aramatürleri.`ownerType` Çoğu uygulama, [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] ad alanına eşlenmiş varsayılan XML ad alanına sahiptir, bu nedenle bir ön ek genellikle yalnızca bu ad alanı dışında özel türler veya türler için gereklidir. `propertyName`, `ownerType`üzerinde varolan bir özelliğin adı olacak şekilde çözümlenmelidir. Olarak `propertyName` belirtilen özelliği bir <xref:System.Windows.DependencyProperty>olmalıdır. (Tüm [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Ekli Özellikler bağımlılık özellikleri olarak uygulanır, bu nedenle bu sorun yalnızca özel Ekli Özellikler için sorun olabilir.)

<a name="indexanim"></a>

### <a name="indexers"></a>Dizin Oluşturucular

```xml
<animation Storyboard.TargetProperty="propertyName.propertyName2[index].propertyName3" .../>
```

Çoğu bağımlılık özellikleri veya <xref:System.Windows.Freezable> türleri bir dizin oluşturucuyu desteklemez. Bu nedenle, bir animasyon yolundaki dizin oluşturucunun tek kullanımı, adlandırılmış hedefte zinciri Başlatan özelliği ile son animasyonlu özelliği arasında bir ara konumda bulunur. Belirtilen sözdiziminde, diğer bir deyişle `propertyName2`. Örneğin, ara özellik gibi bir özellik yolunda <xref:System.Windows.Media.TransformGroup> `RenderTransform.Children[1].Angle`bir koleksiyon ise, Dizin Oluşturucu kullanımı gerekli olabilir.

<a name="ppincode"></a>

## <a name="propertypath-in-code"></a>Kodda PropertyPath

' Nin nasıl <xref:System.Windows.PropertyPath>oluşturulacağı <xref:System.Windows.PropertyPath>dahil olmak üzere kod kullanımı, için <xref:System.Windows.PropertyPath>başvuru konusunda belgelenmiştir.

Genel olarak, <xref:System.Windows.PropertyPath> biri bağlama kullanımları ve en basit animasyon kullanımları ve bir diğeri de karmaşık animasyon kullanımları için olmak üzere iki farklı Oluşturucu kullanmak üzere tasarlanmıştır. Nesnenin dize olduğu, kullanımları bağlama için imzakullanın.<xref:System.Windows.PropertyPath.%23ctor%28System.Object%29> Nesnenin bir<xref:System.Windows.DependencyProperty>olduğu tek adımlı animasyon yolları için imzayıkullanın.<xref:System.Windows.PropertyPath.%23ctor%28System.Object%29> Karmaşık animasyonlar için imzayı kullanın. <xref:System.Windows.PropertyPath.%23ctor%28System.String%2CSystem.Object%5B%5D%29> Bu ikinci Oluşturucu ilk parametre için bir belirteç dizesi ve bir özellik yolu ilişkisi tanımlamak için belirteç dizesindeki pozisyonları dolduran nesne dizisi kullanır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.PropertyPath>
- [Veri Bağlamaya Genel Bakış](../data/data-binding-overview.md)
- [Görsel Taslaklara Genel Bakış](../graphics-multimedia/storyboards-overview.md)
