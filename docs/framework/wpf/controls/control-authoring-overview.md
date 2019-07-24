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
ms.openlocfilehash: 3ea5519259ba2ee31bfd6bc25f6bedf1f1250799
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401550"
---
# <a name="control-authoring-overview"></a>Denetim Yazımına Genel Bakış

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Denetim modelinin genişletilebilirliği, yeni bir denetim oluşturma gereksinimini önemli ölçüde azaltır. Ancak bazı durumlarda, hala özel bir denetim oluşturmanız gerekebilir. Bu konuda, içinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]özel bir denetim ve farklı denetim yazma modelleri oluşturma gereksiniminizi en aza indirecek özellikler açıklanmaktadır. Bu konuda ayrıca nasıl yeni bir denetim oluşturacağınız gösterilmektedir.

<a name="when_to_write_a_new_control"></a>

## <a name="alternatives-to-writing-a-new-control"></a>Yeni denetim yazma alternatifleri

Tarihsel olarak, var olan bir denetimden özelleştirilmiş bir deneyim almak isterseniz, denetimin, arka plan rengi, kenarlık genişliği ve yazı tipi boyutu gibi standart özelliklerini değiştirmekle sınırlı olursunuz. Bir denetimin görünüşünü veya davranışını bu önceden tanımlanmış parametrelerin ötesinde uzatmak istiyorsanız, genellikle var olan bir denetimden devralarak ve denetimi çizmekten sorumlu yöntemi geçersiz kılarak yeni bir denetim oluşturmanız gerekir.  Yine de bir seçenek olsa da, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] var olan denetimleri zengin içerik modeli, stiller, şablonlar ve Tetikleyiciler kullanarak özelleştirmenize olanak sağlar. Aşağıdaki listede, bu özelliklerin yeni bir denetim oluşturmak zorunda kalmadan özel ve tutarlı deneyimler oluşturmak için nasıl kullanılabileceği hakkında örnekler verilmektedir.

