---
title: Veri bağlamaya genel bakış
description: .NET Core için Windows Presentation Foundation ' de projenize ekleyebileceğiniz farklı veri kaynakları hakkında bilgi edinin. Veri kaynakları, dinamik uygulamalar oluşturmak için XAML öğelerine bağlanabilir.
author: adegeo
ms.date: 09/19/2019
ms.author: adegeo
dev_langs:
- csharp
- vb
ms.openlocfilehash: 3c9615d7d79b5da1c180bb505f5f37b99aeae775
ms.sourcegitcommit: e0803b8975d3eb12e735a5d07637020dd6dac5ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2020
ms.locfileid: "89272003"
---
# <a name="data-binding-overview-in-wpf"></a>WPF 'de veri bağlamaya genel bakış

Windows Presentation Foundation (WPF) içindeki veri bağlama, uygulamaların verileri sunmak ve verilerle etkileşim kurmak için basit ve tutarlı bir yol sağlar. Öğeler, .NET nesneleri ve XML biçiminde çeşitli veri kaynaklarından verilere bağlanabilir. Ve gibi her türlü gibi, <xref:System.Windows.Controls.ContentControl> <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.ItemsControl> <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.ListView> tek veri öğelerinin veya veri öğelerinin koleksiyonlarının esnek stillendirilmesini sağlayan yerleşik işlevlere sahiptir. Sıralama, filtre ve grup görünümleri verilerin üzerine oluşturulabilir.

WPF 'deki veri bağlama işlevselliği, geniş kapsamlı özellikler, verilerin esnek Kullanıcı arabirimi gösterimi ve kullanıcı arabiriminden iş mantığı ayırmayı temizleme dahil olmak üzere geleneksel modellere göre çeşitli avantajlar sunar.

Bu makalede ilk olarak WPF veri bağlama için temel kavramlar ele alınmaktadır ve <xref:System.Windows.Data.Binding> sınıfının kullanımı ve veri bağlamanın diğer özellikleri ele alınmıştır.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="what-is-data-binding"></a>Veri bağlama nedir?

Veri bağlama, uygulama kullanıcı arabirimi ve görüntülediği veriler arasında bağlantı kuran işlemdir. Bağlamanın doğru ayarları varsa ve veriler doğru bildirimleri sağlıyorsa, veriler değerini değiştirdiğinde veriye bağlanan öğeler otomatik olarak değişiklikleri yansıtır. Veri bağlama Ayrıca bir öğedeki verilerin bir dış gösterimi değişirse, temel alınan verilerin değişikliği yansıtacak şekilde otomatik olarak güncelleştirilmesini sağlayabilir. Örneğin, Kullanıcı bir öğesindeki değeri düzenlerse `TextBox` , temel alınan veri değeri bu değişikliği yansıtacak şekilde otomatik olarak güncelleştirilir.

Veri bağlamanın tipik bir kullanımı, sunucu veya yerel yapılandırma verilerini formlara veya diğer kullanıcı arabirimi denetimlerine yerleştirkullanmaktır. WPF 'de, bu kavram çeşitli veri kaynaklarına çok çeşitli özellikler bağlamayı kapsayacak şekilde genişletilir. WPF 'de, öğelerin bağımlılık özellikleri .NET nesnelerine (ADO.NET nesneleri veya Web Hizmetleri ve Web özellikleriyle ilişkili nesneler dahil) ve XML verileriyle bağlanabilir.

Veri bağlama örneği için, bir açık eksiltme öğelerinin listesini görüntüleyen [veri bağlama tanıtımına][data-binding-demo]ait aşağıdaki uygulama kullanıcı arabirimine göz atın.

![Veri bağlama örnek ekran görüntüsü](./media/data-binding-overview/demo.png "DataBinding_DataBindingDemo")

Uygulama, veri bağlamanın aşağıdaki özelliklerini gösterir:

- ListBox 'ın içeriği bir *AuctionItem* nesneleri koleksiyonuna bağlanır. Bir *AuctionItem* nesnesi *Description*, *StartPrice*, *StartDate*, *category*, *SpecialFeatures*gibi özelliklere sahiptir.

