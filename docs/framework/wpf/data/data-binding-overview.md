---
title: Veri Bağlamaya Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data conversion for binding [WPF]
- binding data [WPF], about data binding
- data binding [WPF], about data binding
- conversion for data binding [WPF]
ms.assetid: c707c95f-7811-401d-956e-2fffd019a211
ms.openlocfilehash: 0b58cde738e2584662fa5f9ad90634931674f48b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558180"
---
# <a name="data-binding-overview"></a>Veri Bağlamaya Genel Bakış
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] veri bağlama sunmak ve veri ile etkileşim kurmak üzere uygulamalar için basit ve tutarlı bir yol sağlar. Çeşitli veri kaynakları biçiminde veriye, öğeler bağlanabilir [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] nesneleri ve [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]. <xref:System.Windows.Controls.ContentControl>s gibi <xref:System.Windows.Controls.Button> ve <xref:System.Windows.Controls.ItemsControl>gibi s <xref:System.Windows.Controls.ListBox> ve <xref:System.Windows.Controls.ListView> tek veri öğelerinin esnek stil veya veri öğeleri koleksiyonlarının etkinleştirmek için yerleşik işlevselliğe sahiptir. Sıralama, filtre ve Grup görünümleri, veriler üzerinde oluşturulabilir.  
  
 Veri bağlama işlevindeki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] geleneksel modeller, çok çeşitli kendiliğinden veri bağlama, esnek destek özellikleri dahil olmak üzere çeşitli avantajları vardır [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] verileri ve iş temiz ayrılması gösterimi mantığından [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Bu konu öncelikle için temel kavramları açıklar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] verileri bağlama ve kullanımını sonra gerçekleştirmeyeceğini <xref:System.Windows.Data.Binding> sınıfı ve diğer veri bağlama özellikleri.  
  
  
<a name="what_is_data_binding"></a>   
## <a name="what-is-data-binding"></a>Veri bağlama nedir?  
 Veri bağlama işlemidir uygulama arasında bir bağlantı kuran [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ve iş mantığı. Veri değeri, değiştiğinde bağlama doğru ayarları varsa ve verileri uygun bildirimleri sağlar, daha sonra veriye bağlı öğeleri değişiklikleri otomatik olarak yansıtır. Veri bağlama, bir öğenin verilerde dış gösterimi değişirse, ardından temel alınan veri otomatik olarak değişikliği yansıtacak şekilde güncelleştirilmesi anlamına da gelebilir. Örneğin, kullanıcı değeri düzenler bir <xref:System.Windows.Controls.TextBox> öğesi, temel alınan veri değeri bu değişikliği yansıtacak şekilde otomatik olarak güncelleştirilir.  
  
 Veri bağlama, tipik kullanımını sunucu veya yerel yapılandırma verilerini forms veya diğer yerleştirmektir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kontrol eder. İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], çok çeşitli özellikler çeşitli veri kaynakları için bağlama eklemek için bu kavram genişletilir. İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], öğelerin bağımlılık özellikleri bağlanabilir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] nesneleri (de dahil olmak üzere [!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] nesneleri veya Web Hizmetleri ve Web özellikleri ile ilişkili nesneler) ve [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] veri.  
  
 Veri bağlama örneği için aşağıdaki uygulama bakalım [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] gelen [veri bağlama gösterisi](http://go.microsoft.com/fwlink/?LinkID=163703):  
  
 ![Veri bağlama örnek ekran görüntüsü](../../../../docs/framework/wpf/data/media/databinding-databindingdemo.png "DataBinding_DataBindingDemo")  
  
 Yukarıdaki olduğu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] uygulamanın açık artırma öğelerinin bir listesini görüntüler. Uygulama veri bağlama, aşağıdaki özellikleri gösterir:  
  
-   İçeriği <xref:System.Windows.Controls.ListBox> bir koleksiyona bağlı *Highlight* nesneleri. Bir *Highlight* nesne olan özellikler gibi *açıklama*, *StartPrice*, *StartDate*, *kategori*, *SpecialFeatures*, vb.  
  
-   Verileri (*Highlight* nesneler) görüntülenen <xref:System.Windows.Controls.ListBox> şablonlu, böylelikle her öğe için bir açıklama ve güncel fiyat gösterilir. Bu yapılır kullanarak bir <xref:System.Windows.DataTemplate>. Her öğenin görünümünü ek olarak, bağımlı *SpecialFeatures* değerini *Highlight* görüntüleniyor. Varsa *SpecialFeatures* değerini *Highlight* olan *renk*, mavi bir kenarlık öğesi içeriyor. Değer ise *vurgulayın*, öğenin turuncu bir kenarlık ve bir yıldız vardır. [Veri şablon](#data_templating) bölüm veri şablonu oluşturma hakkında bilgi sağlar.  
  
-   Kullanıcı grubu, filtre uygulayabilir veya kullanarak verileri sıralamak <xref:System.Windows.Controls.CheckBox>sağlanan es. Yukarıdaki resimde, "Grubu kategoriye göre" ve "Kategori ve tarihe göre sıralama" <xref:System.Windows.Controls.CheckBox>es seçilir. Veriler ürün kategorisi göre gruplandırılır ve kategori adı alfabetik sırada olduğunu fark etmiş olabilirsiniz. Görüntüden fark zordur ancak öğeler de her kategoride başlangıç tarihine göre sıralanır. Bu yapılır kullanarak bir *koleksiyon görünümü*. [Koleksiyonlara bağlama](#binding_to_collections) bölüm koleksiyon görünümlerini anlatır.  
  
-   Kullanıcı bir öğeyi seçtiğinde <xref:System.Windows.Controls.ContentControl> seçili öğenin ayrıntılarını görüntüler. Bu adlı *ana-ayrıntı senaryosu*. [Ana-ayrıntı senaryosu](#master_detail_scenario) bölüm, bu tür bir bağlama senaryosu hakkında bilgi sağlar.  
  
-   Türü *StartDate* özelliği <xref:System.DateTime>, milisaniyeye saati içeren bir tarihi döndürür. Daha kısa bir tarih dizesi görüntülenmesi için bu uygulama, özel bir dönüştürücü kullanıldı. [Veri dönüştürme](#data_conversion) bölüm dönüştürücüler hakkında bilgi sağlar.  
  
 Kullanıcı tıkladığında *Ürün Ekle* düğme, aşağıdaki form gelir:  
  
 ![Ürün listesi ekleme sayfası](../../../../docs/framework/wpf/data/media/databinding-demo-addproductlisting.png "DataBinding_Demo_AddProductListing")  
  
 Kullanıcı form alanları Düzenle, kısa Önizleme ve daha detaylı ön izleme panoları kullanarak ürün listesini Önizleme ve ardından *gönderme* yeni ürün listesini eklemek için. Var olan herhangi gruplandırma, filtreleme ve sıralama işlevleri yeni girişe uygulanır. Bu örnekte, yukarıdaki resimde girilen öğe içinde ikinci öğe olarak görüntülenir *bilgisayar* kategorisi.  
  
 Bu görüntüde görünmeyen, sağlanan doğrulama mantığını *başlangıç tarihi* <xref:System.Windows.Controls.TextBox>. Kullanıcı geçersiz girerse tarih (geçersiz biçimlendirme veya geçmiş bir tarihe), kullanıcı ile bildirilecek bir <xref:System.Windows.Controls.ToolTip> ve yanında kırmızı bir ünlem <xref:System.Windows.Controls.TextBox>. [Veri doğrulama](#data_validation) bölümde doğrulama mantığının nasıl oluşturulacağı açıklanmaktadır.  
  
 Yukarıda özetlenen veri bağlamanın farklı özelliklerine girmeden önce ilk olarak bir sonraki bölümde anlamak için kritik olan temel kavramlar aşağıdakiler ele alınacaktır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] veri bağlama.  
  
## <a name="basic-data-binding-concepts"></a>Temel veri bağlama kavramları  
  
 Hangi öğe bağımsız olarak, bağlama ve veri kaynağınız yapısı, her bağlama daima aşağıdaki şekilde gösterilen modeli izler:  
  
 ![Basit veri bağlama diyagramı](../../../../docs/framework/wpf/data/media/databindingmostbasic.png "DataBindingMostBasic")  
  
 Yukarıdaki şekil tarafından gösterildiği gibi veri bağlama temelde, bağlama hedef ve bağlama kaynağınız arasında köprü gereklidir. Aşağıdaki temel şekilde gösterilmektedir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] veri bağlama Kavramları:  
  
-   Genellikle, her bağlama bu dört bileşene sahiptir: bağlama hedef nesne, bir hedef özellik, bağlama kaynağı ve kullanmak için bağlama kaynağındaki değer için bir yol. Örneğin, içeriği bağlamak istiyorsanız bir <xref:System.Windows.Controls.TextBox> için *adı* özelliği bir *çalışan* nesnesi, hedef nesnesi <xref:System.Windows.Controls.TextBox>, hedef özelliği <xref:System.Windows.Controls.TextBox.Text%2A> kullanılacak değer özelliğidir *adı*, ve kaynak nesnesi *çalışan* nesnesi.  
  
-   Target özelliği, bir bağımlılık özelliği olmalıdır. Çoğu <xref:System.Windows.UIElement> özelliklerdir bağımlılık özellikleri ve salt okunur olanlar dışında çoğu bağımlılık özelliği varsayılan olarak veri bağlamayı destekler. (Yalnızca <xref:System.Windows.DependencyObject> bağımlılık özellikleri ve tüm türleri tanımlayabilirsiniz <xref:System.Windows.UIElement>s türetilen <xref:System.Windows.DependencyObject>.)  
  
-   Şekilde belirtilmedi ancak, özel bir duruma bağlama kaynak nesnesi sınırlı değil unutulmamalıdır [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] nesnesi. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] veri bağlamayı destekleyen veri biçiminde [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] nesneleri ve [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]. Bazı örnekler sağlamak için bağlama kaynağınız olabilir bir <xref:System.Windows.UIElement>, herhangi bir liste nesnesi bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] ile ilişkili nesne [!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] veri veya Web Hizmetleri veya içeren bir XmlNode, [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] veri. Daha fazla bilgi için bkz: [bağlama kaynaklarına genel bakış](../../../../docs/framework/wpf/data/binding-sources-overview.md).  
  
 Diğer salt okunur [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)] konular, bunu bir bağlama kurarken bir bağlama hedef bağlıyorsanız unutmamak *için* bağlama kaynağı. Örneğin, bazı temel görüntülüyorsanız [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] verileri bir <xref:System.Windows.Controls.ListBox> veri bağlama kullanarak, bağlama, <xref:System.Windows.Controls.ListBox> için [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] veri.  
  
 Bir bağlama kurmak için kullandığınız <xref:System.Windows.Data.Binding> nesnesi. Bu konunun geri kalanında ilişkili kavramlardan birçoğunu ve bazı özelliklerin ve kullanımını anlatır <xref:System.Windows.Data.Binding> nesnesi.  
  