- **Zengin Içerik.** Standart [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimlerin birçoğu zengin içerikleri destekler. Örneğin, öğesinin <xref:System.Windows.Controls.Button> içerik özelliği türündedir <xref:System.Object>, bu nedenle teorik olarak her şey bir <xref:System.Windows.Controls.Button>üzerinde görüntülenebilir.  Bir düğmenin bir görüntü ve metin görüntülemesi için, <xref:System.Windows.Controls.TextBlock> bir görüntü ve a <xref:System.Windows.Controls.StackPanel> ekleyebilir <xref:System.Windows.Controls.ContentControl.Content%2A> ve özelliğini özelliğine atayabilirsiniz <xref:System.Windows.Controls.StackPanel> . Denetimler görsel öğeleri ve rastgele [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] verileri görüntüleyeceğinden, yeni bir denetim oluşturmanız veya var olan bir denetimi karmaşık görselleştirmeyi destekleyecek şekilde değiştirmeniz daha az olabilir. ' Deki içerik modeli <xref:System.Windows.Controls.Button> ve içindeki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]diğer içerik modelleri hakkında daha fazla bilgi için bkz. [WPF içerik modeli](wpf-content-model.md).

- **Stillerde.** <xref:System.Windows.Style> , Bir denetimin özelliklerini temsil eden bir değerler koleksiyonudur. Stilleri kullanarak, istenen denetim görünümü ve davranışı için yeni bir denetim yazmadan yeniden kullanılabilir bir temsili oluşturabilirsiniz. Örneğin, tüm denetimlerinizin <xref:System.Windows.Controls.TextBlock> , 14 yazı tipi boyutuyla kırmızı, Arial yazı tipine sahip olmasını istediğinizi varsayalım. Kaynak olarak bir stil oluşturabilir ve uygun özellikleri uygun şekilde ayarlayabilirsiniz. Sonra uygulamanıza <xref:System.Windows.Controls.TextBlock> eklediğiniz her bir görünüm aynı olur.

- **Veri şablonları.** Bir <xref:System.Windows.DataTemplate> denetimde verilerin nasıl görüntülendiğini özelleştirmenizi sağlar. Örneğin, bir, <xref:System.Windows.DataTemplate> ' <xref:System.Windows.Controls.ListBox>de verilerin nasıl görüntüleneceğini belirtmek için kullanılabilir.  Buna bir örnek için bkz. [veri şablonu oluşturmaya genel bakış](../data/data-templating-overview.md).  Verilerin görünümünü özelleştirmenin yanı sıra, <xref:System.Windows.DataTemplate> özel uıof 'ta çok sayıda esneklik sağlayan UI öğeleri içerebilir.  Örneğin, bir <xref:System.Windows.DataTemplate>kullanarak, her bir öğenin bir onay kutusu <xref:System.Windows.Controls.ComboBox> içerdiği bir oluşturabilirsiniz.

- **Denetim şablonları.** İçindeki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pek çok denetim, <xref:System.Windows.Controls.ControlTemplate> denetimin işlevselliğiyle denetimin bir denetimin görünüşünü ayıran denetimin yapısını ve görünümünü tanımlamak için kullanır. Denetimin görünümünü büyük ölçüde tekrar tanımlayarak <xref:System.Windows.Controls.ControlTemplate>değiştirebilirsiniz.  Örneğin, bir denetim ışığı gibi görünen bir denetim istediğinizi varsayalım. Bu denetimde basit bir kullanıcı arabirimi ve işlevselliği vardır.  Denetim üç dairedir, tek seferde yalnızca bir tane olabilir. Bazı yansımalardan sonra, bir <xref:System.Windows.Controls.RadioButton> kerede yalnızca bir tane seçilmekte olan işlevi sunduğunu fark edebilirsiniz, ancak varsayılan görünümü <xref:System.Windows.Controls.RadioButton> bir trafik ışığı üzerindeki ışıklar gibi görünmüyor.  , <xref:System.Windows.Controls.RadioButton> Görünümünü tanımlamak için bir denetim şablonu kullandığından, denetimin gereksinimlerine uyacak <xref:System.Windows.Controls.ControlTemplate> şekilde öğesini yeniden tanımlamak ve trafik durma alanınızı açmak için radyo düğmelerini kullanmak kolaydır.

  > [!NOTE]
  > , Bir kullanabilir ancak, <xref:System.Windows.DataTemplate> Bu örnekte yeterli değildir. <xref:System.Windows.Controls.RadioButton> <xref:System.Windows.DataTemplate>  , <xref:System.Windows.DataTemplate> Bir denetimin içeriğinin görünümünü tanımlar. Bir <xref:System.Windows.Controls.RadioButton>durumunda, içerik seçili <xref:System.Windows.Controls.RadioButton> olup olmadığını gösteren dairenin sağında görüntülenir.  Trafik ışığı örneğinde radyo düğmesi yalnızca "hafif" bir daire olmalıdır. Durma ışığı için görünüm gereksinimi, <xref:System.Windows.Controls.RadioButton>' nin varsayılan görünümüyle farklı olduğundan, öğesini yeniden <xref:System.Windows.Controls.ControlTemplate>tanımlamak gerekir.  Genel a <xref:System.Windows.DataTemplate> , bir denetimin içeriğini (veya verilerini) tanımlamak için kullanılır ve bir <xref:System.Windows.Controls.ControlTemplate> denetimin nasıl yapılandırıldığını tanımlamak için kullanılır.

- **Tetikleyiciler.** , Bir denetimin görünümünü ve davranışını yeni bir denetim oluşturmadan dinamik olarak değiştirmenize olanaksağlar.<xref:System.Windows.Trigger> Örneğin, uygulamanızda birden çok <xref:System.Windows.Controls.ListBox> denetiminizin olduğunu ve her birinin <xref:System.Windows.Controls.ListBox> seçildikleri zaman kalın ve kırmızı olmasını istediğinizi varsayalım. İlk işlem, ' den <xref:System.Windows.Controls.ListBox> devralan bir sınıf oluşturmak ve seçilen öğenin görünümünü değiştirmek için <xref:System.Windows.Controls.Primitives.Selector.OnSelectionChanged%2A> yöntemini geçersiz kılmak, ancak bir ' nin görünümünü değiştiren bir <xref:System.Windows.Controls.ListBoxItem> stiline tetikleyici eklemek daha iyi bir yaklaşım olabilir. Seçilen öğe. Tetikleyici, özellik değerlerini değiştirmenize veya bir özelliğin değerine göre eylem yapmanıza olanak sağlar. Bir <xref:System.Windows.EventTrigger> olay gerçekleştiğinde eylemler gerçekleştirmenizi sağlar.

Stiller, şablonlar ve Tetikleyiciler hakkında daha fazla bilgi için bkz. [Stil oluşturma ve şablon](styling-and-templating.md)oluşturma.

Genel olarak, denetiminiz var olan bir denetimin işlevselliğini yansıtır, ancak denetimin farklı görünmesini istiyorsanız, bu bölümde açıklanan yöntemlerden herhangi birini kullanıp kullanmayacağınızı, var olan denetimin görünümünü değiştirmek için göz önünde bulundurmanız gerekir.

<a name="models_for_control_authoring"></a>

## <a name="models-for-control-authoring"></a>Denetim yazma modelleri

Zengin içerik modeli, stiller, şablonlar ve Tetikleyiciler, yeni bir denetim oluşturmanız gereksinimini en aza indirir. Ancak, yeni bir denetim oluşturmanız gerekiyorsa, içinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]farklı denetim yazma modellerinin anlaşılması önemlidir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], her biri farklı bir özellik kümesi ve esneklik düzeyi sağlayan denetim oluşturmak için üç genel model sağlar. Üç modelin temel sınıfları, <xref:System.Windows.Controls.UserControl> <xref:System.Windows.Controls.Control>ve <xref:System.Windows.FrameworkElement>' dir.

### <a name="deriving-from-usercontrol"></a>UserControl 'ten türetme

