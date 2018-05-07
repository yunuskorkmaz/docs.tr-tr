---
title: PropertyPath XAML Sözdizimi
ms.date: 03/30/2017
helpviewer_keywords:
- PropertyPath object [WPF]
- XAML [WPF], PropertyPath object
ms.assetid: 0e3cdf07-abe6-460a-a9af-3764b4fd707f
ms.openlocfilehash: 547c7d009d2fecf863284324c7ea45006d20d20c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="propertypath-xaml-syntax"></a>PropertyPath XAML Sözdizimi
<xref:System.Windows.PropertyPath> Nesnesi destekler karmaşık bir satır içi [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ele çeşitli özelliklerini ayarlamak için sözdizimi <xref:System.Windows.PropertyPath> değer türü. Bu konuda belgeleri <xref:System.Windows.PropertyPath> bağlama ve animasyon sözdizimleri uygulanan olarak sözdizimi.  
    
  
<a name="where"></a>   
## <a name="where-propertypath-is-used"></a>PropertyPath nerede kullanılır  
 <xref:System.Windows.PropertyPath> birkaç içinde kullanılan yaygın bir nesnedir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] özellikleri. Ortak kullanarak rağmen <xref:System.Windows.PropertyPath> her kullanımları özelliği yol bilgileri iletmek için alan özellik nerede <xref:System.Windows.PropertyPath> farklı bir tür olarak kullanılır. Bu nedenle, özellik başına temelinde sözdizimleri belge daha pratik olur.  
  
 Öncelikle, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullandığı <xref:System.Windows.PropertyPath> nesne veri kaynağının özelliklerini geçiş için nesne modeli yollarını açıklar ve hedeflenen animasyonları hedef yolu açıklamak için.  
  
 Bazı stil ve şablon özellikler gibi <xref:System.Windows.Setter.Property%2A?displayProperty=nameWithType> yüzeysel olarak benzer bir tam özellik adı ele bir <xref:System.Windows.PropertyPath>. Ancak bu bir true değil <xref:System.Windows.PropertyPath>; bunun yerine bir tam olduğu *owner.property* dize WPF tarafından etkin biçimde kullanım [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci türü dönüştürücü ile birlikte <xref:System.Windows.DependencyProperty>.  
  
<a name="databinding_s"></a>   
## <a name="propertypath-for-objects-in-data-binding"></a>Veri bağlama nesneler için PropertyPath  
 Veri bağlama bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] herhangi bir bağımlılık özelliğinin hedef değer bağlayabilirsiniz aslına özelliği. Ancak, böyle bir veri bağlama kaynağı bağımlılık özelliği olması gerekmez; Geçerli veri sağlayıcısı tarafından tanınan herhangi bir özellik türü olabilir. Özellik yolları için kullanılan özellikle <xref:System.Windows.Data.ObjectDataProvider>, bağlama kaynaklardan almak için kullanılan [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] nesneler ve onların özellikleri.  
  
 Bu veri bağlama Not [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] kullanmayan <xref:System.Windows.PropertyPath>kullanmaz çünkü <xref:System.Windows.Data.Binding.Path%2A> içinde <xref:System.Windows.Data.Binding>. Bunun yerine, kullandığınız <xref:System.Windows.Data.Binding.XPath%2A> ve geçerli XPath sözdizimine belirtin [!INCLUDE[TLA#tla_xmldom](../../../../includes/tlasharptla-xmldom-md.md)] verileri. <xref:System.Windows.Data.Binding.XPath%2A> bir dize olarak da belirtilmiş, ancak burada belgelenmemiştir; bkz: [XML verileri kullanarak bir XMLDataProvider ve XPath sorguları bağlamak](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).  
  
 Veri bağlama özelliği yollarında anlamak için bir tek bir özellik değerine bağlamayı hedefleyebilirsiniz veya bunun yerine listeler veya koleksiyonlar alan hedef özellikleri bağlayabilirsiniz anahtardır. Koleksiyonları bağlanıyorsanız, örneğin bağlama bir <xref:System.Windows.Controls.ListBox> , genişletin kaç tane veri öğelerini koleksiyonda yer alan bağlı olarak, sonra da özellik yolu başvurması gereken bireysel koleksiyon öğeleri, koleksiyon nesnesi. Veri bağlama altyapısı veri bağlama hedefi türünü otomatik olarak doldurma gibi davranış kaynaklanan kaynağı olarak kullanılan koleksiyonu eşleşir bir <xref:System.Windows.Controls.ListBox> ile öğeleri dizi.  
  
<a name="singlecurrent"></a>   
### <a name="single-property-on-the-immediate-object-as-data-context"></a>Veri bağlamı olarak anlık nesnesi üzerinde tek özellik  
  
```xml  
<Binding Path="propertyName" .../>  
```  
  
 *propertyName* geçerli olan bir özelliğin adını çözülmesi gerekir <xref:System.Windows.FrameworkElement.DataContext%2A> için bir <xref:System.Windows.Data.Binding.Path%2A> kullanımı. Kaynağını, bağlama güncelleştirir, bu özelliği okuma/yazma olmalıdır ve kaynak nesnesi kesilebilir olmalıdır.  
  
<a name="singleindex"></a>   
### <a name="single-indexer-on-the-immediate-object-as-data-context"></a>Tek Dizin Oluşturucu veri bağlamı hemen nesnesinde  
  
```xml  
<Binding Path="[key]" .../>  
```  
  
 `key` bir sözlük veya karma tablosu yazılan dizine veya tamsayı dizini dizi olması gerekir. Ayrıca, anahtarın değerini uygulanmış burada özellik için doğrudan bağlanabilir bir türü olmalıdır. Örneğin, dize anahtarları ve dize değerlerini içeren bir karma tablosu bu şekilde için metin bağlamak için kullanılabilir bir <xref:System.Windows.Controls.TextBox>. Veya, bir toplama veya alt dizin anahtarı işaret ediyorsa, bir hedef koleksiyon özelliğine bağlamak için bu söz dizimini kullanabilirsiniz. Aksi halde, bir söz dizimi aracılığıyla belirli bir özellik gibi başvurmanız gerekir `<Binding Path="[``key``].``propertyName``" .../>`.  
  
 Gerekirse dizin türünü belirtebilirsiniz. Bir dizin oluşturulmuş özellik yolunun bu yönünün hakkında daha fazla bilgi için bkz: <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>.  
  
<a name="multipleindirect"></a>   
### <a name="multiple-property-indirect-property-targeting"></a>Birden çok özellik (dolaylı özellik hedeflemesi)  
  
```xml  
<Binding Path="propertyName.propertyName2" .../>  
```  
  
 `propertyName` Geçerli bir özellik adı çözülmesi gerekir <xref:System.Windows.FrameworkElement.DataContext%2A>. Yol özellikleri `propertyName` ve `propertyName2` bir ilişkide mevcut herhangi bir özellik olabilir nerede `propertyName2` değeri türünde bulunan bir özelliktir `propertyName`.  
  
<a name="singleattached"></a>   
### <a name="single-property-attached-or-otherwise-type-qualified"></a>Ekli veya yetkili türde tek özelliği  
  
```xml  
<object property="(ownerType.propertyName)" .../>  
```  
  
 Parantez belirtmek bu özellikte bir <xref:System.Windows.PropertyPath> kısmi nitelik kullanılarak oluşturulması. Bir XML ad alanı, uygun bir eşleşme türüyle bulmak için kullanabilirsiniz. `ownerType` Aramaları türleri bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemciye sahip erişimi ile <xref:System.Windows.Markup.XmlnsDefinitionAttribute> her derleme bildirimlerinde. Çoğu uygulama eşlenmiş varsayılan XML ad alanına sahip [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] bir önek genellikle yalnızca özel türleri için gerekli olan veya aksi halde bu ad alanı dışında türleri için ad.  `propertyName` Mevcut bir özellik adı çözülmesi gerekir `ownerType`. Bu sözdizimi genellikle aşağıdaki durumlardan biri için kullanılır:  
  
-   Yolun belirtilen [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bir stil veya belirtilen bir hedef türü yok şablonda olmasıdır. Tam bir kullanım stil olmayan, şablon olmayan durumlarda bir örneği, bir türde bir özellik var olmadığından genellikle Bunun dışındaki durumlarda geçerli değil.  
  
-   Özelliği bağlı bir özelliktir.  
  
-   Bir statik özelliğe bağlarsınız.  
  
 Olarak özelliği film şeridi hedef olarak kullanmak için belirtilen `propertyName` olmalıdır bir <xref:System.Windows.DependencyProperty>.  
  
<a name="sourcetraversal"></a>   
### <a name="source-traversal-binding-to-hierarchies-of-collections"></a>Kaynak çapraz geçişi (Koleksiyonların Hiyerarşilerine Bağlama)  
  
```xml  
<object Path="propertyName/propertyNameX" .../>  
```  
  
 / Bu sözdizimi hiyerarşik veri kaynağı nesnesi ve art arda hiyerarşisiyle içine birden çok adımı içinde gezinmek için kullanılan / karakterleri desteklenir. Kendi görünüm kullanıcı Arabirimi ile veri eşitleme tarafından belirlenen geçerli kayıt işaretçisini konumunu kaynak geçişi hesaplar. Hiyerarşik veri kaynağı nesneleri ve Veri bağlamada geçerli kayıt işaretçisi kavramı ile bağlama hakkında daha fazla bilgi için bkz: [hiyerarşik veriler ile ana-ayrıntı desenini kullanma](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md) veya [veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
> [!NOTE]
>  Yüzeysel olarak, bu söz dizimini benzer [!INCLUDE[TLA2#tla_xpath](../../../../includes/tla2sharptla-xpath-md.md)]. Gerçek [!INCLUDE[TLA2#tla_xpath](../../../../includes/tla2sharptla-xpath-md.md)] ifade bağlama için bir [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] veri kaynağı olarak kullanılan değil bir <xref:System.Windows.Data.Binding.Path%2A> değeri ve bunun yerine birbirini dışlayan için kullanılması gereken <xref:System.Windows.Data.Binding.XPath%2A> özelliği.  
  
### <a name="collection-views"></a>Koleksiyon görünümleri  
 Adlandırılmış bir koleksiyon görünümüne başvurmak için karma karakteri koleksiyon görünümü adıyla önek (`#`).  
  
### <a name="current-record-pointer"></a>Geçerli kayıt işaretçisi  
 Bir koleksiyon görünümü veya ana ayrıntı veri bağlama senaryosu için geçerli kayıt işaretçi başvuru için eğik çizgiyle yol dizesi başlatın (`/`). Herhangi bir yol eğik geçmiş geçerli kayıt işaretçi başlayarak geçiş yapılır.  
  
### <a name="multiple-indexers"></a>Birden çok dizin oluşturucular  
  
```  
<object Path="[index1,index2...]" .../>  
or  
<object Path="propertyName[index,index2...]" .../>  
```  
  
 Belirli bir nesne birden çok dizin oluşturucu destekliyorsa, bu dizin oluşturucular sırada sözdizimi başvuran bir diziye benzer belirtilebilir. Söz konusu nesne geçerli bağlam veya birden çok dizin nesnesi içeren bir özelliğin değeri olabilir.  
  
 Varsayılan olarak, dizin oluşturucu değerlerin temel alınan nesnenin özelliklerini kullanarak yazılmalıdır. Gerekirse dizin türünü belirtebilirsiniz. Oluşturucularının hakkında daha fazla bilgi için bkz: <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>.  
  
<a name="mixing"></a>   
### <a name="mixing-syntaxes"></a>Sözdizimi karıştırma  
 Yukarıda gösterilen sözdizimleri her interspersed. Örneğin, aşağıdaki belirli bir x, y rengi için bir özellik yolu oluşturan bir örnektir bir `ColorGrid` piksel kılavuz dizisi içeren özelliği <xref:System.Windows.Media.SolidColorBrush> nesneler:  
  
```xml  
<Rectangle Fill="{Binding ColorGrid[20,30].SolidColorBrushResult}" .../>  
```  
  
### <a name="escapes-for-property-path-strings"></a>Özellik yolu dizeleri için kaçış karakterleri  
 Belirli iş nesneleri için burada özellik yol dizesini doğru ayrıştırmak için kaçış dizisi gerektiren bir durumla karşılaşabilirsiniz. Bu karakterlerin çoğu, genellikle iş nesnesi tanımlamak için kullanılacak olan dillerde benzer adlandırma etkileşim sorunları olduğundan kaçış gereksinimi seyrek, olmalıdır.  
  
-   ([]) Dizin oluşturucular içinde düzeltme işareti karakteri (^) sonraki karakteri atlar.  
  
-   (XML varlıkları kullanarak) XML dil tanımına özel belirli karakterler kaçış gerekir. Kullanım `&` değerinden kaçınmak için "&". Kullanım `>` bitiş etiketi kaçınmak için ">".  
  
-   Kaçış gerekir (ters eğik çizgi kullanarak `\`) WPF XAML ayrıştırıcı davranış biçimlendirme uzantısı işlemek için özel karakter.  
  
    -   Ters eğik çizgi (`\`) kaçış karakteri.  
  
    -   Eşittir işaretinden (`=`) özellik değerinden özellik adını ayırır.  
  
    -   Virgül (`,`) özellikleri ayırır.  
  
    -   Sağ kaşlı ayraç (`}`) biçimlendirme uzantısı sonudur.  
  
> [!NOTE]
>  Teknik olarak, bu çıkışları film şeridi özellik yolu için de, çalışır, ancak genellikle varolan WPF nesneleri için nesne modellerini geçiş yapıyorsanız ve kaçış gereksiz olmalıdır.  
  
<a name="databinding_sa"></a>   
## <a name="propertypath-for-animation-targets"></a>Animasyon hedefleri için PropertyPath  
 Animasyonun hedef özelliği ya da alan bağımlılık özelliği olmalıdır bir <xref:System.Windows.Freezable> veya basit türü. Ancak, bir tür hedeflenen özellik ve animasyonlu özellik farklı nesneler üzerinde bulunabilir. Animasyon için özellik yolu özellik değerlerini nesne özelliği ilişkilerde geçme tarafından adlandırılmış animasyon hedef nesnenin özellik hedeflenen hedef animasyon özelliği arasında bağlantı tanımlamak için kullanılır.  
  
<a name="general"></a>   
### <a name="general-object-property-considerations-for-animations"></a>Animasyon için genel nesne-özellik konuları  
 Animasyon hakkında daha fazla bilgi için genel olarak, bkz: kavramlar [film şeritleri genel bakış](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md) ve [animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 Değer türü veya özelliğin ya da olmalıdır bir <xref:System.Windows.Freezable> türü veya basit bir tür. Yolun başlatan özellik belirtilen adda bir bağımlılık özelliğinin adını çözülmesi gerekir <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> türü.  
  
 Animasyon için kopyalama desteklemek için bir <xref:System.Windows.Freezable> , zaten dondurulmuş, tarafından belirtilen nesne <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> olmalıdır bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement> türetilmiş sınıf.  
  
<a name="singlestepanim"></a>   
### <a name="single-property-on-the-target-object"></a>Hedef nesne üzerinde tek bir özellik  
  
```xml  
<animation Storyboard.TargetProperty="propertyName" .../>  
```  
  
 `propertyName` Belirtilen adda bir bağımlılık özelliğinin adını çözülmesi gerekir <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> türü.  
  
<a name="indirectanim"></a>   
### <a name="indirect-property-targeting"></a>Dolaylı özellik hedeflemesi  
  
```xml  
<animation Storyboard.TargetProperty="propertyName.propertyName2" .../>  
```  
  
 `propertyName` herhangi bir özellik olmalıdır bir <xref:System.Windows.Freezable> değer türü veya belirtilen mevcut bir temel <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> türü.  
  
 `propertyName2` değeri olan nesnede bulunan bir bağımlılık özelliği adı olmalıdır `propertyName`. Diğer bir deyişle, `propertyName2` türü üzerinde bir bağımlılık özelliği olarak mevcut olmalıdır `propertyName` <xref:System.Windows.DependencyProperty.PropertyType%2A>.  
  
 Animasyonların dolaylı hedeflemesi uygulanan stiller ve şablonları nedeniyle gereklidir. Bir animasyon hedeflemek için gereksinim duyduğunuz bir <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> hedef nesne ve, ad tarafından oluşturulur [x: Name](../../../../docs/framework/xaml-services/x-name-directive.md) veya <xref:System.Windows.FrameworkElement.Name%2A>. Şablon ve stil öğeleri de adlara sahip olsa da, bu adları yalnızca stil ve şablon isim alanı içinde geçerlidir. (Şablonlar ve stiller uygulama biçimlendirmesi ile ad kapsamları paylaşıyorsa, adlarının benzersiz olması uygulanamadı. Stilleri ve şablonları tam anlamıyla örnekleri arasında paylaşılır ve yinelenen adlara neden olabilir.) Ayrı ayrı özellikler animasyon eklemek istediğiniz bir öğenin bir stil veya şablondan geliyorsa, bu nedenle, bir stil şablonundan olmayan adlandırılmış öğesi örnek ile başlayın ve özellik gelmesi stili veya şablon görsel ağaç içine hedef yapmanız animasyon istiyor.  
  
 Örneğin, <xref:System.Windows.Controls.Panel.Background%2A> özelliği bir <xref:System.Windows.Controls.Panel> bir tamamlandıktan <xref:System.Windows.Media.Brush> (gerçekte bir <xref:System.Windows.Media.SolidColorBrush>) bir tema şablonundan gelen. Animasyon uygulamak için bir <xref:System.Windows.Media.Brush> tamamen var. gerekir bir BrushAnimation olmalıdır (büyük olasılıkla her <xref:System.Windows.Media.Brush> türü) ve bu tür türü yok. Fırça animasyon için bunun yerine belirli bir özelliklerini animasyon <xref:System.Windows.Media.Brush> türü. Almanız gereken <xref:System.Windows.Media.SolidColorBrush> için kendi <xref:System.Windows.Media.SolidColorBrush.Color%2A> uygulamak için bir <xref:System.Windows.Media.Animation.ColorAnimation> vardır. Bu örnek için özellik yol `Background.Color`.  
  
<a name="attachedanim"></a>   
### <a name="attached-properties"></a>Ekli Özellikler  
  
```xml  
<animation Storyboard.TargetProperty="(ownerType.propertyName)" .../>  
```  
  
 Parantez belirtmek bu özellikte bir <xref:System.Windows.PropertyPath> kısmi nitelik kullanılarak oluşturulması. Bir XML ad alanı, tür bulmak için kullanabilirsiniz. `ownerType` Aramaları türleri bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemciye sahip erişimi ile <xref:System.Windows.Markup.XmlnsDefinitionAttribute> her derleme bildirimlerinde. Çoğu uygulama eşlenmiş varsayılan XML ad alanına sahip [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] bir önek genellikle yalnızca özel türleri için gerekli olan veya aksi halde bu ad alanı dışında türleri için ad. `propertyName` Mevcut bir özellik adı çözülmesi gerekir `ownerType`. Olarak belirtilen özellik `propertyName` olmalıdır bir <xref:System.Windows.DependencyProperty>. (Tüm [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Bu sorun yalnızca özel ekli özellikler kaygısı, böylece ekli özellikler bağımlılık özelliği olarak uygulanır.)  
  
<a name="indexanim"></a>   
### <a name="indexers"></a>Dizin Oluşturucular  
  
```xml  
<animation Storyboard.TargetProperty="propertyName.propertyName2[index].propertyName3" .../>  
```  
  
 Çoğu bağımlılık özellikleri veya <xref:System.Windows.Freezable> türleri bir dizin oluşturucu desteklemez. Bu nedenle, yalnızca bir animasyon yol bir dizin oluşturucu için adlandırılmış hedef zincirini başlatan özellik animasyonlu özellik arasındaki bir ara konumundaki kullanımdır. Sağlanan sözdiziminde olan `propertyName2`. Örneğin, bir dizin oluşturucu kullanımını Ara özelliği bir koleksiyon gibi ise gerekli olabilir <xref:System.Windows.Media.TransformGroup>, bir özellik yolunda gibi `RenderTransform.Children[1].Angle`.  
  
<a name="ppincode"></a>   
## <a name="propertypath-in-code"></a>Kod içinde PropertyPath  
 Kod kullanımı için <xref:System.Windows.PropertyPath>, nasıl oluşturulacağını dahil olmak üzere bir <xref:System.Windows.PropertyPath>, başvuru konusunda belgelenen <xref:System.Windows.PropertyPath>.  
  
 Genel olarak, <xref:System.Windows.PropertyPath> iki farklı Oluşturucular, basit animasyon kullanımları ve bağlama kullanımlar için ve bir karmaşık animasyon kullanımlar için kullanmak üzere tasarlanmıştır. Kullanım <xref:System.Windows.PropertyPath.%23ctor%28System.Object%29> nesne bir dize olduğunda kullanımları, bağlama için imza. Kullanım <xref:System.Windows.PropertyPath.%23ctor%28System.Object%29> nesne olduğunda tek adımlı animasyon yolları için imza bir <xref:System.Windows.DependencyProperty>. Kullanım <xref:System.Windows.PropertyPath.%23ctor%28System.String%2CSystem.Object%5B%5D%29> karmaşık animasyonları için imza. Bu ikinci oluşturucu, ilk parametre ve bir özellik yolu ilişki tanımlamak için belirteç dizesini konumda doldurun nesnelerinin bir dizisi için bir belirteç dizesi kullanır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.PropertyPath>  
 [Veri Bağlamaya Genel Bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Görsel Taslaklara Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
