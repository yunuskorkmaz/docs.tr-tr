---
title: Denetim Yazımına Genel Bakış
description: Windows Presentation Foundation denetimlerinin genişletilebilirliği, özel denetimler oluşturma gereksinimini en aza indirir. Gerekirse yeni bir denetim oluşturmayı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], authoring overview
- authoring overview for controls [WPF]
ms.assetid: 3d864748-cff0-4e63-9b23-d8e5a635b28f
ms.openlocfilehash: 600eb193613846d7eeeb626a6dfd317d2592f809
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166341"
---
# <a name="control-authoring-overview"></a>Denetim yazma genel bakış

Denetim modelinin genişletilebilirliği, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Yeni bir denetim oluşturma gereksinimini önemli ölçüde azaltır. Ancak bazı durumlarda, hala özel bir denetim oluşturmanız gerekebilir. Bu konuda, içinde özel bir denetim ve farklı denetim yazma modelleri oluşturma gereksiniminizi en aza indirecek özellikler açıklanmaktadır [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] . Bu konuda ayrıca nasıl yeni bir denetim oluşturacağınız gösterilmektedir.

<a name="when_to_write_a_new_control"></a>

## <a name="alternatives-to-writing-a-new-control"></a>Yeni denetim yazma alternatifleri

Tarihsel olarak, var olan bir denetimden özelleştirilmiş bir deneyim almak isterseniz, denetimin, arka plan rengi, kenarlık genişliği ve yazı tipi boyutu gibi standart özelliklerini değiştirmekle sınırlı olursunuz. Bir denetimin görünüşünü veya davranışını bu önceden tanımlanmış parametrelerin ötesinde uzatmak istiyorsanız, genellikle var olan bir denetimden devralarak ve denetimi çizmekten sorumlu yöntemi geçersiz kılarak yeni bir denetim oluşturmanız gerekir.  Yine de bir seçenek olsa da, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] var olan denetimleri zengin içerik modeli, stiller, şablonlar ve Tetikleyiciler kullanarak özelleştirmenize olanak sağlar. Aşağıdaki listede, bu özelliklerin yeni bir denetim oluşturmak zorunda kalmadan özel ve tutarlı deneyimler oluşturmak için nasıl kullanılabileceği hakkında örnekler verilmektedir.

- **Zengin Içerik.** Standart [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimlerin birçoğu zengin içerikleri destekler. Örneğin, öğesinin içerik özelliği <xref:System.Windows.Controls.Button> türündedir <xref:System.Object> , bu nedenle teorik olarak her şey bir üzerinde görüntülenebilir <xref:System.Windows.Controls.Button> .  Bir düğmenin bir görüntü ve metin görüntülemesi için, bir görüntü ve a ekleyebilir <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.StackPanel> ve <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Controls.ContentControl.Content%2A> özelliğini özelliğine atayabilirsiniz. Denetimler [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] görsel öğeleri ve rastgele verileri görüntüleyeceğinden, yeni bir denetim oluşturmanız veya var olan bir denetimi karmaşık görselleştirmeyi destekleyecek şekilde değiştirmeniz daha az olabilir. ' Deki içerik modeli <xref:System.Windows.Controls.Button> ve içindeki diğer içerik modelleri hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bkz. [WPF içerik modeli](wpf-content-model.md).

- **Stillerde.** <xref:System.Windows.Style>, Bir denetimin özelliklerini temsil eden bir değerler koleksiyonudur. Stilleri kullanarak, istenen denetim görünümü ve davranışı için yeni bir denetim yazmadan yeniden kullanılabilir bir temsili oluşturabilirsiniz. Örneğin, tüm <xref:System.Windows.Controls.TextBlock> denetimlerinizin, 14 yazı tipi boyutuyla kırmızı, Arial yazı tipine sahip olmasını istediğinizi varsayalım. Kaynak olarak bir stil oluşturabilir ve uygun özellikleri uygun şekilde ayarlayabilirsiniz. Sonra <xref:System.Windows.Controls.TextBlock> uygulamanıza eklediğiniz her bir görünüm aynı olur.

- **Veri şablonları.** Bir <xref:System.Windows.DataTemplate> denetimde verilerin nasıl görüntülendiğini özelleştirmenizi sağlar. Örneğin, bir, ' <xref:System.Windows.DataTemplate> de verilerin nasıl görüntüleneceğini belirtmek için kullanılabilir <xref:System.Windows.Controls.ListBox> .  Buna bir örnek için bkz. [veri şablonu oluşturmaya genel bakış](../data/data-templating-overview.md).  Verilerin görünümünü özelleştirmenin yanı sıra, <xref:System.Windows.DataTemplate> özel uıof 'ta çok sayıda esneklik sağlayan UI öğeleri içerebilir.  Örneğin, bir kullanarak <xref:System.Windows.DataTemplate> , <xref:System.Windows.Controls.ComboBox> her bir öğenin bir onay kutusu içerdiği bir oluşturabilirsiniz.

- **Denetim şablonları.** İçindeki pek çok denetim, denetimin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] işlevselliğiyle denetimin bir denetimin <xref:System.Windows.Controls.ControlTemplate> görünüşünü ayıran denetimin yapısını ve görünümünü tanımlamak için kullanır. Denetimin görünümünü büyük ölçüde tekrar tanımlayarak değiştirebilirsiniz <xref:System.Windows.Controls.ControlTemplate> .  Örneğin, bir denetim ışığı gibi görünen bir denetim istediğinizi varsayalım. Bu denetimde basit bir kullanıcı arabirimi ve işlevselliği vardır.  Denetim üç dairedir, tek seferde yalnızca bir tane olabilir. Bazı yansımalardan sonra, bir <xref:System.Windows.Controls.RadioButton> kerede yalnızca bir tane seçilmekte olan işlevi sunduğunu fark edebilirsiniz, ancak varsayılan görünümü bir <xref:System.Windows.Controls.RadioButton> trafik ışığı üzerindeki ışıklar gibi görünmüyor.  , <xref:System.Windows.Controls.RadioButton> Görünümünü tanımlamak için bir denetim şablonu kullandığından, <xref:System.Windows.Controls.ControlTemplate> denetimin gereksinimlerine uyacak şekilde öğesini yeniden tanımlamak ve trafik durma alanınızı açmak için radyo düğmelerini kullanmak kolaydır.

  > [!NOTE]
  > , Bir <xref:System.Windows.Controls.RadioButton> kullanabilir ancak <xref:System.Windows.DataTemplate> , <xref:System.Windows.DataTemplate> Bu örnekte yeterli değildir.  , <xref:System.Windows.DataTemplate> Bir denetimin içeriğinin görünümünü tanımlar. Bir durumunda <xref:System.Windows.Controls.RadioButton> , içerik seçili olup olmadığını gösteren dairenin sağında görüntülenir <xref:System.Windows.Controls.RadioButton> .  Trafik ışığı örneğinde radyo düğmesi yalnızca "hafif" bir daire olmalıdır. Durma ışığı için görünüm gereksinimi, ' nin varsayılan görünümüyle farklı olduğundan, <xref:System.Windows.Controls.RadioButton> öğesini yeniden tanımlamak gerekir <xref:System.Windows.Controls.ControlTemplate> .  Genel a <xref:System.Windows.DataTemplate> , bir denetimin içeriğini (veya verilerini) tanımlamak için kullanılır ve bir <xref:System.Windows.Controls.ControlTemplate> denetimin nasıl yapılandırıldığını tanımlamak için kullanılır.

