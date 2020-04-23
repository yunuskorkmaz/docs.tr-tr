---
title: Veri bağlamaya genel bakış
description: .NET Core için Windows Presentation Foundation ' de projenize ekleyebileceğiniz farklı veri kaynakları hakkında bilgi edinin. Veri kaynakları, dinamik uygulamalar oluşturmak için XAML öğelerine bağlanabilir.
author: thraka
ms.date: 09/19/2019
ms.author: adegeo
dev_langs:
- csharp
- vb
ms.openlocfilehash: 7f17ff094a35c04ba880c87c6966d7d249817516
ms.sourcegitcommit: b75a45f0cfe012b71b45dd9bf723adf32369d40c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2020
ms.locfileid: "82072013"
---
# <a name="data-binding-overview-in-wpf"></a>WPF 'de veri bağlamaya genel bakış

Windows Presentation Foundation (WPF) içindeki veri bağlama, uygulamaların verileri sunmak ve verilerle etkileşim kurmak için basit ve tutarlı bir yol sağlar. Öğeler, .NET nesneleri ve XML biçiminde çeşitli veri kaynaklarından verilere bağlanabilir. <xref:System.Windows.Controls.ContentControl> <xref:System.Windows.Controls.Button> Ve gibi <xref:System.Windows.Controls.ListView>her türlü gibi, tek veri öğelerinin veya veri öğelerinin koleksiyonlarının esnek stillendirilmesini sağlayan yerleşik işlevlere sahiptir. <xref:System.Windows.Controls.ItemsControl> <xref:System.Windows.Controls.ListBox> Sıralama, filtre ve grup görünümleri verilerin üzerine oluşturulabilir.

WPF 'deki veri bağlama işlevselliği, geniş kapsamlı özellikler, verilerin esnek Kullanıcı arabirimi gösterimi ve kullanıcı arabiriminden iş mantığı ayırmayı temizleme dahil olmak üzere geleneksel modellere göre çeşitli avantajlar sunar.

Bu makalede ilk olarak WPF veri bağlama için temel kavramlar ele alınmaktadır ve <xref:System.Windows.Data.Binding> sınıfının kullanımı ve veri bağlamanın diğer özellikleri ele alınmıştır.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="what-is-data-binding"></a>Veri bağlama nedir?

Veri bağlama, uygulama kullanıcı arabirimi ve görüntülediği veriler arasında bağlantı kuran işlemdir. Bağlamanın doğru ayarları varsa ve veriler doğru bildirimleri sağlıyorsa, veriler değerini değiştirdiğinde veriye bağlanan öğeler otomatik olarak değişiklikleri yansıtır. Veri bağlama Ayrıca bir öğedeki verilerin bir dış gösterimi değişirse, temel alınan verilerin değişikliği yansıtacak şekilde otomatik olarak güncelleştirilmesini sağlayabilir. Örneğin, Kullanıcı bir `TextBox` öğesindeki değeri düzenlerse, temel alınan veri değeri bu değişikliği yansıtacak şekilde otomatik olarak güncelleştirilir.

Veri bağlamanın tipik bir kullanımı, sunucu veya yerel yapılandırma verilerini formlara veya diğer kullanıcı arabirimi denetimlerine yerleştirkullanmaktır. WPF 'de, bu kavram çeşitli veri kaynaklarına çok çeşitli özellikler bağlamayı kapsayacak şekilde genişletilir. WPF 'de, öğelerin bağımlılık özellikleri .NET nesnelerine (ADO.NET nesneleri veya Web Hizmetleri ve Web özellikleriyle ilişkili nesneler dahil) ve XML verileriyle bağlanabilir.

Veri bağlama örneği için, bir açık eksiltme öğelerinin listesini görüntüleyen [veri bağlama tanıtımına][data-binding-demo]ait aşağıdaki uygulama kullanıcı arabirimine göz atın.

![Veri bağlama örnek ekran görüntüsü](./media/data-binding-overview/demo.png "DataBinding_DataBindingDemo")

Uygulama, veri bağlamanın aşağıdaki özelliklerini gösterir:

- ListBox 'ın içeriği bir *AuctionItem* nesneleri koleksiyonuna bağlanır. Bir *AuctionItem* nesnesi *Description*, *StartPrice*, *StartDate*, *category*, *SpecialFeatures*gibi özelliklere sahiptir.

