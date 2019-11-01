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
ms.openlocfilehash: fba640ab71459407bfc7a62908021e509346c363
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197356"
---
# <a name="control-authoring-overview"></a>Denetim Yazımına Genel Bakış

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] denetim modelinin genişletilebilirliği, yeni bir denetim oluşturma gereksinimini önemli ölçüde azaltır. Ancak bazı durumlarda, hala özel bir denetim oluşturmanız gerekebilir. Bu konuda, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]bir özel denetim ve farklı denetim yazma modellerini oluşturma gereksiniminizi en aza indirecek özellikler açıklanmaktadır. Bu konuda ayrıca nasıl yeni bir denetim oluşturacağınız gösterilmektedir.

<a name="when_to_write_a_new_control"></a>

## <a name="alternatives-to-writing-a-new-control"></a>Yeni denetim yazma alternatifleri

Tarihsel olarak, var olan bir denetimden özelleştirilmiş bir deneyim almak isterseniz, denetimin, arka plan rengi, kenarlık genişliği ve yazı tipi boyutu gibi standart özelliklerini değiştirmekle sınırlı olursunuz. Bir denetimin görünüşünü veya davranışını bu önceden tanımlanmış parametrelerin ötesinde uzatmak istiyorsanız, genellikle var olan bir denetimden devralarak ve denetimi çizmekten sorumlu yöntemi geçersiz kılarak yeni bir denetim oluşturmanız gerekir.  Yine de bir seçenek olsa da, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zengin içerik modeli, stilleri, şablonları ve Tetikleyicileri kullanarak var olan denetimleri özelleştirmenize olanak sağlar. Aşağıdaki listede, bu özelliklerin yeni bir denetim oluşturmak zorunda kalmadan özel ve tutarlı deneyimler oluşturmak için nasıl kullanılabileceği hakkında örnekler verilmektedir.

- **Zengin Içerik.** Birçok standart [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimi zengin içerikleri destekler. Örneğin, bir <xref:System.Windows.Controls.Button> içerik özelliği <xref:System.Object>türündedir, bu nedenle teorik olarak <xref:System.Windows.Controls.Button>her şey görüntülenebilir.  Bir düğmenin resim ve metin görüntülemesi için, bir <xref:System.Windows.Controls.StackPanel> bir görüntü ve <xref:System.Windows.Controls.TextBlock> ekleyebilir ve <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Controls.ContentControl.Content%2A> özelliğine atayabilirsiniz. Denetimler [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] görsel öğeleri ve rastgele verileri görüntüleyebilmesi nedeniyle, yeni bir denetim oluşturmanız veya var olan bir denetimi karmaşık görselleştirmeyi destekleyecek şekilde değiştirmeniz daha az olabilir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Button> ve diğer içerik modelleriyle ilgili içerik modeli hakkında daha fazla bilgi için bkz. [WPF Içerik modeli](wpf-content-model.md).

- **Stillerde.** <xref:System.Windows.Style>, bir denetimin özelliklerini temsil eden bir değer koleksiyonudur. Stilleri kullanarak, istenen denetim görünümü ve davranışı için yeni bir denetim yazmadan yeniden kullanılabilir bir temsili oluşturabilirsiniz. Örneğin, tüm <xref:System.Windows.Controls.TextBlock> denetimlerinizi kırmızı, Arial yazı tipine sahip olduğunu, 14 yazı tipi boyutuyla istediğinizi varsayalım. Kaynak olarak bir stil oluşturabilir ve uygun özellikleri uygun şekilde ayarlayabilirsiniz. Sonra uygulamanıza eklediğiniz her <xref:System.Windows.Controls.TextBlock> aynı görünüme sahip olur.

- **Veri şablonları.** <xref:System.Windows.DataTemplate>, verilerin denetimde nasıl görüntülendiğini özelleştirmenizi sağlar. Örneğin, bir <xref:System.Windows.DataTemplate> verilerin bir <xref:System.Windows.Controls.ListBox>nasıl görüntülendiğini belirtmek için kullanılabilir.  Buna bir örnek için bkz. [veri şablonu oluşturmaya genel bakış](../data/data-templating-overview.md).  Verilerin görünümünü özelleştirmenin yanı sıra, bir <xref:System.Windows.DataTemplate>, özel Uıof 'ta çok sayıda esneklik sağlayan UI öğeleri içerebilir.  Örneğin, bir <xref:System.Windows.DataTemplate>kullanarak her bir öğenin onay kutusu içerdiği bir <xref:System.Windows.Controls.ComboBox> oluşturabilirsiniz.

- **Denetim şablonları.** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] birçok denetim, denetimin yapısını ve görünümünü tanımlamak için bir <xref:System.Windows.Controls.ControlTemplate> kullanır ve bu da denetimin görünüşünü denetimin işlevselliğiyle ayırır. Bir denetimin görünümünü <xref:System.Windows.Controls.ControlTemplate>yeniden tanımlayarak büyük ölçüde değiştirebilirsiniz.  Örneğin, bir denetim ışığı gibi görünen bir denetim istediğinizi varsayalım. Bu denetimde basit bir kullanıcı arabirimi ve işlevselliği vardır.  Denetim üç dairedir, tek seferde yalnızca bir tane olabilir. Bazı yansımalardan sonra, bir <xref:System.Windows.Controls.RadioButton> her seferinde yalnızca bir tane seçilmekte olan işlevleri sunduğunu fark edebilirsiniz, ancak <xref:System.Windows.Controls.RadioButton> varsayılan görünümü bir durma ışığının ışıkları gibi hiçbir şey yapmaz.  <xref:System.Windows.Controls.RadioButton> görünümünü tanımlamak için bir denetim şablonu kullandığından, denetimin gereksinimlerine uyacak şekilde <xref:System.Windows.Controls.ControlTemplate> yeniden tanımlamak ve trafik durma alanınızı açmak için radyo düğmelerini kullanmak kolaydır.

  > [!NOTE]
  > <xref:System.Windows.Controls.RadioButton> bir <xref:System.Windows.DataTemplate>kullanabilse de, bu örnekte <xref:System.Windows.DataTemplate> yeterli değildir.  <xref:System.Windows.DataTemplate>, bir denetimin içeriğinin görünümünü tanımlar. <xref:System.Windows.Controls.RadioButton>söz konusu olduğunda içerik, <xref:System.Windows.Controls.RadioButton> seçili olup olmadığını gösteren dairenin sağında görüntülenir.  Trafik ışığı örneğinde radyo düğmesi yalnızca "hafif" bir daire olmalıdır. Durma ışığı için görünüm gereksinimi <xref:System.Windows.Controls.RadioButton>varsayılan görünüşünün dışında olduğundan, <xref:System.Windows.Controls.ControlTemplate>yeniden tanımlanması gerekir.  Genel olarak <xref:System.Windows.DataTemplate> bir denetimin içeriğini (veya verilerini) tanımlamak için kullanılır ve bir denetimin nasıl yapılandırıldığını tanımlamak için bir <xref:System.Windows.Controls.ControlTemplate> kullanılır.