- İçinde görüntülenen veriler (*AuctionItem* nesneleri), `ListBox` her öğe için açıklama ve geçerli fiyatın gösterilmesi için şablonlanır. Şablon, kullanılarak oluşturulur <xref:System.Windows.DataTemplate> . Ayrıca, her öğenin görünümü görüntülenmekte olan *AuctionItem* öğesinin *SpecialFeatures* değerine bağlıdır. *AuctionItem* öğesinin *SpecialFeatures* değeri *Color*ise, öğenin mavi kenarlığı vardır. Değer *Vurgulayıcıdır*, öğenin turuncu kenarlığı ve yıldızı vardır. [Veri şablonu](#data-templating) oluşturma bölümü, veri şablonu oluşturma hakkında bilgi sağlar.

- Kullanıcı, verileri belirtilen kullanarak gruplandırabilir, süzebilir veya sıralayabilir `CheckBoxes` . Yukarıdaki görüntüde **kategoriye göre gruplandırma** ve **kategoriye ve tarihe göre sıralama** `CheckBoxes` seçilidir. Verilerin ürün kategorisine göre gruplandığını fark etmiş olabilirsiniz ve kategori adı alfabetik sırada olur. Görüntüden bildirimde bulunulmaları zordur, ancak öğeler her kategori içindeki başlangıç tarihine göre sıralanır. Sıralama, bir *koleksiyon görünümü*kullanılarak yapılır. [Koleksiyonlara bağlama](#binding-to-collections) bölümü koleksiyon görünümlerini tartışır.

- Kullanıcı bir öğe seçtiğinde, <xref:System.Windows.Controls.ContentControl> Seçili öğenin ayrıntılarını görüntüler. Bu deneyim, *ana ayrıntı senaryosu*olarak adlandırılır. [Ana ayrıntı senaryosu](#master-detail-binding-scenario) bölümünde bu bağlama türü hakkında bilgi sağlanır.

- *StartDate* özelliğinin türü <xref:System.DateTime> , milisaniye cinsinden saati içeren bir tarih döndürür. Bu uygulamada, daha kısa bir tarih dizesinin görüntülenmesi için özel bir dönüştürücü kullanılmıştır. [Veri dönüştürme](#data-conversion) bölümünde dönüştürücüler hakkında bilgi sağlanır.

Kullanıcı *Ürün Ekle* düğmesini seçtiğinde aşağıdaki form gelir.

![Ürün listeleme sayfası ekle](./media/data-binding-overview/demo-addproductlisting.png "DataBinding_Demo_AddProductListing")

Kullanıcı formdaki alanları düzenleyebilir, kısa veya ayrıntılı önizleme bölmelerini kullanarak ürün listesini önizleyebilir ve `Submit` yeni ürün listesini eklemeyi seçebilir. Mevcut gruplandırma, filtreleme ve sıralama ayarları, yeni giriş için geçerli olacaktır. Bu durumda, yukarıdaki görüntüde girilen öğe, *bilgisayar* kategorisi içinde ikinci öğe olarak görüntülenir.

Bu görüntüde gösterilmez, *başlangıç tarihinde* verilen doğrulama mantığıdır <xref:System.Windows.Controls.TextBox> . Kullanıcı geçersiz bir tarih (geçersiz biçimlendirme veya geçmiş tarih) girerse, kullanıcıya öğesinin yanında bir ve kırmızı bir ünlem işaretiyle bildirim gönderilir <xref:System.Windows.Controls.ToolTip> <xref:System.Windows.Controls.TextBox> . [Veri doğrulama](#data-validation) bölümü, doğrulama mantığının nasıl oluşturulacağını açıklar.

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
  
  > Örneğin, bir öğesinin içeriğini özelliğine bağlamak istiyorsanız `TextBox` `Employee.Name` , hedef nesneniz, `TextBox` hedef özelliği ise, <xref:System.Windows.Controls.TextBox.Text%2A> kullanılacak değer, *adı*ise ve kaynak nesne *çalışan* nesnesidir.

- Target özelliği bir Dependency özelliği olmalıdır. Çoğu <xref:System.Windows.UIElement> Özellik bağımlılık özellikleridir ve salt okuma dışındaki çoğu bağımlılık özellikleri varsayılan olarak veri bağlamayı destekler. (Yalnızca öğesinden türetilmiş türler <xref:System.Windows.DependencyObject> , bağımlılık özelliklerini tanımlayabilir ve tüm <xref:System.Windows.UIElement> türler öğesinden türetilir `DependencyObject` .)

- Şekilde gösterilmese de, bağlama kaynak nesnesinin özel bir .NET nesnesi olmasına sınırlı olmadığından not edilmelidir. WPF veri bağlama, verileri .NET nesneleri ve XML biçiminde destekler. Bazı örnekler sağlamak için bağlama kaynağınız bir <xref:System.Windows.UIElement> , herhangi bir liste nesnesi, ADO.NET veya Web Hizmetleri nesnesi veya XML verilerinizi içeren bir XmlNode olabilir. Daha fazla bilgi için bkz. [bağlama kaynaklarına genel bakış](../../framework/wpf/data/binding-sources-overview.md).

Bir bağlama oluştururken bağlama hedefini bağlama kaynağı *olarak* bağladığınızda dikkat etmeniz önemlidir. Örneğin, bir veri bağlama kullanarak bazı temel XML verilerini görüntülüyorsanız <xref:System.Windows.Controls.ListBox> , bunu `ListBox` XML verilerine bağlamanız gerekir.

Bir bağlama oluşturmak için <xref:System.Windows.Data.Binding> nesnesini kullanın. Bu makalenin geri kalanında, ile ilişkili kavramların birçoğu ve nesnenin bazı özellikleri ve kullanımları açıklanmaktadır `Binding` .

### <a name="direction-of-the-data-flow"></a>Veri akışının yönü

Önceki şekildeki oka göre gösterildiği gibi, bir bağlamanın veri akışı bağlama kaynağından bağlama kaynağına gidebilir (örneğin, bir Kullanıcı bir ' ın değerini değiştirdiğinde kaynak değer değişir `TextBox` ) ve/veya bağlama kaynağından bağlama hedefine (örneğin, `TextBox` içeriğiniz bağlama kaynağında değişikliklerle güncelleştirilir) ve bağlama kaynağı doğru bildirimleri sağlar.

Uygulamanızın kullanıcıların verileri değiştirmesini ve kaynak nesnesine geri yaymasını etkinleştirmesini isteyebilirsiniz. Ya da kullanıcıların kaynak verileri güncelleştirmesini etkinleştirmek istemeyebilirsiniz. ' İ ayarlayarak veri akışını kontrol edebilirsiniz <xref:System.Windows.Data.Binding.Mode?displayProperty=nameWithType> .

Bu şekilde farklı veri akışı türleri gösterilmektedir:

![Veri bağlama veri akışı](./media/data-binding-overview/databinding-dataflow.png "DataBinding_DataFlow")

- <xref:System.Windows.Data.BindingMode.OneWay> bağlama, hedef özelliği otomatik olarak güncelleştirmek için kaynak özellikte değişikliklere neden olur, ancak Target özelliğindeki değişiklikler kaynak özelliğine geri yayılmaz. Bu tür bir bağlama, bağlanmakta olan denetimin örtülü olarak salt okunurdur. Örneğin, bir stok şeridi gibi bir kaynağa bağlanabilir veya belki de hedef özellikte, bir tablonun veri bağlantılı arka plan rengi gibi değişiklikler yapmak için hiçbir denetim arabirimi sağlanmamıştır. Hedef özelliğin değişikliklerini izlemeye gerek yoksa <xref:System.Windows.Data.BindingMode.OneWay> bağlama modunun kullanılması bağlama modunun ek yükünü önler <xref:System.Windows.Data.BindingMode.TwoWay> .

- <xref:System.Windows.Data.BindingMode.TwoWay> bağlama, kaynak özellikte veya Target özelliğinde, diğerini otomatik olarak güncelleştirmek için değişikliklere neden olur. Bu tür bir bağlama, düzenlenebilir formlar veya diğer tam etkileşimli kullanıcı arabirimi senaryoları için uygundur. Çoğu özellik varsayılan olarak <xref:System.Windows.Data.BindingMode.OneWay> bağlamaya, ancak bazı bağımlılık özelliklerine (genellikle <xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType> ve [onay kutusu](xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked) gibi kullanıcı tarafından düzenlenebilir denetimlerin özellikleri). <xref:System.Windows.Data.BindingMode.TwoWay> Bağımlılık özelliğinin tek yönlü veya iki yönlü olarak bağlama özelliğinin, özelliği olan özellik meta verilerini almak <xref:System.Windows.DependencyProperty.GetMetadata%2A?displayProperty=nameWithType> ve sonra özelliğin Boole değerini denetlemesi için programlı bir yoldur <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A?displayProperty=nameWithType> .

- <xref:System.Windows.Data.BindingMode.OneWayToSource> , <xref:System.Windows.Data.BindingMode.OneWay> bağlamanın tersidir; Target özelliği değiştiğinde kaynak özelliğini güncelleştirir. Tek örnek senaryo yalnızca kaynak değeri kullanıcı arabiriminden yeniden değerlendirmeniz gerektiğinde olur.

- Şekil, <xref:System.Windows.Data.BindingMode.OneTime> kaynak özelliğin hedef özelliği başlatmasına, ancak sonraki değişiklikleri yaymasına neden olan bağlamadır. Veri bağlamı değişirse veya veri bağlamındaki nesne değişirse değişiklik, hedef *özellikte yansıtılmaz.* Geçerli durumun bir anlık görüntüsü uygunsa veya veriler gerçekten statikse, bu tür bir bağlama uygundur. Hedef özelliği bir kaynak özelliğinden bir değer ile başlatmak istiyorsanız ve veri bağlamı önceden bilinmiyorsa, bu tür bağlama de kullanışlıdır. Bu mod aslında <xref:System.Windows.Data.BindingMode.OneWay> kaynak değerin değişmemesi durumunda daha iyi performans sağlayan daha basit bir bağlama biçimidir.

Kaynak değişiklikleri (ve bağlamaları için geçerlidir <xref:System.Windows.Data.BindingMode.OneWay> ) algılamak için <xref:System.Windows.Data.BindingMode.TwoWay> , kaynak gibi uygun bir özellik değişikliği bildirim mekanizması gerçekleştirmelidir <xref:System.ComponentModel.INotifyPropertyChanged> . Bkz. [nasıl yapılır: uygulama örneği için özellik değişikliği bildirimi uygulama](../../framework/wpf/data/how-to-implement-property-change-notification.md) <xref:System.ComponentModel.INotifyPropertyChanged> .

<xref:System.Windows.Data.Binding.Mode?displayProperty=nameWithType>Özelliği bağlama modları hakkında daha fazla bilgi ve bir bağlamanın yönlerinin nasıl belirtilbir örneğini sağlar.

### <a name="what-triggers-source-updates"></a>Hangi kaynak güncelleştirmelerini tetikler

<xref:System.Windows.Data.BindingMode.TwoWay> <xref:System.Windows.Data.BindingMode.OneWayToSource> Hedef özelliğindeki değişiklikler için veya dinleyen bağlamalar, kaynağı güncelleştirme olarak bilinen, kaynak olarak kaynağa geri yayılır. Örneğin, temel alınan kaynak değerini değiştirmek için bir TextBox metnini düzenleyebilirsiniz.

Ancak, metin düzenlenirken veya metni düzenledikten sonra Denetim odağı kaybetirken kaynak değer güncelleştirilir mi? <xref:System.Windows.Data.Binding.UpdateSourceTrigger?displayProperty=nameWithType>Özelliği, kaynağın güncelleştirilmesini neyin tetikleyeceğini belirler. Aşağıdaki şekildeki doğru okların noktaları, özelliğin rolünü gösterir <xref:System.Windows.Data.Binding.UpdateSourceTrigger?displayProperty=nameWithType> .

![UpdateSourceTrigger özelliğinin rolünü gösteren diyagram.](./media/data-binding-overview/data-binding-updatesource-trigger.png)

`UpdateSourceTrigger`Değer ise <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged?displayProperty=nameWithType> , sağ ok veya bağlamalar tarafından işaret edilen değer, <xref:System.Windows.Data.BindingMode.TwoWay> <xref:System.Windows.Data.BindingMode.OneWayToSource> hedef özelliği değiştikçe hemen güncellenir. Ancak `UpdateSourceTrigger` değer ise <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> , bu değer yalnızca Target özelliği odağı kaybettiğinde yeni değerle güncelleştirilir.

Özelliğe benzer şekilde <xref:System.Windows.Data.Binding.Mode%2A> , farklı bağımlılık özellikleri farklı varsayılan değerlere sahiptir <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> . Bağımlılık özelliklerinin çoğu için varsayılan değer <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> , `TextBox.Text` özelliğin varsayılan değeri olan ' dir <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> . `PropertyChanged` kaynak güncelleştirmelerinin genellikle Target özelliği değiştiğinde meydana gelir. Anında değişiklikler, onay kutuları ve diğer basit denetimler için uygundur. Bununla birlikte, metin alanları için, her tuş vuruşundan sonra güncelleştirme performansı azaledebilir ve kullanıcıyı yeni değere işlemeden önce, geri alma ve yazma hatalarını çözme fırsatını reddeder.

<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>Bağımlılık özelliğinin varsayılan değerini bulma hakkında bilgi için bkz. Özellik sayfası.

Aşağıdaki tabloda <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> , örnek olarak kullanılarak her bir değer için örnek bir senaryo verilmiştir <xref:System.Windows.Controls.TextBox> .

| UpdateSourceTrigger değeri | Kaynak değer güncelleştirildiği zaman | TextBox için örnek senaryo |
| ------------------------- | ---------------------------------- | ---------------------------- |
| `LostFocus` (için varsayılan <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> ) | TextBox denetimi odağı kaybettiğinde. | Doğrulama mantığı ile ilişkili bir metin kutusu (aşağıdaki [veri doğrulamasına](#data-validation) bakın). |
| `PropertyChanged` | Öğesine yazarken <xref:System.Windows.Controls.TextBox> . | Bir sohbet odası penceresinde TextBox denetimleri. |
| `Explicit` | Uygulama çağırdığında <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> . | Düzenlenebilir bir formda metin kutusu denetimleri (kaynak değerlerini yalnızca Kullanıcı Gönder düğmesine tıkladığında güncelleştirir). |

Bir örnek için bkz. [nasıl yapılır: denetim kutusu metninde kaynağı ne zaman güncelleştirin](../../framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md).

## <a name="creating-a-binding"></a>Bağlama oluşturma

Önceki bölümlerde ele alınan kavramların bazılarını yeniden oluşturmak için, nesnesini kullanarak bir bağlama kurarsınız <xref:System.Windows.Data.Binding> ve her bağlamada genellikle dört bileşen vardır: bağlama hedefi, hedef özellik, bağlama kaynağı ve kullanılacak kaynak değer yolu. Bu bölümde bir bağlamanın nasıl ayarlanacağı açıklanır.

Bağlama kaynak nesnesinin, *SDKSample* ad alanında tanımlanan *MyData* adlı bir sınıf olduğu aşağıdaki örneği göz önünde bulundurun. Tanıtım amacıyla, *MyData* değeri "Red" olarak ayarlanmış *ColorName* adlı bir String özelliğine sahiptir. Bu nedenle, bu örnek kırmızı bir arka plana sahip bir düğme oluşturur.

[!code-xaml[BindNonTextProperty](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/AutoConvertPropertyToColor.xaml#BindAutoConvertColor)]

Bağlama bildirimi sözdizimi hakkında daha fazla bilgi ve kod içinde bağlama ayarlama örnekleri için bkz. [bağlama bildirimlerine genel bakış](../../framework/wpf/data/binding-declarations-overview.md).

Bu örneği temel diyagramımızı uygulıyoruz, sonuçta elde edilen şekil aşağıdaki gibi görünür. Bu şekilde <xref:System.Windows.Data.BindingMode.OneWay> , arka plan özelliği varsayılan olarak bağlamayı desteklediğinden bu şekilde bir bağlama açıklanmaktadır <xref:System.Windows.Data.BindingMode.OneWay> .

![Veri bağlama arka plan özelliğini gösteren diyagram.](./media/data-binding-overview/data-binding-button-background-example.png)

Bu bağlamanın, bir özellik türü olsa da, *ColorName* özelliği String türünde olmasına rağmen neden bu bağlamanın işe yaradığına merak ediyor olabilirsiniz <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Media.Brush> . Bu bağlama, [veri dönüştürme](#data-conversion) bölümünde ele alınan varsayılan tür dönüşümünü kullanır.

### <a name="specifying-the-binding-source"></a>Bağlama kaynağını belirtme

Önceki örnekte, bağlama kaynağının [DockPanel. DataContext](xref:System.Windows.FrameworkElement.DataContext) özelliği ayarlanarak belirtildiğine dikkat edin. <xref:System.Windows.Controls.Button>Sonra <xref:System.Windows.FrameworkElement.DataContext%2A> değeri, <xref:System.Windows.Controls.DockPanel> üst öğesi olan öğesinden devralır. Yeniden yinelemek için bağlama kaynak nesnesi, bir bağlamanın gerekli dört bileşenlerinden biridir. Bu nedenle, bağlama kaynak nesnesi belirtilmeksizin bağlama hiçbir şey yapmaz.

Bağlama kaynak nesnesini belirtmek için çeşitli yollar vardır. <xref:System.Windows.FrameworkElement.DataContext%2A>Aynı kaynağa birden çok özellik bağlarken bir üst öğe üzerinde özelliğini kullanmak faydalıdır. Ancak, bazen bağlama kaynağını tek tek bağlama bildirimlerinde belirtmek daha uygun olabilir. Önceki örnekte, özelliğini kullanmak yerine, <xref:System.Windows.FrameworkElement.DataContext%2A> <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> Aşağıdaki örnekte olduğu gibi, özelliği doğrudan düğmenin bağlama bildiriminde ayarlayarak bağlama kaynağını belirtebilirsiniz.

[!code-xaml[BindNonTextPropertyCompactBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/AutoConvertPropertyToColor.xaml#BindAutoConvertColorCompactBinding)]

<xref:System.Windows.FrameworkElement.DataContext%2A>Bir öğedeki özelliği doğrudan ayarlama, <xref:System.Windows.FrameworkElement.DataContext%2A> değeri bir üst öğeden devralma (örneğin, birinci örnekteki düğme gibi) ve bağlama üzerindeki özelliği ayarlayarak bağlama kaynağını açıkça belirtme (örneğin, <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> son örnek düğme gibi), <xref:System.Windows.Data.Binding.ElementName?displayProperty=nameWithType> <xref:System.Windows.Data.Binding.RelativeSource?displayProperty=nameWithType> bağlama kaynağını belirtmek için özelliğini veya özelliğini de kullanabilirsiniz. Özelliği, bir <xref:System.Windows.Data.Binding.ElementName%2A> düğmenin genişliğini ayarlamak için kaydırıcı kullanırken olduğu gibi, uygulamanızdaki diğer öğelere bağlarken faydalıdır. <xref:System.Windows.Data.Binding.RelativeSource%2A>Özelliği, veya içinde bağlama belirtildiğinde faydalıdır <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Style> . Daha fazla bilgi için bkz. [nasıl yapılır: bağlama kaynağını belirtme](../../framework/wpf/data/how-to-specify-the-binding-source.md).

### <a name="specifying-the-path-to-the-value"></a>Değerin yolunu belirtme

Bağlama kaynağınız bir nesnedir, <xref:System.Windows.Data.Binding.Path?displayProperty=nameWithType> bağlamanız için kullanılacak değeri belirtmek için özelliğini kullanın. XML verilerine bağlıyorsanız, <xref:System.Windows.Data.Binding.XPath?displayProperty=nameWithType> değerini belirtmek için özelliğini kullanın. Bazı durumlarda, <xref:System.Windows.Data.Binding.Path%2A> VERILERINIZ XML olduğunda bile özelliği kullanmak için geçerli olabilir. Örneğin, döndürülen bir XmlNode 'un Name özelliğine (bir XPath sorgusunun sonucu olarak) erişmek istiyorsanız özelliği ek olarak özelliğini kullanmanız gerekir <xref:System.Windows.Data.Binding.Path%2A> <xref:System.Windows.Data.Binding.XPath%2A> .

Daha fazla bilgi için bkz <xref:System.Windows.Data.Binding.Path%2A> . ve <xref:System.Windows.Data.Binding.XPath%2A> özellikleri.

<xref:System.Windows.Data.Binding.Path%2A>' Nin, kullanılacak değere, bir bağlamanın dört gerekli bileşenlerinden biri olduğunu vurguladığımızda, bir nesnenin tamamına bağlamak istediğiniz senaryolarda, kullanılacak değer bağlanacak kaynak nesneyle aynı olacaktır. Bu durumlarda, bir belirtmemelidir <xref:System.Windows.Data.Binding.Path%2A> . Aşağıdaki örneği inceleyin.

[!code-xaml[EmptyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/EmptyBinding.xaml#EmptyBinding)]

Yukarıdaki örnek, boş bağlama söz dizimini kullanır: {Binding}. Bu durumda, <xref:System.Windows.Controls.ListBox> bir üst DockPanel öğesinden DataContext 'i devralır (Bu örnekte gösterilmez). Yol belirtilmediğinde, varsayılan olarak nesnenin tamamına bağlanır. Diğer bir deyişle, bu örnekte, özelliği nesnenin tamamına bağlamamız nedeniyle yol kalmadı <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> . (Ayrıntılı bir tartışma için [koleksiyonlara bağlama](#binding-to-collections) bölümüne bakın.)

Bir koleksiyona bağlama dışında, bu senaryo aynı zamanda yalnızca bir nesnenin tek bir özelliği yerine bir nesnenin tamamına bağlamak istediğinizde de yararlıdır. Örneğin, kaynak nesneniz tür ise <xref:System.String> , yalnızca dizenin kendisini bağlamak isteyebilirsiniz. Diğer bir yaygın senaryo, bir öğeyi birkaç özelliği olan bir nesneye bağlamak istemizin olur.

Verilerin, bağlantılı hedef özelliği için anlamlı olması için özel mantık uygulamanız gerekebilir. Özel mantık, varsayılan tür dönüştürmesi yoksa özel bir dönüştürücü biçiminde olabilir. Dönüştürücüler hakkında bilgi için bkz. [veri dönüştürme](#data-conversion) .

### <a name="binding-and-bindingexpression"></a>Bağlama ve BindingExpression

Veri bağlamanın diğer özelliklerine ve kullanımlarına geçmeden önce sınıfı tanıtmak yararlı olur <xref:System.Windows.Data.BindingExpression> . Önceki bölümlerde gördüğünüz gibi, <xref:System.Windows.Data.Binding> sınıfı bağlama bildirimi için üst düzey sınıftır; bir bağlamanın özelliklerini belirtmenize imkan tanıyan birçok özellik sağlar. İlişkili bir sınıf, <xref:System.Windows.Data.BindingExpression> kaynak ve hedef arasındaki bağlantıyı tutan temel nesnedir. Bağlama, birkaç bağlama ifadesi genelinde paylaşılabilen tüm bilgileri içerir. <xref:System.Windows.Data.BindingExpression>, Paylaşılamayan bir örnek ifadesidir ve öğesinin tüm örnek bilgilerini içerir <xref:System.Windows.Data.Binding> .

Aşağıdaki örneği, burada `myDataObject` sınıfının bir örneği `MyData` , `myBinding` kaynak <xref:System.Windows.Data.Binding> nesne ise ve `MyData` adlı bir dize özelliği içeren tanımlanmış bir sınıftır `ColorName` . Bu örnek, bir örneği olan öğesinin metin içeriğini `myText` öğesine bağlar <xref:System.Windows.Controls.TextBlock> `ColorName` .

[!code-csharp[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/ManualBinding.cs#CodeOnlyBinding)]
[!code-vb[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/ManualBinding.vb#CodeOnlyBinding)]

Diğer bağlamaları oluşturmak için aynı *myBinding* nesnesi kullanabilirsiniz. Örneğin, bir onay kutusunun metin içeriğini *ColorName*' e bağlamak Için *myBinding* nesnesini kullanabilirsiniz. Bu senaryoda, <xref:System.Windows.Data.BindingExpression> *myBinding* nesnesini paylaşan iki örnek olacaktır.

Bir <xref:System.Windows.Data.BindingExpression> nesne, <xref:System.Windows.Data.BindingOperations.GetBindingExpression%2A> veriye bağlı bir nesne çağırarak döndürülür. Aşağıdaki makalelerde, sınıfının kullanımları gösterilmektedir <xref:System.Windows.Data.BindingExpression> :

- [Bağımlı hedef özelliğinden bağlama nesnesi alma](../../framework/wpf/data/how-to-get-the-binding-object-from-a-bound-target-property.md)

- [TextBox metni kaynağı güncelleştirdiğinde denetleme](../../framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md)

## <a name="data-conversion"></a>Veri dönüştürme

[Bağlama oluşturma](#creating-a-binding) bölümünde düğme kırmızıdır çünkü <xref:System.Windows.Controls.Control.Background%2A> özelliği "Red" değerine sahip bir dize özelliğine bağımlıdır. Bu dize değeri, <xref:System.Windows.Media.Brush> dize değerini bir olarak dönüştürmek için türde bir tür dönüştürücüsü bulunduğundan geçerlidir <xref:System.Windows.Media.Brush> .

Bu bilgileri [bağlama oluşturma](#creating-a-binding) bölümünde şekle eklemek şuna benzer.

![Veri bağlama varsayılan özelliğini gösteren diyagram.](./media/data-binding-overview/data-binding-button-default-conversion.png)

Ancak, Binding kaynak nesnenizin dize türünde bir özelliği olması yerine ne tür bir *Color* özelliği vardır <xref:System.Windows.Media.Color> ? Bu durumda, bağlamanın çalışması için öncelikle *Color* özelliğinin değerini <xref:System.Windows.Controls.Control.Background%2A> özelliğin kabul ettiği bir şeye dönüştürmeniz gerekir. <xref:System.Windows.Data.IValueConverter>Aşağıdaki örnekte olduğu gibi, arabirimini uygulayarak özel bir dönüştürücü oluşturmanız gerekir.

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

- Target özelliği, bir bağlama koleksiyonu içerir <xref:System.Windows.Data.MultiBinding> . İçin <xref:System.Windows.Data.MultiBinding> , <xref:System.Windows.Data.IMultiValueConverter> bağlamaların değerlerinden son bir değer üretmek için özel kullanırsınız. Örneğin, aynı veya farklı bağlama kaynak nesnelerinden değer olabilen kırmızı, mavi ve yeşil değerlerden renk hesaplanabilir. <xref:System.Windows.Data.MultiBinding>Örnekler ve bilgiler için bkz..

## <a name="binding-to-collections"></a>Koleksiyonlara bağlama

Bağlama kaynak nesnesi, özellikleri veri içeren tek bir nesne olarak ya da genellikle birlikte gruplanmış çok biçimli nesnelerin veri koleksiyonu olarak (bir veritabanının bir sorgusunun sonucu gibi) değerlendirilir. Şimdiye kadar yalnızca tek nesnelere bağlamayı tartıştık. Ancak, bir veri koleksiyonuna bağlama yaygın bir senaryodur. Örneğin, yaygın bir senaryo, veya gibi bir <xref:System.Windows.Controls.ItemsControl> <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.ListView> <xref:System.Windows.Controls.TreeView> veri koleksiyonunu ( [veri bağlama nedir](#what-is-data-binding) bölümünde gösterilen uygulamadaki gibi) göstermek için kullanılır.

Neyse ki temel diyagramımız hala geçerli olur. Bir <xref:System.Windows.Controls.ItemsControl> koleksiyona bağlıyorsanız, diyagram şuna benzer şekilde görünür.

![Veri bağlama ItemControl nesnesini gösteren diyagram.](./media/data-binding-overview/data-binding-itemscontrol.png)

Bu diyagramda gösterildiği gibi, bir <xref:System.Windows.Controls.ItemsControl> koleksiyon nesnesine bağlamak için <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A?displayProperty=nameWithType> özelliği kullanılacak özelliktir. ' Nin `ItemsSource` içeriği olarak düşünebilirsiniz <xref:System.Windows.Controls.ItemsControl> . Bağlama, <xref:System.Windows.Data.BindingMode.OneWay> `ItemsSource` özelliğin `OneWay` Varsayılan olarak bağlamayı desteklediğinden kaynaklanır.

### <a name="how-to-implement-collections"></a>Koleksiyonları uygulama

Arabirimini uygulayan herhangi bir koleksiyonun üzerinde listeleme yapabilirsiniz <xref:System.Collections.IEnumerable> . Bununla birlikte, koleksiyondaki eklemelerin veya silinmelerin Kullanıcı arabirimini otomatik olarak güncelleştirmeleri için dinamik bağlamaları ayarlamak için koleksiyonun arabirimini uygulaması gerekir <xref:System.Collections.Specialized.INotifyCollectionChanged> . Bu arabirim, temeldeki koleksiyon değiştiğinde oluşturulması gereken bir olay gösterir.

WPF, <xref:System.Collections.ObjectModel.ObservableCollection%601> arabirimi kullanıma sunan bir veri koleksiyonunun yerleşik bir uygulama olan sınıfını sağlar <xref:System.Collections.Specialized.INotifyCollectionChanged> . Veri değerlerinin Kaynak nesnelerden hedeflere aktarılmasını tam olarak desteklemek için, koleksiyonunuzdaki bağlanabilir özellikleri destekleyen her nesnenin de arabirimini uygulaması gerekir <xref:System.ComponentModel.INotifyPropertyChanged> . Daha fazla bilgi için bkz. [bağlama kaynaklarına genel bakış](../../framework/wpf/data/binding-sources-overview.md).

Kendi koleksiyonunuzu uygulamadan önce,, ve gibi <xref:System.Collections.ObjectModel.ObservableCollection%601> var olan koleksiyon sınıflarından birini ya da <xref:System.Collections.Generic.List%601> <xref:System.Collections.ObjectModel.Collection%601> birçok başka konuda kullanmayı düşünün <xref:System.ComponentModel.BindingList%601> . Gelişmiş bir senaryonuz varsa ve kendi koleksiyonunuzu uygulamak istiyorsanız <xref:System.Collections.IList> , dizin tarafından ayrı ayrı erişilebilen nesnelerin genel olmayan bir koleksiyonunu sağlayan öğesini kullanmayı düşünün ve bu sayede en iyi performansı elde edebilirsiniz.

### <a name="collection-views"></a>Koleksiyon görünümleri

<xref:System.Windows.Controls.ItemsControl>Bir veri koleksiyonu bağladıktan sonra verileri sıralamak, filtrelemek veya gruplandırmak isteyebilirsiniz. Bunu yapmak için, arabirimini uygulayan sınıflar olan koleksiyon görünümlerini kullanırsınız <xref:System.ComponentModel.ICollectionView> .

#### <a name="what-are-collection-views"></a>Koleksiyon görünümleri nelerdir?

Koleksiyon görünümü, temel kaynak koleksiyonun kendisini değiştirmek zorunda kalmadan sıralama, filtre ve grup sorgularına göre kaynak koleksiyonunu gezinmenize ve görüntülemenize olanak tanıyan bir bağlama kaynak koleksiyonunun en üstünde yer alan bir katmandır. Koleksiyon görünümü Ayrıca koleksiyondaki geçerli öğe için bir işaretçi tutar. Kaynak koleksiyon arabirimini uygularsa <xref:System.Collections.Specialized.INotifyCollectionChanged> , olay tarafından oluşturulan değişiklikler <xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged> görünümlere yayılır.

Görünümler temeldeki kaynak koleksiyonlarını değiştirmediğinden, her kaynak koleksiyonda ilişkili birden fazla görünüm bulunabilir. Örneğin, *görev* nesneleri koleksiyonunuz olabilir. Görünümlerin kullanımı ile aynı verileri farklı yollarla görüntüleyebilirsiniz. Örneğin, sayfanızın sol tarafında önceliğe göre sıralanmış görevleri ve sağ tarafa alana göre gruplanmış olarak göstermek isteyebilirsiniz.

#### <a name="how-to-create-a-view"></a>Görünüm oluşturma

Bir görünüm oluşturmanın ve kullanmanın bir yolu, doğrudan görünüm nesnesini oluşturmak ve bunu bağlama kaynağı olarak kullanmaktır. Örneğin, [veri bağlama tanıtımı bölümünde gösterilen](#what-is-data-binding) [veri bağlama tanıtım][data-binding-demo] uygulamasını göz önünde bulundurun. Uygulama, <xref:System.Windows.Controls.ListBox> veri toplamayı doğrudan değil, veri koleksiyonu üzerinden bir görünüme bağlamalara uygulanır. Aşağıdaki örnek, [veri bağlama tanıtım][data-binding-demo] uygulamasından ayıklanır. <xref:System.Windows.Data.CollectionViewSource>Sınıfı, öğesinden devralan bir SıNıFıN xaml ara sunucusu <xref:System.Windows.Data.CollectionView> . Bu örnekte, <xref:System.Windows.Data.CollectionViewSource.Source%2A> görünümün geçerli uygulama nesnesinin *AuctionItems* koleksiyonuna (türü) bağlanması gerekir <xref:System.Collections.ObjectModel.ObservableCollection%601> .

[!code-xaml[CollectionView](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#CollectionView)]

*ListingDataView* kaynağı daha sonra uygulamadaki öğeler için bağlama kaynağı olarak görev yapar (örneğin,) <xref:System.Windows.Controls.ListBox> .

[!code-xaml[ListBoxCollectionView](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#ListBoxCollectionView)]

Aynı koleksiyon için başka bir görünüm oluşturmak üzere başka bir <xref:System.Windows.Data.CollectionViewSource> örnek oluşturabilir ve buna farklı bir `x:Key` ad verebilirsiniz.

Aşağıdaki tabloda, varsayılan koleksiyon görünümü olarak veya <xref:System.Windows.Data.CollectionViewSource> Kaynak koleksiyon türüne göre hangi görünüm verisi türlerinin oluşturulduğu gösterilmektedir.

| Kaynak koleksiyon türü                    | Koleksiyon görünüm türü | Notlar |
| ----------------------------------------- | -------------------- | ----- |
| <xref:System.Collections.IEnumerable>     | Temelinde bir iç tür <xref:System.Windows.Data.CollectionView> | Öğeler gruplandırılamıyor. |
| <xref:System.Collections.IList>           | <xref:System.Windows.Data.ListCollectionView> | En hızlı. |
| <xref:System.ComponentModel.IBindingList> | <xref:System.Windows.Data.BindingListCollectionView> | |

#### <a name="using-a-default-view"></a>Varsayılan görünüm kullanma

Bir koleksiyon görünümünü bağlama kaynağı olarak belirtme, koleksiyon görünümü oluşturmanın ve kullanmanın bir yoludur. WPF ayrıca, bağlama kaynağı olarak kullanılan her koleksiyon için varsayılan bir koleksiyon görünümü oluşturur. Doğrudan bir koleksiyona bağlarsanız, WPF varsayılan görünümüne bağlanır. Bu varsayılan görünüm, aynı koleksiyondaki tüm bağlamalar tarafından paylaşılır. bu nedenle, bir bağlantılı denetim veya kodla (sıralama ya da geçerli öğe işaretçisine yapılan bir değişiklik gibi) bir varsayılan görünümde yapılan değişiklik, aynı koleksiyona yapılan diğer tüm bağlamalara yansıtılır.

Varsayılan görünümü almak için <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> yöntemini kullanırsınız. Bir örnek için bkz. [veri koleksiyonunun varsayılan görünümünü edinme](../../framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md).

#### <a name="collection-views-with-adonet-datatables"></a>ADO.NET DataTable ile koleksiyon görünümleri

Performansı artırmak için, ADO.NET veya nesneleri için koleksiyon görünümleri, sıralama <xref:System.Data.DataTable> <xref:System.Data.DataView> <xref:System.Data.DataView> ve filtreleme ile veri kaynağının tüm koleksiyon görünümlerinde paylaşılmasına neden olur. Her koleksiyon görünümünün bağımsız olarak sıralanmasını ve filtrelemesine olanak tanımak için her koleksiyon görünümünü kendi nesnesiyle başlatın <xref:System.Data.DataView> .

#### <a name="sorting"></a>Sıralama

Daha önce bahsedildiği gibi, görünümler bir koleksiyona sıralama düzeni uygulayabilir. Temel koleksiyonda olduğu gibi, verileriniz ilgili ve kendine özgü bir sıraya sahip olabilir veya olmayabilir. Koleksiyon üzerindeki görünüm, sağladığınız karşılaştırma ölçütlerine göre bir sipariş veya varsayılan sırayı değiştirmenize olanak sağlar. Verilerin istemci tabanlı bir görünümü olduğundan, yaygın olarak kullanılan bir senaryo, kullanıcının sütun için karşılık gelen tablo verilerinin sütunlarını sütuna karşılık geldiği bir değere göre sıralamak isteyebilir. Görünümleri kullanarak, bu kullanıcı odaklı sıralama, temel koleksiyonda herhangi bir değişiklik yapılmadan veya koleksiyon içeriğini yeniden sorgulamak zorunda kalmadan uygulanabilir. Bir örnek için bkz. [bir başlık tıklandığında GridView sütununu sıralama](../../framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).

Aşağıdaki örnek, <xref:System.Windows.Controls.CheckBox> [veri bağlama nedir](#what-is-data-binding) bölümünde uygulama kullanıcı arabirimindeki "kategoriye göre sıralama ve tarihe göre sırala" öğesinin sıralama mantığını gösterir.

[!code-csharp[AddSortChecked](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#AddSortChecked)]
[!code-vb[AddSortChecked](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#AddSortChecked)]

#### <a name="filtering"></a>Filtreleme

Görünümler bir koleksiyona bir filtre de uygulayabilir, böylece görünüm tam koleksiyonun yalnızca belirli bir alt kümesini gösterir. Verilerdeki bir koşula filtre ekleyebilirsiniz. Örneğin, [veri bağlama nedir](#what-is-data-binding) bölümünde uygulama tarafından yapıldığı gibi, "yalnızca Barkazancı göster", <xref:System.Windows.Controls.CheckBox> Maliyet $25 veya daha fazla olan öğeleri filtrelemek için mantık içerir. Aşağıdaki kod, seçildiğinde, *ShowOnlyBargainsFilter* öğesini olay işleyicisi olarak ayarlamak için yürütülür <xref:System.Windows.Data.CollectionViewSource.Filter> <xref:System.Windows.Controls.CheckBox> .

[!code-csharp[ListingViewFilter](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#ListingViewFilter)]
[!code-vb[ListingViewFilter](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#ListingViewFilter)]

*ShowOnlyBargainsFilter* olay işleyicisi aşağıdaki uygulamaya sahiptir.

[!code-csharp[FilterEvent](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#FilterEvent)]
[!code-vb[FilterEvent](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#FilterEvent)]

<xref:System.Windows.Data.CollectionView>Yerine doğrudan sınıflardan birini kullanıyorsanız <xref:System.Windows.Data.CollectionViewSource> , <xref:System.Windows.Data.CollectionView.Filter%2A> bir geri çağırma belirtmek için özelliğini kullanın. Bir örnek için bkz. [bir görünümdeki verileri filtreleme](../../framework/wpf/data/how-to-filter-data-in-a-view.md).

#### <a name="grouping"></a>Gruplandırma

Bir koleksiyonu görüntüleyen iç sınıf hariç <xref:System.Collections.IEnumerable> , tüm koleksiyon görünümleri, kullanıcının koleksiyon görünümündeki koleksiyonu mantıksal gruplar halinde bölümlamasına olanak sağlayan *gruplandırmayı*destekler. Gruplar, kullanıcının grupların bir listesini sağladığı veya örtük olarak, grupların verilere göre dinamik olarak oluşturulduğu açık olabilir.

Aşağıdaki örnekte, "kategoriye göre gruplandırma" mantığı gösterilmektedir <xref:System.Windows.Controls.CheckBox> .

[!code-csharp[ListingGroupCheck](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#ListingGroupCheck)]
[!code-vb[ListingGroupCheck](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#ListingGroupCheck)]

Başka bir gruplandırma örneği için bkz. [GridView uygulayan bir ListView Içindeki öğeleri gruplandırma](../../framework/wpf/controls/how-to-group-items-in-a-listview-that-implements-a-gridview.md).

#### <a name="current-item-pointers"></a>Geçerli öğe işaretçileri

Görünümler, geçerli bir öğe kavramını da destekler. Bir koleksiyon görünümündeki nesneler arasında gezinebilirsiniz. Gezindiğinizde, koleksiyonda belirli bir konumda bulunan nesneyi almanıza izin veren bir öğe işaretçisini taşıyor olursunuz. Bir örnek için bkz. [Data CollectionView içindeki nesneler arasında gezinme](../../framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).

WPF bir koleksiyona yalnızca bir görünüm (belirttiğiniz bir görünüm veya koleksiyonun varsayılan görünümü) kullanarak bağlandığından, koleksiyonlara yönelik tüm bağlamaların geçerli öğe işaretçisi vardır. Bir görünüme bağlanırken, bir değer içindeki eğik çizgi ("/") karakteri `Path` görünümün geçerli öğesini belirler. Aşağıdaki örnekte, veri bağlamı bir koleksiyon görünümüdür. İlk satır koleksiyona bağlanır. İkinci satır koleksiyondaki geçerli öğeye bağlanır. Üçüncü satır `Description` koleksiyondaki geçerli öğenin özelliğine bağlar.

```xaml
<Button Content="{Binding }" />
<Button Content="{Binding Path=/}" />
<Button Content="{Binding Path=/Description}" />
```

Eğik çizgi ve özellik söz dizimi bir koleksiyon hiyerarşisinin çapraz geçişini sağlamak için de yığınlanalabilir. Aşağıdaki örnek `Offices` , kaynak koleksiyonun geçerli öğesinin bir özelliği olan adlı bir koleksiyonun geçerli öğesine bağlar.

```xaml
<Button Content="{Binding /Offices/}" />
```

Geçerli öğe işaretçisi, koleksiyona uygulanan sıralama veya filtrelemeden etkilenebilir. Sıralama, seçili son öğe üzerinde geçerli öğe işaretçisini korur, ancak koleksiyon görünümü artık bunun etrafında yeniden yapılandırılmış. (Belki de seçili öğe listenin başında, ancak artık seçili öğe ortada bir yerde olabilir.) Filtre, filtreleme sonrasında Görünüm ' de kalırsa, seçili öğeyi korur. Aksi takdirde, geçerli öğe işaretçisi filtrelenmiş koleksiyon görünümünün ilk öğesine ayarlanır.

#### <a name="master-detail-binding-scenario"></a>Ana-ayrıntı bağlama senaryosu

Geçerli bir öğe kavramı yalnızca bir koleksiyondaki öğelerin gezinmesi için değil, aynı zamanda ana ayrıntı bağlama senaryosu için de kullanışlıdır. [Veri bağlama nedir](#what-is-data-binding) bölümünde uygulama kullanıcı arabirimini de göz önünde bulundurun. Bu uygulamada, içindeki seçim içinde <xref:System.Windows.Controls.ListBox> gösterilen içeriği belirler <xref:System.Windows.Controls.ContentControl> . Bir öğe seçildiğinde, bu öğeyi başka bir şekilde koymak için <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.ContentControl> Seçili öğenin ayrıntılarını gösterir.

Aynı görünüme iki veya daha fazla denetim bağlayarak, ana ayrıntı senaryosunu uygulayabilirsiniz. [Veri bağlama tanıtımında][data-binding-demo] bulunan aşağıdaki örnek, <xref:System.Windows.Controls.ListBox> ve <xref:System.Windows.Controls.ContentControl> [veri bağlama nedir](#what-is-data-binding) bölümünde uygulama kullanıcı arabiriminde gördüğünüz ve ' nin işaretlemesini gösterir.

[!code-xaml[ListBoxContentControl](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#ListBoxContentControl)]

Denetimlerin her ikisinin de aynı kaynağa, *listingDataView* statik kaynağına ( [bir görünüm oluşturma bölümünde](#how-to-create-a-view)bu kaynağın tanımına bakın) bağlandığını unutmayın. Bu bağlama, tek bir nesne ( <xref:System.Windows.Controls.ContentControl> Bu durumda) bir koleksiyon görünümüne bağlı olduğunda otomatik olarak görünümün öğesine bağlandığı için geçerlidir <xref:System.Windows.Data.CollectionView.CurrentItem%2A> . <xref:System.Windows.Data.CollectionViewSource>Nesneler, para birimini ve seçimi otomatik olarak eşitler. Liste denetiminiz bir <xref:System.Windows.Data.CollectionViewSource> nesneye bu örnekte olduğu gibi bağlanmazsa, <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> bunun çalışması için özelliğini olarak ayarlamanız gerekir `true` .

Diğer örnekler için bkz. [bir koleksiyona bağlama ve seçime göre bilgi görüntüleme](../../framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md) ve [hiyerarşik verilerle ana ayrıntı modelini kullanma](../../framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md).

Yukarıdaki örneğin bir şablon kullandığını fark etmiş olabilirsiniz. Aslında, veriler şablonlar kullanılmadan (tarafından açıkça kullanılan ve tarafından örtülü olarak kullanılan), istediğimiz şekilde gösterilmez <xref:System.Windows.Controls.ContentControl> <xref:System.Windows.Controls.ListBox> . Şimdi, sonraki bölümde veri şablonu oluşturma özelliğini kullanacağız.

## <a name="data-templating"></a>Veri şablonu oluşturma

Veri şablonlarının kullanımı olmadan, uygulama Kullanıcı arabirimimiz [veri bağlama](#what-is-data-binding) bölümünde aşağıdaki gibi görünür.

![Veri şablonları olmadan veri bağlama tanıtımı](./media/data-binding-overview/demo-no-template.png)

Önceki bölümde gösterildiği gibi, hem <xref:System.Windows.Controls.ListBox> Denetim hem de <xref:System.Windows.Controls.ContentControl> tüm koleksiyon nesnesine (ya da daha fazla özellikle, koleksiyon nesnesi üzerinde Görünüm), *AuctionItem*s ' nin tamamına bağlanır. Veri koleksiyonunun nasıl görüntüleneceği konusunda belirli yönergeler olmadan, <xref:System.Windows.Controls.ListBox> temel alınan koleksiyondaki her nesnenin dize gösterimini görüntüler ve <xref:System.Windows.Controls.ContentControl> bağladığına ait nesnenin dize temsilini görüntüler.

Bu sorunu çözmek için uygulama tanımlar <xref:System.Windows.DataTemplate?text=DataTemplates> . Önceki bölümdeki örnekte gösterildiği gibi, <xref:System.Windows.Controls.ContentControl> açıkça *Ayrıntılar Productlistingtemplate* veri şablonunu kullanır. <xref:System.Windows.Controls.ListBox>Denetim, koleksiyonda *AuctionItem* nesnelerini görüntülerken aşağıdaki veri şablonunu örtülü olarak kullanır.

[!code-xaml[AuctionItemDataTemplate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#AuctionItemDataTemplate)]

Bu iki DataTemplate kullanımı ile elde edilen kullanıcı arabirimi, [veri bağlama nedir](#what-is-data-binding) bölümünde gösterilen şeydir. Söz konusu ekran görüntüsünden görebileceğiniz gibi, denetimlerinizde veri yerleştirmenize izin vermenin yanı sıra DataTemplates verileriniz için etkileyici görseller tanımlamanızı sağlar. Örneğin, <xref:System.Windows.DataTrigger> yukarıda ' de, <xref:System.Windows.DataTemplate> *özelleştirilmiş özellikler* içeren *AuctionItem*s 'in, turuncu bir kenarlık ve yıldız *HighLight* ile görüntülenebilmesi için, yukarıda ' de kullanılır.

Veri şablonları hakkında daha fazla bilgi için bkz. [veri şablonu oluşturmaya genel bakış](../../framework/wpf/data/data-templating-overview.md).

## <a name="data-validation"></a>Veri doğrulama

Kullanıcının beklenen bilgileri girdiğinden emin olmak için Kullanıcı girişi kullanan çoğu uygulamanın doğrulama mantığı olması gerekir. Doğrulama denetimleri tür, Aralık, biçim veya uygulamaya özgü diğer gereksinimlere göre yapılabilir. Bu bölümde, veri doğrulamanın WPF 'de nasıl çalıştığı açıklanmaktadır.

### <a name="associating-validation-rules-with-a-binding"></a>Doğrulama kurallarını bir bağlama ile ilişkilendirme

WPF veri bağlama modeli, nesneniz ile ilişkilendirmenize olanak tanır <xref:System.Windows.Data.Binding.ValidationRules%2A> <xref:System.Windows.Data.Binding> . Örneğin, aşağıdaki örnek öğesini <xref:System.Windows.Controls.TextBox> adlı bir özelliğe bağlar `StartPrice` ve özelliğine bir nesne ekler <xref:System.Windows.Controls.ExceptionValidationRule> <xref:System.Windows.Data.Binding.ValidationRules%2A?displayProperty=nameWithType> .

[!code-xaml[TextboxStartPrice](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextboxStartPrice)]

Bir <xref:System.Windows.Controls.ValidationRule> nesne, özelliğin değerinin geçerli olup olmadığını denetler. WPF 'de iki tür yerleşik <xref:System.Windows.Controls.ValidationRule> nesne vardır:

- <xref:System.Windows.Controls.ExceptionValidationRule>Bağlama kaynağı özelliğinin güncelleştirilmesi sırasında oluşturulan özel durumları denetler. Önceki örnekte, `StartPrice` integer türündedir. Kullanıcı tamsayıya dönüştürülemeyen bir değer girdiğinde, bir özel durum oluşturulur ve bağlamanın geçersiz olarak işaretlenmesine neden olur. Açıkça ayarlamaya yönelik alternatif bir sözdizimi, <xref:System.Windows.Controls.ExceptionValidationRule> <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> veya nesneniz için özelliğini olarak ayarlanmıştır `true` <xref:System.Windows.Data.Binding> <xref:System.Windows.Data.MultiBinding> .

- Bir <xref:System.Windows.Controls.DataErrorValidationRule> nesnesi, arabirimini uygulayan nesneler tarafından oluşturulan hataları denetler <xref:System.ComponentModel.IDataErrorInfo> . Bu doğrulama kuralını kullanmayla ilgili bir örnek için bkz <xref:System.Windows.Controls.DataErrorValidationRule> .. Açıkça ayarlamaya yönelik alternatif bir sözdizimi, <xref:System.Windows.Controls.DataErrorValidationRule> <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> veya nesneniz için özelliğini olarak ayarlanmıştır `true` <xref:System.Windows.Data.Binding> <xref:System.Windows.Data.MultiBinding> .

Ayrıca, sınıfından türeterek ve metodunu uygulayarak kendi doğrulama kuralınızı de oluşturabilirsiniz <xref:System.Windows.Controls.ValidationRule> <xref:System.Windows.Controls.ValidationRule.Validate%2A> . Aşağıdaki örnek, *Add Product Listing* <xref:System.Windows.Controls.TextBox> [veri bağlama nedir](#what-is-data-binding) bölümünde "başlangıç tarihi" ürün ekleme listesi tarafından kullanılan kuralı gösterir.

[!code-csharp[FutureDateRule](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/FutureDateRule.cs#FutureDateRule)]
[!code-vb[FutureDateRule](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/FutureDateRule.vb#FutureDateRule)]

*StartDateEntryForm* , <xref:System.Windows.Controls.TextBox> Aşağıdaki örnekte gösterildiği gibi bu *Futuredadterule*öğesini kullanır.

[!code-xaml[TextboxStartDate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextboxStartDate)]

Değer olduğundan <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> , bağlama altyapısı her tuş vuruşunda kaynak değerini günceller, bu da <xref:System.Windows.Data.Binding.ValidationRules%2A> her tuş vuruşu üzerinde koleksiyondaki her kuralı denetlediği anlamına gelir. Bunu doğrulama Işlemi bölümünde ele aldık.

### <a name="providing-visual-feedback"></a>Görsel geri bildirim sağlama

Kullanıcı geçersiz bir değer girerse, uygulama kullanıcı arabiriminde hata hakkında bazı geri bildirimler sağlamak isteyebilirsiniz. Bu tür geri bildirimde bulunmak için bir yol, <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> ekli özelliği özel olarak ayarlamaya yönelik bir yoldur <xref:System.Windows.Controls.ControlTemplate> . Önceki alt bölümde gösterildiği gibi, *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> adlı bir *validationTemplate*'i kullanır. Aşağıdaki örnek *validationTemplate*tanımını gösterir.

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#ControlTemplate)]

<xref:System.Windows.Controls.AdornedElementPlaceholder>Öğesi, donatılan denetimin yerleştirilmesi gereken yeri belirtir.

Ayrıca, <xref:System.Windows.Controls.ToolTip> hata iletisini göstermek için de kullanabilirsiniz. Hem *StartDateEntryForm* hem de *StartPriceEntryForm*, <xref:System.Windows.Controls.TextBox> hata Iletisini görüntüleyen bir oluşturan *textStyleTextBox*stilini kullanır <xref:System.Windows.Controls.ToolTip> . Aşağıdaki örnek *textStyleTextBox*'ın tanımını gösterir. İliştirilmiş özelliği, <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> `true` bağlı öğenin özelliklerindeki bir veya daha fazla bağlamanın hatalı olması durumunda olur.

[!code-xaml[TextBoxStyle](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextBoxStyle)]

Özel ve ile, <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> <xref:System.Windows.Controls.ToolTip> bir doğrulama hatası olduğunda *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> aşağıdaki gibi görünür.

![Veri bağlama doğrulama hatası](./media/data-binding-overview/demo-validation-date.png "DataBindingDemo_Validation")

Eğer hesabınız, <xref:System.Windows.Data.Binding> doğrulama kurallarına sahipse ancak <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> ilişkili denetimde belirtmezseniz, bir <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> doğrulama hatası olduğunda kullanıcıları bilgilendirmek için varsayılan olarak kullanılır. Varsayılan değer, <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> donatıcı katmanında kırmızı bir kenarlığı tanımlayan bir denetim şablonudur. Varsayılan ve ile, <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> <xref:System.Windows.Controls.ToolTip> *STARTPRICEENTRYFORM* Kullanıcı arabirimi, <xref:System.Windows.Controls.TextBox> doğrulama hatası olduğunda aşağıdaki gibi görünür.

![Veri bağlama doğrulama hatası](./media/data-binding-overview/demo-validation-price.png "DataBindingDemo_ValidationDefault")

Bir iletişim kutusundaki tüm denetimleri doğrulamaya yönelik mantık sağlama hakkında bir örnek için [iletişim kutularında](../../framework/wpf/app-development/dialog-boxes-overview.md)özel iletişim kutuları bölümüne bakın.

### <a name="validation-process"></a>Doğrulama işlemi

Doğrulama genellikle bir hedefin değeri bağlama kaynağı özelliğine aktarıldığında oluşur. Bu aktarım <xref:System.Windows.Data.BindingMode.TwoWay> , ve <xref:System.Windows.Data.BindingMode.OneWayToSource> bağlamalarda gerçekleşir. Yeniden yinelemek için, bir kaynak güncelleştirmesine neden olan kaynak <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> [güncelleştirmelerini tetikleyen](#what-triggers-source-updates) bölümünde açıklandığı gibi, özelliğin değerine bağlıdır.

Aşağıdaki öğeler *doğrulama* işlemini anlatmaktadır. Bu işlem sırasında herhangi bir doğrulama hatası veya başka türde bir hata oluşursa, işlem durdurulur:

1. Bağlama altyapısı, olarak ayarlanmış herhangi bir özel nesne olup olmadığını denetler <xref:System.Windows.Controls.ValidationRule> <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> <xref:System.Windows.Controls.ValidationStep.RawProposedValue> <xref:System.Windows.Data.Binding> ; Bu durumda, <xref:System.Windows.Controls.ValidationRule.Validate%2A> <xref:System.Windows.Controls.ValidationRule> biri bir hata halinde çalıştırana kadar veya hepsi geçene kadar her bir yöntemi çağırır.

2. Bağlama altyapısı, varsa dönüştürücüyü çağırır.

3. Dönüştürücü başarılı olursa bağlama motoru, için olarak ayarlanmış herhangi bir özel nesne olup olmadığını denetler <xref:System.Windows.Controls.ValidationRule> <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> <xref:System.Windows.Data.Binding> ; Bu durumda, <xref:System.Windows.Controls.ValidationRule.Validate%2A> <xref:System.Windows.Controls.ValidationRule> <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> biri bir hata halinde veya hepsi geçene kadar ayarlanmış olan her bir yöntem için olarak ayarlanan her bir yöntemi çağırır.

4. Bağlama altyapısı, kaynak özelliğini ayarlar.

5. Bağlama altyapısı, için olarak ayarlanmış herhangi bir özel nesne olup olmadığını denetler <xref:System.Windows.Controls.ValidationRule> <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> <xref:System.Windows.Controls.ValidationStep.UpdatedValue> <xref:System.Windows.Data.Binding> ; Bu durumda, <xref:System.Windows.Controls.ValidationRule.Validate%2A> <xref:System.Windows.Controls.ValidationRule> <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> <xref:System.Windows.Controls.ValidationStep.UpdatedValue> biri bir hata halinde çalıştırana kadar ya da hepsi geçene kadar ayarlanmış olan her bir bir yöntemi çağırır. Bir <xref:System.Windows.Controls.DataErrorValidationRule> bağlama ile ilişkiliyse ve <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> Bu, varsayılan olarak ayarlanırsa, <xref:System.Windows.Controls.ValidationStep.UpdatedValue> <xref:System.Windows.Controls.DataErrorValidationRule> Bu noktada denetlenir. Bu noktada, olarak ayarlanmış herhangi bir bağlama <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> `true` denetlenir.

6. Bağlama altyapısı, için olarak ayarlanmış herhangi bir özel nesne olup olmadığını denetler <xref:System.Windows.Controls.ValidationRule> <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> <xref:System.Windows.Controls.ValidationStep.CommittedValue> <xref:System.Windows.Data.Binding> ; Bu durumda, <xref:System.Windows.Controls.ValidationRule.Validate%2A> <xref:System.Windows.Controls.ValidationRule> <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> <xref:System.Windows.Controls.ValidationStep.CommittedValue> biri bir hata halinde çalıştırana kadar ya da hepsi geçene kadar ayarlanmış olan her bir bir yöntemi çağırır.

<xref:System.Windows.Controls.ValidationRule>Bu işlem boyunca hiçbir zaman geçemezse bağlama altyapısı bir <xref:System.Windows.Controls.ValidationError> nesnesi oluşturur ve onu <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> bağlantılı öğenin koleksiyonuna ekler. Bağlama altyapısı <xref:System.Windows.Controls.ValidationRule> herhangi bir adımda nesneleri çalıştırmadan önce, söz konusu <xref:System.Windows.Controls.ValidationError> <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> adım sırasında bağlı öğenin Ekli özelliğine eklenen her türlü öğeyi kaldırır. Örneğin, bir,,, bir <xref:System.Windows.Controls.ValidationRule> <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> <xref:System.Windows.Controls.ValidationStep.UpdatedValue> sonraki doğrulama işlemi başarısız olduğunda, bağlama altyapısı, <xref:System.Windows.Controls.ValidationError> <xref:System.Windows.Controls.ValidationRule> olarak ayarlanmış herhangi bir ' i çağırmadan önce onu kaldırır <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> <xref:System.Windows.Controls.ValidationStep.UpdatedValue> .

<xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType>Boş olmadığında, <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> öğesinin ekli özelliği olarak ayarlanır `true` . Ayrıca, <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A> öğesinin özelliği <xref:System.Windows.Data.Binding> olarak ayarlandıysa `true` , bağlama altyapısı <xref:System.Windows.Controls.Validation.Error?displayProperty=nameWithType> öğesinde ekli olayı başlatır.

Ayrıca, her iki yönde de geçerli bir değer aktarımının (hedeften kaynağa veya kaynaktan hedefe) ekli özelliği temizlemiş olduğunu unutmayın <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> .

Bağlama onunla ilişkili bir varsa <xref:System.Windows.Controls.ExceptionValidationRule> veya <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> özelliği olarak ayarlanmışsa ya da `true` bağlama altyapısı kaynağı ayarlarsa, bağlama altyapısı bir olup olmadığını denetler <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> . Özel <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> durumları işlemek için özel bir işleyici sağlamak üzere geri aramayı kullanma seçeneğiniz vardır. ' Nde <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> belirtilmemişse <xref:System.Windows.Data.Binding> , bağlama motoru <xref:System.Windows.Controls.ValidationError> özel durum ile bir oluşturur ve onu <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> bağlı öğenin koleksiyonuna ekler.

## <a name="debugging-mechanism"></a>Hata ayıklama mekanizması

<xref:System.Diagnostics.PresentationTraceSources.TraceLevel%2A?displayProperty=nameWithType>Belirli bir bağlamanın durumu hakkında bilgi almak için bağlama ile ilgili nesne üzerinde iliştirilmiş özelliğini ayarlayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.DataErrorValidationRule>
- [LINQ sorgusunun sonuçlarına bağlama](../../framework/wpf/data/how-to-bind-to-the-results-of-a-linq-query.md)
- [Veri bağlama](../../framework/wpf/advanced/optimizing-performance-data-binding.md)
- [Veri bağlama tanıtımı][data-binding-demo]
- [Nasıl yapılır makaleleri](../../framework/wpf/data/data-binding-how-to-topics.md)
- [ADO.NET veri kaynağına bağlama](../../framework/wpf/data/how-to-bind-to-an-ado-net-data-source.md)

[data-binding-demo]: https://github.com/microsoft/WPF-Samples/tree/master/Sample%20Applications/DataBindingDemo "veri bağlama tanıtım uygulaması"
