---
title: Veri bağlamaya genel bakış
description: .NET Core için Windows Presentation Foundation'da projenize ekleyebileceğiniz farklı veri kaynakları hakkında bilgi edinin. Dinamik uygulamalar oluşturmak için veri kaynakları XAML öğelerine bağlanabilir.
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
# <a name="data-binding-overview-in-wpf"></a>WPF'de veri bağlama genel bakış

Windows Presentation Foundation 'da (WPF) veri bağlama, uygulamaların verileri sunması ve bunlarla etkileşimde bulunması için basit ve tutarlı bir yol sağlar. Öğeler .NET nesneleri ve XML şeklinde çeşitli veri kaynaklarından gelen verilere bağlanabilir. Tek <xref:System.Windows.Controls.ContentControl> veri <xref:System.Windows.Controls.Button> öğelerinin veya <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.ListView>veri öğelerikoleksiyonlarının esnek bir şekilde şekillendirilmesini sağlamak için yerleşik işlevsellik gibi herhangi bir ve herhangi bir <xref:System.Windows.Controls.ItemsControl>işlev vardır. Verilerin üzerinde sıralama, filtreleme ve grup görünümleri oluşturulabilir.

WPF'deki veri bağlama işlevi, çok çeşitli özelliklerle veri bağlama için doğal destek, verilerin esnek UI gösterimi ve iş mantığının UI'den temiz ayrılması dahil olmak üzere geleneksel modellere göre çeşitli avantajlara sahiptir.

Bu makalede, önce WPF veri bağlama için temel kavramları <xref:System.Windows.Data.Binding> tartışır ve daha sonra sınıfın kullanımı ve veri bağlama diğer özellikleri kapsar.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="what-is-data-binding"></a>Veri bağlama nedir?

Veri bağlama, uygulama arabirimi ile görüntüleþtistirilen veriler arasýnda bir bağlantı kuran bir iþlemidir. Bağlama doğru ayarlara sahipse ve veriler doğru bildirimleri sağlıyorsa, veriler değerini değiştirdiğinde, verilere bağlı öğeler değişiklikleri otomatik olarak yansıtır. Veri bağlama, bir öğedeki verilerin dış gösterimi değişirse, temel verilerin değişikliği yansıtacak şekilde otomatik olarak güncelleştirilebildiği anlamına da gelebilir. Örneğin, kullanıcı bir `TextBox` öğedeki değeri değiştirirse, temel veri değeri bu değişikliği yansıtacak şekilde otomatik olarak güncelleştirilir.

Veri bağlamanın tipik bir kullanımı, sunucu veya yerel yapılandırma verilerini formlara veya diğer Web-kullanım birimi denetimlerine yerleştirmektir. WPF'de bu kavram, çok çeşitli veri kaynaklarına çok çeşitli özellikleri bağlamayı içerecek şekilde genişletilir. WPF'de, öğelerin bağımlılık özellikleri .NET nesnelerine (Web Hizmetleri ve Web özellikleriyle ilişkili ADO.NET nesneler veya nesneler dahil) ve XML verilerine bağlanabilir.