- **Tetikleyiciler.** <xref:System.Windows.Trigger>, bir denetimin görünümünü ve davranışını yeni bir denetim oluşturmadan dinamik olarak değiştirmenize olanak sağlar. Örneğin, uygulamanızda birden çok <xref:System.Windows.Controls.ListBox> denetimine sahip olduğunuzu ve her bir <xref:System.Windows.Controls.ListBox> öğelerin seçildiklerinde kalın ve kırmızı olmasını istediğinizi varsayalım. İlk işlem, <xref:System.Windows.Controls.ListBox> devralan bir sınıf oluşturabilir ve seçilen öğenin görünümünü değiştirmek için <xref:System.Windows.Controls.Primitives.Selector.OnSelectionChanged%2A> metodunu geçersiz kılabilir, ancak seçilen öğenin görünümünü değiştiren bir <xref:System.Windows.Controls.ListBoxItem> stiline tetikleyici eklemek daha iyi bir yaklaşımdır. . Tetikleyici, özellik değerlerini değiştirmenize veya bir özelliğin değerine göre eylem yapmanıza olanak sağlar. Bir <xref:System.Windows.EventTrigger>, bir olay gerçekleştiğinde eylemler gerçekleştirmenizi sağlar.

Stiller, şablonlar ve Tetikleyiciler hakkında daha fazla bilgi için bkz. [Stil oluşturma ve şablon](styling-and-templating.md)oluşturma.

Genel olarak, denetiminiz var olan bir denetimin işlevselliğini yansıtır, ancak denetimin farklı görünmesini istiyorsanız, bu bölümde açıklanan yöntemlerden herhangi birini kullanıp kullanmayacağınızı, var olan denetimin görünümünü değiştirmek için göz önünde bulundurmanız gerekir.

<a name="models_for_control_authoring"></a>

## <a name="models-for-control-authoring"></a>Denetim yazma modelleri

Zengin içerik modeli, stiller, şablonlar ve Tetikleyiciler, yeni bir denetim oluşturmanız gereksinimini en aza indirir. Ancak, yeni bir denetim oluşturmanız gerekiyorsa, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]farklı denetim yazma modellerinin anlaşılması önemlidir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], her biri farklı bir özellik kümesi ve esneklik düzeyi sağlayan denetim oluşturmak için üç genel model sağlar. Üç modelin temel sınıfları <xref:System.Windows.Controls.UserControl>, <xref:System.Windows.Controls.Control>ve <xref:System.Windows.FrameworkElement>.

