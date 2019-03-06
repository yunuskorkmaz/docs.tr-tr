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
ms.openlocfilehash: 2007ee7680707cd1cc9628cc3900ca1068db8678
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368733"
---
# <a name="control-authoring-overview"></a>Denetim Yazımına Genel Bakış
Genişletilmesinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] denetimi modeli, yeni bir denetim oluşturmak için gereken önemli ölçüde azaltır. Ancak, bazı durumlarda, yine de özel bir denetim oluşturmak gerekebilir. Bu konuda bir özel denetim oluşturup farklı denetim modellerinde yazma gereksiniminizi en aza özellikleri anlatılmaktadır [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Bu konuda ayrıca yeni bir denetimin nasıl oluşturulacağını gösterir.  
  
 
  
<a name="when_to_write_a_new_control"></a>   
## <a name="alternatives-to-writing-a-new-control"></a>Yeni bir denetim yazmak için alternatifleri  
 Varolan bir denetimden özelleştirilmiş bir deneyim almak istediyseniz, tarihsel olarak, denetimin arka plan renk ve kenarlık genişliği yazı tipi boyutu gibi standart özelliklerini değiştirme ile sınırlıydı. Görünümünü veya davranışını bir denetimin önceden tanımlanmış bu parametreleri ötesine genişletmek istediğinizde, yeni bir denetim, varolan bir denetimden devralan ve denetimi çizmek için sorumlu yöntemini geçersiz kılma tarafından genellikle oluşturmanız gerekir.  Bu seçenek, hala olsa [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zengin içerik modeli, stiller, şablonlar ve Tetikleyicileri kullanarak mevcut denetimleri özelleştirmenizi, sağlar. Aşağıdaki listede, bu özellikleri yeni bir denetim oluşturmak zorunda kalmadan, özel ve tutarlı deneyimler oluşturmak için nasıl kullanılabileceğini örnekler verilmektedir.  
  
-   **Zengin içerik.** Çoğu standart [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimleri Zengin içeriği destekler. Örneğin, içerik özelliğinin bir <xref:System.Windows.Controls.Button> türünde <xref:System.Object>, bu nedenle teorik herhangi bir şey görüntülenebilir üzerinde bir <xref:System.Windows.Controls.Button>.  Bir resim ve metin görüntülemek için bir düğme için resim ekleyebilirsiniz ve <xref:System.Windows.Controls.TextBlock> için bir <xref:System.Windows.Controls.StackPanel> ve atama <xref:System.Windows.Controls.StackPanel> için <xref:System.Windows.Controls.ContentControl.Content%2A> özelliği. Çünkü denetimleri görüntüleyebilir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] görsel öğeler ve rastgele veriler, yeni bir denetim oluşturmak veya karmaşık bir görselleştirmeyi desteklemek için varolan bir denetimi değiştirmek için daha az gerek yoktur. İçin içerik modeli hakkında daha fazla bilgi için <xref:System.Windows.Controls.Button> ve diğer içerik modelleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bkz: [WPF içerik modeli](wpf-content-model.md).  
  
-   **Stilleri.** A <xref:System.Windows.Style> denetimin özelliklerini göstermek değerleri oluşan bir koleksiyondur. Stilleri kullanarak, yeni bir denetim yazmaya gerek kalmadan istenen denetimin görünümünü ve davranışını yeniden kullanılabilir bir temsilini oluşturabilirsiniz. Örneğin, tüm istediğinizi varsayalım, <xref:System.Windows.Controls.TextBlock> 14 yazı tipi boyutunu kırmızı, Arial yazı tipi denetimleri. Bir kaynak olarak stil oluşturma ve buna uygun olarak uygun özelliklerini ayarlayın. Sonra her <xref:System.Windows.Controls.TextBlock> uygulamanıza eklemek, aynı görünüme sahip olur.  
  
-   **Veri şablonları.** A <xref:System.Windows.DataTemplate> denetimde verilerin nasıl görüntüleneceğini özelleştirmenize olanak sağlar. Örneğin, bir <xref:System.Windows.DataTemplate> verilerin nasıl görüntüleneceğini belirtmek için kullanılan bir <xref:System.Windows.Controls.ListBox>.  Bu örnek için bkz [veri şablonu oluşturmaya genel bakış](../data/data-templating-overview.md).  Veri görünümünü özelleştirme yanı sıra bir <xref:System.Windows.DataTemplate> hangi, özel kullanıcı arabirimleri büyük bir esneklik sunar UI öğelerini içerebilir.  Kullanarak örneğin, bir <xref:System.Windows.DataTemplate>, oluşturabileceğiniz bir <xref:System.Windows.Controls.ComboBox> içinde bir onay kutusu her hangi bir öğesi içerir.  
  
-   **Denetim şablonları.** Birçok denetimlerinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullanan bir <xref:System.Windows.Controls.ControlTemplate> denetimin yapısını ve denetimi işlevlerini bir denetimin görünümünü ayıran tanımlamak için. Önemli ölçüde tanımlayarak bir denetimin görünümünü değiştirebilirsiniz, <xref:System.Windows.Controls.ControlTemplate>.  Örneğin, bir trafik ışığı gibi görünen bir denetim istediğinizi varsayalım. Bu denetim, bir basit kullanıcı arabirimi ve işlevleri vardır.  Aynı anda yalnızca biri yanabildiği üç daire denetimidir. Bazı yansıma sonra fark edebilirsiniz bir <xref:System.Windows.Controls.RadioButton> tek bir zaman, ancak varsayılan görünümünü seçili işlevselliği sunduğunu <xref:System.Windows.Controls.RadioButton> bir trafik ışığı üzerinde ışık yokmuş gibi görünüyor.  Çünkü <xref:System.Windows.Controls.RadioButton> onun görünümünü tanımlamak için bir denetim şablonu kullanır tanımlanacak kolaydır <xref:System.Windows.Controls.ControlTemplate> denetimin gereksinimlere uygun ve radyo düğmeleri, trafik ışığı yapmak için kullanın.  
  
    > [!NOTE]
    >  Ancak bir <xref:System.Windows.Controls.RadioButton> kullanabileceğiniz bir <xref:System.Windows.DataTemplate>, <xref:System.Windows.DataTemplate> Bu örnekte yeterli değildir.  <xref:System.Windows.DataTemplate> Denetiminin içeriğini görünümünü tanımlar. Durumunda, bir <xref:System.Windows.Controls.RadioButton>, içeriği ne olursa olsun gösteren daire sağında görünür olup olmadığını <xref:System.Windows.Controls.RadioButton> seçilir.  Trafik ışığı örnekte radyo düğmesini yalnızca "vurgulamasında." bir daire olması gerekir Trafik ışığı görünüm gereksinimi çok varsayılan görünümünü farklı olduğundan <xref:System.Windows.Controls.RadioButton>, yeniden tanımlanacak gereklidir <xref:System.Windows.Controls.ControlTemplate>.  Genel bir <xref:System.Windows.DataTemplate> bir denetimi ve bir içerik (veya veri) tanımlamak için kullanılan <xref:System.Windows.Controls.ControlTemplate> denetimin nasıl yapılandırılacağını tanımlamak için kullanılır.  
  
-   **Tetikler.** A <xref:System.Windows.Trigger> yeni bir denetim oluşturmadan görünümünü ve davranışını bir denetimi dinamik olarak değiştirmenize olanak tanır. Örneğin, birden çok olduğunu varsayalım <xref:System.Windows.Controls.ListBox> denetimleri, uygulamanızda ve her öğe <xref:System.Windows.Controls.ListBox> seçildiklerinde kalın ve kırmızı olarak. İlk olarak, devralınan bir sınıf oluşturmak için olabilir <xref:System.Windows.Controls.ListBox> ve geçersiz kılma <xref:System.Windows.Controls.Primitives.Selector.OnSelectionChanged%2A> seçilen öğe, ancak daha iyi bir yaklaşım görünümünü değiştirmek için yöntemi stili için bir tetikleyici eklemek için bir <xref:System.Windows.Controls.ListBoxItem> görünümünü değiştirir Seçili öğe. Bir tetikleyici özellik değerlerini değiştirmek veya bir özellik değerine göre eylemleri sağlar. Bir <xref:System.Windows.EventTrigger> bir olay gerçekleştiğinde Eylemler yararlanmanıza olanak sağlar.  
  
 Stiller, şablonlar ve tetikleyicileri hakkında daha fazla bilgi için bkz: [stil ve şablon oluşturma](styling-and-templating.md).  
  
 Genel olarak, varolan bir denetimi işlevlerini denetiminiz yansıtır, ancak denetim farklı görünmesini istediğiniz, öncelikle, bu bölümde açıklanan yöntemlerden herhangi birini varolan denetimin görünümünü değiştirmek için kullanıp kullanamayacağını düşünmelisiniz.  
  
<a name="models_for_control_authoring"></a>   
## <a name="models-for-control-authoring"></a>Denetim yazma modelleri  
 Zengin içerik modeli, stiller, şablonlar ve Tetikleyicileri yeni bir denetim oluşturmak için gereken en aza indirin. Yeni bir denetim oluşturmak ihtiyacınız varsa, ancak farklı denetim modellerinde yazma anlamak önemlidir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] her biri farklı bir özellik kümesi ve esneklik düzeyi sağlayan bir denetim oluşturmak için üç genel model sağlar. Temel sınıflar için üç model <xref:System.Windows.Controls.UserControl>, <xref:System.Windows.Controls.Control>, ve <xref:System.Windows.FrameworkElement>.  
  
### <a name="deriving-from-usercontrol"></a>UserControl türetme  
 Denetimi oluşturmak için en basit yolu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] türetmek için <xref:System.Windows.Controls.UserControl>. Öğesinden devralınan bir denetim oluşturduğunuzda <xref:System.Windows.Controls.UserControl>, mevcut bileşenine ekleme <xref:System.Windows.Controls.UserControl>bileşenleri adlandırın ve olay işleyicileri başvuru [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Adlandırılmış öğeleri başvurusu ve kod işleyicilerini tanımlar. Bu geliştirme modeli uygulama geliştirmesinde kullanılan modeline benzer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Doğru bir şekilde oluşturulduysa bir <xref:System.Windows.Controls.UserControl> zengin içerik ve stiller Tetikleyicileri avantajlarından yararlanabilirsiniz. Bununla birlikte, Denetim öğesinden devralıyorsa <xref:System.Windows.Controls.UserControl>, denetiminizin kullanan kişilerin kullanmanız mümkün olmayacak bir <xref:System.Windows.DataTemplate> veya <xref:System.Windows.Controls.ControlTemplate> görünümünü özelleştirmek için.  Öğesinden türetilen gereklidir <xref:System.Windows.Controls.Control> sınıfı veya türetilmiş sınıflarının biri (dışında <xref:System.Windows.Controls.UserControl>) Şablonları destekleyen özel bir denetim oluşturmak için.  
  
#### <a name="benefits-of-deriving-from-usercontrol"></a>UserControl türetme avantajları  
 Öğesinden türetme göz önünde bulundurun <xref:System.Windows.Controls.UserControl> aşağıdakilerin tümü geçerli değilse:  
  
-   Benzer şekilde bir uygulamayı nasıl oluşturacağınız denetiminizi oluşturmak istiyorsunuz.  
  
-   Denetim, yalnızca mevcut bileşenden oluşur.  
  
-   Destek karmaşık özelleştirme gerek yoktur.  
  
### <a name="deriving-from-control"></a>Denetim türetme  
 Öğesinden türetme <xref:System.Windows.Controls.Control> sınıfı, var olan bir çoğu tarafından kullanılan model [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrol eder. Bir denetim oluştururken devraldığı <xref:System.Windows.Controls.Control> sınıfı, tanımladığınız görünümünü şablonları kullanarak. Bunu yaptığınızda, çalışma mantığını görsel gösterimden ayırın. Kullanıcı Arabirimi ve mantık komutları ve bağlamaları olayları ve kaçınarak başvuruda bulunan öğeleri yerine kullanarak bağlantıyı kesme sağlayabilirsiniz <xref:System.Windows.Controls.ControlTemplate> mümkün olduğunda.  Kullanıcı denetiminizin Denetiminizin mantığı ve UI düzgün ayrılmış, denetimin tanımlayabilirsiniz <xref:System.Windows.Controls.ControlTemplate> görünümünü özelleştirmek için. Özel bir derleme rağmen <xref:System.Windows.Controls.Control> oluşturma kadar basit değil bir <xref:System.Windows.Controls.UserControl>, özel bir <xref:System.Windows.Controls.Control> en fazla esnekliği sağlar.  
  
#### <a name="benefits-of-deriving-from-control"></a>Denetim türetme avantajları  
 Öğesinden türetme göz önünde bulundurun <xref:System.Windows.Controls.Control> kullanmak yerine <xref:System.Windows.Controls.UserControl> aşağıdaki durumlardan biri geçerliyse sınıfı:  
  
-   Denetim aracılığıyla özelleştirilebilir görünümünü istediğiniz <xref:System.Windows.Controls.ControlTemplate>.  
  
-   Denetiminiz farklı Temalar desteklemek için kullanmanız gerekir.  
  
### <a name="deriving-from-frameworkelement"></a>FrameworkElement türetme  
 Öğesinden türetilen denetimler <xref:System.Windows.Controls.UserControl> veya <xref:System.Windows.Controls.Control> var olan öğeleri birleştirmeye dayanır. Herhangi bir nesne öğesinden devralan birçok senaryo için kabul edilebilir bir çözümü olmasıdır <xref:System.Windows.FrameworkElement> olabilir bir <xref:System.Windows.Controls.ControlTemplate>. Ancak, bir denetimin görünümünü birden çok basit bir öğe oluşturma işlevselliğini gerektirdiğinde zamanlar vardır. Bu senaryolarda, bir bileşen dayandırmaktadır <xref:System.Windows.FrameworkElement> doğru seçimdir.  
  
 Standart iki farklı yöntemle oluşturmak için <xref:System.Windows.FrameworkElement>-temel bileşenleri: doğrudan işleme ve özel öğesi oluşturma. İşleme içerir geçersiz kılma doğrudan <xref:System.Windows.UIElement.OnRender%2A> yöntemi <xref:System.Windows.FrameworkElement> sağlayarak <xref:System.Windows.Media.DrawingContext> bileşeni görsellerini açıkça tanımlayan operations. Tarafından kullanılan yöntem budur <xref:System.Windows.Controls.Image> ve <xref:System.Windows.Controls.Border>. Özel öğe oluşturma içerir türündeki nesneler kullanarak <xref:System.Windows.Media.Visual> bileşeniniz görünümünü oluşturmak için. Bir örnek için bkz. [DrawingVisual nesnelerini kullanma](../graphics-multimedia/using-drawingvisual-objects.md). <xref:System.Windows.Controls.Primitives.Track> bir denetimde örneğidir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , özel öğe oluşturma kullanır. Doğrudan işleme ve aynı denetimi özel öğe birleşimde karıştırmak mümkündür.  
  
#### <a name="benefits-of-deriving-from-frameworkelement"></a>FrameworkElement türetme avantajları  
 Öğesinden türetme göz önünde bulundurun <xref:System.Windows.FrameworkElement> aşağıdaki durumlardan biri geçerliyse:  
  
-   Basit bir öğe oluşturma tarafından sağlanan dışında denetimin görünümünü üzerinde tam denetime sahip olmasını istediğiniz.  
  
-   Kendi işleme mantığı tanımlayarak, denetimin görünümünü tanımlamak istersiniz.  
  
-   Var olan öğeleri ile neler yapılabileceğini ötesinde yeni yollarla oluşturmak istediğiniz <xref:System.Windows.Controls.UserControl> ve <xref:System.Windows.Controls.Control>.  
  
<a name="control_authoring_basics"></a>   
## <a name="control-authoring-basics"></a>Denetim temelleri yazma  
 En güçlü özelliklerinden biri daha önce açıklandığı gibi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yeteneği temel görünümünü ve davranışını değiştirmek için bir denetim özelliklerini ayarlama, ancak yine de özel bir denetim oluşturmak zorunda kalmamanız ötesine gidin. Stil, veri bağlama ve tetikleme özellikleri tarafından gerçekleştirilebilen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellik sistemi ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olay sistemi. Uygulamanız gereken bazı yöntemler aşağıdaki bölümlerde, bulunan bir denetim için yaptıkları gibi özel denetiminizin kullanıcılar bu özellikleri kullanabilmesi için model bağımsız olarak özel bir denetim oluşturmak için kullandığınız [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="use-dependency-properties"></a>Bağımlılık özellikleri kullanın  
 Bağımlılık özelliği bir özellik olduğundan, aşağıdakileri yapmak mümkündür:  
  
-   Bir stil özelliğini ayarlayın.  
  
-   Özelliği, bir veri kaynağına bağlama.  
  
-   Dinamik bir kaynak özelliğinin değeri kullanın.  
  
-   Özelliğe animasyon ekleme.  
  
 Bu işlevleri desteklemek için denetimin bir özelliğine istiyorsanız, bir bağımlılık özelliği olarak uygulamanız gerekir. Aşağıdaki örnekte adlı bir bağımlılık özelliğini tanımlar `Value` aşağıdakileri yaparak:  
  
-   Tanımlayan bir <xref:System.Windows.DependencyProperty> tanımlayıcı adlı `ValueProperty` olarak bir `public` `static` `readonly` alan.  
  
-   Özellik adı, özellik sistemi ile çağırarak kaydedin <xref:System.Windows.DependencyProperty.Register%2A?displayProperty=nameWithType>, aşağıdakileri belirtin:  
  
    -   Özelliğin adı.  
  
    -   Özelliğin türü.  
  
    -   Özellik sahibi türü.  
  
    -   Bir özellik için meta veriler. Özelliğin varsayılan değeri, meta veriler içeren bir <xref:System.Windows.CoerceValueCallback> ve <xref:System.Windows.PropertyChangedCallback>.  
  
-   Tanımlayan bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] adlı sarmalayıcı özellik `Value`, özelliğin uygulayarak bağımlılık özelliği kaydetmek için kullanılan aynı adı `get` ve `set` erişimcileri. Unutmayın `get` ve `set` erişimciler yalnızca çağrı <xref:System.Windows.DependencyObject.GetValue%2A> ve <xref:System.Windows.DependencyObject.SetValue%2A> sırasıyla. Bağımlılık özellikleri erişimcileri ek mantık için içermemesi önerilir istemcileri ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] erişimciler ve arama devre dışı bırakabilir <xref:System.Windows.DependencyObject.GetValue%2A> ve <xref:System.Windows.DependencyObject.SetValue%2A> doğrudan. Örneğin, bir özellik için bir veri bağlı olduğunda kaynak, özelliğin `set` erişimci çağrılmaz.  Get için ilave bir mantık eklemek yerine ve ayarlama erişimci, kullanın <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.CoerceValueCallback>, ve <xref:System.Windows.PropertyChangedCallback> temsilciler yanıtlamak ya da değiştiğinde değerini denetleyin.  Bu geri aramalarda hakkında daha fazla bilgi için bkz. [bağımlılık özelliği geri aramaları ve doğrulama](../advanced/dependency-property-callbacks-and-validation.md).  
  
-   Bir yöntemi tanımlamak <xref:System.Windows.CoerceValueCallback> adlı `CoerceValue`. `CoerceValue` sağlar `Value` büyük veya eşittir `MinValue` ve daha az veya buna eşit `MaxValue`.  
  
-   Bir yöntemi tanımlamak <xref:System.Windows.PropertyChangedCallback>, adlandırılmış `OnValueChanged`. `OnValueChanged` oluşturur bir <xref:System.Windows.RoutedPropertyChangedEventArgs%601> nesne ve yükseltmek hazırlar `ValueChanged` yönlendirilmiş olay. Yönlendirilmiş olaylar, sonraki bölümde ele alınmıştır.  
  
 [!code-csharp[UserControlNumericUpDown#DependencyProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#dependencyproperty)]
 [!code-vb[UserControlNumericUpDown#DependencyProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#dependencyproperty)]  
  
 Daha fazla bilgi için [özel bağımlılık özellikleri](../advanced/custom-dependency-properties.md).  
  
### <a name="use-routed-events"></a>Yönlendirilmiş olayları kullanma  
 Bağımlılık olarak kavramı özellikleri genişletmenize [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] ek işlevsellik ile özellikleri, yönlendirilmiş olaylar genişleten standart [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] olayları. Yeni bir oluşturduğunuzda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimi olduğu da gönderilmiş bir olay aşağıdaki davranış desteklediğinden, olay gönderilmiş bir olay uygulamak için iyi bir uygulamadır:  
  
-   Olayları üst öğesi birden çok denetim üzerinde yönetilebilir. Bir olay, tırmanma olay ise, öğe ağacında tek bir üst olaya abone olabilirsiniz. Ardından uygulama yazarları, birden çok denetim olaya yanıt vermek için bir işleyici kullanabilirsiniz. Örneğin, denetim her öğe bir parçası ise bir <xref:System.Windows.Controls.ListBox> (içinde bulunduğundan bir <xref:System.Windows.DataTemplate>), uygulama geliştiricisi üzerinde denetim olayı için olay işleyicisi tanımlayabilirsiniz <xref:System.Windows.Controls.ListBox>. Tüm denetimleri olay oluştuğunda, olay işleyicisinde çağrılır.  
  
-   Yönlendirilmiş olaylar kullanılabilir bir <xref:System.Windows.EventSetter>, stil içinde bir olay işleyicisi belirtmek, uygulama geliştiricilerinin sağlar.  
  
-   Yönlendirilmiş olaylar kullanılabilir bir <xref:System.Windows.EventTrigger>, kullanarak hareketlendirme özellikleri için yararlı olan [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Daha fazla bilgi için [animasyona genel bakış](../graphics-multimedia/animation-overview.md).  
  
 Aşağıdaki örnek, aşağıdakileri yaparak gönderilmiş bir olayı tanımlar:  
  
-   Tanımlayan bir <xref:System.Windows.RoutedEvent> tanımlayıcı adlı `ValueChangedEvent` olarak bir `public` `static` `readonly` alan.  
  
-   Yönlendirilmiş olay çağırarak kayıt <xref:System.Windows.EventManager.RegisterRoutedEvent%2A?displayProperty=nameWithType> yöntemi. Çağırdığında, örnek aşağıdaki bilgiler belirtir <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>:  
  
    -   Olay adı `ValueChanged`.  
  
    -   Yönlendirme stratejisi <xref:System.Windows.RoutingStrategy.Bubble>, yani bir olay işleyicisi (olayı başlatan nesne) kaynak ilk olarak adlandırılır ve art arda en yakın üzerinde olay işleyicisi ile başlayarak, olay işleyicileri kaynağın üst öğelerde sonra çağırılır üst öğe.  
  
    -   Olay işleyicisinin türü <xref:System.Windows.RoutedPropertyChangedEventHandler%601>, ile oluşturulmuş bir <xref:System.Decimal> türü.  
  
    -   Sahip olan olay türüdür `NumericUpDown`.  
  
-   Adlı bir ortak olay bildirmek `ValueChanged` ve olay erişimcisi bildirimlerine içerir. Örneği çağrıları <xref:System.Windows.UIElement.AddHandler%2A> içinde `add` erişimci bildirimi ve <xref:System.Windows.UIElement.RemoveHandler%2A> içinde `remove` kullanmak için erişimci bildirimi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olay Hizmetleri.  
  
-   Adlı korumalı, sanal bir yöntem oluşturma `OnValueChanged` olayını `ValueChanged` olay.  
  
 [!code-csharp[UserControlNumericUpDown#RoutedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#routedevent)]
 [!code-vb[UserControlNumericUpDown#RoutedEvent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#routedevent)]  
  
 Daha fazla bilgi için [yönlendirilmiş olaylara genel bakış](../advanced/routed-events-overview.md) ve [yönlendirilmiş bir özel olay oluşturma](../advanced/how-to-create-a-custom-routed-event.md).  
  
### <a name="use-binding"></a>Bağlama kullanın  
 Kullanıcı arabirimini denetiminizin mantığından ayırmak için veri bağlama kullanmayı düşünün. Bu, denetimin görünümünü kullanarak tanımlarsanız, özellikle önemli bir <xref:System.Windows.Controls.ControlTemplate>. Veri bağlama kullandığınızda, kullanıcı Arabiriminin belirli bölümlerini koddan başvuru yapmak zorunda kalmıyoruz mümkün olabilir. İçindeki öğelere başvuran önlemek için iyi bir fikirdir <xref:System.Windows.Controls.ControlTemplate> zaman kod içinde olan öğeler başvurduğundan <xref:System.Windows.Controls.ControlTemplate> ve <xref:System.Windows.Controls.ControlTemplate> değiştirildiğinde, yeni dahil edilecek başvurulan öğenin gereksinimlerini <xref:System.Windows.Controls.ControlTemplate>.  
  
 Aşağıdaki örnek güncelleştirmeleri <xref:System.Windows.Controls.TextBlock> , `NumericUpDown` için bir ad atamak ve kod adı metin kutusuna başvurularak denetimi.  
  
 [!code-xaml[UserControlNumericUpDownSimple#UIRefMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml#uirefmarkup)]  
  
 [!code-csharp[UserControlNumericUpDownSimple#UIRefCode](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml.cs#uirefcode)]
 [!code-vb[UserControlNumericUpDownSimple#UIRefCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDownSimple/VisualBasic/NumericUpDown.xaml.vb#uirefcode)]  
  
 Aşağıdaki örnek, bağlama aynı şeyi yapmak için kullanır.  
  
 [!code-xaml[UserControlNumericUpDown#Binding](~/samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml#binding)]  
  
 Veri bağlama hakkında daha fazla bilgi için bkz. [Data Binding Overview](../data/data-binding-overview.md).  
  
### <a name="design-for-designers"></a>Tasarımcılarına yönelik tasarım  
 Özel bir WPF denetimlerindeki destek almak için [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] (örneğin, özelliğin Özellikler penceresi ile düzenleme), aşağıdaki yönergeleri izleyin.  Geliştirme hakkında daha fazla bilgi için [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)], bkz: [Visual Studio'da XAML tasarım](/visualstudio/designers/designing-xaml-in-visual-studio).  
  
#### <a name="dependency-properties"></a>Bağımlılık özellikleri  
 Uygulamak mutlaka [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] `get` ve `set` "Kullanımı bağımlılık özelliklerini." daha önce açıklandığı erişimcileri Tasarımcıları gibi bir bağımlılık özelliği, ancak bunun varolup olmadığını algılamak için sarmalayıcı kullanabilir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve denetimin istemciler alma veya ayarlama özelliğini ayarlarken erişimcileri çağrı için gerekli değildir.  
  
#### <a name="attached-properties"></a>Ekli Özellikler  
 Ekli özellikler aşağıdaki yönergeleri kullanarak özel denetimlere uygulamanız gerekir:  
  
-   Sahip bir `public` `static` `readonly` <xref:System.Windows.DependencyProperty> formun *PropertyName* `Property` kullanarak sine <xref:System.Windows.DependencyProperty.RegisterAttached%2A> yöntemi. Geçirilen özellik adı <xref:System.Windows.DependencyProperty.RegisterAttached%2A> eşleşmelidir *PropertyName*.  
  
-   Bir çift uygulamak `public` `static` adlı CLR yöntemlerinde `Set` *PropertyName* ve `Get` *PropertyName*. Her iki yöntem, türetilen bir sınıf kabul etmelidir <xref:System.Windows.DependencyProperty> , ilk bağımsız değişken olarak. `Set` *PropertyName* yöntemi de türü özelliği için kayıtlı veri türü ile eşleşen bir bağımsız değişkeni kabul eder. `Get` *PropertyName* yöntemi, aynı türde bir değer döndürmelidir. Varsa `Set` *PropertyName* yöntemi eksik, özellik salt okunur olarak işaretlenir.  
  
-   `Set` *PropertyName* ve `Get` *PropertyName* doğrudan yönlendirmesi gerekirse <xref:System.Windows.DependencyObject.GetValue%2A> ve <xref:System.Windows.DependencyObject.SetValue%2A> hedef bağımlılık yöntemlerde nesnesi, sırasıyla. Tasarımcılar tarafından yöntemi sarmalayıcı çağrı yapma veya bir hedef bağımlılık nesneye doğrudan çağırmak ekli özellik erişebilir.  
  
 Ekli özellikler hakkında daha fazla bilgi için bkz. [ekli özelliklere genel bakış](../advanced/attached-properties-overview.md).  
  
### <a name="define-and-use-shared-resources"></a>Tanımlama ve paylaşılan kaynakları kullan  
 Uygulamanızla aynı derlemede denetiminiz içerebilir veya birden çok uygulamada kullanılabilen ayrı bir derleme denetiminizi paketleyebilirsiniz. Çoğunlukla, bu konuda tartışılan bilgiler kullandığınız yöntemden bağımsız olarak geçerlidir.  Ancak önemli bir fark yoktur.  Bir uygulama olarak aynı derleme içerisindeki bir denetim yerleştirdiğinizde, Genel kaynaklar App.xaml dosyasına eklemek ücretsizdir. Ancak yalnızca denetimleri içeren bir bütünleştirilmiş kod sahip olmadığı bir <xref:System.Windows.Application> bir App.xaml dosyası kullanılabilir değil. Bu nedenle, ilişkili nesne.  
  
 Bir uygulama için bir kaynak göründüğünde, üç düzeyde şu sırayla arar:  
  
1.  Öğe düzeyi.  
  
     Sistem kök öğe ulaşılana kadar kaynak mantıksal üst ve benzeri arar ve kaynağa başvuran bir öğe ile başlar.  
  
2.  Uygulama düzeyi.  
  
     Tarafından tanımlanan kaynakları <xref:System.Windows.Application> nesne.  
  
3.  Tema düzeyi.  
  
     Tema düzeyi sözlükler temaları adlı alt klasörde depolanır.  Temalar klasöründeki dosyaları temalara karşılık gelir.  Örneğin, Aero.NormalColor.xaml, Luna.NormalColor.xaml, Royale.NormalColor.xaml vb. olabilir.  Generic.xaml adlı bir dosya da olabilir.  Sistem, temalar düzeyinde bir kaynak için göründüğünde, ilk için temaya özgü dosyasına bakar ve ardından onu generic.xaml içinde arar.  
  
 Denetiminizi uygulamadan ayrı bir derleme olduğunda, öğe düzeyinde veya tema düzeyinde genel kaynaklarınızı yerleştirmeniz gerekir. Her iki yöntem de üstünlükleri vardır.  
  
#### <a name="defining-resources-at-the-element-level"></a>Öğe düzeyinde kaynakları tanımlama  
 Özel bir kaynak sözlüğü oluşturarak ve denetiminizin kaynak sözlüğü ile birleştirme öğe düzeyinde paylaşılan kaynakları tanımlayabilirsiniz.  Bu yöntemi kullandığınızda, istediğiniz herhangi bir şey ve bu denetimleri ile aynı klasörde olabilir, kaynak dosya adı verebilirsiniz. Öğe düzeyinde kaynakları, basit dizeler anahtarlar olarak da kullanabilirsiniz. Aşağıdaki örnek, oluşturur bir <xref:System.Windows.Media.LinearGradientBrush> Dictionary1.xaml adlı kaynak dosyası.  
  
 [!code-xaml[SharedResources#1](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/Dictionary1.xaml#1)]  
  
 Sözlüğünüz tanımlandıktan sonra denetiminizin kaynak sözlüğü ile birleştirmeniz gerekir.  Kullanarak bunu yapabilirsiniz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] veya kod.  
  
 Aşağıdaki örnek bir kaynak sözlüğü kullanarak birleştirir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[SharedResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml#2)]  
  
 Bu yaklaşımın bir dezavantajı olan bir <xref:System.Windows.ResourceDictionary> her başvurunuzda nesnesi oluşturulur.  10 özel Denetim Kitaplığı'nda varsa ve XAML kullanarak her denetim için paylaşılan kaynak sözlükleri birleştirme, örneğin, 10 aynı oluşturduğunuz <xref:System.Windows.ResourceDictionary> nesneleri.  Bu kodda kaynakları birleştirir ve sonuç döndüren bir statik sınıf oluşturarak önlemek <xref:System.Windows.ResourceDictionary>.  
  
 Aşağıdaki örnek, paylaşılan döndüren bir sınıf oluşturur. <xref:System.Windows.ResourceDictionary>.  
  
 [!code-csharp[SharedResources#3](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/SharedDictionaryManager.cs#3)]  
  
 Çağırmadan önce aşağıdaki örnek, paylaşılan kaynak denetim oluşturucusunda bir özel denetim kaynakları ile birleştirir. `InitializeComponent`.  Çünkü `SharedDictionaryManager.SharedDictionary` statik bir özellik <xref:System.Windows.ResourceDictionary> yalnızca bir kez oluşturulur. Kaynak sözlüğü önce birleştirilmesinden dolayı `InitializeComponent` olan adlı kaynaklar denetimi için kullanılabilir, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya.  
  
 [!code-csharp[SharedResources#4](~/samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml.cs#4)]  
  
#### <a name="defining-resources-at-the-theme-level"></a>Tema düzeyinde kaynakları tanımlama  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] farklı Windows temaları için kaynaklar oluşturmanızı sağlar.  Denetim yazarı olarak, hangi tema kullanımda bağlı olarak, denetimin görünümünü değiştirmek belirli bir tema için bir kaynak tanımlayabilirsiniz. Örneğin, görünümünü bir <xref:System.Windows.Controls.Button> Windows Klasik tema (Windows 2000 için varsayılan tema) farklıdır bir <xref:System.Windows.Controls.Button> (Windows XP için varsayılan tema) Windows Luna temadaki çünkü <xref:System.Windows.Controls.Button> farklı bir kullanır <xref:System.Windows.Controls.ControlTemplate> Her bir tema için.  
  
 Temaya özgü olan kaynakların belirli bir dosya adı ile bir kaynak sözlüğünde tutulur. Bu dosyalar adlı bir klasörde olmalıdır `Themes` diğer bir deyişle denetimi içeren bir klasörün bir alt. Aşağıdaki tabloda, kaynak sözlüğü dosyaları ve her bir dosya ile ilişkilendirilmiş tema listelenmektedir:  
  
|Kaynak sözlüğü dosyası adı|Windows teması|  
|-----------------------------------|-------------------|  
|`Classic.xaml`|Klasik Windows 9 x / 2000, Windows XP arayın|  
|`Luna.NormalColor.xaml`|Windows XP varsayılan mavi tema|  
|`Luna.Homestead.xaml`|Windows XP Zeytin teması|  
|`Luna.Metallic.xaml`|Windows XP Gümüş tema|  
|`Royale.NormalColor.xaml`|Windows XP Media Center Edition varsayılan tema|  
|`Aero.NormalColor.xaml`|Windows Vista'da varsayılan tema|  
  
 Her bir tema için bir kaynak tanımlamak gerekmez. Bir kaynak için belirli bir tema tanımlanmazsa denetimini kontrol eder `Classic.xaml` kaynak için. Kaynağın geçerli tema veya buna karşılık gelen dosyayı tanımlanmazsa `Classic.xaml`, adlı bir kaynak sözlüğü dosyasındaki genel kaynak denetimi kullanan `generic.xaml`.  `generic.xaml` Dosya temaya özgü kaynak sözlük dosyalarıyla aynı klasörde bulunur. Ancak `generic.xaml` gelmediğinden belirli bir Windows teması için hala bir tema düzeyinde sözlüktür.  
  
 [NumericUpDown özel denetim teması ve UI Otomasyon desteği örnek](https://go.microsoft.com/fwlink/?LinkID=160025) iki kaynak sözlükleri için içeren `NumericUpDown` denetimi: generic.xaml içinde biridir ve Luna.NormalColor.xaml biridir.  Uygulamayı çalıştırmak ve Windows XP'de Gümüş tema ve iki denetim şablonları arasındaki farkı görmek için başka bir tema arasında geçiş yapabilirsiniz. (Windows Vista çalıştırıyorsanız, Luna.NormalColor.xaml Aero.NormalColor.xaml ve klasik Windows gibi iki tema ile varsayılan tema arasında geçiş için Windows Vista için yeniden adlandırabilirsiniz.)  
  
 Yerleştirdiğinizde bir <xref:System.Windows.Controls.ControlTemplate> temaya özgü kaynak sözlük dosyaların hiçbirinde denetimi ve arama için statik bir oluşturucu oluşturmalısınız <xref:System.Windows.DependencyProperty.OverrideMetadata%28System.Type%2CSystem.Windows.PropertyMetadata%29> metodunda <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>, aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-csharp[CustomControlNumericUpDownOneProject#StaticConstructor](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/CSharp/NumericUpDown.cs#staticconstructor)]
 [!code-vb[CustomControlNumericUpDownOneProject#StaticConstructor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/visualbasic/numericupdown.vb#staticconstructor)]  
  
##### <a name="defining-and-referencing-keys-for-theme-resources"></a>Tanımlama ve tema kaynakları için anahtarları başvurma  
 Öğe düzeyinde bir kaynak tanımladığınızda, bir dize olarak anahtarıyla atayabilir ve kaynak dizesi aracılığıyla erişin. Bir kaynak tema düzeyinde tanımladığınızda, kullanmalısınız bir <xref:System.Windows.ComponentResourceKey> anahtar.  Aşağıdaki örnek, bir kaynak generic.xaml içinde tanımlar.  
  
 [!code-xaml[ThemeResourcesControlLibrary#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/Themes/generic.xaml#5)]  
  
 Aşağıdaki örnek, belirterek kaynağa başvuruda <xref:System.Windows.ComponentResourceKey> anahtar.  
  
 [!code-xaml[ThemeResourcesControlLibrary#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/NumericUpDown.xaml#6)]  
  
##### <a name="specifying-the-location-of-theme-resources"></a>Tema kaynakların konumunu belirtme  
 Bir denetim için kaynakları bulmak için barındırma uygulaması derlemeyi denetime özgü kaynakları içeren bilmesi gerekir. Ekleyerek, gerçekleştirebilirsiniz <xref:System.Windows.ThemeInfoAttribute> denetimi içeren derleme. <xref:System.Windows.ThemeInfoAttribute> Sahip bir <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> Genel kaynaklar konumunu belirten özellik ve <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A> temaya özgü kaynak konumunu belirten özelliği.  
  
 Aşağıdaki örnek kümeleri <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> ve <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A> özelliklerine <xref:System.Windows.ResourceDictionaryLocation.SourceAssembly>, genel ve temaya özgü kaynak denetimi ile aynı bütünleştirilmiş kod olduğunu belirtmek için.  
  
 [!code-csharp[CustomControlNumericUpDown#ThemesSection](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/Properties/AssemblyInfo.cs#themessection)]
 [!code-vb[CustomControlNumericUpDown#ThemesSection](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/my project/assemblyinfo.vb#themessection)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio’da XAML tasarlama](/visualstudio/designers/designing-xaml-in-visual-studio)
- [WPF İçinde URI'leri Paketleme](../app-development/pack-uris-in-wpf.md)
- [Denetim Özelleştirme](control-customization.md)