' De bir denetim oluşturmanın en kolay yolu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , ' den <xref:System.Windows.Controls.UserControl>türetmektir. Öğesinden <xref:System.Windows.Controls.UserControl>devralan bir denetim oluşturduğunuzda, var olan bileşenleri <xref:System.Windows.Controls.UserControl>içine ekleyin, bileşenleri adlandırın ve içindeki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]olay işleyicilerini başvuru yapın. Daha sonra adlandırılmış öğelere başvurabilir ve koddaki olay işleyicilerini tanımlayabilirsiniz. Bu geliştirme modeli, içinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]uygulama geliştirme için kullanılan modele çok benzer.

Doğru şekilde oluşturulıyorsa, <xref:System.Windows.Controls.UserControl> zengin içerik, stiller ve tetikleyicilerin avantajlarından faydalanabilirsiniz. Ancak, denetiminiz öğesinden <xref:System.Windows.Controls.UserControl>devralırsa, denetiminizi kullanan kişiler görünümünü özelleştirmek için bir <xref:System.Windows.DataTemplate> veya <xref:System.Windows.Controls.ControlTemplate> kullanamaz.  Şablonları destekleyen özel bir denetim oluşturmak için <xref:System.Windows.Controls.Control> sınıfından veya türetilmiş sınıflarından birinden ( <xref:System.Windows.Controls.UserControl>dışında) türetmeniz gerekir.

#### <a name="benefits-of-deriving-from-usercontrol"></a>UserControl 'dan Türetmenin avantajları

Aşağıdakilerin tümü uygulandıysanız ' dan <xref:System.Windows.Controls.UserControl> türetmeyi göz önünde bulundurun:

- Bir uygulamayı nasıl derlemenize benzer şekilde denetiminizi oluşturmak istersiniz.

- Denetiminiz yalnızca mevcut bileşenlerden oluşur.

- Karmaşık özelleştirmeyi desteklemek zorunda değilsiniz.

### <a name="deriving-from-control"></a>Denetimden türetme

Sınıfından türetmek, varolan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimlerin çoğu tarafından kullanılan modeldir. <xref:System.Windows.Controls.Control> <xref:System.Windows.Controls.Control> Sınıfından devralan bir denetim oluşturduğunuzda, görünümünü şablonlar kullanarak tanımlarsınız. Bunu yaptığınızda, işlemsel mantığı görsel gösterimden ayırdığınızda. Ayrıca, olaylar yerine komutları ve bağlamaları kullanarak ve mümkün olan <xref:System.Windows.Controls.ControlTemplate> her durumda öğelere başvurmaktan kaçınarak UI ve mantığın ayrılmasıyla emin olabilirsiniz.  Denetiminizin Kullanıcı arabirimi ve mantığı düzgün şekilde ayrıldıysanız, denetiminizin bir kullanıcısı, görünümünü özelleştirmek <xref:System.Windows.Controls.ControlTemplate> için denetimi yeniden tanımlayabilir. Özel <xref:System.Windows.Controls.Control> derleme, oluşturma kadar <xref:System.Windows.Controls.UserControl>basit olmasa da, özel <xref:System.Windows.Controls.Control> bir en esnekliği sağlar.

#### <a name="benefits-of-deriving-from-control"></a>Denetimden Türetmenin avantajları

Aşağıdakilerden birini uyguladığınızda <xref:System.Windows.Controls.Control> <xref:System.Windows.Controls.UserControl> sınıfını kullanmak yerine ' den türetmeyi göz önünde bulundurun:

- Denetiminizin görünümünün aracılığıyla <xref:System.Windows.Controls.ControlTemplate>özelleştirilebilir olmasını istiyorsunuz.

- Denetiminizin farklı temaları desteklemesini istiyorsunuz.

### <a name="deriving-from-frameworkelement"></a>FrameworkElement 'ten türetme

Var olan öğeleri oluşturma <xref:System.Windows.Controls.UserControl> işleminden <xref:System.Windows.Controls.Control> türetilen veya bunları temel alan denetimler. Birçok senaryoda, ' den <xref:System.Windows.FrameworkElement> devralan herhangi bir nesne bir <xref:System.Windows.Controls.ControlTemplate>içinde olabileceğinden, bu, kabul edilebilir bir çözümdür. Ancak, bir denetimin görünümü basit öğe kompozisyonunun işlevlerinden daha fazlasını gerektirdiğinde zaman vardır. Bu senaryolar için, bir bileşeni temel alan <xref:System.Windows.FrameworkElement> doğru tercih edilir.

Yapı <xref:System.Windows.FrameworkElement>tabanlı bileşenler için iki standart yöntem vardır: doğrudan işleme ve özel öğe oluşturma. Doğrudan işleme <xref:System.Windows.UIElement.OnRender%2A> <xref:System.Windows.Media.DrawingContext> yöntemi geçersiz kılmayı ve bileşen görsellerini açıkça tanımlayan işlemleri sağlamayı içerir. <xref:System.Windows.FrameworkElement> Bu, ve <xref:System.Windows.Controls.Image> <xref:System.Windows.Controls.Border>tarafından kullanılan yöntemidir. Özel öğe kompozisyonu, bileşeninizin görünümünü oluşturmak <xref:System.Windows.Media.Visual> için türündeki nesnelerin kullanımını içerir. Bir örnek için bkz. [DrawingVisual nesnelerini kullanma](../graphics-multimedia/using-drawingvisual-objects.md). <xref:System.Windows.Controls.Primitives.Track>, içinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özel öğe kompozisyonu kullanan bir denetimin örneğidir. Aynı denetimde doğrudan işleme ve özel öğe oluşturmayı karıştırmak da mümkündür.

