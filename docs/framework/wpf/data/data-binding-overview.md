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
ms.openlocfilehash: 318473c146f5822259a3131192ce33b9d28a5461
ms.sourcegitcommit: 68eb5c4928e2b082f178a42c16f73fedf52c2ab8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59055358"
---
# <a name="data-binding-overview"></a>Veri Bağlamaya Genel Bakış
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] veri bağlama sunmak ve verilerle etkileşimde bulunmak üzere uygulamalar için basit ve tutarlı bir yol sağlar. Çeşitli veri kaynaklarından biçiminde veriye, öğeler bağlanabilir [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] nesneleri ve [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]. <xref:System.Windows.Controls.ContentControl>s gibi <xref:System.Windows.Controls.Button> ve <xref:System.Windows.Controls.ItemsControl>s gibi <xref:System.Windows.Controls.ListBox> ve <xref:System.Windows.Controls.ListView> esnek tek veri öğelerini stilini veya koleksiyonları etkinleştirmek için yerleşik bir işlevselliğe sahiptir. Sıralama, filtreleme ve Grup görünümleri, veri üzerinde oluşturulabilir.  
  
 Veri bağlama işlevindeki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] geleneksel modeller, çok çeşitli veri bağlama, esnek kendiliğinden destekleyen özellikler dahil olmak üzere çeşitli avantajları vardır [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] verileri ve iş ayrılmasına gösterimi mantığından [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Bu konu öncelikle için temel kavramları açıklar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] veri bağlamayı ve ardından gerçekleştirmeyeceğini kullanımını <xref:System.Windows.Data.Binding> sınıfı ve veri bağlama, diğer özellikler.  
  
  