Veri bağlama örneğinde, açık artırma öğelerinin listesini görüntüleyen [Veri Bağlama Demo'ndan][data-binding-demo]aşağıdaki uygulama Ara Birimi'ne bir göz atın.

![Veri bağlama örnek ekran görüntüsü](./media/data-binding-overview/demo.png "DataBinding_DataBindingDemo")

Uygulama veri bağlama nın aşağıdaki özelliklerini gösterir:

- ListBox'ın içeriği *AuctionItem* nesnelerinden oluşan bir koleksiyona bağlıdır. Bir *AuctionItem* *nesnesi Açıklama,* *Başlangıç Fiyatı,* *Başlangıç Tarihi,* *Kategori,* *Özel Özellikler*ve benzeri özelliklere sahiptir.

- Veriler *(AuctionItem* nesneleri) `ListBox` her öğe için açıklama ve geçerli fiyat gösterilecek şekilde şablonlanır. Şablon bir <xref:System.Windows.DataTemplate>. Ayrıca, her öğenin görünümü, görüntülenen *AuctionItem'in* *Özel Özellikler* değerine bağlıdır. *AuctionItem'in* *Özel Özellikler* değeri *Renk*ise, öğenin mavi bir kenarlığı vardır. Değer *Vurgulanırsa,* öğenin turuncu bir kenarlığı ve bir yıldızı vardır. [Veri Templating](#data-templating) bölümü veri templating hakkında bilgi sağlar.

- `CheckBoxes` Kullanıcı, sağlanan verileri gruplayabilir, filtreleyebilir veya sıralayabilir. Yukarıdaki resimde, kategoriye ve **kategoriye ve tarihe** `CheckBoxes` **göre Gruplandırma** seçilir. Verilerin ürünün kategorisine göre gruplandırış olduğunu ve kategori adının alfabetik sırada olduğunu fark etmiş olabilirsiniz. Görüntüden fark etmek zordur, ancak öğeler de her kategorideki başlangıç tarihine göre sıralanır. Sıralama bir koleksiyon *görünümü*kullanılarak yapılır. [Koleksiyonlara Bağlama](#binding-to-collections) bölümü koleksiyon görünümlerini tartışır.

- Kullanıcı bir öğe yi seçtiğinde, seçili öğenin ayrıntılarını <xref:System.Windows.Controls.ContentControl> görüntüler. Bu deneyim, *Ana ayrıntı senaryosu*olarak adlandırılır. [Ana ayrıntı senaryosu](#master-detail-binding-scenario) bölümü, bu tür bağlama hakkında bilgi sağlar.

- *StartDate* özelliğinin <xref:System.DateTime>türü, milisaniyeye zamanı içeren bir tarih döndürür. Bu uygulamada, daha kısa bir tarih dizesi görüntülenecek şekilde özel bir dönüştürücü kullanılmıştır. [Veri dönüştürme](#data-conversion) bölümü dönüştürücüler hakkında bilgi sağlar.

Kullanıcı *Ürün Ekle* düğmesini seçtiğinde aşağıdaki form gelir.

![Ürün Listeleme sayfası ekle](./media/data-binding-overview/demo-addproductlisting.png "DataBinding_Demo_AddProductListing")

Kullanıcı formdaki alanları dinleyebilir, kısa veya ayrıntılı önizleme bölmelerini kullanarak ürün `Submit` girişini önizleyebilir ve yeni ürün girişini eklemeyi seçebilir. Varolan tüm gruplandırma, filtreleme ve sıralama ayarları yeni giriş için geçerli olacaktır. Bu özel durumda, yukarıdaki resimde girilen öğe *Bilgisayar* kategorisindeikinci öğe olarak görüntülenir.

Bu resimde gösterilmeyen *Başlangıç Tarihi'nde* <xref:System.Windows.Controls.TextBox>sağlanan doğrulama mantığıdır. Kullanıcı geçersiz bir tarih (geçersiz biçimlendirme veya geçmiş bir tarih) girerse, <xref:System.Windows.Controls.ToolTip> kullanıcı yada bir ve kırmızı <xref:System.Windows.Controls.TextBox>ünlem işareti yle bildirilir. [Veri Doğrulama](#data-validation) bölümünde doğrulama mantığının nasıl oluşturuldurulması açıklanmıştır.

Yukarıda özetlenen veri bağlamanın farklı özelliklerine girmeden önce, öncelikle WPF veri bağlamayı anlamak için kritik olan temel kavramları tartışacağız.

## <a name="basic-data-binding-concepts"></a>Temel veri bağlama kavramları

Hangi öğeyi bağlasanız ve veri kaynağınızın yapısından bağımsız olarak, her bağlama her zaman aşağıdaki şekilde gösterilen modeli izler.

![Temel veri bağlama modelini gösteren diyagram.](./media/data-binding-overview/basic-data-binding-diagram.png)

Şekildeki gibi, veri bağlama aslında bağlayıcı hedefiniz ile bağlayıcı kaynağınız arasındaki köprüdür. Şekil aşağıdaki temel WPF veri bağlama kavramlarını göstermektedir:

- Tipik olarak, her bağlama nın dört bileşeni vardır:

  - Bağlayıcı bir hedef nesne.
  - Hedef bir özellik.
  - Bağlayıcı bir kaynak.
  - Kullanılacak bağlayıcı kaynaktaki değere giden yol.
  
  > Örneğin, bir `TextBox` `Employee.Name` `TextBox`özelliği bağlamak istiyorsanız, hedef nesne , hedef özelliği <xref:System.Windows.Controls.TextBox.Text%2A> özelliği, kullanılacak değer *Ad*ve kaynak nesne *Çalışan* nesnesidir.

- Hedef özellik bir bağımlılık özelliği olmalıdır. Çoğu <xref:System.Windows.UIElement> özellik bağımlılık özellikleridir ve salt okunur olanlar hariç çoğu bağımlılık özelliği varsayılan olarak veri bağlamayı destekler. (Yalnızca bağımlılık <xref:System.Windows.DependencyObject> özelliklerini tanımlayabilir ve tüm <xref:System.Windows.UIElement> türler `DependencyObject`türetilmiştir.)

- Şekilde gösterilmese de, bağlama kaynak nesnesinin özel bir .NET nesnesi olmakla sınırlı olmadığı unutulmamalıdır. WPF veri bağlama ,NET nesneleri ve XML şeklinde verileri destekler. Bazı örnekler sağlamak için, bağlama <xref:System.Windows.UIElement>kaynağınız bir , herhangi bir liste nesnesi, bir ADO.NET veya Web Hizmetleri nesnesi veya XML verilerinizi içeren bir XmlNode olabilir. Daha fazla bilgi için [bkz.](../../framework/wpf/data/binding-sources-overview.md)

Bağlayıcı bir hedef oluştururken bağlayıcı bir *hedefe* bağlandığınızı unutmamak önemlidir. Örneğin, bazı temel XML verilerini <xref:System.Windows.Controls.ListBox> kullanarak veri bağlamada görüntüleniyorsanız, `ListBox` xml verilerinize bağlasanız.

Bağlayıcı oluşturmak için nesneyi <xref:System.Windows.Data.Binding> kullanırsınız. Bu makalenin geri kalanında, `Binding` nesnenin özellikleri ve kullanımıyla ilişkili kavramların çoğu ve bazı özellikleri tartışılır.

### <a name="direction-of-the-data-flow"></a>Veri akışının yönü

Önceki şekildeki okta belirtildiği gibi, bağlayıcı kaynağın veri akışı bağlayıcı hedeften bağlayıcı kaynağa (örneğin, kullanıcı a `TextBox`değerini düzenlediğinde kaynak değeri değişir) ve/veya bağlayıcı kaynaktan `TextBox` bağlayıcı hedefe (örneğin, içeriğiniz bağlayıcı kaynaktaki değişikliklerle güncellenir)

Uygulamanızın kullanıcıların verileri değiştirmesini ve kaynak nesneye geri yaymasını etkinleştirmesini isteyebilirsiniz. Veya kullanıcıların kaynak verileri güncelleştirmesini etkinleştirmek istemeyebilirsiniz. Veri akışını ayarlayarak kontrol <xref:System.Windows.Data.Binding.Mode?displayProperty=nameWithType>edebilirsiniz.

Bu şekil, farklı veri akışı türlerini göstermektedir:

![Veri bağlama veri akışı](./media/data-binding-overview/databinding-dataflow.png "DataBinding_DataFlow")

- <xref:System.Windows.Data.BindingMode.OneWay>bağlama, hedef özelliği otomatik olarak güncelleştirmek için kaynak özellikte değişikliklere neden olur, ancak hedef özellikteki değişiklikler kaynak özelliğine geri yayılmaz. Bu tür bir bağlama, bağlı olan denetim örtülü olarak salt okunursa uygundur. Örneğin, stok işaretçisi gibi bir kaynağa bağlanabilir veya belki de hedef özelliğinizde tablonun veriye bağlı arka plan rengi gibi değişiklikler yapmak için sağlanan denetim arabirimi yoktur. Hedef özelliğinin değişikliklerini izlemeye gerek yoksa, bağlama <xref:System.Windows.Data.BindingMode.OneWay> modunu kullanarak <xref:System.Windows.Data.BindingMode.TwoWay> bağlama modunun genel yükü önlenir.

- <xref:System.Windows.Data.BindingMode.TwoWay>bağlama, diğerini otomatik olarak güncelleştirmek için kaynak özellikte veya hedef özellikte değişikliklere neden olur. Bu tür bağlama, değiştirilebilir formlar veya diğer tam etkileşimli arabirimi senaryoları için uygundur. Çoğu özellik <xref:System.Windows.Data.BindingMode.OneWay> varsayılan bağlama, ancak bazı bağımlılık özellikleri (genellikle kullanıcı tarafından kullanılabilir <xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType> denetimleri özellikleri ve [CheckBox.IsChecked](xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked) varsayılan <xref:System.Windows.Data.BindingMode.TwoWay> bağlama. Bağımlılık özelliğinin varsayılan olarak tek yönlü veya iki yönlü bağlayıp bağlamadığını belirlemenin programlı <xref:System.Windows.DependencyProperty.GetMetadata%2A?displayProperty=nameWithType> bir yolu, özellik meta <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A?displayProperty=nameWithType> verilerini almak ve sonra özelliğin Boolean değerini denetlemektir.

- <xref:System.Windows.Data.BindingMode.OneWayToSource>bağlamanın <xref:System.Windows.Data.BindingMode.OneWay> tersidir; hedef özellik değiştiğinde kaynak özelliği güncelleştirir. Bir örnek senaryo, ui kaynak değerini yeniden değerlendirmek gerekiyorsa.

- Şekilde gösterilmeyecek olan <xref:System.Windows.Data.BindingMode.OneTime> bağlayıcıdır, bu da kaynak özelliğin hedef özelliği ni başlatmasına neden olur, ancak sonraki değişiklikleri yaymaz. Veri bağlamı değişirse veya veri bağlamında nesne değişirse, değişiklik hedef özelliğe *yansıtılmaz.* Geçerli durum anlık görüntüsü uygunsa veya veriler gerçekten statikse, bu tür bir bağlama uygundur. Hedef özelliğinizi kaynak bir özellikten belirli bir değerle başlatmayı istiyorsanız ve veri bağlamı önceden bilinmiyorsa, bu tür bir bağlama da yararlıdır. Bu mod, kaynak değerinin değişmediği durumlarda daha iyi performans sağlayan daha basit bir <xref:System.Windows.Data.BindingMode.OneWay> bağlama biçimidir.

Kaynak değişikliklerini (ve <xref:System.Windows.Data.BindingMode.OneWay> <xref:System.Windows.Data.BindingMode.TwoWay> bağlamaları) algılamak için, kaynak . <xref:System.ComponentModel.INotifyPropertyChanged> Bkz. Nasıl Yapılacağını: Bir <xref:System.ComponentModel.INotifyPropertyChanged> uygulama örneği için özellik değişikliği [bildirimini uygulayın.](../../framework/wpf/data/how-to-implement-property-change-notification.md)

Özellik, <xref:System.Windows.Data.Binding.Mode?displayProperty=nameWithType> bağlama modları hakkında daha fazla bilgi ve bağlama nın yönünü nasıl belirtin bir örnek sağlar.

### <a name="what-triggers-source-updates"></a>Kaynak güncelleştirmelerini tetikleyen nedir?

Hedef özellikteki <xref:System.Windows.Data.BindingMode.TwoWay> <xref:System.Windows.Data.BindingMode.OneWayToSource> değişiklikleri dinleyen veya dinleyen ve bunları kaynağı güncelleştirme olarak bilinen kaynağa geri yayılabilen bağlayıcılar. Örneğin, temel kaynak değerini değiştirmek için TextBox'ın metnini değiştirebilirsiniz.

Ancak, metni düzenlerken veya metni düzenlemeyi bitirdikten sonra kaynak değeriniz güncelleştirildi ve denetim odağı mı kaybetti? Özellik, <xref:System.Windows.Data.Binding.UpdateSourceTrigger?displayProperty=nameWithType> kaynağın güncelleştirmesini neyin tetiklediğini belirler. Aşağıdaki şekilde ki sağ okların noktalarında <xref:System.Windows.Data.Binding.UpdateSourceTrigger?displayProperty=nameWithType> özelliğin rolü gösterin.

![UpdateSourceTrigger özelliğinin rolünü gösteren diyagram.](./media/data-binding-overview/data-binding-updatesource-trigger.png)

`UpdateSourceTrigger` Değer <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged?displayProperty=nameWithType>ise, hedef özellik değişir değişmez sağ <xref:System.Windows.Data.BindingMode.TwoWay> ok <xref:System.Windows.Data.BindingMode.OneWayToSource> veya bağlamalarla işaret edilen değer güncelleştirilir. Ancak, `UpdateSourceTrigger` değer ise, <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>bu değer yalnızca hedef özellik odağı kaybettiğinde yeni değerle güncelleştirilir.

<xref:System.Windows.Data.Binding.Mode%2A> Özelliğe benzer şekilde, farklı bağımlılık <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> özelliklerinin farklı varsayılan değerleri vardır. Çoğu bağımlılık özelliği için varsayılan <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>değer, `TextBox.Text` özelliğin varsayılan <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>değeri ise . `PropertyChanged`kaynak güncelleştirmeleri genellikle hedef özellik değiştiğinde meydana gelir. Anında değişiklikler Onay Kutuları ve diğer basit kontroller için iyidir. Ancak, metin alanları için, her tuş vuruşundan sonra güncelleştirme performansı azaltabilir ve kullanıcının yeni değere bağlanmadan önce arka alan ve yazım hatalarını düzeltmesi için olağan fırsatı reddeder.

Bağımlılık <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> özelliğinin varsayılan değerini nasıl bulabileceğiniz hakkında bilgi için özellik sayfasına bakın.

Aşağıdaki tablo, örnek <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> <xref:System.Windows.Controls.TextBox> olarak kullanarak her değer için bir örnek senaryo sağlar.

| UpdateSourceTrigger değeri | Kaynak değeri güncelleştirildiğinde | TextBox için örnek senaryo |
| ------------------------- | ---------------------------------- | ---------------------------- |
| `LostFocus`(varsayılan <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>) | TextBox denetimi odağı kaybettiğinde. | Doğrulama mantığıyla ilişkili bir TextBox (aşağıdaki [Veri Doğrulama'ya](#data-validation) bakın). |
| `PropertyChanged` | Girerken <xref:System.Windows.Controls.TextBox>. | Sohbet odası penceresinde TextBox denetimleri. |
| `Explicit` | Uygulama aradığında. <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> | TextBox, editable formunda denetimler (kaynak değerlerini yalnızca kullanıcı gönder düğmesini tıklattığında güncelleştirir). |

Örneğin, [bkz.](../../framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md)

## <a name="creating-a-binding"></a>Bağlayıcı oluşturma

Önceki bölümlerde tartışılan bazı kavramları yeniden ifade etmek için, <xref:System.Windows.Data.Binding> nesneyi kullanarak bir bağlama kurarsınız ve her bağlamanın genellikle dört bileşeni vardır: bağlayıcı hedef, hedef özellik, bağlayıcı bir kaynak ve kullanılacak kaynak değerine giden bir yol. Bu bölümde bağlama nasıl ayarlanan açıklanmıştır.

Bağlayıcı kaynak nesnenin SDKSample ad alanında tanımlanan *MyData* adlı bir sınıf olduğu aşağıdaki örneği göz önünde *bulundurun.* Gösterim amacıyla, *MyData'nın* *ColorName* adında bir dize özelliği vardır ve değeri "Kırmızı" olarak ayarlanır. Böylece, bu örnek kırmızı arka plan ile bir düğme oluşturur.

[!code-xaml[BindNonTextProperty](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/AutoConvertPropertyToColor.xaml#BindAutoConvertColor)]

Bağlayıcı bildirim sözdizimi ve kodda bir bağlama nın nasıl ayarlanacaklarına ilişkin örnekler hakkında daha fazla bilgi için [bkz.](../../framework/wpf/data/binding-declarations-overview.md)

Bu örneği temel diyagramımıza uygularsak, elde edilen şekil aşağıdaki gibi görünür. Arka Plan <xref:System.Windows.Data.BindingMode.OneWay> özelliği varsayılan olarak <xref:System.Windows.Data.BindingMode.OneWay> bağlamayı desteklediğinden, bu şekil bir bağlamayı açıklar.

![Veri bağlama Arka Plan özelliğini gösteren diyagram.](./media/data-binding-overview/data-binding-button-background-example.png)

*ColorName* özelliği türü <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Media.Brush>nde yken bu bağlamanın neden çalıştığını merak edebilirsiniz. Bu bağlama, [Veri dönüştürme](#data-conversion) bölümünde tartışılan varsayılan tür dönüştürmekullanır.

### <a name="specifying-the-binding-source"></a>Bağlayıcı kaynağı belirtme

Önceki örnekte, bağlama kaynağının [DockPanel.DataContext](xref:System.Windows.FrameworkElement.DataContext) özelliğini ayarlayarak belirtildiğine dikkat edin. Daha <xref:System.Windows.Controls.Button> sonra <xref:System.Windows.FrameworkElement.DataContext%2A> değeri ana <xref:System.Windows.Controls.DockPanel>öğesi olan ,'dan devralır. Yinelemek gerekirse, bağlayıcı kaynak nesne bir bağlama dört gerekli bileşenlerinden biridir. Bu nedenle, bağlayıcı kaynak nesne belirtilmeden, bağlama hiçbir şey yapmaz.

Bağlayıcı kaynak nesneyi belirtmenin birkaç yolu vardır. Aynı <xref:System.Windows.FrameworkElement.DataContext%2A> kaynağa birden çok özellik bağlarken, özelliği bir üst öğeüzerinde kullanmak yararlıdır. Ancak, bazen bağlayıcı kaynağı tek tek bağlama bildirimlerinde belirtmek daha uygun olabilir. Önceki örnekte, <xref:System.Windows.FrameworkElement.DataContext%2A> özelliği kullanmak yerine, aşağıdaki örnekte olduğu <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> gibi, özelliği doğrudan düğmenin bağlayıcı bildirimine ayarlayarak bağlama kaynağını belirtebilirsiniz.

[!code-xaml[BindNonTextPropertyCompactBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/AutoConvertPropertyToColor.xaml#BindAutoConvertColorCompactBinding)]

<xref:System.Windows.FrameworkElement.DataContext%2A> Özelliği doğrudan bir öğeüzerinde <xref:System.Windows.FrameworkElement.DataContext%2A> ayarlamak, değeri bir atadan devralmak (ilk örnekteki düğme gibi) ve <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> bağlama özelliğini bağlamaya ayarlayarak bağlayıcı kaynağı açıkça belirtmek (son örnekteki düğme gibi), bağlama kaynağını belirtmek için <xref:System.Windows.Data.Binding.ElementName?displayProperty=nameWithType> özelliği veya <xref:System.Windows.Data.Binding.RelativeSource?displayProperty=nameWithType> özelliği de kullanabilirsiniz. Özellik, <xref:System.Windows.Data.Binding.ElementName%2A> bir düğmenin genişliğini ayarlamak için kaydırıcı kullandığınızda olduğu gibi uygulamanızdaki diğer öğelere bağlanırken kullanışlıdır. Özellik, <xref:System.Windows.Data.Binding.RelativeSource%2A> bir veya bir <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Style>'de bağlama belirtildiğinde yararlıdır. Daha fazla bilgi için [bkz: Bağlama kaynağını belirtin.](../../framework/wpf/data/how-to-specify-the-binding-source.md)

### <a name="specifying-the-path-to-the-value"></a>Değere giden yolu belirtme

Bağlama kaynağınız bir nesneyse, <xref:System.Windows.Data.Binding.Path?displayProperty=nameWithType> bağlamanız için kullanılacak değeri belirtmek için özelliği kullanırsınız. XML verilerine bağlanıyorsunsa, <xref:System.Windows.Data.Binding.XPath?displayProperty=nameWithType> değeri belirtmek için özelliği kullanırsınız. Bazı durumlarda, verileriniz XML <xref:System.Windows.Data.Binding.Path%2A> olsa bile özelliği kullanmak geçerli olabilir. Örneğin, döndürülen bir XmlNode'un Ad özelliğine erişmek istiyorsanız (XPath sorgusunun bir <xref:System.Windows.Data.Binding.Path%2A> sonucu olarak), <xref:System.Windows.Data.Binding.XPath%2A> özelliği özelliğine ek olarak kullanmanız gerekir.

Daha fazla bilgi <xref:System.Windows.Data.Binding.Path%2A> için, bkz. <xref:System.Windows.Data.Binding.XPath%2A>

Kullanılacak değerin bağlayıcının <xref:System.Windows.Data.Binding.Path%2A> dört gerekli bileşeninden biri olduğunu vurgulamış olsak da, tüm nesneye bağlamak istediğiniz senaryolarda kullanılacak değer bağlayıcı kaynak nesneyle aynı olacaktır. Bu gibi durumlarda, bir <xref:System.Windows.Data.Binding.Path%2A>. Aşağıdaki örneği inceleyin.

[!code-xaml[EmptyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/EmptyBinding.xaml#EmptyBinding)]

Yukarıdaki örnekte boş bağlama sözdizimi kullanır: {Bağlama}. Bu durumda, <xref:System.Windows.Controls.ListBox> Veri Bağlamı bir üst DockPanel öğesinden devralır (bu örnekte gösterilmez). Yol belirtilmediğinde, varsayılan nesnenin tamamına bağlanır. Başka bir deyişle, bu örnekte, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliği tüm nesneye bağladığımız için yol dışarıda bırakılmış. (Ayrıntılı bir tartışma için [koleksiyonlara Bağlama](#binding-to-collections) bölümüne bakın.)

Bir koleksiyona bağlama dışında, bu senaryo, bir nesnenin yalnızca tek bir özelliği yerine tüm nesneye bağlanmak istediğinizde de yararlıdır. Örneğin, kaynak nesneniz türdeyse, <xref:System.String>yalnızca dizekendisine bağlamak isteyebilirsiniz. Başka bir yaygın senaryo, bir öğeyi birkaç özelliği olan bir nesneye bağlamak istediğinizde.

Verilerin bağlı hedef özelliğiniz için anlamlı olması için özel mantık uygulamanız gerekebilir. Varsayılan tür dönüştürme yoksa özel mantık özel bir dönüştürücü şeklinde olabilir. Dönüştürücüler hakkında bilgi için [Veri dönüştürme](#data-conversion) ye bakın.

### <a name="binding-and-bindingexpression"></a>Bağlama ve Bağlamaİfadesi

Diğer özellikleri ve veri bağlama kullanımları girmeden <xref:System.Windows.Data.BindingExpression> önce, sınıf tanıtmak yararlıdır. Önceki bölümlerde de gördüğünüz <xref:System.Windows.Data.Binding> gibi, sınıf bir bağlama bildirimi için üst düzey sınıftır; bir bağlama nın özelliklerini belirtmenize olanak tanıyan birçok özellik sağlar. İlgili bir <xref:System.Windows.Data.BindingExpression>sınıf, kaynak ve hedef arasındaki bağlantıyı koruyan altta yatan nesnedir. Bağlama, birkaç bağlama deyimi arasında paylaşılabilen tüm bilgileri içerir. A, <xref:System.Windows.Data.BindingExpression> paylaşılamayan ve tüm örnek bilgilerini içeren <xref:System.Windows.Data.Binding>bir örnek ifadesidir.

Sınıfın `myDataObject` bir örneği `MyData` olan, kaynak `myBinding` <xref:System.Windows.Data.Binding> nesnenin bulunduğu ve `MyData` 'adı bir `MyDataProperty`dize özelliği içeren tanımlı bir sınıf olduğu aşağıdaki örneği göz önünde bulundurun. Bu `myText`örnek, metin içeriğini , bir <xref:System.Windows.Controls.TextBlock>örneğini `MyDataProperty`.

[!code-csharp[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/ManualBinding.cs#CodeOnlyBinding)]
[!code-vb[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/ManualBinding.vb#CodeOnlyBinding)]

Diğer bağlamalar oluşturmak için aynı *myBinding* nesnesini kullanabilirsiniz. Örneğin, bir onay kutusunun metin içeriğini *MyDataProperty'e*bağlamak için *myBinding* nesnesini kullanabilirsiniz. Bu senaryoda, *myBinding* nesnesini <xref:System.Windows.Data.BindingExpression> paylaşmanın iki örneği olacaktır.

Bir <xref:System.Windows.Data.BindingExpression> nesne, veriye bağlı bir nesneyi çağırarak <xref:System.Windows.Data.BindingOperations.GetBindingExpression%2A> döndürülür. Aşağıdaki makaleler <xref:System.Windows.Data.BindingExpression> sınıfın bazı kullanımlarını göstermektedir:

- [Bağımlı hedef özelliğinden bağlama nesnesi alma](../../framework/wpf/data/how-to-get-the-binding-object-from-a-bound-target-property.md)

- [TextBox metni kaynağı güncellediğinde denetim](../../framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md)

## <a name="data-conversion"></a>Veri dönüştürme

[Bağlama](#creating-a-binding) bölümünde, <xref:System.Windows.Controls.Control.Background%2A> özelliği "Kırmızı" değerine sahip bir dize özelliğine bağlı olduğundan düğme kırmızıdır. Dize değerini <xref:System.Windows.Media.Brush> <xref:System.Windows.Media.Brush>bir .'ye dönüştürmek için tür dönüştürücü türünde bulunduğundan, bu dize değeri çalışır

Bu bilgileri şekil Bağlama [bölümü oluşturma](#creating-a-binding) şuna benzer.

![Veri bağlama Varsayılan özelliğini gösteren diyagram.](./media/data-binding-overview/data-binding-button-default-conversion.png)

Ancak, bağlayıcı kaynak nesnenizin bir renk özelliği varsa *Color* <xref:System.Windows.Media.Color>ne olur? Bu durumda, bağlamanın çalışması için öncelikle *Renk* özelliği değerini özelliğin <xref:System.Windows.Controls.Control.Background%2A> kabul ettiği bir şeye dönüştürmeniz gerekir. Aşağıdaki örnekte olduğu gibi <xref:System.Windows.Data.IValueConverter> arabirimi uygulayarak özel bir dönüştürücü oluşturmanız gerekir.

[!code-csharp[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/ColorBrushConverter.cs#ColorBrushConverter)]
[!code-vb[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/ColorBrushConverter.vb#ColorBrushConverter)]

Daha fazla bilgi edinmek için bkz. <xref:System.Windows.Data.IValueConverter>.

Şimdi varsayılan dönüştürme yerine özel dönüştürücü kullanılır ve diyagramımız şu na benzer.

![Veri bağlama özel dönüştürücü gösteren diyagram.](./media/data-binding-overview/data-binding-converter-color-example.png)

Yinelemek gerekirse, varsayılan dönüşümler, bağlı olan tür dönüştürücüler nedeniyle kullanılabilir. Bu davranış, hedefte hangi tür dönüştürücülerin bulunduğuna bağlıdır. Şüpheniz varsa, kendi dönüştürücü oluşturun.

Veri dönüştürücüsi uygulamanın mantıklı olduğu bazı tipik senaryolar şunlardır:

- Verileriniz kültüre bağlı olarak farklı şekilde görüntülenmelidir. Örneğin, belirli bir kültürde kullanılan kuralları temel alan bir para birimi dönüştürücüsü veya takvim tarihi/saat dönüştürücüsü uygulamak isteyebilirsiniz.

- Kullanılan verilerin bir özelliğin metin değerini değiştirmek için tasarlanmaması gerekmez, ancak bunun yerine görüntünün kaynağı veya görüntü metninin rengi veya stili gibi başka bir değeri değiştirmek amaçlanır. Dönüştürücüler, metin alanını bir tablo hücresinin Arka Plan özelliğine bağlamak gibi uygun görünmeyen bir özelliğin bağlamasını dönüştürerek bu örnekte kullanılabilir.

- Birden fazla denetim veya denetimlerin birden çok özelliği aynı verilere bağlıdır. Bu durumda, birincil bağlama yalnızca metni görüntüleyebilir, diğer bağlamalar ise belirli ekran sorunlarını işler, ancak yine de kaynak bilgilerle aynı bağlamayı kullanır.

- Hedef özellik, <xref:System.Windows.Data.MultiBinding>". Bunun <xref:System.Windows.Data.MultiBinding>için, bağlamaların değerlerinden son bir değer üretmek için bir özel <xref:System.Windows.Data.IMultiValueConverter> kullanırsınız. Örneğin, renk aynı veya farklı bağlayıcı kaynak nesnelerden gelen değerler olabilir kırmızı, mavi ve yeşil değerler, hesaplanabilir. Örnekler <xref:System.Windows.Data.MultiBinding> ve bilgiler için bkz.

## <a name="binding-to-collections"></a>Koleksiyonlara bağlanma

Bağlayıcı kaynak nesne, özellikleri veri içeren tek bir nesne olarak veya genellikle birlikte gruplanan çok biçimli nesnelerin veri koleksiyonu olarak (veritabanına yapılan bir sorgunun sonucu gibi) olarak işlenebilir. Şimdiye kadar sadece tek nesnelere bağlanmayı tartıştık. Ancak, veri toplamaya bağlama yaygın bir senaryodur. Örneğin, yaygın bir <xref:System.Windows.Controls.ItemsControl> senaryo, veri bağlama <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.ListView>bölümünde <xref:System.Windows.Controls.TreeView> gösterilen uygulamada olduğu gibi bir , , gibi bir , kullanmak veya bir veri toplama [görüntülemektir.](#what-is-data-binding)

Neyse ki, temel diyagramımız hala geçerli. Bir koleksiyona <xref:System.Windows.Controls.ItemsControl> bağlıysanız, diyagram aşağıdaki gibi görünür.

![Veri bağlama ÖğeleriDenetim nesnesini gösteren diyagram.](./media/data-binding-overview/data-binding-itemscontrol.png)

Bu diyagramda gösterildiği gibi, <xref:System.Windows.Controls.ItemsControl> bir koleksiyon nesnesine bağlamak için, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A?displayProperty=nameWithType> özellik kullanılacak özelliktir. İçeriği `ItemsSource` olarak <xref:System.Windows.Controls.ItemsControl>düşünebilirsiniz. Bağlama, <xref:System.Windows.Data.BindingMode.OneWay> özelliğin `ItemsSource` varsayılan `OneWay` olarak bağlamayı desteklemesidir.

### <a name="how-to-implement-collections"></a>Koleksiyonlar nasıl uygulanır?

<xref:System.Collections.IEnumerable> Arabirimi uygulayan herhangi bir koleksiyon üzerinden sayısalatabilirsiniz. Ancak, koleksiyondaki eklemeler veya silmelerin Kullanıcı Arabirimi'ni otomatik olarak güncelleştirmesi için dinamik <xref:System.Collections.Specialized.INotifyCollectionChanged> bağlamalar ayarlamak için, koleksiyonun arabirimi uygulaması gerekir. Bu arabirim, temel koleksiyon değiştiğinde yükseltilmesi gereken bir olayı ortaya çıkarır.

WPF, <xref:System.Collections.ObjectModel.ObservableCollection%601> <xref:System.Collections.Specialized.INotifyCollectionChanged> arabirimi ortaya çıkaran bir veri koleksiyonunun yerleşik bir uygulaması olan sınıfı sağlar. Veri değerlerinin kaynak nesnelerden hedeflere aktarılmasını tam olarak desteklemek için, koleksiyonunuzdaki bağlanabilir özellikleri destekleyen her nesnenin <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi de uygulaması gerekir. Daha fazla bilgi için [bkz.](../../framework/wpf/data/binding-sources-overview.md)

Kendi koleksiyonunuzu uygulamadan önce, başkaları arasında <xref:System.Collections.ObjectModel.ObservableCollection%601> , ve <xref:System.Collections.Generic.List%601> <xref:System.Collections.ObjectModel.Collection%601> <xref:System.ComponentModel.BindingList%601>, gibi varolan toplama sınıflarından birini kullanmayı düşünün. Gelişmiş bir senaryonuz varsa ve kendi koleksiyonunuzu <xref:System.Collections.IList>uygulamak istiyorsanız, dizin tarafından tek tek erişilebilen ve böylece en iyi performansı sağlayan genel olmayan bir nesne koleksiyonu sağlayan nesneleri kullanmayı düşünün.

### <a name="collection-views"></a>Koleksiyon görünümleri

Bir <xref:System.Windows.Controls.ItemsControl> veri koleksiyonuna bağlandıktan sonra, verileri sıralamak, filtrelemek veya gruplandırmak isteyebilirsiniz. Bunu yapmak için, <xref:System.ComponentModel.ICollectionView> arabirimi uygulayan sınıflar olan koleksiyon görünümlerini kullanırsınız.

#### <a name="what-are-collection-views"></a>Koleksiyon görünümleri nedir?

Koleksiyon görünümü, temel kaynak koleksiyonunun kendisini değiştirmek zorunda kalmadan kaynak koleksiyonunu sıralama, filtre ve grup sorgularına göre gezinmenizi ve görüntülemenizi sağlayan bağlayıcı kaynak koleksiyonunun üstündeki katmandır. Koleksiyon görünümü, koleksiyondaki geçerli öğeiçin bir işaretçi de tutar. Kaynak koleksiyon <xref:System.Collections.Specialized.INotifyCollectionChanged> arabirimi uygularsa, olay <xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged> tarafından yükseltilen değişiklikler görünümlere yayılır.

Görünümler temel kaynak koleksiyonlarını değiştirmedığından, her kaynak koleksiyonuyla ilişkili birden çok görünüm eolabilir. Örneğin, *Görev* nesneleri koleksiyonunuz olabilir. Görünümlerin kullanımıyla, aynı verileri farklı şekillerde görüntüleyebilirsiniz. Örneğin, sayfanızın sol tarafında, önceliğe göre sıralanmış görevleri ve alana göre gruplanmış sağ tarafta göstermek isteyebilirsiniz.

#### <a name="how-to-create-a-view"></a>Görünüm oluşturma

Bir görünüm oluşturmanın ve kullanmanın bir yolu, görünüm nesnesini doğrudan anında kullanmak ve sonra bağlama kaynağı olarak kullanmaktır. Örneğin, veri [bağlama][data-binding-demo] nedir bölümünde gösterilen Veri bağlama demo uygulamasını göz önünde [bulundurun.](#what-is-data-binding) Uygulama, doğrudan veri toplama <xref:System.Windows.Controls.ListBox> yerine veri toplama üzerinde bir görünüme bağlanır şekilde uygulanır. Aşağıdaki [örnek, Veri bağlama demo][data-binding-demo] uygulamasından çıkarılır. Sınıf, <xref:System.Windows.Data.CollectionViewSource> bir sınıfın xaml proxy'sidir. <xref:System.Windows.Data.CollectionView> Bu özel örnekte, <xref:System.Windows.Data.CollectionViewSource.Source%2A> görünümün görünümü geçerli uygulama nesnesinin *AuctionItems* koleksiyonuna (tür) <xref:System.Collections.ObjectModel.ObservableCollection%601>bağlıdır.

[!code-xaml[CollectionView](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#CollectionView)]

Kaynak *listelemeDataView* daha sonra uygulamadaki öğeler için bağlayıcı <xref:System.Windows.Controls.ListBox>kaynak olarak hizmet vermektedir.

[!code-xaml[ListBoxCollectionView](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#ListBoxCollectionView)]

Aynı koleksiyon için başka bir görünüm oluşturmak <xref:System.Windows.Data.CollectionViewSource> için başka bir `x:Key` örnek oluşturabilir ve ona farklı bir ad verebilirsiniz.

Aşağıdaki tablo, varsayılan koleksiyon görünümü olarak veya kaynak <xref:System.Windows.Data.CollectionViewSource> toplama türüne göre hangi görünüm veri türlerinin oluşturulduğunu gösterir.

| Kaynak toplama türü                    | Koleksiyon görünümü türü | Notlar |
| ----------------------------------------- | -------------------- | ----- |
| <xref:System.Collections.IEnumerable>     | Dayalı bir iç tip<xref:System.Windows.Data.CollectionView> | Öğeleri gruplayamaz. |
| <xref:System.Collections.IList>           | <xref:System.Windows.Data.ListCollectionView> | Hızlı. |
| <xref:System.ComponentModel.IBindingList> | <xref:System.Windows.Data.BindingListCollectionView> | |

#### <a name="using-a-default-view"></a>Varsayılan görünüm kullanma

Bağlayıcı kaynak olarak bir koleksiyon görünümü belirtme, bir koleksiyon görünümü oluşturmak ve kullanmak için bir yoldur. WPF ayrıca bağlayıcı kaynak olarak kullanılan her koleksiyon için varsayılan bir koleksiyon görünümü oluşturur. Doğrudan bir koleksiyona bağlanırsanız, WPF varsayılan görünümüne bağlanır. Bu varsayılan görünüm aynı koleksiyona tüm bağlamalar tarafından paylaşılır, bu nedenle varsayılan görünüme tek bir bağlı denetim veya kod (sıralama veya daha sonra tartışılan geçerli madde işaretçisinde değişiklik gibi) yapılan bir değişiklik, aynı koleksiyona diğer tüm bağlamalara yansıtılır.

Varsayılan görünümü elde etmek için <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> yöntemi kullanırsınız. Örneğin, bkz. [veri koleksiyonunun varsayılan görünümünü al.](../../framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md)

#### <a name="collection-views-with-adonet-datatables"></a>ADO.NET DataTables ile toplama görünümleri

Performansı artırmak için, ADO.NET <xref:System.Data.DataTable> <xref:System.Data.DataView> veya nesnelerin koleksiyon görünümleri, <xref:System.Data.DataView>veri kaynağının tüm koleksiyon görünümlerinde paylaşılmasına neden olan sıralama ve filtreleme nin , "davlumon" olarak sıralanmasını ve filtrelediğini belirtir. Her koleksiyon görünümünün bağımsız olarak sıralanmasını ve filtrelemesini <xref:System.Data.DataView> sağlamak için, her koleksiyon görünümünü kendi nesnesiyle baş harfe ayırın.

#### <a name="sorting"></a>Sıralama

Daha önce de belirtildiği gibi, görünümler bir koleksiyona bir sıralama sırası uygulayabilir. Temel koleksiyonda bulunduğundan, verileriniz ilgili, doğal bir sıraya sahip olabilir veya olmayabilir. Koleksiyon üzerindeki görünüm, sağladığınız karşılaştırma ölçütlerine bağlı olarak bir sipariş uygulamanıza veya varsayılan siparişi değiştirmenize olanak tanır. Verilerin istemci tabanlı görünümü olduğundan, yaygın bir senaryo, kullanıcının sütunun karşılık geldiği değere göre sıralı veri sütunlarını sıralamak isteyebileceğidir. Görünümleri kullanarak, bu kullanıcı tarafından yönlendirilen sıralama, yine temel koleksiyonda herhangi bir değişiklik yapmadan ve hatta koleksiyon içeriği için yeniden sorgulamayapmak zorunda kalmadan uygulanabilir. Örneğin, [üstbilgi tıklatıldığında GridView sütununa](../../framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)bakın.

Aşağıdaki örnekte, veri <xref:System.Windows.Controls.CheckBox> [bağlama](#what-is-data-binding) bölümündeki uygulama Arabirimi'nin "Kategori ve tarihe göre sırala" sıralama mantığını gösterilmektedir.

[!code-csharp[AddSortChecked](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#AddSortChecked)]
[!code-vb[AddSortChecked](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#AddSortChecked)]

#### <a name="filtering"></a>Filtreleme

Görünümler, görünümün tam koleksiyonun yalnızca belirli bir alt kümesini göstermesi için bir koleksiyona filtre de uygulayabilir. Verilerdeki bir koşula filtre uygulayabilirsiniz. Örneğin, [veri bağlama](#what-is-data-binding) bölümündeki uygulama tarafından yapıldığı gibi, "Yalnızca pazarlıkları <xref:System.Windows.Controls.CheckBox> göster" 25 TL veya daha pahalı öğeleri filtrelemek için mantık içerir. Aşağıdaki kod, seçildiğinde <xref:System.Windows.Data.CollectionViewSource.Filter> <xref:System.Windows.Controls.CheckBox> olay işleyicisi olarak *ShowOnlyBargainsFilter* ayarlamak için yürütülür.

[!code-csharp[ListingViewFilter](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#ListingViewFilter)]
[!code-vb[ListingViewFilter](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#ListingViewFilter)]

*ShowOnlyBargainsFilter* olay işleyicisi aşağıdaki uygulamaya sahiptir.

[!code-csharp[FilterEvent](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#FilterEvent)]
[!code-vb[FilterEvent](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#FilterEvent)]

<xref:System.Windows.Data.CollectionView> Sınıflardan birini doğrudan yerine <xref:System.Windows.Data.CollectionViewSource>kullanıyorsanız, geri arama belirtmek için <xref:System.Windows.Data.CollectionView.Filter%2A> özelliği kullanırsınız. Örneğin, [bkz. Bir Görünümdeki Verileri Filtrele.](../../framework/wpf/data/how-to-filter-data-in-a-view.md)

#### <a name="grouping"></a>Gruplandırma

Bir <xref:System.Collections.IEnumerable> koleksiyonu görüntüleyen iç sınıf dışında, tüm koleksiyon görünümleri, kullanıcının koleksiyon görünümünde koleksiyonu mantıksal gruplara bölmesine olanak tanıyan destek *gruplandırmasını*görüntüler. Gruplar, kullanıcının verilere bağlı olarak dinamik olarak oluşturulduğu grupların listesini sağladığı açık veya örtülü olabilir.

Aşağıdaki örnekte "Kategoriye göre gruplandırma" <xref:System.Windows.Controls.CheckBox>mantığı gösterilmektedir.

[!code-csharp[ListingGroupCheck](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#ListingGroupCheck)]
[!code-vb[ListingGroupCheck](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#ListingGroupCheck)]

Başka bir gruplandırma örneği için, [GridView uygulayan bir ListView'daki Grup Öğeleri'ne](../../framework/wpf/controls/how-to-group-items-in-a-listview-that-implements-a-gridview.md)bakın.

#### <a name="current-item-pointers"></a>Geçerli madde işaretçileri

Görünümler, geçerli öğe kavramını da destekler. Koleksiyon görünümünde nesneler arasında gezinebilirsiniz. Gezinirken, koleksiyondaki belirli bir konumda bulunan nesneyi almanıza olanak tanıyan bir öğe işaretçisi taşıyorsunuz. Örneğin, [bkz. veri CollectionView'daki nesneler arasında gezinme.](../../framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md)

WPF yalnızca bir görünüm (belirttiğiniz bir görünüm veya koleksiyonun varsayılan görünümü) kullanarak koleksiyona bağlandığından, koleksiyonlara yapılan tüm bağlamaların geçerli bir madde işaretçisi vardır. Bir görünüme bağlanırken, değerdeki `Path` eğik çizgi ("/") karakteri görünümün geçerli öğesini belirtir. Aşağıdaki örnekte, veri bağlamı bir koleksiyon görünümüdür. İlk satır koleksiyona bağlanır. İkinci satır koleksiyondaki geçerli öğeye bağlanır. Üçüncü satır, koleksiyondaki `Description` geçerli öğenin özelliğine bağlanır.

```xaml
<Button Content="{Binding }" />
<Button Content="{Binding Path=/}" />
<Button Content="{Binding Path=/Description}" />
```

Eğik çizgi ve özellik sözdizimi de koleksiyonlar hiyerarşisi geçmek için yığılmış olabilir. Aşağıdaki örnek, kaynak koleksiyonun geçerli öğesi `Offices`olan adlı koleksiyonun geçerli öğesine bağlanır.

```xaml
<Button Content="{Binding /Offices/}" />
```

Geçerli madde işaretçisi, koleksiyona uygulanan herhangi bir sıralama veya filtrelemeden etkilenebilir. Sıralama, seçili son öğedeki geçerli madde işaretçisini korur, ancak koleksiyon görünümü artık onun etrafında yeniden yapılandırılır. (Seçili öğe daha önce listenin başındaydı, ancak şimdi seçili öğe ortada bir yerde olabilir.) Filtreleme, bu seçim filtrelemeden sonra görünümde kalırsa seçili öğeyi korur. Aksi takdirde, geçerli madde işaretçisi filtre uygulanmış koleksiyon görünümünün ilk öğesine ayarlanır.

#### <a name="master-detail-binding-scenario"></a>Ana ayrıntı bağlama senaryosu

Geçerli öğe kavramı yalnızca koleksiyondaki öğelerin gezinmesi için değil, aynı zamanda ana ayrıntı bağlama senaryosu için de yararlıdır. [Veri bağlama](#what-is-data-binding) bölümündeki uygulama UI'sini yeniden düşünün. Bu uygulamada, içindeki seçim, 'de gösterilen <xref:System.Windows.Controls.ContentControl>içeriği <xref:System.Windows.Controls.ListBox> belirler. Başka bir şekilde ifade etmek <xref:System.Windows.Controls.ListBox> gerekirse, bir <xref:System.Windows.Controls.ContentControl> öğe seçildiğinde, seçili öğenin ayrıntılarını gösterir.

Ana ayrıntı senaryosunu, aynı görünüme bağlı iki veya daha fazla denetime sahip olarak uygulayabilirsiniz. [Veri bağlama demosundan][data-binding-demo] aşağıdaki örnek, veri <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.ContentControl> [bağlama](#what-is-data-binding) nedir bölümünde uygulama ui'sinde gördüğünüz ve gördüğünüz biçimlendirmeyi gösterir.

[!code-xaml[ListBoxContentControl](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#ListBoxContentControl)]

Denetimlerin her ikisinin de aynı kaynağa, *listingDataView* statik kaynağına bağlı olduğuna dikkat edin [(görünüm bölümü nasıl oluşturulur](#how-to-create-a-view)bölümünde bu kaynağın tanımına bakın). Bu bağlama çalışır, çünkü singleton <xref:System.Windows.Controls.ContentControl> nesnesi (bu durumda) bir koleksiyon görünümüne bağlı <xref:System.Windows.Data.CollectionView.CurrentItem%2A> olduğunda, otomatik olarak görünümün görünümüne bağlanır. Nesneler <xref:System.Windows.Data.CollectionViewSource> para birimini ve seçimi otomatik olarak eşitler. Liste denetiminiz bu örnekte <xref:System.Windows.Data.CollectionViewSource> olduğu gibi bir nesneye bağlı değilse, `true` bunun çalışması için özelliğini <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> ayarlamanız gerekir.

Diğer örnekler için, [bağlayıcı toplama ve seçime dayalı bilgileri görüntülemek](../../framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md) ve [hiyerarşik verilerle ana ayrıntı deseni kullanın](../../framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)bakın.

Yukarıdaki örnekte bir şablon kullandığını fark etmiş olabilirsiniz. Aslında, veriler şablonlar (açıkça tarafından açıkça kullanılan <xref:System.Windows.Controls.ContentControl> ve bir örtülü tarafından <xref:System.Windows.Controls.ListBox>kullanılan) kullanmadan istediğimiz şekilde görüntülenmez. Şimdi bir sonraki bölümde veri cazip açın.

## <a name="data-templating"></a>Veri şablonu oluşturma

Veri şablonları kullanılmadan, [veri bağlama](#what-is-data-binding) bölümündeki uygulamamız UI aşağıdaki gibi görünür.

![Veri Şablonları Olmadan Veri Bağlama Demosu](./media/data-binding-overview/demo-no-template.png)

Önceki bölümde gösterildiği gibi, <xref:System.Windows.Controls.ListBox> hem denetim hem <xref:System.Windows.Controls.ContentControl> de *denetim, AuctionItem*s'nin tüm koleksiyon nesnesine (veya daha spesifik olarak koleksiyon nesnesi üzerindeki görünüme) bağlıdır. Veri toplamanın nasıl görüntüleneciyi <xref:System.Windows.Controls.ListBox> gösteren özel yönergeler olmadan, altta <xref:System.Windows.Controls.ContentControl> yatan koleksiyondaki her nesnenin dize gösterimini görüntüler ve bağlı olduğu nesnenin dize gösterimini görüntüler.

Bu sorunu çözmek için uygulama <xref:System.Windows.DataTemplate?text=DataTemplates>tanımlar. Önceki bölümde örnekte gösterildiği gibi, <xref:System.Windows.Controls.ContentControl> açıkça *ayrıntılarıProductListingTemplate* veri şablonu kullanır. Denetim, <xref:System.Windows.Controls.ListBox> koleksiyondaki *AuctionItem* nesnelerini görüntülerken aşağıdaki veri şablonlarını örtülü olarak kullanır.

[!code-xaml[AuctionItemDataTemplate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#AuctionItemDataTemplate)]

Bu iki DataTemplates kullanımı ile, ortaya çıkan UI [veri bağlama](#what-is-data-binding) bölümünde gösterilen biridir. Bu ekran görüntüsünden de görebileceğiniz gibi, verileri kontrollerinize yerleştirmenize izin vermenin yanı sıra, DataTemplates verileriniz için etkileyici görseller tanımlamanıza olanak sağlar. Örneğin, <xref:System.Windows.DataTrigger> *highlight* *SpecialFeatures* <xref:System.Windows.DataTemplate> değeri ile *AuctionItem*s turuncu bir kenarlık ve bir yıldız ile görüntülenecektir, böylece yukarıda s kullanılır.

Veri şablonları hakkında daha fazla bilgi [için, Veri cazip genel bakış](../../framework/wpf/data/data-templating-overview.md)bakın.

## <a name="data-validation"></a>Veri doğrulama

Kullanıcı girişi alan çoğu uygulamanın, kullanıcının beklenen bilgileri girdiğinden emin olmak için doğrulama mantığına sahip olması gerekir. Doğrulama denetimleri tür, aralık, biçim veya uygulamaya özgü diğer gereksinimleri temel alabilir. Bu bölümde WPF'de veri doğrulamanın nasıl çalıştığı açıklanmıştır.

### <a name="associating-validation-rules-with-a-binding"></a>Doğrulama kurallarını bağlayıcı bir ilişkiyle ilişkilendirme

WPF veri bağlama modeli nesnenizle <xref:System.Windows.Data.Binding> ilişkilendirmenizi <xref:System.Windows.Data.Binding.ValidationRules%2A> sağlar. Örneğin, aşağıdaki örnek a'yı <xref:System.Windows.Controls.TextBox> adlı `StartPrice` bir özelliğe <xref:System.Windows.Controls.ExceptionValidationRule> bağlar <xref:System.Windows.Data.Binding.ValidationRules%2A?displayProperty=nameWithType> ve özelliğe bir nesne ekler.

[!code-xaml[TextboxStartPrice](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextboxStartPrice)]

Nesne, <xref:System.Windows.Controls.ValidationRule> bir özelliğin değerinin geçerli olup olmadığını denetler. WPF'nin iki tür <xref:System.Windows.Controls.ValidationRule> yerleşik nesnesi vardır:

- Bağlayıcı <xref:System.Windows.Controls.ExceptionValidationRule> kaynak özelliğinin güncelleştirmesi sırasında atılan özel durumlar için denetimler. Önceki örnekte, `StartPrice` tür dosdoğru. Kullanıcı tamsayıya dönüştürülemeyen bir değer girdiğinde, bir özel durum atılır ve bağlamageçersiz olarak işaretlenir. <xref:System.Windows.Controls.ExceptionValidationRule> Açık olarak ayarlamak için alternatif bir sözdizimi, <xref:System.Windows.Data.Binding> özelliği <xref:System.Windows.Data.MultiBinding> sizin veya <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> `true` nesnenizde ayarlamaktır.

- Nesne, <xref:System.Windows.Controls.DataErrorValidationRule> <xref:System.ComponentModel.IDataErrorInfo> arabirimi uygulayan nesneler tarafından yükseltilen hataları denetler. Bu doğrulama kuralını kullanma örneği <xref:System.Windows.Controls.DataErrorValidationRule>için bkz. <xref:System.Windows.Controls.DataErrorValidationRule> Açık olarak ayarlamak için alternatif bir sözdizimi, <xref:System.Windows.Data.Binding> özelliği <xref:System.Windows.Data.MultiBinding> sizin veya <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> `true` nesnenizde ayarlamaktır.

<xref:System.Windows.Controls.ValidationRule> Ayrıca, sınıftan türeyen ve <xref:System.Windows.Controls.ValidationRule.Validate%2A> yöntemi uygulayarak kendi doğrulama kuralınızı da oluşturabilirsiniz. Aşağıdaki örnek, [veri bağlama](#what-is-data-binding) bölümündeki *Ürün Ekleme* <xref:System.Windows.Controls.TextBox> "Başlangıç Tarihi" tarafından kullanılan kuralı gösterir.

[!code-csharp[FutureDateRule](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/FutureDateRule.cs#FutureDateRule)]
[!code-vb[FutureDateRule](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/FutureDateRule.vb#FutureDateRule)]

*StartDateEntryForm* <xref:System.Windows.Controls.TextBox> aşağıdaki örnekte gösterildiği gibi bu *FutureDateRule*kullanır.

[!code-xaml[TextboxStartDate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextboxStartDate)]

<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> Değer olduğundan, <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>bağlama motoru her tuş vuruşunda kaynak değerini güncelleştirir, bu da <xref:System.Windows.Data.Binding.ValidationRules%2A> her tuş vuruşunda koleksiyondaki her kuralı denetlediği anlamına gelir. Bunu Doğrulama İşlemi bölümünde daha fazla tartışıyoruz.

### <a name="providing-visual-feedback"></a>Görsel geri bildirim sağlama

Kullanıcı geçersiz bir değer girerse, uygulama kullanıcı arabirimi ndeki hata hakkında bazı geri bildirimler vermek isteyebilirsiniz. Bu tür geribildirim sağlamanın <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> bir yolu, ekli <xref:System.Windows.Controls.ControlTemplate>özelliği özel bir değere ayarlamaktır. Önceki alt bölümde gösterildiği gibi, *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> adlı *doğrulama Şablonu*kullanır. Aşağıdaki *örnekdoğrulamaŞablontanımını*gösterir.

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#ControlTemplate)]

Öğe, <xref:System.Windows.Controls.AdornedElementPlaceholder> bezenlenen denetimin nereye yerleştirileceğini belirtir.

Ayrıca, hata iletisini <xref:System.Windows.Controls.ToolTip> görüntülemek için a da kullanabilirsiniz. Hem *StartDateEntryForm* ve *StartPriceEntryForm*<xref:System.Windows.Controls.TextBox>es stil *textStyleTextBox*kullanın <xref:System.Windows.Controls.ToolTip> , hangi hata iletisi görüntüler oluşturur. Aşağıdaki *örnektextStyleTextBox*tanımını gösterir. Bağlı öğe, <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> `true` bağlı öğenin özelliklerine bağlanan bağlayıcılardan biri veya birkaçı hatalı olduğunda dır.

[!code-xaml[TextBoxStyle](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextBoxStyle)]

Özel <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> ve <xref:System.Windows.Controls.ToolTip>ile, *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> bir doğrulama hatası olduğunda aşağıdaki gibi görünüyor.

![Veri bağlama doğrulama hatası](./media/data-binding-overview/demo-validation-date.png "DataBindingDemo_Validation")

İlişkili <xref:System.Windows.Data.Binding> doğrulama kurallarınız varsa ancak bağlı <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> denetimde bir belirtmezseniz, doğrulama hatası olduğunda kullanıcıları bilgilendirmek için varsayılan bir varsayılan <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> kullanılır. Varsayılan, <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> süsleyici katmanında kırmızı kenarlık tanımlayan bir denetim şablonudur. Varsayılan <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> ve <xref:System.Windows.Controls.ToolTip>, *StartPriceEntryForm* <xref:System.Windows.Controls.TextBox> ui bir doğrulama hatası olduğunda aşağıdaki gibi görünüyor.

![Veri bağlama doğrulama hatası](./media/data-binding-overview/demo-validation-price.png "DataBindingDemo_ValidationDefault")

İletişim kutusundaki tüm denetimleri doğrulamak için mantığın nasıl sağlayabileceğinize bir örnek olarak, [İletişim kutularına genel bakıştaki](../../framework/wpf/app-development/dialog-boxes-overview.md)Özel İletişim Kutuları bölümüne bakın.

### <a name="validation-process"></a>Doğrulama işlemi

Doğrulama genellikle bir hedefin değeri bağlayıcı kaynak özelliğine aktarıldığında oluşur. Bu aktarım <xref:System.Windows.Data.BindingMode.TwoWay> üzerinde <xref:System.Windows.Data.BindingMode.OneWayToSource> oluşur ve ciltler. Yinelemek gerekirse, kaynak güncelleştirmesine neden olan şey, kaynak <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> [güncelleştirmelerini tetikleyenler](#what-triggers-source-updates) bölümünde açıklandığı gibi özelliğin değerine bağlıdır.

Aşağıdaki öğeler *doğrulama* işlemini açıklar. Bu işlem sırasında herhangi bir zamanda bir doğrulama hatası veya başka bir hata türü oluşursa, işlem durdurulur:

1. Bağlama motoru, <xref:System.Windows.Controls.ValidationRule> bunun <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> <xref:System.Windows.Controls.ValidationStep.RawProposedValue> için ayarlanmış özel nesneler olup olmadığını <xref:System.Windows.Data.Binding>denetler, bu <xref:System.Windows.Controls.ValidationRule.Validate%2A> durumda biri <xref:System.Windows.Controls.ValidationRule> bir hataya girene kadar veya hepsi geçene kadar her birinde yöntemi çağırır.

2. Bağlayıcı motor daha sonra varsa dönüştürücü çağırır.

3. Dönüştürücü başarılı olursa, bağlayıcı motor, <xref:System.Windows.Controls.ValidationRule> bunun <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> <xref:System.Windows.Data.Binding>için ayarlanmış özel nesneler varsa, bu durumda biri <xref:System.Windows.Controls.ValidationRule.Validate%2A> bir hataya girene <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> kadar veya hepsi geçene kadar <xref:System.Windows.Controls.ValidationRule> <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ayarlanmış her bir yöntem çağırır.

4. Bağlama motoru kaynak özelliği ayarlar.

5. Bağlama <xref:System.Windows.Controls.ValidationRule> motoru, bunun <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> <xref:System.Windows.Controls.ValidationStep.UpdatedValue> için ayarlanmış özel nesneler olup olmadığını <xref:System.Windows.Data.Binding>denetler, bu <xref:System.Windows.Controls.ValidationRule.Validate%2A> durumda, <xref:System.Windows.Controls.ValidationRule> biri <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> bir <xref:System.Windows.Controls.ValidationStep.UpdatedValue> hataya girene kadar veya hepsi geçene kadar ayarlanmış her bir yöntem çağırır. A <xref:System.Windows.Controls.DataErrorValidationRule> bir bağlama ile ilişkili <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> yse ve onun <xref:System.Windows.Controls.ValidationStep.UpdatedValue>varsayılan <xref:System.Windows.Controls.DataErrorValidationRule> olarak ayarlanırsa, bu noktada denetlenir. Bu <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> noktada, ayarlanan herhangi `true` bir bağlama denetlenir.

6. Bağlama <xref:System.Windows.Controls.ValidationRule> motoru, bunun <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> <xref:System.Windows.Controls.ValidationStep.CommittedValue> için ayarlanmış özel nesneler olup olmadığını <xref:System.Windows.Data.Binding>denetler, bu <xref:System.Windows.Controls.ValidationRule.Validate%2A> durumda, <xref:System.Windows.Controls.ValidationRule> biri <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> bir <xref:System.Windows.Controls.ValidationStep.CommittedValue> hataya girene kadar veya hepsi geçene kadar ayarlanmış her bir yöntem çağırır.

A <xref:System.Windows.Controls.ValidationRule> bu işlem boyunca herhangi bir zamanda geçmezse, bağlama <xref:System.Windows.Controls.ValidationError> motoru bir nesne <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> oluşturur ve bağlı öğenin koleksiyonuna ekler. Bağlama altyapısı nesneleri <xref:System.Windows.Controls.ValidationRule> belirli bir adımda çalıştırmadan önce, bu adım <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> sırasında bağlı öğenin ekli özelliğine eklenen herhangi bir <xref:System.Windows.Controls.ValidationError> kaldırır. Örneğin, bir <xref:System.Windows.Controls.ValidationRule> olan <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> başarısız <xref:System.Windows.Controls.ValidationStep.UpdatedValue> olacak şekilde ayarlanmışsa, bir sonraki doğrulama işlemi gerçekleştiğinde, bağlama <xref:System.Windows.Controls.ValidationRule> motoru, <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> ayarlanan herhangi bir çağrıyı <xref:System.Windows.Controls.ValidationStep.UpdatedValue> <xref:System.Windows.Controls.ValidationError> hemen önce kaldırır.

<xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> Boş olmadığında, öğenin <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> bağlı özelliği `true`. Ayrıca, <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A> özelliği <xref:System.Windows.Data.Binding> ayarlanırsa `true`, bağlama motoru öğe <xref:System.Windows.Controls.Validation.Error?displayProperty=nameWithType> üzerinde ekli olay yükseltir.

Ayrıca, her iki yönde geçerli bir değer aktarımı (hedefkaynak <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> veya kaynak hedef) ekli özelliği temizler unutmayın.

Bağlama ile ilişkili <xref:System.Windows.Controls.ExceptionValidationRule> bir ya varsa, <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> ya da `true` özellik ayarlanmış olsaydı ve bağlama motoru kaynağı ayarlar zaman bir özel durum <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>atılır, bağlama motoru olup olmadığını görmek için . Özel durumları işlemek için <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> özel bir işleyici sağlamak için geri aramayı kullanma seçeneğiniz vardır. Bir <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> üzerinde <xref:System.Windows.Data.Binding>belirtilmemişse, bağlama motoru <xref:System.Windows.Controls.ValidationError> özel bir durum oluşturur <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> ve bağlı öğenin koleksiyonuna ekler.

## <a name="debugging-mechanism"></a>Hata ayıklama mekanizması

Belirli bir bağlamanın <xref:System.Diagnostics.PresentationTraceSources.TraceLevel%2A?displayProperty=nameWithType> durumu hakkında bilgi almak için bağlı bir nesne üzerinde ekli özelliği ayarlayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.DataErrorValidationRule>
- [LINQ sorgusunun sonuçlarına bağlama](../../framework/wpf/data/how-to-bind-to-the-results-of-a-linq-query.md)
- [Veri bağlama](../../framework/wpf/advanced/optimizing-performance-data-binding.md)
- [Veri bağlama demosu][data-binding-demo]
- [Nasıl dır makaleleri](../../framework/wpf/data/data-binding-how-to-topics.md)
- [ADO.NET veri kaynağına bağlama](../../framework/wpf/data/how-to-bind-to-an-ado-net-data-source.md)

[data-binding-demo]: https://github.com/microsoft/WPF-Samples/tree/master/Sample%20Applications/DataBindingDemo "veri bağlama demo uygulaması"
