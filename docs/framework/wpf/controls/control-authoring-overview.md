---
title: Denetim Yazımına Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], authoring overview
- authoring overview for controls [WPF]
ms.assetid: 3d864748-cff0-4e63-9b23-d8e5a635b28f
ms.openlocfilehash: d5dd2d962c554b860fb6f68110945d56c4ee03ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400157"
---
# <a name="control-authoring-overview"></a>Denetim Yazımına Genel Bakış

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Denetim modelinin genişletilebilirliği, yeni bir denetim oluşturma gereksinimini büyük ölçüde azaltır. Ancak, bazı durumlarda yine de özel bir denetim oluşturmanız gerekebilir. Bu konu, özel bir denetim oluşturma gereksiniminizi en aza indiren [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]özellikleri ve 'deki farklı denetim yazma modellerini tartışır. Bu konu aynı zamanda yeni bir denetimin nasıl oluşturultur olduğunu da gösterir.

<a name="when_to_write_a_new_control"></a>

## <a name="alternatives-to-writing-a-new-control"></a>Yeni Bir Denetim Yazmaya Alternatifler

Tarihsel olarak, varolan bir denetimden özelleştirilmiş bir deneyim elde etmek istiyorsanız, arka plan rengi, kenarlık genişliği ve yazı tipi boyutu gibi denetimin standart özelliklerini değiştirmekle sınırlıydınız. Bir denetimin görünümünü veya davranışını bu önceden tanımlanmış parametrelerin ötesine genişletmek isterseniz, genellikle varolan bir denetimden devralma ve denetimi çizmekten sorumlu yöntemi geçersiz kılarak yeni bir denetim oluşturmanız gerekir.  Bu hala bir seçenek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olmasına rağmen, zengin içerik modelini, stillerini, şablonlarını ve tetikleyicilerini kullanarak varolan denetimleri özelleştirmenize olanak tanır. Aşağıdaki liste, bu özelliklerin yeni bir denetim oluşturmak zorunda kalmadan özel ve tutarlı deneyimler oluşturmak için nasıl kullanılabileceğini örnekler eve verir.

- **Zengin İçerik.** Standart [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimlerin çoğu zengin içeriği destekler. Örneğin, bir <xref:System.Windows.Controls.Button> içerik özelliği türündedir, <xref:System.Object>bu nedenle teorik olarak <xref:System.Windows.Controls.Button>her şey bir .  Bir düğmenin bir görüntüyü ve metni görüntülemesi <xref:System.Windows.Controls.TextBlock> için, <xref:System.Windows.Controls.StackPanel> bir görüntü <xref:System.Windows.Controls.StackPanel> ve <xref:System.Windows.Controls.ContentControl.Content%2A> a'ya bir görüntü ekleyebilir ve özelliğiata atayabilirsiniz. Denetimler görsel [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğeleri ve rasgele verileri görüntüleyebildiği için, yeni bir denetim oluşturmak veya karmaşık bir görselleştirmeyi desteklemek için varolan denetimi değiştirmek için daha az gereksinim vardır. İçerik modeli ve diğer <xref:System.Windows.Controls.Button> içerik modelleri hakkında [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]daha fazla bilgi için [WPF İçerik Modeli'ne](wpf-content-model.md)bakın.

- **Stil.** A, <xref:System.Windows.Style> denetim in özelliklerini temsil eden değerler topluluğudur. Stilleri kullanarak, yeni bir denetim yazmadan istenen denetim görünümünün ve davranışının yeniden kullanılabilir bir temsilini oluşturabilirsiniz. Örneğin, tüm denetimlerinizin <xref:System.Windows.Controls.TextBlock> kırmızı, yazı tipi boyutu 14 olan Arial yazı tipine sahip olmasını istediğinizi varsayalım. Kaynak olarak bir stil oluşturabilir ve uygun özellikleri buna göre ayarlayabilirsiniz. Daha <xref:System.Windows.Controls.TextBlock> sonra uygulamanıza eklediğiniz her şey aynı görünüme sahip olacaktır.

- **Veri Şablonları.** A, <xref:System.Windows.DataTemplate> verilerin denetimde nasıl görüntüleneceğini özelleştirmenize olanak tanır. Örneğin, bir <xref:System.Windows.DataTemplate> <xref:System.Windows.Controls.ListBox>' de verilerin nasıl görüntüleneceğini belirtmek için kullanılabilir.  Bunun bir örneği için [bkz.](../data/data-templating-overview.md)  Verilerin görünümünü özelleştirmenin yanı sıra, <xref:System.Windows.DataTemplate> özel kullanıcı arama larında çok fazla esneklik sağlayan Kullanıcı Bira öğeleri de içerebilir.  Örneğin, bir <xref:System.Windows.DataTemplate>, her öğenin <xref:System.Windows.Controls.ComboBox> bir onay kutusu içerdiği bir oluşturabilirsiniz.