### <a name="deriving-from-usercontrol"></a>UserControl 'ten türetme

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir denetim oluşturmanın en kolay yolu <xref:System.Windows.Controls.UserControl>türetmektir. <xref:System.Windows.Controls.UserControl>devralan bir denetim oluşturduğunuzda, var olan bileşenleri <xref:System.Windows.Controls.UserControl>ekler, bileşenleri ve başvuru olay işleyicilerini [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Daha sonra adlandırılmış öğelere başvurabilir ve koddaki olay işleyicilerini tanımlayabilirsiniz. Bu geliştirme modeli, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]' de uygulama geliştirme için kullanılan modele çok benzer.

Doğru bir şekilde oluşturulıyorsa, bir <xref:System.Windows.Controls.UserControl> zengin içerik, stiller ve tetikleyicilerin avantajlarından faydalanabilirsiniz. Ancak, denetiminiz <xref:System.Windows.Controls.UserControl>devralırsa, denetiminizi kullanan kişiler, görünümünü özelleştirmek için bir <xref:System.Windows.DataTemplate> veya <xref:System.Windows.Controls.ControlTemplate> kullanamaz.  Şablonları destekleyen özel bir denetim oluşturmak için <xref:System.Windows.Controls.Control> sınıfından veya türetilmiş sınıflarından biri (<xref:System.Windows.Controls.UserControl>dışında) türetmeniz gerekir.

#### <a name="benefits-of-deriving-from-usercontrol"></a>UserControl 'dan Türetmenin avantajları

Aşağıdakilerin tümü uygulandıysanız <xref:System.Windows.Controls.UserControl> türetmeyi göz önünde bulundurun:

- Bir uygulamayı nasıl derlemenize benzer şekilde denetiminizi oluşturmak istersiniz.

- Denetiminiz yalnızca mevcut bileşenlerden oluşur.

- Karmaşık özelleştirmeyi desteklemek zorunda değilsiniz.

### <a name="deriving-from-control"></a>Denetimden türetme

<xref:System.Windows.Controls.Control> sınıfından türetmek, varolan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimlerinin çoğu tarafından kullanılan modeldir. <xref:System.Windows.Controls.Control> sınıfından devralan bir denetim oluşturduğunuzda, onun görünümünü şablonlar kullanarak tanımlarsınız. Bunu yaptığınızda, işlemsel mantığı görsel gösterimden ayırdığınızda. Ayrıca, Kullanıcı arabirimi ve mantığın olay yerine komutları ve bağlamaları kullanarak ve mümkün olduğunda <xref:System.Windows.Controls.ControlTemplate> öğeleri başvurmayı önleyerek emin olabilirsiniz.  Denetiminizin kullanıcı ARABIRIMI ve mantığı düzgün şekilde ayrıltıysa, denetiminizin bir kullanıcısı denetimin <xref:System.Windows.Controls.ControlTemplate> görünümünü özelleştirmek için yeniden tanımlayabilir. Özel bir <xref:System.Windows.Controls.Control> oluşturmak <xref:System.Windows.Controls.UserControl>oluşturmak kadar basit olmasa da, özel bir <xref:System.Windows.Controls.Control> en çok esnekliği sağlar.

#### <a name="benefits-of-deriving-from-control"></a>Denetimden Türetmenin avantajları

Aşağıdakilerden biri varsa <xref:System.Windows.Controls.UserControl> sınıfını kullanmak yerine <xref:System.Windows.Controls.Control> türetmeyi göz önünde bulundurun:

- Denetiminizin görünümünün <xref:System.Windows.Controls.ControlTemplate>aracılığıyla özelleştirilebilir olmasını istiyorsunuz.

- Denetiminizin farklı temaları desteklemesini istiyorsunuz.

### <a name="deriving-from-frameworkelement"></a>FrameworkElement 'ten türetme

<xref:System.Windows.Controls.UserControl> veya <xref:System.Windows.Controls.Control> türetilen denetimler varolan öğeleri oluşturmaya bağlıdır. Birçok senaryoda, <xref:System.Windows.FrameworkElement> devralan herhangi bir nesne <xref:System.Windows.Controls.ControlTemplate>olabileceğinden bu, kabul edilebilir bir çözümdür. Ancak, bir denetimin görünümü basit öğe kompozisyonunun işlevlerinden daha fazlasını gerektirdiğinde zaman vardır. Bu senaryolar için <xref:System.Windows.FrameworkElement> bir bileşeni temel alan doğru seçenektir.

<xref:System.Windows.FrameworkElement>tabanlı bileşenleri oluşturmak için iki standart yöntem vardır: doğrudan işleme ve özel öğe oluşturma. Doğrudan işleme, <xref:System.Windows.FrameworkElement> <xref:System.Windows.UIElement.OnRender%2A> yöntemini geçersiz kılmayı ve bileşen görsellerini açıkça tanımlayan <xref:System.Windows.Media.DrawingContext> işlemleri sağlamayı içerir. Bu, <xref:System.Windows.Controls.Image> ve <xref:System.Windows.Controls.Border>tarafından kullanılan yöntemdir. Özel öğe kompozisyonu, bileşeninizin görünümünü oluşturmak için <xref:System.Windows.Media.Visual> türündeki nesnelerin kullanımını içerir. Bir örnek için bkz. [DrawingVisual nesnelerini kullanma](../graphics-multimedia/using-drawingvisual-objects.md). <xref:System.Windows.Controls.Primitives.Track>, özel öğe kompozisyonu kullanan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir denetimin örneğidir. Aynı denetimde doğrudan işleme ve özel öğe oluşturmayı karıştırmak da mümkündür.