- İçinde görüntülenen veriler (*AuctionItem* nesneleri), `ListBox` her öğe için açıklama ve geçerli fiyatın gösterilmesi için şablonlanır. Şablon, kullanılarak oluşturulur <xref:System.Windows.DataTemplate>. Ayrıca, her öğenin görünümü görüntülenmekte olan *AuctionItem* öğesinin *SpecialFeatures* değerine bağlıdır. *AuctionItem* öğesinin *SpecialFeatures* değeri *Color*ise, öğenin mavi kenarlığı vardır. Değer *Vurgulayıcıdır*, öğenin turuncu kenarlığı ve yıldızı vardır. [Veri şablonu](#data-templating) oluşturma bölümü, veri şablonu oluşturma hakkında bilgi sağlar.

- Kullanıcı, verileri `CheckBoxes` belirtilen kullanarak gruplandırabilir, süzebilir veya sıralayabilir. Yukarıdaki görüntüde **kategoriye göre gruplandırma** ve `CheckBoxes` **kategoriye ve tarihe göre sıralama** seçilidir. Verilerin ürün kategorisine göre gruplandığını fark etmiş olabilirsiniz ve kategori adı alfabetik sırada olur. Görüntüden bildirimde bulunulmaları zordur, ancak öğeler her kategori içindeki başlangıç tarihine göre sıralanır. Sıralama, bir *koleksiyon görünümü*kullanılarak yapılır. [Koleksiyonlara bağlama](#binding-to-collections) bölümü koleksiyon görünümlerini tartışır.

- Kullanıcı bir öğe seçtiğinde, seçili öğenin ayrıntılarını <xref:System.Windows.Controls.ContentControl> görüntüler. Bu deneyim, *ana ayrıntı senaryosu*olarak adlandırılır. [Ana ayrıntı senaryosu](#master-detail-binding-scenario) bölümünde bu bağlama türü hakkında bilgi sağlanır.

- *StartDate* özelliğinin türü <xref:System.DateTime>, milisaniye cinsinden saati içeren bir tarih döndürür. Bu uygulamada, daha kısa bir tarih dizesinin görüntülenmesi için özel bir dönüştürücü kullanılmıştır. [Veri dönüştürme](#data-conversion) bölümünde dönüştürücüler hakkında bilgi sağlanır.

Kullanıcı *Ürün Ekle* düğmesini seçtiğinde aşağıdaki form gelir.

![Ürün listeleme sayfası ekle](./media/data-binding-overview/demo-addproductlisting.png "DataBinding_Demo_AddProductListing")

Kullanıcı formdaki alanları düzenleyebilir, kısa veya ayrıntılı önizleme bölmelerini kullanarak ürün listesini önizleyebilir ve yeni ürün listesini eklemeyi seçebilir `Submit` . Mevcut gruplandırma, filtreleme ve sıralama ayarları, yeni giriş için geçerli olacaktır. Bu durumda, yukarıdaki görüntüde girilen öğe, *bilgisayar* kategorisi içinde ikinci öğe olarak görüntülenir.

Bu görüntüde gösterilmez, *başlangıç tarihinde* <xref:System.Windows.Controls.TextBox>verilen doğrulama mantığıdır. Kullanıcı geçersiz bir tarih (geçersiz biçimlendirme veya geçmiş tarih) girerse, kullanıcıya öğesinin yanında bir <xref:System.Windows.Controls.ToolTip> ve kırmızı bir ünlem işaretiyle bildirim gönderilir. <xref:System.Windows.Controls.TextBox> [Veri doğrulama](#data-validation) bölümü, doğrulama mantığının nasıl oluşturulacağını açıklar.

Yukarıda özetlenen veri bağlamasının farklı özelliklerine geçmeden önce, WPF veri bağlamayı anlamak için kritik olan temel kavramları tartışacağız.

## <a name="basic-data-binding-concepts"></a>Temel veri bağlama kavramları

Bağladığınız öğeden ve veri kaynağınızın doğası ne olursa olsun, her bağlama her zaman aşağıdaki şekilde gösterilen modeli izler.

![Temel veri bağlama modelini gösteren diyagram.](./media/data-binding-overview/basic-data-binding-diagram.png)

Şekil gösterdiği gibi, veri bağlama temelde bağlama hedefi ve bağlama kaynağınız arasındaki köprüdir. Şekil aşağıdaki temel WPF veri bağlama kavramlarını göstermektedir:

- Genellikle, her bağlamada dört bileşen vardır:

  - Bağlama hedefi nesnesi.
  - Target özelliği.
  - Bağlama kaynağı.
  - Kullanılacak bağlama kaynağındaki değerin yolu.
  
  > Örneğin `TextBox` , bir öğesinin içeriğini `Employee.Name` özelliğine bağlamak istiyorsanız, hedef nesneniz `TextBox`, hedef özelliği <xref:System.Windows.Controls.TextBox.Text%2A> ise, kullanılacak değer, *adı*ise ve kaynak nesne *çalışan* nesnesidir.

- Target özelliği bir Dependency özelliği olmalıdır. Çoğu <xref:System.Windows.UIElement> Özellik bağımlılık özellikleridir ve salt okuma dışındaki çoğu bağımlılık özellikleri varsayılan olarak veri bağlamayı destekler. (Yalnızca öğesinden <xref:System.Windows.DependencyObject> türetilmiş türler, bağımlılık özelliklerini tanımlayabilir ve tüm <xref:System.Windows.UIElement> türler öğesinden `DependencyObject`türetilir.)

- Şekilde gösterilmese de, bağlama kaynak nesnesinin özel bir .NET nesnesi olmasına sınırlı olmadığından not edilmelidir. WPF veri bağlama, verileri .NET nesneleri ve XML biçiminde destekler. Bazı örnekler sağlamak için bağlama kaynağınız bir, herhangi bir <xref:System.Windows.UIElement>liste nesnesi, ADO.NET veya Web Hizmetleri NESNESI veya XML verilerinizi Içeren bir XmlNode olabilir. Daha fazla bilgi için bkz. [bağlama kaynaklarına genel bakış](../../framework/wpf/data/binding-sources-overview.md).

Bir bağlama oluştururken bağlama hedefini bağlama kaynağı *olarak* bağladığınızda dikkat etmeniz önemlidir. Örneğin, bir <xref:System.Windows.Controls.ListBox> veri bağlama kullanarak bazı temel XML verilerini görüntülüyorsanız, bunu XML verilerine bağlamanız `ListBox` gerekir.

Bir bağlama oluşturmak için <xref:System.Windows.Data.Binding> nesnesini kullanın. Bu makalenin geri kalanında, ile ilişkili kavramların birçoğu ve `Binding` nesnenin bazı özellikleri ve kullanımları açıklanmaktadır.

### <a name="direction-of-the-data-flow"></a>Veri akışının yönü

Önceki şekildeki oka göre gösterildiği gibi, bir bağlamanın veri akışı bağlama kaynağından bağlama kaynağına gidebilir (örneğin, bir Kullanıcı bir `TextBox`' ın değerini değiştirdiğinde kaynak değer değişir) ve/veya bağlama kaynağından bağlama hedefine (örneğin, `TextBox` içeriğiniz bağlama kaynağında değişikliklerle güncelleştirilir) ve bağlama kaynağı doğru bildirimleri sağlar.

Uygulamanızın kullanıcıların verileri değiştirmesini ve kaynak nesnesine geri yaymasını etkinleştirmesini isteyebilirsiniz. Ya da kullanıcıların kaynak verileri güncelleştirmesini etkinleştirmek istemeyebilirsiniz. ' İ ayarlayarak veri akışını kontrol edebilirsiniz <xref:System.Windows.Data.Binding.Mode?displayProperty=nameWithType>.

Bu şekilde farklı veri akışı türleri gösterilmektedir:

![Veri bağlama veri akışı](./media/data-binding-overview/databinding-dataflow.png "DataBinding_DataFlow")

- <xref:System.Windows.Data.BindingMode.OneWay>bağlama, hedef özelliği otomatik olarak güncelleştirmek için kaynak özellikte değişikliklere neden olur, ancak Target özelliğindeki değişiklikler kaynak özelliğine geri yayılmaz. Bu tür bir bağlama, bağlanmakta olan denetimin örtülü olarak salt okunurdur. Örneğin, bir stok şeridi gibi bir kaynağa bağlanabilir veya belki de hedef özellikte, bir tablonun veri bağlantılı arka plan rengi gibi değişiklikler yapmak için hiçbir denetim arabirimi sağlanmamıştır. Hedef özelliğin değişikliklerini izlemeye gerek yoksa <xref:System.Windows.Data.BindingMode.OneWay> bağlama modunun kullanılması <xref:System.Windows.Data.BindingMode.TwoWay> bağlama modunun ek yükünü önler.

- <xref:System.Windows.Data.BindingMode.TwoWay>bağlama, kaynak özellikte veya Target özelliğinde, diğerini otomatik olarak güncelleştirmek için değişikliklere neden olur. Bu tür bir bağlama, düzenlenebilir formlar veya diğer tam etkileşimli kullanıcı arabirimi senaryoları için uygundur. Çoğu özellik varsayılan olarak <xref:System.Windows.Data.BindingMode.OneWay> bağlamaya, ancak bazı bağımlılık özelliklerine (genellikle <xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType> ve [onay kutusu](xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked) gibi kullanıcı tarafından düzenlenebilir denetimlerin özellikleri). <xref:System.Windows.Data.BindingMode.TwoWay> Bağımlılık özelliğinin tek yönlü veya iki yönlü olarak bağlama özelliğinin, özelliği olan <xref:System.Windows.DependencyProperty.GetMetadata%2A?displayProperty=nameWithType> özellik meta verilerini almak ve sonra <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A?displayProperty=nameWithType> özelliğin Boole değerini denetlemesi için programlı bir yoldur.

- <xref:System.Windows.Data.BindingMode.OneWayToSource>, <xref:System.Windows.Data.BindingMode.OneWay> bağlamanın tersidir; hedef özelliği değiştiğinde kaynak özelliğini güncelleştirir. Tek örnek senaryo yalnızca kaynak değeri kullanıcı arabiriminden yeniden değerlendirmeniz gerektiğinde olur.

- Şekil, kaynak özelliğin hedef özelliği <xref:System.Windows.Data.BindingMode.OneTime> başlatmasına, ancak sonraki değişiklikleri yaymasına neden olan bağlamadır. Veri bağlamı değişirse veya veri bağlamındaki nesne değişirse değişiklik, hedef *özellikte yansıtılmaz.* Geçerli durumun bir anlık görüntüsü uygunsa veya veriler gerçekten statikse, bu tür bir bağlama uygundur. Hedef özelliği bir kaynak özelliğinden bir değer ile başlatmak istiyorsanız ve veri bağlamı önceden bilinmiyorsa, bu tür bağlama de kullanışlıdır. Bu mod aslında kaynak değerin değişmemesi durumunda <xref:System.Windows.Data.BindingMode.OneWay> daha iyi performans sağlayan daha basit bir bağlama biçimidir.

Kaynak değişiklikleri (ve <xref:System.Windows.Data.BindingMode.OneWay> <xref:System.Windows.Data.BindingMode.TwoWay> bağlamaları için geçerlidir) algılamak için, kaynak gibi uygun bir özellik değişikliği bildirim mekanizması gerçekleştirmelidir. <xref:System.ComponentModel.INotifyPropertyChanged> Bkz. nasıl yapılır: <xref:System.ComponentModel.INotifyPropertyChanged> uygulama örneği için [özellik değişikliği bildirimi uygulama](../../framework/wpf/data/how-to-implement-property-change-notification.md) .

<xref:System.Windows.Data.Binding.Mode?displayProperty=nameWithType> Özelliği bağlama modları hakkında daha fazla bilgi ve bir bağlamanın yönlerinin nasıl belirtilbir örneğini sağlar.

### <a name="what-triggers-source-updates"></a>Hangi kaynak güncelleştirmelerini tetikler

Hedef özelliğindeki değişiklikler <xref:System.Windows.Data.BindingMode.TwoWay> için <xref:System.Windows.Data.BindingMode.OneWayToSource> veya dinleyen bağlamalar, kaynağı güncelleştirme olarak bilinen, kaynak olarak kaynağa geri yayılır. Örneğin, temel alınan kaynak değerini değiştirmek için bir TextBox metnini düzenleyebilirsiniz.

Ancak, metin düzenlenirken veya metni düzenledikten sonra Denetim odağı kaybetirken kaynak değer güncelleştirilir mi? Özelliği <xref:System.Windows.Data.Binding.UpdateSourceTrigger?displayProperty=nameWithType> , kaynağın güncelleştirilmesini neyin tetikleyeceğini belirler. Aşağıdaki şekildeki doğru okların noktaları, <xref:System.Windows.Data.Binding.UpdateSourceTrigger?displayProperty=nameWithType> özelliğin rolünü gösterir.

![UpdateSourceTrigger özelliğinin rolünü gösteren diyagram.](./media/data-binding-overview/data-binding-updatesource-trigger.png)

`UpdateSourceTrigger` Değer <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged?displayProperty=nameWithType>ise, sağ ok veya <xref:System.Windows.Data.BindingMode.TwoWay> <xref:System.Windows.Data.BindingMode.OneWayToSource> bağlamalar tarafından işaret edilen değer, hedef özelliği değiştikçe hemen güncellenir. Ancak `UpdateSourceTrigger` değer ise <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>, bu değer yalnızca Target özelliği odağı kaybettiğinde yeni değerle güncelleştirilir.

<xref:System.Windows.Data.Binding.Mode%2A> Özelliğe benzer şekilde, farklı bağımlılık özellikleri farklı varsayılan <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> değerlere sahiptir. Bağımlılık özelliklerinin çoğu için varsayılan değer, <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> `TextBox.Text` özelliğin varsayılan değeri olan ' dir. <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> `PropertyChanged`kaynak güncelleştirmelerinin genellikle Target özelliği değiştiğinde meydana gelir. Anında değişiklikler, onay kutuları ve diğer basit denetimler için uygundur. Bununla birlikte, metin alanları için, her tuş vuruşundan sonra güncelleştirme performansı azaledebilir ve kullanıcıyı yeni değere işlemeden önce, geri alma ve yazma hatalarını çözme fırsatını reddeder.

Bağımlılık özelliğinin <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> varsayılan değerini bulma hakkında bilgi için bkz. Özellik sayfası.

Aşağıdaki tabloda, <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> <xref:System.Windows.Controls.TextBox> örnek olarak kullanılarak her bir değer için örnek bir senaryo verilmiştir.

| UpdateSourceTrigger değeri | Kaynak değer güncelleştirildiği zaman | TextBox için örnek senaryo |
| ------------------------- | ---------------------------------- | ---------------------------- |
| `LostFocus`(için <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>varsayılan) | TextBox denetimi odağı kaybettiğinde. | Doğrulama mantığı ile ilişkili bir metin kutusu (aşağıdaki [veri doğrulamasına](#data-validation) bakın). |
| `PropertyChanged` | Öğesine yazarken <xref:System.Windows.Controls.TextBox>. | Bir sohbet odası penceresinde TextBox denetimleri. |
| `Explicit` | Uygulama çağırdığında <xref:System.Windows.Data.BindingExpression.UpdateSource%2A>. | Düzenlenebilir bir formda metin kutusu denetimleri (kaynak değerlerini yalnızca Kullanıcı Gönder düğmesine tıkladığında güncelleştirir). |

Bir örnek için bkz. [nasıl yapılır: denetim kutusu metninde kaynağı ne zaman güncelleştirin](../../framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md).

## <a name="creating-a-binding"></a>Bağlama oluşturma

Önceki bölümlerde ele alınan kavramların bazılarını yeniden oluşturmak için, <xref:System.Windows.Data.Binding> nesnesini kullanarak bir bağlama kurarsınız ve her bağlamada genellikle dört bileşen vardır: bağlama hedefi, hedef özellik, bağlama kaynağı ve kullanılacak kaynak değer yolu. Bu bölümde bir bağlamanın nasıl ayarlanacağı açıklanır.

Bağlama kaynak nesnesinin, *SDKSample* ad alanında tanımlanan *MyData* adlı bir sınıf olduğu aşağıdaki örneği göz önünde bulundurun. Tanıtım amacıyla, *MyData* değeri "Red" olarak ayarlanmış *ColorName* adlı bir String özelliğine sahiptir. Bu nedenle, bu örnek kırmızı bir arka plana sahip bir düğme oluşturur.

[!code-xaml[BindNonTextProperty](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/AutoConvertPropertyToColor.xaml#BindAutoConvertColor)]

Bağlama bildirimi sözdizimi hakkında daha fazla bilgi ve kod içinde bağlama ayarlama örnekleri için bkz. [bağlama bildirimlerine genel bakış](../../framework/wpf/data/binding-declarations-overview.md).

Bu örneği temel diyagramımızı uygulıyoruz, sonuçta elde edilen şekil aşağıdaki gibi görünür. Bu şekilde, arka <xref:System.Windows.Data.BindingMode.OneWay> plan özelliği varsayılan olarak bağlamayı desteklediğinden <xref:System.Windows.Data.BindingMode.OneWay> bu şekilde bir bağlama açıklanmaktadır.

![Veri bağlama arka plan özelliğini gösteren diyagram.](./media/data-binding-overview/data-binding-button-background-example.png)

Bu bağlamanın, bir <xref:System.Windows.Controls.Control.Background%2A> Özellik türü <xref:System.Windows.Media.Brush>olsa da, *ColorName* özelliği String türünde olmasına rağmen neden bu bağlamanın işe yaradığına merak ediyor olabilirsiniz. Bu bağlama, [veri dönüştürme](#data-conversion) bölümünde ele alınan varsayılan tür dönüşümünü kullanır.

### <a name="specifying-the-binding-source"></a>Bağlama kaynağını belirtme

Önceki örnekte, bağlama kaynağının [DockPanel. DataContext](xref:System.Windows.FrameworkElement.DataContext) özelliği ayarlanarak belirtildiğine dikkat edin. Sonra değeri, üst öğesi olan öğesinden <xref:System.Windows.Controls.DockPanel>devralır. <xref:System.Windows.FrameworkElement.DataContext%2A> <xref:System.Windows.Controls.Button> Yeniden yinelemek için bağlama kaynak nesnesi, bir bağlamanın gerekli dört bileşenlerinden biridir. Bu nedenle, bağlama kaynak nesnesi belirtilmeksizin bağlama hiçbir şey yapmaz.

Bağlama kaynak nesnesini belirtmek için çeşitli yollar vardır. Aynı kaynağa <xref:System.Windows.FrameworkElement.DataContext%2A> birden çok özellik bağlarken bir üst öğe üzerinde özelliğini kullanmak faydalıdır. Ancak, bazen bağlama kaynağını tek tek bağlama bildirimlerinde belirtmek daha uygun olabilir. Önceki örnekte, <xref:System.Windows.FrameworkElement.DataContext%2A> özelliğini kullanmak yerine, aşağıdaki örnekte olduğu gibi, özelliği doğrudan düğmenin bağlama bildiriminde ayarlayarak <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> bağlama kaynağını belirtebilirsiniz.

[!code-xaml[BindNonTextPropertyCompactBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/AutoConvertPropertyToColor.xaml#BindAutoConvertColorCompactBinding)]

<xref:System.Windows.FrameworkElement.DataContext%2A> Bir öğedeki özelliği doğrudan ayarlama, <xref:System.Windows.FrameworkElement.DataContext%2A> değeri bir üst öğeden devralma (örneğin, birinci örnekteki düğme gibi) ve bağlama üzerindeki <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> özelliği ayarlayarak bağlama kaynağını açıkça belirtme (örneğin, son örnek düğme gibi), bağlama kaynağını belirtmek için <xref:System.Windows.Data.Binding.ElementName?displayProperty=nameWithType> özelliğini veya <xref:System.Windows.Data.Binding.RelativeSource?displayProperty=nameWithType> özelliğini de kullanabilirsiniz. <xref:System.Windows.Data.Binding.ElementName%2A> Özelliği, bir düğmenin genişliğini ayarlamak için kaydırıcı kullanırken olduğu gibi, uygulamanızdaki diğer öğelere bağlarken faydalıdır. <xref:System.Windows.Data.Binding.RelativeSource%2A> Özelliği, <xref:System.Windows.Controls.ControlTemplate> veya içinde bağlama belirtildiğinde faydalıdır <xref:System.Windows.Style>. Daha fazla bilgi için bkz. [nasıl yapılır: bağlama kaynağını belirtme](../../framework/wpf/data/how-to-specify-the-binding-source.md).

### <a name="specifying-the-path-to-the-value"></a>Değerin yolunu belirtme

Bağlama kaynağınız bir nesnedir, bağlamanız için kullanılacak değeri belirtmek <xref:System.Windows.Data.Binding.Path?displayProperty=nameWithType> için özelliğini kullanın. XML verilerine bağlıyorsanız, değerini belirtmek için <xref:System.Windows.Data.Binding.XPath?displayProperty=nameWithType> özelliğini kullanın. Bazı durumlarda, verileriniz XML olduğunda bile <xref:System.Windows.Data.Binding.Path%2A> özelliği kullanmak için geçerli olabilir. Örneğin, döndürülen bir XmlNode 'un Name özelliğine (bir XPath sorgusunun sonucu olarak) erişmek istiyorsanız özelliği ek <xref:System.Windows.Data.Binding.Path%2A> <xref:System.Windows.Data.Binding.XPath%2A> olarak özelliğini kullanmanız gerekir.

Daha fazla bilgi için bkz. <xref:System.Windows.Data.Binding.Path%2A> ve <xref:System.Windows.Data.Binding.XPath%2A> özellikleri.

' Nin, kullanılacak değere, <xref:System.Windows.Data.Binding.Path%2A> bir bağlamanın dört gerekli bileşenlerinden biri olduğunu vurguladığımızda, bir nesnenin tamamına bağlamak istediğiniz senaryolarda, kullanılacak değer bağlanacak kaynak nesneyle aynı olacaktır. Bu durumlarda, bir <xref:System.Windows.Data.Binding.Path%2A>belirtmemelidir. Aşağıdaki örneği inceleyin.

[!code-xaml[EmptyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/EmptyBinding.xaml#EmptyBinding)]

Yukarıdaki örnek, boş bağlama söz dizimini kullanır: {Binding}. Bu durumda, bir üst <xref:System.Windows.Controls.ListBox> DockPanel öğesinden DataContext 'i devralır (Bu örnekte gösterilmez). Yol belirtilmediğinde, varsayılan olarak nesnenin tamamına bağlanır. Diğer bir deyişle, bu örnekte, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliği nesnenin tamamına bağlamamız nedeniyle yol kalmadı. (Ayrıntılı bir tartışma için [koleksiyonlara bağlama](#binding-to-collections) bölümüne bakın.)

Bir koleksiyona bağlama dışında, bu senaryo aynı zamanda yalnızca bir nesnenin tek bir özelliği yerine bir nesnenin tamamına bağlamak istediğinizde de yararlıdır. Örneğin, kaynak nesneniz tür <xref:System.String>ise, yalnızca dizenin kendisini bağlamak isteyebilirsiniz. Diğer bir yaygın senaryo, bir öğeyi birkaç özelliği olan bir nesneye bağlamak istemizin olur.

Verilerin, bağlantılı hedef özelliği için anlamlı olması için özel mantık uygulamanız gerekebilir. Özel mantık, varsayılan tür dönüştürmesi yoksa özel bir dönüştürücü biçiminde olabilir. Dönüştürücüler hakkında bilgi için bkz. [veri dönüştürme](#data-conversion) .

### <a name="binding-and-bindingexpression"></a>Bağlama ve BindingExpression

Veri bağlamanın diğer özelliklerine ve kullanımlarına geçmeden önce <xref:System.Windows.Data.BindingExpression> sınıfı tanıtmak yararlı olur. Önceki bölümlerde gördüğünüz gibi, <xref:System.Windows.Data.Binding> sınıfı bağlama bildirimi için üst düzey sınıftır; bir bağlamanın özelliklerini belirtmenize imkan tanıyan birçok özellik sağlar. İlişkili bir sınıf, <xref:System.Windows.Data.BindingExpression>kaynak ve hedef arasındaki bağlantıyı tutan temel nesnedir. Bağlama, birkaç bağlama ifadesi genelinde paylaşılabilen tüm bilgileri içerir. <xref:System.Windows.Data.BindingExpression> , <xref:System.Windows.Data.Binding>Paylaşılamayan bir örnek ifadesidir ve öğesinin tüm örnek bilgilerini içerir.

Aşağıdaki örneği, burada `myDataObject` `MyData` sınıfının bir örneği, `myBinding` kaynak <xref:System.Windows.Data.Binding> nesne ise ve `MyData` adlı `MyDataProperty`bir dize özelliği içeren tanımlanmış bir sınıftır. Bu örnek, bir örneği `myText` <xref:System.Windows.Controls.TextBlock>olan öğesinin metin içeriğini öğesine `MyDataProperty`bağlar.

[!code-csharp[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/ManualBinding.cs#CodeOnlyBinding)]
[!code-vb[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/ManualBinding.vb#CodeOnlyBinding)]

Diğer bağlamaları oluşturmak için aynı *myBinding* nesnesi kullanabilirsiniz. Örneğin, bir onay kutusunun metin içeriğini *MyDataProperty*olarak bağlamak Için *myBinding* nesnesini kullanabilirsiniz. Bu senaryoda, <xref:System.Windows.Data.BindingExpression> *myBinding* nesnesini paylaşan iki örnek olacaktır.

Bir <xref:System.Windows.Data.BindingExpression> nesne, veriye bağlı bir <xref:System.Windows.Data.BindingOperations.GetBindingExpression%2A> nesne çağırarak döndürülür. Aşağıdaki makalelerde, <xref:System.Windows.Data.BindingExpression> sınıfının kullanımları gösterilmektedir:

- [Bağımlı hedef özelliğinden bağlama nesnesi alma](../../framework/wpf/data/how-to-get-the-binding-object-from-a-bound-target-property.md)

- [TextBox metni kaynağı güncelleştirdiğinde denetleme](../../framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md)

## <a name="data-conversion"></a>Veri dönüştürme

[Bağlama oluşturma](#creating-a-binding) bölümünde düğme kırmızıdır çünkü <xref:System.Windows.Controls.Control.Background%2A> özelliği "Red" değerine sahip bir dize özelliğine bağımlıdır. Bu dize değeri, dize değerini bir <xref:System.Windows.Media.Brush> <xref:System.Windows.Media.Brush>olarak dönüştürmek için türde bir tür dönüştürücüsü bulunduğundan geçerlidir.

Bu bilgileri [bağlama oluşturma](#creating-a-binding) bölümünde olduğu şekle ekleme bu şekilde görünür.

![Veri bağlama varsayılan özelliğini gösteren diyagram.](./media/data-binding-overview/data-binding-button-default-conversion.png)

Ancak, Binding kaynak nesnenizin dize türünde bir özelliği olması yerine ne tür <xref:System.Windows.Media.Color>bir *Color* özelliği vardır? Bu durumda, bağlamanın çalışması için öncelikle *Color* özelliğinin değerini <xref:System.Windows.Controls.Control.Background%2A> özelliğin kabul ettiği bir şeye dönüştürmeniz gerekir. Aşağıdaki örnekte olduğu gibi, <xref:System.Windows.Data.IValueConverter> arabirimini uygulayarak özel bir dönüştürücü oluşturmanız gerekir.

[!code-csharp[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/ColorBrushConverter.cs#ColorBrushConverter)]
[!code-vb[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/ColorBrushConverter.vb#ColorBrushConverter)]

Daha fazla bilgi edinmek için bkz. <xref:System.Windows.Data.IValueConverter>.

Artık özel dönüştürücü varsayılan dönüştürme yerine kullanılır ve diyagramımız şuna benzer.

![Veri bağlama özel dönüştürücüsünü gösteren diyagram.](./media/data-binding-overview/data-binding-converter-color-example.png)

Yeniden yinelemek için, bağlanmakta olan türde bulunan tür dönüştürücüler nedeniyle varsayılan dönüşümler kullanılabilir olabilir. Bu davranış, hedefte hangi tür dönüştürücülerinin kullanılabilir olduğuna bağlı olarak değişir. Şüpheniz varsa, kendi dönüştürücüyü oluşturun.

Aşağıda, bir veri dönüştürücüsünü uygulamak açısından anlamlı olduğu bazı tipik senaryolar verilmiştir:

- Verileriniz kültüre bağlı olarak farklı şekilde görüntülenmelidir. Örneğin, belirli bir kültürde kullanılan kurallara göre bir para birimi dönüştürücü veya takvim tarih/saat Dönüştürücüsü uygulamak isteyebilirsiniz.

- Kullanılan veriler bir özelliğin metin değerini değiştirmek zorunda değildir, ancak bunun yerine bir görüntünün kaynağı veya görüntü metninin rengi ya da stili gibi başka bir değerin değiştirilmesini amaçlanır. Dönüştürücüler, bir metin alanını tablo hücresinin arka plan özelliğine bağlama gibi, uygun gibi görünmeyebilir bir özelliğin bağlamasını dönüştürerek bu örnekte kullanılabilir.

- Denetimlerin birden fazla denetimi veya birden çok özelliği aynı verilere bağlıydı. Bu durumda, birincil bağlama yalnızca metni görüntüleyebilir, diğer bağlamalar ise belirli görüntüleme sorunlarını işler ancak yine de kaynak bilgilerle aynı bağlamayı kullanır.

- Target özelliği, bir bağlama koleksiyonu içerir <xref:System.Windows.Data.MultiBinding>. İçin <xref:System.Windows.Data.MultiBinding>, bağlamaların değerlerinden son <xref:System.Windows.Data.IMultiValueConverter> bir değer üretmek için özel kullanırsınız. Örneğin, aynı veya farklı bağlama kaynak nesnelerinden değer olabilen kırmızı, mavi ve yeşil değerlerden renk hesaplanabilir. Örnekler <xref:System.Windows.Data.MultiBinding> ve bilgiler için bkz..

## <a name="binding-to-collections"></a>Koleksiyonlara bağlama

Bağlama kaynak nesnesi, özellikleri veri içeren tek bir nesne olarak ya da genellikle birlikte gruplanmış çok biçimli nesnelerin veri koleksiyonu olarak (bir veritabanının bir sorgusunun sonucu gibi) değerlendirilir. Şimdiye kadar yalnızca tek nesnelere bağlamayı tartıştık. Ancak, bir veri koleksiyonuna bağlama yaygın bir senaryodur. Örneğin, yaygın bir senaryo <xref:System.Windows.Controls.ItemsControl> , veya <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.ListView> <xref:System.Windows.Controls.TreeView> gibi bir veri koleksiyonunu ( [veri bağlama nedir](#what-is-data-binding) bölümünde gösterilen uygulamadaki gibi) göstermek için kullanılır.

Neyse ki temel diyagramımız hala geçerli olur. Bir koleksiyona bağlıyorsanız <xref:System.Windows.Controls.ItemsControl> , diyagram şuna benzer şekilde görünür.

![Veri bağlama ItemControl nesnesini gösteren diyagram.](./media/data-binding-overview/data-binding-itemscontrol.png)

Bu diyagramda gösterildiği gibi, bir <xref:System.Windows.Controls.ItemsControl> koleksiyon nesnesine bağlamak için <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A?displayProperty=nameWithType> özelliği kullanılacak özelliktir. ' Nin içeriği `ItemsSource` olarak düşünebilirsiniz <xref:System.Windows.Controls.ItemsControl>. Bağlama, <xref:System.Windows.Data.BindingMode.OneWay> `ItemsSource` özelliğin varsayılan olarak bağlamayı desteklediğinden `OneWay` kaynaklanır.

### <a name="how-to-implement-collections"></a>Koleksiyonları uygulama

<xref:System.Collections.IEnumerable> Arabirimini uygulayan herhangi bir koleksiyonun üzerinde listeleme yapabilirsiniz. Bununla birlikte, koleksiyondaki eklemelerin veya silinmelerin Kullanıcı arabirimini otomatik olarak güncelleştirmeleri için dinamik bağlamaları ayarlamak için koleksiyonun <xref:System.Collections.Specialized.INotifyCollectionChanged> arabirimini uygulaması gerekir. Bu arabirim, temeldeki koleksiyon değiştiğinde oluşturulması gereken bir olay gösterir.

WPF, <xref:System.Collections.Specialized.INotifyCollectionChanged> arabirimi <xref:System.Collections.ObjectModel.ObservableCollection%601> kullanıma sunan bir veri koleksiyonunun yerleşik bir uygulama olan sınıfını sağlar. Veri değerlerinin Kaynak nesnelerden hedeflere aktarılmasını tam olarak desteklemek için, koleksiyonunuzdaki bağlanabilir özellikleri destekleyen her nesnenin de <xref:System.ComponentModel.INotifyPropertyChanged> arabirimini uygulaması gerekir. Daha fazla bilgi için bkz. [bağlama kaynaklarına genel bakış](../../framework/wpf/data/binding-sources-overview.md).

Kendi koleksiyonunuzu uygulamadan önce <xref:System.Collections.ObjectModel.ObservableCollection%601> ,, ve <xref:System.Collections.Generic.List%601> <xref:System.Collections.ObjectModel.Collection%601> <xref:System.ComponentModel.BindingList%601>gibi var olan koleksiyon sınıflarından birini ya da birçok başka konuda kullanmayı düşünün. Gelişmiş bir senaryonuz varsa ve kendi koleksiyonunuzu uygulamak istiyorsanız <xref:System.Collections.IList>, dizin tarafından ayrı ayrı erişilebilen nesnelerin genel olmayan bir koleksiyonunu sağlayan öğesini kullanmayı düşünün ve bu sayede en iyi performansı elde edebilirsiniz.

### <a name="collection-views"></a>Koleksiyon görünümleri

<xref:System.Windows.Controls.ItemsControl> Bir veri koleksiyonu bağladıktan sonra verileri sıralamak, filtrelemek veya gruplandırmak isteyebilirsiniz. Bunu yapmak için, <xref:System.ComponentModel.ICollectionView> arabirimini uygulayan sınıflar olan koleksiyon görünümlerini kullanırsınız.

#### <a name="what-are-collection-views"></a>Koleksiyon görünümleri nelerdir?

Koleksiyon görünümü, temel kaynak koleksiyonun kendisini değiştirmek zorunda kalmadan sıralama, filtre ve grup sorgularına göre kaynak koleksiyonunu gezinmenize ve görüntülemenize olanak tanıyan bir bağlama kaynak koleksiyonunun en üstünde yer alan bir katmandır. Koleksiyon görünümü Ayrıca koleksiyondaki geçerli öğe için bir işaretçi tutar. Kaynak koleksiyon <xref:System.Collections.Specialized.INotifyCollectionChanged> arabirimini uygularsa, <xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged> olay tarafından oluşturulan değişiklikler görünümlere yayılır.

Görünümler temeldeki kaynak koleksiyonlarını değiştirmediğinden, her kaynak koleksiyonda ilişkili birden fazla görünüm bulunabilir. Örneğin, *görev* nesneleri koleksiyonunuz olabilir. Görünümlerin kullanımı ile aynı verileri farklı yollarla görüntüleyebilirsiniz. Örneğin, sayfanızın sol tarafında önceliğe göre sıralanmış görevleri ve sağ tarafa alana göre gruplanmış olarak göstermek isteyebilirsiniz.

#### <a name="how-to-create-a-view"></a>Görünüm oluşturma

Bir görünüm oluşturmanın ve kullanmanın bir yolu, doğrudan görünüm nesnesini oluşturmak ve bunu bağlama kaynağı olarak kullanmaktır. Örneğin, [veri bağlama tanıtımı bölümünde gösterilen](#what-is-data-binding) [veri bağlama tanıtım][data-binding-demo] uygulamasını göz önünde bulundurun. Uygulama, veri toplamayı doğrudan değil, <xref:System.Windows.Controls.ListBox> veri koleksiyonu üzerinden bir görünüme bağlamalara uygulanır. Aşağıdaki örnek, [veri bağlama tanıtım][data-binding-demo] uygulamasından ayıklanır. <xref:System.Windows.Data.CollectionViewSource> Sınıfı, öğesinden <xref:System.Windows.Data.CollectionView>devralan bir sınıfın xaml ara sunucusu. Bu örnekte, <xref:System.Windows.Data.CollectionViewSource.Source%2A> görünümün geçerli uygulama nesnesinin *AuctionItems* koleksiyonuna (türü <xref:System.Collections.ObjectModel.ObservableCollection%601>) bağlanması gerekir.

[!code-xaml[CollectionView](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#CollectionView)]

*ListingDataView* kaynağı daha sonra uygulamadaki öğeler için bağlama kaynağı olarak görev yapar (örneğin, <xref:System.Windows.Controls.ListBox>).

[!code-xaml[ListBoxCollectionView](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#ListBoxCollectionView)]

Aynı koleksiyon için başka bir görünüm oluşturmak üzere başka <xref:System.Windows.Data.CollectionViewSource> bir örnek oluşturabilir ve buna farklı `x:Key` bir ad verebilirsiniz.

Aşağıdaki tabloda, varsayılan koleksiyon görünümü olarak veya kaynak koleksiyon türüne <xref:System.Windows.Data.CollectionViewSource> göre hangi görünüm verisi türlerinin oluşturulduğu gösterilmektedir.

| Kaynak koleksiyon türü                    | Koleksiyon görünüm türü | Notlar |
| ----------------------------------------- | -------------------- | ----- |
| <xref:System.Collections.IEnumerable>     | Temelinde bir iç tür<xref:System.Windows.Data.CollectionView> | Öğeler gruplandırılamıyor. |
| <xref:System.Collections.IList>           | <xref:System.Windows.Data.ListCollectionView> | En hızlı. |
| <xref:System.ComponentModel.IBindingList> | <xref:System.Windows.Data.BindingListCollectionView> | |

#### <a name="using-a-default-view"></a>Varsayılan görünüm kullanma

Bir koleksiyon görünümünü bağlama kaynağı olarak belirtme, koleksiyon görünümü oluşturmanın ve kullanmanın bir yoludur. WPF ayrıca, bağlama kaynağı olarak kullanılan her koleksiyon için varsayılan bir koleksiyon görünümü oluşturur. Doğrudan bir koleksiyona bağlarsanız, WPF varsayılan görünümüne bağlanır. Bu varsayılan görünüm, aynı koleksiyondaki tüm bağlamalar tarafından paylaşılır. bu nedenle, bir bağlantılı denetim veya kodla (sıralama ya da geçerli öğe işaretçisine yapılan bir değişiklik gibi) bir varsayılan görünümde yapılan değişiklik, aynı koleksiyona yapılan diğer tüm bağlamalara yansıtılır.

Varsayılan görünümü almak için <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> yöntemini kullanırsınız. Bir örnek için bkz. [veri koleksiyonunun varsayılan görünümünü edinme](../../framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md).

#### <a name="collection-views-with-adonet-datatables"></a>ADO.NET DataTable ile koleksiyon görünümleri

Performansı artırmak için, ADO.NET <xref:System.Data.DataTable> veya <xref:System.Data.DataView> nesneleri <xref:System.Data.DataView>için koleksiyon görünümleri, sıralama ve filtreleme ile veri kaynağının tüm koleksiyon görünümlerinde paylaşılmasına neden olur. Her koleksiyon görünümünün bağımsız olarak sıralanmasını ve filtrelemesine olanak tanımak için her koleksiyon görünümünü kendi <xref:System.Data.DataView> nesnesiyle başlatın.

#### <a name="sorting"></a>Sıralama

Daha önce bahsedildiği gibi, görünümler bir koleksiyona sıralama düzeni uygulayabilir. Temel koleksiyonda olduğu gibi, verileriniz ilgili ve kendine özgü bir sıraya sahip olabilir veya olmayabilir. Koleksiyon üzerindeki görünüm, sağladığınız karşılaştırma ölçütlerine göre bir sipariş veya varsayılan sırayı değiştirmenize olanak sağlar. Verilerin istemci tabanlı bir görünümü olduğundan, yaygın olarak kullanılan bir senaryo, kullanıcının sütun için karşılık gelen tablo verilerinin sütunlarını sütuna karşılık geldiği bir değere göre sıralamak isteyebilir. Görünümleri kullanarak, bu kullanıcı odaklı sıralama, temel koleksiyonda herhangi bir değişiklik yapılmadan veya koleksiyon içeriğini yeniden sorgulamak zorunda kalmadan uygulanabilir. Bir örnek için bkz. [bir başlık tıklandığında GridView sütununu sıralama](../../framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).

Aşağıdaki örnek, [veri bağlama nedir](#what-is-data-binding) bölümünde uygulama kullanıcı arabirimindeki "kategoriye göre sıralama ve tarihe <xref:System.Windows.Controls.CheckBox> göre sırala" öğesinin sıralama mantığını gösterir.

[!code-csharp[AddSortChecked](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#AddSortChecked)]
[!code-vb[AddSortChecked](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#AddSortChecked)]

#### <a name="filtering"></a>Filtreleme

Görünümler bir koleksiyona bir filtre de uygulayabilir, böylece görünüm tam koleksiyonun yalnızca belirli bir alt kümesini gösterir. Verilerdeki bir koşula filtre ekleyebilirsiniz. Örneğin, [veri bağlama nedir](#what-is-data-binding) bölümünde uygulama tarafından yapıldığı gibi, "yalnızca Barkazancı göster" <xref:System.Windows.Controls.CheckBox> , maliyet $25 veya daha fazla olan öğeleri filtrelemek için mantık içerir. Aşağıdaki kod, seçildiğinde, *ShowOnlyBargainsFilter* öğesini <xref:System.Windows.Data.CollectionViewSource.Filter> olay işleyicisi <xref:System.Windows.Controls.CheckBox> olarak ayarlamak için yürütülür.

[!code-csharp[ListingViewFilter](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#ListingViewFilter)]
[!code-vb[ListingViewFilter](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#ListingViewFilter)]

*ShowOnlyBargainsFilter* olay işleyicisi aşağıdaki uygulamaya sahiptir.

[!code-csharp[FilterEvent](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#FilterEvent)]
[!code-vb[FilterEvent](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#FilterEvent)]

Yerine doğrudan <xref:System.Windows.Data.CollectionView> sınıflardan birini kullanıyorsanız <xref:System.Windows.Data.CollectionViewSource>, bir geri çağırma belirtmek için <xref:System.Windows.Data.CollectionView.Filter%2A> özelliğini kullanın. Bir örnek için bkz. [bir görünümdeki verileri filtreleme](../../framework/wpf/data/how-to-filter-data-in-a-view.md).

#### <a name="grouping"></a>Gruplandırma

Bir <xref:System.Collections.IEnumerable> koleksiyonu görüntüleyen iç sınıf hariç, tüm koleksiyon görünümleri, kullanıcının koleksiyon görünümündeki koleksiyonu mantıksal gruplar halinde bölümlamasına olanak sağlayan *gruplandırmayı*destekler. Gruplar, kullanıcının grupların bir listesini sağladığı veya örtük olarak, grupların verilere göre dinamik olarak oluşturulduğu açık olabilir.

Aşağıdaki örnekte, "kategoriye göre gruplandırma" <xref:System.Windows.Controls.CheckBox>mantığı gösterilmektedir.

[!code-csharp[ListingGroupCheck](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#ListingGroupCheck)]
[!code-vb[ListingGroupCheck](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#ListingGroupCheck)]

Başka bir gruplandırma örneği için bkz. [GridView uygulayan bir ListView Içindeki öğeleri gruplandırma](../../framework/wpf/controls/how-to-group-items-in-a-listview-that-implements-a-gridview.md).

#### <a name="current-item-pointers"></a>Geçerli öğe işaretçileri

Görünümler, geçerli bir öğe kavramını da destekler. Bir koleksiyon görünümündeki nesneler arasında gezinebilirsiniz. Gezindiğinizde, koleksiyonda belirli bir konumda bulunan nesneyi almanıza izin veren bir öğe işaretçisini taşıyor olursunuz. Bir örnek için bkz. [Data CollectionView içindeki nesneler arasında gezinme](../../framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).

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

#### <a name="master-detail-binding-scenario"></a>Ana-ayrıntı bağlama senaryosu

Geçerli bir öğe kavramı yalnızca bir koleksiyondaki öğelerin gezinmesi için değil, aynı zamanda ana ayrıntı bağlama senaryosu için de kullanışlıdır. [Veri bağlama nedir](#what-is-data-binding) bölümünde uygulama kullanıcı arabirimini de göz önünde bulundurun. Bu uygulamada, içindeki seçim içinde gösterilen içeriği <xref:System.Windows.Controls.ListBox> belirler <xref:System.Windows.Controls.ContentControl>. Bir <xref:System.Windows.Controls.ListBox> öğe seçildiğinde, bu öğeyi başka bir şekilde koymak için seçili öğenin ayrıntılarını <xref:System.Windows.Controls.ContentControl> gösterir.

Aynı görünüme iki veya daha fazla denetim bağlayarak, ana ayrıntı senaryosunu uygulayabilirsiniz. [Veri bağlama tanıtımında][data-binding-demo] bulunan aşağıdaki örnek, <xref:System.Windows.Controls.ListBox> ve [veri bağlama nedir](#what-is-data-binding) bölümünde uygulama Kullanıcı <xref:System.Windows.Controls.ContentControl> arabiriminde gördüğünüz ve ' nin işaretlemesini gösterir.

[!code-xaml[ListBoxContentControl](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#ListBoxContentControl)]

Denetimlerin her ikisinin de aynı kaynağa, *listingDataView* statik kaynağına ( [bir görünüm oluşturma bölümünde](#how-to-create-a-view)bu kaynağın tanımına bakın) bağlandığını unutmayın. Bu bağlama, tek bir nesne ( <xref:System.Windows.Controls.ContentControl> bu durumda) bir koleksiyon görünümüne bağlı olduğunda otomatik olarak görünümün öğesine bağlandığı için <xref:System.Windows.Data.CollectionView.CurrentItem%2A> geçerlidir. Nesneler <xref:System.Windows.Data.CollectionViewSource> , para birimini ve seçimi otomatik olarak eşitler. Liste denetiminiz bir <xref:System.Windows.Data.CollectionViewSource> nesneye bu örnekte olduğu gibi bağlanmazsa, bunun çalışması için <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> özelliğini olarak `true` ayarlamanız gerekir.

Diğer örnekler için bkz. [bir koleksiyona bağlama ve seçime göre bilgi görüntüleme](../../framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md) ve [hiyerarşik verilerle ana ayrıntı modelini kullanma](../../framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md).

Yukarıdaki örneğin bir şablon kullandığını fark etmiş olabilirsiniz. Aslında, veriler şablonlar kullanılmadan (tarafından açıkça kullanılan <xref:System.Windows.Controls.ContentControl> ve tarafından örtülü olarak kullanılan <xref:System.Windows.Controls.ListBox>), istediğimiz şekilde gösterilmez. Şimdi, sonraki bölümde veri şablonu oluşturma özelliğini kullanacağız.

## <a name="data-templating"></a>Veri şablonu oluşturma

Veri şablonlarının kullanımı olmadan, uygulama Kullanıcı arabirimimiz [veri bağlama](#what-is-data-binding) bölümünde aşağıdaki gibi görünür.

![Veri şablonları olmadan veri bağlama tanıtımı](./media/data-binding-overview/demo-no-template.png)

Önceki bölümde gösterildiği gibi, hem <xref:System.Windows.Controls.ListBox> denetim hem <xref:System.Windows.Controls.ContentControl> de tüm koleksiyon nesnesine (ya da daha fazla özellikle, koleksiyon nesnesi üzerinde Görünüm), *AuctionItem*s ' nin tamamına bağlanır. Veri koleksiyonunun nasıl görüntüleneceği konusunda belirli yönergeler olmadan, temel alınan koleksiyondaki <xref:System.Windows.Controls.ListBox> her nesnenin dize gösterimini görüntüler ve bağladığına ait nesnenin dize temsilini <xref:System.Windows.Controls.ContentControl> görüntüler.

Bu sorunu çözmek için uygulama tanımlar <xref:System.Windows.DataTemplate?text=DataTemplates>. Önceki bölümdeki örnekte gösterildiği gibi, <xref:System.Windows.Controls.ContentControl> açıkça *Ayrıntılar Productlistingtemplate* veri şablonunu kullanır. <xref:System.Windows.Controls.ListBox> Denetim, koleksiyonda *AuctionItem* nesnelerini görüntülerken aşağıdaki veri şablonunu örtülü olarak kullanır.

[!code-xaml[AuctionItemDataTemplate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#AuctionItemDataTemplate)]

Bu iki DataTemplate kullanımı ile elde edilen kullanıcı arabirimi, [veri bağlama nedir](#what-is-data-binding) bölümünde gösterilen şeydir. Söz konusu ekran görüntüsünden görebileceğiniz gibi, denetimlerinizde veri yerleştirmenize izin vermenin yanı sıra DataTemplates verileriniz için etkileyici görseller tanımlamanızı sağlar. Örneğin, yukarıda <xref:System.Windows.DataTrigger>' de, *özelleştirilmiş özellikler* içeren <xref:System.Windows.DataTemplate> *AuctionItem* *s 'in,* turuncu bir kenarlık ve yıldız ile görüntülenebilmesi için, yukarıda ' de kullanılır.

Veri şablonları hakkında daha fazla bilgi için bkz. [veri şablonu oluşturmaya genel bakış](../../framework/wpf/data/data-templating-overview.md).

## <a name="data-validation"></a>Veri doğrulama

Kullanıcının beklenen bilgileri girdiğinden emin olmak için Kullanıcı girişi kullanan çoğu uygulamanın doğrulama mantığı olması gerekir. Doğrulama denetimleri tür, Aralık, biçim veya uygulamaya özgü diğer gereksinimlere göre yapılabilir. Bu bölümde, veri doğrulamanın WPF 'de nasıl çalıştığı açıklanmaktadır.

### <a name="associating-validation-rules-with-a-binding"></a>Doğrulama kurallarını bir bağlama ile ilişkilendirme

WPF veri bağlama modeli, <xref:System.Windows.Data.Binding.ValidationRules%2A> <xref:System.Windows.Data.Binding> nesneniz ile ilişkilendirmenize olanak tanır. Örneğin, aşağıdaki <xref:System.Windows.Controls.TextBox> örnek öğesini adlı `StartPrice` bir özelliğe bağlar ve <xref:System.Windows.Controls.ExceptionValidationRule> <xref:System.Windows.Data.Binding.ValidationRules%2A?displayProperty=nameWithType> özelliğine bir nesne ekler.

[!code-xaml[TextboxStartPrice](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextboxStartPrice)]

Bir <xref:System.Windows.Controls.ValidationRule> nesne, özelliğin değerinin geçerli olup olmadığını denetler. WPF 'de <xref:System.Windows.Controls.ValidationRule> iki tür yerleşik nesne vardır:

- Bağlama <xref:System.Windows.Controls.ExceptionValidationRule> kaynağı özelliğinin güncelleştirilmesi sırasında oluşturulan özel durumları denetler. Önceki örnekte, `StartPrice` integer türündedir. Kullanıcı tamsayıya dönüştürülemeyen bir değer girdiğinde, bir özel durum oluşturulur ve bağlamanın geçersiz olarak işaretlenmesine neden olur. <xref:System.Windows.Controls.ExceptionValidationRule> Açıkça ayarlamaya yönelik alternatif <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> bir sözdizimi, `true` <xref:System.Windows.Data.Binding> veya <xref:System.Windows.Data.MultiBinding> nesneniz için özelliğini olarak ayarlanmıştır.

- Bir <xref:System.Windows.Controls.DataErrorValidationRule> nesnesi, <xref:System.ComponentModel.IDataErrorInfo> arabirimini uygulayan nesneler tarafından oluşturulan hataları denetler. Bu doğrulama kuralını kullanmayla ilgili bir örnek için bkz <xref:System.Windows.Controls.DataErrorValidationRule>.. <xref:System.Windows.Controls.DataErrorValidationRule> Açıkça ayarlamaya yönelik alternatif <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> bir sözdizimi, `true` <xref:System.Windows.Data.Binding> veya <xref:System.Windows.Data.MultiBinding> nesneniz için özelliğini olarak ayarlanmıştır.

Ayrıca, <xref:System.Windows.Controls.ValidationRule> sınıfından türeterek ve <xref:System.Windows.Controls.ValidationRule.Validate%2A> metodunu uygulayarak kendi doğrulama kuralınızı de oluşturabilirsiniz. Aşağıdaki örnek, [veri bağlama nedir](#what-is-data-binding) bölümünde "başlangıç tarihi" <xref:System.Windows.Controls.TextBox> *ürün ekleme listesi* tarafından kullanılan kuralı gösterir.

[!code-csharp[FutureDateRule](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/FutureDateRule.cs#FutureDateRule)]
[!code-vb[FutureDateRule](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/FutureDateRule.vb#FutureDateRule)]

*StartDateEntryForm* <xref:System.Windows.Controls.TextBox> , aşağıdaki örnekte gösterildiği gibi bu *futuredadterule*öğesini kullanır.

[!code-xaml[TextboxStartDate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextboxStartDate)]

<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> Değer olduğundan <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, bağlama altyapısı her tuş vuruşunda kaynak değerini günceller, bu da her tuş vuruşu üzerinde <xref:System.Windows.Data.Binding.ValidationRules%2A> koleksiyondaki her kuralı denetlediği anlamına gelir. Bunu doğrulama Işlemi bölümünde ele aldık.

### <a name="providing-visual-feedback"></a>Görsel geri bildirim sağlama

Kullanıcı geçersiz bir değer girerse, uygulama kullanıcı arabiriminde hata hakkında bazı geri bildirimler sağlamak isteyebilirsiniz. Bu tür geri bildirimde bulunmak için bir yol, <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> ekli özelliği özel <xref:System.Windows.Controls.ControlTemplate>olarak ayarlamaya yönelik bir yoldur. Önceki alt bölümde gösterildiği gibi, *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> adlı bir <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> *validationTemplate*'i kullanır. Aşağıdaki örnek *validationTemplate*tanımını gösterir.

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#ControlTemplate)]

<xref:System.Windows.Controls.AdornedElementPlaceholder> Öğesi, donatılan denetimin yerleştirilmesi gereken yeri belirtir.

Ayrıca, hata iletisini göstermek <xref:System.Windows.Controls.ToolTip> için de kullanabilirsiniz. Hem *StartDateEntryForm* hem de <xref:System.Windows.Controls.ToolTip> *StartPriceEntryForm*<xref:System.Windows.Controls.TextBox>, hata iletisini görüntüleyen bir oluşturan *textStyleTextBox*stilini kullanır. Aşağıdaki örnek *textStyleTextBox*'ın tanımını gösterir. İliştirilmiş özelliği <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> , bağlı `true` öğenin özelliklerindeki bir veya daha fazla bağlamanın hatalı olması durumunda olur.

[!code-xaml[TextBoxStyle](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextBoxStyle)]

Özel <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> ve <xref:System.Windows.Controls.ToolTip>ile, bir doğrulama hatası olduğunda *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> aşağıdaki gibi görünür.

![Veri bağlama doğrulama hatası](./media/data-binding-overview/demo-validation-date.png "DataBindingDemo_Validation")

Eğer hesabınız <xref:System.Windows.Data.Binding> , doğrulama kurallarına sahipse ancak ilişkili denetimde belirtmezseniz <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> , bir doğrulama hatası olduğunda kullanıcıları bilgilendirmek için varsayılan <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> olarak kullanılır. Varsayılan değer <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> , donatıcı katmanında kırmızı bir kenarlığı tanımlayan bir denetim şablonudur. Varsayılan <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> ve <xref:System.Windows.Controls.ToolTip>ile, *StartPriceEntryForm* <xref:System.Windows.Controls.TextBox> Kullanıcı arabirimi, doğrulama hatası olduğunda aşağıdaki gibi görünür.

![Veri bağlama doğrulama hatası](./media/data-binding-overview/demo-validation-price.png "DataBindingDemo_ValidationDefault")

Bir iletişim kutusundaki tüm denetimleri doğrulamaya yönelik mantık sağlama hakkında bir örnek için [iletişim kutularında](../../framework/wpf/app-development/dialog-boxes-overview.md)özel iletişim kutuları bölümüne bakın.

### <a name="validation-process"></a>Doğrulama işlemi

Doğrulama genellikle bir hedefin değeri bağlama kaynağı özelliğine aktarıldığında oluşur. Bu aktarım, ve <xref:System.Windows.Data.BindingMode.TwoWay> <xref:System.Windows.Data.BindingMode.OneWayToSource> bağlamalarda gerçekleşir. Yeniden yinelemek için, bir kaynak güncelleştirmesine neden olan kaynak [güncelleştirmelerini tetikleyen](#what-triggers-source-updates) bölümünde açıklandığı <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> gibi, özelliğin değerine bağlıdır.

Aşağıdaki öğeler *doğrulama* işlemini anlatmaktadır. Bu işlem sırasında herhangi bir doğrulama hatası veya başka türde bir hata oluşursa, işlem durdurulur:

1. Bağlama altyapısı, olarak <xref:System.Windows.Controls.ValidationRule> <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> <xref:System.Windows.Controls.ValidationStep.RawProposedValue> ayarlanmış herhangi bir özel nesne olup olmadığını denetler; bu <xref:System.Windows.Data.Binding>durumda, biri bir hata halinde çalıştırana kadar veya <xref:System.Windows.Controls.ValidationRule.Validate%2A> hepsi geçene <xref:System.Windows.Controls.ValidationRule> kadar her bir yöntemi çağırır.

2. Bağlama altyapısı, varsa dönüştürücüyü çağırır.

3. Dönüştürücü başarılı olursa bağlama motoru, için <xref:System.Windows.Controls.ValidationRule> olarak <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> ayarlanmış herhangi bir özel nesne olup olmadığını denetler; bu <xref:System.Windows.Data.Binding>durumda, biri bir hata halinde veya hepsi geçene kadar <xref:System.Windows.Controls.ValidationRule.Validate%2A> <xref:System.Windows.Controls.ValidationRule> <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ayarlanmış olan her bir yöntem için olarak <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> ayarlanan her bir yöntemi çağırır.

4. Bağlama altyapısı, kaynak özelliğini ayarlar.

5. Bağlama altyapısı, <xref:System.Windows.Controls.ValidationRule> için olarak <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> <xref:System.Windows.Controls.ValidationStep.UpdatedValue> ayarlanmış herhangi bir özel nesne olup olmadığını denetler; bu <xref:System.Windows.Data.Binding>durumda, biri bir hata halinde <xref:System.Windows.Controls.ValidationRule.Validate%2A> <xref:System.Windows.Controls.ValidationRule> <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> <xref:System.Windows.Controls.ValidationStep.UpdatedValue> çalıştırana kadar ya da hepsi geçene kadar ayarlanmış olan her bir bir yöntemi çağırır. Bir <xref:System.Windows.Controls.DataErrorValidationRule> bağlama ile ilişkiliyse ve <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> bu, varsayılan <xref:System.Windows.Controls.ValidationStep.UpdatedValue> <xref:System.Windows.Controls.DataErrorValidationRule> olarak ayarlanırsa, bu noktada denetlenir. Bu noktada, olarak <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> `true` ayarlanmış herhangi bir bağlama denetlenir.

6. Bağlama altyapısı, <xref:System.Windows.Controls.ValidationRule> için olarak <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> <xref:System.Windows.Controls.ValidationStep.CommittedValue> ayarlanmış herhangi bir özel nesne olup olmadığını denetler; bu <xref:System.Windows.Data.Binding>durumda, biri bir hata halinde <xref:System.Windows.Controls.ValidationRule.Validate%2A> <xref:System.Windows.Controls.ValidationRule> <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> <xref:System.Windows.Controls.ValidationStep.CommittedValue> çalıştırana kadar ya da hepsi geçene kadar ayarlanmış olan her bir bir yöntemi çağırır.

<xref:System.Windows.Controls.ValidationRule> Bu işlem boyunca hiçbir zaman geçemezse bağlama altyapısı bir <xref:System.Windows.Controls.ValidationError> nesnesi oluşturur ve onu bağlantılı öğenin <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> koleksiyonuna ekler. Bağlama altyapısı herhangi bir adımda <xref:System.Windows.Controls.ValidationRule> nesneleri çalıştırmadan önce, söz konusu adım sırasında bağlı öğenin <xref:System.Windows.Controls.ValidationError> <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> Ekli özelliğine eklenen her türlü öğeyi kaldırır. Örneğin, bir,, <xref:System.Windows.Controls.ValidationRule> , <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> bir sonraki doğrulama <xref:System.Windows.Controls.ValidationStep.UpdatedValue> işlemi başarısız olduğunda, bağlama <xref:System.Windows.Controls.ValidationError> altyapısı, olarak <xref:System.Windows.Controls.ValidationRule> <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> <xref:System.Windows.Controls.ValidationStep.UpdatedValue>ayarlanmış herhangi bir ' i çağırmadan önce onu kaldırır.

<xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> Boş olmadığında, öğesinin <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği olarak `true`ayarlanır. Ayrıca <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A> , öğesinin <xref:System.Windows.Data.Binding> özelliği olarak `true`ayarlandıysa, bağlama altyapısı öğesinde <xref:System.Windows.Controls.Validation.Error?displayProperty=nameWithType> ekli olayı başlatır.

Ayrıca, her iki yönde de geçerli bir değer aktarımının (hedeften kaynağa veya kaynaktan hedefe) <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> ekli özelliği temizlemiş olduğunu unutmayın.

Bağlama onunla <xref:System.Windows.Controls.ExceptionValidationRule> ilişkili bir varsa veya <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> özelliği olarak `true` ayarlanmışsa ya da bağlama altyapısı kaynağı ayarlarsa, bağlama altyapısı bir <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>olup olmadığını denetler. Özel durumları işlemek için özel bir işleyici <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> sağlamak üzere geri aramayı kullanma seçeneğiniz vardır. ' Nde belirtilmemişse, bağlama motoru <xref:System.Windows.Controls.ValidationError> özel durum ile bir oluşturur ve onu bağlı öğenin <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> koleksiyonuna ekler. <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> <xref:System.Windows.Data.Binding>

## <a name="debugging-mechanism"></a>Hata ayıklama mekanizması

Belirli bir bağlamanın durumu hakkında bilgi <xref:System.Diagnostics.PresentationTraceSources.TraceLevel%2A?displayProperty=nameWithType> almak için bağlama ile ilgili nesne üzerinde iliştirilmiş özelliğini ayarlayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.DataErrorValidationRule>
- [LINQ sorgusunun sonuçlarına bağlama](../../framework/wpf/data/how-to-bind-to-the-results-of-a-linq-query.md)
- [Veri bağlama](../../framework/wpf/advanced/optimizing-performance-data-binding.md)
- [Veri bağlama tanıtımı][data-binding-demo]
- [Nasıl yapılır makaleleri](../../framework/wpf/data/data-binding-how-to-topics.md)
- [ADO.NET veri kaynağına bağlama](../../framework/wpf/data/how-to-bind-to-an-ado-net-data-source.md)

[data-binding-demo]: https://github.com/microsoft/WPF-Samples/tree/master/Sample%20Applications/DataBindingDemo "veri bağlama tanıtım uygulaması"