#### <a name="benefits-of-deriving-from-frameworkelement"></a>FrameworkElement 'ten Türetmenin avantajları

Aşağıdakilerden birini uyguladığınızda <xref:System.Windows.FrameworkElement> ' den türetmeyi göz önünde bulundurun:

- Denetimin görünümü üzerinde basit öğe kompozisyonu tarafından sağlananların ötesinde kesin denetim sahibi olmak istiyorsunuz.

- Kendi oluşturma mantığınızı tanımlayarak denetiminizin görünümünü tanımlamak istiyorsunuz.

- <xref:System.Windows.Controls.UserControl> Ve<xref:System.Windows.Controls.Control>ile mümkün olan unsurların ötesine geçen önemli yollarla mevcut öğeleri oluşturmak istersiniz.

<a name="control_authoring_basics"></a>

## <a name="control-authoring-basics"></a>Denetim Yazma Temelleri

Daha önce anlatıldığı gibi, en güçlü özelliklerinden [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] biri de bir denetimin temel özelliklerinin, görünümünü ve davranışını değiştirmek, ancak yine de özel bir denetim oluşturmaya gerek yoktur. Stil, veri bağlama ve tetikleyici özellikleri, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellik sistemi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve olay sistemi tarafından mümkün hale getirilir. Aşağıdaki bölümlerde, özel denetim oluşturmak için kullandığınız model ne olursa olsun, özel denetim kullanıcılarının, bu özellikleri ' de bulunan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]bir denetim için yaptıkları gibi kullanabilmesi için, izlemeniz gereken bazı yöntemler açıklanır.

### <a name="use-dependency-properties"></a>Bağımlılık özelliklerini kullanma

Bir özellik bir bağımlılık özelliği olduğunda, şunları yapmak mümkündür:

- Bir stilde özelliği ayarlayın.

- Özelliği bir veri kaynağına bağlayın.

- Özelliğin değeri olarak dinamik bir kaynak kullanın.

- Özelliği canlandırın.

Denetiminizin bir özelliğinin bu işlevlerden herhangi birini desteklemesini istiyorsanız, bunu bir bağımlılık özelliği olarak uygulamalısınız. Aşağıdaki örnek, aşağıdaki işlemleri gerçekleştirerek adlı `Value` bir bağımlılık özelliğini tanımlar:

- `ValueProperty` <xref:System.Windows.DependencyProperty> Alanolarak`static` adlandırılan birtanımlayıcıtanımlayın.`public` `readonly`

- Aşağıdaki belirtmek için, özellik adını çağırarak <xref:System.Windows.DependencyProperty.Register%2A?displayProperty=nameWithType>özellik sistemiyle kaydedin:

  - Özelliğin adı.

  - Özelliğin türü.

  - Özelliğin sahibi olan tür.

  - Özelliğin meta verileri. Meta veriler, özelliğinin varsayılan değerini, a <xref:System.Windows.CoerceValueCallback> <xref:System.Windows.PropertyChangedCallback>ve, içerir.

- `Value`Özellik ve erişimcileri`set` uygulayarak bağımlılık özelliğini kaydetmek için kullanılan aynı ada sahip adlı bir clr sarmalayıcı özelliği tanımlayın `get` . `get` <xref:System.Windows.DependencyObject.GetValue%2A> Ve `set` erişimcilerinin yalnızca ve<xref:System.Windows.DependencyObject.SetValue%2A> sırasıyla çağrı olduğunu unutmayın. Bağımlılık özellikleri erişimcilerinin, istemciler [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] için ek mantık içermemesi ve bu nedenle erişimcileri ve <xref:System.Windows.DependencyObject.SetValue%2A> çağrı ve doğrudan çağırabileceğinden <xref:System.Windows.DependencyObject.GetValue%2A> bu önerilir. Örneğin, bir özellik bir veri kaynağına bağlandığında, özelliğin `set` erişimcisi çağrılmaz.  Get ve set erişimcilerine ek mantık eklemek yerine,,, <xref:System.Windows.ValidateValueCallback> <xref:System.Windows.CoerceValueCallback>, ve <xref:System.Windows.PropertyChangedCallback> ' ı, değiştiğinde değerini yanıtlamak veya denetlemek için kullanın.  Bu geri çağrılar hakkında daha fazla bilgi için bkz. [bağımlılık özelliği geri çağırmaları ve doğrulama](../advanced/dependency-property-callbacks-and-validation.md).

- <xref:System.Windows.CoerceValueCallback> Adlandırılmış`CoerceValue`için bir yöntem tanımlayın. `CoerceValue`Bunun daha büyük veya `MinValue` eşit ya da `MaxValue`daha küçük veya eşit olmasını sağlar. `Value`

