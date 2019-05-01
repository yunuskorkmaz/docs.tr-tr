---
title: PropertyPath XAML Sözdizimi
ms.date: 03/30/2017
helpviewer_keywords:
- PropertyPath object [WPF]
- XAML [WPF], PropertyPath object
ms.assetid: 0e3cdf07-abe6-460a-a9af-3764b4fd707f
ms.openlocfilehash: 7db435e45ddc55346af5ea5fdbcce611173c774b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053541"
---
# <a name="propertypath-xaml-syntax"></a>PropertyPath XAML Sözdizimi
<xref:System.Windows.PropertyPath> Nesne destekleyen karmaşık bir satır içi [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ele çeşitli özelliklerini ayarlamak için söz dizimi <xref:System.Windows.PropertyPath> değerlerine türü. Bu konu belgeleri <xref:System.Windows.PropertyPath> bağlama ve animasyon sözdizimleri için uygulanan sözdizimi.  

<a name="where"></a>   
## <a name="where-propertypath-is-used"></a>PropertyPath kullanıldığı  
 <xref:System.Windows.PropertyPath> çeşitli kullanılan ortak bir nesnedir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] özellikleri. Yaygın rağmen <xref:System.Windows.PropertyPath> her kullanımları özellik yolu bilgileri iletmek için alan özelliği olduğu <xref:System.Windows.PropertyPath> farklı bir tür olarak kullanılır. Bu nedenle, özellik başına temelinde sözdizimleri belge daha yararlı olur.  
  
 Öncelikle, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullanan <xref:System.Windows.PropertyPath> bir nesne veri kaynağı özelliklerini geçiş için nesne modeli yollarını açıklar ve hedeflenen animasyonları hedef yolunu tanımlamak için.  
  
 Stil ve şablon bazı özellikler gibi <xref:System.Windows.Setter.Property%2A?displayProperty=nameWithType> yüzeysel olarak benzer bir tam özellik adını Al bir <xref:System.Windows.PropertyPath>. Ancak bu bir true değil <xref:System.Windows.PropertyPath>; bunun yerine bir tam olan *owner.property* dize WPF tarafından etkinleştirilen biçimi kullanım [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcisi için tür dönüştürücüsü birlikte <xref:System.Windows.DependencyProperty>.  
  
<a name="databinding_s"></a>   
## <a name="propertypath-for-objects-in-data-binding"></a>Veri bağlama nesneler için PropertyPath  
 Veri bağlama bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hedef değeri herhangi bir bağımlılık özelliği olarak bağlayabilirsiniz gerçekleştirilmesine özelliği. Ancak, bir bağımlılık özelliği gibi bir veri bağlama kaynağı olması gerekmez; Bu, geçerli veri sağlayıcısı tarafından tanınan herhangi bir özellik türü olabilir. Özellik yolları için kullanılan özellikle <xref:System.Windows.Data.ObjectDataProvider>, bağlama kaynaktan almak için kullanılan [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] nesneleri ve özellikleri.  
  
 Bu veri bağlama Not [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] kullanmaz <xref:System.Windows.PropertyPath>kullanmaz çünkü <xref:System.Windows.Data.Binding.Path%2A> içinde <xref:System.Windows.Data.Binding>. Bunun yerine, kullandığınız <xref:System.Windows.Data.Binding.XPath%2A> ve geçerli bir XPath sözdizimi içine belirtin [!INCLUDE[TLA#tla_xmldom](../../../../includes/tlasharptla-xmldom-md.md)] veri. <xref:System.Windows.Data.Binding.XPath%2A> bir dize olarak da belirtilmiş, ancak burada belgelenmedi; bkz: [XMLDataProvider ve XPath sorgularını kullanarak XML verilerine bağlama](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).  
  
 Veri bağlama özelliğini yolları anlamak için bir bağlama için tek bir özellik değerine hedefleyebilir veya listeleri veya koleksiyonları hedef özellikler için bunun yerine bağlayabilirsiniz anahtardır. Koleksiyonları bağlanıyorsanız, örneğin bağlama bir <xref:System.Windows.Controls.ListBox> , genişletir kaç veri öğelerini koleksiyonda yer alan bağlı olarak, ardından özellik yolunuzu başvurması gereken bireysel koleksiyon öğeleri, koleksiyon nesnesi. Veri bağlama altyapısı, veri bağlama hedefi türü için otomatik olarak doldurma gibi davranış kaynaklanan kaynağı olarak kullanılan koleksiyon eşleşecek bir <xref:System.Windows.Controls.ListBox> öğeleri dizi olan.  
  
<a name="singlecurrent"></a>   
### <a name="single-property-on-the-immediate-object-as-data-context"></a>Veri bağlamı olarak anında nesnesindeki tek özelliği  
  
```xml  
<Binding Path="propertyName" .../>  
```  
  
 *propertyName* geçerli olan bir özelliğin adını çözülmesi gerekir <xref:System.Windows.FrameworkElement.DataContext%2A> için bir <xref:System.Windows.Data.Binding.Path%2A> kullanım. Bağlamanız kaynağını güncelleştirir, bu özelliği okuma/yazma olmalıdır ve kaynak nesnesi değişebilir olmalıdır.  
  
<a name="singleindex"></a>   
### <a name="single-indexer-on-the-immediate-object-as-data-context"></a>Veri bağlamı olarak anında nesne üzerinde tek bir dizin oluşturucu  
  
```xml  
<Binding Path="[key]" .../>  
```  
  
 `key` bir sözlük veya karma tablo türü belirtilmiş dizine veya tamsayı dizini bir dizi olmalıdır. Ayrıca, anahtarın değeri özelliği doğrudan bağlanabilir, uygulandığı bir türü olmalıdır. Örneğin, dize ve dize değerlerini içeren bir karma tablo bu şekilde metin bağlamak için kullanılabilir bir <xref:System.Windows.Controls.TextBox>. Veya, bir koleksiyon veya ATL önemli noktalar varsa, bir hedef toplama özelliğine bağlamak için bu sözdizimini kullanabilirsiniz. Aksi takdirde, aşağıdaki gibi bir söz dizimi aracılığıyla belirli bir özelliğine başvurmak ihtiyacınız `<Binding Path="[key].propertyName" .../>`.  
  
 Gerekirse dizinin türünü belirtebilirsiniz. Bu yönü bir dizine alınan özelliğinin yolu ile ilgili daha fazla ayrıntı için bkz. <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>.  
  
<a name="multipleindirect"></a>   
### <a name="multiple-property-indirect-property-targeting"></a>Birden çok özelliği (dolaylı özelliği desteği)  
  
```xml  
<Binding Path="propertyName.propertyName2" .../>  
```  
  
 `propertyName` Geçerli bir özelliğin adını çözülmesi gerekir <xref:System.Windows.FrameworkElement.DataContext%2A>. Yol özellikleri `propertyName` ve `propertyName2` bir ilişkide mevcut herhangi bir özelliği olabilir burada `propertyName2` değeri türde bulunan bir özelliktir `propertyName`.  
  
<a name="singleattached"></a>   
### <a name="single-property-attached-or-otherwise-type-qualified"></a>Ekli veya yetkili türde tek özelliği  
  
```xml  
<object property="(ownerType.propertyName)" .../>  
```  
  
 Parantezler belirtmek bu özellik bir <xref:System.Windows.PropertyPath> kısmi bir nitelik kullanılarak oluşturulması. Bir XML ad alanı, uygun bir eşleme türüyle bulmak için kullanabilirsiniz. `ownerType` Aramaları türleri bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemciye sahip erişimi ile <xref:System.Windows.Markup.XmlnsDefinitionAttribute> her derlemede bildirimleri. Çoğu uygulama için eşlenmiş varsayılan XML ad alanına sahip [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] ad alanı öneki genellikle yalnızca özel türleri için gerekli olan ya da aksi takdirde, ad alanı dışında türleri.  `propertyName` Mevcut bir özelliğin adını çözülmesi gerekir `ownerType`. Bu sözdizimi, genellikle aşağıdaki durumlarından biri kullanılır:  
  
- Belirtilen yolun [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bir stil veya belirtilen bir hedef türü olmayan şablon olmasıdır. Tam bir kullanım olmayan stil, şablon olmayan durumlarda özelliği bir tür değil bir örneğinde var olduğundan genellikle Bunun dışındaki durumlarda geçerli değil.  
  
- Ekli özelliği özelliğidir.  
  
- Statik bir özellik için bağlama.  
  
 Özelliği görsel taslak hedefi olarak kullanım için belirtilen `propertyName` olmalıdır bir <xref:System.Windows.DependencyProperty>.  
  
<a name="sourcetraversal"></a>   
### <a name="source-traversal-binding-to-hierarchies-of-collections"></a>Kaynak geçişi (koleksiyonlarının Hiyerarşilere bağlama)  
  
```xml  
<object Path="propertyName/propertyNameX" .../>  
```  
  
 / Bu sözdizimi hiyerarşik veri kaynağı nesnesi ve art arda gelen içeren bir hiyerarşiye birden çok adım içinde gezinmek için kullanılan / karakterleri desteklenir. Kendi görünümünün kullanıcı Arabirimi ile verileri eşitleyerek belirlenir geçerli kayıt işaretçisi konumunu, kaynak geçişi hesaplar. Hiyerarşik veri kaynağı nesneleri ve veri bağlama, geçerli kayıt işaretçisi kavramı ile bağlama hakkında daha fazla bilgi için bkz: [hiyerarşik veriler ile ana öğe-ayrıntı desenini kullanma](../data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md) veya [Data Binding Overview](../data/data-binding-overview.md).  
  
> [!NOTE]
>  Yüzeysel olarak, bu sözdizimi benzer [!INCLUDE[TLA2#tla_xpath](../../../../includes/tla2sharptla-xpath-md.md)]. Gerçek bir [!INCLUDE[TLA2#tla_xpath](../../../../includes/tla2sharptla-xpath-md.md)] bağlama ifadesi bir [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] veri kaynağı olarak kullanılan değil bir <xref:System.Windows.Data.Binding.Path%2A> değer ve bunun yerine birbirini için kullanılması gereken <xref:System.Windows.Data.Binding.XPath%2A> özelliği.  
  
### <a name="collection-views"></a>Koleksiyon Görünümleri  
 Adlandırılmış koleksiyon görünümü başvurmak için karma karakteri ile koleksiyon görünümü adı ön eki (`#`).  
  
### <a name="current-record-pointer"></a>Geçerli kayıt işaretçisi  
 Koleksiyon görünümü veya ana ayrıntı veri bağlama senaryosu için geçerli kayıt işaretçi başvurusu yapmak için yol dizesini bir eğik çizgi ile Başlat (`/`). Herhangi bir yola son eğik geçerli kayıt işaretçisinden başlangıç geçiş yapılır.  
  
### <a name="multiple-indexers"></a>Birden çok dizin oluşturucu  
  
```  
<object Path="[index1,index2...]" .../>  
or  
<object Path="propertyName[index,index2...]" .../>  
```  
  
 Belirli bir nesne birden çok dizin oluşturucu destekliyorsa, bu dizin oluşturucular sırada, söz dizimi başvuran bir diziye benzer belirtilebilir. Söz konusu nesne geçerli bağlam ya da birden çok dizin nesnesi içeren bir özelliğin değerini olabilir.  
  
 Varsayılan olarak, dizin oluşturucu değerleri temel nesnenin özelliklerini kullanarak yazılmalıdır. Gerekirse dizinin türünü belirtebilirsiniz. Oluşturucularının hakkında daha fazla bilgi için bkz <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>.  
  
<a name="mixing"></a>   
### <a name="mixing-syntaxes"></a>Sözdizimleri karıştırma  
 Yukarıda gösterilen sözdizimleri her interspersed. Örneğin, belirli bir x, y, renk için bir özellik yolu oluşturan bir örneği verilmiştir bir `ColorGrid` piksel Kılavuzu dizisi içeren özellik <xref:System.Windows.Media.SolidColorBrush> nesneler:  
  
```xml  
<Rectangle Fill="{Binding ColorGrid[20,30].SolidColorBrushResult}" .../>  
```  
  
### <a name="escapes-for-property-path-strings"></a>Özellik yolu dizeleri için kaçış karakterleri  
 Belirli iş nesneleri için bir kaçış dizisi özelliği yol dizesi düzgün ayrıştırılabilmesi için burada gerektiren bir durumla karşılaşabilirsiniz. Bu karakterlerden biri çok benzer adlandırma etkileşimi sorunlar genellikle iş nesnesi tanımlamak için kullanılan dillerde olduğundan kaçış gerek nadir olmalıdır.  
  
- Oluşturucular ([]) sonraki karakteri inceltme işareti (^) atlar.  
  
- (XML varlıkları kullanarak), XML dil tanımına özel belirli karakter kaçış gerekir. Kullanım `&` karakteri kaçırmak için "&". Kullanım `>` bitiş etiketi kaçış ">".  
  
- Kaçış gerekir (ters eğik çizgi kullanarak `\`) WPF XAML ayrıştırıcı davranışını bir işaretleme uzantısı işlenirken özel karakter.  
  
    - Ters eğik çizgi (`\`) kaçış karakteri.  
  
    - Eşittir işareti (`=`) özellik adı, özellik değerinden ayırır.  
  
    - Virgül (`,`) özellikleri ayırır.  
  
    - Sağ büyük ayraç (`}`) bir işaretleme uzantısı sonudur.  
  
> [!NOTE]
>  Teknik olarak bu çıkışları iş bir görsel taslak özellik yolu için Ayrıca, ancak genellikle varolan WPF nesneleri için nesne modellerini geçiş yapıyorsanız ve kaçış gereksiz olmalıdır.  
  
<a name="databinding_sa"></a>   
## <a name="propertypath-for-animation-targets"></a>PropertyPath animasyon hedefleri için  
 Hedef özelliği bir animasyon alır ya da bir bağımlılık özelliği olmalıdır bir <xref:System.Windows.Freezable> veya basit bir tür. Ancak, bir tür hedeflenen özellik ve animasyonlu özellik farklı nesneler üzerinde bulunabilir. Animasyon için özellik yolu nesne özelliğini özellik değerleri ilişkilerde geçiş tarafından adlandırılmış animasyon hedef nesnenin özellik ve hedef animasyon özelliği arasındaki bağlantıyı tanımlamak için kullanılır.  
  
<a name="general"></a>   
### <a name="general-object-property-considerations-for-animations"></a>Animasyonlara genel nesne özelliğini dikkate alınacak noktalar  
 Animasyon hakkında daha fazla bilgi için genel olarak, bkz [görsel taslaklara genel bakış](../graphics-multimedia/storyboards-overview.md) ve [animasyona genel bakış](../graphics-multimedia/animation-overview.md).  
  
 Değer türü veya animasyon uygulanan bir özellik olmalıdır bir <xref:System.Windows.Freezable> türü veya basit bir tür. Yolun başlatan özellik belirtilen var olan bir bağımlılık özelliği adı çözülmesi gerekir <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> türü.  
  
 Animasyon için kopyalama desteklemek için bir <xref:System.Windows.Freezable> , zaten dondurulmuş, tarafından belirtilen nesnede <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> olmalıdır bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement> türetilmiş sınıf.  
  
<a name="singlestepanim"></a>   
### <a name="single-property-on-the-target-object"></a>Hedef nesne üzerinde tek özelliği  
  
```xml  
<animation Storyboard.TargetProperty="propertyName" .../>  
```  
  
 `propertyName` Belirtilen mevcut bir bağımlılık özelliği adı çözülmesi gerekir <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> türü.  
  
<a name="indirectanim"></a>   
### <a name="indirect-property-targeting"></a>Dolaylı özelliğini hedefleme  
  
```xml  
<animation Storyboard.TargetProperty="propertyName.propertyName2" .../>  
```  
  
 `propertyName` ya da özelliği olmalıdır bir <xref:System.Windows.Freezable> değer türü veya belirtilen mevcut bir basit tür <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> türü.  
  
 `propertyName2` bağımlılık özelliğinin değeri bir nesne üzerinde var olan ad `propertyName`. Diğer bir deyişle, `propertyName2` türü üzerinde bir bağımlılık özelliği olarak bulunmalıdır `propertyName` <xref:System.Windows.DependencyProperty.PropertyType%2A>.  
  
 Dolaylı animasyonları hedefleme uygulanan stiller ve şablonlar nedeniyle gereklidir. Bir animasyon hedeflemek için gereken bir <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> hedef nesne ve, adı tarafından kurulur [x: Name](../../xaml-services/x-name-directive.md) veya <xref:System.Windows.FrameworkElement.Name%2A>. Bu adları yalnızca şablon ve stil öğeleri de adlara sahip olsa da, stil ve şablon namescope içinde geçerli değil. (Ad kapsamları ile uygulama biçimlendirme paylaşıyorsa, şablonlar ve stiller adları benzersiz silinemedi. "Stilleri ve şablonları tam anlamıyla örnekleri arasında paylaşılır ve yinelenen adlara neden olabilir.) Özellikler animasyon eklemek istediğiniz bir öğenin bir stil veya şablondan geliyorsa, bu nedenle, bir stil şablonundan değil bir adlandırılmış öğe örneğiyle başlatın ve sonra özellik gelmesi stil veya şablon görsel ağacında hedef için ihtiyacınız animasyon uygulamak istediğiniz.  
  
 Örneğin, <xref:System.Windows.Controls.Panel.Background%2A> özelliği bir <xref:System.Windows.Controls.Panel> bir tamamlandıktan <xref:System.Windows.Media.Brush> (aslında bir <xref:System.Windows.Media.SolidColorBrush>) bir tema şablondan gelen. Animasyon uygulamak için bir <xref:System.Windows.Media.Brush> tamamen var bir BrushAnimation olması gerekir (büyük olasılıkla her <xref:System.Windows.Media.Brush> türü) ve böyle bir türü vardır. Fırça animasyon uygulamak için bunun yerine belirli bir özelliklerine animasyon <xref:System.Windows.Media.Brush> türü. Alma ihtiyacınız <xref:System.Windows.Media.SolidColorBrush> için kendi <xref:System.Windows.Media.SolidColorBrush.Color%2A> uygulamak için bir <xref:System.Windows.Media.Animation.ColorAnimation> vardır. Bu örnek için özellik yol `Background.Color`.  
  
<a name="attachedanim"></a>   
### <a name="attached-properties"></a>Ekli Özellikler  
  
```xml  
<animation Storyboard.TargetProperty="(ownerType.propertyName)" .../>  
```  
  
 Parantezler belirtmek bu özellik bir <xref:System.Windows.PropertyPath> kısmi bir nitelik kullanılarak oluşturulması. Bir XML ad alanı, tür bulmak için kullanabilirsiniz. `ownerType` Aramaları türleri bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemciye sahip erişimi ile <xref:System.Windows.Markup.XmlnsDefinitionAttribute> her derlemede bildirimleri. Çoğu uygulama için eşlenmiş varsayılan XML ad alanına sahip [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] ad alanı öneki genellikle yalnızca özel türleri için gerekli olan ya da aksi takdirde, ad alanı dışında türleri. `propertyName` Mevcut bir özelliğin adını çözülmesi gerekir `ownerType`. Olarak belirtilen özellik `propertyName` olmalıdır bir <xref:System.Windows.DependencyProperty>. (Tüm [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kaygısı özel ekli özellikler, yalnızca bu sorun, bu nedenle, iliştirilmiş özellikler bağımlılık özellikleri uygulanır.)  
  
<a name="indexanim"></a>   
### <a name="indexers"></a>Dizin Oluşturucular  
  
```xml  
<animation Storyboard.TargetProperty="propertyName.propertyName2[index].propertyName3" .../>  
```  
  
 Bağımlılık özelliklerinin çoğu veya <xref:System.Windows.Freezable> türleri, dizin oluşturucu desteklemez. Bu nedenle, yalnızca bir animasyon yolu bir dizin oluşturucu için adlandırılmış hedef zinciri başlatan özellik ve animasyonlu özellik arasında bir ara konumundaki kullanımdır. Sağlanan sözdiziminde olan `propertyName2`. Örneğin, bir dizin oluşturucu kullanımını Ara özellik koleksiyonu gibi ise gerekli olabilir <xref:System.Windows.Media.TransformGroup>, bir özellik yolda gibi `RenderTransform.Children[1].Angle`.  
  
<a name="ppincode"></a>   
## <a name="propertypath-in-code"></a>Kod içinde PropertyPath  
 Kod için kullanım <xref:System.Windows.PropertyPath>, nasıl oluşturulacağını dahil olmak üzere bir <xref:System.Windows.PropertyPath>, için başvuru konusu belgelenen <xref:System.Windows.PropertyPath>.  
  
 Genel olarak, <xref:System.Windows.PropertyPath> iki farklı Oluşturucu, bir bağlama kullanımları ve basit animasyon kullanımları için ve biri karmaşık animasyon kullanımları için kullanmak üzere tasarlanmıştır. Kullanım <xref:System.Windows.PropertyPath.%23ctor%28System.Object%29> imza nesnesinin bir dize olduğu kullanımları, bağlama için. Kullanım <xref:System.Windows.PropertyPath.%23ctor%28System.Object%29> tek adımlı animasyon yolları, nesne olduğu için imza bir <xref:System.Windows.DependencyProperty>. Kullanım <xref:System.Windows.PropertyPath.%23ctor%28System.String%2CSystem.Object%5B%5D%29> karmaşık animasyonları imzası. Bu ikinci oluşturucu, ilk parametre ve bir özellik yolu ilişki tanımlamak için belirteç dizesinde konumları dolduracak nesnelerinin bir dizisi için bir belirteç dizesini kullanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.PropertyPath>
- [Veri Bağlamaya Genel Bakış](../data/data-binding-overview.md)
- [Görsel Taslaklara Genel Bakış](../graphics-multimedia/storyboards-overview.md)