#### <a name="benefits-of-deriving-from-frameworkelement"></a>FrameworkElement 'ten Türetmenin avantajları

Aşağıdakilerden biri varsa <xref:System.Windows.FrameworkElement> türetmeyi göz önünde bulundurun:

- Denetimin görünümü üzerinde basit öğe kompozisyonu tarafından sağlananların ötesinde kesin denetim sahibi olmak istiyorsunuz.

- Kendi oluşturma mantığınızı tanımlayarak denetiminizin görünümünü tanımlamak istiyorsunuz.

- <xref:System.Windows.Controls.UserControl> ve <xref:System.Windows.Controls.Control>nelerin mümkün olduğunu belirten önemli yollarla mevcut öğeleri oluşturmak istersiniz.

<a name="control_authoring_basics"></a>

## <a name="control-authoring-basics"></a>Denetim Yazma Temelleri

Daha önce anlatıldığı gibi, en güçlü [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özelliklerinden biri, bir denetimin temel özelliklerini ayarlamanın, görünümünü ve davranışını değiştirmek, ancak yine de özel bir denetim oluşturmaya gerek yoktur. Stil, veri bağlama ve tetikleyici özellikleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellik sistemi ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olay sistemi tarafından mümkün hale getirilir. Aşağıdaki bölümlerde, özel denetim oluşturmak için kullandığınız modelden bağımsız olarak, özel denetiminizin kullanıcıları bu özellikleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]' de bulunan bir denetim gibi kullanabilmesi için, izlemeniz gereken bazı yöntemler açıklanır.

### <a name="use-dependency-properties"></a>Bağımlılık özelliklerini kullanma

Bir özellik bir bağımlılık özelliği olduğunda, şunları yapmak mümkündür:

- Bir stilde özelliği ayarlayın.

- Özelliği bir veri kaynağına bağlayın.

- Özelliğin değeri olarak dinamik bir kaynak kullanın.

- Özelliği canlandırın.

Denetiminizin bir özelliğinin bu işlevlerden herhangi birini desteklemesini istiyorsanız, bunu bir bağımlılık özelliği olarak uygulamalısınız. Aşağıdaki örnek aşağıdakileri yaparak `Value` adlı bir bağımlılık özelliğini tanımlar:

- `public` `static` `readonly` alanı olarak `ValueProperty` adlı bir <xref:System.Windows.DependencyProperty> tanımlayıcı tanımlayın.

- Aşağıdaki belirtmek için, özellik adını <xref:System.Windows.DependencyProperty.Register%2A?displayProperty=nameWithType>çağırarak özellik sistemiyle kaydedin:

  - Özelliğin adı.

  - Özelliğin türü.

  - Özelliğin sahibi olan tür.

  - Özelliğin meta verileri. Meta veriler, özelliğin varsayılan değerini, bir <xref:System.Windows.CoerceValueCallback> ve <xref:System.Windows.PropertyChangedCallback>içerir.

- Özelliğin `get` ve `set` erişimcileri uygulayarak bağımlılık özelliğini kaydetmek için kullanılan aynı ada sahip `Value`adlı bir CLR sarmalayıcı özelliği tanımlayın. `get` ve `set` erişimcilerinin sırasıyla <xref:System.Windows.DependencyObject.GetValue%2A> ve <xref:System.Windows.DependencyObject.SetValue%2A> çağırdığına unutmayın. İstemciler ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] erişimcileri atlayıp <xref:System.Windows.DependencyObject.GetValue%2A> ve <xref:System.Windows.DependencyObject.SetValue%2A> doğrudan arayabileceğinden, bağımlılık özellikleri erişimcilerinin ek mantık içermemesi önerilir. Örneğin, bir özellik bir veri kaynağına bağlandığında, özelliğin `set` erişimcisi çağrılmaz.  Get ve set erişimcilerine ek mantık eklemek yerine, <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.CoerceValueCallback>ve <xref:System.Windows.PropertyChangedCallback> temsilcilerini, değiştiğinde değere yanıt vermek veya denetlemek için kullanın.  Bu geri çağrılar hakkında daha fazla bilgi için bkz. [bağımlılık özelliği geri çağırmaları ve doğrulama](../advanced/dependency-property-callbacks-and-validation.md).

- `CoerceValue`adlı <xref:System.Windows.CoerceValueCallback> için bir yöntem tanımlayın. `CoerceValue`, `Value` `MinValue` daha büyük veya eşit ve `MaxValue`eşit veya daha küçük olmasını sağlar.