- **Tetikleyiciler.** <xref:System.Windows.Trigger>, Bir denetimin görünümünü ve davranışını yeni bir denetim oluşturmadan dinamik olarak değiştirmenize olanak sağlar. Örneğin, uygulamanızda birden çok <xref:System.Windows.Controls.ListBox> denetiminizin olduğunu ve her birinin <xref:System.Windows.Controls.ListBox> seçildikleri zaman kalın ve kırmızı olmasını istediğinizi varsayalım. İlk işlem, ' den devralan bir sınıf oluşturmak <xref:System.Windows.Controls.ListBox> ve <xref:System.Windows.Controls.Primitives.Selector.OnSelectionChanged%2A> Seçilen öğenin görünümünü değiştirmek için yöntemini geçersiz kılmak, ancak daha iyi bir yaklaşım, <xref:System.Windows.Controls.ListBoxItem> Seçilen öğenin görünümünü değiştiren bir öğesinin stiline bir tetikleyici eklemektir. Tetikleyici, özellik değerlerini değiştirmenize veya bir özelliğin değerine göre eylem yapmanıza olanak sağlar. Bir <xref:System.Windows.EventTrigger> olay gerçekleştiğinde eylemler gerçekleştirmenizi sağlar.

Stiller, şablonlar ve Tetikleyiciler hakkında daha fazla bilgi için bkz. [Stil oluşturma ve şablon](../../../desktop-wpf/fundamentals/styles-templates-overview.md)oluşturma.

Genel olarak, denetiminiz var olan bir denetimin işlevselliğini yansıtır, ancak denetimin farklı görünmesini istiyorsanız, bu bölümde açıklanan yöntemlerden herhangi birini kullanıp kullanmayacağınızı, var olan denetimin görünümünü değiştirmek için göz önünde bulundurmanız gerekir.

<a name="models_for_control_authoring"></a>

## <a name="models-for-control-authoring"></a>Denetim yazma modelleri

Zengin içerik modeli, stiller, şablonlar ve Tetikleyiciler, yeni bir denetim oluşturmanız gereksinimini en aza indirir. Ancak, yeni bir denetim oluşturmanız gerekiyorsa, içinde farklı denetim yazma modellerinin anlaşılması önemlidir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], her biri farklı bir özellik kümesi ve esneklik düzeyi sağlayan denetim oluşturmak için üç genel model sağlar. Üç modelin temel sınıfları, ve ' dir <xref:System.Windows.Controls.UserControl> <xref:System.Windows.Controls.Control> <xref:System.Windows.FrameworkElement> .

### <a name="deriving-from-usercontrol"></a>UserControl 'ten türetme