<a name="direction_of_data_flow"></a>   
### <a name="direction-of-the-data-flow"></a>Veri akış yönü  
 Daha önce belirtildiği gibi ve oku Yukarıdaki şekilde gösterildiği gibi veri akışı bağlaması bağlama kaynağına bağlama hedef gidebilirsiniz (örneğin, bir kullanıcı değerini düzenlediğinde kaynak değer değiştirir bir <xref:System.Windows.Controls.TextBox>) ve/veya bağlama kaynağından bağlama hedefi (örneğin, <xref:System.Windows.Controls.TextBox> içerik güncelleştirildi bağlama kaynağı değişiklikler) bağlama kaynağı uygun bildirimleri sağlarsa.  
  
 Kullanıcıların verileri değiştirebilir ve kaynak nesneye yayılmasına olanak tanımak için uygulamanızı isteyebilirsiniz. Veya veri kaynağını güncelleştirmek kullanıcıların etkinleştirmek isteyebilirsiniz. Bu ayarlayarak kontrol <xref:System.Windows.Data.Binding.Mode%2A> özelliği, <xref:System.Windows.Data.Binding> nesnesi. Aşağıdaki şekilde, farklı türlerde veri akışını gösterilmektedir:  
  
 ![Veri bağlama veri akışı](../../../../docs/framework/wpf/data/media/databinding-dataflow.png "DataBinding_DataFlow")  
  
-   <xref:System.Windows.Data.BindingMode.OneWay> bağlama hedef özelliğini otomatik olarak güncelleştirmek için kaynak özellikte değişikliklere neden olur, ancak hedef özelliğindeki değişiklikler kaynak özelliğine geri yayılmaz. Bu tür bir bağlama bağlanan denetim dolaylı olarak salt okunur ise uygundur. Örneği için borsa gibi bir kaynağı bağlayın veya belki de hedef özelliği bir tablo veri bağlama arka plan rengini gibi değişiklikler yapmak için sağlanan denetim arayüzüne sahip. Target özelliği değişiklikler izlemeye gerek ise kullanarak <xref:System.Windows.Data.BindingMode.OneWay> bağlama modu önler yükü <xref:System.Windows.Data.BindingMode.TwoWay> bağlama modu.  
  
-   <xref:System.Windows.Data.BindingMode.TwoWay> Bağlama kaynak özelliğin veya diğer otomatik olarak güncelleştirmek için target özelliği değişikliklere neden olur. Bu tür bir bağlama düzenlenebilir formlar veya diğer tamamen etkileşimli için uygun olan [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] senaryoları. Özelliklerin çoğu <xref:System.Windows.Data.BindingMode.OneWay> bağlama, ancak bazı bağımlılık özellikleri (genellikle gibi kullanıcı düzenlenebilir denetimlerin özelliklerini <xref:System.Windows.Controls.TextBox.Text%2A> özelliği <xref:System.Windows.Controls.TextBox> ve <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> özelliği <xref:System.Windows.Controls.CheckBox>) içinvarsayılan<xref:System.Windows.Data.BindingMode.TwoWay> bağlama. Bağımlılık özelliği tek veya çift yönlü varsayılan olarak olup olmadığını belirlemek için programlı bir yolunu kullanarak özelliğin özellik meta verilerini almak için olan <xref:System.Windows.DependencyProperty.GetMetadata%2A> ve Boolean değeri denetleyin <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A> özelliği.  
  
