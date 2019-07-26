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
ms.openlocfilehash: e1fbb46c76fbc729818b6ff24b55c0d18f6b05df
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400705"
---
# <a name="data-binding-overview"></a>Veri Bağlamaya Genel Bakış
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]veri bağlama, uygulamaların sunmak ve verilerle etkileşim kurmak için basit ve tutarlı bir yol sağlar. Öğeler, ortak dil çalışma zamanı (CLR) nesneleri ve [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]içindeki çeşitli veri kaynaklarından verilere bağlanabilir. <xref:System.Windows.Controls.ContentControl>ve gibi gibi, <xref:System.Windows.Controls.ItemsControl> <xref:System.Windows.Controls.ListBox>tekveri öğelerinin veya veri öğelerinin koleksiyonlarının esnek stillendirilmesini sağlayan yerleşik işlevlere sahiptir.<xref:System.Windows.Controls.ListView> <xref:System.Windows.Controls.Button> Sıralama, filtre ve grup görünümleri verilerin üzerine oluşturulabilir.  
  
 ' Deki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] veri bağlama işlevselliği, veri bağlamayı, verilerin esnek [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] sunumunu ve iş ayırmayı temizleme gibi çok çeşitli özellikler de dahil olmak üzere geleneksel modellere göre birçok avantaj sağlar [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]mantığı.  
  
 Bu konu, <xref:System.Windows.Data.Binding> ilk olarak veri bağlama [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] için temel kavramları açıklar ve sonra sınıfının kullanımına ve veri bağlamanın diğer özelliklerine gider.  