- **Denetim Şablonları.** Denetimin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] görünümünü <xref:System.Windows.Controls.ControlTemplate> denetimin işlevselliğinden ayıran denetimin yapısını ve görünümünü tanımlamak için kullanılan birçok denetim. Büyük ölçüde onun <xref:System.Windows.Controls.ControlTemplate>yeniden tanımlayarak bir denetim görünümünü değiştirebilirsiniz.  Örneğin, stop lambası gibi görünen bir denetim istediğinizi varsayalım. Bu denetim basit bir kullanıcı arabirimi ve işlevselliği vardır.  Denetim üç dairedir ve bunlardan yalnızca biri aynı anda aydınlatılabilir. Biraz düşündükten sonra, bir <xref:System.Windows.Controls.RadioButton> seferde seçilen yalnızca bir işlevsellik sunuyor fark edebilirsiniz, ancak varsayılan görünüm bir stoplight ışıklar gibi <xref:System.Windows.Controls.RadioButton> görünüyor.  Görünümünü <xref:System.Windows.Controls.RadioButton> tanımlamak için bir denetim şablonu kullandığından, denetimgereksinimlerini karşılamak için yeniden <xref:System.Windows.Controls.ControlTemplate> tanımlamak ve stoplambanızı yapmak için radyo düğmelerini kullanmak kolaydır.

  > [!NOTE]
  > A, <xref:System.Windows.Controls.RadioButton> a <xref:System.Windows.DataTemplate> <xref:System.Windows.DataTemplate> bu örnekte yeterli olmasa da.  Denetim <xref:System.Windows.DataTemplate> içeriğinin görünümünü tanımlar. Bir <xref:System.Windows.Controls.RadioButton>durumunda , içerik seçilip <xref:System.Windows.Controls.RadioButton> seçilmediğini gösteren dairenin sağında görünen şeydir.  Stoplight örneğinde, radyo düğmesinin sadece "yanabilen" bir daire olması gerekir. Stop lambası için görünüm gereksinimi varsayılan görünümden <xref:System.Windows.Controls.RadioButton>çok farklı olduğundan, yeniden <xref:System.Windows.Controls.ControlTemplate>tanımlamak gerekir.  Genel olarak <xref:System.Windows.DataTemplate> a, bir denetimin içeriğini (veya verilerini) <xref:System.Windows.Controls.ControlTemplate> tanımlamak için kullanılır ve bir denetimin nasıl yapılandırılacağını tanımlamak için kullanılır.

- **Tetikleyiciler.** A, <xref:System.Windows.Trigger> yeni bir denetim oluşturmadan denetimin görünümünü ve davranışını dinamik olarak değiştirmenize olanak tanır. Örneğin, uygulamanızda birden <xref:System.Windows.Controls.ListBox> çok denetiminiz olduğunu ve <xref:System.Windows.Controls.ListBox> her bir indeki öğelerin seçildiğinde kalın ve kırmızı olmasını istediğinizi varsayalım. İlk içgüdünüz, seçili öğenin <xref:System.Windows.Controls.ListBox> görünümünü değiştirmek <xref:System.Windows.Controls.Primitives.Selector.OnSelectionChanged%2A> için yöntemi devralan ve geçersiz kılabilecek bir sınıf oluşturmak olabilir, ancak <xref:System.Windows.Controls.ListBoxItem> daha iyi bir yaklaşım, seçili öğenin görünümünü değiştiren bir stile tetikleyici eklemektir. Tetikleyici, özellik değerlerini değiştirmenize veya bir özelliğin değerine göre eylem yapmanızı sağlar. Bir <xref:System.Windows.EventTrigger> olay meydana geldiğinde eylem yapmanızı sağlar.

Stiller, şablonlar ve tetikleyiciler hakkında daha fazla bilgi için [bkz.](styling-and-templating.md)

Genel olarak, denetiminiz varolan bir denetimin işlevselliğini yansıtıyorsa, ancak denetimin farklı görünmesini istiyorsanız, öncelikle varolan denetimin görünümünü değiştirmek için bu bölümde tartışılan yöntemlerden herhangi birini kullanıp kullanamayacağınızı düşünmelisiniz.

<a name="models_for_control_authoring"></a>

## <a name="models-for-control-authoring"></a>Denetim Yazma Modelleri

Zengin içerik modeli, stilleri, şablonları ve tetikleyicileri, yeni bir denetim oluşturma gereksinimini en aza indirir. Ancak, yeni bir denetim oluşturmanız gerekiyorsa, farklı denetim yazma modellerini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]anlamak önemlidir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]her biri farklı özellikler ve esneklik düzeyi sağlayan bir denetim oluşturmak için üç genel model sağlar. Üç model için temel <xref:System.Windows.Controls.UserControl>sınıflar <xref:System.Windows.Controls.Control>, <xref:System.Windows.FrameworkElement>, ve .

### <a name="deriving-from-usercontrol"></a>UserControl'den Türeyen