- <xref:System.Windows.PropertyChangedCallback> Adlı`OnValueChanged`için bir yöntem tanımlayın. `OnValueChanged`bir <xref:System.Windows.RoutedPropertyChangedEventArgs%601> nesnesi oluşturur ve `ValueChanged` yönlendirilmiş olayı yükseltmek için hazırlar. Yönlendirilmiş olaylar, sonraki bölümde ele alınmıştır.

[!code-csharp[UserControlNumericUpDown#DependencyProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#dependencyproperty)]
[!code-vb[UserControlNumericUpDown#DependencyProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#dependencyproperty)]

Daha fazla bilgi için bkz. [Özel bağımlılık özellikleri](../advanced/custom-dependency-properties.md).

### <a name="use-routed-events"></a>Yönlendirilmiş olayları kullanma

Bağımlılık özellikleri, CLR özelliklerinin kavramını ek işlevlerle genişletmenin yanı da, yönlendirilmiş olaylar standart CLR olayları kavramını uzatır. Yeni [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir denetim oluşturduğunuzda, yönlendirilmiş bir olay aşağıdaki davranışı desteklediğinden, olayınızı yönlendirilmiş bir olay olarak uygulamak da iyi bir uygulamadır:

- Olaylar, birden fazla denetimin üst öğesi üzerinde işlenebilir. Bir olay bir kabarcıklanma olayıdır, öğe ağacındaki tek bir üst öğe olaya abone olabilir. Ardından, uygulama yazarları birden çok denetimin olayına yanıt vermek için bir işleyici kullanabilir. Örneğin, denetiminiz bir içindeki <xref:System.Windows.Controls.ListBox> her öğenin parçasıysa (bir ' a <xref:System.Windows.DataTemplate>dahil edildiği için), uygulama geliştiricisi, <xref:System.Windows.Controls.ListBox>denetim olayınızın ' de olay işleyicisini tanımlayabilir. Her bir denetim üzerinde olay gerçekleştiğinde olay işleyicisi çağırılır.

- Yönlendirilmiş olaylar, uygulama geliştiricilerinin bir stil <xref:System.Windows.EventSetter>içindeki bir olayın işleyicisini belirtmesini sağlayan bir ' de kullanılabilir.

- Yönlendirilmiş olaylar, kullanarak <xref:System.Windows.EventTrigger> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]özellikleri hareketlendirmek için yararlı olan bir içinde kullanılabilir. Daha fazla bilgi için bkz. [animasyon genel bakış](../graphics-multimedia/animation-overview.md).

Aşağıdaki örnek aşağıdakileri yaparak bir yönlendirilmiş olayı tanımlar:

- `ValueChangedEvent` <xref:System.Windows.RoutedEvent> Alanolarak`static` adlandırılan birtanımlayıcıtanımlayın.`public` `readonly`

- <xref:System.Windows.EventManager.RegisterRoutedEvent%2A?displayProperty=nameWithType> Yöntemini çağırarak yönlendirilmiş olayı kaydedin. Örnek, çağrı <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>sırasında aşağıdaki bilgileri belirtir:

  - Olayın `ValueChanged`adı.

  - Yönlendirme stratejisi <xref:System.Windows.RoutingStrategy.Bubble>, kaynak üzerindeki bir olay işleyicisinin (olayı oluşturan nesne) ilk olarak çağrıldığı ve ardından kaynağın üst öğelerinde olay işleyicilerinin, en yakın olay işleyicisiyle başlayarak art arda çağrıldığı üst öğe.

  - Olay işleyicisinin <xref:System.Windows.RoutedPropertyChangedEventHandler%601>türü, bir <xref:System.Decimal> tür ile oluşturulur.

  - Olayın sahibi olan türü `NumericUpDown`.

- Adlı `ValueChanged` bir genel olay bildirin ve olay erişimcisi bildirimlerini içerir. <xref:System.Windows.UIElement.AddHandler%2A> Örnek, olay[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hizmetlerini kullanmak `add` <xref:System.Windows.UIElement.RemoveHandler%2A> için`remove` erişimci bildiriminde ve erişimci bildiriminde çağırır.

- `ValueChanged` Olayı oluşturan adlı `OnValueChanged` korumalı, sanal bir yöntem oluşturun.

[!code-csharp[UserControlNumericUpDown#RoutedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#routedevent)]
[!code-vb[UserControlNumericUpDown#RoutedEvent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#routedevent)]

Daha fazla bilgi için bkz. [yönlendirilmiş olaylara genel bakış](../advanced/routed-events-overview.md) ve [özel bir yönlendirilmiş olay oluşturma](../advanced/how-to-create-a-custom-routed-event.md).

### <a name="use-binding"></a>Bağlamayı kullan

Denetiminizin Kullanıcı arabirimini mantığa ayırmak için veri bağlamayı kullanmayı düşünün. Bu, bir <xref:System.Windows.Controls.ControlTemplate>kullanarak denetiminizin görünümünü tanımlarsanız özellikle önemlidir. Veri bağlamayı kullandığınızda, koddan Kullanıcı arabiriminin belirli bölümlerine başvurma gereksinimini ortadan kaldırabiliyor olabilirsiniz. <xref:System.Windows.Controls.ControlTemplate> Kod içinde olan öğelerin <xref:System.Windows.Controls.ControlTemplate> başvurduğu ve <xref:System.Windows.Controls.ControlTemplate> değiştirildiği, başvurulan öğenin yeni <xref:System.Windows.Controls.ControlTemplate>içine dahil olması gerektiği için, içinde bulunan öğelerin başvurmaması iyi bir fikirdir.

Aşağıdaki örnek <xref:System.Windows.Controls.TextBlock> `NumericUpDown` , denetimin ' de bir ad atamasını ve koddaki ada göre TextBox 'a başvurmayı sağlar.

[!code-xaml[UserControlNumericUpDownSimple#UIRefMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml#uirefmarkup)]

[!code-csharp[UserControlNumericUpDownSimple#UIRefCode](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml.cs#uirefcode)]
[!code-vb[UserControlNumericUpDownSimple#UIRefCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDownSimple/VisualBasic/NumericUpDown.xaml.vb#uirefcode)]

Aşağıdaki örnek, aynı şeyi gerçekleştirmek için bağlamayı kullanır.

[!code-xaml[UserControlNumericUpDown#Binding](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml#binding)]

Veri bağlama hakkında daha fazla bilgi için bkz. [veri bağlamaya genel bakış](../data/data-binding-overview.md).

### <a name="design-for-designers"></a>Tasarımcılar için tasarım

İçindeki özel WPF denetimleri için destek almak üzere [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] (örneğin, Özellikler penceresi ile özellik düzenlemesi), bu yönergeleri izleyin.  İçin [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]geliştirme hakkında daha fazla bilgi için bkz. [Visual Studio 'da xaml tasarlama](/visualstudio/designers/designing-xaml-in-visual-studio).

#### <a name="dependency-properties"></a>Bağımlılık Özellikleri

Daha önce açıklandığı gibi CLR `get` ve `set` erişimcileri, "bağımlılık özelliklerini kullan" bölümünde uyguladığınızdan emin olun. Tasarımcılar bir bağımlılık özelliğinin varlığını algılamak için sarmalayıcı kullanabilir, ancak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bu özellik ve denetimin istemcileri, özelliği alırken veya ayarlarken erişimcileri çağırmak için gerekli değildir.

#### <a name="attached-properties"></a>Ekli Özellikler

Aşağıdaki yönergeleri kullanarak özel denetimlere Ekli Özellikler uygulamalısınız:

- `public` `static` Yöntemikullanılarak<xref:System.Windows.DependencyProperty>  oluşturulan birformPropertyName`Property` 'e sahip. `readonly` <xref:System.Windows.DependencyProperty.RegisterAttached%2A> Geçirilen <xref:System.Windows.DependencyProperty.RegisterAttached%2A> Özellik adı *PropertyName*ile aynı olmalıdır.

- `public` `static` *PropertyName* ve PropertyName adlı `Set`bir çift clr yöntemiuygulayın.`Get` Her iki yöntem de ilk bağımsız değişkeni <xref:System.Windows.DependencyProperty> olarak sınıfından türetilmiş bir sınıfı kabul etmelidir. PropertyName yöntemi, türü özelliği için kayıtlı veri türüyle eşleşen bir bağımsız değişkeni de kabul eder.  `Set` PropertyName yöntemi aynı türde bir değer döndürmelidir.  `Get` PropertyName yöntemi eksikse, özelliği salt okunurdur olarak işaretlenir.  `Set`

- `Set`*PropertyName* ve `Get` *PropertyName* , sırasıyla hedef bağımlılık nesnesi <xref:System.Windows.DependencyObject.GetValue%2A> üzerindeki <xref:System.Windows.DependencyObject.SetValue%2A> ve yöntemlerine doğrudan yönlendirmelidir. Tasarımcılar, yöntem sarmalayıcısı aracılığıyla arayarak veya hedef bağımlılık nesnesine doğrudan çağrı yaparak ekli özelliğe erişebilir.

Ekli Özellikler hakkında daha fazla bilgi için bkz. [ekli özelliklere genel bakış](../advanced/attached-properties-overview.md).

### <a name="define-and-use-shared-resources"></a>Paylaşılan kaynakları tanımlama ve kullanma

Denetiminizi uygulamanız ile aynı derlemeye dahil edebilir veya birden çok uygulamada kullanılabilen ayrı bir derlemede denetiminizi paketleyebilir. Çoğu bölümde, bu konuda tartışılan bilgiler kullandığınız yöntemden bağımsız olarak geçerlidir.  Ancak, buna dikkat edilecek bir fark vardır.  Bir uygulamayı bir uygulama olarak aynı derlemeye yerleştirdiğinizde, App. xaml dosyasına genel kaynaklar ekleyebilirsiniz. Ancak yalnızca denetimleri içeren bir derlemeye kendisiyle ilişkili bir <xref:System.Windows.Application> nesne yoktur, bu nedenle App. xaml dosyası kullanılamaz.

Bir uygulama bir kaynağı ararken, üç düzeye aşağıdaki sırayla bakar:

1. Öğe düzeyi.

   Sistem, kaynağa başvuruda bulunan öğeyle başlar ve sonra mantıksal üst öğenin kaynaklarını arar ve bu nedenle kök öğeye ulaşılana kadar bu şekilde devam eder.

2. Uygulama düzeyi.

   <xref:System.Windows.Application> Nesne tarafından tanımlanan kaynaklar.

3. Tema düzeyi.

   Tema düzeyi sözlükler, Temalar adlı bir alt klasörde depolanır.  Temalar klasöründeki dosyalar temalara karşılık gelir.  Örneğin, Aero. NormalColor. xaml, Luna. NormalColor. xaml, Royale. NormalColor. xaml, vb. olabilir.  Ayrıca, Generic. xaml adlı bir dosyaya da sahip olabilirsiniz.  Sistem Temalar düzeyinde bir kaynak ararken, önce temaya özel dosyada arama yapar ve ardından bunu genel. xaml içinde arar.

Denetiminiz uygulamadan ayrı bir derlemede olduğunda, genel kaynaklarınızı öğe düzeyinde veya tema düzeyinde koymanız gerekir. Her iki yöntem de avantajlarına sahiptir.

#### <a name="defining-resources-at-the-element-level"></a>Öğe düzeyinde kaynakları tanımlama

Özel bir kaynak sözlüğü oluşturarak ve denetimin kaynak sözlüğü ile birleştirerek, öğe düzeyinde paylaşılan kaynaklar tanımlayabilirsiniz.  Bu yöntemi kullandığınızda, kaynak dosyanıza istediğiniz her şeyi verebilir ve denetimleriniz ile aynı klasörde olabilir. Öğe düzeyindeki kaynaklar, anahtar olarak basit dizeler da kullanabilir. Aşağıdaki örnek Dictionary1. xaml <xref:System.Windows.Media.LinearGradientBrush> adlı bir kaynak dosyası oluşturur.

[!code-xaml[SharedResources#1](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/Dictionary1.xaml#1)]

Sözlüğünüzü tanımladıktan sonra denetimin kaynak sözlüğü ile birleştirmeniz gerekir.  Bunu veya kodunu kullanarak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yapabilirsiniz.

Aşağıdaki örnek kullanarak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]bir kaynak sözlüğünü birleştirir.

[!code-xaml[SharedResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml#2)]

Bu yaklaşımın dezavantajı, ona her başvurduğunuzda bir <xref:System.Windows.ResourceDictionary> nesne oluşturulur.  Örneğin, kitaplığınızda 10 özel denetiminiz varsa ve XAML kullanarak her denetim için paylaşılan kaynak sözlüklerini birleştirirseniz, 10 özdeş <xref:System.Windows.ResourceDictionary> nesne oluşturursunuz.  Bu, koddaki kaynakları birleştiren ve sonucu <xref:System.Windows.ResourceDictionary>döndüren bir statik sınıf oluşturarak bunu önleyebilirsiniz.

Aşağıdaki örnek, paylaşılan <xref:System.Windows.ResourceDictionary>bir sınıf oluşturur.

[!code-csharp[SharedResources#3](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/SharedDictionaryManager.cs#3)]

Aşağıdaki örnek, bir paylaşılan kaynağı, çağrı `InitializeComponent`yapmadan önce denetimin oluşturucusunda özel bir denetimin kaynaklarıyla birleştirir.  Statik bir özellik <xref:System.Windows.ResourceDictionary> olduğundan, yalnızca bir kez oluşturulur. `SharedDictionaryManager.SharedDictionary` Kaynak sözlüğü çağrılmadan önce `InitializeComponent` birleştirildiğinden, kaynaklar [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyasında denetim için kullanılabilir.

[!code-csharp[SharedResources#4](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml.cs#4)]

#### <a name="defining-resources-at-the-theme-level"></a>Tema düzeyinde kaynakları tanımlama

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]farklı Windows temaları için kaynaklar oluşturmanızı sağlar.  Denetim yazarı olarak, belirli bir temaya ait bir kaynağı tanımlayabilir ve hangi temanın kullanımda olduğuna bağlı olarak denetiminizin görünümünü değiştirebilirsiniz. Örneğin, Windows <xref:System.Windows.Controls.Button> klasik teması içindeki (Windows 2000 için varsayılan tema) görünümü, farklı <xref:System.Windows.Controls.ControlTemplate> bir değer <xref:System.Windows.Controls.Button> kullandığından Windows Luna temasının ( <xref:System.Windows.Controls.Button> Windows XP için varsayılan tema) bir ' dan farklıdır. Her tema için.

Bir temaya özgü kaynaklar, belirli bir dosya adına sahip bir kaynak sözlüğünde tutulur. Bu dosyalar, denetimi içeren klasörün bir alt `Themes` klasörü olan adlı bir klasörde olmalıdır. Aşağıdaki tabloda, kaynak sözlüğü dosyaları ve her bir dosyayla ilişkili tema listelenmektedir:

|Kaynak sözlüğü dosya adı|Windows teması|
|-----------------------------------|-------------------|
|`Classic.xaml`|Klasik Windows 9x/2000 Windows XP 'ye bakış|
|`Luna.NormalColor.xaml`|Windows XP 'de varsayılan mavi tema|
|`Luna.Homestead.xaml`|Windows XP 'de zeytin teması|
|`Luna.Metallic.xaml`|Windows XP 'de Gümüş teması|
|`Royale.NormalColor.xaml`|Windows XP Media Center Edition 'da varsayılan tema|
|`Aero.NormalColor.xaml`|Windows Vista 'da varsayılan tema|

Her tema için bir kaynak tanımlamanız gerekmez. Belirli bir tema için bir kaynak tanımlanmamışsa denetim, kaynağı denetler `Classic.xaml` . Kaynak, geçerli temaya veya ' de `Classic.xaml`karşılık gelen dosyada tanımlanmamışsa, Denetim adlı `generic.xaml`bir kaynak sözlüğü dosyasında olan genel kaynağı kullanır.  `generic.xaml` Dosya, temaya özgü kaynak sözlüğü dosyalarıyla aynı klasörde bulunur. `generic.xaml` , Belirli bir Windows temasına karşılık gelmese de, hala Tema düzeyi bir sözlüktür.

[NumericUpDown özel denetimi Tema ve UI Otomasyonu desteği örneği](https://go.microsoft.com/fwlink/?LinkID=160025) , `NumericUpDown` denetim için iki kaynak sözlükleri içerir: biri genel. xaml ve diğeri Luna. NormalColor. xaml içinde bulunur.  İki denetim şablonu arasındaki farkı görmek için uygulamayı çalıştırabilir ve Windows XP 'deki Gümüş tema arasında geçiş yapabilirsiniz. (Windows Vista çalıştırıyorsanız, Luna. NormalColor. xaml ' i Aero. NormalColor. xaml olarak yeniden adlandırabilir ve Windows Klasik ve Windows Vista için varsayılan tema gibi iki tema arasında geçiş yapabilirsiniz.)

Temayı özel kaynak sözlüğü <xref:System.Windows.Controls.ControlTemplate> dosyalarından birine yerleştirdiğinizde, denetiminiz için bir statik oluşturucu oluşturmanız ve aşağıdaki örnekte gösterildiği gibi, üzerinde <xref:System.Windows.DependencyProperty.OverrideMetadata%28System.Type%2CSystem.Windows.PropertyMetadata%29> <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>yöntemini çağırmanız gerekir.

[!code-csharp[CustomControlNumericUpDownOneProject#StaticConstructor](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/CSharp/NumericUpDown.cs#staticconstructor)]
[!code-vb[CustomControlNumericUpDownOneProject#StaticConstructor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/visualbasic/numericupdown.vb#staticconstructor)]

##### <a name="defining-and-referencing-keys-for-theme-resources"></a>Tema kaynakları için anahtar tanımlama ve başvuru

Öğe düzeyinde bir kaynak tanımladığınızda, anahtarı olarak bir dize atayabilir ve dize aracılığıyla kaynağa erişebilirsiniz. Tema düzeyinde bir kaynak tanımladığınızda, anahtar olarak bir <xref:System.Windows.ComponentResourceKey> olarak kullanmanız gerekir.  Aşağıdaki örnek, genel. xaml içinde bir kaynağı tanımlar.

[!code-xaml[ThemeResourcesControlLibrary#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/Themes/generic.xaml#5)]

Aşağıdaki örnek, anahtar <xref:System.Windows.ComponentResourceKey> olarak öğesini belirterek kaynağa başvurur.

[!code-xaml[ThemeResourcesControlLibrary#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/NumericUpDown.xaml#6)]

##### <a name="specifying-the-location-of-theme-resources"></a>Tema kaynaklarının konumunu belirtme

Bir denetimin kaynaklarını bulmak için barındırma uygulamasının, derlemenin denetime özgü kaynakları içerdiğini bilmeleri gerekir. Bunu, <xref:System.Windows.ThemeInfoAttribute> denetimini içeren derlemeye ekleyerek yapabilirsiniz. , <xref:System.Windows.ThemeInfoAttribute> Genel kaynakların <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> konumunu ve temaya özgü kaynakların konumunu belirten bir <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A> özelliği olan bir özelliğine sahiptir.

Aşağıdaki örnek, <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> ve <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A> özelliklerini, genel ve <xref:System.Windows.ResourceDictionaryLocation.SourceAssembly>temaya özgü kaynakların denetimle aynı derlemede olduğunu belirtmek için olarak ayarlar.

[!code-csharp[CustomControlNumericUpDown#ThemesSection](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/Properties/AssemblyInfo.cs#themessection)]
[!code-vb[CustomControlNumericUpDown#ThemesSection](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/my project/assemblyinfo.vb#themessection)]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio’da XAML tasarlama](/visualstudio/designers/designing-xaml-in-visual-studio)
- [WPF İçinde URI'leri Paketleme](../app-development/pack-uris-in-wpf.md)
- [Denetim Özelleştirme](control-customization.md)