<a name="what_is_data_binding"></a>   
## <a name="what-is-data-binding"></a>Veri bağlama nedir?  
 Veri bağlama, uygulama [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ve iş mantığı arasında bağlantı kuran bir işlemdir. Bağlamanın doğru ayarları varsa ve veriler doğru bildirimleri sağlıyorsa, veriler değeri değiştirdiğinde, verilere bağlanan öğeler otomatik olarak değişiklikleri yansıtır. Veri bağlama Ayrıca bir öğedeki verilerin bir dış gösterimi değişirse, temel alınan verilerin değişikliği yansıtacak şekilde otomatik olarak güncelleştirilmesini sağlayabilir. Örneğin, Kullanıcı bir <xref:System.Windows.Controls.TextBox> öğesindeki değeri düzenlerse, temel alınan veri değeri bu değişikliği yansıtacak şekilde otomatik olarak güncelleştirilir.  
  
 Veri bağlamanın tipik bir kullanımı, sunucu veya yerel yapılandırma verilerini formlara veya diğer [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] denetimlere yerleştirkullanmaktır. ' [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]De, bu kavram çeşitli veri kaynaklarına çok sayıda özelliklerin bağlamasını kapsayacak şekilde genişletilir. ' [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]De, öğelerin bağımlılık özellikleri, clr nesnelerine (ADO.NET nesneleri veya Web Hizmetleri ve Web özellikleriyle ilişkili nesneler dahil) ve [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] verilerle bağlanabilir.  
  
 Veri bağlama tanıtımına ilişkin bir örnek için, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] [veri bağlama tanıtımında](https://go.microsoft.com/fwlink/?LinkID=163703)aşağıdaki uygulamaya göz atın:  
  
 ![Veri bağlama örnek ekran görüntüsü](./media/databinding-databindingdemo.png "DataBinding_DataBindingDemo")  
  
 Yukarıdaki [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , bir açık eksiltme öğelerinin listesini görüntüleyen bir uygulamadır. Uygulama, veri bağlamanın aşağıdaki özelliklerini gösterir:  
  
- Öğesinin <xref:System.Windows.Controls.ListBox> içeriği bir *AuctionItem* nesneleri koleksiyonuna bağımlıdır. Bir *AuctionItem* nesnesi *Description*, *StartPrice*, *StartDate*, *category*, *SpecialFeatures*vb. gibi özelliklere sahiptir.  
  
- İçinde görüntülenen veriler (*AuctionItem* nesneleri), <xref:System.Windows.Controls.ListBox> her öğe için açıklama ve geçerli fiyatın gösterilmesi için şablonlanır. Bu, kullanılarak <xref:System.Windows.DataTemplate>yapılır. Ayrıca, her öğenin görünümü görüntülenmekte olan *AuctionItem* öğesinin *SpecialFeatures* değerine bağlıdır. *AuctionItem* öğesinin *SpecialFeatures* değeri *Color*ise, öğenin mavi kenarlığı vardır. Değer *Vurgulayıcıdır*, öğenin turuncu kenarlığı ve yıldızı vardır. [Veri şablonu](#data_templating) oluşturma bölümü, veri şablonu oluşturma hakkında bilgi sağlar.  
  
- Kullanıcı, verileri belirtilen <xref:System.Windows.Controls.CheckBox>es kullanarak gruplandırabilir, süzebilir veya sıralayabilir. Yukarıdaki görüntüde, "kategoriye göre gruplandırma" ve "kategoriye ve tarihe göre sıralama" <xref:System.Windows.Controls.CheckBox>seçilidir. Verilerin ürün kategorisine göre gruplandığını fark etmiş olabilirsiniz ve kategori adı alfabetik sırada olur. Görüntüden bildirimde bulunulmaları zordur, ancak öğeler her kategori içindeki başlangıç tarihine göre sıralanır. Bu, bir *koleksiyon görünümü*kullanılarak yapılır. [Koleksiyonlara bağlama](#binding_to_collections) bölümü koleksiyon görünümlerini tartışır.  
  
- Kullanıcı bir öğe <xref:System.Windows.Controls.ContentControl> seçtiğinde, seçili öğenin ayrıntılarını görüntüler. Buna *Master-Detail senaryosu*denir. [Ana ayrıntı senaryosu](#master_detail_scenario) bölümü, bu tür bağlama senaryosu hakkında bilgi sağlar.  
  
- *StartDate* özelliğinin <xref:System.DateTime>türü, milisaniye cinsinden saati içeren bir tarih döndürür. Bu uygulamada, daha kısa bir tarih dizesinin görüntülenmesi için özel bir dönüştürücü kullanılmıştır. [Veri dönüştürme](#data_conversion) bölümünde dönüştürücüler hakkında bilgi sağlanır.  
  
 Kullanıcı *Ürün Ekle* düğmesine tıkladığında aşağıdaki form gelir:  
  
 ![Ürün listeleme sayfası ekle](./media/databinding-demo-addproductlisting.png "DataBinding_Demo_AddProductListing")  
  
 Kullanıcı formdaki alanları düzenleyebilir, kısa önizlemeyi ve daha ayrıntılı önizleme bölmelerini kullanarak ürün listesini önizleyebilir ve ardından yeni ürün listesini eklemek için *Gönder* ' e tıklayın. Mevcut gruplandırma, filtreleme ve sıralama işlevleri, yeni giriş için geçerli olacaktır. Bu durumda, yukarıdaki görüntüde girilen öğe, *bilgisayar* kategorisi içinde ikinci öğe olarak görüntülenir.  
  
 Bu görüntüde gösterilmez, *başlangıç tarihinde* <xref:System.Windows.Controls.TextBox>verilen doğrulama mantığıdır. Kullanıcı geçersiz bir tarih (geçersiz biçimlendirme veya geçmiş tarih) girerse, kullanıcıya öğesinin yanında <xref:System.Windows.Controls.ToolTip> <xref:System.Windows.Controls.TextBox>bir ve kırmızı bir ünlem işaretiyle bildirim gönderilir. [Veri doğrulama](#data_validation) bölümü, doğrulama mantığının nasıl oluşturulacağını açıklar.  
  
 Yukarıda özetlenen veri bağlamasının farklı özelliklerine geçmeden önce, ilk olarak veri bağlamayı anlamak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] için kritik olan temel kavramların bir sonraki bölümünde tartışacağız.  
  
## <a name="basic-data-binding-concepts"></a>Temel veri bağlama kavramları  
  
 Bağladığınız öğeden ve veri kaynağınızın doğası ne olursa olsun, her bağlama her zaman aşağıdaki şekilde gösterilen modeli izler:  
  
 ![Temel veri bağlama modelini gösteren diyagram.](./media/data-binding-overview/basic-data-binding-diagram.png)  
  
 Yukarıdaki şekilde gösterildiği gibi, veri bağlama aslında bağlama hedefi ve bağlama kaynağınız arasındaki köprüdir. Şekil aşağıdaki temel [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] veri bağlama kavramlarını göstermektedir:  
  
- Genellikle, her bağlamada şu dört bileşen vardır: bağlama hedef nesnesi, hedef özellik, bağlama kaynağı ve kullanılacak bağlama kaynağındaki değerin yolu. Örneğin, bir öğesinin <xref:System.Windows.Controls.TextBox> içeriğini bir *çalışan* nesnesinin <xref:System.Windows.Controls.TextBox> *Name* özelliğine bağlamak istiyorsanız, hedef nesneniz, hedef özelliği <xref:System.Windows.Controls.TextBox.Text%2A> ise, kullanılacak değer, *adı*ve Kaynak nesne, *çalışan* nesnesidir.  
  
- Target özelliği bir Dependency özelliği olmalıdır. Çoğu <xref:System.Windows.UIElement> Özellik bağımlılık özellikleridir ve salt okuma özellikleri hariç, varsayılan olarak veri bağlamayı destekler. (Yalnızca <xref:System.Windows.DependencyObject> türler bağımlılık özelliklerini tanımlayabilir ve tüm <xref:System.Windows.UIElement>s 'ler öğesinden <xref:System.Windows.DependencyObject>türetilir.)  
  
- Şekilde belirtilmese de, bağlama kaynak nesnesinin özel bir CLR nesnesi olmasına sınırlı olmadığından not edilmelidir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]veri bağlama, verileri CLR nesneleri biçiminde destekler ve [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]. Bazı örnekler sağlamak için bağlama kaynağınız bir, herhangi bir <xref:System.Windows.UIElement>liste nesnesi, ADO.NET veri veya Web hizmetleriyle ilişkili bir CLR nesnesi ya da [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] verilerinizi içeren bir XmlNode olabilir. Daha fazla bilgi için bkz. [bağlama kaynaklarına genel bakış](binding-sources-overview.md).  
  
 Diğer [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)] konuları okuduğunuzdan, bir bağlama oluştururken *bağlama hedefini bir* bağlama kaynağına bağladığınızda dikkat etmeniz önemlidir. Örneğin [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] , bir <xref:System.Windows.Controls.ListBox> veri bağlama kullanarak bazı temel verileri görüntülüyorsanız <xref:System.Windows.Controls.ListBox> , verilerinizi bu verilere bağladıysanız [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] .  
  
 Bir bağlama oluşturmak için <xref:System.Windows.Data.Binding> nesnesini kullanın. Bu konunun geri kalanında, ile ilişkili kavramların birçoğu ve <xref:System.Windows.Data.Binding> nesnenin bazı özellikleri ve kullanımları ele alınmaktadır.  
  
<a name="direction_of_data_flow"></a>   
### <a name="direction-of-the-data-flow"></a>Veri akışının yönü  
 Daha önce ve Yukarıdaki şekildeki ok tarafından belirtildiği gibi, bir bağlamanın veri akışı bağlama kaynağından bağlama kaynağına gidebilir (örneğin, bir Kullanıcı bir <xref:System.Windows.Controls.TextBox>' ın değerini düzenlediğinde kaynak değeri değişir) ve/veya bağlama kaynağından bağlama kaynağına doğru bildirimleri sağlıyorsa bağlama hedefi için ( <xref:System.Windows.Controls.TextBox> Örneğin, içeriğiniz bağlama kaynağındaki değişikliklerle güncellenir).  
  
 Uygulamanızın kullanıcıların verileri değiştirmesini ve kaynak nesnesine geri yaymasını etkinleştirmesini isteyebilirsiniz. Ya da kullanıcıların kaynak verileri güncelleştirmesini etkinleştirmek istemeyebilirsiniz. <xref:System.Windows.Data.Binding.Mode%2A> Nesnenizin özelliğini<xref:System.Windows.Data.Binding> ayarlayarak bunu kontrol edebilirsiniz. Aşağıdaki şekilde farklı türde veri akışı gösterilmektedir:  
  
 ![Veri bağlama veri akışı](./media/databinding-dataflow.png "DataBinding_DataFlow")  
  
- <xref:System.Windows.Data.BindingMode.OneWay>bağlama, hedef özelliği otomatik olarak güncelleştirmek için kaynak özellikte değişikliklere neden olur, ancak Target özelliğindeki değişiklikler kaynak özelliğine geri yayılmaz. Bu tür bir bağlama, bağlanmakta olan denetimin örtülü olarak salt okunurdur. Örneğin, bir stok şeridi gibi bir kaynağa bağlanabilir ya da hedef özellikte, bir tablonun veri bağlantılı arka plan rengi gibi değişiklikler yapmak için hiçbir denetim arabirimi sağlanmamıştır. Hedef özelliğin değişikliklerini izlemeye gerek yoksa <xref:System.Windows.Data.BindingMode.OneWay> bağlama modunun kullanılması <xref:System.Windows.Data.BindingMode.TwoWay> bağlama modunun ek yükünü önler.  
  
- <xref:System.Windows.Data.BindingMode.TwoWay>bağlama, kaynak özellikte veya Target özelliğinde, diğerini otomatik olarak güncelleştirmek için değişikliklere neden olur. Bu tür bir bağlama, düzenlenebilir formlar veya diğer tam etkileşimli [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] senaryolar için uygundur. <xref:System.Windows.Data.BindingMode.OneWay> Çoğu özellik varsayılan olarak bağlamaya, ancak bazı bağımlılık özelliklerine (genellikle <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.TextBox.Text%2A> özelliği ve <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> özelliği <xref:System.Windows.Controls.CheckBox>gibi kullanıcı tarafından düzenlenebilir denetimlerin özellikleri) varsayılan olarak <xref:System.Windows.Data.BindingMode.TwoWay> bağlama. Bağımlılık özelliğinin tek yönlü veya iki yönlü olarak bağlama özelliğinin, kullanarak <xref:System.Windows.DependencyProperty.GetMetadata%2A> özelliğin özellik meta verilerini almak ve sonra <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A> özelliğin Boole değerini denetlemesi için programlı bir yoldur.  
  
- <xref:System.Windows.Data.BindingMode.OneWayToSource>, <xref:System.Windows.Data.BindingMode.OneWay> bağlamanın tersidir; Target özelliği değiştiğinde kaynak özelliğini güncelleştirir. Tek örnek senaryo, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]yalnızca kaynağından kaynak değeri yeniden değerlendirmeniz gerektiğinde olur.  
  
- Şekil, kaynak özelliğin hedef özelliği <xref:System.Windows.Data.BindingMode.OneTime> başlatmasına neden olan Binding bağlamadır, ancak sonraki değişiklikler yayılmaz. Bu, veri bağlamı bir değişikliğe geçtiğinde veya veri bağlamındaki nesne değiştiğinde, değişikliğin hedef özellikte yansıtılmadığını gösterir. Geçerli durumunun bir anlık görüntüsünün kullanım için uygun olduğu veya verilerin gerçekten statik olduğu durumlarda veri kullanıyorsanız, bu tür bir bağlama uygundur. Hedef özelliği bir kaynak özelliğinden bir değer ile başlatmak istiyorsanız ve veri bağlamı önceden bilinmiyorsa, bu tür bağlama de kullanışlıdır. Bu aslında, kaynak değerin değişmemesi <xref:System.Windows.Data.BindingMode.OneWay> durumunda daha iyi performans sağlayan daha basit bir bağlama biçimidir.  
  
 Kaynak değişikliklerini (ve <xref:System.Windows.Data.BindingMode.OneWay> <xref:System.Windows.Data.BindingMode.TwoWay> bağlamaları için geçerlidir) algılamak için, kaynağın gibi uygun bir özellik <xref:System.ComponentModel.INotifyPropertyChanged>değişikliği bildirim mekanizması uygulaması gerektiğini unutmayın. Bkz. bir <xref:System.ComponentModel.INotifyPropertyChanged> uygulama örneği için [özellik değişikliği bildirimi uygulama](how-to-implement-property-change-notification.md) .  
  
 <xref:System.Windows.Data.Binding.Mode%2A> Özellik sayfası, bağlama modları hakkında daha fazla bilgi ve bir bağlamanın yönlerinin nasıl belirtilbir örneğini sağlar.  
  
<a name="what_triggers_source_updates"></a>   
### <a name="what-triggers-source-updates"></a>Hangi kaynak güncelleştirmelerini tetikler  
 Hedef özelliğindeki değişiklikler <xref:System.Windows.Data.BindingMode.TwoWay> için <xref:System.Windows.Data.BindingMode.OneWayToSource> veya dinleme yapan bağlamalar ve bunları kaynağa geri yayar. Bu, kaynağı güncelleştirme olarak bilinir. Örneğin, temel alınan kaynak değerini değiştirmek için bir TextBox metnini düzenleyebilirsiniz. Son bölümde açıklandığı gibi, veri akışının yönü, bağlamanın <xref:System.Windows.Data.Binding.Mode%2A> özelliğinin değerine göre belirlenir.  
  
 Ancak, metin düzenlenirken veya metni düzenledikten sonra farenizi metin kutusu 'ndan uzağa işaret ettikten sonra kaynak değeri güncellenir mi? Bağlamanın <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> özelliği, kaynağın güncelleştirilmesini neyin tetikleyeceğini belirler. Aşağıdaki şekildeki doğru okların noktaları, <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> özelliğin rolünü gösterir:  
  
 ![UpdateSourceTrigger özelliğinin rolünü gösteren diyagram.](./media/data-binding-overview/data-binding-updatesource-trigger.png)  
  
 Değer ise <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> <xref:System.Windows.Data.BindingMode.TwoWay> ,<xref:System.Windows.Data.BindingMode.OneWayToSource> sağ ok veya bağlamalar tarafından işaret edilen değer, hedef özelliği değiştiğinde güncellenir. <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> Ancak, <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>değer ise, bu değer yalnızca hedef özelliği odağı kaybettiğinde yeni değeri ile güncellenir. <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>  
  
 <xref:System.Windows.Data.Binding.Mode%2A> Özelliğe benzer şekilde, farklı bağımlılık özellikleri farklı varsayılan <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> değerlere sahiptir. Bağımlılık özelliklerinin çoğu için varsayılan değer, <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> <xref:System.Windows.Controls.TextBox.Text%2A> özelliğin varsayılan değeri <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>olan ' dir. Yani, kaynak güncelleştirmelerinin genellikle Target özelliği her değiştiğinde gerçekleşir. Bu, es ve diğer basit <xref:System.Windows.Controls.CheckBox>denetimler için de uygundur. Ancak, metin alanları için, her tuş vuruşundan sonra güncelleştirme performansı azallebiliyor ve kullanıcıyı yeni değere işlemeden önce, geri alma ve yazma hatalarını çözme fırsatını reddeder. <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> Bunun nedeni <xref:System.Windows.Controls.TextBox.Text%2A> özelliğin yerine<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>varsayılan değeri vardır.  
  
 Bağımlılık özelliğinin varsayılan <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> değerini bulma hakkında bilgi için bkz. özelliksayfası.<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>  
  
 Aşağıdaki tabloda, <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> <xref:System.Windows.Controls.TextBox> örnek olarak kullanılarak her bir değer için örnek bir senaryo verilmiştir:  
  
|UpdateSourceTrigger değeri|Kaynak değer güncelleştirildiği zaman|TextBox için örnek senaryo|  
|-------------------------------|----------------------------------------|----------------------------------|  
|LostFocus (için <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>varsayılan)|TextBox denetimi odağı kaybettiğinde|Doğrulama <xref:System.Windows.Controls.TextBox> mantığı ile ilişkili bir (bkz. veri doğrulama bölümü)|  
|PropertyChanged|İçine yazarken<xref:System.Windows.Controls.TextBox>|<xref:System.Windows.Controls.TextBox>sohbet odası penceresindeki denetimler|  
|Anlaşılır|Uygulama çağırdığında<xref:System.Windows.Data.BindingExpression.UpdateSource%2A>|<xref:System.Windows.Controls.TextBox>düzenlenebilir bir formdaki denetimler (kaynak değerleri yalnızca Kullanıcı Gönder düğmesine tıkladığında güncelleştirir)|  
  
 Bir örnek için bkz. [TextBox metni kaynağı Güncelleştirne zaman denetim](how-to-control-when-the-textbox-text-updates-the-source.md).  
  
<a name="creating_a_binding"></a>   
## <a name="creating-a-binding"></a>Bağlama oluşturma  
  
 Önceki bölümlerde ele alınan kavramların bazılarını belirlemek için, <xref:System.Windows.Data.Binding> nesnesini kullanarak bir bağlama kurarsınız ve her bağlamada genellikle dört bileşen vardır: bağlama hedefi, hedef özellik, bağlama kaynağı ve kullanılacak kaynak değerin yolu. Bu bölümde bir bağlamanın nasıl ayarlanacağı açıklanır.  
  
 Bağlama kaynak nesnesinin, *SDKSample* ad alanında tanımlanan *MyData* adlı bir sınıf olduğu aşağıdaki örneği göz önünde bulundurun. Tanıtım amacıyla, *MyData* sınıfının *ColorName*adlı ve değerin "Red" olarak ayarlandığı bir String özelliği vardır. Bu nedenle, bu örnek kırmızı bir arka plana sahip bir düğme oluşturur.  
  
 [!code-xaml[BindNonTextProperty#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindNonTextProperty/CS/Page1.xaml#1)]  
  
 Bağlama bildirimi sözdizimi hakkında daha fazla bilgi ve kod içinde bağlama ayarlama örnekleri için bkz. [bağlama bildirimlerine genel bakış](binding-declarations-overview.md).  
  
 Bu örneği temel diyagramımızı uygulıyoruz, sonuçta elde edilen şekil aşağıdaki gibi görünür. Bu bir <xref:System.Windows.Data.BindingMode.OneWay> bağlamadır çünkü Arkaplan özelliği varsayılan olarak <xref:System.Windows.Data.BindingMode.OneWay> bağlamayı destekler.  
  
 ![Veri bağlama arka plan özelliğini gösteren diyagram.](./media/data-binding-overview/data-binding-button-background-example.png)  
  
 <xref:System.Windows.Controls.Control.Background%2A> Özelliğin tür<xref:System.Windows.Media.Brush>olduğu sürece *ColorName* özelliği String türünde olmasına rağmen bunun neden olduğunu merak edebilirsiniz. Bu, iş sırasında varsayılan tür dönüştürmedir ve [veri dönüştürme](#data_conversion) bölümünde ele alınmıştır.  
  
<a name="specifying_the_binding_source"></a>   
### <a name="specifying-the-binding-source"></a>Bağlama kaynağını belirtme  
 Önceki örnekte, bağlama kaynağının <xref:System.Windows.FrameworkElement.DataContext%2A> <xref:System.Windows.Controls.DockPanel> öğesinde özelliği ayarlanarak belirtildiğine dikkat edin. Sonra değeri, üst öğesi olan öğesinden <xref:System.Windows.Controls.DockPanel>devralır. <xref:System.Windows.FrameworkElement.DataContext%2A> <xref:System.Windows.Controls.Button> Yeniden yinelemek için bağlama kaynak nesnesi, bir bağlamanın gerekli dört bileşenlerinden biridir. Bu nedenle, bağlama kaynak nesnesi belirtilmeksizin bağlama hiçbir şey yapmaz.  
  
 Bağlama kaynak nesnesini belirtmek için çeşitli yollar vardır. Aynı kaynağa birden çok özellik bağlarken bir üst öğe üzerinde özelliğinikullanmakfaydalıdır.<xref:System.Windows.FrameworkElement.DataContext%2A> Ancak, bazen bağlama kaynağını tek tek bağlama bildirimlerinde belirtmek daha uygun olabilir. Önceki örnekte, <xref:System.Windows.FrameworkElement.DataContext%2A> özelliğini kullanmak yerine, aşağıdaki örnekte olduğu gibi, özelliği doğrudan düğmenin bağlama bildiriminde <xref:System.Windows.Data.Binding.Source%2A> ayarlayarak bağlama kaynağını belirtebilirsiniz:  
  
 [!code-xaml[BindNonTextProperty#BackgroundBindingCompact](~/samples/snippets/csharp/VS_Snippets_Wpf/BindNonTextProperty/CS/Page2.xaml#backgroundbindingcompact)]  
  
 Bir öğedeki <xref:System.Windows.FrameworkElement.DataContext%2A> özelliği doğrudan ayarlamaya, <xref:System.Windows.FrameworkElement.DataContext%2A> değeri bir üst öğeden devralından (örneğin, ilk örnekteki düğme gibi) ve <xref:System.Windows.Data.Binding.Source%2A> <xref:System.Windows.Data.Binding> (son örnekteki düğme gibi), bağlama kaynağını belirtmek için <xref:System.Windows.Data.Binding.ElementName%2A> özelliğini <xref:System.Windows.Data.Binding.RelativeSource%2A> veya özelliğini de kullanabilirsiniz. <xref:System.Windows.Data.Binding.ElementName%2A> Özelliği, bir düğmenin genişliğini ayarlamak için kaydırıcı kullanırken olduğu gibi, uygulamanızdaki diğer öğelere bağlarken faydalıdır. Özelliği, <xref:System.Windows.Controls.ControlTemplate> veya<xref:System.Windows.Style>içinde bağlama belirtildiğinde faydalıdır. <xref:System.Windows.Data.Binding.RelativeSource%2A> Daha fazla bilgi için bkz. [bağlama kaynağını belirtme](how-to-specify-the-binding-source.md).  
  
<a name="specifying_the_path_to_the_value"></a>   
### <a name="specifying-the-path-to-the-value"></a>Değerin yolunu belirtme  
 Bağlama kaynağınız bir nesnedir, bağlamanız için kullanılacak değeri belirtmek <xref:System.Windows.Data.Binding.Path%2A> için özelliğini kullanın. [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] Verilere bağlıyorsanız, değeri belirtmek için <xref:System.Windows.Data.Binding.XPath%2A> özelliğini kullanın. Bazı durumlarda, <xref:System.Windows.Data.Binding.Path%2A> [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]verileriniz olduğunda bile özelliği kullanmak için geçerli olabilir. Örneğin, döndürülen bir XmlNode 'un Name özelliğine (bir XPath sorgusunun sonucu olarak) erişmek istiyorsanız özelliği ek <xref:System.Windows.Data.Binding.Path%2A> <xref:System.Windows.Data.Binding.XPath%2A> olarak özelliğini kullanmanız gerekir.  
  
 Sözdizimi bilgileri ve örnekleri için, <xref:System.Windows.Data.Binding.Path%2A> ve <xref:System.Windows.Data.Binding.XPath%2A> özellik sayfalarına bakın.  
  
 Kullanılacak değere öğesinin, <xref:System.Windows.Data.Binding.Path%2A> bir bağlamanın dört gerekli bileşenlerinden biri olduğunu vurguladığımızda, bir nesnenin tamamına bağlamak istediğiniz senaryoların, bağlanacak değerin bağlama kaynak nesnesi ile aynı olacağını unutmayın. Bu durumlarda, bir <xref:System.Windows.Data.Binding.Path%2A>belirtmemelidir. Aşağıdaki örnek göz önünde bulundurun:  
  
 [!code-xaml[MasterDetail#EmptyBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetail/CSharp/Page1.xaml#emptybinding)]  
  
 Yukarıdaki örnek, boş bağlama söz dizimini kullanır: {Binding}. Bu durumda <xref:System.Windows.Controls.ListBox> , bir üst DockPanel öğesinden DataContext 'i devralır (Bu örnekte gösterilmez). Yol belirtilmediğinde, varsayılan olarak nesnenin tamamına bağlanır. Diğer bir deyişle, bu örnekte, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliği nesnenin tamamına bağlamamız nedeniyle yol kalmadı. (Ayrıntılı bir tartışma için [koleksiyonlara bağlama](#binding_to_collections) bölümüne bakın.)  
  
 Bir koleksiyona bağlama dışında, bu senaryo aynı zamanda yalnızca bir nesnenin tek bir özelliği yerine bir nesnenin tamamına bağlamak istediğinizde de yararlıdır. Örneğin, kaynak nesneniz dize türündedir ve yalnızca dizenin kendisini bağlamak istiyorsanız. Diğer bir yaygın senaryo, bir öğeyi birkaç özelliği olan bir nesneye bağlamak istemizin olur.  
  
 Verilerin, bağlantılı hedef özelliği için anlamlı olması için özel mantık uygulamanız gerekebileceğini unutmayın. Özel mantık özel bir dönüştürücü biçiminde olabilir (varsayılan tür dönüştürmesi yoksa). Dönüştürücüler hakkında bilgi için bkz. [veri dönüştürme](#data_conversion) .  
  
<a name="binding_bindingexpression"></a>   
### <a name="binding-and-bindingexpression"></a>Bağlama ve BindingExpression  
 Veri bağlamanın diğer özelliklerine ve kullanımlarına geçmeden önce, <xref:System.Windows.Data.BindingExpression> sınıfı tanıtmak yararlı olacaktır. Önceki bölümlerde gördüğünüz gibi, <xref:System.Windows.Data.Binding> sınıfı bağlama bildirimi için üst düzey sınıftır <xref:System.Windows.Data.Binding> ; sınıfı, bir bağlamanın özelliklerini belirtmenize imkan tanıyan birçok özellik sağlar. İlişkili bir sınıf, <xref:System.Windows.Data.BindingExpression>kaynak ve hedef arasındaki bağlantıyı tutan temel nesnedir. Bağlama, birkaç bağlama ifadesi genelinde paylaşılabilen tüm bilgileri içerir. <xref:System.Windows.Data.BindingExpression> ,<xref:System.Windows.Data.Binding>Paylaşılamayan bir örnek ifadesidir ve öğesinin tüm örnek bilgilerini içerir.  
  
 Örneğin, *myDataObject* bir *MyData* sınıfının örneği olduğu, *myBinding* 'in kaynak <xref:System.Windows.Data.Binding> nesne olduğu ve *MyData* sınıfının, bir dize özelliği *içeren tanımlanmış bir sınıf olduğu MyDataProperty*. Bu örnek, bir örneği olan <xref:System.Windows.Controls.TextBlock> *myText*metin içeriğini *MyDataProperty*öğesine bağlar.  
  
 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 Diğer bağlamaları oluşturmak için aynı *myBinding* nesnesi kullanabilirsiniz. Örneğin, bir onay kutusunun metin içeriğini *MyDataProperty*olarak bağlamak Için *myBinding* nesnesini kullanabilirsiniz. Bu senaryoda, <xref:System.Windows.Data.BindingExpression> *myBinding* nesnesini paylaşan iki örnek olacaktır.  
  
 Bir <xref:System.Windows.Data.BindingExpression> nesne, veriye bağlı bir nesne üzerinde çağırmanın <xref:System.Windows.Data.BindingOperations.GetBindingExpression%2A> dönüş değeri aracılığıyla elde edilebilir. Aşağıdaki konularda, <xref:System.Windows.Data.BindingExpression> sınıfının kullanımları gösterilmektedir:  
  
- [Bağımlı Hedef Özelliğinden Bağlama Nesnesi Alma](how-to-get-the-binding-object-from-a-bound-target-property.md)  
  
- [TextBox Metni Kaynağı Güncelleştirdiğinde Denetleme](how-to-control-when-the-textbox-text-updates-the-source.md)  
  
<a name="data_conversion"></a>   
## <a name="data-conversion"></a>Veri Dönüştürme  
 Önceki örnekte düğme kırmızıdır çünkü <xref:System.Windows.Controls.Control.Background%2A> özelliği "Red" değerine sahip bir dize özelliğine bağımlıdır. Bu, dize değerini bir <xref:System.Windows.Media.Brush> <xref:System.Windows.Media.Brush>türüne dönüştürmek için tür dönüştürücünün mevcut olduğu için geçerlidir.  
  
 Bu bilgileri [bağlama oluşturma](#creating_a_binding) bölümünde şekle eklemek için, diyagram aşağıdakine benzer şekilde görünür:  
  
 ![Veri bağlama varsayılan özelliğini gösteren diyagram.](./media/data-binding-overview/data-binding-button-default-conversion.png)  
  
 Ancak, Binding kaynak nesnenizin dize türünde bir özelliği olması yerine ne tür <xref:System.Windows.Media.Color>bir *Color* özelliği vardır? Bu durumda, bağlamanın çalışması için öncelikle *Color* özelliğinin değerini <xref:System.Windows.Controls.Control.Background%2A> özelliğin kabul ettiği bir şeye dönüştürmeniz gerekir. Aşağıdaki örnekte olduğu gibi, <xref:System.Windows.Data.IValueConverter> arabirimini uygulayarak özel bir dönüştürücü oluşturmanız gerekir:  
  
 [!code-csharp[ColorPicker_snip#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ColorPicker_snip/CSharp/ColorPickerLib/ColorPicker.cs#16)]
 [!code-vb[ColorPicker_snip#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ColorPicker_snip/visualbasic/colorpickerlib/colorpicker.vb#16)]  
  
 <xref:System.Windows.Data.IValueConverter> Başvuru sayfası daha fazla bilgi sağlar.  
  
 Artık varsayılan dönüştürme yerine özel dönüştürücü kullanılır ve diyagramımız şuna benzer:  
  
 ![Veri bağlama özel dönüştürücüsünü gösteren diyagram.](./media/data-binding-overview/data-binding-converter-color-example.png)  
  
 Yeniden yinelemek için, bağlanmakta olan türde bulunan tür dönüştürücüler nedeniyle varsayılan dönüşümler kullanılabilir olabilir. Bu davranış, hedefte hangi tür dönüştürücülerinin kullanılabilir olduğuna bağlı olarak değişir. Şüpheniz varsa, kendi dönüştürücüyü oluşturun.  
  
 Aşağıda, bir veri dönüştürücüsünü uygulamak açısından anlamlı olduğu bazı tipik senaryolar verilmiştir:  
  
- Verileriniz kültüre bağlı olarak farklı şekilde görüntülenmelidir. Örneğin, belirli bir kültürden kullanılan değerlere veya standartlara göre bir para birimi dönüştürücü veya takvim tarih/saat Dönüştürücüsü uygulamak isteyebilirsiniz.  
  
- Kullanılan veriler bir özelliğin metin değerini değiştirmek zorunda değildir, ancak bunun yerine bir görüntünün kaynağı veya görüntü metninin rengi ya da stili gibi başka bir değerin değiştirilmesini amaçlanır. Dönüştürücüler, bir metin alanını tablo hücresinin arka plan özelliğine bağlama gibi, uygun gibi görünmeyebilir bir özelliğin bağlamasını dönüştürerek bu örnekte kullanılabilir.  
  
- Denetimlerin birden fazla denetimi veya birden çok özelliği aynı verilere bağlıydı. Bu durumda, birincil bağlama yalnızca metni görüntüleyebilir, diğer bağlamalar ise belirli görüntüleme sorunlarını işler ancak yine de kaynak bilgilerle aynı bağlamayı kullanır.  
  
- Şimdiye kadar henüz açıklanmamıştır <xref:System.Windows.Data.MultiBinding>, burada bir hedef özellik bir bağlama koleksiyonuna sahiptir. Bir <xref:System.Windows.Data.MultiBinding>durumunda, bağlamaların değerlerinden son bir değer üretmek <xref:System.Windows.Data.IMultiValueConverter> için özel ' i kullanırsınız. Örneğin, aynı veya farklı bağlama kaynak nesnelerinden değer olabilen kırmızı, mavi ve yeşil değerlerden renk hesaplanabilir. Örnekler ve bilgiler için bkz. sınıfsayfası.<xref:System.Windows.Data.MultiBinding>  
  
<a name="binding_to_collections"></a>   
## <a name="binding-to-collections"></a>Koleksiyonlara bağlama  
  
 Bağlama kaynak nesnesi, verilerin bulunduğu tek bir nesne olarak veya genellikle birlikte gruplandırılan çok biçimli nesnelerin veri koleksiyonu olarak (bir veritabanının bir sorgusunun sonucu gibi) ele alınabilir. Şimdiye kadar yalnızca tek nesnelere bağlamayı tartıştık, ancak bir veri koleksiyonuna bağlama yaygın bir senaryodur. Örneğin, yaygın bir senaryo <xref:System.Windows.Controls.ItemsControl> ,, veya <xref:System.Windows.Controls.TreeView> gibi bir veri koleksiyonunu ( <xref:System.Windows.Controls.ListBox> [veri bağlama nedir?](#what_is_data_binding) bölümünde gösterilen uygulamada) göstermek için kullanılır <xref:System.Windows.Controls.ListView>.  
  
 Neyse ki temel diyagramımız hala geçerli olur. Bir koleksiyona bağlıyorsanız <xref:System.Windows.Controls.ItemsControl> , diyagram şuna benzer:  
  
 ![Veri bağlama ItemControl nesnesini gösteren diyagram.](./media/data-binding-overview/data-binding-itemscontrol.png)  
  
 Bu diyagramda gösterildiği gibi, bir <xref:System.Windows.Controls.ItemsControl> koleksiyon <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> nesnesine bağlamak için özelliği kullanılacak özelliktir. <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> Özelliğini öğesinin içeriği <xref:System.Windows.Controls.ItemsControl>olarak düşünebilirsiniz. Bağlamanın <xref:System.Windows.Data.BindingMode.OneWay> <xref:System.Windows.Data.BindingMode.OneWay> , özelliğinvarsayılanolarakbağlamayıdesteklediğiniunutmayın.<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>  
  
<a name="how_to_implement_collections"></a>   
### <a name="how-to-implement-collections"></a>Koleksiyonları uygulama  
 <xref:System.Collections.IEnumerable> Arabirimini uygulayan herhangi bir koleksiyonun üzerinde listeleme yapabilirsiniz. Bununla birlikte, koleksiyondaki ekleme veya silme işlemlerinin [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] otomatik olarak güncelleştirilmesini sağlamak için dinamik bağlamaları ayarlamak için koleksiyonun <xref:System.Collections.Specialized.INotifyCollectionChanged> arabirimini uygulaması gerekir. Bu arabirim, temeldeki koleksiyon değiştiğinde oluşturulması gereken bir olay gösterir.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], arabirimi kullanıma sunan bir veri koleksiyonunun yerleşik bir uygulama olan sınıfınısağlar.<xref:System.Collections.ObjectModel.ObservableCollection%601> <xref:System.Collections.Specialized.INotifyCollectionChanged> Veri değerlerinin Kaynak nesnelerden hedeflere aktarılmasını tam olarak desteklemek için, koleksiyonunuzdaki bağlanabilir özellikleri destekleyen her nesnenin da <xref:System.ComponentModel.INotifyPropertyChanged> arabirimini uygulaması gerekir. Daha fazla bilgi için bkz. [bağlama kaynaklarına genel bakış](binding-sources-overview.md).  
  
 Kendi koleksiyonunuzu uygulamadan önce, <xref:System.Collections.ObjectModel.ObservableCollection%601> , ve <xref:System.ComponentModel.BindingList%601>gibi var olan koleksiyon sınıflarından <xref:System.Collections.Generic.List%601> <xref:System.Collections.ObjectModel.Collection%601>birini ya da birçok başka konuda kullanmayı düşünün. Gelişmiş bir senaryonuz varsa ve kendi koleksiyonunuzu uygulamak istiyorsanız <xref:System.Collections.IList>, dizin tarafından ayrı ayrı erişilebilen nesnelerin genel olmayan bir koleksiyonunu sağlayan öğesini kullanın ve bu nedenle en iyi performansı elde edebilirsiniz.  
  
<a name="collection_views"></a>   
### <a name="collection-views"></a>Koleksiyon Görünümleri  
 <xref:System.Windows.Controls.ItemsControl> Bir veri koleksiyonu bağladıktan sonra verileri sıralamak, filtrelemek veya gruplandırmak isteyebilirsiniz. Bunu yapmak için, <xref:System.ComponentModel.ICollectionView> arabirimini uygulayan sınıflar olan koleksiyon görünümlerini kullanırsınız.  

#### <a name="what-are-collection-views"></a>Koleksiyon görünümleri nelerdir?  
 Koleksiyon görünümü, temel kaynak koleksiyonun kendisini değiştirmek zorunda kalmadan sıralama, filtre ve grup sorgularına göre kaynak koleksiyonunu gezinmenize ve görüntülemenize olanak tanıyan bir bağlama kaynak koleksiyonunun en üstünde yer alan bir katmandır. Koleksiyon görünümü Ayrıca koleksiyondaki geçerli öğe için bir işaretçi tutar. Kaynak koleksiyon <xref:System.Collections.Specialized.INotifyCollectionChanged> arabirimini uygularsa, <xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged> olay tarafından oluşturulan değişiklikler görünümlere yayılır.  
  
 Görünümler temeldeki kaynak koleksiyonlarını değiştirmediğinden, her kaynak koleksiyonda ilişkili birden fazla görünüm bulunabilir. Örneğin, *görev* nesneleri koleksiyonunuz olabilir. Görünümlerin kullanımı ile aynı verileri farklı yollarla görüntüleyebilirsiniz. Örneğin, sayfanızın sol tarafında önceliğe göre sıralanmış görevleri ve sağ tarafa alana göre gruplanmış olarak göstermek isteyebilirsiniz.  
  
<a name="how_to_create_a_view"></a>   
#### <a name="how-to-create-a-view"></a>Görünüm oluşturma  
 Bir görünüm oluşturmanın ve kullanmanın bir yolu, doğrudan görünüm nesnesini oluşturmak ve bunu bağlama kaynağı olarak kullanmaktır. Örneğin veri bağlama [demo](https://go.microsoft.com/fwlink/?LinkID=163703) uygulamasını, [veri bağlama nedir?](#what_is_data_binding) bölümünde gösterilen şekilde düşünün. Uygulama, veri toplamayı doğrudan değil, <xref:System.Windows.Controls.ListBox> veri koleksiyonu üzerinden bir görünüme bağlalara uygulanır. Aşağıdaki örnek [veri bağlama tanıtım](https://go.microsoft.com/fwlink/?LinkID=163703) uygulamasından ayıklanır. Sınıfı, öğesinden<xref:System.Windows.Data.CollectionView>devralan bir sınıfın proxy'si.[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] <xref:System.Windows.Data.CollectionViewSource> Bu örnekte, <xref:System.Windows.Data.CollectionViewSource.Source%2A> görünümün geçerli uygulama nesnesinin *AuctionItems* koleksiyonuna (türü <xref:System.Collections.ObjectModel.ObservableCollection%601>) bağlanması gerekir.  
  
 [!code-xaml[DataBindingLab#WindowResources1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#windowresources1)]  
[!code-xaml[DataBindingLab#CollectionViewSource](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#collectionviewsource)]  
[!code-xaml[DataBindingLab#WindowResources2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#windowresources2)]  
  
 *ListingDataView* kaynağı daha sonra uygulamadaki <xref:System.Windows.Controls.ListBox>öğeler için bağlama kaynağı olarak görev yapar; örneğin:  
  
 [!code-xaml[DataBindingLab#Master1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master1)]  
[!code-xaml[DataBindingLab#Master2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master2)]  
  
 Aynı koleksiyon için başka bir görünüm oluşturmak üzere başka <xref:System.Windows.Data.CollectionViewSource> bir örnek oluşturabilir ve buna farklı `x:Key` bir ad verebilirsiniz.  
  
 Aşağıdaki tabloda, varsayılan koleksiyon görünümü olarak veya <xref:System.Windows.Data.CollectionViewSource> kaynak koleksiyon türüne göre oluşturulan görünüm veri türleri gösterilmektedir.  
  
|Kaynak koleksiyon türü|Koleksiyon görünüm türü|Notlar|  
|----------------------------|--------------------------|-----------|  
|<xref:System.Collections.IEnumerable>|Temelinde bir iç tür<xref:System.Windows.Data.CollectionView>|Öğeler gruplandırılamıyor.|  
|<xref:System.Collections.IList>|<xref:System.Windows.Data.ListCollectionView>|En hızlı.|  
|<xref:System.ComponentModel.IBindingList>|<xref:System.Windows.Data.BindingListCollectionView>||  
  
##### <a name="using-a-default-view"></a>Varsayılan görünüm kullanma  
 Bir koleksiyon görünümünü bağlama kaynağı olarak belirtme, koleksiyon görünümü oluşturmanın ve kullanmanın bir yoludur. WPF ayrıca, bağlama kaynağı olarak kullanılan her koleksiyon için varsayılan bir koleksiyon görünümü oluşturur. Doğrudan bir koleksiyona bağlarsanız, WPF varsayılan görünümüne bağlanır. Bu varsayılan görünümün tüm bağlamalar tarafından aynı koleksiyona paylaşıldığını unutmayın. bu nedenle, bir bağlantılı denetim veya kodla (sıralama ya da geçerli öğe İşaretçisinde yapılan bir değişiklik gibi) bir varsayılan görünümde yapılan bir değişiklik, aynı koleksiyona yönelik diğer tüm bağlamalara yansıtılır.  
  
 Varsayılan görünümü almak için <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> yöntemini kullanırsınız. Bir örnek için bkz. [veri koleksiyonunun varsayılan görünümünü edinme](how-to-get-the-default-view-of-a-data-collection.md).  
  
##### <a name="collection-views-with-adonet-datatables"></a>ADO.NET DataTable ile koleksiyon görünümleri  
 Performansı artırmak için, ADO.net <xref:System.Data.DataTable> veya <xref:System.Data.DataView> nesneleri için koleksiyon görünümlerini, <xref:System.Data.DataView>sıralama ve filtreleme yetkisini sağlar. Bu, sıralama ve filtrelemenin veri kaynağının tüm koleksiyon görünümlerinde paylaşılmasına neden olur. Her koleksiyon görünümünün bağımsız olarak sıralanmasını ve filtrelemesine olanak tanımak için her koleksiyon görünümünü kendi <xref:System.Data.DataView> nesnesiyle başlatın.  
  
#### <a name="sorting"></a>Sıralama  
 Daha önce bahsedildiği gibi, görünümler bir koleksiyona sıralama düzeni uygulayabilir. Temel koleksiyonda olduğu gibi, verileriniz ilgili ve kendine özgü bir sıraya sahip olabilir veya olmayabilir. Koleksiyon üzerindeki görünüm, sağladığınız karşılaştırma ölçütlerine göre bir sipariş veya varsayılan sırayı değiştirmenize olanak sağlar. Verilerin istemci tabanlı bir görünümü olduğundan, yaygın olarak kullanılan bir senaryo, kullanıcının sütun için karşılık gelen tablo verilerinin sütunlarını sütuna karşılık geldiği bir değere göre sıralamak isteyebilir. Görünümleri kullanarak, bu kullanıcı odaklı sıralama, temel koleksiyonda herhangi bir değişiklik yapılmadan veya koleksiyon içeriğini yeniden sorgulamak zorunda kalmadan uygulanabilir. Bir örnek için bkz. [bir başlık tıklandığında GridView sütununu sıralama](../controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).  
  
 Aşağıdaki örnek, uygulamanın <xref:System.Windows.Controls.CheckBox> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] [veri bağlama nedir?](#what_is_data_binding) bölümünde "kategoriye ve tarihe göre sırala" öğesinin sıralama mantığını gösterir:  
  
 [!code-csharp[DataBindingLab#8](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#8)]
 [!code-vb[DataBindingLab#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#8)]  
  
#### <a name="filtering"></a>Filtreleme  
 Görünümler, bir koleksiyona filtre de uygulayabilir. Bu, koleksiyonda bir öğe var olabileceğinden, bu görünümün tam koleksiyonun yalnızca belirli bir alt kümesini göstermesini amaçladığı anlamına gelir. Verilerdeki bir koşula filtre ekleyebilirsiniz. Örneğin, [veri bağlama nedir?](#what_is_data_binding) bölümünde uygulama tarafından yapıldığı gibi, "yalnızca barkazancı göster" <xref:System.Windows.Controls.CheckBox> , maliyet $25 veya daha fazla olan öğeleri filtrelemek için mantık içerir. Aşağıdaki kod, seçili olduğunda <xref:System.Windows.Data.CollectionViewSource.Filter> <xref:System.Windows.Controls.CheckBox> olay işleyicisi olarak *ShowOnlyBargainsFilter* öğesini ayarlamak için yürütülür:  
  
 [!code-csharp[DataBindingLab#10](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 *ShowOnlyBargainsFilter* olay işleyicisi aşağıdaki uygulamaya sahiptir:  
  
 [!code-csharp[DataBindingLab#5](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
 Yerine doğrudan <xref:System.Windows.Data.CollectionView> sınıflardan birini kullanıyorsanız <xref:System.Windows.Data.CollectionView.Filter%2A> ,birgeriçağırmabelirtmekiçinözelliğinikullanın.<xref:System.Windows.Data.CollectionViewSource> Bir örnek için bkz. [bir görünümdeki verileri filtreleme](how-to-filter-data-in-a-view.md).  
  
#### <a name="grouping"></a>Gruplandırma  
 Bir <xref:System.Collections.IEnumerable> koleksiyonu görüntüleyen iç sınıf hariç, tüm koleksiyon görünümleri gruplandırma işlevlerini destekler, bu da kullanıcının koleksiyon görünümündeki koleksiyonu mantıksal gruplar halinde bölümlendirmeye olanak tanır. Gruplar, kullanıcının grupların bir listesini sağladığı veya örtük olarak, grupların verilere göre dinamik olarak oluşturulduğu açık olabilir.  
  
 Aşağıdaki örnek, "kategoriye göre gruplandırma" <xref:System.Windows.Controls.CheckBox>mantığını gösterir:  
  
 [!code-csharp[DataBindingLab#6](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#6)]
 [!code-vb[DataBindingLab#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#6)]  
  
 Başka bir gruplandırma örneği için bkz. [GridView uygulayan bir ListView Içindeki öğeleri gruplandırma](../controls/how-to-group-items-in-a-listview-that-implements-a-gridview.md).  
  
#### <a name="current-item-pointers"></a>Geçerli öğe Işaretçileri  
 Görünümler, geçerli bir öğe kavramını da destekler. Bir koleksiyon görünümündeki nesneler arasında gezinebilirsiniz. Gezindiğinizde, koleksiyonda belirli bir konumda bulunan nesneyi almanıza izin veren bir öğe işaretçisini taşıyor olursunuz. Bir örnek için bkz. [Data CollectionView Içindeki nesneler arasında gezinme](how-to-navigate-through-the-objects-in-a-data-collectionview.md).  
  
 WPF bir koleksiyona yalnızca bir görünüm (belirttiğiniz bir görünüm veya koleksiyonun varsayılan görünümü) kullanarak bağlandığından, koleksiyonlara yönelik tüm bağlamaların geçerli öğe işaretçisi vardır. Bir görünüme bağlanırken, bir `Path` değer içindeki eğik çizgi ("/") karakteri görünümün geçerli öğesini belirler. Aşağıdaki örnekte, veri bağlamı bir koleksiyon görünümüdür. İlk satır koleksiyona bağlanır. İkinci satır koleksiyondaki geçerli öğeye bağlanır. Üçüncü satır koleksiyondaki geçerli öğenin `Description` özelliğine bağlar.  
  
```xaml  
<Button Content="{Binding }" />  
<Button Content="{Binding Path=/}" />  
<Button Content="{Binding Path=/Description}" />   
```  
  
 Eğik çizgi ve özellik söz dizimi bir koleksiyon hiyerarşisinin çapraz geçişini sağlamak için de yığınlanalabilir. Aşağıdaki örnek, kaynak koleksiyonun geçerli öğesinin bir özelliği olan adlı `Offices`bir koleksiyonun geçerli öğesine bağlar.  
  
```xaml  
<Button Content="{Binding /Offices/}" />  
```  
  
 Geçerli öğe işaretçisi, koleksiyona uygulanan sıralama veya filtrelemeden etkilenebilir. Sıralama, seçili son öğe üzerinde geçerli öğe işaretçisini korur, ancak koleksiyon görünümü artık bunun etrafında yeniden yapılandırılmış. (Belki de seçili öğe listenin başında, ancak artık seçili öğe ortada bir yerde olabilir.) Filtre, filtreleme sonrasında Görünüm ' de kalırsa, seçili öğeyi korur. Aksi takdirde, geçerli öğe işaretçisi filtrelenmiş koleksiyon görünümünün ilk öğesine ayarlanır.  
  
<a name="master_detail_scenario"></a>   
#### <a name="master-detail-binding-scenario"></a>Ana-ayrıntı bağlama senaryosu  
 Geçerli bir öğe kavramı yalnızca bir koleksiyondaki öğelerin gezinmesi için değil, aynı zamanda ana ayrıntı bağlama senaryosu için de kullanışlıdır. Uygulamayı [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] [veri bağlama nedir?](#what_is_data_binding) bölümünde yeniden düşünün. Bu uygulamada, içindeki <xref:System.Windows.Controls.ListBox> seçim içinde gösterilen <xref:System.Windows.Controls.ContentControl>içeriği belirler. Bir <xref:System.Windows.Controls.ListBox> öğe seçildiğinde <xref:System.Windows.Controls.ContentControl> , bu öğeyi başka bir şekilde koymak için seçili öğenin ayrıntılarını gösterir.  
  
 Aynı görünüme iki veya daha fazla denetim bağlayarak, ana ayrıntı senaryosunu uygulayabilirsiniz. [Veri bağlama tanıtımında](https://go.microsoft.com/fwlink/?LinkID=163703) bulunan aşağıdaki <xref:System.Windows.Controls.ListBox> örnek, ve [](#what_is_data_binding) <xref:System.Windows.Controls.ContentControl> veri bağlama nedir? bölümünde uygulamada [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] gördüklerinizi gösterir.  
  
 [!code-xaml[DataBindingLab#Master1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master1)]  
[!code-xaml[DataBindingLab#Master2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master2)]  
[!code-xaml[DataBindingLab#Detail](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#detail)]  
  
 Denetimlerin her ikisinin de aynı kaynağa, *listingDataView* statik kaynağına ( [bir görünüm oluşturma bölümünde](#how_to_create_a_view)bu kaynağın tanımına bakın) bağlandığını unutmayın. Bu, bir tekil nesne ( <xref:System.Windows.Controls.ContentControl> bu durumda) bir koleksiyon görünümüne bağlı olduğunda, otomatik olarak görünümün <xref:System.Windows.Data.CollectionView.CurrentItem%2A> öğesine bağladığı için geçerlidir. <xref:System.Windows.Data.CollectionViewSource> Nesnelerin para birimi ve seçimi otomatik olarak eşitlediğini unutmayın. Liste denetiminiz bir <xref:System.Windows.Data.CollectionViewSource> nesneye bu örnekte olduğu gibi bağlanmazsa, bunun çalışması için <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> özelliğini olarak `true` ayarlamanız gerekir.  
  
 Diğer örnekler için bkz. [bir koleksiyona bağlama ve seçime göre bilgi görüntüleme](how-to-bind-to-a-collection-and-display-information-based-on-selection.md) ve [hiyerarşik verilerle ana ayrıntı modelini kullanma](how-to-use-the-master-detail-pattern-with-hierarchical-data.md).  
  
 Yukarıdaki örneğin bir şablon kullandığını fark etmiş olabilirsiniz. Aslında, veriler şablonlar kullanılmadan (tarafından açıkça <xref:System.Windows.Controls.ContentControl> kullanılan ve <xref:System.Windows.Controls.ListBox>tarafından örtülü olarak kullanılan), istediğimiz şekilde gösterilmez. Şimdi, sonraki bölümde veri şablonu oluşturma özelliğini kullanacağız.  
  
<a name="data_templating"></a>   
## <a name="data-templating"></a>Veri şablonu oluşturma  
 Veri şablonlarının kullanımı olmadan, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] [veri bağlama nedir?](#what_is_data_binding) bölümündeki uygulamamız aşağıdaki gibi görünür:  
  
 ![Veri şablonları olmadan veri bağlama tanıtımı](./media/data-binding-overview/data-binding-demo-templates.png)  
  
 Önceki bölümde gösterildiği gibi, hem <xref:System.Windows.Controls.ListBox> denetim <xref:System.Windows.Controls.ContentControl> hem de tüm koleksiyon nesnesine (ya da daha fazla özellikle, koleksiyon nesnesi üzerinde Görünüm), *AuctionItem*s ' nin tamamına bağlanır. Veri koleksiyonunun <xref:System.Windows.Controls.ListBox> nasıl görüntüleneceği konusunda belirli yönergeler olmadan, temel alınan koleksiyondaki her nesnenin dize gösterimini görüntülüyor <xref:System.Windows.Controls.ContentControl> ve bağlandığı nesnenin dize gösterimini görüntülüyor.  
  
 Bu sorunu çözmek için uygulama, s 'yi <xref:System.Windows.DataTemplate>tanımlar. Önceki bölümdeki <xref:System.Windows.Controls.ContentControl> örnekte gösterildiği gibi, açıkça *Ayrıntılar productlistingtemplate*<xref:System.Windows.DataTemplate>kullanır. Denetim, koleksiyonda *AuctionItem* nesnelerini <xref:System.Windows.DataTemplate> görüntülerken şunları örtülü olarak kullanır: <xref:System.Windows.Controls.ListBox>  
  
 [!code-xaml[DataBindingLab#AuctionItemDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#auctionitemdatatemplate)]  
  
 Bu iki <xref:System.Windows.DataTemplate>öğesinin kullanımıyla birlikte, sonuçta elde edilen kullanıcı arabirimi, [veri bağlama nedir?](#what_is_data_binding) bölümünde gösterilen şeydir. Bu ekran görüntüsünden görebileceğiniz gibi, denetimlerinizde veri yerleştirmenize izin vermenin yanı sıra verileriniz için etkileyici görseller tanımlamanızı <xref:System.Windows.DataTemplate>da sağlar. Örneğin, yukarıda <xref:System.Windows.DataTrigger>' de, *özelleştirilmiş özellikler* içeren <xref:System.Windows.DataTemplate> *AuctionItem*s 'in, turuncu bir kenarlık ve yıldız  ile görüntülenebilmesi için, yukarıda ' de kullanılır.  
  
 Veri şablonları hakkında daha fazla bilgi için bkz. [veri şablonu oluşturmaya genel bakış](data-templating-overview.md).  
  
<a name="data_validation"></a>   
## <a name="data-validation"></a>Veri doğrulama  
  
 Kullanıcı girişi kullanan çoğu uygulamanın, kullanıcının beklenen bilgileri girdiğinden emin olmak için doğrulama mantığı olması gerekir. Doğrulama denetimleri tür, Aralık, biçim veya uygulamaya özgü diğer gereksinimlere göre yapılabilir. Bu bölümde, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]içinde veri doğrulamanın nasıl çalıştığı açıklanmaktadır.  
  
### <a name="associating-validation-rules-with-a-binding"></a>Doğrulama kurallarını bir bağlama ile ilişkilendirme  
 Veri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bağlama modeli, <xref:System.Windows.Data.Binding> nesneniz ile ilişkilendirmenize <xref:System.Windows.Data.Binding.ValidationRules%2A> olanak tanır. Örneğin, <xref:System.Windows.Controls.TextBox> aşağıdaki örnek öğesini adlı `StartPrice` bir özelliğe bağlar ve <xref:System.Windows.Data.Binding.ValidationRules%2A?displayProperty=nameWithType> özelliğine bir <xref:System.Windows.Controls.ExceptionValidationRule> nesne ekler.  
  
 [!code-xaml[DataBindingLab#DefaultValidation](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#defaultvalidation)]  
  
 Bir <xref:System.Windows.Controls.ValidationRule> nesne, özelliğin değerinin geçerli olup olmadığını denetler. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Aşağıdaki iki tür yerleşik <xref:System.Windows.Controls.ValidationRule> nesneye sahiptir:  
  
- Bağlama kaynağı özelliğinin güncelleştirilmesi sırasında oluşturulan özel durumları denetler.<xref:System.Windows.Controls.ExceptionValidationRule> Önceki örnekte, `StartPrice` integer türündedir. Kullanıcı tamsayıya dönüştürülemeyen bir değer girdiğinde, bir özel durum oluşturulur ve bağlamanın geçersiz olarak işaretlenmesine neden olur. <xref:System.Windows.Controls.ExceptionValidationRule> Açıkça ayarlamaya yönelik alternatif bir sözdizimi, <xref:System.Windows.Data.Binding> veya <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> <xref:System.Windows.Data.MultiBinding> nesneniz için özelliğini olarak `true` ayarlanmıştır.  
  
- Bir <xref:System.Windows.Controls.DataErrorValidationRule> nesnesi, <xref:System.ComponentModel.IDataErrorInfo> arabirimini uygulayan nesneler tarafından oluşturulan hataları denetler. Bu doğrulama kuralını kullanmayla ilgili bir örnek için bkz <xref:System.Windows.Controls.DataErrorValidationRule>. <xref:System.Windows.Controls.DataErrorValidationRule> Açıkça ayarlamaya yönelik alternatif bir sözdizimi, <xref:System.Windows.Data.Binding> veya <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> <xref:System.Windows.Data.MultiBinding> nesneniz için özelliğini olarak `true` ayarlanmıştır.  
  
 Ayrıca, <xref:System.Windows.Controls.ValidationRule> sınıfından türeterek ve <xref:System.Windows.Controls.ValidationRule.Validate%2A> metodunu uygulayarak kendi doğrulama kuralınızı de oluşturabilirsiniz. Aşağıdaki örnek, [veri bağlama nedir?](#what_is_data_binding) bölümünde *ürün ekleme listesi* "başlangıç tarihi" <xref:System.Windows.Controls.TextBox> tarafından kullanılan kuralı gösterir:  
  
 [!code-csharp[DataBindingLab#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/FutureDateRule.cs#2)]
 [!code-vb[DataBindingLab#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/FutureDateRule.vb#2)]  
  
 *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> , aşağıdaki örnekte gösterildiği gibi bu *futuredadterule*öğesini kullanır:  
  
 [!code-xaml[DataBindingLab#CustomValidation](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#customvalidation)]  
  
 Değer olduğu için <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> , bağlama altyapısının her tuş vuruşunda kaynak değeri güncelleştirdiğine, bu da her tuş vuruşu üzerinde <xref:System.Windows.Data.Binding.ValidationRules%2A> koleksiyondaki her kuralı denetlediği anlamına gelir. <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> Bunu doğrulama Işlemi bölümünde ele aldık.  
  
<a name="invalidation_feedback"></a>   
### <a name="providing-visual-feedback"></a>Görsel geri bildirim sağlama  
 Kullanıcı geçersiz bir değer girerse, uygulamada [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]hata hakkında bazı geri bildirimler sağlamak isteyebilirsiniz. Bu tür geri bildirimde bulunmak için bir yol, <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> ekli özelliği özel <xref:System.Windows.Controls.ControlTemplate>olarak ayarlamaya yönelik bir yoldur. Önceki alt bölümde gösterildiği gibi, *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> adlı bir <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> *validationTemplate*'i kullanır. Aşağıdaki örnek *validationTemplate*tanımını gösterir:  
  
 [!code-xaml[DataBindingLab#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#1)]  
  
 <xref:System.Windows.Controls.AdornedElementPlaceholder> Öğesi, donatılan denetimin yerleştirilmesi gereken yeri belirtir.  
  
 Ayrıca, hata iletisini göstermek <xref:System.Windows.Controls.ToolTip> için de kullanabilirsiniz. Hem *StartDateEntryForm* hem de <xref:System.Windows.Controls.ToolTip> *StartPriceEntryForm*<xref:System.Windows.Controls.TextBox>, hata iletisini görüntüleyen bir oluşturan *textStyleTextBox*stilini kullanır. Aşağıdaki örnek *textStyleTextBox*'ın tanımını gösterir. İliştirilmiş özelliği <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> , bağlı `true` öğenin özelliklerindeki bir veya daha fazla bağlamanın hatalı olması durumunda olur.  
  
 [!code-xaml[DataBindingLab#14](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#14)]  
  
 Özel <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> <xref:System.Windows.Controls.TextBox> ve ile, bir doğrulama hatası olduğunda *StartDateEntryForm* aşağıdaki gibi görünür: <xref:System.Windows.Controls.ToolTip>  
  
 ![Veri bağlama doğrulama hatası](./media/databindingdemo-validation.PNG "DataBindingDemo_Validation")  
  
 Eğer hesabınız <xref:System.Windows.Data.Binding> , doğrulama kurallarına sahipse ancak ilişkili denetimde <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> belirtmezseniz, bir doğrulama hatası olduğunda kullanıcıları bilgilendirmek için varsayılan <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> olarak kullanılır. Varsayılan değer <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> , donatıcı katmanında kırmızı bir kenarlığı tanımlayan bir denetim şablonudur. Varsayılan <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> ve[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ile, *StartPriceEntryForm* <xref:System.Windows.Controls.TextBox> , doğrulama hatası olduğunda aşağıdaki gibi görünür: <xref:System.Windows.Controls.ToolTip>  
  
 ![Veri bağlama doğrulama hatası](./media/databindingdemo-validationdefault.PNG "DataBindingDemo_ValidationDefault")  
  
 Bir iletişim kutusundaki tüm denetimleri doğrulamaya yönelik mantık sağlama hakkında bir örnek için [Iletişim kutularında](../app-development/dialog-boxes-overview.md)özel iletişim kutuları bölümüne bakın.  
  
### <a name="validation-process"></a>Doğrulama Işlemi  
 Doğrulama genellikle bir hedefin değeri bağlama kaynağı özelliğine aktarıldığında oluşur. Bu ve <xref:System.Windows.Data.BindingMode.TwoWay> <xref:System.Windows.Data.BindingMode.OneWayToSource> bağlamalarda gerçekleşir. Yeniden yinelemek için, bir kaynak güncelleştirmesine neden olan kaynak [güncelleştirmelerini tetikleyen](#what_triggers_source_updates) bölümünde açıklandığı <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> gibi, özelliğin değerine bağlıdır.  
  
 *Doğrulama* süreci aşağıda açıklanmaktadır. Bu işlem sırasında herhangi bir zaman doğrulama hatası veya başka bir hata türü oluşursa, işlem durdurulur.  
  
1. Bağlama altyapısı <xref:System.Windows.Controls.ValidationRule> , olarak <xref:System.Windows.Data.Binding> <xref:System.Windows.Controls.ValidationRule.Validate%2A> <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> <xref:System.Windows.Controls.ValidationStep.RawProposedValue> ayarlanmış herhangi bir özel nesne olup olmadığını denetler; bu durumda, bir hata halinde çalıştıktan sonra yöntemi her <xref:System.Windows.Controls.ValidationRule> biri için çağırır. veya hepsi geçene kadar.  
  
2. Bağlama altyapısı, varsa dönüştürücüyü çağırır.  
  
3. Dönüştürücü başarılı olursa bağlama <xref:System.Windows.Controls.ValidationRule> altyapısı, <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> <xref:System.Windows.Data.Binding> <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> Buşekilde<xref:System.Windows.Controls.ValidationRule> ayarlanmış olan herhangi bir özel nesne olup olmadığını denetler; bu durumda, <xref:System.Windows.Controls.ValidationRule.Validate%2A> bir hata <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> veya hepsi geçene kadar bir hatayla çalışana kadar olarak ayarlayın. <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>  
  
4. Bağlama altyapısı, kaynak özelliğini ayarlar.  
  
5. Bağlama <xref:System.Windows.Controls.ValidationRule> altyapısı, için olarak <xref:System.Windows.Controls.ValidationStep.UpdatedValue> ayarlanmış herhangi bir özel nesne <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> olup olmadığını denetler; <xref:System.Windows.Controls.ValidationRule.Validate%2A> bu <xref:System.Windows.Data.Binding>durumda <xref:System.Windows.Controls.ValidationRule> <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> , <xref:System.Windows.Controls.ValidationStep.UpdatedValue> biri bir hata veya hepsi geçene kadar bir hatayla çalışana kadar. Bir <xref:System.Windows.Controls.DataErrorValidationRule> bağlama ile ilişkiliyse <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ve bu, varsayılan <xref:System.Windows.Controls.ValidationStep.UpdatedValue> <xref:System.Windows.Controls.DataErrorValidationRule> olarak ayarlanırsa, bu noktada denetlenir. Bu Ayrıca, <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> `true` kümesi olan bağlamalar işaretli olduğunda da nokta olur.  
  
6. Bağlama <xref:System.Windows.Controls.ValidationRule> altyapısı, için olarak <xref:System.Windows.Controls.ValidationStep.CommittedValue> ayarlanmış herhangi bir özel nesne <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> olup olmadığını denetler; <xref:System.Windows.Controls.ValidationRule.Validate%2A> bu <xref:System.Windows.Data.Binding>durumda <xref:System.Windows.Controls.ValidationRule> <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> , <xref:System.Windows.Controls.ValidationStep.CommittedValue> biri bir hata veya hepsi geçene kadar bir hatayla çalışana kadar.  
  
 Bu işlem boyunca hiçbir zaman geçemezse bağlama altyapısı bir <xref:System.Windows.Controls.ValidationError> nesnesi oluşturur <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> ve onu bağlantılı öğenin koleksiyonuna ekler. <xref:System.Windows.Controls.ValidationRule> Bağlama altyapısı <xref:System.Windows.Controls.ValidationRule> herhangi bir adımda nesneleri çalıştırmadan önce, söz konusu adım sırasında bağlı öğenin <xref:System.Windows.Controls.ValidationError> <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> Ekli özelliğine eklenen her türlü öğeyi kaldırır. Örneğin, bir,, <xref:System.Windows.Controls.ValidationRule> bir <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> sonraki doğrulama <xref:System.Windows.Controls.ValidationError> işlemi <xref:System.Windows.Controls.ValidationStep.UpdatedValue> başarısız olduğunda, bağlama altyapısı, ' a <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ayarlanmış olan herhangi <xref:System.Windows.Controls.ValidationRule> bir kez çağrı yapmadan önce <xref:System.Windows.Controls.ValidationStep.UpdatedValue>.  
  
 Boş olmadığında, öğesinin ekli özelliği olarak `true`ayarlanır. <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> `true` <xref:System.Windows.Controls.Validation.Error?displayProperty=nameWithType> Ayrıca, <xref:System.Windows.Data.Binding> öğesinin özelliği olarak ayarlandıysa, bağlama altyapısı öğesinde ekli olayı başlatır. <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A>  
  
 Ayrıca, her iki yönde de geçerli bir değer aktarımının (hedeften kaynağa veya kaynaktan hedefe) <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> ekli özelliği temizlemiş olduğunu unutmayın.  
  
 Bağlama <xref:System.Windows.Controls.ExceptionValidationRule> onunla ilişkili bir varsa veya <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> özelliği olarak `true` ayarlanmışsa ya da bağlama altyapısı kaynağı ayarlarsa, bağlama altyapısı bir <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>olup olmadığını denetler. Özel durumları işlemek için özel bir işleyici <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> sağlamak üzere geri aramayı kullanma seçeneğiniz vardır. ' Nde <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> belirtilmemişse <xref:System.Windows.Controls.ValidationError> , bağlama motoru özel durum ile bir oluşturur ve onu bağlı öğenin koleksiyonuna ekler. <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> <xref:System.Windows.Data.Binding>  
  
## <a name="debugging-mechanism"></a>Hata ayıklama mekanizması  
 Belirli bir bağlamanın durumu hakkında bilgi <xref:System.Diagnostics.PresentationTraceSources.TraceLevel%2A?displayProperty=nameWithType> almak için bağlama ile ilgili nesne üzerinde iliştirilmiş özelliğini ayarlayabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.DataErrorValidationRule>
- [WPF Sürüm 4.5'teki Yenilikler](../getting-started/whats-new.md)
- [LINQ Sorgusunun Sonuçlarına Bağlama](how-to-bind-to-the-results-of-a-linq-query.md)
- [Veri Bağlama](../advanced/optimizing-performance-data-binding.md)
- [Veri bağlama tanıtımı](https://go.microsoft.com/fwlink/?LinkID=163703)
- [Nasıl Yapılır Konuları](data-binding-how-to-topics.md)
- [ADO.NET Veri Kaynağına Bağlama](how-to-bind-to-an-ado-net-data-source.md)