-   <xref:System.Windows.Data.BindingMode.OneWayToSource> tersidir <xref:System.Windows.Data.BindingMode.OneWay> hedef özelliği değiştiğinde bağlama; bu kaynak özelliğini güncelleştirir. Bir örnek senaryo olduğundan yalnızca kaynak değerini yeniden değerlendirmeniz gerektiğinde [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
-   Görüldüğü değil olduğu <xref:System.Windows.Data.BindingMode.OneTime> bağlama, hedef özelliği başlatmak kaynak özelliği neden olur, ancak sonraki değişiklikler yayılmaz. Bu, veri bağlamı bir değişiklik ya da veri bağlam değişiklikleri nesnesinde uğradığında, sonra bu değişiklik hedef özelliğinde yansıtılır değil anlamına gelir. Burada da geçerli durumunun anlık görüntü kullanmak uygun olan ya da verileri gerçekten statik verileri kullanıyorsanız, bu tür bir bağlama uygundur. Bu tür bir bağlama de hedef özelliğinizi kaynak özelliğinden bazı değerle başlatmak ve veri bağlamı önceden bilinmiyor istiyorsanız yararlıdır. Bu temelde daha basit biçimidir <xref:System.Windows.Data.BindingMode.OneWay> bağlaması burada kaynak değer değişmez durumlarda daha iyi performans sağlar.  
  
 Kaynak değişikliklerini algılamak için unutmayın (uygulanabilir <xref:System.Windows.Data.BindingMode.OneWay> ve <xref:System.Windows.Data.BindingMode.TwoWay> bağlamaları), kaynak gibi uygun bir değişiklik bildirim mekanizması uygulamalıdır <xref:System.ComponentModel.INotifyPropertyChanged>. Bkz: [uygulama özellik değişikliği bildirimi](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md) ilişkin bir örnek bir <xref:System.ComponentModel.INotifyPropertyChanged> uygulaması.  
  
 <xref:System.Windows.Data.Binding.Mode%2A> Özellik sayfası modları ve bağlama yönünü belirtmek nasıl bir örnek bağlama hakkında daha fazla bilgi sağlar.  
  
<a name="what_triggers_source_updates"></a>   
### <a name="what-triggers-source-updates"></a>Ne kaynak güncelleştirmelerini tetikler  
 Bağlamaları <xref:System.Windows.Data.BindingMode.TwoWay> veya <xref:System.Windows.Data.BindingMode.OneWayToSource> hedef özelliğindeki değişiklikleri dinler ve bunları kaynağa geri yayar. Bu kaynak güncelleştirmesi olarak bilinir. Örneğin, temel alınan kaynak değerini değiştirmek için metin kutusu metnini düzenleyebilirsiniz. Son bölümde açıklandığı gibi veri akış yönünü değeri tarafından belirlenir <xref:System.Windows.Data.Binding.Mode%2A> bağlama özelliği.  
  
 Ancak, kaynak değeri metin düzenlerken veya TextBox farenizi gelin ve metni düzenlemeyi tamamladıktan sonra güncelleştirilmiş olur mu? <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> Bağlama özelliğini belirler ne kaynağının güncelleştirmesini tetikler. Aşağıdaki şekilde sağ okları nokta rolü göstermek <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> özelliği:  
  
 ![UpdateSourceTrigger diyagramı](../../../../docs/framework/wpf/data/media/databindingupdatesourcetrigger.png "DataBindingUpdateSourceTrigger")  
  
 Varsa <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> değer <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, ardından değeri işaret için tarafından sağ okunu <xref:System.Windows.Data.BindingMode.TwoWay> veya <xref:System.Windows.Data.BindingMode.OneWayToSource> bağlamaları güncelleştirilmiş hedef özellik değişikliklerini olan en kısa sürede. Ancak, varsa <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> değer <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>, hedef özelliği odağı kaybettiğinde bu değer yalnızca yeni değeriyle güncelleştirilir.  
  
 Benzer şekilde <xref:System.Windows.Data.Binding.Mode%2A> özelliği, farklı bağımlılık özelliklere sahip farklı varsayılan <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> değerleri. Çoğu bağımlılık özellikleri için varsayılan değer <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, sırada <xref:System.Windows.Controls.TextBox.Text%2A> özelliğinin varsayılan değeri <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>. Bu kaynak güncelleştirmeler genellikle her olması anlamına gelir için uygundur hedef özelliği değişiklikleri <xref:System.Windows.Controls.CheckBox>es ve diğer basit denetimler. Bununla birlikte, metin alanları için performans ve her tuş vuruşu düşmesine sonra güncelleştirme kullanıcı Al ve yeni değeri uygulamadan önce yazım hataları düzeltmek için fırsatını reddeder. İşte bu nedenle <xref:System.Windows.Controls.TextBox.Text%2A> özelliğinin varsayılan değeri <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> yerine <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.  
  
 Bkz: <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> varsayılan bulma hakkında bilgi için özellik sayfası <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> bir bağımlılık özelliğinin değeri.  
  
 Aşağıdaki tabloda her biri için bir örnek senaryosunu sağlayan <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> kullanarak değer <xref:System.Windows.Controls.TextBox> bir örnek olarak:  
  
|UpdateSourceTrigger değeri|Kaynak değerin güncelleştirildiğinde|TextBox için Örnek senaryo|  
|-------------------------------|----------------------------------------|----------------------------------|  
|Deactivate (için varsayılan <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>)|Ne zaman TextBox denetimi odağı kaybettiğinde|A <xref:System.Windows.Controls.TextBox> Doğrulama mantığı ile ilişkili olan (veri doğrulama bölümüne bakın)|  
|PropertyChanged|Yazdığınız gibi <xref:System.Windows.Controls.TextBox>|<xref:System.Windows.Controls.TextBox> sohbet odası penceresindeki denetimleri|  
|Açık|Uygulama çağırdığında <xref:System.Windows.Data.BindingExpression.UpdateSource%2A>|<xref:System.Windows.Controls.TextBox> (yalnızca kullanıcı gönder düğmesine tıkladığında kaynak değerlerini güncelleştirir) düzenlenebilir bir forma denetimlerinde|  
  
 Bir örnek için bkz: [zaman TextBox metni kaynak güncelleştirmelerini denetlemek](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md).  
  
<a name="creating_a_binding"></a>   
## <a name="creating-a-binding"></a>Bağlama oluşturma  
  
 Bazı önceki bölümlerde açıklanan kavramları özetlemek için kullanarak bir bağlama kurmak <xref:System.Windows.Data.Binding> nesnesi ve her bağlamanın genellikle dört bileşeni vardır: hedef, hedef özelliği, bağlama kaynağı ve bir yol kullanmak üzere kaynak değeri bağlama. Bu bölümde, nasıl bir bağlamanın ayarlanacağı açıklanmaktadır.  
  
 Aşağıdaki örnekte, bağlama kaynak nesnesi adlı bir sınıf olduğunu göz önünde bulundurun *MyData* içinde tanımlanan *SDKSample* ad alanı. Tanıtım amacıyla *MyData* sınıfına sahip adlı bir dize özelliği *ColorName*, hangi değerin "Red" kümesi. Bu nedenle, bu örnek bir düğme kırmızı bir arka plan oluşturur.  
  
 [!code-xaml[BindNonTextProperty#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindNonTextProperty/CS/Page1.xaml#1)]  
  
 Bağlama bildirimi sözdizimi hakkında daha fazla ayrıntı ve nasıl kodda bir bağlamanın ayarlanacağı örnekleri için bkz: [bağlama bildirimleri genel bakış](../../../../docs/framework/wpf/data/binding-declarations-overview.md).  
  
 Biz bu örnek bizim temel diyagrama uygularsanız, sonuçta elde edilen şekilde aşağıdaki gibi görünür. Bu bir <xref:System.Windows.Data.BindingMode.OneWay> arka plan özelliğini desteklediğinden bağlama <xref:System.Windows.Data.BindingMode.OneWay> varsayılan olarak bağlama.  
  
 ![Veri bağlama diyagramı](../../../../docs/framework/wpf/data/media/databindingbuttonbackgroundexample.png "DataBindingButtonBackgroundExample")  
  
 Neden bu rağmen çalıştığını merak ediyor olabilirsiniz *ColorName* özelliktir sırasında dize türünde <xref:System.Windows.Controls.Control.Background%2A> özelliği türüdür <xref:System.Windows.Media.Brush>. Bu varsayılan tür dönüşümü işyerindeki ve içinde ele alınmıştır [veri dönüştürme](#data_conversion) bölümü.  
  
<a name="specifying_the_binding_source"></a>   
### <a name="specifying-the-binding-source"></a>Bağlama kaynağı belirtme  
 Önceki örnekte, bağlama kaynağı ayarlayarak belirtilen fark <xref:System.Windows.FrameworkElement.DataContext%2A> özellikte <xref:System.Windows.Controls.DockPanel> öğesi. <xref:System.Windows.Controls.Button> Sonra devralır <xref:System.Windows.FrameworkElement.DataContext%2A> değeri <xref:System.Windows.Controls.DockPanel>, kendi üst öğesi değil. Yinelemek için bağlama kaynak nesnesi bir bağlama dört gerekli bileşenlerini biridir. Bu nedenle, belirtilen bağlama kaynak nesnesi belirtilmeden bağlama hiçbir şey yapmayabilir.  
  
 Bağlama kaynak nesnesini belirtmenin birkaç yolu vardır. Kullanarak <xref:System.Windows.FrameworkElement.DataContext%2A> bir üst öğesi özelliği, birden çok özellikleri aynı kaynağına bağlanırken yararlıdır. Ancak, bazen onu bağlama kaynağı tek bağlama bildirimleri üzerinde belirtmek daha uygun olabilir. Önceki örneğin kullanmak yerine, <xref:System.Windows.FrameworkElement.DataContext%2A> özelliği, ayarlayarak bağlama kaynağı belirtebilirsiniz <xref:System.Windows.Data.Binding.Source%2A> doğrudan düğmesinin aşağıdaki örnekteki gibi bağlama bildirimi özelliği:  
  
 [!code-xaml[BindNonTextProperty#BackgroundBindingCompact](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindNonTextProperty/CS/Page2.xaml#backgroundbindingcompact)]  
  
 Dışında ayarı <xref:System.Windows.FrameworkElement.DataContext%2A> özelliği, doğrudan bir öğede devralma <xref:System.Windows.FrameworkElement.DataContext%2A> değeri (örneğin, ilk örnekteki düğme) bir üst öğeden ve açıkça bağlama kaynağı ayarlayarak belirterek <xref:System.Windows.Data.Binding.Source%2A> özelliği<xref:System.Windows.Data.Binding> de kullanabilirsiniz (düğme gibi son örnek) <xref:System.Windows.Data.Binding.ElementName%2A> özelliği veya <xref:System.Windows.Data.Binding.RelativeSource%2A> özelliği bağlama kaynağı belirtin. <xref:System.Windows.Data.Binding.ElementName%2A> Özelliği, uygulamanızdaki bir düğme genişliğini ayarlamak için kaydırıcıyı kullanırken olduğu gibi diğer öğelerine bağlama sırasında yararlıdır. <xref:System.Windows.Data.Binding.RelativeSource%2A> Bağlama belirtildiğinde özellik kullanışlı bir <xref:System.Windows.Controls.ControlTemplate> veya <xref:System.Windows.Style>. Daha fazla bilgi için bkz: [bağlama kaynak](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md).  
  
<a name="specifying_the_path_to_the_value"></a>   
### <a name="specifying-the-path-to-the-value"></a>Değer yolunu belirtme  
 Bağlama kaynağınız bir nesne ise, kullandığınız <xref:System.Windows.Data.Binding.Path%2A> özelliği, bağlama için kullanılacak bir değer belirtin. İçin bağlıyorsanız [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] veri, kullandığınız <xref:System.Windows.Data.Binding.XPath%2A> özellik değeri belirtin. Bazı durumlarda kullanmak için geçerli olabilecek <xref:System.Windows.Data.Binding.Path%2A> verilerinizi olduğunda bile özelliği [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]. Örneğin, döndürülen XmlNode (sonucunda bir XPath sorgusu) Name özelliğine erişmek istiyorsanız, kullanmalısınız <xref:System.Windows.Data.Binding.Path%2A> özelliğine ek olarak <xref:System.Windows.Data.Binding.XPath%2A> özelliği.  
  
 Sözdizimi bilgi ve örnekler için bkz: <xref:System.Windows.Data.Binding.Path%2A> ve <xref:System.Windows.Data.Binding.XPath%2A> özellik sayfaları.  
  
 Biz, vurgulanmış rağmen unutmayın <xref:System.Windows.Data.Binding.Path%2A> kullanılacak değer tüm nesneyi bağlamak istediğiniz senaryolarda bir bağlama dört gerekli bileşenlerden biri, kullanılacak değer bağlama kaynak nesnesi ile aynı olur. Bu gibi durumlarda belirtmemek için geçerli bir <xref:System.Windows.Data.Binding.Path%2A>. Aşağıdaki örnek göz önünde bulundurun:  
  
 [!code-xaml[MasterDetail#EmptyBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MasterDetail/CSharp/Page1.xaml#emptybinding)]  
  
 Yukarıdaki örnek boş bağlama söz dizimini kullanır: {bağlama}. Bu durumda, <xref:System.Windows.Controls.ListBox> (Bu örnekte gösterilmez) bir üst DockPanel öğesi devralır. Yolun belirtilmediğinde tüm nesneyi bağlamak için varsayılandır. Biz bağlama çünkü diğer bir deyişle, bu örnekte, yolun bırakıldı <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> nesnenin tamamı için özellik. (Bkz [koleksiyonlara bağlama](#binding_to_collections) ayrıntılı bir tartışma için bölümüne.)  
  
 Nesnenin tamamı yerine yalnızca tek bir özelliği bir nesnenin bağlamak istediğiniz bir koleksiyona bağlama dışında bu senaryo ayrıca yararlıdır. Kaynak nesne türü dizesi ve, yalnızca ise, örneğin, dizeye bağlamak istediğiniz. Başka bir yaygın bir senaryo, çeşitli özelliklere sahip bir nesne bir öğe bağlamak istediğiniz durumdur.  
  
 Veri bağlama hedef özelliğinizi anlamlı olmasını sağlamak özel mantığını uygulamak gerekebileceğini unutmayın. (Varsayılan tür dönüşümü yoksa) özel mantık özel bir dönüştürücü biçiminde olabilir. Bkz: [veri dönüştürme](#data_conversion) dönüştürücüler hakkında bilgi için.  
  
<a name="binding_bindingexpression"></a>   
### <a name="binding-and-bindingexpression"></a>Bağlama ve BindingExpression  
 Diğer özellikler ve veri bağlamanın kullanımları almadan önce onu tanıtmak yararlı olabilecek <xref:System.Windows.Data.BindingExpression> sınıfı. Önceki bölümlerde görülen <xref:System.Windows.Data.Binding> sınıftır üst düzey bir bağlama; bildiriminin <xref:System.Windows.Data.Binding> sınıfı bağlama özelliklerini belirtmenize olanak veren birçok özellik sağlar. İlgili bir sınıf <xref:System.Windows.Data.BindingExpression>, kaynak ve hedef arasındaki bağlantıyı tutar temel nesnedir. Bir bağlama çeşitli bağlama ifadeleri arasında paylaşılan tüm bilgileri içerir. A <xref:System.Windows.Data.BindingExpression> paylaşılamayan bir örnek ifadesidir ve tüm örnek bilgileri içeren <xref:System.Windows.Data.Binding>.  
  
 Örneğin, aşağıdakileri göz önünde bulundurun nerede *myDataObject* örneği *MyData* sınıfı, *myBinding* kaynak <xref:System.Windows.Data.Binding> nesne ve *MyData* sınıftır adlı bir dize özelliği içeren bir tanımlanan *MyDataProperty*. Bu örnek metin içeriği bağlar *mytext*, örneği <xref:System.Windows.Controls.TextBlock>, *MyDataProperty*.  
  
 [!code-csharp[CodeOnlyBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 Aynı kullanabilirsiniz *myBinding* diğer bağlamaları oluşturulacak nesne. Örneğin, kullanabilir *myBinding* bir onay kutusu metin içeriğini bağlamak için nesne *MyDataProperty*. Bu senaryoda olacaktır iki örneğini <xref:System.Windows.Data.BindingExpression> paylaşımı *myBinding* nesnesi.  
  
 A <xref:System.Windows.Data.BindingExpression> nesne çağırmanın dönüş değeri elde edilebilir <xref:System.Windows.Data.BindingOperations.GetBindingExpression%2A> veri bağlama nesnesi üzerinde. Aşağıdaki konular bazı kullanımlarını gösterir <xref:System.Windows.Data.BindingExpression> sınıfı:  
  
-   [Bağımlı Hedef Özelliğinden Bağlama Nesnesi Alma](../../../../docs/framework/wpf/data/how-to-get-the-binding-object-from-a-bound-target-property.md)  
  
-   [TextBox Metni Kaynağı Güncelleştirdiğinde Denetleme](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md)  
  
<a name="data_conversion"></a>   
## <a name="data-conversion"></a>Veri Dönüştürme  
 Önceki örnekte düğme kırmızıdır çünkü kendi <xref:System.Windows.Controls.Control.Background%2A> özelliği, "Red" değerine sahip bir dize özelliği bağlanır. Tür dönüştürücüsünü mevcut olduğundan bu çalışır <xref:System.Windows.Media.Brush> dize değerine dönüştürmek için türü bir <xref:System.Windows.Media.Brush>.  
  
 Bu bilgiler şekilde eklemek için [bağlama oluşturma](#creating_a_binding) bölümünde diyagramı aşağıdaki gibi görünür:  
  
 ![Veri bağlama diyagramı](../../../../docs/framework/wpf/data/media/databindingbuttondefaultconversion.png "DataBindingButtonDefaultConversion")  
  
 Ancak, ne bağlama kaynak nesnesinin dize türünde bir özellik olan yerine bir *renk* türünde özellik <xref:System.Windows.Media.Color>? Bu durumda çalışmaya bağlama için sırayla ilk Aç gerekir *renk* bir şey içine özellik değeri, <xref:System.Windows.Controls.Control.Background%2A> özelliği kabul eder. Özel bir dönüştürücü uygulayarak oluşturmanız gerekecek <xref:System.Windows.Data.IValueConverter> arabirimi, aşağıdaki örnekteki gibi:  
  
 [!code-csharp[ColorPicker_snip#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ColorPicker_snip/CSharp/ColorPickerLib/ColorPicker.cs#16)]
 [!code-vb[ColorPicker_snip#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ColorPicker_snip/visualbasic/colorpickerlib/colorpicker.vb#16)]  
  
 <xref:System.Windows.Data.IValueConverter> Başvuru sayfası daha fazla bilgi sağlar.  
  
 Özel bir dönüştürücü yerine varsayılan dönüştürme şimdi kullanılır ve bizim diyagram şuna benzer:  
  
 ![Veri bağlama diyagramı](../../../../docs/framework/wpf/data/media/databindingconvertercolorexample.png "DataBindingConverterColorExample")  
  
 Yinelemek için varsayılan dönüşümler bağlanan türünde bulunan tür dönüştürücüleri nedeniyle bulunabilir. Bu davranış, hangi tür dönüştürücüleri hedef kullanılabilir olduğuna bağlıdır. Emin değilseniz, kendi dönüştürücü oluşturun.  
  
 Burada bir veri dönüştürücüsü uygulamak için bir anlam bazı tipik senaryolar şunlardır:  
  
-   Verilerinizi kültür bağlı olarak farklı şekilde görüntülenmesi gerekir. Örneğin, bir para birimi dönüştürücüsü veya değerleri veya belirli bir kültür içinde kullanılan standartları temel bir takvim tarih dönüştürücü uygulamak isteyebilirsiniz.  
  
-   Veri kullanılan mutlaka bir özelliğin metin değerini değiştirmek için tasarlanmamıştır, ancak bunun yerine bir görüntü veya rengini veya stilini görüntüleme metni için kaynak gibi diğer bazı değerini değiştirmek için tasarlanmıştır. Bu örnekte dönüştürücüler bir metin alanı tablo hücresi arka plan özelliğine bağlama gibi uygun olacak şekilde görünebilir olmayan bir özelliğin bağlama dönüştürerek kullanılabilir.  
  
-   Büyük bir denetim veya denetimlerin birden çok özellikleri için aynı verilere bağlıdır. Bu durumda, diğer bağlamalar belirli görüntüleme sorunlarını işler ancak aynı bağlama kaynak bilgisi olarak kullanmaya devam ancak birincil bağlama yalnızca metin görüntülenebilir.  
  
-   Şu ana kadar biz henüz açıklanmayan <xref:System.Windows.Data.MultiBinding>, bir hedef özellik bağlama koleksiyonuna sahip olduğu. Durumunda bir <xref:System.Windows.Data.MultiBinding>, özel bir kullandığınız <xref:System.Windows.Data.IMultiValueConverter> bağlamaları değerlerinden son bir değer üretmek için. Örneğin, renk değerleri aynı veya farklı bağlama kaynak nesnelerden olabilir, kırmızı, mavi ve yeşil değerlerinden hesaplanabilir. Bkz: <xref:System.Windows.Data.MultiBinding> sınıfı sayfasına örnekler ve bilgiler.  
  
<a name="binding_to_collections"></a>   
## <a name="binding-to-collections"></a>Koleksiyonlara bağlama  
  
 Bağlama kaynak nesnesi özelliklerin verileri içerdiği tek bir nesne veya veri toplama birlikte (örneğin, bir veritabanı için bir sorgunun sonucu) genellikle gruplandırılmış biçimli nesnelerin olarak işlenebilir. Şu ana kadar biz yalnızca tek nesnelere bağlama ele alınan, ancak, veri toplama bağlama yaygın bir senaryo. Örneğin, yaygın bir senaryo kullanmaktır bir <xref:System.Windows.Controls.ItemsControl> gibi bir <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.ListView>, veya <xref:System.Windows.Controls.TreeView> uygulamada gösterildiği gibi bir veri koleksiyonunu görüntülemek için [veri bağlama nedir?](#what_is_data_binding) bölümü.  
  
 Neyse ki, bizim temel diyagramı hala geçerlidir. Bağlıyorsanız bir <xref:System.Windows.Controls.ItemsControl> bir koleksiyona diyagram şuna benzer:  
  
 ![Veri bağlama ItemsControl diyagramı](../../../../docs/framework/wpf/data/media/databindingitemscontrol.png "DataBindingItemsControl")  
  
 Bağlamak için bu diyagramda gösterildiği gibi bir <xref:System.Windows.Controls.ItemsControl> bir koleksiyon nesnesine <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> kullanılacak özelliği bir özelliktir. Düşünebilirsiniz <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliği içeriği olarak <xref:System.Windows.Controls.ItemsControl>. Bağlama olduğuna dikkat edin <xref:System.Windows.Data.BindingMode.OneWay> çünkü <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliği destekler <xref:System.Windows.Data.BindingMode.OneWay> varsayılan olarak bağlama.  
  
<a name="how_to_implement_collections"></a>   
### <a name="how-to-implement-collections"></a>Koleksiyonlar nasıl uygulanır  
 Uygulayan herhangi bir koleksiyonu listeleme <xref:System.Collections.IEnumerable> arabirimi. Ancak, dinamik bağlamaları eklemeleri ya da silme işlemleri koleksiyondaki güncelleştirecek şekilde ayarlamak için [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] toplama otomatik olarak uygulamalıdır <xref:System.Collections.Specialized.INotifyCollectionChanged> arabirimi. Bu arabirim temel alınan koleksiyon her değiştiğinde oluşturulması gereken olayı sunar.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sağlar <xref:System.Collections.ObjectModel.ObservableCollection%601> sunan veri koleksiyonunun yerleşik bir uygulamasıdır sınıfı <xref:System.Collections.Specialized.INotifyCollectionChanged> arabirimi. Tam veri değerlerini aktarmak kaynak nesnelerden hedefleri desteklemek için her nesne koleksiyonunuzdaki bağlanabilir özellikleri destekler de uygulamanız gerekir Not <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi. Daha fazla bilgi için bkz: [bağlama kaynaklarına genel bakış](../../../../docs/framework/wpf/data/binding-sources-overview.md).  
  
 Kendi koleksiyonunuzu uygulamadan önce kullanmayı <xref:System.Collections.ObjectModel.ObservableCollection%601> veya gibi mevcut koleksiyonu birini sınıfları <xref:System.Collections.Generic.List%601>, <xref:System.Collections.ObjectModel.Collection%601>, ve <xref:System.ComponentModel.BindingList%601>, diğer birçok arasında. Gelişmiş bir senaryo varsa ve kendi koleksiyonunuzu uygulamak isterseniz, kullanmayı <xref:System.Collections.IList>, dizini ve bu nedenle en iyi performansı tarafından erişilebilecek nesnelerin genel olmayan koleksiyonu sağlar.  
  
<a name="collection_views"></a>   
### <a name="collection-views"></a>Koleksiyon görünümleri  
 Bir kez, <xref:System.Windows.Controls.ItemsControl> veri toplama için sıralama, filtre veya grup verileri isteyebilirsiniz bağlıdır. Bunu yapmak için uygulayan sınıflar olan koleksiyon görünümlerini kullanın <xref:System.ComponentModel.ICollectionView> arabirimi.  
  
  
#### <a name="what-are-collection-views"></a>Koleksiyon görünümlerini nelerdir?  
 Bir koleksiyon görünümü gidin ve sıralama, filtre ve Grup sorguları, temel alınan kaynak koleksiyonu kendisi değiştirmek zorunda kalmadan göre kaynak koleksiyonu görüntülemek izin veren bir bağlama kaynak koleksiyonu üstünde bir katmanıdır. Bir koleksiyon görünümü de koleksiyondaki geçerli öğe için bir işaretçi tutar. Kaynak koleksiyonu uyguluyorsa <xref:System.Collections.Specialized.INotifyCollectionChanged> arabirimi tarafından gerçekleştirilen değişikliklerin <xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged> olay görünümlerine yayılır.  
  
 Görünümler temel kaynak koleksiyonlarını değiştirmeyin çünkü her kaynak koleksiyonu kendisiyle ilişkili birden çok görünüm olabilir. Örneğin, bir koleksiyonu olabilir *görev* nesneleri. Görünümlerin kullanımı ile aynı bu verileri farklı şekillerde görüntüleyebilirsiniz. Örneğin, sayfanızın sol tarafta öncelik ve alanına göre gruplandırılmış sağ tarafındaki sıralanır görevleri göster isteyebilirsiniz.  
  
<a name="how_to_create_a_view"></a>   
#### <a name="how-to-create-a-view"></a>Bir görünümü oluşturma  
 Bir görünüm oluşturmak için bir görünüm nesnesini doğrudan başlatmak ve bağlama kaynağı olarak kullanmak için yoludur. Örneğin, göz önünde bulundurun [veri bağlama gösterisi](http://go.microsoft.com/fwlink/?LinkID=163703) gösterilen uygulama [veri bağlama nedir?](#what_is_data_binding) bölümü. Uygulama gerçekleştirilir gibi <xref:System.Windows.Controls.ListBox> doğrudan bir görünüme veri koleksiyonu yerine veri toplama üzerinde bağlar. Aşağıdaki örnek ayıklanan [veri bağlama gösterisi](http://go.microsoft.com/fwlink/?LinkID=163703) uygulama. <xref:System.Windows.Data.CollectionViewSource> Sınıf [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] proxy öğesinden devralınan bir sınıf <xref:System.Windows.Data.CollectionView>. Bu örnekte, <xref:System.Windows.Data.CollectionViewSource.Source%2A> görünümünü bağlı *AuctionItems* koleksiyonu (türünde <xref:System.Collections.ObjectModel.ObservableCollection%601>) geçerli uygulama nesnesi.  
  
 [!code-xaml[DataBindingLab#WindowResources1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#windowresources1)]  
[!code-xaml[DataBindingLab#CollectionViewSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#collectionviewsource)]  
[!code-xaml[DataBindingLab#WindowResources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#windowresources2)]  
  
 Kaynak *listingDataView* uygulama içindeki öğelerin bağlama kaynağı olarak gibi hizmet <xref:System.Windows.Controls.ListBox>:  
  
 [!code-xaml[DataBindingLab#Master1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master1)]  
[!code-xaml[DataBindingLab#Master2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master2)]  
  
 Aynı koleksiyon için başka bir görünüm oluşturmak için başka oluşturabilirsiniz <xref:System.Windows.Data.CollectionViewSource> örneği ve farklı bir vermek `x:Key` adı.  
  
 Aşağıdaki tabloda gösterilmektedir hangi veri türleri görünümünün varsayılan koleksiyon görünümü olarak ya da oluşturulan <xref:System.Windows.Data.CollectionViewSource> kaynak koleksiyon türüne göre.  
  
|Kaynak koleksiyon türü|Koleksiyon görünüm türü|Notlar|  
|----------------------------|--------------------------|-----------|  
|<xref:System.Collections.IEnumerable>|Temel bir iç türü <xref:System.Windows.Data.CollectionView>|Öğeleri gruplandırma yapamazsınız.|  
|<xref:System.Collections.IList>|<xref:System.Windows.Data.ListCollectionView>|Hızlı.|  
|<xref:System.ComponentModel.IBindingList>|<xref:System.Windows.Data.BindingListCollectionView>||  
  
##### <a name="using-a-default-view"></a>Varsayılan görünüm kullanma  
 Bağlama kaynağı olarak bir koleksiyon görünümü belirtme oluşturmak ve bir koleksiyon görünümü kullanmak için bir yoludur. WPF bağlama kaynağı olarak kullanılan her koleksiyon için bir varsayılan koleksiyon görünümü de oluşturur. Doğrudan bir koleksiyona bağlarsanız, WPF kendi varsayılan görünümüne bağlar. Bu varsayılan görünüm tarafından aynı koleksiyondaki tüm bağlamaları ile ilişkili bir denetim için varsayılan görünüm değişiklik ya da aynı koleksiyondaki tüm diğer bağlamaları kod (örneğin, sıralama veya bir değişiklik yapılması daha sonra ele alınan geçerli öğe işaretçisi) yansıtılmıştır paylaşılan olduğunu unutmayın.  
  
 Varsayılan görünümü almak için kullandığınız <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> yöntemi. Bir örnek için bkz: [veri koleksiyonunun varsayılan görünümünü elde](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md).  
  
##### <a name="collection-views-with-adonet-datatables"></a>ADO.NET DataTables ile koleksiyonu görünümleri  
 Toplama performansı artırmak için ADO.NET için görünümleri <xref:System.Data.DataTable> veya <xref:System.Data.DataView> nesneleri temsilci sıralama ve filtreleme <xref:System.Data.DataView>. Bu sıralama ve veri kaynağının tüm koleksiyon görünümleri arasında paylaşılacak filtreleme neden olur. Sıralama ve bağımsız olarak filtrelemek her koleksiyon görünümü etkinleştirmek için her koleksiyon görünümü ile kendi başlatma <xref:System.Data.DataView> nesnesi.  
  
#### <a name="sorting"></a>Sıralama  
 Önceden belirtildiği gibi görünümler bir koleksiyon için bir sıralama düzeni uygulayabilir. Temel koleksiyonda var olduğu gibi verilerinizi olabilir veya ilgili bir sıraya sahip olmayabilir. Koleksiyon üzerinden görünüm sipariş zorunlu tuttukları veya sağladığınız karşılaştırma ölçütü temel alarak varsayılan düzenini değiştirme olanak sağlar. Verilerin istemci tabanlı bir görünümünü olduğundan yaygın bir senaryo kullanıcının her sütuna karşılık gelen değeri verilerinin sütünlarını sıralamak isteyebileceği ' dir. Görünümleri kullanarak, bu kullanıcı tabanlı sıralama, yeniden temel koleksiyona herhangi bir değişiklik yapmadan veya hatta koleksiyon içeriğini requery zorunda kalmadan uygulanabilir. Bir örnek için bkz: [bir GridView Sütun olduğunda bir üstbilgi tıklandığında sıralama](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).  
  
 Aşağıdaki örnek, "Tür" kategoriye ve tarihe göre sıralama mantığını gösterir <xref:System.Windows.Controls.CheckBox> uygulamanın [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] içinde [veri bağlama nedir?](#what_is_data_binding) bölümü:  
  
 [!code-csharp[DataBindingLab#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#8)]
 [!code-vb[DataBindingLab#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#8)]  
  
#### <a name="filtering"></a>Filtreleme  
 Görünümler, ayrıca bir koleksiyon için bir filtre uygulayabilirsiniz. Bu öğe koleksiyonda bulunmasına karşın, bu belirli görünümün yalnızca belirli bir alt kümesi tam koleksiyonu göstermek için hedeflenen anlamına gelir. Veriler durum üzerinde filtreleyebilirsiniz. Örneğin, yapıldığı gibi uygulama tarafından [veri bağlama nedir?](#what_is_data_binding) bölümünde, "Yalnızca teklifleri Göster" <xref:System.Windows.Controls.CheckBox> $25 veya daha fazla maliyeti öğeleri filtrelemek için mantık içerir. Aşağıdaki kod ayarlamak için çalıştırılır *ShowOnlyBargainsFilter* olarak <xref:System.Windows.Data.CollectionViewSource.Filter> olay işleyicisi olduğunda, <xref:System.Windows.Controls.CheckBox> seçilir:  
  
 [!code-csharp[DataBindingLab#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 *ShowOnlyBargainsFilter* olay işleyicisi aşağıdaki uygulama vardır:  
  
 [!code-csharp[DataBindingLab#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
 Aşağıdakilerden birini kullanıyorsanız, <xref:System.Windows.Data.CollectionView> doğrudan yerine sınıflarından <xref:System.Windows.Data.CollectionViewSource>, kullanacağınız <xref:System.Windows.Data.CollectionView.Filter%2A> bir geri çağırma belirtmek için özellik. Bir örnek için bkz: [görünümünde filtre veri](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md).  
  
#### <a name="grouping"></a>Gruplandırma  
 Görünümleri iç sınıf dışında bir <xref:System.Collections.IEnumerable> koleksiyon, tüm koleksiyon görünümleri koleksiyon görünümü mantıksal gruplar halinde koleksiyonunda bölüm kullanıcıya izin veren gruplama işlevini destekler. Grupları grupları dinamik olarak bağlı olarak veri oluşturulan kullanıcı grupları listesini sağladığı yerlerde doğrudan veya dolaylı olabilir.  
  
 Aşağıdaki örnekte "grubu" kategoriye göre mantığı gösterilmektedir <xref:System.Windows.Controls.CheckBox>:  
  
 [!code-csharp[DataBindingLab#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#6)]
 [!code-vb[DataBindingLab#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#6)]  
  
 Başka bir gruplama örneği için bkz: [Grup öğeleri ListView olduğunu uygular GridView](../../../../docs/framework/wpf/controls/how-to-group-items-in-a-listview-that-implements-a-gridview.md).  
  
#### <a name="current-item-pointers"></a>Geçerli öğe işaretçileri  
 Görünümler, geçerli öğenin kavramı da destekler. Bir koleksiyon görünümü içinde nesneler aracılığıyla gidebilirsiniz. Gezinmenizi gibi bir koleksiyondaki belirli bir yerde bulunan nesnenin almanıza olanak tanır bir öğe işaretçisi taşıyor. Bir örnek için bkz: [gidin aracılığıyla nesnelerindeki Veri CollectionView](../../../../docs/framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).  
  
 Bir koleksiyona WPF bağlandığı için yalnızca bir görünüm (belirttiğiniz görünüm veya koleksiyonunun varsayılan görünüm), kullanarak geçerli bir öğe işaretçisi koleksiyonlara tüm bağlamaları vardır. Bir görünüme bağlanırken, eğik çizgi ("/") karakteri bir `Path` değeri görünümün güncel öğesini belirler. Aşağıdaki örnekte, veri bağlamı bir koleksiyon görünümüdür. İlk satır koleksiyona bağlar. İkinci satır koleksiyondaki geçerli öğenin bağlar. Üçüncü satır bağlar `Description` koleksiyondaki geçerli öğesinin özelliği.  
  
```xaml  
<Button Content="{Binding }" />  
<Button Content="{Binding Path=/}" />  
<Button Content="{Binding Path=/Description}" />   
```  
  
 Eğik çizgi ve özellik sözdizimi bir koleksiyon hiyerarşisi çapraz Yığılmış olabilir. Aşağıdaki örnek adlı bir koleksiyon geçerli öğesine bağlar `Offices`, kaynak koleksiyonunun geçerli öğesinin bir özellik değil.  
  
```xaml  
<Button Content="{Binding /Offices/}" />  
```  
  
 Geçerli öğe işaretçisi herhangi bir sıralama tarafından etkilenebilir veya filtrelemesi koleksiyona uygulanır. Geçerli öğe işaretçisi seçilen son öğe üzerinde sıralama korur, ancak koleksiyon görünümü şimdi etrafında yeniden oluşturulamaz. (Belki de önce listenin başında seçili öğe olan, ancak artık seçili öğe ortada herhangi bir yerde olabilir.) Bu seçim görünümünde filtreleme sonrasında kalırsa filtreleme seçili öğe korur. Aksi halde, geçerli öğe işaretçisi filtrelenmiş koleksiyon görünümü ilk öğesine ayarlanır.  
  
<a name="master_detail_scenario"></a>   
#### <a name="master-detail-binding-scenario"></a>Ana-ayrıntı bağlama senaryosu  
 Geçerli öğenin kavramı, yalnızca bir koleksiyondaki öğelerin gezinti için aynı zamanda ana-ayrıntı bağlama senaryosu için kullanışlıdır. Uygulamayı göz önünde bulundurun [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] içinde [veri bağlama nedir?](#what_is_data_binding) yeniden bölüm. Bu uygulamada, içinden seçim <xref:System.Windows.Controls.ListBox> gösterilen içeriği belirler <xref:System.Windows.Controls.ContentControl>. Başka bir yolla koymak istediğiniz zaman bir <xref:System.Windows.Controls.ListBox> öğesi seçildiğinde <xref:System.Windows.Controls.ContentControl> seçili öğenin ayrıntılarını gösterir.  
  
 Ana-ayrıntı senaryosu aynı görünüme bağlı iki veya daha fazla denetim sağlayarak uygulayabilirsiniz. Aşağıdaki örnekte [veri bağlama gösterisi](http://go.microsoft.com/fwlink/?LinkID=163703) biçimlerini gösterir <xref:System.Windows.Controls.ListBox> ve <xref:System.Windows.Controls.ContentControl> uygulaması üzerinde gördüğünüz [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] içinde [veri bağlama nedir?](#what_is_data_binding) bölümü:  
  
 [!code-xaml[DataBindingLab#Master1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master1)]  
[!code-xaml[DataBindingLab#Master2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master2)]  
[!code-xaml[DataBindingLab#Detail](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#detail)]  
  
 Denetimleri her ikisi de aynı kaynağına bağlı olan fark *listingDataView* statik kaynak (Bu kaynak tanımını görmek [görünüm bölümü oluşturmak nasıl](#how_to_create_a_view)). Bu çalışır çünkü bir singleton nesne ( <xref:System.Windows.Controls.ContentControl> bu durumda) bağlı bir koleksiyon görünümü için otomatik olarak bağlandığı <xref:System.Windows.Data.CollectionView.CurrentItem%2A> görünüm. Unutmayın <xref:System.Windows.Data.CollectionViewSource> nesneleri otomatik olarak eşitleme para birimi ve seçim. Liste denetimi için bağlı değilse bir <xref:System.Windows.Data.CollectionViewSource> ayarlamanız gerekir sonra bu örnekte olduğu gibi nesne kendi <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> özelliğine `true` Bunun çalışması.  
  
 Diğer örnekler için bkz: [toplama ve görüntüleme bilgileri seçimi temel bağlamak](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md) ve [hiyerarşik veriler ile ana-ayrıntı desenini kullanma](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md).  
  
 Yukarıdaki örnek şablon kullandığını fark etmiş olabilirsiniz. Aslında, veriler, Şablonları kullanmadan istediğimiz şekilde görüntülenmez (açıkça tarafından kullanılan bir <xref:System.Windows.Controls.ContentControl> ve dolaylı olarak kullanılan bir <xref:System.Windows.Controls.ListBox>). Biz şimdi sonraki bölümdeki veri şablonu oluşturmaya açın.  
  
<a name="data_templating"></a>   
## <a name="data-templating"></a>Veri şablonu oluşturma  
 Veri şablonları, uygulamamız kullanmadan [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] içinde [veri bağlama nedir?](#what_is_data_binding) bölüm uygulamamız şu şekilde görünecektir:  
  
 ![Veri bağlama Demo veri şablonları olmadan](../../../../docs/framework/wpf/data/media/databindingdemotemplates.png "DataBindingDemoTemplates")  
  
 Önceki bölümdeki örnekte gösterildiği gibi hem <xref:System.Windows.Controls.ListBox> denetim ve <xref:System.Windows.Controls.ContentControl> tüm koleksiyon nesnesi (veya daha belirgin olarak görünümüne koleksiyon nesnesi üzerinden) bağlı *Highlight*s. Veri koleksiyonunun nasıl görüntüleneceği hakkında belirli yönergeler olmadan <xref:System.Windows.Controls.ListBox> temel koleksiyonda her nesnenin dize gösterimini görüntüleme ve <xref:System.Windows.Controls.ContentControl> bağlı için nesnenin dize gösterimini görüntüleme.  
  
 Bu sorunu çözmek için uygulamayı tanımlayan <xref:System.Windows.DataTemplate>s. Önceki bölümdeki örnekte gösterildiği gibi <xref:System.Windows.Controls.ContentControl> açıkça kullanır *detailsProductListingTemplate*<xref:System.Windows.DataTemplate>. <xref:System.Windows.Controls.ListBox> Denetim örtük olarak kullanan aşağıdaki <xref:System.Windows.DataTemplate> görüntülenirken *Highlight* koleksiyonundaki nesneleri:  
  
 [!code-xaml[DataBindingLab#AuctionItemDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#auctionitemdatatemplate)]  
  
 Bu iki kullanarak <xref:System.Windows.DataTemplate>, elde edilen UI s'dir gösterildiği bir [veri bağlama nedir?](#what_is_data_binding) bölümü. Bu ekran görüntüsünde gördüğünüz veren yanı sıra veri, denetimlerinde yerleştirdiğiniz <xref:System.Windows.DataTemplate>s verileriniz için ilgi çekici görselleri tanımlamak izin verir. Örneğin, <xref:System.Windows.DataTrigger>s yukarıdaki içinde kullanılan <xref:System.Windows.DataTemplate> böylece *Highlight*s *SpecialFeatures* değerini *vurgulayın* ile görüntülenen bir Turuncu kenarlık ve bir yıldız.  
  
 Veri şablonları hakkında daha fazla bilgi için bkz: [veri şablonu özeti](../../../../docs/framework/wpf/data/data-templating-overview.md).  
  
<a name="data_validation"></a>   
## <a name="data-validation"></a>Veri doğrulama  
  
 Kullanıcı girişi çoğu uygulamalar kullanıcı beklenen bilgiyi girdiğinden emin olmak için doğrulama mantığını olması gerekir. Doğrulama denetimlerini türü, aralık, biçimi veya diğer uygulamaya özgü gereksinimler temel alabilir. Bu bölümde, veri doğrulama işleyişi anlatılmaktadır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="associating-validation-rules-with-a-binding"></a>Doğrulama kuralları bağlama ile ilişkilendirme  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Veri bağlama modelini ilişkilendirmenizi sağlar <xref:System.Windows.Data.Binding.ValidationRules%2A> ile <xref:System.Windows.Data.Binding> nesnesi. Örneğin, aşağıdaki örnekte bağlar bir <xref:System.Windows.Controls.TextBox> adlı bir özellik için `StartPrice` ve ekleyen bir <xref:System.Windows.Controls.ExceptionValidationRule> nesnesinin <xref:System.Windows.Data.Binding.ValidationRules%2A?displayProperty=nameWithType> özelliği.  
  
 [!code-xaml[DataBindingLab#DefaultValidation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#defaultvalidation)]  
  
 A <xref:System.Windows.Controls.ValidationRule> nesnesi bir özellik değerinin geçerli olup olmadığını denetler. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Aşağıdaki iki tür yerleşik olan <xref:System.Windows.Controls.ValidationRule> nesneler:  
  
-   A <xref:System.Windows.Controls.ExceptionValidationRule> bağlama kaynak özelliği güncelleştirme sırasında oluşturulan özel durumları olup olmadığını denetler. Önceki örnekte, `StartPrice` integer türündedir. Kullanıcı bir tamsayıya dönüştürülemiyor bir değer girdiğinde, bağlama geçersiz olarak işaretlenmesine neden olan bir özel durum atılır. Ayar için alternatif bir sözdizimi <xref:System.Windows.Controls.ExceptionValidationRule> açıkça ayarlamaktır <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> özelliğine `true` üzerinde <xref:System.Windows.Data.Binding> veya <xref:System.Windows.Data.MultiBinding> nesnesi.  
  
-   A <xref:System.Windows.Controls.DataErrorValidationRule> nesnesi denetler uygulayan nesneler tarafından oluşturulan hataları <xref:System.ComponentModel.IDataErrorInfo> arabirimi. Bu doğrulama kuralı kullanarak bir örnek için bkz: <xref:System.Windows.Controls.DataErrorValidationRule>. Ayar için alternatif bir sözdizimi <xref:System.Windows.Controls.DataErrorValidationRule> açıkça ayarlamaktır <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> özelliğine `true` üzerinde <xref:System.Windows.Data.Binding> veya <xref:System.Windows.Data.MultiBinding> nesnesi.  
  
 Türetme tarafından kendi doğrulama kuralı da oluşturabilirsiniz <xref:System.Windows.Controls.ValidationRule> sınıfı ve uygulama <xref:System.Windows.Controls.ValidationRule.Validate%2A> yöntemi. Aşağıdaki örnek tarafından kullanılan kuralı gösterir *ürün listesi ekleme* "Başlangıç tarihi" <xref:System.Windows.Controls.TextBox> gelen [veri bağlama nedir?](#what_is_data_binding) bölümü:  
  
 [!code-csharp[DataBindingLab#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/FutureDateRule.cs#2)]
 [!code-vb[DataBindingLab#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/FutureDateRule.vb#2)]  
  
 *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> bu kullanır *FutureDateRule'u*, aşağıdaki örnekte gösterildiği gibi:  
  
 [!code-xaml[DataBindingLab#CustomValidation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#customvalidation)]  
  
 Çünkü unutmayın <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> değer <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, bağlama motoru her kuralı denetlediği anlamına da gelir her basıldığında kaynak değeri güncelleştirmeleri <xref:System.Windows.Data.Binding.ValidationRules%2A> her basıldığında koleksiyonu. Bu, daha fazla doğrulama işlemi bölümde aşağıdakiler ele.  
  
<a name="invalidation_feedback"></a>   
### <a name="providing-visual-feedback"></a>Görsel geri bildirim sağlama  
 Kullanıcı geçersiz bir değer girerse, uygulamanın hata ile ilgili bazı geri bildirim sağlamak isteyebilirsiniz [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Bu tür geri bildirimi sağlamak için tek yönlü <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> iliştirilmiş bir özel özellik <xref:System.Windows.Controls.ControlTemplate>. Önceki alt bölümde gösterildiği gibi *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> kullanan bir <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> adlı *validationTemplate*. Aşağıdaki örnek tanımını gösterir *validationTemplate*:  
  
 [!code-xaml[DataBindingLab#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#1)]  
  
 <xref:System.Windows.Controls.AdornedElementPlaceholder> Öğesi donatılmakta denetim nereye yerleştirileceğini belirler.  
  
 Ayrıca, ayrıca kullanabilirsiniz bir <xref:System.Windows.Controls.ToolTip> hata iletisi görüntülenecek. Her iki *StartDateEntryForm* ve *StartPriceEntryForm*<xref:System.Windows.Controls.TextBox>es kullanın stili *textStyleTextBox*, oluşturan bir <xref:System.Windows.Controls.ToolTip> , hata iletisi görüntüler. Aşağıdaki örnek tanımını gösterir *textStyleTextBox*. Ekli özelliğe <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> olan `true` bir veya daha fazla ilişkili öğenin özelliklerini bağlantılarına olduğunda hata.  
  
 [!code-xaml[DataBindingLab#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#14)]  
  
 Özel ile <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> ve <xref:System.Windows.Controls.ToolTip>, *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> bir doğrulama hatası olduğunda aşağıdaki gibi görünür:  
  
 ![Veri bağlama doğrulama hatası](../../../../docs/framework/wpf/data/media/databindingdemo-validation.PNG "DataBindingDemo_Validation")  
  
 Varsa, <xref:System.Windows.Data.Binding> doğrulama kuralları ilişkili ancak belirtmezseniz bir <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> bağlama denetimi, bir varsayılan üzerinde <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> bir doğrulama hatası olduğunda kullanıcıları bilgilendirmek için kullanılacak. Varsayılan <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> donatıcı katmanındaki kırmızı bir sınır tanımlayan bir denetim şablonudur. Varsayılan <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> ve <xref:System.Windows.Controls.ToolTip>, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , *StartPriceEntryForm* <xref:System.Windows.Controls.TextBox> bir doğrulama hatası olduğunda aşağıdaki gibi görünür:  
  
 ![Veri bağlama doğrulama hatası](../../../../docs/framework/wpf/data/media/databindingdemo-validationdefault.PNG "DataBindingDemo_ValidationDefault")  
  
 Bir iletişim kutusundaki tüm denetimleri doğrulamak için mantığın nasıl bir örnek için özel iletişim kutuları bölümüne bakın [iletişim kutularına genel bakış](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md).  
  
### <a name="validation-process"></a>Doğrulama işlemi  
 Bir hedef değer bağlama kaynak özelliğine aktarıldığında doğrulama genellikle oluşur. Bu meydana gelme <xref:System.Windows.Data.BindingMode.TwoWay> ve <xref:System.Windows.Data.BindingMode.OneWayToSource> bağlar. Yinelemek için hangi kaynak güncelleştirmesine neden değerine bağlıdır <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> açıklandığı gibi özelliği [kaynak güncelleştirmelerini neler tetikler](#what_triggers_source_updates) bölümü.  
  
 Aşağıdaki açıklar *doğrulama* işlemi. Bu işlem sırasında herhangi bir zamanda bir doğrulama hatası veya başka türde bir hata oluşursa, işlem durdurulur.  
  
1.  Bağlama motoru herhangi bir özel olup olmadığını denetler <xref:System.Windows.Controls.ValidationRule> nesnesinin tanımlanmış <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ayarlanır <xref:System.Windows.Controls.ValidationStep.RawProposedValue> söz konusu <xref:System.Windows.Data.Binding>, bu durumda çağırır <xref:System.Windows.Controls.ValidationRule.Validate%2A> yöntemi her <xref:System.Windows.Controls.ValidationRule> bunlardan birini bir hata verinceye kadar veya bunların tümünün geçinceye kadar.  
  
2.  Varsa, bağlama altyapısı sonra dönüştürücü çağırır.  
  
3.  Dönüştürücü başarılı olursa, bağlama motoru herhangi bir özel olup olmadığını denetler <xref:System.Windows.Controls.ValidationRule> nesnesinin tanımlanmış <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ayarlanır <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> söz konusu <xref:System.Windows.Data.Binding>, bu durumda çağırır <xref:System.Windows.Controls.ValidationRule.Validate%2A> yöntemi her <xref:System.Windows.Controls.ValidationRule> sahip <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> kümesine <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> bunlardan birini bir hata verinceye kadar veya bunların tümünün geçinceye kadar.  
  
4.  Bağlama motoru kaynak özelliğini ayarlar.  
  
5.  Bağlama motoru herhangi bir özel olup olmadığını denetler <xref:System.Windows.Controls.ValidationRule> nesnesinin tanımlanmış <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ayarlanır <xref:System.Windows.Controls.ValidationStep.UpdatedValue> söz konusu <xref:System.Windows.Data.Binding>, bu durumda çağırır <xref:System.Windows.Controls.ValidationRule.Validate%2A> yöntemi her <xref:System.Windows.Controls.ValidationRule> olan <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ayarlayın <xref:System.Windows.Controls.ValidationStep.UpdatedValue> bunlardan birini bir hata verinceye kadar veya bunların tümünün geçinceye kadar. Varsa bir <xref:System.Windows.Controls.DataErrorValidationRule> bağlama ile ilişkili ve bunun <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> default olarak ayarlanırsa <xref:System.Windows.Controls.ValidationStep.UpdatedValue>, <xref:System.Windows.Controls.DataErrorValidationRule> bu noktada denetlenir. Bu ayrıca noktasıdır zaman sahip bağlamaları <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> kümesine `true` denetlenir.  
  
6.  Bağlama motoru herhangi bir özel olup olmadığını denetler <xref:System.Windows.Controls.ValidationRule> nesnesinin tanımlanmış <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ayarlanır <xref:System.Windows.Controls.ValidationStep.CommittedValue> söz konusu <xref:System.Windows.Data.Binding>, bu durumda çağırır <xref:System.Windows.Controls.ValidationRule.Validate%2A> yöntemi her <xref:System.Windows.Controls.ValidationRule> olan <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ayarlayın <xref:System.Windows.Controls.ValidationStep.CommittedValue> bunlardan birini bir hata verinceye kadar veya bunların tümünün geçinceye kadar.  
  
 Varsa bir <xref:System.Windows.Controls.ValidationRule> geçemezse bağlama altyapısı bu işlemi boyunca herhangi bir zamanda oluşturur bir <xref:System.Windows.Controls.ValidationError> nesne ve ona ekler <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> ilişkili öğe koleksiyonu. Altyapısı bağlama işleminden önce çalışır <xref:System.Windows.Controls.ValidationRule> nesneleri herhangi verilen aşamada herhangi kaldırır <xref:System.Windows.Controls.ValidationError> eklenen <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> bağımlı öğesi özelliği bu adım sırasında bağlı. Örneğin, varsa bir <xref:System.Windows.Controls.ValidationRule> , <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ayarlanır <xref:System.Windows.Controls.ValidationStep.UpdatedValue> başarısız oldu, doğrulama işlemi, bağlama altyapısı kaldırır sonraki oluştuğunda <xref:System.Windows.Controls.ValidationError> önce herhangi çağırır hemen <xref:System.Windows.Controls.ValidationRule> olan <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ayarlayın <xref:System.Windows.Controls.ValidationStep.UpdatedValue>.  
  
 Zaman <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> boş değil <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> öğesinin ekli özelliği ayarlanmış `true`. Ayrıca, varsa <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A> özelliği <xref:System.Windows.Data.Binding> ayarlanır `true`, bağlama motoru oluşturur <xref:System.Windows.Controls.Validation.Error?displayProperty=nameWithType> ekli öğesindeki olayı.  
  
 Ayrıca her iki yönde (hedef kaynak veya hedef kaynak için) geçerli değer aktarımı temizler Not <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> özelliği eklenmiş.  
  
 Bağlama ya da varsa bir <xref:System.Windows.Controls.ExceptionValidationRule> ilişkili veya olduğu <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> özelliği ayarlanmış `true` ve bir özel durum oluşur bağlama motoru kaynak ayarladığında, bağlama altyapısı olup olmadığını görmek için denetler bir <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>. Kullanılacak seçeneğiniz <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> özel durumları işlemek için özel işleyici sağlamak için geri çağırma. Varsa bir <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> üzerinde belirtilmemişse <xref:System.Windows.Data.Binding>, bağlama motoru oluşturur bir <xref:System.Windows.Controls.ValidationError> özel ve ona ekler <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> ilişkili öğe koleksiyonu.  
  
## <a name="debugging-mechanism"></a>Hata ayıklama mekanizması  
 Ekli özelliğe ayarlayabilirsiniz <xref:System.Diagnostics.PresentationTraceSources.TraceLevel%2A?displayProperty=nameWithType> belirli bir bağlamanın durumu hakkında bilgi almak için bir bağlama ile ilgili nesne üzerinde.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.DataErrorValidationRule>  
 [WPF Sürüm 4.5'teki Yenilikler](../../../../docs/framework/wpf/getting-started/whats-new.md)  
 [LINQ Sorgusunun Sonuçlarına Bağlama](../../../../docs/framework/wpf/data/how-to-bind-to-the-results-of-a-linq-query.md)  
 [Veri Bağlama](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Veri bağlama Tanıtımı](http://go.microsoft.com/fwlink/?LinkID=163703)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)  
 [ADO.NET Veri Kaynağına Bağlama](../../../../docs/framework/wpf/data/how-to-bind-to-an-ado-net-data-source.md)