' De bir denetim oluşturmanın en kolay yolu, ' [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] den türetmektir <xref:System.Windows.Controls.UserControl> . Öğesinden devralan bir denetim oluşturduğunuzda, <xref:System.Windows.Controls.UserControl> var olan bileşenleri <xref:System.Windows.Controls.UserControl> içine ekleyin, bileşenleri adlandırın ve içindeki olay işleyicilerini başvuru yapın [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] . Daha sonra adlandırılmış öğelere başvurabilir ve koddaki olay işleyicilerini tanımlayabilirsiniz. Bu geliştirme modeli, içinde uygulama geliştirme için kullanılan modele çok benzer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] .

Doğru şekilde oluşturulıyorsa, <xref:System.Windows.Controls.UserControl> zengin içerik, stiller ve tetikleyicilerin avantajlarından faydalanabilirsiniz. Ancak, denetiminiz öğesinden devralırsa <xref:System.Windows.Controls.UserControl> , denetiminizi kullanan kişiler <xref:System.Windows.DataTemplate> <xref:System.Windows.Controls.ControlTemplate> görünümünü özelleştirmek için bir veya kullanamaz.  <xref:System.Windows.Controls.Control> <xref:System.Windows.Controls.UserControl> Şablonları destekleyen özel bir denetim oluşturmak için sınıfından veya türetilmiş sınıflarından birinden (dışında) türetmeniz gerekir.

#### <a name="benefits-of-deriving-from-usercontrol"></a>UserControl 'dan Türetmenin avantajları

Aşağıdakilerin tümü uygulandıysanız ' dan türetmeyi göz önünde bulundurun <xref:System.Windows.Controls.UserControl> :

- Bir uygulamayı nasıl derlemenize benzer şekilde denetiminizi oluşturmak istersiniz.

- Denetiminiz yalnızca mevcut bileşenlerden oluşur.

- Karmaşık özelleştirmeyi desteklemek zorunda değilsiniz.

### <a name="deriving-from-control"></a>Denetimden türetme

Sınıfından türetmek, <xref:System.Windows.Controls.Control> varolan denetimlerin çoğu tarafından kullanılan modeldir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . Sınıfından devralan bir denetim oluşturduğunuzda <xref:System.Windows.Controls.Control> , görünümünü şablonlar kullanarak tanımlarsınız. Bunu yaptığınızda, işlemsel mantığı görsel gösterimden ayırdığınızda. Ayrıca, olaylar yerine komutları ve bağlamaları kullanarak ve mümkün olan her durumda öğelere başvurmaktan kaçınarak UI ve mantığın ayrılmasıyla emin olabilirsiniz <xref:System.Windows.Controls.ControlTemplate> .  Denetiminizin kullanıcı ARABIRIMI ve mantığı düzgün şekilde ayrıldıysanız, denetiminizin bir kullanıcısı, <xref:System.Windows.Controls.ControlTemplate> görünümünü özelleştirmek için denetimi yeniden tanımlayabilir. Özel derleme, oluşturma <xref:System.Windows.Controls.Control> kadar basit olmasa da <xref:System.Windows.Controls.UserControl> , özel bir <xref:System.Windows.Controls.Control> en esnekliği sağlar.

#### <a name="benefits-of-deriving-from-control"></a>Denetimden Türetmenin avantajları

<xref:System.Windows.Controls.Control>Aşağıdakilerden birini uyguladığınızda sınıfını kullanmak yerine ' den türetmeyi göz önünde bulundurun <xref:System.Windows.Controls.UserControl> :

- Denetiminizin görünümünün aracılığıyla özelleştirilebilir olmasını istiyorsunuz <xref:System.Windows.Controls.ControlTemplate> .

- Denetiminizin farklı temaları desteklemesini istiyorsunuz.

### <a name="deriving-from-frameworkelement"></a>FrameworkElement 'ten türetme

<xref:System.Windows.Controls.UserControl>Var olan öğeleri oluşturma işleminden türetilen veya bunları temel alan denetimler <xref:System.Windows.Controls.Control> . Birçok senaryoda, ' den devralan herhangi bir nesne bir içinde olabileceğinden, bu, kabul edilebilir bir çözümdür <xref:System.Windows.FrameworkElement> <xref:System.Windows.Controls.ControlTemplate> . Ancak, bir denetimin görünümü basit öğe kompozisyonunun işlevlerinden daha fazlasını gerektirdiğinde zaman vardır. Bu senaryolar için, bir bileşeni temel alan <xref:System.Windows.FrameworkElement> doğru tercih edilir.