Bir denetim [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oluşturmanın en basit <xref:System.Windows.Controls.UserControl>yolu. Devralan bir denetim <xref:System.Windows.Controls.UserControl>oluşturduğunuzda, varolan bileşenleri <xref:System.Windows.Controls.UserControl>, bileşenleri adlandırmave başvuru olay [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]işleyicileri ekleyin. Daha sonra adlandırılmış öğelere başvuru yapabilir ve koddaki olay işleyicilerini tanımlayabilirsiniz. Bu geliştirme modeli, uygulama geliştirme için kullanılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]modele çok benzer.

Doğru bir şekilde <xref:System.Windows.Controls.UserControl> oluşturulursa, zengin içeriğin, stillerin ve tetikleyicilerin avantajlarından yararlanabilir. Ancak, denetiminiz <xref:System.Windows.Controls.UserControl>devralırsa, denetiminizi kullanan kişiler bir <xref:System.Windows.DataTemplate> kişiyi kullanamaz <xref:System.Windows.Controls.ControlTemplate> veya görünümünü özelleştiremez.  Şablonları destekleyen özel bir <xref:System.Windows.Controls.Control> denetim oluşturmak için sınıftan <xref:System.Windows.Controls.UserControl>veya türetilmiş sınıflarından (diğer) türemiş olması gerekir.

#### <a name="benefits-of-deriving-from-usercontrol"></a>UserControl'den Türeyen Faydaları

Aşağıdakilerin tümü <xref:System.Windows.Controls.UserControl> geçerliyse, aşağıdakilerden kaynaklanın:

- Denetiminizi, bir uygulamayı nasıl oluşturduğunuza benzer şekilde oluşturmak istiyorsunuz.

- Denetiminiz yalnızca varolan bileşenlerden oluşur.

- Karmaşık özelleştirmeyi desteklemeniz gerekmez.

### <a name="deriving-from-control"></a>Kontrolden Türeyen

Sınıftan <xref:System.Windows.Controls.Control> türeyen model, varolan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimlerin çoğu tarafından kullanılan modeldir. <xref:System.Windows.Controls.Control> Sınıftan devralan bir denetim oluşturduğunuzda, şablonları kullanarak görünümünü tanımlarsınız. Bunu yaparak, çalışma mantığını görsel gösterimden ayırırsınız. Ayrıca, olaylar yerine komutlar ve bağlamalar kullanarak ve mümkün <xref:System.Windows.Controls.ControlTemplate> olduğunca referans öğeleri kaçınarak UI ve mantığın ayrıştırılması sağlayabilirsiniz.  Kullanıcı GÖn'ü ve denetiminizin mantığı düzgün bir şekilde ayrılmışsa, denetiminizdeki <xref:System.Windows.Controls.ControlTemplate> bir kullanıcı denetimin görünümünü özelleştirmek için denetimi yeniden tanımlayabilir. Bir özel <xref:System.Windows.Controls.Control> bina kadar basit olmasa <xref:System.Windows.Controls.UserControl>da, <xref:System.Windows.Controls.Control> bir özel en esnekliği sağlar.

#### <a name="benefits-of-deriving-from-control"></a>Kontrolden Elde Edilen Faydaları

Aşağıdakilerden herhangi <xref:System.Windows.Controls.Control> biri uygulanıyorsa <xref:System.Windows.Controls.UserControl> sınıfı kullanmak yerine elde etmeyi düşünün:

- Denetiminizin görünümünün <xref:System.Windows.Controls.ControlTemplate>.

- Denetiminizin farklı temaları desteklemesini istiyorsunuz.

### <a name="deriving-from-frameworkelement"></a>FrameworkElement'den Türeyen

Varolan öğelerden <xref:System.Windows.Controls.UserControl> <xref:System.Windows.Controls.Control> türeyen veya bu öğelerin besteedilmesine dayanan denetimler. Birçok senaryo için bu kabul edilebilir bir çözümdür, <xref:System.Windows.FrameworkElement> çünkü devralan <xref:System.Windows.Controls.ControlTemplate>herhangi bir nesne bir . Ancak, bir denetimin görünümünün basit öğe bileşiminin işlevselliğinden daha fazlasını gerektirdiği zamanlar vardır. Bu senaryolar için, bir <xref:System.Windows.FrameworkElement> bileşeni temel alma doğru seçimdir.