<a name="what_is_data_binding"></a>   
## <a name="what-is-data-binding"></a>Veri bağlama nedir?  
 Veri bağlama olan uygulama arasında bağlantı kuran işlem [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ve iş mantığı. Veriler, değeri değiştiğinde bağlama doğru ayarları varsa ve verileri uygun bildirimleri sağlar, daha sonra veriye bağlı öğeleri değişiklikleri otomatik olarak yansıtır. Veri bağlama, bir öğe verileri bir dış temsilini değişirse, ardından temel alınan verileri otomatik olarak değişikliği yansıtacak şekilde güncelleştirilmesi anlamına da gelebilir. Örneğin, kullanıcı değeri düzenlerse bir <xref:System.Windows.Controls.TextBox> öğesi, temel alınan veri değeri bu değişikliği yansıtacak şekilde otomatik olarak güncelleştirilir.  
  
 Forms veya diğer sunucu veya yerel yapılandırma verilerini yerleştirmek için tipik bir kullanımı, veri bağlama olan [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kontrol eder. İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bu kavram, çeşitli veri kaynaklarından özelliklerinin geniş bir bağlama eklemek için genişletilir. İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], öğelerin bağımlılık özellikleri bağlanabilir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] nesneleri (dahil olmak üzere [!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] nesneleri veya Web Hizmetleri ve Web özellikleri ile ilişkili nesneleri) ve [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] veri.  
  
 Veri bağlama örneği için aşağıdaki uygulama göz atın [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] gelen [veri bağlama tanıtım](https://go.microsoft.com/fwlink/?LinkID=163703):  
  
 ![Veri bağlama örnek ekran](./media/databinding-databindingdemo.png "DataBinding_DataBindingDemo")  
  
 Yukarıdaki olan [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] eksiltme öğeleri listesini görüntüleyen bir uygulama. Uygulama, veri bağlama, aşağıdaki özellikleri gösterir:  
  
-   İçeriği <xref:System.Windows.Controls.ListBox> koleksiyonuna bağlı *Highlight* nesneleri. Bir *Highlight* nesne olan özellikleri gibi *açıklama*, *StartPrice*, *StartDate*, *kategorisi*, *SpecialFeatures*vb.  
  
-   Verileri (*Highlight* nesneleri) görüntülenen <xref:System.Windows.Controls.ListBox> , şablonlu, böylelikle her öğe için bir açıklama ve geçerli fiyat gösterilir. Bu yapılır kullanarak bir <xref:System.Windows.DataTemplate>. Her bir öğenin görünümünü ayrıca bağlıdır *SpecialFeatures* değerini *Highlight* görüntülenir. Varsa *SpecialFeatures* değerini *Highlight* olduğu *renk*, öğenin mavi bir kenarlık vardır. Değer ise *vurgulayın*, turuncu bir kenarlık ve yıldızı öğesi vardır. [Veri şablonu oluşturmaya](#data_templating) bölüm veri şablonu oluşturma hakkında bilgi sağlar.  
  
-   Kullanıcı grubu, filtre uygulayabilir veya bunu kullanarak verileri sıralama <xref:System.Windows.Controls.CheckBox>sağlanan es. Yukarıdaki resimde, "Grubu kategoriye göre" ve "Kategorisi ve tarihe göre sıralama" <xref:System.Windows.Controls.CheckBox>es seçilir. Veriler ürün kategorisine göre gruplandırılır ve kategori adı alfabetik sırada olduğunu fark etmiş olabilirsiniz. Görüntüyü fark zor olduğunda ancak öğeler de her bir kategorideki başlangıç tarihine göre sıralanır. Bu yapılır kullanarak bir *koleksiyon görünümü*. [Koleksiyonlara bağlama](#binding_to_collections) bölümde koleksiyon görünümlerini ele alınmaktadır.  
  
-   Kullanıcı bir öğe seçtiğinde <xref:System.Windows.Controls.ContentControl> seçili öğe ayrıntılarını görüntüler. Bu adlandırılır *ana öğe-ayrıntı senaryo*. [Ana öğe-ayrıntı senaryo](#master_detail_scenario) bölümü, bu tür bir bağlama senaryosu hakkında bilgi sağlar.  
  
-   Türünü *StartDate* özelliği <xref:System.DateTime>, süresini milisaniye bilgisini içeren bir tarih döndürür. Daha kısa bir tarih dizesi görüntülenir, böylece bu uygulamada özel bir dönüştürücü kullanıldı. [Veri dönüştürme](#data_conversion) bölüm dönüştürücüler hakkında bilgi sağlar.  
  
 Kullanıcı tıkladığında *Ürün Ekle* düğme, aşağıdaki form gelir:  
  
 ![Ürün listesi ekleme sayfası](./media/databinding-demo-addproductlisting.png "DataBinding_Demo_AddProductListing")  
  
 Kullanıcı formunda alanları düzenleyin, kısa ön izleme ve ayrıntılı önizleme bölmelerini kullanarak ürün listesi Önizleme ve ardından *gönderme* yeni ürün listesi eklemek için. Mevcut tüm gruplandırma, filtreleme ve sıralama işlevleri yeni giriş için uygulanır. Bu durumda, yukarıdaki resimde girilen öğesi içinde ikinci öğe olarak görüntülenecektir *bilgisayar* kategorisi.  
  
 Bu görüntüde görünmeyen, sağlanan doğrulama mantığı *başlangıç tarihi* <xref:System.Windows.Controls.TextBox>. Geçersiz kullanıcı girerse tarih (geçersiz biçimlendirme veya son tarihi), kullanıcı ile bildirilir bir <xref:System.Windows.Controls.ToolTip> ve yanında kırmızı bir ünlem <xref:System.Windows.Controls.TextBox>. [Veri doğrulama](#data_validation) bölüm doğrulama mantığını nasıl oluşturulacağını anlatır.  
  
 Veri bağlama yukarıda özetlenen farklı özelliklerinin girmeden önce ilk sonraki bölümde anlamak için kritik olan temel kavramlar ele alınacaktır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] veri bağlama.  
  
## <a name="basic-data-binding-concepts"></a>Temel veri bağlama kavramları  
  
 Öğeye ne olursa olsun, bağlama ve veri kaynağınızın yapısı, her bağlamanın aşağıdaki şekilde gösterilen modelini kullanır:  
  
 ![Temel veri bağlama modelini gösteren diyagram.](./media/data-binding-overview/basic-data-binding-diagram.png)  
  
 Yukarıdaki şekilde gösterildiği gibi veri bağlama temelde, bağlama hedefi ile bağlama kaynağınız arasında köprü ' dir. Aşağıdaki temel şekil gösterir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] veri bağlama Kavramları:  
  
-   Genellikle, her bir bağlaması bu dört bileşene sahiptir: bağlama hedefi nesnesi, bir hedef özelliği, bağlama kaynağı ve bir yol değeri kullanmak için bağlama kaynağı. Örneğin, içeriği bağlamak istiyorsanız bir <xref:System.Windows.Controls.TextBox> için *adı* özelliği bir *çalışan* nesnesi, hedef nesnesi <xref:System.Windows.Controls.TextBox>, hedef özelliği <xref:System.Windows.Controls.TextBox.Text%2A> özelliği, kullanılacak değeri *adı*, kaynak nesnesi *çalışan* nesne.  
  
-   Hedef özelliği, bir bağımlılık özelliği olmalıdır. Çoğu <xref:System.Windows.UIElement> özelliklerdir bağımlılık özellikleri ve salt okunur olanlar dışında birçok bağımlılık özellikleri varsayılan olarak veri bağlamayı destekler. (Yalnızca <xref:System.Windows.DependencyObject> bağımlılık özellikleri ve tüm türleri tanımlayabilirsiniz <xref:System.Windows.UIElement>s türetilen <xref:System.Windows.DependencyObject>.)  
  
-   Aşağıdaki şekilde belirtilmemiş olsa da, özel olarak bağlama kaynak nesnesi sınırlı değildir unutulmamalıdır [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] nesne. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] veri bağlamayı destekleyen veri biçiminde [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] nesneleri ve [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]. Bazı örnekler sağlamak için bağlama kaynağınızı olabilir bir <xref:System.Windows.UIElement>, herhangi bir liste nesnesi bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] ile ilişkili nesne [!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] verileri veya Web Hizmetleri ya da içeren bir XmlNode, [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] veri. Daha fazla bilgi için [bağlama kaynaklarına genel bakış](binding-sources-overview.md).  
  
 Diğer okurken [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)] konular, bağlama kurarken bir bağlama hedefi bağlıyorsanız unutmamak *için* bağlama kaynağı. Örneğin, bazı temel görüntülüyorsanız [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] verilerinde bir <xref:System.Windows.Controls.ListBox> kullanarak veri bağlama, bağlama, <xref:System.Windows.Controls.ListBox> için [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] veri.  
  
 Bir bağlama'kurmak için kullandığınız <xref:System.Windows.Data.Binding> nesne. Bu konunun geri kalanı ile ilgili kavramları birçoğu ve bazı özellikleri ve kullanımını açıklar <xref:System.Windows.Data.Binding> nesne.  
  
<a name="direction_of_data_flow"></a>   
### <a name="direction-of-the-data-flow"></a>Veri akış yönü  
 Daha önce belirtildiği gibi ve ok Yukarıdaki şekilde gösterildiği gibi veri akışını bir bağlama için bağlama kaynağı bağlama hedefi'ndan gidebilirsiniz (örneğin, bir kullanıcı değerini düzenlediğinde kaynak değeri değiştirir. bir <xref:System.Windows.Controls.TextBox>) ve/veya bağlama kaynağı bağlama hedefi için (örneğin, <xref:System.Windows.Controls.TextBox> içerik bağlama kaynağı değişikliklerle güncelleştirilir) bağlama kaynağı uygun bildirimleri sağlıyorsa.  
  
 Kullanıcıların verileri değiştirin ve kaynak nesnesine geri yaymak uygulamanızı isteyebilirsiniz. Veya, kaynak verileri güncelleştirmek kullanıcıları etkinleştirmek istemeyebilir. Bu ayarlayarak kontrol <xref:System.Windows.Data.Binding.Mode%2A> özelliği, <xref:System.Windows.Data.Binding> nesne. Aşağıdaki şekilde, farklı türde veri akışı gösterilmektedir:  
  
 ![Veri bağlama veri akışı](./media/databinding-dataflow.png "DataBinding_DataFlow")  
  
-   <xref:System.Windows.Data.BindingMode.OneWay> bağlama hedef özelliği otomatik olarak güncelleştirmek için kaynak özelliği değişikliklere neden olur, ancak değişiklikler hedef özelliği için kaynak özelliğine geri yayılmaz. Bu tür bir bağlama, bağlı Denetim örtük salt okunur ise uygundur. Örneğin, borsa gibi bir kaynağı bağlayın veya belki de, hedef özelliğini bir tablonun verilere bağlı arka plan rengi gibi değişiklikler yapmak için sağlanan denetim arayüzüne sahip. Hedef özelliği değişiklikler izlemeye gerek yoksa, kullanarak <xref:System.Windows.Data.BindingMode.OneWay> bağlama modu ek yükü ortadan kaldırır <xref:System.Windows.Data.BindingMode.TwoWay> bağlama modu.  
  
-   <xref:System.Windows.Data.BindingMode.TwoWay> bağlama kaynağı özelliği veya diğer otomatik olarak güncelleştirmek için target özelliği değişikliklere neden olur. Bu tür bir bağlama için Düzenlenebilir formlar veya diğer tam etkileşimli uygun [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] senaryoları. Özelliklerin çoğu <xref:System.Windows.Data.BindingMode.OneWay> bağlama, ancak bazı bağımlılık özellikleri (genellikle gibi kullanıcı tarafından düzenlenebilen denetimlerin özelliklerini <xref:System.Windows.Controls.TextBox.Text%2A> özelliği <xref:System.Windows.Controls.TextBox> ve <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> özelliği <xref:System.Windows.Controls.CheckBox>) varsayılan<xref:System.Windows.Data.BindingMode.TwoWay> bağlama. Bağımlılık özelliği tek veya çift yönlü varsayılan olarak olup olmadığını belirlemek için programlı bir yöntem kullanarak özelliğin özellik meta verileri almaktır <xref:System.Windows.DependencyProperty.GetMetadata%2A> ve Boole değerini denetleyin <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A> özelliği.  
  
-   <xref:System.Windows.Data.BindingMode.OneWayToSource> tersidir <xref:System.Windows.Data.BindingMode.OneWay> hedef özelliği değiştiğinde bağlama; bu kaynak özelliğini güncelleştirir. Bir örnek senaryo olduğundan yalnızca kaynak değerini yeniden değerlendirmeniz gerektiğinde [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
-   Aşağıdaki şekilde gösterilen değil olduğundan <xref:System.Windows.Data.BindingMode.OneTime> bağlama, hedef özelliğini başlatmak kaynak özelliği neden olur, ancak sonraki değişiklikler yayılmaz. Bu, bir değişiklik veya veri bağlamı değiştiğinde nesnenin veri bağlamı uğradığında, ardından değişiklik hedef özelliği yansıtılmaz, anlamına gelir. Burada geçerli durumun anlık görüntüsünü kullanmak uygun olan veya verileri gerçek anlamda statik verileri kullanıyorsanız, bu tür bir bağlama uygundur. Bu bağlama türünü de bazı kaynak özelliği değerinden, hedef özelliğiyle başlatmak istiyorsanız ve veri bağlamı önceden bilinmiyor yararlıdır. Bu aslında bir formudur <xref:System.Windows.Data.BindingMode.OneWay> bağlaması, burada kaynak değeri değişmez durumlarda daha iyi performans sağlar.  
  
 Kaynak değişikliklerini algılamak için unutmayın (uygulanabilir <xref:System.Windows.Data.BindingMode.OneWay> ve <xref:System.Windows.Data.BindingMode.TwoWay> bağlamaları), kaynak gibi uygun bir değişiklik bildirimi mekanizması uygulamalıdır <xref:System.ComponentModel.INotifyPropertyChanged>. Bkz: [özellik değişikliği bildirimi uygulama](how-to-implement-property-change-notification.md) örneği için bir <xref:System.ComponentModel.INotifyPropertyChanged> uygulaması.  
  
 <xref:System.Windows.Data.Binding.Mode%2A> Özellik sayfası modları ve bağlama yönünü belirtme ilişkin bir örnek bağlama hakkında daha fazla bilgi sağlar.  
  
<a name="what_triggers_source_updates"></a>   
### <a name="what-triggers-source-updates"></a>Ne Tetikleyicileri kaynağını güncelleştirir  
 Bağlamaları <xref:System.Windows.Data.BindingMode.TwoWay> veya <xref:System.Windows.Data.BindingMode.OneWayToSource> hedef özelliğinde değişiklikleri dinlemek ve bunları kaynağa geri yayar. Bu güncelleştirme kaynağı olarak bilinir. Örneğin, temel alınan kaynak değerinin metin kutusundaki metni düzenleyebilirsiniz. Son bölümde açıklandığı gibi veri akış yönü değeri tarafından belirlenir <xref:System.Windows.Data.Binding.Mode%2A> bağlama özelliği.  
  
 Ancak, kaynak değeri metin düzenlerken veya metin düzenlenmesini tamamlamayı ve farenizi uzağa metin kutusunun üzerine getirin sonra güncelleştirilmiş olur mu? <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> Bağlama özelliğini belirler ne kaynağının güncelleştirmesini tetikler. Rolünü aşağıdaki şekilde sağ okları noktaları gösteren <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> özelliği:  
  
 ![Rol UpdateSourceTrigger özelliğinin gösteren diyagram.](./media/data-binding-overview/data-binding-updatesource-trigger.png)  
  
 Varsa <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> değer <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, ardından değeri işaret edilen tarafından sağ oku <xref:System.Windows.Data.BindingMode.TwoWay> veya <xref:System.Windows.Data.BindingMode.OneWayToSource> bağlamalar hedef özellik değişiklikleri olan en kısa sürede güncelleştirilir. Ancak, varsa <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> değer <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>, hedef özelliği odağı kaybettiğinde bu değer yalnızca yeni değeri ile güncelleştirilir.  
  
 Benzer şekilde <xref:System.Windows.Data.Binding.Mode%2A> özelliği, farklı bağımlılık özellikleri olan farklı varsayılan <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> değerleri. Bağımlılık özelliklerinin çoğu için varsayılan değerdir <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, ancak <xref:System.Windows.Controls.TextBox.Text%2A> özelliği varsayılan değerine sahip <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>. Bu kaynak güncelleştirmeleri genellikle her olması anlamına gelir için hedef özellik değişiklikleri <xref:System.Windows.Controls.CheckBox>es ve diğer basit denetimler. Bununla birlikte, metin alanları için performans ve her tuş vuruşunda kötüleşmesiyle sonra güncelleştirme kullanıcı Geri Al ve yeni değere yapmadan önce yazım hatalarını düzeltmek için fırsatını reddeder. İşte bu <xref:System.Windows.Controls.TextBox.Text%2A> özelliği varsayılan değerine sahip <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> yerine <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.  
  
 Bkz: <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> varsayılan bulma hakkında daha fazla bilgi için özellik sayfası <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> bir bağımlılık özelliğinin değeri.  
  
 Aşağıdaki tabloda her biri için bir örnek senaryosunu sağlayan <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> kullanarak değer <xref:System.Windows.Controls.TextBox> örnek olarak:  
  
|UpdateSourceTrigger değeri|Kaynak değeri güncelleştirildiğinde|Örnek senaryo için metin kutusu|  
|-------------------------------|----------------------------------------|----------------------------------|  
|Deactivate (için varsayılan <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>)|TextBox denetimi odağından zaman|A <xref:System.Windows.Controls.TextBox> Doğrulama mantığı ile ilişkili olan (veri doğrulama bölümüne bakın)|  
|PropertyChanged|Yazdığınız gibi <xref:System.Windows.Controls.TextBox>|<xref:System.Windows.Controls.TextBox> sohbet odası penceresinde denetimleri|  
|açık|Uygulama çağırdığında <xref:System.Windows.Data.BindingExpression.UpdateSource%2A>|<xref:System.Windows.Controls.TextBox> (yalnızca kullanıcı gönder düğmesine tıkladığında kaynak değerlerini güncelleştirir) düzenlenebilir bir formdaki denetimleri|  
  
 Bir örnek için bkz. [TextBox metni kaynağı, güncelleştirmeleri denetlemek](how-to-control-when-the-textbox-text-updates-the-source.md).  
  
<a name="creating_a_binding"></a>   
## <a name="creating-a-binding"></a>Bir bağlama oluşturma  
  
 Bazı önceki bölümlerde ele alınan kavramları özetlemek için kullanarak bir bağlama oluşturun <xref:System.Windows.Data.Binding> nesnesi ve her bağlamanın genellikle dört bileşene sahiptir: hedef, hedef özelliği, bağlama kaynağı ve bir yol kullanmak üzere kaynak değeri bağlama. Bu bölümde bağlamasını ayarlamak nasıl ele alınmaktadır.  
  
 Aşağıdaki örnekte, bağlama kaynak nesnesi adlı bir sınıf olduğunu göz önünde bulundurun *MyData* içinde tanımlanan *MyData* ad alanı. Tanıtım amacıyla *MyData* sınıfında adlı bir dize özelliği *ColorName*, hangi değeri "Kırmızı" kümesi. Bu nedenle, bu örnek, kırmızı bir arka plana sahip bir düğme oluşturur.  
  
 [!code-xaml[BindNonTextProperty#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindNonTextProperty/CS/Page1.xaml#1)]  
  
 Bağlama bildirimi sözdizimi hakkında daha fazla ayrıntı ve kod içinde bağlama ayarlama örnekleri için bkz: [bağlama bildirimlerine genel bakış](binding-declarations-overview.md).  
  
 Biz bu bizim temel diyagramı örneği uygularsanız, sonuçta elde edilen şekilde aşağıdaki gibi görünür. Bu bir <xref:System.Windows.Data.BindingMode.OneWay> arka plan özelliği desteklediğinden bağlama <xref:System.Windows.Data.BindingMode.OneWay> varsayılan bağlama.  
  
 ![Veri bağlama arka plan özelliği gösteren diyagram.](./media/data-binding-overview/data-binding-button-background-example.png)  
  
 Neden olsa bile çalıştığını merak ediyor olabilirsiniz *ColorName* özelliktir sırasında dize türündeki <xref:System.Windows.Controls.Control.Background%2A> özelliği türüdür <xref:System.Windows.Media.Brush>. Bu işte varsayılan tür dönüştürme ve içinde ele alınmıştır [veri dönüştürme](#data_conversion) bölümü.  
  
<a name="specifying_the_binding_source"></a>   
### <a name="specifying-the-binding-source"></a>Bağlama kaynağı belirtme  
 Önceki örnekte, bağlama kaynağı ayarlayarak belirtilen fark <xref:System.Windows.FrameworkElement.DataContext%2A> özelliği <xref:System.Windows.Controls.DockPanel> öğesi. <xref:System.Windows.Controls.Button> Ardından devralan <xref:System.Windows.FrameworkElement.DataContext%2A> değerini <xref:System.Windows.Controls.DockPanel>, üst öğesi olan. Yinelemek için bağlama kaynak nesnesi dört gerekli bileşenleri bağlama biridir. Bu nedenle, belirtilen bağlama kaynak nesnesi bağlama hiçbir şey yapmayabilir.  
  
 Bağlama kaynağı nesnesi belirtmenin birkaç yolu vardır. Kullanarak <xref:System.Windows.FrameworkElement.DataContext%2A> birden çok özellik aynı kaynağına bağlanırken bir üst öğe üzerinde özellik yararlıdır. Ancak, bazı durumlarda da tek bağlama bildirimlerinde bağlama kaynağı belirtme daha uygun olabilir. Önceki örneğin kullanmak yerine, <xref:System.Windows.FrameworkElement.DataContext%2A> özelliği, bağlama kaynağı ayarlayarak belirtebilirsiniz <xref:System.Windows.Data.Binding.Source%2A> doğrudan bağlama bildirimi aşağıdaki örnekte olduğu gibi düğmenin özelliği:  
  
 [!code-xaml[BindNonTextProperty#BackgroundBindingCompact](~/samples/snippets/csharp/VS_Snippets_Wpf/BindNonTextProperty/CS/Page2.xaml#backgroundbindingcompact)]  
  
 Dışında ayarlama <xref:System.Windows.FrameworkElement.DataContext%2A> doğrudan bir öğe üzerinde özellik devralan <xref:System.Windows.FrameworkElement.DataContext%2A> değeri bir üst öğeden (örneğin, ilk örnekte düğme) ve açıkça ayarlayarak bağlama kaynağı belirtme <xref:System.Windows.Data.Binding.Source%2A> özelliği<xref:System.Windows.Data.Binding> de kullanabilirsiniz (düğme gibi son örnek) <xref:System.Windows.Data.Binding.ElementName%2A> özelliği veya <xref:System.Windows.Data.Binding.RelativeSource%2A> bağlama kaynağı belirtme özelliği. <xref:System.Windows.Data.Binding.ElementName%2A> Özelliği, uygulamanızdaki bir düğme genişliğini ayarlamak için bir kaydırıcı kullanırken olduğu gibi diğer öğelere bağlama gerektiğinde kullanışlıdır. <xref:System.Windows.Data.Binding.RelativeSource%2A> Özelliği, bağlama belirtildiğinde yararlıdır bir <xref:System.Windows.Controls.ControlTemplate> veya <xref:System.Windows.Style>. Daha fazla bilgi için [bağlama kaynağı belirtme](how-to-specify-the-binding-source.md).  
  
<a name="specifying_the_path_to_the_value"></a>   
### <a name="specifying-the-path-to-the-value"></a>Değer yolunu belirtme  
 Bağlama kaynağı, bir nesne ise, kullandığınız <xref:System.Windows.Data.Binding.Path%2A> özelliği, bağlama için kullanılacak değeri belirtin. İçin bağlıyorsanız [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] kullandığınız veri <xref:System.Windows.Data.Binding.XPath%2A> özelliği değeri belirtin. Bazı durumlarda kullanmak için geçerli olabilecek <xref:System.Windows.Data.Binding.Path%2A> olsa bile verilerinizi özelliği [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]. Örneğin, ad özelliği (bir XPath sorgusu) sonucunda döndürülen bir XmlNode erişmek istiyorsanız, kullanmanız gerekir <xref:System.Windows.Data.Binding.Path%2A> özelliğine ek olarak <xref:System.Windows.Data.Binding.XPath%2A> özelliği.  
  
 Söz dizimi bilgileri ve örnekler için bkz. <xref:System.Windows.Data.Binding.Path%2A> ve <xref:System.Windows.Data.Binding.XPath%2A> özellik sayfaları.  
  
 Biz bu teknolojilerin unutmayın <xref:System.Windows.Data.Binding.Path%2A> değeri kullanılacak senaryolarda tüm nesneyi bağlamak istediğiniz bir bağlama öğesinin dört gerekli bileşenlerini biridir, kullanılacak değeri bağlama kaynak nesne ile aynı olacaktır. Bu gibi durumlarda belirtmemek için geçerli bir <xref:System.Windows.Data.Binding.Path%2A>. Aşağıdaki örnek göz önünde bulundurun:  
  
 [!code-xaml[MasterDetail#EmptyBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetail/CSharp/Page1.xaml#emptybinding)]  
  
 Yukarıdaki örnek boş bağlama söz dizimini kullanır: {Binding}. Bu durumda, <xref:System.Windows.Controls.ListBox> (Bu örnekte gösterilmiştir değil) bir üst DockPanel öğesini devralır. Yolun belirtilmediğinde, varsayılan tüm nesneyi bağlamaktır. Biz bağlama çünkü başka bir deyişle, bu örnekte, yolun bırakıldı <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliği tüm nesne için. (Bkz [koleksiyonlara bağlama](#binding_to_collections) ilgili ayrıntılı bir tartışma için bölümüne.)  
  
 Yalnızca tek bir özellik bir nesnenin yerine tüm nesneyi bağlamak istediğiniz bir koleksiyona bağlama dışında bu senaryo ayrıca yararlı olur. Yalnızca dize türünde ve, kaynak nesneniz ise, örneğin, dize için bağlamak istediğiniz. Birden fazla özelliğe sahip bir nesne bir öğe bağlamak istediğiniz zaman başka bir yaygın senaryodur.  
  
 Böylece veriler, ilişkili hedef özelliği için anlamlı olan özel mantığı uygulamak gerekebileceğini unutmayın. (Varsayılan tür dönüştürmesi mevcut değilse) özel mantığı özel bir dönüştürücü biçiminde olabilir. Bkz: [veri dönüştürme](#data_conversion) dönüştürücüler hakkında bilgi için.  
  
<a name="binding_bindingexpression"></a>   
### <a name="binding-and-bindingexpression"></a>Bağlama ve BindingExpression  
 Diğer özellikler ve veri bağlama kullanımları almadan önce onu tanıtmak yararlı olabilecek <xref:System.Windows.Data.BindingExpression> sınıfı. Önceki bölümlerde görülen <xref:System.Windows.Data.Binding> ; bağlama bildirimi için üst düzey sınıfı <xref:System.Windows.Data.Binding> sınıfı bir bağlama özelliklerini belirtmenize olanak tanıyan birçok özelliği sağlar. İlgili bir sınıf <xref:System.Windows.Data.BindingExpression>, kaynak ve hedef arasındaki bağlantıyı tutar temel nesnedir. Bir bağlama çeşitli bağlama ifadeleri arasında paylaşılabilecek tüm bilgileri içerir. A <xref:System.Windows.Data.BindingExpression> paylaşılamayan örnek ifade olan ve tüm örnek bilgileri içeren <xref:System.Windows.Data.Binding>.  
  
 Örneğin, aşağıdakileri göz önünde bulundurun burada *myDataObject* örneğidir *MyData* sınıfı *myBinding* kaynağı <xref:System.Windows.Data.Binding> nesne ve *MyData* adlı bir dize özelliği içeren bir tanımlı sınıfı *MyDataProperty*. Bu örnekte metin içeriği bağlar *Metnim*, örneği <xref:System.Windows.Controls.TextBlock>, *MyDataProperty*.  
  
 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 Aynı kullanabileceğiniz *myBinding* diğer bağlamalar oluşturulacak nesne. Örneğin, kullanabilir *myBinding* bağlamak için bir onay kutusunun metin içeriği için nesne *MyDataProperty*. Bu senaryoda olacaktır iki örneğini <xref:System.Windows.Data.BindingExpression> paylaşımı *myBinding* nesne.  
  
 A <xref:System.Windows.Data.BindingExpression> nesnesi arama dönüş değerini elde edilebilir <xref:System.Windows.Data.BindingOperations.GetBindingExpression%2A> bir verilere bağlı nesnede. Aşağıdaki konular bazı kullanımlarını gösterir <xref:System.Windows.Data.BindingExpression> sınıfı:  
  
-   [Bağımlı Hedef Özelliğinden Bağlama Nesnesi Alma](how-to-get-the-binding-object-from-a-bound-target-property.md)  
  
-   [TextBox Metni Kaynağı Güncelleştirdiğinde Denetleme](how-to-control-when-the-textbox-text-updates-the-source.md)  
  
<a name="data_conversion"></a>   
## <a name="data-conversion"></a>Veri Dönüştürme  
 Önceki örnekte düğme kırmızıdır olduğundan, <xref:System.Windows.Controls.Control.Background%2A> özelliği, "Red" değerine sahip bir dize özelliği bağlanır. Bir tür dönüştürücüsü mevcut olduğu için bu çalışır <xref:System.Windows.Media.Brush> türü dize değerine dönüştürmek için bir <xref:System.Windows.Media.Brush>.  
  
 Şekilde, bu bilgiyi eklemek için [bağlama oluşturma](#creating_a_binding) bölümünde diyagramı aşağıdaki gibi görünür:  
  
 ![Veri bağlama varsayılan özelliği gösteren diyagram.](./media/data-binding-overview/data-binding-button-default-conversion.png)  
  
 Ancak, ne tür dizesi, kaynak ensnede bir özelliği olan yerine bir *renk* türünün özelliği <xref:System.Windows.Media.Color>? Bu durumda, sırayla çalışmak bağlama için ilk Aç gerekir *renk* değerlerinizden özellik değeri, <xref:System.Windows.Controls.Control.Background%2A> özelliği kabul eder. Özel bir dönüştürücü uygulayarak oluşturmanız gerekecektir <xref:System.Windows.Data.IValueConverter> arabirimi, aşağıdaki örnekte olduğu gibi:  
  
 [!code-csharp[ColorPicker_snip#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ColorPicker_snip/CSharp/ColorPickerLib/ColorPicker.cs#16)]
 [!code-vb[ColorPicker_snip#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ColorPicker_snip/visualbasic/colorpickerlib/colorpicker.vb#16)]  
  
 <xref:System.Windows.Data.IValueConverter> Başvuru sayfası, daha fazla bilgi sağlar.  
  
 Artık özel dönüştürücü varsayılan dönüştürme yerine kullanılır ve bizim diyagram şöyle görünür:  
  
 ![Veri bağlama özel dönüştürücü gösteren diyagram.](./media/data-binding-overview/data-binding-converter-color-example.png)  
  
 Yinelemek için varsayılan dönüştürmeler bağlanan türünde bulunan tür dönüştürücüleri nedeniyle bulunabilir. Bu davranış, hangi tür dönüştürücüleri hedefte kullanılabilir olduğuna bağlıdır. Bu konuda şüpheleriniz varsa kendi dönüştürücü oluşturun.  
  
 Bir veri dönüştürücüsü uygulamak için yarayacak yerde bazı tipik senaryolar aşağıda verilmiştir:  
  
-   Verilerinizi kültüre bağlı olarak farklı şekilde görüntülenmesi gerekir. Örneğin, bir para birimi dönüştürücü ya da değerlerini veya belirli bir kültürün kullanılan standartları temel alarak bir takvim tarih/saat dönüştürücü uygulamak isteyebilirsiniz.  
  
-   Veri kullanılan mutlaka bir özelliğin metin değerini değiştirmek üzere tasarlanmamıştır, ancak bunun yerine bir görüntü veya rengini veya stilini görüntü metninin kaynağını gibi diğer bazı değerini değiştirmek için tasarlanmıştır. Bu örnekte dönüştürücüler bir metin alanı tablo hücresi arka plan özelliğine bağlama gibi uygun olacak şekilde görülmeyebilir bir özelliğin bağlama dönüştürerek kullanılabilir.  
  
-   Bir denetim veya denetimlerin birden çok özellikleri için daha fazla aynı verilere bağlıdır. Bu durumda, diğer bağlamalar özel bir görüntü sorunları ele ancak aynı bağlama kaynak bilgisi olarak kullanmaya devam edebilirsiniz ancak birincil bağlama metin yalnızca görüntüleyebilir.  
  
-   Şu ana kadar değil henüz ele almıştık <xref:System.Windows.Data.MultiBinding>, burada bir hedef özelliği bağlamaları koleksiyonu vardır. Durumunda, bir <xref:System.Windows.Data.MultiBinding>, özel bir kullandığınız <xref:System.Windows.Data.IMultiValueConverter> bağlamaları değerlerinden son değer üretmek için. Örneğin, aynı veya farklı bir bağlama kaynak nesnelerden değerleri kırmızı, mavi ve yeşil değerlerden renk hesaplanabilir. Bkz: <xref:System.Windows.Data.MultiBinding> sınıfı sayfasına örnekler ve bilgiler.  
  
<a name="binding_to_collections"></a>   
## <a name="binding-to-collections"></a>Koleksiyonlara bağlama  
  
 Bağlama kaynak nesnesi, verileri hangi özellikleri içeren tek bir nesne veya birlikte (örneğin, bir veritabanına bir sorgu sonucunu) çoğunlukla gruplandırılmıştır polimorfik nesneleri veri koleksiyonu olarak işlenebilir. Şu ana kadar yalnızca tek nesneler için bağlamayı ele almıştık, ancak veri koleksiyonu bağlama sık karşılaşılan bir senaryodur. Örneğin, sık karşılaşılan bir senaryodur kullanmaktır bir <xref:System.Windows.Controls.ItemsControl> gibi bir <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.ListView>, veya <xref:System.Windows.Controls.TreeView> uygulamada gösterildiği gibi bir veri koleksiyonunu görüntülemek için [veri bağlama nedir?](#what_is_data_binding) bölümü.  
  
 Neyse ki, bizim temel diyagram hala geçerlidir. Bağlıyorsanız bir <xref:System.Windows.Controls.ItemsControl> bir koleksiyon için diyagram şöyle görünür:  
  
 ![Veri bağlama ItemsControl nesneyi gösteren diyagram.](./media/data-binding-overview/data-binding-itemscontrol.png)  
  
 Bağlamak için bu diyagramda gösterildiği gibi bir <xref:System.Windows.Controls.ItemsControl> bir koleksiyon nesnesine <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> kullanılacak özellik bir özelliktir. Düşünebilirsiniz <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliği içeriği olarak <xref:System.Windows.Controls.ItemsControl>. Bağlama olduğuna dikkat edin <xref:System.Windows.Data.BindingMode.OneWay> çünkü <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliği destekleyen <xref:System.Windows.Data.BindingMode.OneWay> varsayılan bağlama.  
  
<a name="how_to_implement_collections"></a>   
### <a name="how-to-implement-collections"></a>Koleksiyonlar nasıl uygulanır  
 Uygulayan herhangi bir koleksiyonu numaralandırabilirsiniz <xref:System.Collections.IEnumerable> arabirimi. Ancak, dinamik bağlamaları eklemeler ve silmeleri koleksiyondaki güncelleştirecek şekilde ayarlamak için [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] koleksiyonu otomatik olarak, uygulamalıdır <xref:System.Collections.Specialized.INotifyCollectionChanged> arabirimi. Bu arabirim, altta yatan seçki değiştiğinde harekete Geçirilmemesi gereken bir olayı kullanıma sunar.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sağlar <xref:System.Collections.ObjectModel.ObservableCollection%601> kullanıma sunan bir veri toplama yerleşik bir uygulaması sınıfı <xref:System.Collections.Specialized.INotifyCollectionChanged> arabirimi. Tam kaynak nesnelerden aktarma veri değerlerini hedefleri desteklemek için her nesne koleksiyonunuzdaki bağlanabilir özellikler destekler ayrıca gerçekleyebilmeli olduğunu unutmayın <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi. Daha fazla bilgi için [bağlama kaynaklarına genel bakış](binding-sources-overview.md).  
  
 Kendi koleksiyon uygulamadan önce kullanmayı <xref:System.Collections.ObjectModel.ObservableCollection%601> veya gibi bir mevcut koleksiyon sınıfları <xref:System.Collections.Generic.List%601>, <xref:System.Collections.ObjectModel.Collection%601>, ve <xref:System.ComponentModel.BindingList%601>, birçok diğerlerinin yanı sıra. Gelişmiş bir senaryo varsa ve kendi koleksiyon uygulamak istiyorsanız kullanmayı <xref:System.Collections.IList>, ayrı ayrı dizin ve bu nedenle en iyi performansı tarafından erişilebilir nesneleri genel olmayan koleksiyonu sağlar.  
  
<a name="collection_views"></a>   
### <a name="collection-views"></a>Koleksiyon Görünümleri  
 Bir kez, <xref:System.Windows.Controls.ItemsControl> veri toplama için sıralama, filtreleme veya grup verileri isteyebileceğiniz bağlıdır. Bunu yapmak için uygulayan sınıflar olan koleksiyon görünümlerini kullanın. <xref:System.ComponentModel.ICollectionView> arabirimi.  
  
  
#### <a name="what-are-collection-views"></a>Koleksiyon görünümleri nelerdir?  
 Koleksiyon görünümü, üzerine gidin ve temel alınan kaynak koleksiyonu kendisini değiştirmek zorunda kalmadan, sıralama, filtreleme ve Grup sorguları tabanlı kaynak koleksiyonu görüntülemek izin veren bir bağlama kaynak koleksiyonu katmanıdır. Koleksiyon görünümü Ayrıca, koleksiyondaki geçerli öğeye bir işaretçi tutar. Kaynak koleksiyonu uyguluyorsa <xref:System.Collections.Specialized.INotifyCollectionChanged> arabirimi, tarafından gerçekleştirilen değişikliklerin <xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged> olay görünümlerine yayılır.  
  
 Temel alınan kaynak koleksiyonları görünümleri değiştirmeyin, çünkü her bir kaynak koleksiyonu kendisiyle ilişkilendirilmiş birden çok görünüm olabilir. Örneğin, bir koleksiyonunu olabilir *görev* nesneleri. Görünümleri kullanımıyla aynı veriye farklı şekillerde görüntüleyebilirsiniz. Örneğin, sayfanızın sol tarafta, öncelik ve alana göre gruplandırılmış sağ taraftaki sıralanır görevleri göstermek isteyebilirsiniz.  
  
<a name="how_to_create_a_view"></a>   
#### <a name="how-to-create-a-view"></a>Bir görünümü oluşturma  
 Bir görünüm oluşturma ve bir doğrudan view nesnesinin örneğini oluşturma ve bağlama kaynağı kullanmak için yoludur. Örneğin, düşünün [veri bağlama tanıtım](https://go.microsoft.com/fwlink/?LinkID=163703) gösterilen uygulama [veri bağlama nedir?](#what_is_data_binding) bölümü. Uygulama uygulanan şekilde <xref:System.Windows.Controls.ListBox> doğrudan bir görünüme veri koleksiyonu yerine veri koleksiyonu üzerinden bağlanır. Aşağıdaki örnek ayıklanacağı [veri bağlama tanıtım](https://go.microsoft.com/fwlink/?LinkID=163703) uygulama. <xref:System.Windows.Data.CollectionViewSource> Sınıfı [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] devralan bir sınıfın proxy <xref:System.Windows.Data.CollectionView>. Bu örnekte, <xref:System.Windows.Data.CollectionViewSource.Source%2A> görünümünü bağlı *AuctionItems* koleksiyon (türü <xref:System.Collections.ObjectModel.ObservableCollection%601>) geçerli uygulama nesnesi.  
  
 [!code-xaml[DataBindingLab#WindowResources1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#windowresources1)]  
[!code-xaml[DataBindingLab#CollectionViewSource](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#collectionviewsource)]  
[!code-xaml[DataBindingLab#WindowResources2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#windowresources2)]  
  
 Kaynak *listingDataView* uygulama içindeki öğelerin bağlama kaynağı olarak gibi hizmet <xref:System.Windows.Controls.ListBox>:  
  
 [!code-xaml[DataBindingLab#Master1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master1)]  
[!code-xaml[DataBindingLab#Master2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master2)]  
  
 Aynı koleksiyon için başka bir görünüm oluşturmak için başka bir oluşturabilirsiniz <xref:System.Windows.Data.CollectionViewSource> örnek ve farklı bir verin `x:Key` adı.  
  
 Aşağıdaki tabloda gösterilmektedir hangi görünüm veri türlerinin varsayılan koleksiyon görünümü olarak ya da oluşturulan <xref:System.Windows.Data.CollectionViewSource> kaynak koleksiyon türüne göre.  
  
|Kaynak koleksiyon türü|Koleksiyon görünüm türü|Notlar|  
|----------------------------|--------------------------|-----------|  
|<xref:System.Collections.IEnumerable>|Temel bir iç türü <xref:System.Windows.Data.CollectionView>|Öğeleri gruplandıramazsınız.|  
|<xref:System.Collections.IList>|<xref:System.Windows.Data.ListCollectionView>|Fastest.|  
|<xref:System.ComponentModel.IBindingList>|<xref:System.Windows.Data.BindingListCollectionView>||  
  
##### <a name="using-a-default-view"></a>Varsayılan görünüm kullanma  
 Koleksiyon görünümü bağlama kaynağı belirtme oluşturmak ve bir koleksiyon görünümü kullanmak için bir yoludur. WPF bağlama kaynağı olarak kullanılan her koleksiyon için bir varsayılan koleksiyon görünümü de oluşturur. Bir derlemeye doğrudan bağlarsanız, kendi varsayılan görünüme WPF bağlar. Bu varsayılan görünüm aynı koleksiyondaki tüm bağlamalar tarafından ilişkili bir denetim tarafından varsayılan görünüme değişiklik veya kod (örneğin, sıralama veya daha sonra açıklanan geçerli öğe işaretçisi için bir değişiklik) diğer bağlamalarda aynı koleksiyona yansıtılır paylaşıldığını unutmayın.  
  
 Varsayılan görünüm almak için kullandığınız <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> yöntemi. Bir örnek için bkz. [veri koleksiyonunun varsayılan görünümünü alma](how-to-get-the-default-view-of-a-data-collection.md).  
  
##### <a name="collection-views-with-adonet-datatables"></a>ADO.NET veri tablolarını içeren koleksiyon görünümleri  
 Toplama performansı artırmak için ADO.NET için görünümler <xref:System.Data.DataTable> veya <xref:System.Data.DataView> nesneler, sıralama ve filtreleme temsilci <xref:System.Data.DataView>. Bu, sıralama ve filtreleme tüm koleksiyon görünümlerini veri kaynağı arasında paylaşılacak neden olur. Sıralamak ve bağımsız olarak filtrelemek her koleksiyon görünümü etkinleştirmek için her koleksiyon görünümü ile kendi başlatmak <xref:System.Data.DataView> nesne.  
  
#### <a name="sorting"></a>Sıralama  
 Daha önce belirtildiği gibi görünümler, bir koleksiyona bir sıralama düzeni uygulayabilirsiniz. Temel alınan koleksiyonunda var olduğu gibi verileriniz olabilir veya ilgili bir sıraya sahip olmayabilir. Görünümü koleksiyonu üzerinden sipariş dayatır veya sağladığınız karşılaştırma ölçütleri temel alarak varsayılan sırasını değiştirmek sağlar. Verilerin istemci tabanlı bir görünüm olduğundan, bir ortak kullanıcı her sütuna karşılık gelen değeri tablosal veri sütunlarının sıralamak isteyebilirsiniz senaryodur. Görünümleri kullanarak, kullanıcı odaklı Bu sıralama, yeniden temel toplulukta herhangi bir değişiklik yapmadan veya koleksiyon içeriğini requery bile gerek olmadan uygulanabilir. Bir örnek için bkz. [bir GridView Sütun, bir üstbilgi tıklandığında sıralama](../controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).  
  
 Aşağıdaki örnek, "Tür" kategorisi ve tarihe göre sıralama mantığını gösterir <xref:System.Windows.Controls.CheckBox> uygulamanın [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] içinde [veri bağlama nedir?](#what_is_data_binding) bölümü:  
  
 [!code-csharp[DataBindingLab#8](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#8)]
 [!code-vb[DataBindingLab#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#8)]  
  
#### <a name="filtering"></a>Filtreleme  
 Görünümler, bir koleksiyona de filtre uygulayabilirsiniz. Bu koleksiyondaki bir öğe olmasına rağmen bu belirli görünüm yalnızca belirli bir alt kümesi tam koleksiyonu göstermek için hedeflenen anlamına gelir. Bir koşul veri çubuğunda filtreleyebilirsiniz. Örneğin, yapıldığı gibi uygulama tarafından [veri bağlama nedir?](#what_is_data_binding) konusundaki "Yalnızca teklifleri Göster" <xref:System.Windows.Controls.CheckBox> $25 veya daha fazla maliyet öğeleri filtrelemek için mantığı içerir. Ayarlamak için aşağıdaki kodu yürütülür *ShowOnlyBargainsFilter* olarak <xref:System.Windows.Data.CollectionViewSource.Filter> olay işleyicisi olduğunda, <xref:System.Windows.Controls.CheckBox> seçilir:  
  
 [!code-csharp[DataBindingLab#10](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 *ShowOnlyBargainsFilter* olay işleyicisi aşağıdaki uygulama vardır:  
  
 [!code-csharp[DataBindingLab#5](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
 Aşağıdakilerden birini kullanıyorsanız <xref:System.Windows.Data.CollectionView> doğrudan yerine sınıflarından <xref:System.Windows.Data.CollectionViewSource>, kullanacağınız <xref:System.Windows.Data.CollectionView.Filter%2A> özelliği bir geri çağırma belirtmek için. Bir örnek için bkz. [görünümde veri filtreleme](how-to-filter-data-in-a-view.md).  
  
#### <a name="grouping"></a>Gruplandırma  
 Görüntüleyen bir iç sınıf dışında bir <xref:System.Collections.IEnumerable> koleksiyonu tüm koleksiyon görünümlerini destekleyen işlevselliğini gruplandırma, koleksiyon koleksiyon görünümü mantıksal gruplar halinde bölümlere izin verir. Grupları verilere bağlı grupları dinamik olarak oluşturulan kullanıcı grupları listesini sağladığı yerlerde doğrudan veya dolaylı olabilir.  
  
 Aşağıdaki örnek "grubu" kategoriye göre mantığı gösterilmektedir <xref:System.Windows.Controls.CheckBox>:  
  
 [!code-csharp[DataBindingLab#6](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#6)]
 [!code-vb[DataBindingLab#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#6)]  
  
 Başka bir gruplandırma örneği için bkz. [Grup öğeleri ListView olmasını uygular GridView](../controls/how-to-group-items-in-a-listview-that-implements-a-gridview.md).  
  
#### <a name="current-item-pointers"></a>Geçerli öğe işaretçileri  
 Görünümleri, geçerli öğenin kavram da destekler. Koleksiyon görünümü içindeki nesneler aracılığıyla gidebilirsiniz. Gezinirken, bir koleksiyondaki belirli bir yerde var olan bir nesneyi almanızı sağlayan bir öğe işaretçisi taşınıyor. Bir örnek için bkz. [Git aracılığıyla CollectionView içindeki nesneler veri](how-to-navigate-through-the-objects-in-a-data-collectionview.md).  
  
 WPF bir koleksiyona bağlandığından yalnızca (belirttiğiniz bir görünüm veya koleksiyonunun varsayılan görünümünü), bir görünümü kullanarak geçerli bir öğe işaretçisi koleksiyonlara tüm bağlamaları vardır. Bir görünüme bağlanırken, eğik çizgi ("/") karakteri bir `Path` görünümün geçerli öğe değeri atar. Aşağıdaki örnekte, bir koleksiyon görünümü veri bağlamıdır. İlk satırı koleksiyonuna bağlar. İkinci satır, koleksiyondaki geçerli öğesine bağlar. Üçüncü satır bağlar `Description` koleksiyondaki geçerli öğe özelliği.  
  
```xaml  
<Button Content="{Binding }" />  
<Button Content="{Binding Path=/}" />  
<Button Content="{Binding Path=/Description}" />   
```  
  
 Eğik çizgi ve özellik söz dizimi geçiş koleksiyonlarının bir hiyerarşi için yığın olabilir. Aşağıdaki örnekte adlı bir koleksiyon geçerli öğeye bağlanan `Offices`, geçerli öğenin kaynak koleksiyonunun bir özelliği olan.  
  
```xaml  
<Button Content="{Binding /Offices/}" />  
```  
  
 Geçerli öğe işaretçisi, herhangi bir sıralama tarafından etkilenebilir veya filtrelemesi koleksiyonuna uygulanır. Seçilen son öğe geçerli öğe işaretçide sıralama korur, ancak koleksiyon görünümü etrafında artık yapılandırılmıştır. (Belki önce listenin başında seçili öğe olan, ancak artık seçili öğe ortadaki yere olabilir.) Bu seçim görünümünde filtreleme sonrasında kalırsa filtreleme seçili öğe korur. Aksi takdirde, geçerli öğe işaretçisi filtrelenmiş koleksiyon görünümü ilk öğeye ayarlanır.  
  
<a name="master_detail_scenario"></a>   
#### <a name="master-detail-binding-scenario"></a>Ana öğe-ayrıntı bağlama senaryosu  
 Geçerli öğenin kavram, yalnızca bir koleksiyondaki öğelerin gezinme için aynı zamanda ana öğe-ayrıntı bağlama senaryosu için yararlıdır. Uygulamayı göz önünde bulundurun [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] içinde [veri bağlama nedir?](#what_is_data_binding) yeniden bölümü. Bu uygulamada, içinden seçim <xref:System.Windows.Controls.ListBox> gösterilen içeriği belirler <xref:System.Windows.Controls.ContentControl>. Başka bir yolla koymak istediğiniz zaman bir <xref:System.Windows.Controls.ListBox> öğesi seçildiğinde <xref:System.Windows.Controls.ContentControl> seçilen öğenin ayrıntılarını gösterir.  
  
 Aynı görünüme bağlı iki veya daha fazla denetim sağlayarak ana öğe-ayrıntı senaryo uygulayabilirsiniz. Aşağıdaki örnekte [veri bağlama tanıtım](https://go.microsoft.com/fwlink/?LinkID=163703) biçimlerini gösterir <xref:System.Windows.Controls.ListBox> ve <xref:System.Windows.Controls.ContentControl> uygulamasında gördüğünüz [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] içinde [veri bağlama nedir?](#what_is_data_binding) bölümü:  
  
 [!code-xaml[DataBindingLab#Master1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master1)]  
[!code-xaml[DataBindingLab#Master2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master2)]  
[!code-xaml[DataBindingLab#Detail](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#detail)]  
  
 Denetimlerin her ikisi de aynı kaynağa bağlı fark *listingDataView* statik kaynak (Bu kaynak tanımına bakın [görünüm bölümü oluşturulacağını](#how_to_create_a_view)). Bunun çalışmasının nedeni bir singleton nesne ( <xref:System.Windows.Controls.ContentControl> bu durumda) bağlı bir koleksiyon görünümü için otomatik olarak bağlar <xref:System.Windows.Data.CollectionView.CurrentItem%2A> görünümün. Unutmayın <xref:System.Windows.Data.CollectionViewSource> nesneleri otomatik olarak eşitle para birimi ve seçimi. Liste denetiminiz için bağlı değilse bir <xref:System.Windows.Data.CollectionViewSource> ayarlanacak gerekir nesne bu örnekte olduğu gibi kendi <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> özelliğini `true` Bunun çalışması.  
  
 Diğer örnekler için bkz: [bağlama toplama ve görüntüleme bilgileri seçimi temel](how-to-bind-to-a-collection-and-display-information-based-on-selection.md) ve [hiyerarşik veriler ile ana öğe-ayrıntı desenini kullanma](how-to-use-the-master-detail-pattern-with-hierarchical-data.md).  
  
 Yukarıdaki örnekte, şablon kullandığını fark etmiş olabilirsiniz. Aslında, veri şablonları kullanmadan istediğimiz şekilde görüntülenmez (açıkça tarafından kullanılan <xref:System.Windows.Controls.ContentControl> tarafından örtük olarak kullanılan <xref:System.Windows.Controls.ListBox>). Biz artık sonraki bölümde veri şablonu oluşturmaya açın.  
  
<a name="data_templating"></a>   
## <a name="data-templating"></a>Veri şablonu oluşturma  
 Veri şablonları, uygulamamız kullanmadan [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] içinde [veri bağlama nedir?](#what_is_data_binding) bölümü, aşağıdaki gibi görünür:  
  
 ![Veri olmadan veri şablonları Tanıtıma bağlama](./media/data-binding-overview/data-binding-demo-templates.png)  
  
 Önceki bölümdeki örnekte gösterildiği gibi hem <xref:System.Windows.Controls.ListBox> denetimi ve <xref:System.Windows.Controls.ContentControl> tüm koleksiyon nesnesi (veya daha açık belirtmek gerekirse koleksiyon nesnesi üzerinden Görünüm) bağlı *Highlight*s. Veri koleksiyonunun nasıl görüntüleneceği hakkında belirli yönergeler olmadan <xref:System.Windows.Controls.ListBox> temel alınan koleksiyon içindeki her bir nesnenin dize gösterimini görüntüler ve <xref:System.Windows.Controls.ContentControl> bağlı için nesnenin dize gösterimini görüntüler.  
  
 Bu sorunu çözmek için uygulamayı tanımlayan <xref:System.Windows.DataTemplate>s. Önceki bölümdeki örnekte gösterildiği gibi <xref:System.Windows.Controls.ContentControl> açıkça kullanan *detailsProductListingTemplate*<xref:System.Windows.DataTemplate>. <xref:System.Windows.Controls.ListBox> Denetim örtülü olarak kullanan aşağıdaki <xref:System.Windows.DataTemplate> görüntülenirken *Highlight* koleksiyonundaki nesneleri:  
  
 [!code-xaml[DataBindingLab#AuctionItemDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#auctionitemdatatemplate)]  
  
 Bu iki kullanımı ile <xref:System.Windows.DataTemplate>s, sonuçta elde edilen kullanıcı Arabirimi olan gösterilen bir [veri bağlama nedir?](#what_is_data_binding) bölümü. Bu ekran görüntüsünden görebileceğiniz gibi izin vermek yanı sıra veri denetimlerinize yerleştirdiğiniz <xref:System.Windows.DataTemplate>s, verileriniz için ilgi çekici görseller tanımlamak olanak tanır. Örneğin, <xref:System.Windows.DataTrigger>s yukarıdaki kullanılan <xref:System.Windows.DataTemplate> böylece *Highlight*s ile *SpecialFeatures* değerini *vurgulayın* ile görüntülenen bir turuncu bir kenarlık ve bir yıldız.  
  
 Veri şablonları hakkında daha fazla bilgi için bkz. [veri şablonu oluşturmaya genel bakış](data-templating-overview.md).  
  
<a name="data_validation"></a>   
## <a name="data-validation"></a>Veri doğrulama  
  
 Kullanıcı girişi alan çoğu uygulama, kullanıcının beklenen bilgileri girdiğinden emin olmak için doğrulama mantığını sahip olması. Doğrulama denetimleri türü, aralık, biçim veya başka bir uygulamaya özgü gereksinimler temel alabilir. Bu bölümde, içinde veri doğrulama nasıl çalıştığı anlatılmaktadır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="associating-validation-rules-with-a-binding"></a>Doğrulama kuralları bağlama ile ilişkilendirme  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Veri bağlama modelini ilişkilendirmenizi sağlar <xref:System.Windows.Data.Binding.ValidationRules%2A> ile <xref:System.Windows.Data.Binding> nesne. Örneğin, aşağıdaki örnekte bağlayan bir <xref:System.Windows.Controls.TextBox> adlı bir özellik için `StartPrice` ve ekler bir <xref:System.Windows.Controls.ExceptionValidationRule> nesnesini <xref:System.Windows.Data.Binding.ValidationRules%2A?displayProperty=nameWithType> özelliği.  
  
 [!code-xaml[DataBindingLab#DefaultValidation](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#defaultvalidation)]  
  
 A <xref:System.Windows.Controls.ValidationRule> nesnesi bir özelliğinin değerini geçerli olup olmadığını denetler. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Aşağıdaki iki tür yerleşik olan <xref:System.Windows.Controls.ValidationRule> nesneler:  
  
-   A <xref:System.Windows.Controls.ExceptionValidationRule> bağlama kaynak özelliği güncelleştirme sırasında oluşturulan özel durumları denetler. Önceki örnekte, `StartPrice` integer türündedir. Kullanıcı bir tamsayıya dönüştürülüp bir değer girdiğinde, bağlama geçersiz olarak işaretlenmesine neden olan bir özel durum oluşturulur. Ayar için farklı bir sözdizimi <xref:System.Windows.Controls.ExceptionValidationRule> açıkça ayarlamaktır <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> özelliğini `true` üzerinde <xref:System.Windows.Data.Binding> veya <xref:System.Windows.Data.MultiBinding> nesne.  
  
-   A <xref:System.Windows.Controls.DataErrorValidationRule> nesnesi denetler uygulayan nesneler tarafından oluşturulan hatalara <xref:System.ComponentModel.IDataErrorInfo> arabirimi. Bu doğrulama kuralı kullanarak bir örnek için bkz: <xref:System.Windows.Controls.DataErrorValidationRule>. Ayar için farklı bir sözdizimi <xref:System.Windows.Controls.DataErrorValidationRule> açıkça ayarlamaktır <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> özelliğini `true` üzerinde <xref:System.Windows.Data.Binding> veya <xref:System.Windows.Data.MultiBinding> nesne.  
  
 Türetilen kendi doğrulama kuralı oluşturabilirsiniz <xref:System.Windows.Controls.ValidationRule> sınıfı ve uygulama <xref:System.Windows.Controls.ValidationRule.Validate%2A> yöntemi. Aşağıdaki örnek, kural tarafından kullanılan gösterir *ürün listesi ekleme* "StartDate" <xref:System.Windows.Controls.TextBox> gelen [veri bağlama nedir?](#what_is_data_binding) bölümü:  
  
 [!code-csharp[DataBindingLab#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/FutureDateRule.cs#2)]
 [!code-vb[DataBindingLab#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/FutureDateRule.vb#2)]  
  
 *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> bu kullanır *FutureDateRule'u*, aşağıdaki örnekte gösterildiği gibi:  
  
 [!code-xaml[DataBindingLab#CustomValidation](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#customvalidation)]  
  
 Dikkat edin çünkü <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> değer <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, bağlama altyapısı ile kaynak değer de denetler demektir her tuş vuruşunda her kuralda güncelleştirir <xref:System.Windows.Data.Binding.ValidationRules%2A> her tuş vuruşunda koleksiyonu. Bu doğrulama işlemi bölümünde ele alır.  
  
<a name="invalidation_feedback"></a>   
### <a name="providing-visual-feedback"></a>Görsel geri bildirim sağlama  
 Kullanıcı geçersiz bir değer girerse, üzerinde uygulama hata ile ilgili bazı geri bildirim sağlamak isteyebilirsiniz [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Bu tür geri bildirimi sağlamak için tek yönlü <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> iliştirilmiş bir özel özellik <xref:System.Windows.Controls.ControlTemplate>. Önceki alt bölümünde gösterildiği gibi *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> kullanan bir <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> adlı *validationTemplate*. Aşağıdaki örnek tanımı gösterilmektedir *validationTemplate*:  
  
 [!code-xaml[DataBindingLab#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#1)]  
  
 <xref:System.Windows.Controls.AdornedElementPlaceholder> Öğesi donatılan denetimin nereye yerleştirileceğini belirtir.  
  
 Ayrıca, ayrıca kullanabilirsiniz bir <xref:System.Windows.Controls.ToolTip> hata iletisini görüntüleyin. Her iki *StartDateEntryForm* ve *StartPriceEntryForm*<xref:System.Windows.Controls.TextBox>es stili kullanın *textStyleTextBox*, oluşturan bir <xref:System.Windows.Controls.ToolTip> , hata iletisi görüntüler. Aşağıdaki örnek tanımı gösterilmektedir *textStyleTextBox*. Ekli özellik <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> olduğu `true` bir veya daha fazla bağlama öğesinin özelliklerinde bağlama olduğunda hata.  
  
 [!code-xaml[DataBindingLab#14](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#14)]  
  
 Özel ile <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> ve <xref:System.Windows.Controls.ToolTip>, *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> bir doğrulama hatası olduğunda aşağıdaki gibi görünür:  
  
 ![Veri bağlama doğrulama hatası](./media/databindingdemo-validation.PNG "DataBindingDemo_Validation")  
  
 Varsa, <xref:System.Windows.Data.Binding> doğrulama kuralları ile ilişkilendirilmiş ancak belirtmediğiniz bir <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> ilişkili denetimde, varsayılan <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> bir doğrulama hatası olduğunda kullanıcıları bilgilendirmek için kullanılacak. Varsayılan <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> kırmızı bir kenarlık donatıcı katmanındaki tanımlayan bir denetim şablonudur. Varsayılan <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> ve <xref:System.Windows.Controls.ToolTip>, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , *StartPriceEntryForm* <xref:System.Windows.Controls.TextBox> bir doğrulama hatası olduğunda aşağıdaki gibi görünür:  
  
 ![Veri bağlama doğrulama hatası](./media/databindingdemo-validationdefault.PNG "DataBindingDemo_ValidationDefault")  
  
 İletişim kutusundaki tüm denetimlere doğrulamak için mantığı sağlamaya ilişkin bir örnek için özel iletişim kutuları bölümüne bakın. [iletişim kutularına genel bakış](../app-development/dialog-boxes-overview.md).  
  
### <a name="validation-process"></a>Doğrulama işlemi  
 Doğrulama genellikle bir hedef değeri bağlama kaynak özelliğine aktarılırken ortaya çıkar. Bu oluşma <xref:System.Windows.Data.BindingMode.TwoWay> ve <xref:System.Windows.Data.BindingMode.OneWayToSource> bağlar. Yinelemek için hangi kaynak güncelleştirmesine neden değerine bağlıdır <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> açıklandığı gibi özellik [kaynak Tetikleyicileri hangi güncelleştirmelerin](#what_triggers_source_updates) bölümü.  
  
 Aşağıdaki açıklar *doğrulama* işlem. Bu işlem sırasında herhangi bir zamanda bir doğrulama hatası veya diğer türdeki bir hata oluşursa, işlem durdurulur.  
  
1.  Bağlama altyapısı herhangi bir özel olup olmadığını denetler. <xref:System.Windows.Controls.ValidationRule> nesneleri tanımlanan <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ayarlanır <xref:System.Windows.Controls.ValidationStep.RawProposedValue> söz konusu <xref:System.Windows.Data.Binding>, bu durumda çağıran <xref:System.Windows.Controls.ValidationRule.Validate%2A> yöntemi her <xref:System.Windows.Controls.ValidationRule> bunlardan biri bir hata verinceye kadar veya tümünün geçinceye kadar.  
  
2.  Varsa, bağlama altyapısı ardından dönüştürücü çağırır.  
  
3.  Dönüştürücü başarılı olursa, bağlama altyapısı herhangi bir özel olup olmadığını denetler <xref:System.Windows.Controls.ValidationRule> nesneleri tanımlanan <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ayarlanır <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> söz konusu <xref:System.Windows.Data.Binding>, bu durumda çağıran <xref:System.Windows.Controls.ValidationRule.Validate%2A> yöntemi her <xref:System.Windows.Controls.ValidationRule> sahip <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> kümesine <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> bunlardan birinin hatayla çalışana kadar veya tümünün geçinceye kadar.  
  
4.  Bağlama altyapısı kaynak özelliği ayarlar.  
  
5.  Bağlama altyapısı herhangi bir özel olup olmadığını denetler. <xref:System.Windows.Controls.ValidationRule> nesneleri tanımlanan <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ayarlanır <xref:System.Windows.Controls.ValidationStep.UpdatedValue> söz konusu <xref:System.Windows.Data.Binding>, bu durumda çağıran <xref:System.Windows.Controls.ValidationRule.Validate%2A> yöntemi her <xref:System.Windows.Controls.ValidationRule> olan <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ayarlayın <xref:System.Windows.Controls.ValidationStep.UpdatedValue> bunlardan birinin hatayla çalışana kadar veya tümünün geçinceye kadar. Varsa bir <xref:System.Windows.Controls.DataErrorValidationRule> bir bağlamayla ilişkili ve kendi <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> Varsayılana Ayarla <xref:System.Windows.Controls.ValidationStep.UpdatedValue>, <xref:System.Windows.Controls.DataErrorValidationRule> bu noktada denetlenir. Bu nokta Ayrıca, zaman sahip bağlamaları <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> kümesine `true` denetlenir.  
  
6.  Bağlama altyapısı herhangi bir özel olup olmadığını denetler. <xref:System.Windows.Controls.ValidationRule> nesneleri tanımlanan <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ayarlanır <xref:System.Windows.Controls.ValidationStep.CommittedValue> söz konusu <xref:System.Windows.Data.Binding>, bu durumda çağıran <xref:System.Windows.Controls.ValidationRule.Validate%2A> yöntemi her <xref:System.Windows.Controls.ValidationRule> olan <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ayarlayın <xref:System.Windows.Controls.ValidationStep.CommittedValue> bunlardan birinin hatayla çalışana kadar veya tümünün geçinceye kadar.  
  
 Varsa bir <xref:System.Windows.Controls.ValidationRule> geçemezse bağlama altyapısı bu süreci boyunca herhangi bir zamanda oluşturur bir <xref:System.Windows.Controls.ValidationError> ekler ve nesne <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> ilişkili öğe koleksiyonu. Altyapısı bağlama işleminden önce çalışır <xref:System.Windows.Controls.ValidationRule> nesneleri belirli bir adımda herhangi kaldırır <xref:System.Windows.Controls.ValidationError> eklenen <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> Bu adım sırasında ekli özellik ilişkili öğe. Örneğin, bir <xref:System.Windows.Controls.ValidationRule> olan <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ayarlanır <xref:System.Windows.Controls.ValidationStep.UpdatedValue> başarısız oldu, sonraki açışınızda doğrulama işleminin gerçekleşeceği, bağlama altyapısı kaldırır <xref:System.Windows.Controls.ValidationError> hemen önce tüm çağrıları <xref:System.Windows.Controls.ValidationRule> olan <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ayarlayın <xref:System.Windows.Controls.ValidationStep.UpdatedValue>.  
  
 Zaman <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> boş değildir <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği öğenin `true`. Ayrıca, varsa <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A> özelliği <xref:System.Windows.Data.Binding> ayarlanır `true`, bağlama altyapısı oluşturur <xref:System.Windows.Controls.Validation.Error?displayProperty=nameWithType> ekli öğesindeki olay.  
  
 Ayrıca her iki yönde (hedef kaynak veya hedef kaynak) bir geçerli değer aktarımı temizler Not <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> ekli özellik.  
  
 Bağlama ya da varsa bir <xref:System.Windows.Controls.ExceptionValidationRule> ilişkili veya olduğu <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> özelliği `true` ve bir özel durum harekete geçirilir bağlama altyapısı kaynak kümeleri kullanırken, bağlama altyapısı olup olmadığını görmek için denetimleri bir <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>. Kullanılacak seçeneğiniz <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> özel durumları işlemek için özel bir işleyici sağlamak için geri çağırma. Varsa bir <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> üzerinde belirtilmemişse <xref:System.Windows.Data.Binding>, bağlama altyapısı oluşturur bir <xref:System.Windows.Controls.ValidationError> özel durumla ve ekler <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> ilişkili öğe koleksiyonu.  
  
## <a name="debugging-mechanism"></a>Hata ayıklama mekanizması  
 Ekli özellik ayarlayabilirsiniz <xref:System.Diagnostics.PresentationTraceSources.TraceLevel%2A?displayProperty=nameWithType> belirli bir bağlama durumu hakkında bilgi almak için bağlama ile ilgili bir nesne üzerinde.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Controls.DataErrorValidationRule>
- [WPF Sürüm 4.5'te Yenilikler](../getting-started/whats-new.md)
- [LINQ Sorgusunun Sonuçlarına Bağlama](how-to-bind-to-the-results-of-a-linq-query.md)
- [Veri Bağlama](../advanced/optimizing-performance-data-binding.md)
- [Veri bağlama Tanıtımı](https://go.microsoft.com/fwlink/?LinkID=163703)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
- [ADO.NET Veri Kaynağına Bağlama](how-to-bind-to-an-ado-net-data-source.md)