Yapı tabanlı bileşenler için iki standart yöntem vardır <xref:System.Windows.FrameworkElement> : doğrudan işleme ve özel öğe oluşturma. Doğrudan işleme yöntemi geçersiz kılmayı <xref:System.Windows.UIElement.OnRender%2A> <xref:System.Windows.FrameworkElement> ve <xref:System.Windows.Media.DrawingContext> bileşen görsellerini açıkça tanımlayan işlemleri sağlamayı içerir. Bu, ve tarafından kullanılan yöntemidir <xref:System.Windows.Controls.Image> <xref:System.Windows.Controls.Border> . Özel öğe kompozisyonu <xref:System.Windows.Media.Visual> , bileşeninizin görünümünü oluşturmak için türündeki nesnelerin kullanımını içerir. Bir örnek için bkz. [DrawingVisual nesnelerini kullanma](../graphics-multimedia/using-drawingvisual-objects.md). <xref:System.Windows.Controls.Primitives.Track>, içinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özel öğe kompozisyonu kullanan bir denetimin örneğidir. Aynı denetimde doğrudan işleme ve özel öğe oluşturmayı karıştırmak da mümkündür.

#### <a name="benefits-of-deriving-from-frameworkelement"></a>FrameworkElement 'ten Türetmenin avantajları

Aşağıdakilerden birini uyguladığınızda ' den türetmeyi göz önünde bulundurun <xref:System.Windows.FrameworkElement> :

- Denetimin görünümü üzerinde basit öğe kompozisyonu tarafından sağlananların ötesinde kesin denetim sahibi olmak istiyorsunuz.

- Kendi oluşturma mantığınızı tanımlayarak denetiminizin görünümünü tanımlamak istiyorsunuz.

- Ve ile mümkün olan unsurların ötesine geçen önemli yollarla mevcut öğeleri oluşturmak istersiniz <xref:System.Windows.Controls.UserControl> <xref:System.Windows.Controls.Control> .

<a name="control_authoring_basics"></a>

## <a name="control-authoring-basics"></a>Denetim Yazma Temelleri

Daha önce anlatıldığı gibi, en güçlü özelliklerinden biri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de bir denetimin temel özelliklerinin, görünümünü ve davranışını değiştirmek, ancak yine de özel bir denetim oluşturmaya gerek yoktur. Stil, veri bağlama ve tetikleyici özellikleri, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellik sistemi ve olay sistemi tarafından mümkün hale getirilir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . Aşağıdaki bölümlerde, özel denetim oluşturmak için kullandığınız model ne olursa olsun, özel denetim kullanıcılarının, bu özellikleri ' de bulunan bir denetim için yaptıkları gibi kullanabilmesi için, izlemeniz gereken bazı yöntemler açıklanır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] .

### <a name="use-dependency-properties"></a>Bağımlılık özelliklerini kullanma

Bir özellik bir bağımlılık özelliği olduğunda, şunları yapmak mümkündür:

- Bir stilde özelliği ayarlayın.

- Özelliği bir veri kaynağına bağlayın.

- Özelliğin değeri olarak dinamik bir kaynak kullanın.

- Özelliği canlandırın.

Denetiminizin bir özelliğinin bu işlevlerden herhangi birini desteklemesini istiyorsanız, bunu bir bağımlılık özelliği olarak uygulamalısınız. Aşağıdaki örnek, aşağıdaki işlemleri gerçekleştirerek adlı bir bağımlılık özelliğini tanımlar `Value` :

- <xref:System.Windows.DependencyProperty>Alan olarak adlandırılan bir tanımlayıcı tanımlayın `ValueProperty` `public` `static` `readonly` .

- Aşağıdaki belirtmek için, özellik adını çağırarak özellik sistemiyle kaydedin <xref:System.Windows.DependencyProperty.Register%2A?displayProperty=nameWithType> :

  - Özelliğin adı.

  - Özelliğin türü.

  - Özelliğin sahibi olan tür.

  - Özelliğin meta verileri. Meta veriler, özelliğinin varsayılan değerini, a ve, içerir <xref:System.Windows.CoerceValueCallback> <xref:System.Windows.PropertyChangedCallback> .

- `Value`Özellik ve erişimcileri uygulayarak bağımlılık özelliğini kaydetmek için kullanılan aynı ada sahip adlı BIR clr sarmalayıcı özelliği tanımlayın `get` `set` . `get`Ve `set` erişimcilerinin yalnızca ve sırasıyla çağrı olduğunu unutmayın <xref:System.Windows.DependencyObject.GetValue%2A> <xref:System.Windows.DependencyObject.SetValue%2A> . Bağımlılık özellikleri erişimcilerinin, istemciler için ek mantık içermemesi ve bu nedenle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] erişimcileri ve çağrı ve doğrudan çağırabileceğinden bu önerilir <xref:System.Windows.DependencyObject.GetValue%2A> <xref:System.Windows.DependencyObject.SetValue%2A> . Örneğin, bir özellik bir veri kaynağına bağlandığında, özelliğin `set` erişimcisi çağrılmaz.  Get ve set erişimcilerine ek mantık eklemek yerine,,,, ve ' ı, <xref:System.Windows.ValidateValueCallback> <xref:System.Windows.CoerceValueCallback> <xref:System.Windows.PropertyChangedCallback> değiştiğinde değerini yanıtlamak veya denetlemek için kullanın.  Bu geri çağrılar hakkında daha fazla bilgi için bkz. [bağımlılık özelliği geri çağırmaları ve doğrulama](../advanced/dependency-property-callbacks-and-validation.md).