Yapı tabanlı bileşenler için <xref:System.Windows.FrameworkElement>iki standart yöntem vardır: doğrudan işleme ve özel öğe kompozisyonu. Doğrudan işleme, bileşen <xref:System.Windows.UIElement.OnRender%2A> görsellerini <xref:System.Windows.FrameworkElement> açıkça <xref:System.Windows.Media.DrawingContext> tanımlayan yöntemin geçersiz kılınması ve işlemlerin sağlanmasını içerir. Bu yöntem tarafından <xref:System.Windows.Controls.Image> kullanılan <xref:System.Windows.Controls.Border>ve . Özel öğe bileşimi, bileşeninizin görünümünü oluşturmak için tür <xref:System.Windows.Media.Visual> nesneleri kullanmayı içerir. Örneğin, [bkz. ÇizimGörsel Nesneleri Kullanma.](../graphics-multimedia/using-drawingvisual-objects.md) <xref:System.Windows.Controls.Primitives.Track>özel öğe kompozisyonu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullanan bir denetim örneğidir. Doğrudan işleme ve özel eleman kompozisyonu aynı denetimde karıştırmak da mümkündür.

#### <a name="benefits-of-deriving-from-frameworkelement"></a>FrameworkElement'den Türemanın Faydaları

Aşağıdakilerden herhangi <xref:System.Windows.FrameworkElement> biri geçerliyse, aşağıdakilerden birini kullanmayı düşünün:

- Basit öğe bileşimi tarafından sağlananın ötesinde, denetiminizin görünümü üzerinde kesin denetime sahip olmak istiyorsunuz.

- Kendi render mantığınızı tanımlayarak denetiminizin görünümünü tanımlamak istiyorsunuz.

- Varolan öğeleri, mümkün olanın ötesine geçecek yeni <xref:System.Windows.Controls.UserControl> <xref:System.Windows.Controls.Control>yollarla oluşturmak istiyorsunuz.

<a name="control_authoring_basics"></a>

## <a name="control-authoring-basics"></a>Denetim Yazma Temelleri

Daha önce de ele alındığı gibi, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en güçlü özelliklerinden biri, görünümünü ve davranışını değiştirmek için bir denetimin temel özelliklerini ayarlamanın ötesine geçebilmektir, ancak yine de özel bir denetim oluşturmaya gerek yoktur. Stil, veri bağlama ve tetikleyici özellikleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellik sistemi ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olay sistemi tarafından mümkün kılınmaktadır. Aşağıdaki bölümler, özel denetimi oluşturmak için kullandığınız modelden bağımsız olarak izlemeniz gereken bazı uygulamaları açıklar, böylece özel denetiminizdeki kullanıcılar bu özellikleri tıpkı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]bu özellikleri, bir denetimde olduğu gibi kullanabilirler.

### <a name="use-dependency-properties"></a>Bağımlılık Özelliklerini Kullanma

Bir özellik bir bağımlılık özelliği olduğunda, aşağıdakileri yapmak mümkündür:

- Özelliği bir tarzda ayarlayın.

- Özelliği bir veri kaynağına bağla.

- Özelliğin değeri olarak dinamik bir kaynak kullanın.

- Mülkü canlandırın.

Bu işlevselliklerden herhangi birini desteklemek için denetiminizin bir özelliğini istiyorsanız, bunu bir bağımlılık özelliği olarak uygulamanız gerekir. Aşağıdaki örnek, aşağıdakileri yaparak `Value` adlı bir bağımlılık özelliği tanımlar:

- Alan <xref:System.Windows.DependencyProperty> olarak adlandırılan `ValueProperty` bir `public` `static` `readonly` tanımlayıcı tanımlayın.

- Aşağıdakileri belirtmek için, emlak sistemine, arayarak <xref:System.Windows.DependencyProperty.Register%2A?displayProperty=nameWithType>özellik adını kaydedin:

  - Özelliğin adı.

  - Özelliğin türü.

  - Mülkün sahibi olan tür.

  - Özellik için meta veriler. Meta veriler özelliğin varsayılan değerini içerir, <xref:System.Windows.CoerceValueCallback> <xref:System.Windows.PropertyChangedCallback>a ve a .