- `OnValueChanged`adlı <xref:System.Windows.PropertyChangedCallback>için bir yöntem tanımlayın. `OnValueChanged` bir <xref:System.Windows.RoutedPropertyChangedEventArgs%601> nesnesi oluşturur ve `ValueChanged` yönlendirilmiş olayı yükseltmek için hazırlar. Yönlendirilmiş olaylar, sonraki bölümde ele alınmıştır.

[!code-csharp[UserControlNumericUpDown#DependencyProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#dependencyproperty)]
[!code-vb[UserControlNumericUpDown#DependencyProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#dependencyproperty)]

Daha fazla bilgi için bkz. [Özel bağımlılık özellikleri](../advanced/custom-dependency-properties.md).

### <a name="use-routed-events"></a>Yönlendirilmiş olayları kullanma

Bağımlılık özellikleri, CLR özelliklerinin kavramını ek işlevlerle genişletmenin yanı da, yönlendirilmiş olaylar standart CLR olayları kavramını uzatır. Yeni bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimi oluşturduğunuzda, yönlendirilmiş bir olay aşağıdaki davranışı desteklediğinden, olayınızı yönlendirilmiş bir olay olarak uygulamak da iyi bir uygulamadır:

- Olaylar, birden fazla denetimin üst öğesi üzerinde işlenebilir. Bir olay bir kabarcıklanma olayıdır, öğe ağacındaki tek bir üst öğe olaya abone olabilir. Ardından, uygulama yazarları birden çok denetimin olayına yanıt vermek için bir işleyici kullanabilir. Örneğin, denetiminiz bir <xref:System.Windows.Controls.ListBox> her öğenin parçasıysa (bir <xref:System.Windows.DataTemplate>dahil edildiğinden), uygulama geliştiricisi denetim olayınızın olay işleyicisini <xref:System.Windows.Controls.ListBox>tanımlayabilir. Her bir denetim üzerinde olay gerçekleştiğinde olay işleyicisi çağırılır.

- Yönlendirilmiş olaylar, uygulama geliştiricilerinin bir stil içindeki bir olayın işleyicisini belirtmesini sağlayan bir <xref:System.Windows.EventSetter>kullanılabilir.

- Yönlendirilmiş olaylar, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]kullanılarak özellikleri hareketlendirmek için yararlı olan bir <xref:System.Windows.EventTrigger>kullanılabilir. Daha fazla bilgi için bkz. [animasyon genel bakış](../graphics-multimedia/animation-overview.md).

Aşağıdaki örnek aşağıdakileri yaparak bir yönlendirilmiş olayı tanımlar:

- `public` `static` `readonly` alanı olarak `ValueChangedEvent` adlı bir <xref:System.Windows.RoutedEvent> tanımlayıcı tanımlayın.

- <xref:System.Windows.EventManager.RegisterRoutedEvent%2A?displayProperty=nameWithType> yöntemini çağırarak yönlendirilmiş olayı kaydedin. Örnek, <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>çağırdığında aşağıdaki bilgileri belirtir:

  - Olayın adı `ValueChanged`.

  - Yönlendirme stratejisi, kaynak üzerindeki bir olay işleyicisinin (olayı oluşturan nesne) ilk olarak çağrıldığı ve ardından kaynağın üst öğelerinde olay işleyicilerinin, en yakın olay işleyicisinden başlayarak her ikisi de olarak çağrıldığı <xref:System.Windows.RoutingStrategy.Bubble>. üst öğe.

  - Olay işleyicisinin türü, <xref:System.Decimal> bir türle oluşturulan <xref:System.Windows.RoutedPropertyChangedEventHandler%601>.

  - Olayın sahip olduğu tür `NumericUpDown`.

- `ValueChanged` adlı bir genel olay bildirin ve olay erişimcisi bildirimlerini içerir. Örnek, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olay hizmetlerini kullanmak için `add` erişimci bildirimindeki <xref:System.Windows.UIElement.AddHandler%2A> çağırır ve `remove` erişimci bildiriminde <xref:System.Windows.UIElement.RemoveHandler%2A>.

- `ValueChanged` olayını oluşturan `OnValueChanged` adlı korumalı, sanal bir yöntem oluşturun.

[!code-csharp[UserControlNumericUpDown#RoutedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#routedevent)]
[!code-vb[UserControlNumericUpDown#RoutedEvent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#routedevent)]

Daha fazla bilgi için bkz. [yönlendirilmiş olaylara genel bakış](../advanced/routed-events-overview.md) ve [özel bir yönlendirilmiş olay oluşturma](../advanced/how-to-create-a-custom-routed-event.md).

### <a name="use-binding"></a>Bağlamayı kullan

Denetiminizin Kullanıcı arabirimini mantığa ayırmak için veri bağlamayı kullanmayı düşünün. <xref:System.Windows.Controls.ControlTemplate>kullanarak denetiminizin görünümünü tanımlarsanız bu özellikle önemlidir. Veri bağlamayı kullandığınızda, koddan Kullanıcı arabiriminin belirli bölümlerine başvurma gereksinimini ortadan kaldırabiliyor olabilirsiniz. Kod, <xref:System.Windows.Controls.ControlTemplate> ve <xref:System.Windows.Controls.ControlTemplate> değiştiği için, başvurulan öğenin yeni <xref:System.Windows.Controls.ControlTemplate>dahil olması gerektiği için <xref:System.Windows.Controls.ControlTemplate> olan öğelerin başvurmaması iyi bir fikirdir.

Aşağıdaki örnek, `NumericUpDown` denetiminin <xref:System.Windows.Controls.TextBlock> güncelleştirir, bu ada bir ad atayarak ve koddaki ada göre metin kutusuna başvuruda bulunuyor.

[!code-xaml[UserControlNumericUpDownSimple#UIRefMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml#uirefmarkup)]

[!code-csharp[UserControlNumericUpDownSimple#UIRefCode](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml.cs#uirefcode)]
[!code-vb[UserControlNumericUpDownSimple#UIRefCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDownSimple/VisualBasic/NumericUpDown.xaml.vb#uirefcode)]

Aşağıdaki örnek, aynı şeyi gerçekleştirmek için bağlamayı kullanır.

[!code-xaml[UserControlNumericUpDown#Binding](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml#binding)]

Veri bağlama hakkında daha fazla bilgi için bkz. [veri bağlamaya genel bakış](../data/data-binding-overview.md).

### <a name="design-for-designers"></a>Tasarımcılar için tasarım

[!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] özel WPF denetimlerine yönelik destek almak için (örneğin, Özellikler penceresi ile özellik düzenlemesi), bu yönergeleri izleyin.  [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]için geliştirme hakkında daha fazla bilgi için bkz. [Visual Studio 'DA xaml tasarlama](/visualstudio/xaml-tools/designing-xaml-in-visual-studio).

#### <a name="dependency-properties"></a>Bağımlılık Özellikleri

Daha önce açıklandığı gibi CLR `get` ve `set` erişimcileri uyguladığınızdan emin olun, "bağımlılık özelliklerini kullan" bölümünde. Tasarımcılar bir bağımlılık özelliğinin varlığını algılamak için sarmalayıcı kullanabilir, ancak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve denetimin istemcileri gibi, özelliği alırken veya ayarlarken erişimcileri çağırmak için gerekli değildir.

#### <a name="attached-properties"></a>Ekli Özellikler

Aşağıdaki yönergeleri kullanarak özel denetimlere Ekli Özellikler uygulamalısınız:

- `Property` yöntemi kullanılarak oluşturulan *PropertyName* <xref:System.Windows.DependencyProperty.RegisterAttached%2A> `readonly` <xref:System.Windows.DependencyProperty> `static` bir `public` olmalıdır. <xref:System.Windows.DependencyProperty.RegisterAttached%2A> geçirilen Özellik adı *PropertyName*ile eşleşmelidir.

- `Set`*PropertyName* ve `Get`*propertyname*ADıNDA bir `public` `static` CLR yöntemi uygulayın. Her iki yöntem de ilk bağımsız değişken olarak <xref:System.Windows.DependencyProperty> türetilmiş bir sınıfı kabul etmelidir. `Set`*PropertyName* yöntemi, türü özelliği için kayıtlı veri türüyle eşleşen bir bağımsız değişkeni de kabul eder. `Get`*PropertyName* yöntemi aynı türde bir değer döndürmelidir. `Set`*PropertyName* yöntemi eksikse, özellik salt okunurdur olarak işaretlenir.

- `Set` *PropertyName* ve `Get`*PropertyName* , sırasıyla hedef bağımlılık nesnesindeki <xref:System.Windows.DependencyObject.GetValue%2A> ve <xref:System.Windows.DependencyObject.SetValue%2A> yöntemlerine doğrudan yönlendirmelidir. Tasarımcılar, yöntem sarmalayıcısı aracılığıyla arayarak veya hedef bağımlılık nesnesine doğrudan çağrı yaparak ekli özelliğe erişebilir.

Ekli Özellikler hakkında daha fazla bilgi için bkz. [ekli özelliklere genel bakış](../advanced/attached-properties-overview.md).

### <a name="define-and-use-shared-resources"></a>Paylaşılan kaynakları tanımlama ve kullanma

Denetiminizi uygulamanız ile aynı derlemeye dahil edebilir veya birden çok uygulamada kullanılabilen ayrı bir derlemede denetiminizi paketleyebilir. Çoğu bölümde, bu konuda tartışılan bilgiler kullandığınız yöntemden bağımsız olarak geçerlidir.  Ancak, buna dikkat edilecek bir fark vardır.  Bir uygulamayı bir uygulama olarak aynı derlemeye yerleştirdiğinizde, App. xaml dosyasına genel kaynaklar ekleyebilirsiniz. Ancak yalnızca denetimleri içeren bir derlemenin kendisiyle ilişkili bir <xref:System.Windows.Application> nesnesi yoktur, bu nedenle bir App. xaml dosyası kullanılamaz.

Bir uygulama bir kaynağı ararken, üç düzeye aşağıdaki sırayla bakar:

1. Öğe düzeyi.

   Sistem, kaynağa başvuruda bulunan öğeyle başlar ve sonra mantıksal üst öğenin kaynaklarını arar ve bu nedenle kök öğeye ulaşılana kadar bu şekilde devam eder.

2. Uygulama düzeyi.

   <xref:System.Windows.Application> nesnesi tarafından tanımlanan kaynaklar.

3. Tema düzeyi.

   Tema düzeyi sözlükler, Temalar adlı bir alt klasörde depolanır.  Temalar klasöründeki dosyalar temalara karşılık gelir.  Örneğin, Aero. NormalColor. xaml, Luna. NormalColor. xaml, Royale. NormalColor. xaml, vb. olabilir.  Ayrıca, Generic. xaml adlı bir dosyaya da sahip olabilirsiniz.  Sistem Temalar düzeyinde bir kaynak ararken, önce temaya özel dosyada arama yapar ve ardından bunu genel. xaml içinde arar.

Denetiminiz uygulamadan ayrı bir derlemede olduğunda, genel kaynaklarınızı öğe düzeyinde veya tema düzeyinde koymanız gerekir. Her iki yöntem de avantajlarına sahiptir.

#### <a name="defining-resources-at-the-element-level"></a>Öğe düzeyinde kaynakları tanımlama

Özel bir kaynak sözlüğü oluşturarak ve denetimin kaynak sözlüğü ile birleştirerek, öğe düzeyinde paylaşılan kaynaklar tanımlayabilirsiniz.  Bu yöntemi kullandığınızda, kaynak dosyanıza istediğiniz her şeyi verebilir ve denetimleriniz ile aynı klasörde olabilir. Öğe düzeyindeki kaynaklar, anahtar olarak basit dizeler da kullanabilir. Aşağıdaki örnek Dictionary1. xaml adlı bir <xref:System.Windows.Media.LinearGradientBrush> kaynak dosyası oluşturur.

[!code-xaml[SharedResources#1](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/Dictionary1.xaml#1)]

Sözlüğünüzü tanımladıktan sonra denetimin kaynak sözlüğü ile birleştirmeniz gerekir.  Bunu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] veya kodu kullanarak yapabilirsiniz.

Aşağıdaki örnek, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]kullanarak bir kaynak sözlüğünü birleştirir.

[!code-xaml[SharedResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml#2)]

Bu yaklaşımın dezavantajı, her başvurduğunuzda bir <xref:System.Windows.ResourceDictionary> nesnesinin oluşturulmasıdır.  Örneğin, kitaplığınızda 10 özel denetiminiz varsa ve XAML kullanarak her denetim için paylaşılan kaynak sözlüklerini birleştirirseniz, 10 özdeş <xref:System.Windows.ResourceDictionary> nesnesi oluşturursunuz.  Bu, koddaki kaynakları birleştiren ve elde edilen <xref:System.Windows.ResourceDictionary>döndüren bir statik sınıf oluşturarak bunu önleyebilirsiniz.

Aşağıdaki örnek, paylaşılan bir <xref:System.Windows.ResourceDictionary>döndüren bir sınıf oluşturur.

[!code-csharp[SharedResources#3](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/SharedDictionaryManager.cs#3)]

Aşağıdaki örnek, `InitializeComponent`çağrısı yapmadan önce denetimin oluşturucusunda özel bir denetimin kaynaklarıyla paylaşılan kaynağı birleştirir.  `SharedDictionaryManager.SharedDictionary` statik bir özellik olduğundan, <xref:System.Windows.ResourceDictionary> yalnızca bir kez oluşturulur. Kaynak sözlüğü `InitializeComponent` çağrılmadan önce birleştirildiğinden, kaynaklar [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyasında denetim için kullanılabilir.

[!code-csharp[SharedResources#4](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml.cs#4)]

#### <a name="defining-resources-at-the-theme-level"></a>Tema düzeyinde kaynakları tanımlama

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], farklı Windows temaları için kaynaklar oluşturmanızı sağlar.  Denetim yazarı olarak, belirli bir temaya ait bir kaynağı tanımlayabilir ve hangi temanın kullanımda olduğuna bağlı olarak denetiminizin görünümünü değiştirebilirsiniz. Örneğin, Windows klasik teması 'ndaki bir <xref:System.Windows.Controls.Button> (Windows 2000 için varsayılan tema), <xref:System.Windows.Controls.Button> her tema için farklı bir <xref:System.Windows.Controls.ControlTemplate> kullandığından, Windows Luna teması içindeki bir <xref:System.Windows.Controls.Button> (Windows XP için varsayılan tema) farklıdır.

Bir temaya özgü kaynaklar, belirli bir dosya adına sahip bir kaynak sözlüğünde tutulur. Bu dosyalar, denetimi içeren klasörün bir alt klasörü olan `Themes` adlı bir klasörde olmalıdır. Aşağıdaki tabloda, kaynak sözlüğü dosyaları ve her bir dosyayla ilişkili tema listelenmektedir:

|Kaynak sözlüğü dosya adı|Windows teması|
|-----------------------------------|-------------------|
|`Classic.xaml`|Klasik Windows 9x/2000 Windows XP 'ye bakış|
|`Luna.NormalColor.xaml`|Windows XP 'de varsayılan mavi tema|
|`Luna.Homestead.xaml`|Windows XP 'de zeytin teması|
|`Luna.Metallic.xaml`|Windows XP 'de Gümüş teması|
|`Royale.NormalColor.xaml`|Windows XP Media Center Edition 'da varsayılan tema|
|`Aero.NormalColor.xaml`|Windows Vista 'da varsayılan tema|

Her tema için bir kaynak tanımlamanız gerekmez. Belirli bir tema için bir kaynak tanımlanmamışsa denetim, kaynak için `Classic.xaml` denetler. Kaynak, geçerli temaya veya `Classic.xaml`karşılık gelen dosyada tanımlanmamışsa, denetim, `generic.xaml`adlı bir kaynak sözlüğü dosyasında bulunan genel kaynağı kullanır.  `generic.xaml` dosyası, temaya özgü kaynak sözlüğü dosyalarıyla aynı klasörde bulunur. `generic.xaml`, belirli bir Windows temasına karşılık gelmese de, hala Tema düzeyi bir sözlüktür.

[C#](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp) Or [Visual Basic](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic) NumericUpDown özel denetimi Tema ve uı Otomasyonu desteği örneği `NumericUpDown` için iki kaynak sözlük içerir: biri Generic. xaml Içinde ve diğeri de Luna. NormalColor. xaml ' de bulunur. 

Temaya özgü kaynak sözlüğü dosyalarından herhangi birine bir <xref:System.Windows.Controls.ControlTemplate> yerleştirdiğinizde, denetiminiz için bir statik oluşturucu oluşturmanız ve aşağıdaki örnekte gösterildiği gibi <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A><xref:System.Windows.DependencyProperty.OverrideMetadata%28System.Type%2CSystem.Windows.PropertyMetadata%29> yöntemini çağırmanız gerekir.

[!code-csharp[CustomControlNumericUpDownOneProject#StaticConstructor](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/CSharp/NumericUpDown.cs#staticconstructor)]
[!code-vb[CustomControlNumericUpDownOneProject#StaticConstructor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/visualbasic/numericupdown.vb#staticconstructor)]

##### <a name="defining-and-referencing-keys-for-theme-resources"></a>Tema kaynakları için anahtar tanımlama ve başvuru

Öğe düzeyinde bir kaynak tanımladığınızda, anahtarı olarak bir dize atayabilir ve dize aracılığıyla kaynağa erişebilirsiniz. Tema düzeyinde bir kaynak tanımladığınızda, anahtar olarak bir <xref:System.Windows.ComponentResourceKey> kullanmanız gerekir.  Aşağıdaki örnek, genel. xaml içinde bir kaynağı tanımlar.

[!code-xaml[ThemeResourcesControlLibrary#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/Themes/generic.xaml#5)]

Aşağıdaki örnek, <xref:System.Windows.ComponentResourceKey> anahtarı olarak belirterek kaynağa başvurur.

[!code-xaml[ThemeResourcesControlLibrary#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/NumericUpDown.xaml#6)]

##### <a name="specifying-the-location-of-theme-resources"></a>Tema kaynaklarının konumunu belirtme

Bir denetimin kaynaklarını bulmak için barındırma uygulamasının, derlemenin denetime özgü kaynakları içerdiğini bilmeleri gerekir. Bunu, denetimi içeren derlemeye <xref:System.Windows.ThemeInfoAttribute> ekleyerek yapabilirsiniz. <xref:System.Windows.ThemeInfoAttribute>, genel kaynakların konumunu belirten bir <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> özelliğine ve temaya özgü kaynakların konumunu belirten bir <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A> özelliğine sahiptir.

Aşağıdaki örnek, genel ve temaya özgü kaynakların denetimle aynı derlemede olduğunu belirtmek için <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> ve <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A> özelliklerini <xref:System.Windows.ResourceDictionaryLocation.SourceAssembly>olarak ayarlar.

[!code-csharp[CustomControlNumericUpDown#ThemesSection](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/Properties/AssemblyInfo.cs#themessection)]
[!code-vb[CustomControlNumericUpDown#ThemesSection](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/my project/assemblyinfo.vb#themessection)]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio’da XAML tasarlama](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [WPF İçinde URI'leri Paketleme](../app-development/pack-uris-in-wpf.md)
- [Denetim Özelleştirme](control-customization.md)