- Adlandırılmış için bir yöntem tanımlayın <xref:System.Windows.CoerceValueCallback> `CoerceValue` . `CoerceValue`Bunun daha `Value` büyük veya eşit ya da `MinValue` daha küçük veya eşit olmasını sağlar `MaxValue` .

- Adlı için bir yöntem tanımlayın <xref:System.Windows.PropertyChangedCallback> `OnValueChanged` . `OnValueChanged`bir <xref:System.Windows.RoutedPropertyChangedEventArgs%601> nesnesi oluşturur ve yönlendirilmiş olayı yükseltmek için hazırlar `ValueChanged` . Yönlendirilmiş olaylar, sonraki bölümde ele alınmıştır.

[!code-csharp[UserControlNumericUpDown#DependencyProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#dependencyproperty)]
[!code-vb[UserControlNumericUpDown#DependencyProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#dependencyproperty)]

Daha fazla bilgi için bkz. [Özel bağımlılık özellikleri](../advanced/custom-dependency-properties.md).

### <a name="use-routed-events"></a>Yönlendirilmiş olayları kullanma

Bağımlılık özellikleri, CLR özelliklerinin kavramını ek işlevlerle genişletmenin yanı da, yönlendirilmiş olaylar standart CLR olayları kavramını uzatır. Yeni bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetim oluşturduğunuzda, yönlendirilmiş bir olay aşağıdaki davranışı desteklediğinden, olayınızı yönlendirilmiş bir olay olarak uygulamak da iyi bir uygulamadır:

- Olaylar, birden fazla denetimin üst öğesi üzerinde işlenebilir. Bir olay bir kabarcıklanma olayıdır, öğe ağacındaki tek bir üst öğe olaya abone olabilir. Ardından, uygulama yazarları birden çok denetimin olayına yanıt vermek için bir işleyici kullanabilir. Örneğin, denetiminiz bir içindeki her öğenin parçasıysa <xref:System.Windows.Controls.ListBox> (bir ' a dahil edildiği için <xref:System.Windows.DataTemplate> ), uygulama geliştiricisi, denetim olayınızın ' de olay işleyicisini tanımlayabilir <xref:System.Windows.Controls.ListBox> . Her bir denetim üzerinde olay gerçekleştiğinde olay işleyicisi çağırılır.

- Yönlendirilmiş olaylar <xref:System.Windows.EventSetter> , uygulama geliştiricilerinin bir stil içindeki bir olayın işleyicisini belirtmesini sağlayan bir ' de kullanılabilir.

- Yönlendirilmiş olaylar <xref:System.Windows.EventTrigger> , kullanarak özellikleri hareketlendirmek için yararlı olan bir içinde kullanılabilir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] . Daha fazla bilgi için bkz. [animasyon genel bakış](../graphics-multimedia/animation-overview.md).

Aşağıdaki örnek aşağıdakileri yaparak bir yönlendirilmiş olayı tanımlar:

- <xref:System.Windows.RoutedEvent>Alan olarak adlandırılan bir tanımlayıcı tanımlayın `ValueChangedEvent` `public` `static` `readonly` .

- Yöntemini çağırarak yönlendirilmiş olayı kaydedin <xref:System.Windows.EventManager.RegisterRoutedEvent%2A?displayProperty=nameWithType> . Örnek, çağrı sırasında aşağıdaki bilgileri belirtir <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> :

  - Olayın adı `ValueChanged` .

  - Yönlendirme stratejisi, <xref:System.Windows.RoutingStrategy.Bubble> kaynak üzerindeki bir olay işleyicisinin (olayı oluşturan nesne) ilk olarak çağrıldığı ve ardından kaynağın üst öğelerinde olay işleyicilerinin, en yakın üst öğedeki olay işleyicisiyle başlayarak birbirini izleyen şekilde çağrıldığı anlamına gelir.

  - Olay işleyicisinin türü <xref:System.Windows.RoutedPropertyChangedEventHandler%601> , bir tür ile oluşturulur <xref:System.Decimal> .

  - Olayın sahibi olan türü `NumericUpDown` .

- Adlı bir genel olay bildirin `ValueChanged` ve olay erişimcisi bildirimlerini içerir. Örnek, <xref:System.Windows.UIElement.AddHandler%2A> `add` <xref:System.Windows.UIElement.RemoveHandler%2A> `remove` olay hizmetlerini kullanmak için erişimci bildiriminde ve erişimci bildiriminde çağırır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] .

- Olayı oluşturan adlı korumalı, sanal bir yöntem oluşturun `OnValueChanged` `ValueChanged` .

[!code-csharp[UserControlNumericUpDown#RoutedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#routedevent)]
[!code-vb[UserControlNumericUpDown#RoutedEvent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#routedevent)]

Daha fazla bilgi için bkz. [yönlendirilmiş olaylara genel bakış](../advanced/routed-events-overview.md) ve [özel bir yönlendirilmiş olay oluşturma](../advanced/how-to-create-a-custom-routed-event.md).

### <a name="use-binding"></a>Bağlamayı kullan

Denetiminizin Kullanıcı arabirimini mantığa ayırmak için veri bağlamayı kullanmayı düşünün. Bu, bir kullanarak denetiminizin görünümünü tanımlarsanız özellikle önemlidir <xref:System.Windows.Controls.ControlTemplate> . Veri bağlamayı kullandığınızda, koddan Kullanıcı arabiriminin belirli bölümlerine başvurma gereksinimini ortadan kaldırabiliyor olabilirsiniz. Kod içinde olan <xref:System.Windows.Controls.ControlTemplate> öğelerin başvurduğu <xref:System.Windows.Controls.ControlTemplate> ve <xref:System.Windows.Controls.ControlTemplate> değiştirildiği, başvurulan öğenin yeni içine dahil olması gerektiği için, içinde bulunan öğelerin başvurmaması iyi bir fikirdir <xref:System.Windows.Controls.ControlTemplate> .

Aşağıdaki örnek, <xref:System.Windows.Controls.TextBlock> `NumericUpDown` denetimin ' de bir ad atamasını ve koddaki ada göre TextBox 'a başvurmayı sağlar.

[!code-xaml[UserControlNumericUpDownSimple#UIRefMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml#uirefmarkup)]

[!code-csharp[UserControlNumericUpDownSimple#UIRefCode](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml.cs#uirefcode)]
[!code-vb[UserControlNumericUpDownSimple#UIRefCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDownSimple/VisualBasic/NumericUpDown.xaml.vb#uirefcode)]

Aşağıdaki örnek, aynı şeyi gerçekleştirmek için bağlamayı kullanır.

[!code-xaml[UserControlNumericUpDown#Binding](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml#binding)]

Veri bağlama hakkında daha fazla bilgi için bkz. [veri bağlamaya genel bakış](../../../desktop-wpf/data/data-binding-overview.md).

### <a name="design-for-designers"></a>Tasarımcılar için tasarım

Visual Studio için WPF Tasarımcısında özel WPF denetimleri için destek almak üzere (örneğin, Özellikler penceresi ile özellik düzenlemesi), bu yönergeleri izleyin.  WPF Tasarımcısı için geliştirme hakkında daha fazla bilgi için bkz. [Visual Studio 'DA xaml tasarlama](/visualstudio/xaml-tools/designing-xaml-in-visual-studio).

#### <a name="dependency-properties"></a>Bağımlılık Özellikleri

`get` `set` Daha önce AÇıKLANDıĞı gibi CLR ve erişimcileri, "bağımlılık özelliklerini kullan" bölümünde uyguladığınızdan emin olun. Tasarımcılar bir bağımlılık özelliğinin varlığını algılamak için sarmalayıcı kullanabilir, ancak bu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellik ve denetimin istemcileri, özelliği alırken veya ayarlarken erişimcileri çağırmak için gerekli değildir.

#### <a name="attached-properties"></a>İliştirilmiş Özellikler

Aşağıdaki yönergeleri kullanarak özel denetimlere Ekli Özellikler uygulamalısınız:

- `public` `static` `readonly` <xref:System.Windows.DependencyProperty> Yöntemi kullanılarak oluşturulan bir form *PropertyName* 'e sahip `Property` <xref:System.Windows.DependencyProperty.RegisterAttached%2A> . Geçirilen Özellik adı <xref:System.Windows.DependencyProperty.RegisterAttached%2A> *PropertyName*ile aynı olmalıdır.

- `public` `static` `Set` *PropertyName* ve `Get` *PropertyName*adlı bir çift CLR yöntemi uygulayın. Her iki yöntem de <xref:System.Windows.DependencyProperty> ilk bağımsız değişkeni olarak sınıfından türetilmiş bir sınıfı kabul etmelidir. `Set` *PropertyName* yöntemi, türü özelliği için kayıtlı veri türüyle eşleşen bir bağımsız değişkeni de kabul eder. `Get` *PropertyName* yöntemi aynı türde bir değer döndürmelidir. `Set` *PropertyName* yöntemi eksikse, özelliği salt okunurdur olarak işaretlenir.

- `Set`*PropertyName* ve `Get` *PropertyName* , <xref:System.Windows.DependencyObject.GetValue%2A> <xref:System.Windows.DependencyObject.SetValue%2A> sırasıyla hedef bağımlılık nesnesi üzerindeki ve yöntemlerine doğrudan yönlendirmelidir. Tasarımcılar, yöntem sarmalayıcısı aracılığıyla arayarak veya hedef bağımlılık nesnesine doğrudan çağrı yaparak ekli özelliğe erişebilir.

Ekli Özellikler hakkında daha fazla bilgi için bkz. [ekli özelliklere genel bakış](../advanced/attached-properties-overview.md).

### <a name="define-and-use-shared-resources"></a>Paylaşılan kaynakları tanımlama ve kullanma

Denetiminizi uygulamanız ile aynı derlemeye dahil edebilir veya birden çok uygulamada kullanılabilen ayrı bir derlemede denetiminizi paketleyebilir. Çoğu bölümde, bu konuda tartışılan bilgiler kullandığınız yöntemden bağımsız olarak geçerlidir.  Ancak, buna dikkat edilecek bir fark vardır.  Bir uygulamayı bir uygulama olarak aynı derlemeye yerleştirdiğinizde, App. xaml dosyasına genel kaynaklar ekleyebilirsiniz. Ancak yalnızca denetimleri içeren bir derlemeye <xref:System.Windows.Application> kendisiyle ilişkili bir nesne yoktur, bu nedenle App. xaml dosyası kullanılamaz.

Bir uygulama bir kaynağı ararken, üç düzeye aşağıdaki sırayla bakar:

1. Öğe düzeyi.

   Sistem, kaynağa başvuruda bulunan öğeyle başlar ve sonra mantıksal üst öğenin kaynaklarını arar ve bu nedenle kök öğeye ulaşılana kadar bu şekilde devam eder.

2. Uygulama düzeyi.

   Nesne tarafından tanımlanan kaynaklar <xref:System.Windows.Application> .

3. Tema düzeyi.

   Tema düzeyi sözlükler, Temalar adlı bir alt klasörde depolanır.  Temalar klasöründeki dosyalar temalara karşılık gelir.  Örneğin, Aero. NormalColor. xaml, Luna. NormalColor. xaml, Royale. NormalColor. xaml, vb. olabilir.  Ayrıca, Generic. xaml adlı bir dosyaya da sahip olabilirsiniz.  Sistem Temalar düzeyinde bir kaynak ararken, önce temaya özel dosyada arama yapar ve ardından bunu genel. xaml içinde arar.

Denetiminiz uygulamadan ayrı bir derlemede olduğunda, genel kaynaklarınızı öğe düzeyinde veya tema düzeyinde koymanız gerekir. Her iki yöntem de avantajlarına sahiptir.

#### <a name="defining-resources-at-the-element-level"></a>Öğe düzeyinde kaynakları tanımlama

Özel bir kaynak sözlüğü oluşturarak ve denetimin kaynak sözlüğü ile birleştirerek, öğe düzeyinde paylaşılan kaynaklar tanımlayabilirsiniz.  Bu yöntemi kullandığınızda, kaynak dosyanıza istediğiniz her şeyi verebilir ve denetimleriniz ile aynı klasörde olabilir. Öğe düzeyindeki kaynaklar, anahtar olarak basit dizeler da kullanabilir. Aşağıdaki örnek <xref:System.Windows.Media.LinearGradientBrush> Dictionary1. xaml adlı bir kaynak dosyası oluşturur.

[!code-xaml[SharedResources#1](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/Dictionary1.xaml#1)]

Sözlüğünüzü tanımladıktan sonra denetimin kaynak sözlüğü ile birleştirmeniz gerekir.  Bunu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] veya kodunu kullanarak yapabilirsiniz.

Aşağıdaki örnek kullanarak bir kaynak sözlüğünü birleştirir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] .

[!code-xaml[SharedResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml#2)]

Bu yaklaşımın dezavantajı, <xref:System.Windows.ResourceDictionary> ona her başvurduğunuzda bir nesne oluşturulur.  Örneğin, kitaplığınızda 10 özel denetiminiz varsa ve XAML kullanarak her denetim için paylaşılan kaynak sözlüklerini birleştirirseniz, 10 özdeş <xref:System.Windows.ResourceDictionary> nesne oluşturursunuz.  Bu, koddaki kaynakları birleştiren ve sonucu döndüren bir statik sınıf oluşturarak bunu önleyebilirsiniz <xref:System.Windows.ResourceDictionary> .

Aşağıdaki örnek, paylaşılan bir sınıf oluşturur <xref:System.Windows.ResourceDictionary> .

[!code-csharp[SharedResources#3](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/SharedDictionaryManager.cs#3)]

Aşağıdaki örnek, bir paylaşılan kaynağı, çağrı yapmadan önce denetimin oluşturucusunda özel bir denetimin kaynaklarıyla birleştirir `InitializeComponent` .  `SharedDictionaryManager.SharedDictionary`Statik bir özellik olduğundan, <xref:System.Windows.ResourceDictionary> yalnızca bir kez oluşturulur. Kaynak sözlüğü çağrılmadan önce birleştirildiğinden `InitializeComponent` , kaynaklar dosyasında denetim için kullanılabilir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] .

[!code-csharp[SharedResources#4](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml.cs#4)]

#### <a name="defining-resources-at-the-theme-level"></a>Tema düzeyinde kaynakları tanımlama

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]farklı Windows temaları için kaynaklar oluşturmanızı sağlar.  Denetim yazarı olarak, belirli bir temaya ait bir kaynağı tanımlayabilir ve hangi temanın kullanımda olduğuna bağlı olarak denetiminizin görünümünü değiştirebilirsiniz. Örneğin, <xref:System.Windows.Controls.Button> Windows klasik teması içindeki (windows 2000 için varsayılan tema) görünümü, <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Button> her tema için farklı bir değer kullandığından, Windows Luna TEMASıNDAKI (Windows XP için varsayılan tema) bir ' dan farklıdır <xref:System.Windows.Controls.ControlTemplate> .

Bir temaya özgü kaynaklar, belirli bir dosya adına sahip bir kaynak sözlüğünde tutulur. Bu dosyalar, `Themes` denetimi içeren klasörün bir alt klasörü olan adlı bir klasörde olmalıdır. Aşağıdaki tabloda, kaynak sözlüğü dosyaları ve her bir dosyayla ilişkili tema listelenmektedir:

|Kaynak sözlüğü dosya adı|Windows teması|
|-----------------------------------|-------------------|
|`Classic.xaml`|Klasik Windows 9x/2000 Windows XP 'ye bakış|
|`Luna.NormalColor.xaml`|Windows XP 'de varsayılan mavi tema|
|`Luna.Homestead.xaml`|Windows XP 'de zeytin teması|
|`Luna.Metallic.xaml`|Windows XP 'de Gümüş teması|
|`Royale.NormalColor.xaml`|Windows XP Media Center Edition 'da varsayılan tema|
|`Aero.NormalColor.xaml`|Windows Vista 'da varsayılan tema|

Her tema için bir kaynak tanımlamanız gerekmez. Belirli bir tema için bir kaynak tanımlanmamışsa denetim, `Classic.xaml` kaynağı denetler. Kaynak, geçerli temaya veya ' de karşılık gelen dosyada tanımlanmamışsa, `Classic.xaml` Denetim adlı bir kaynak sözlüğü dosyasında olan genel kaynağı kullanır `generic.xaml` .  `generic.xaml`Dosya, temaya özgü kaynak sözlüğü dosyalarıyla aynı klasörde bulunur. `generic.xaml`, Belirli bir Windows temasına karşılık gelmese de, hala Tema düzeyi bir sözlüktür.

[C#](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp) veya [Visual Basic](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic) NumericUpDown özel denetımı ile tema ve UI Otomasyonu desteği örneği, denetim için iki kaynak sözlüğü içerir `NumericUpDown` : biri Generic. xaml içinde, diğeri de Luna. NormalColor. xaml ' de bulunur.

<xref:System.Windows.Controls.ControlTemplate>Temayı özel kaynak sözlüğü dosyalarından birine yerleştirdiğinizde, denetiminiz için bir statik oluşturucu oluşturmanız ve <xref:System.Windows.DependencyProperty.OverrideMetadata%28System.Type%2CSystem.Windows.PropertyMetadata%29> <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> Aşağıdaki örnekte gösterildiği gibi, üzerinde yöntemini çağırmanız gerekir.

[!code-csharp[CustomControlNumericUpDownOneProject#StaticConstructor](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/CSharp/NumericUpDown.cs#staticconstructor)]
[!code-vb[CustomControlNumericUpDownOneProject#StaticConstructor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/visualbasic/numericupdown.vb#staticconstructor)]

##### <a name="defining-and-referencing-keys-for-theme-resources"></a>Tema kaynakları için anahtar tanımlama ve başvuru

Öğe düzeyinde bir kaynak tanımladığınızda, anahtarı olarak bir dize atayabilir ve dize aracılığıyla kaynağa erişebilirsiniz. Tema düzeyinde bir kaynak tanımladığınızda, <xref:System.Windows.ComponentResourceKey> anahtar olarak bir olarak kullanmanız gerekir.  Aşağıdaki örnek, genel. xaml içinde bir kaynağı tanımlar.

[!code-xaml[ThemeResourcesControlLibrary#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/Themes/generic.xaml#5)]

Aşağıdaki örnek, anahtar olarak öğesini belirterek kaynağa başvurur <xref:System.Windows.ComponentResourceKey> .

[!code-xaml[ThemeResourcesControlLibrary#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/NumericUpDown.xaml#6)]

##### <a name="specifying-the-location-of-theme-resources"></a>Tema kaynaklarının konumunu belirtme

Bir denetimin kaynaklarını bulmak için barındırma uygulamasının, derlemenin denetime özgü kaynakları içerdiğini bilmeleri gerekir. Bunu, <xref:System.Windows.ThemeInfoAttribute> denetimini içeren derlemeye ekleyerek yapabilirsiniz. , <xref:System.Windows.ThemeInfoAttribute> <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> Genel kaynakların konumunu ve <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A> temaya özgü kaynakların konumunu belirten bir özelliği olan bir özelliğine sahiptir.

Aşağıdaki örnek, <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> ve <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A> özelliklerini <xref:System.Windows.ResourceDictionaryLocation.SourceAssembly> , genel ve temaya özgü kaynakların denetimle aynı derlemede olduğunu belirtmek için olarak ayarlar.

[!code-csharp[CustomControlNumericUpDown#ThemesSection](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/Properties/AssemblyInfo.cs#themessection)]
[!code-vb[CustomControlNumericUpDown#ThemesSection](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/my project/assemblyinfo.vb#themessection)]

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio’da XAML tasarlama](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [WPF İçinde URI'leri Paketleme](../app-development/pack-uris-in-wpf.md)
- [Denetim Özelleştirme](control-customization.md)