- Özelliğin `get` ve `set` erişimedenlerin `Value`uygulanmasını uygulayarak bağımlılık özelliğini kaydetmek için kullanılan aynı ad olan CLR sarıcı özelliğini tanımlayın. `get` Ve `set` erişimedenlerin yalnızca ve <xref:System.Windows.DependencyObject.GetValue%2A> <xref:System.Windows.DependencyObject.SetValue%2A> sırasıyla aramalarını unutmayın. Bağımlılık özelliklerinin erişimcilerin ek mantık içermemesi önerilir, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çünkü istemciler ve erişimcileri <xref:System.Windows.DependencyObject.SetValue%2A> atlayabilir ve doğrudan arayabilir. <xref:System.Windows.DependencyObject.GetValue%2A> Örneğin, bir özellik bir veri kaynağına bağlı olduğunda, özelliğin `set` erişimcisi çağrılmaz.  Erişime erişim ve erişime ek mantık eklemek <xref:System.Windows.ValidateValueCallback>yerine, değiştiğinde değeri yanıtlamak veya denetlemek için , ve <xref:System.Windows.CoerceValueCallback> <xref:System.Windows.PropertyChangedCallback> temsilciler kullanın.  Bu geri aramalarla ilgili daha fazla bilgi için Bağımlılık [Özelliği Geri Aramaları ve Doğrulama'ya](../advanced/dependency-property-callbacks-and-validation.md)bakın.

- Adlandırılmış `CoerceValue`için <xref:System.Windows.CoerceValueCallback> bir yöntem tanımlayın. `CoerceValue`'den `Value` daha büyük veya `MinValue` eşit ve daha `MaxValue`az veya eşit olmasını sağlar.

- <xref:System.Windows.PropertyChangedCallback>, adlı için bir `OnValueChanged`yöntem tanımlayın. `OnValueChanged`bir <xref:System.Windows.RoutedPropertyChangedEventArgs%601> nesne oluşturur ve yönlendirilen `ValueChanged` olayı yükseltmeye hazırlanır. Yönlendirilen olaylar sonraki bölümde ele alınmıştır.

[!code-csharp[UserControlNumericUpDown#DependencyProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#dependencyproperty)]
[!code-vb[UserControlNumericUpDown#DependencyProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#dependencyproperty)]

Daha fazla bilgi için [bkz.](../advanced/custom-dependency-properties.md)

### <a name="use-routed-events"></a>Yönlendirilen Olayları Kullanma

Bağımlılık özelliklerinin ek işlevsellikle CLR özellikleri kavramını genişletmesi gibi, yönlendirilen olaylar da standart CLR olayları kavramını genişletir. Yeni [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir denetim oluşturduğunuzda, yönlendirilen bir olay aşağıdaki davranışı desteklediğinden, olayınızı yönlendirilmiş bir olay olarak uygulamak da iyi bir uygulamadır:

- Olaylar, birden çok denetimin üst öğesinde işlenebilir. Bir olay köpüren bir olaysa, öğe ağacındaki tek bir üst öğe olaya abone olabilir. Daha sonra uygulama yazarları birden çok denetim olayına yanıt vermek için bir işleyici kullanabilirsiniz. Örneğin, denetiminiz her maddenin bir <xref:System.Windows.Controls.ListBox> parçasıysa (bir maddeye dahil <xref:System.Windows.DataTemplate>olduğundan), uygulama geliştiricisi denetiminizin olayı nın <xref:System.Windows.Controls.ListBox>olay ını tanımlayabilir. Olay denetimlerden herhangi birinde oluştuğunda, olay işleyicisi çağrılır.

- Yönlendirilen olaylar, uygulama <xref:System.Windows.EventSetter>geliştiricilerin bir stil içinde bir olayın işleyicisini belirtmelerini sağlayan bir , kullanılabilir.

- Yönlendirilen olaylar kullanarak <xref:System.Windows.EventTrigger>özellikleri canlandırmak için yararlı olan [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]bir , kullanılabilir . Daha fazla bilgi için [Animasyona Genel Bakış'a](../graphics-multimedia/animation-overview.md)bakın.

Aşağıdaki örnek, aşağıdakileri yaparak yönlendirilmiş bir olayı tanımlar:

- Alan <xref:System.Windows.RoutedEvent> olarak adlandırılan `ValueChangedEvent` bir `public` `static` `readonly` tanımlayıcı tanımlayın.

- Yöntemi arayarak yönlendirilen <xref:System.Windows.EventManager.RegisterRoutedEvent%2A?displayProperty=nameWithType> olayı kaydedin. Örnek, aradığında <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>aşağıdaki bilgileri belirtir:

  - Olayın adı `ValueChanged`.

  - Yönlendirme <xref:System.Windows.RoutingStrategy.Bubble>stratejisi, kaynaktaki bir olay işleyicisinin (olayı yükselten nesne) önce çağrıldığı ve daha sonra kaynağın üst öğelerindeki olay işleyicilerinin en yakın üst öğedeki olay işleyicisi ile başlayarak art arda çağrıldığı anlamına gelir.

  - Olay işleyicisi türü, bir <xref:System.Windows.RoutedPropertyChangedEventHandler%601> <xref:System.Decimal> tür ile inşa edilir.

  - Olayın sahip olduğu `NumericUpDown`tür.

- Adlandırılmış `ValueChanged` ve olay alalı bildirimleri içeren herkese açık bir olayı bildirin. Örnek, <xref:System.Windows.UIElement.AddHandler%2A> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olay hizmetlerini kullanmak <xref:System.Windows.UIElement.RemoveHandler%2A> için `remove` erişimci bildiriminde `add` ve erişimci bildiriminde çağrıda bulunur.

- `ValueChanged` Olayı `OnValueChanged` yükselten korumalı, sanal bir yöntem oluşturun.

[!code-csharp[UserControlNumericUpDown#RoutedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#routedevent)]
[!code-vb[UserControlNumericUpDown#RoutedEvent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#routedevent)]

Daha fazla bilgi için, [Yönlendirilen Olaylara Genel Bakış'a](../advanced/routed-events-overview.md) bakın ve [Özel Yönlendirilmiş Etkinlik Oluşturun.](../advanced/how-to-create-a-custom-routed-event.md)

### <a name="use-binding"></a>Ciltleme Kullan

Denetiminizin UI'sini mantığından ayırmak için veri bağlama yı kullanmayı düşünün. Bu, özellikle bir <xref:System.Windows.Controls.ControlTemplate>. Veri bağlama yı kullandığınızda, UI'nin belirli bölümlerine koddan başvurma gereksinimini ortadan kaldırabilirsiniz. Kod, içinde <xref:System.Windows.Controls.ControlTemplate> bulunan <xref:System.Windows.Controls.ControlTemplate> ve değiştirilen öğelere başvuru yaptığında, başvurulan öğenin yeni <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.ControlTemplate>öğeye dahil edilmesi gerektiğinden, bu öğelere başvurmaktan kaçınmak iyi bir fikirdir.

Aşağıdaki örnek, <xref:System.Windows.Controls.TextBlock> `NumericUpDown` denetimin güncelleştirmesini, ona bir ad atamasını ve textbox'ı kodda ada göre yönlendirmesini sağlar.

[!code-xaml[UserControlNumericUpDownSimple#UIRefMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml#uirefmarkup)]

[!code-csharp[UserControlNumericUpDownSimple#UIRefCode](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml.cs#uirefcode)]
[!code-vb[UserControlNumericUpDownSimple#UIRefCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDownSimple/VisualBasic/NumericUpDown.xaml.vb#uirefcode)]

Aşağıdaki örnekte aynı şeyi gerçekleştirmek için bağlama kullanır.

[!code-xaml[UserControlNumericUpDown#Binding](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml#binding)]

Veri bağlama hakkında daha fazla bilgi için [bkz.](../../../desktop-wpf/data/data-binding-overview.md)

### <a name="design-for-designers"></a>Tasarımcılar için Tasarım

Visual Studio için WPF Designer'da özel WPF denetimleri için destek almak için (örneğin, Özellikler penceresinde özellik düzenleme), aşağıdaki yönergeleri izleyin.  WPF Designer için geliştirme hakkında daha fazla bilgi için Visual [Studio'da Design XAML](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)bölümüne bakın.

#### <a name="dependency-properties"></a>Bağımlılık Özellikleri

CLR `get` ve `set` erişimcileri daha önce açıklandığı gibi "Bağımlılık Özelliklerini Kullan" adlı nda uyguladığından emin olun. Tasarımcılar bir bağımlılık özelliğinin varlığını algılamak için sarıcıyı kullanabilir, ancak onlar, örneğin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve denetim istemcileri, özelliği alırken veya ayarlarken erişimcileri aramak zorunda değildir.

#### <a name="attached-properties"></a>Ekli Özellikler

Aşağıdaki yönergeleri kullanarak özel denetimler üzerinde ekli özellikleri uygulamalısınız:

- `public` `static` `readonly` <xref:System.Windows.DependencyProperty> *PropertyName* `Property` Yöntemi kullanarak oluşturan form PropertyName bir var. <xref:System.Windows.DependencyProperty.RegisterAttached%2A> Geçirilen özellik adı <xref:System.Windows.DependencyProperty.RegisterAttached%2A> *PropertyName*ile eşleşmelidir.

- PropertyName ve `public` `static` `Set` `Get` *PropertyName* *PropertyName* adlı bir çift CLR yöntemi uygulayın. Her iki yöntem de <xref:System.Windows.DependencyProperty> ilk bağımsız değişken olarak türetilen bir sınıf kabul etmelidir. `Set` *PropertyName* yöntemi, türü özellik için kayıtlı veri türüyle eşleşen bir bağımsız değişkeni de kabul eder. `Get` *PropertyName* yöntemi aynı türde bir değer döndürmelidir. `Set` *Özellik Adı* yöntemi eksikse, özellik salt okunur olarak işaretlenir.

- `Set`*PropertyName* `Get`ve *PropertyName,* sırasıyla hedef bağımlılık nesnesindeki <xref:System.Windows.DependencyObject.GetValue%2A> yöntemlere <xref:System.Windows.DependencyObject.SetValue%2A> doğrudan yönlendirilmelidir. Tasarımcılar, yöntem sarıcı aracılığıyla arayarak veya hedef bağımlılık nesnesine doğrudan çağrı yaparak ekli özelliğe erişebilir.

Ekteki özellikler hakkında daha fazla bilgi için [bkz.](../advanced/attached-properties-overview.md)

### <a name="define-and-use-shared-resources"></a>Paylaşılan Kaynakları Tanımlama ve Kullanma

Denetiminizi uygulamanızla aynı derlemeye ekleyebilirsiniz veya denetiminizi birden çok uygulamada kullanılabilecek ayrı bir derlemede paketleyebilirsiniz. Çoğunlukla, bu konuda tartışılan bilgiler kullandığınız yöntemden bağımsız olarak geçerlidir.  Ancak kayda değer bir fark vardır.  Bir denetimi uygulamayla aynı derlemeye koyduğunuzda, App.xaml dosyasına genel kaynaklar eklemekte özgürsunuz. Ancak yalnızca denetimleri içeren bir <xref:System.Windows.Application> derlemeile ilişkili bir nesne yoktur, bu nedenle app.xaml dosyası kullanılamaz.

Bir uygulama bir kaynak aradığında, aşağıdaki sırayla üç düzeye bakar:

1. Öğe düzeyi.

   Sistem, kaynağa başvuruyapan öğeyle başlar ve ardından kök öğeye ulaşılıncaya kadar mantıksal üst öğenin kaynaklarını arar.

2. Uygulama düzeyi.

   Nesne tarafından <xref:System.Windows.Application> tanımlanan kaynaklar.

3. Tema düzeyi.

   Tema düzeyindesözlükler Temalar adlı bir alt klasörde depolanır.  Temalar klasöründeki dosyalar temalara karşılık gelir.  Örneğin, Aero.NormalColor.xaml, Luna.NormalColor.xaml, Royale.NormalColor.xaml, ve benzeri olabilir.  Generic.xaml adında bir dosyanız da olabilir.  Sistem temalar düzeyinde bir kaynak aradığında, önce temalı dosyada arar ve sonra generic.xaml'da arar.

Denetiminiz uygulamadan ayrı bir derlemedeyken, genel kaynaklarınızı öğe düzeyinde veya tema düzeyine koymanız gerekir. Her iki yöntemin de avantajları vardır.

#### <a name="defining-resources-at-the-element-level"></a>Öğe Düzeyinde Kaynakları Tanımlama

Özel bir kaynak sözlüğü oluşturup denetiminizin kaynak sözlüğüyle birleştirerek paylaşılan kaynakları öğe düzeyinde tanımlayabilirsiniz.  Bu yöntemi kullandığınızda, kaynak dosyanızı istediğiniz her şeyi adlandırabilirsiniz ve bu dosya denetimlerinizle aynı klasörde olabilir. Öğe düzeyindeki kaynaklar, basit dizeleri anahtar olarak da kullanabilir. Aşağıdaki örnek, Dictionary1.xaml adlı bir <xref:System.Windows.Media.LinearGradientBrush> kaynak dosyası oluşturur.

[!code-xaml[SharedResources#1](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/Dictionary1.xaml#1)]

Sözlüğünüztanımlanmıştır sonra, denetiminizin kaynak sözlüğüyle birleştirmeniz gerekir.  Bunu kullanarak veya [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kodkullanarak yapabilirsiniz.

Aşağıdaki örnek kullanarak bir kaynak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]sözlüğü birleştirir.

[!code-xaml[SharedResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml#2)]

Bu yaklaşımın dezavantajı, <xref:System.Windows.ResourceDictionary> bir nesneye her başvuruyaptığınızda oluşturulmuş olmasıdır.  Örneğin, kitaplığınızda 10 özel denetiminiz varsa ve xaml kullanarak her denetim için paylaşılan kaynak <xref:System.Windows.ResourceDictionary> sözlüklerini birleştirirseniz, 10 özdeş nesne oluşturursunuz.  Kaynakları kodda birleştiren ve elde edilen <xref:System.Windows.ResourceDictionary>.

Aşağıdaki örnek, paylaşılan <xref:System.Windows.ResourceDictionary>bir sınıf döndürür.

[!code-csharp[SharedResources#3](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/SharedDictionaryManager.cs#3)]

Aşağıdaki örnek, paylaşılan kaynağı, denetlemenin oluşturucusundaki özel denetimin kaynaklarıyla, aramadan `InitializeComponent`önce birleştirir.  Statik `SharedDictionaryManager.SharedDictionary` bir özellik olduğundan, <xref:System.Windows.ResourceDictionary> yalnızca bir kez oluşturulur. Kaynak sözlüğü çağrılmadan `InitializeComponent` önce birleştirilmeden önce birleştirilmeden önce [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kaynaklar dosyasındaki denetimiçin kullanılabilir.

[!code-csharp[SharedResources#4](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml.cs#4)]

#### <a name="defining-resources-at-the-theme-level"></a>Tema Düzeyinde Kaynakları Tanımlama

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]farklı Windows temaları için kaynak oluşturmanıza olanak tanır.  Denetim yazarı olarak, hangi temanın kullanıldığına bağlı olarak denetiminizin görünümünü değiştirmek için belirli bir tema için bir kaynak tanımlayabilirsiniz. Örneğin, Windows Classic <xref:System.Windows.Controls.Button> temasındaki (Windows 2000 için varsayılan tema) bir <xref:System.Windows.Controls.Button> görünümü, her tema için farklı <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.ControlTemplate> bir tema kullandığından, Windows Luna temasındaki (Windows XP için varsayılan tema) farklıdır.

Bir temaya özgü kaynaklar, belirli bir dosya adı içeren bir kaynak sözlüğünde tutulur. Bu dosyalar, denetimi içeren `Themes` klasörün bir alt klasörü olan adlı bir klasörde olmalıdır. Aşağıdaki tabloda kaynak sözlüğü dosyaları ve her dosyayla ilişkili tema listelenir:

|Kaynak sözlüğü dosya adı|Windows teması|
|-----------------------------------|-------------------|
|`Classic.xaml`|Windows XP'de Klasik Windows 9x/2000 görünümü|
|`Luna.NormalColor.xaml`|Windows XP'de varsayılan mavi tema|
|`Luna.Homestead.xaml`|Windows XP'de zeytin teması|
|`Luna.Metallic.xaml`|Windows XP'de gümüş tema|
|`Royale.NormalColor.xaml`|Windows XP Media Center Sürümü'nde varsayılan tema|
|`Aero.NormalColor.xaml`|Windows Vista'da varsayılan tema|

Her tema için bir kaynak tanımlamanız gerekmez. Belirli bir tema için kaynak tanımlanmamışsa, `Classic.xaml` kaynak denetimini denetler. Kaynak, geçerli temaya karşılık gelen dosyada tanımlanmamışsa `Classic.xaml`veya denetim, kaynak sözlüğü dosyasında bulunan `generic.xaml`genel kaynağı kullanır.  Dosya, `generic.xaml` teme özgü kaynak sözlüğü dosyalarıyla aynı klasörde bulunur. Belirli `generic.xaml` bir Windows temasıyla örtüşmese de, yine de tema düzeyinde bir sözlüktür.

Tema ve Kullanıcı Arabirimi otomasyon destek örneği ile [C#](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp) veya [Visual Basic](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic) NumericUpDown özel `NumericUpDown` denetimi, denetim için iki kaynak sözlük içerir: biri generic.xaml'da, diğeri luna.normalcolor.xaml'dadır.

Temalı özel <xref:System.Windows.Controls.ControlTemplate> kaynak sözlüğü dosyalarından herhangi birini koyduğunuzda, denetiminiz için statik bir <xref:System.Windows.DependencyProperty.OverrideMetadata%28System.Type%2CSystem.Windows.PropertyMetadata%29> oluşturucu <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>oluşturmanız ve aşağıdaki örnekte gösterildiği gibi yöntemi aramanız gerekir.

[!code-csharp[CustomControlNumericUpDownOneProject#StaticConstructor](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/CSharp/NumericUpDown.cs#staticconstructor)]
[!code-vb[CustomControlNumericUpDownOneProject#StaticConstructor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/visualbasic/numericupdown.vb#staticconstructor)]

##### <a name="defining-and-referencing-keys-for-theme-resources"></a>Tema Kaynakları için Anahtar tanımlama ve başvurma

Öğe düzeyinde bir kaynak tanımladığınızda, bir dizeyi anahtarı olarak atayabilir ve dize üzerinden kaynağa erişebilirsiniz. Tema düzeyinde bir kaynak tanımladığınızda, bir <xref:System.Windows.ComponentResourceKey> kaynağı anahtar olarak kullanmanız gerekir.  Aşağıdaki örnek, generic.xaml'da bir kaynak tanımlar.

[!code-xaml[ThemeResourcesControlLibrary#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/Themes/generic.xaml#5)]

Aşağıdaki örnekte anahtar <xref:System.Windows.ComponentResourceKey> olarak belirterek kaynağa başvurur.

[!code-xaml[ThemeResourcesControlLibrary#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/NumericUpDown.xaml#6)]

##### <a name="specifying-the-location-of-theme-resources"></a>Tema Kaynaklarının Konumunu Belirtme

Denetim için kaynakları bulmak için barındırma uygulamasının derlemenin denetime özgü kaynaklar içerdiğini bilmesi gerekir. Denetimi içeren <xref:System.Windows.ThemeInfoAttribute> derlemeye ekleyerek bunu başarabilirsiniz. Genel <xref:System.Windows.ThemeInfoAttribute> kaynakların <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> konumunu belirten bir özelliği ve temalı <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A> özel kaynakların konumunu belirten bir özelliği vardır.

Aşağıdaki örnek, <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> genel <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A> ve <xref:System.Windows.ResourceDictionaryLocation.SourceAssembly>temaya özgü kaynakların denetimle aynı derlemede olduğunu belirtmek için, özellikleri ve özelliklerini ayarlar.

[!code-csharp[CustomControlNumericUpDown#ThemesSection](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/Properties/AssemblyInfo.cs#themessection)]
[!code-vb[CustomControlNumericUpDown#ThemesSection](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/my project/assemblyinfo.vb#themessection)]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio’da XAML tasarlama](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [WPF İçinde URI'leri Paketleme](../app-development/pack-uris-in-wpf.md)
- [Denetim Özelleştirme](control-customization.md)
