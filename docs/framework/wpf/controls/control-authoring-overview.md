---
title: "Denetim Yazımına Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], authoring overview
- authoring overview for controls [WPF]
ms.assetid: 3d864748-cff0-4e63-9b23-d8e5a635b28f
caps.latest.revision: "32"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f9290c249ed85ffc1fe98878daf2c2f0777786f5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="control-authoring-overview"></a>Denetim Yazımına Genel Bakış
Genişletilmesinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] denetim modeli yeni bir denetim oluşturmak için gereken önemli ölçüde azaltır. Ancak, bazı durumlarda, hala özel bir denetim oluşturmak gerekebilir. Bu konuda bir özel denetim ve farklı denetim yazma modellerini oluşturma gereksiniminizi en aza özellikleri ele alınmıştır [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Bu konu ayrıca yeni bir denetimin nasıl oluşturulacağını gösterir.  
  
 
  
<a name="when_to_write_a_new_control"></a>   
## <a name="alternatives-to-writing-a-new-control"></a>Yeni bir denetim yazma alternatifleri  
 Tarihsel olarak, özelleştirilmiş bir deneyim varolan denetimden almak istiyorsanız, denetimin arka plan rengi, kenarlık genişliği ve yazı tipi boyutu gibi standart özelliklerini değiştirmek için sınırlı olmadığınız. Bu önceden tanımlanmış parametrelerin dışında denetimin davranışını veya görünümünü genişletmek istediğinizde, yeni bir denetim genellikle varolan denetimden devralma ve denetim çizim için sorumlu yöntemi geçersiz kılma tarafından oluşturmanız gerekir.  Bu seçenek, hala olsa [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zengin içerik modeli, stiller, şablonları ve Tetikleyicileri kullanarak mevcut denetimleri özelleştirmenizi, sağlar. Aşağıdaki listede, yeni bir denetim oluşturmak zorunda kalmadan özel ve tutarlı deneyimleri oluşturmak için bu özellikleri'nın nasıl kullanılabileceğini örnekler verilmektedir.  
  
-   **Rich Content.** Çoğu standart [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimleri Zengin içeriği destekler. Örneğin, içerik özelliği bir <xref:System.Windows.Controls.Button> türü <xref:System.Object>, bu nedenle teorik olarak herhangi bir şey görüntülenebilir üzerinde bir <xref:System.Windows.Controls.Button>.  Bir resim ve metin görüntüleme bir düğmeye sahip olmak için bir görüntü ekleyebilirsiniz ve <xref:System.Windows.Controls.TextBlock> için bir <xref:System.Windows.Controls.StackPanel> ve Ata <xref:System.Windows.Controls.StackPanel> için <xref:System.Windows.Controls.ContentControl.Content%2A> özelliği. Çünkü denetimleri görüntüleyebilir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] görsel öğelerini ve rasgele verileri, yeni bir denetim oluşturma veya karmaşık bir görsel öğe desteklemek için varolan denetimi değiştirme daha az gereksinimi yoktur. İçin içerik modeli hakkında daha fazla bilgi için <xref:System.Windows.Controls.Button> ve diğer içerik modelleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bkz: [WPF içeriği modeli](../../../../docs/framework/wpf/controls/wpf-content-model.md).  
  
-   **Stilleri.** A <xref:System.Windows.Style> denetimin özelliklerini temsil eden değerleri koleksiyonudur. Stilleri kullanarak yeni bir denetim yazmadan istenen denetim görünümü ve davranışı yeniden kullanılabilir bir gösterimini oluşturabilirsiniz. Örneğin, tüm istediğinizi varsayalım, <xref:System.Windows.Controls.TextBlock> 14 yazı tipi boyutunu kırmızı, Arial yazı tipi için denetimleri. Bir kaynak olarak bir stil oluşturun ve uygun özellikleri uygun şekilde ayarlayın. Sonra her <xref:System.Windows.Controls.TextBlock> uygulamanıza eklemek aynı görünüme sahip olur.  
  
-   **Veri şablonları.** A <xref:System.Windows.DataTemplate> , verilerin bir denetimde nasıl görüntüleneceğini özelleştirmenizi sağlar. Örneğin, bir <xref:System.Windows.DataTemplate> verinin nasıl görüntüleneceğini belirtmek için kullanılan bir <xref:System.Windows.Controls.ListBox>.  Bu örneği için bkz: [veri şablonu özeti](../../../../docs/framework/wpf/data/data-templating-overview.md).  Veri görünümünü özelleştirme yanı sıra bir <xref:System.Windows.DataTemplate> , büyük bir esnekliğe içinde özel Uı'lar sağlayan kullanıcı Arabirimi öğeleri içerebilir.  Kullanarak örneğin, bir <xref:System.Windows.DataTemplate>, oluşturabileceğiniz bir <xref:System.Windows.Controls.ComboBox> içinde bir onay kutusu her bir öğe içeriyor.  
  
-   **Denetim şablonları.** Birçok denetimlerinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullanan bir <xref:System.Windows.Controls.ControlTemplate> denetimin yapısı ve denetim işlevinden denetimin görünümünü ayıran görünümünü tanımlamak için. Tanımlayarak büyük ölçüde denetiminin görünümünü değiştirebilirsiniz kendi <xref:System.Windows.Controls.ControlTemplate>.  Örneğin, trafik ışığı gibi görünen bir denetim istediğinizi varsayalım. Bu denetim, bir basit bir kullanıcı arabirimi ve işlevselliği vardır.  Aynı anda yalnızca biri yanabildiği üç daire denetimdir. Bazı yansıma sonra fark edebilirsiniz bir <xref:System.Windows.Controls.RadioButton> tek bir zaman, ancak varsayılan görünümünü seçilmesini işlevselliği sunduğunu <xref:System.Windows.Controls.RadioButton> ışık Durma ışığı üzerinde hiçbir şey yok gibi görünüyor.  Çünkü <xref:System.Windows.Controls.RadioButton> hizmetin görünümünü tanımlamak için bir denetim şablonu kullanan tanımlanacak kolaydır <xref:System.Windows.Controls.ControlTemplate> denetimi gereksinimlere uygun ve radyo düğmeleri, trafik ışığı yapmak için kullanın.  
  
    > [!NOTE]
    >  Ancak bir <xref:System.Windows.Controls.RadioButton> kullanabileceğiniz bir <xref:System.Windows.DataTemplate>, <xref:System.Windows.DataTemplate> Bu örnekte yeterli değil.  <xref:System.Windows.DataTemplate> Denetim içeriğinin görünümünü tanımlar. Durumunda bir <xref:System.Windows.Controls.RadioButton>, içeriği ne olursa olsun gösteren dairenin sağında görünür olan olup olmadığını <xref:System.Windows.Controls.RadioButton> seçilir.  Trafik ışığı örnekte yalnızca "ışık ayarlama." bir daire olması radyo düğmesi gerekir. Trafik ışığı görünüm gereksinimini varsayılan görünümünü çok farklı olduğundan <xref:System.Windows.Controls.RadioButton>, yeniden tanımlamak gerekli olan <xref:System.Windows.Controls.ControlTemplate>.  Genel bir <xref:System.Windows.DataTemplate> bir denetim ve bir içerik (veri ya da) tanımlamak için kullanılan <xref:System.Windows.Controls.ControlTemplate> denetimin nasıl yapılandırılacağını tanımlamak için kullanılır.  
  
-   **Tetikler.** A <xref:System.Windows.Trigger> yeni bir denetim oluşturmadan görünümünü ve davranışını dinamik olarak değiştirmenize olanak tanır. Örneğin, birden çok olduğunu varsayalım <xref:System.Windows.Controls.ListBox> uygulamanızda denetimleri ve her öğe istiyorsanız <xref:System.Windows.Controls.ListBox> seçildiklerinde kalın ve kırmızı olmalıdır. Öğesinden devralınan bir sınıf oluşturmak için ilk olarak olabilir <xref:System.Windows.Controls.ListBox> ve geçersiz kılma <xref:System.Windows.Controls.Primitives.Selector.OnSelectionChanged%2A> seçilen öğe, ancak daha iyi bir yaklaşım görünümünü değiştirmek için yöntemdir tetikleyici için bir stil eklemek için bir <xref:System.Windows.Controls.ListBoxItem> görünümünü değiştirir Seçili öğe. Bir tetikleyici, özellik değerlerini değiştirmek veya bir özelliğin değerini bağlı eylemleri olanak sağlar. Bir <xref:System.Windows.EventTrigger> bir olay gerçekleştiğinde Eylemler duruma getirmenizi sağlar.  
  
 Stil, şablonları ve tetikleyiciler hakkında daha fazla bilgi için bkz: [stil ve şablon](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
 Genel olarak, varolan bir denetim işlevselliğini denetiminizi yansıtan ancak farklı aramak için denetim istiyorsanız, önce bu bölümde açıklanan yöntemlerden herhangi birini varolan denetimin görünümünü değiştirmek için kullanıp kullanamayacağını düşünmelisiniz.  
  
<a name="models_for_control_authoring"></a>   
## <a name="models-for-control-authoring"></a>Denetim yazma modelleri  
 Zengin içerik modeli, stiller, şablonlar ve tetikleyiciler yeni bir denetim oluşturmak için gereken en aza indirin. Yeni bir denetim oluşturmanız gerekiyorsa, ancak, farklı denetim yazma modellerini anlaşılması önemlidir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]her biri farklı bir özellikler kümesi ve esneklik düzeyi sağlayan bir denetim oluşturmak için üç genel modeli sağlar. Temel sınıflar için üç modeli <xref:System.Windows.Controls.UserControl>, <xref:System.Windows.Controls.Control>, ve <xref:System.Windows.FrameworkElement>.  
  
### <a name="deriving-from-usercontrol"></a>UserControl türetme  
 Bir denetim oluşturmak için en basit yolu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğesinden türetilen için <xref:System.Windows.Controls.UserControl>. Bir denetim oluşturduğunuzda devraldığı <xref:System.Windows.Controls.UserControl>, var olan bileşenleri eklemek <xref:System.Windows.Controls.UserControl>bileşenleri adını ve olay işleyicileri başvuru [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Ardından, adlandırılmış öğelere başvurabilir ve kodda olay işleyicileri tanımlayın. Bu geliştirme modeli uygulama geliştirme için kullanılan modele çok benzer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Doğru bir şekilde, oluşturulduysa bir <xref:System.Windows.Controls.UserControl> zengin içerik, stil ve tetikleyicilerin avantajlarından yararlanabilir. Ancak, denetiminiz devraldığı varsa <xref:System.Windows.Controls.UserControl>, Denetim kullananlar kullanmanız mümkün olmayacak bir <xref:System.Windows.DataTemplate> veya <xref:System.Windows.Controls.ControlTemplate> görünümünü özelleştirmek için.  Öğesinden türetilen gereklidir <xref:System.Windows.Controls.Control> sınıf veya türetilmiş sınıflarından biri (dışında <xref:System.Windows.Controls.UserControl>) Şablonları destekleyen özel bir denetim oluşturmak için.  
  
#### <a name="benefits-of-deriving-from-usercontrol"></a>UserControl Türetmenin Yararları  
 Türetme göz önünde bulundurun <xref:System.Windows.Controls.UserControl> aşağıdakilerin tümü uygularsanız:  
  
-   Benzer şekilde nasıl bir uygulama oluşturmak için denetimi oluşturmak istiyorsunuz.  
  
-   Denetiminiz yalnızca mevcut bileşenden oluşur.  
  
-   Karmaşık özelleştirmeyi desteklemeniz gerekmez.  
  
### <a name="deriving-from-control"></a>Denetim türetme  
 Türetme <xref:System.Windows.Controls.Control> sınıfı, var olan çoğu tarafından kullanılan model [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrol eder. Bir denetim oluşturduğunuzda devraldığı <xref:System.Windows.Controls.Control> sınıfı, tanımladığınız görünümünü şablonları kullanarak. Bunu yaparak, görsel gösterimden çalışma mantığını ayırın. UI ve mantık olayları ve kaçınarak başvuru öğelerinde yerine komutlarını ve bağlamaları kullanarak kesilmesi sağlayabilirsiniz <xref:System.Windows.Controls.ControlTemplate> mümkün olduğunda.  Denetiminizin mantığı ve UI düzgün ayrılmış varsa, bir kullanıcı denetiminizin denetimin tanımlayabilirsiniz <xref:System.Windows.Controls.ControlTemplate> görünümünü özelleştirmek için. Özel derleme rağmen <xref:System.Windows.Controls.Control> oluşturma kadar basit değil bir <xref:System.Windows.Controls.UserControl>, özel bir <xref:System.Windows.Controls.Control> en iyi esnekliği sağlar.  
  
#### <a name="benefits-of-deriving-from-control"></a>Denetim türetme avantajları  
 Türetme göz önünde bulundurun <xref:System.Windows.Controls.Control> kullanmak yerine <xref:System.Windows.Controls.UserControl> aşağıdaki durumlardan biri geçerliyse sınıfı:  
  
-   Denetim aracılığıyla özelleştirilebilir görünümünü istediğiniz <xref:System.Windows.Controls.ControlTemplate>.  
  
-   Farklı temaları desteklemek için denetim istiyor.  
  
### <a name="deriving-from-frameworkelement"></a>FrameworkElement türetme  
 Öğesinden türetilen denetimler <xref:System.Windows.Controls.UserControl> veya <xref:System.Windows.Controls.Control> varolan öğeleri birleştirmeye dayanır. Herhangi bir nesne, devraldığı birçok senaryo için kabul edilebilir bir çözüm olmasıdır <xref:System.Windows.FrameworkElement> olabilir bir <xref:System.Windows.Controls.ControlTemplate>. Ancak, ne zaman bir denetimin görünümünü birden çok basit bir öğe birleşim işlevselliğini gerektirdiği zamanlar vardır. Bu senaryolarda, üzerinde bir bileşen alma <xref:System.Windows.FrameworkElement> doğru seçimdir.  
  
 Derleme için standart iki yöntem vardır <xref:System.Windows.FrameworkElement>-bileşenlere dayalı: doğrudan işleme ve özel öğe oluşumu. İşleme içerir geçersiz kılma doğrudan <xref:System.Windows.UIElement.OnRender%2A> yöntemi <xref:System.Windows.FrameworkElement> ve sağlama <xref:System.Windows.Media.DrawingContext> bileşen görsellerini açıkça tanımlayan işlemleri. Tarafından kullanılan yöntem budur <xref:System.Windows.Controls.Image> ve <xref:System.Windows.Controls.Border>. Özel öğe birleşim içerir türünde nesneler kullanmayı <xref:System.Windows.Media.Visual> bileşeniniz görünümünü oluşturmak için. Bir örnek için bkz: [kullanarak DrawingVisual nesneleri](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md). <xref:System.Windows.Controls.Primitives.Track>bir denetimde örneğidir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özel öğe birleşim kullanır. Doğrudan işleme ve aynı denetimi özel öğe birleşimde karıştırmak mümkündür.  
  
#### <a name="benefits-of-deriving-from-frameworkelement"></a>FrameworkElement Türetmenin Yararları  
 Türetme göz önünde bulundurun <xref:System.Windows.FrameworkElement> aşağıdaki durumlardan biri geçerliyse:  
  
-   Basit öğe oluşumu tarafından sağlanan ötesinde, denetimin görünümünü üzerinde tam denetime sahip olmasını istiyor.  
  
-   Kendi işleme mantığınızı tanımlayarak, denetimin görünümünü tanımlamak istersiniz.  
  
-   Ne mümkün olanın ötesinde yeni yollar içinde varolan öğeleri oluşturmak istediğiniz <xref:System.Windows.Controls.UserControl> ve <xref:System.Windows.Controls.Control>.  
  
<a name="control_authoring_basics"></a>   
## <a name="control-authoring-basics"></a>Denetim temelleri yazma  
 En güçlü özelliklerinden biri daha önce bahsedildiği gibi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yeteneği görünümünü ve davranışını değiştirmek için bir denetim temel özelliklerini ayarlama, ancak hala özel bir denetim oluşturmak zorunda kalmamanız ötesine gidin. Stil, veri bağlama ve tetikleyici özellikleri tarafından gerçekleştirilebilen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellik sistemi ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olay sistemi. İzlemeniz gereken bazı yöntemler aşağıdaki bölümlerde, tıpkı ile birlikte bir denetim için olduğu gibi özel denetim kullanıcılarının bu özellikleri kullanabilmesi için model bağımsız olarak özel bir denetim oluşturmak için kullandığınız [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="use-dependency-properties"></a>Bağımlılık özelliklerini kullanma  
 Bir özellik bağımlılık özelliği olduğunda, aşağıdakileri mümkündür:  
  
-   Bir stil özelliğini ayarlayın.  
  
-   Özelliği bir veri kaynağına bağlama.  
  
-   Dinamik bir kaynak özelliğinin değeri olarak kullanın.  
  
-   Özellik animasyon.  
  
 Bu işlevselliği desteklemek için denetim özelliğini istiyorsanız, bir bağımlılık özelliği olarak uygulamanız gerekir. Aşağıdaki örnek, adlandırılmış bir bağımlılık özelliği tanımlar `Value` aşağıdakileri yaparak:  
  
-   Tanımlayan bir <xref:System.Windows.DependencyProperty> adlı tanımlayıcı `ValueProperty` olarak bir `public` `static` `readonly` alan.  
  
-   Özellik adı çağırarak özellik sistemi ile kaydedin <xref:System.Windows.DependencyProperty.Register%2A?displayProperty=nameWithType>, aşağıdakileri belirtin:  
  
    -   Özelliğin adı.  
  
    -   Özelliğin türü.  
  
    -   Özellik sahibi türü.  
  
    -   Özellik için meta veriler. Özelliğin varsayılan değeri, meta veriler içeren bir <xref:System.Windows.CoerceValueCallback> ve <xref:System.Windows.PropertyChangedCallback>.  
  
-   Tanımlayan bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] adlı sarmalayıcı özellik `Value`, bağımlılık özelliği Özelliğin uygulayarak kaydetmek için kullanılan aynı adı `get` ve `set` erişimciler. Unutmayın `get` ve `set` erişimciler yalnızca çağrısı <xref:System.Windows.DependencyObject.GetValue%2A> ve <xref:System.Windows.DependencyObject.SetValue%2A> sırasıyla. Bağımlılık özellikleri erişimciler ek mantık içermemesi önerilir istemcileri ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] erişimciler ve çağrı atlayabilir <xref:System.Windows.DependencyObject.GetValue%2A> ve <xref:System.Windows.DependencyObject.SetValue%2A> doğrudan. Örneğin, bir özellik için bir veri bağlandığında kaynağı, özelliğin `set` erişimci çağrılmaz.  Get için ilave bir mantık eklemek yerine ve ayarlama erişimcileri, kullanma <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.CoerceValueCallback>, ve <xref:System.Windows.PropertyChangedCallback> temsilciler yanıt vermesi veya değişiklik yapıldığında değerini denetleyin.  Bu geri aramalar hakkında daha fazla bilgi için bkz: [bağımlılık özelliği geri çağrıları ve doğrulama](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md).  
  
-   Bir yöntemi tanımlamak <xref:System.Windows.CoerceValueCallback> adlı `CoerceValue`. `CoerceValue`sağlar `Value` büyük veya eşittir `MinValue` ve küçük veya eşit `MaxValue`.  
  
-   Bir yöntemi tanımlamak <xref:System.Windows.PropertyChangedCallback>, adlandırılmış `OnValueChanged`. `OnValueChanged`oluşturur bir <xref:System.Windows.RoutedPropertyChangedEventArgs%601> nesne ve yükseltmek hazırlar `ValueChanged` yönlendirilmiş olay. Yönlendirilmiş olaylar sonraki bölümde açıklanmıştır.  
  
 [!code-csharp[UserControlNumericUpDown#DependencyProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#dependencyproperty)]
 [!code-vb[UserControlNumericUpDown#DependencyProperty](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#dependencyproperty)]  
  
 Daha fazla bilgi için bkz: [özel bağımlılık özellikleri](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).  
  
### <a name="use-routed-events"></a>Yönlendirilmiş olayları kullanma  
 Bağımlılık olarak kavramı özellikleri genişletmek [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] özellikleri ek işlevsellik ile yönlendirilmiş olaylar genişletmek standart kavramı [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] olaylar. Yeni bir oluşturduğunuzda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] onu denetimidir ayrıca yönlendirilmiş olay aşağıdaki davranış desteklediğinden, olay yönlendirilmiş olay olarak uygulamak için iyi bir uygulama:  
  
-   Olaylar birden çok denetim üst öğe üzerinde işlenebilir. Bir olay kabarcıklanma olayı ise, öğe ağacında tek bir üst olaya abone olabilirsiniz. Daha sonra uygulama yazarları birden çok denetim olaya yanıt için bir işleyici kullanabilirsiniz. Örneğin, denetiminiz her öğe bir parçası ise bir <xref:System.Windows.Controls.ListBox> (içinde yer aldığından bir <xref:System.Windows.DataTemplate>), uygulama geliştiricisi üzerinde denetiminizin olay için olay işleyicisini tanımlayabilir <xref:System.Windows.Controls.ListBox>. Olay denetimleri hiçbirinde oluştuğunda, olay işleyicisi çağrılır.  
  
-   Yönlendirilmiş olaylar kullanılabilir bir <xref:System.Windows.EventSetter>, uygulama geliştiricilerinin stil içinde bir olay işleyicisi belirtmelerini sağlar.  
  
-   Yönlendirilmiş olaylar kullanılabilir bir <xref:System.Windows.EventTrigger>, özellikleri kullanarak animasyon için yararlı olan [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Daha fazla bilgi için bkz: [animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 Aşağıdaki örnekte, aşağıdakileri yaparak yönlendirilmiş olay tanımlar:  
  
-   Tanımlayan bir <xref:System.Windows.RoutedEvent> adlı tanımlayıcı `ValueChangedEvent` olarak bir `public` `static` `readonly` alan.  
  
-   Yönlendirilmiş olay çağırarak kaydedin <xref:System.Windows.EventManager.RegisterRoutedEvent%2A?displayProperty=nameWithType> yöntemi. Çağırdığında örnek şunu belirtir <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>:  
  
    -   Olay adı `ValueChanged`.  
  
    -   Yönlendirme stratejisi olduğu <xref:System.Windows.RoutingStrategy.Bubble>anlamına gelir (olayını nesnesi) kaynak üzerinde bir olay işleyicisi ilk olarak adlandırılır ve ardından art arda en yakın üzerinde olay işleyicisi ile başlayarak, kaynağın üst öğeler üzerinde olay işleyicileri olarak adlandırılır üst öğe.  
  
    -   Olay işleyicisinin türü <xref:System.Windows.RoutedPropertyChangedEventHandler%601>, ile oluşturulan bir <xref:System.Decimal> türü.  
  
    -   Sahibi olan olay türüdür `NumericUpDown`.  
  
-   Adlı bir ortak olay bildirme `ValueChanged` ve olay erişimcisi bildirimlerini içerir. Örnek aramalar <xref:System.Windows.UIElement.AddHandler%2A> içinde `add` erişimcisi bildirimi ve <xref:System.Windows.UIElement.RemoveHandler%2A> içinde `remove` kullanmak için erişimcisi bildirimi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olay Hizmetleri.  
  
-   Adlı korumalı, sanal bir yöntem oluşturma `OnValueChanged` olayını `ValueChanged` olay.  
  
 [!code-csharp[UserControlNumericUpDown#RoutedEvent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#routedevent)]
 [!code-vb[UserControlNumericUpDown#RoutedEvent](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#routedevent)]  
  
 Daha fazla bilgi için bkz: [yönlendirilmiş olaylara genel bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md) ve [özel yönlendirilmiş bir olay oluşturma](../../../../docs/framework/wpf/advanced/how-to-create-a-custom-routed-event.md).  
  
### <a name="use-binding"></a>Bağlama kullanın  
 Mantığından denetiminizin UI aynı şekilde veri bağlamasını kullanmayı düşünün. Bu, denetimin görünümünü kullanarak tanımlarsanız, özellikle önemlidir bir <xref:System.Windows.Controls.ControlTemplate>. Veri bağlama kullandığınızda, UI belirli kısımlarını koddan başvuru gereğini ortadan kaldırmak mümkün olabilir. Bulunan öğelere başvurma önlemek için iyi bir fikirdir <xref:System.Windows.Controls.ControlTemplate> zaman kodu bulunan öğeleri başvurduğundan <xref:System.Windows.Controls.ControlTemplate> ve <xref:System.Windows.Controls.ControlTemplate> değiştirildiğinde, yeni dahil edilecek başvurulan öğenin gereksinimlerini <xref:System.Windows.Controls.ControlTemplate>.  
  
 Aşağıdaki örnek güncelleştirmeleri <xref:System.Windows.Controls.TextBlock> , `NumericUpDown` bir ad atanarak ve kodda adı metin kutusuna başvurularak denetimi.  
  
 [!code-xaml[UserControlNumericUpDownSimple#UIRefMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml#uirefmarkup)]  
  
 [!code-csharp[UserControlNumericUpDownSimple#UIRefCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml.cs#uirefcode)]
 [!code-vb[UserControlNumericUpDownSimple#UIRefCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDownSimple/VisualBasic/NumericUpDown.xaml.vb#uirefcode)]  
  
 Aşağıdaki örnek, aynı şeyi başarmak için bağlama kullanır.  
  
 [!code-xaml[UserControlNumericUpDown#Binding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml#binding)]  
  
 Veri bağlama hakkında daha fazla bilgi için bkz: [veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
### <a name="design-for-designers"></a>Tasarımcılar için Tasarım  
 Özel WPF denetimleri için destek almak için [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] (örneğin, Özellikler penceresi ile düzenleme özelliği), aşağıdaki yönergeleri izleyin.  Geliştirme hakkında daha fazla bilgi için [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)], bkz: [WPF Tasarımcısı](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26).  
  
#### <a name="dependency-properties"></a>Bağımlılık özellikleri  
 Uygulamak mutlaka [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] `get` ve `set` "Kullanım bağımlılık özelliklerinde." daha önce açıklandığı gibi erişimciler Tasarımcılar bağımlılık özelliği, ancak bunlar, varlığını gibi algılamak için sarmalayıcı kullanabilirler [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve denetim istemcileri özelliği alırken veya ayarlarken erişimcileri çağırmak için gerekli değildir.  
  
#### <a name="attached-properties"></a>Ekli Özellikler  
 Ekli özellikler aşağıdaki yönergeleri kullanarak özel denetimler üzerinde uygulamanız gerekir:  
  
-   Sahip bir `public` `static` `readonly` <xref:System.Windows.DependencyProperty> formun *PropertyName* `Property` kullanarak sine <xref:System.Windows.DependencyProperty.RegisterAttached%2A> yöntemi. Geçirilir özellik adı <xref:System.Windows.DependencyProperty.RegisterAttached%2A> eşleşmelidir *PropertyName*.  
  
-   Bir çift uygulamak `public` `static` adlı CLR yöntemleri `Set` *PropertyName* ve `Get` *PropertyName*. Her iki yöntem de türetilmiş bir sınıf kabul etmelidir <xref:System.Windows.DependencyProperty> kendi ilk bağımsız değişken olarak. `Set` *PropertyName* yöntemi de, türü kayıtlı veri türü özelliği için eşleşen bir bağımsız değişken kabul eder. `Get` *PropertyName* yöntemi aynı türde bir değer döndürmelidir. Varsa `Set` *PropertyName* yöntemi eksik, özelliği salt okunur olarak işaretlenmiş.  
  
-   `Set`*PropertyName* ve `Get` *PropertyName* doğrudan rota gerekir <xref:System.Windows.DependencyObject.GetValue%2A> ve <xref:System.Windows.DependencyObject.SetValue%2A> sırasıyla hedef bağımlılık yöntemlere nesne. Tasarımcılar yöntem sarmalayıcısı aracılığıyla çağırarak veya hedef bağımlılık nesnesi doğrudan arama yaparak ekli özelliğe erişebilir.  
  
 Ekli özellikler hakkında daha fazla bilgi için bkz: [bağlı özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).  
  
### <a name="define-and-use-shared-resources"></a>Tanımlama ve kullanma paylaşılan kaynaklar  
 Uygulamanız ile aynı bütünleştirilmiş kodda denetiminizi içerebilir veya birçok uygulamada kullanılan ayrı bir derleme, denetiminde paketleyebilirsiniz. Çoğunlukla, bu konuda ele alınan bilgiler kullandığınız yönteminden bağımsız olarak uygulanır.  Bununla birlikte önemli bir fark yoktur.  Bir uygulama ile aynı bütünleştirilmiş kodda bir denetim geçirdiğinizde, genel kaynakları App.xaml dosyasına eklemek boş. Ancak yalnızca denetimleri içeren bir derleme sahip olmayan bir <xref:System.Windows.Application> App.xaml dosya kullanılamıyor şekilde onunla ilişkili nesne.  
  
 Bir uygulama için bir kaynak göründüğünde, üç düzeyde aşağıdaki sırayla arar:  
  
1.  Öğe düzeyi.  
  
     Sistem, kaynağa başvuran ve kök öğesi ulaşılana kadar mantıksal üst kaynakları vb. arar öğe ile başlar.  
  
2.  Uygulama düzeyi.  
  
     Tarafından tanımlanan kaynaklara <xref:System.Windows.Application> nesnesi.  
  
3.  Tema düzeyi.  
  
     Tema düzeyi sözlükler Temalar adlı alt klasörde depolanır.  Temalar klasöründeki dosyaları için Temalar karşılık gelir.  Örneğin, Aero.NormalColor.xaml, Luna.NormalColor.xaml, Royale.NormalColor.xaml vb. olabilir.  Generic.xaml adlı bir dosyaya da sahip olabilirsiniz.  Sistem Temalar düzeyinde bir kaynak için göründüğünde, ilk için özel tema dosyasında görünüyor ve bunun için generic.xaml içinde arar.  
  
 Denetiminiz uygulamadan ayrı bir derleme olduğunda, öğe düzeyinde veya tema düzeyinde genel kaynaklarınızı konulmalıdır. Her iki yöntem de kendi yararları vardır.  
  
#### <a name="defining-resources-at-the-element-level"></a>Öğe düzeyinde kaynakları tanımlama  
 Öğe düzeyinde paylaşılan kaynakları, özel bir kaynak sözlüğü oluşturarak ve denetiminizin kaynak sözlüğü ile birleştirerek tanımlayabilirsiniz.  Bu yöntemi kullandığınızda, istediğiniz herhangi bir şey ve onu denetimleri ile aynı klasörde olabilir, kaynak dosya adı verebilirsiniz. Öğe düzeyinde kaynakları, anahtarları olarak basit dizeleri de kullanabilirsiniz. Aşağıdaki örnekte bir <xref:System.Windows.Media.LinearGradientBrush> Dictionary1.xaml adlı kaynak dosya.  
  
 [!code-xaml[SharedResources#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/Dictionary1.xaml#1)]  
  
 Sözlük tanımladıktan sonra denetiminizin kaynak sözlüğü ile birleştirmeniz gerekir.  Kullanarak bunu yapabilirsiniz [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] veya kod.  
  
 Aşağıdaki örnekte bir kaynak sözlüğü kullanarak birleştirir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[SharedResources#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml#2)]  
  
 Bu yaklaşımın dezavantajı olan bir <xref:System.Windows.ResourceDictionary> nesnesi, bu başvuru her zaman oluşturulur.  Kitaplığınızdaki 10 özel denetim varsa ve her denetim için paylaşılan kaynak sözlüklerindeki XAML kullanarak birleştirmek, örneğin, 10 özdeş oluşturduğunuz <xref:System.Windows.ResourceDictionary> nesneleri.  Bu kodda kaynakları birleştiren ve sonuç döndüren statik bir sınıf oluşturarak kaçının <xref:System.Windows.ResourceDictionary>.  
  
 Aşağıdaki örnek, bir paylaşılan döndüren bir sınıf oluşturur <xref:System.Windows.ResourceDictionary>.  
  
 [!code-csharp[SharedResources#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/SharedDictionaryManager.cs#3)]  
  
 Aşağıdaki örnek çağırmadan önce denetimin oluşturucusunda özel bir denetim kaynaklarla paylaşılan kaynağı birleştirir `InitializeComponent`.  Çünkü `SharedDictionaryManager.SharedDictionary` bir statik özellik <xref:System.Windows.ResourceDictionary> yalnızca bir kez oluşturulur. Kaynak sözlüğü önce birleştirilmesinden dolayı `InitializeComponent` edildi adlı kaynaklar denetime kullanılabilir kendi [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya.  
  
 [!code-csharp[SharedResources#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml.cs#4)]  
  
#### <a name="defining-resources-at-the-theme-level"></a>Tema düzeyinde kaynakları tanımlama  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]farklı Windows temaları için kaynaklar oluşturmanızı sağlar.  Denetim yazarı olarak, hangi tema kullanımda bağlı olarak, denetimin görünümünü değiştirmek özel bir tema için bir kaynak tanımlayabilirsiniz. Örneğin, görünümünü bir <xref:System.Windows.Controls.Button> Windows Klasik tema (Windows 2000 için varsayılan tema) farklı bir <xref:System.Windows.Controls.Button> Windows Luna tema (Windows XP için varsayılan tema) içinde olduğundan <xref:System.Windows.Controls.Button> farklı bir kullanan <xref:System.Windows.Controls.ControlTemplate> her tema için.  
  
 Bir tema belirli kaynaklar bir kaynak sözlüğü belirli bir dosya adı ile korunur. Bu dosyalar adlı bir klasörde olmalıdır `Themes` diğer bir deyişle denetimi içeren klasörün bir alt. Aşağıdaki tabloda, kaynak sözlüğü dosyaları ve her dosya ile ilişkili tema listelenmektedir:  
  
|Kaynak sözlüğü dosya adı|Windows teması|  
|-----------------------------------|-------------------|  
|`Classic.xaml`|Klasik Windows 9 x / 2000, Windows XP arayın|  
|`Luna.NormalColor.xaml`|Windows XP'de varsayılan mavi tema|  
|`Luna.Homestead.xaml`|Windows XP Zeytin teması|  
|`Luna.Metallic.xaml`|Windows XP'de Gümüş tema|  
|`Royale.NormalColor.xaml`|Windows XP Media Center Edition'da varsayılan tema|  
|`Aero.NormalColor.xaml`|Windows Vista'da varsayılan tema|  
  
 Her tema için bir kaynak tanımlamak gerekmez. Bir kaynak için belirli bir tema tanımlanmazsa denetimi denetler `Classic.xaml` kaynak. Kaynağın geçerli tema veya buna karşılık gelen dosyasında tanımlı değilse, `Classic.xaml`, adlı bir kaynak sözlüğü dosyasında genel kaynak denetimi kullanır `generic.xaml`.  `generic.xaml` Dosya özel tema kaynak sözlüğü dosyaları aynı klasörde bulunur. Ancak `generic.xaml` karşılık gelmiyor belirli bir Windows teması için hala bir tema düzeyinde sözlük öyledir.  
  
 [Tema ve UI Otomasyon desteği örnek ile NumericUpDown özel denetimi](http://go.microsoft.com/fwlink/?LinkID=160025) için iki kaynak sözlük içeren `NumericUpDown` denetimi: generic.xaml içinde biridir ve Luna.NormalColor.xaml biridir.  Uygulamayı çalıştırın ve Windows XP'de Gümüş tema ve iki denetim şablonları arasındaki fark görmek için başka bir tema arasında geçiş yapabilirsiniz. (Windows Vista çalıştırıyorsanız, Luna.NormalColor.xaml Aero.NormalColor.xaml ve Windows Klasik gibi iki temalar ve varsayılan tema arasında geçiş için Windows Vista için yeniden adlandırabilirsiniz.)  
  
 Yerleştirdiğinizde bir <xref:System.Windows.Controls.ControlTemplate> herhangi özel tema kaynak sözlüğü dosyaları denetim ve çağrı için statik bir oluşturucu oluşturmalısınız <xref:System.Windows.DependencyProperty.OverrideMetadata%28System.Type%2CSystem.Windows.PropertyMetadata%29> yöntemi <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>, aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-csharp[CustomControlNumericUpDownOneProject#StaticConstructor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/CSharp/NumericUpDown.cs#staticconstructor)]
 [!code-vb[CustomControlNumericUpDownOneProject#StaticConstructor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/visualbasic/numericupdown.vb#staticconstructor)]  
  
##### <a name="defining-and-referencing-keys-for-theme-resources"></a>Tanımlama ve tema kaynakları için anahtarları başvurma  
 Öğe düzeyinde kaynak tanımladığınızda, anahtarı olarak bir dize atayabilir ve dize aracılığıyla kaynağa erişim. Tema düzeyinde kaynak tanımladığınızda, kullanmalısınız bir <xref:System.Windows.ComponentResourceKey> anahtar olarak.  Aşağıdaki örnek, bir kaynak generic.xaml içinde tanımlar.  
  
 [!code-xaml[ThemeResourcesControlLibrary#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/Themes/generic.xaml#5)]  
  
 Aşağıdaki örnek belirterek kaynağa başvuran <xref:System.Windows.ComponentResourceKey> anahtar olarak.  
  
 [!code-xaml[ThemeResourcesControlLibrary#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/NumericUpDown.xaml#6)]  
  
##### <a name="specifying-the-location-of-theme-resources"></a>Tema kaynaklarının konumunu belirtme  
 Bir denetim için kaynakları bulmak için barındırma uygulaması derleme denetime özgü kaynakları içeren bilmek ister. Ekleyerek yapabilirsiniz <xref:System.Windows.ThemeInfoAttribute> denetimi içeren derleme. <xref:System.Windows.ThemeInfoAttribute> Sahip bir <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> genel kaynakların konumunu belirten özellik ve <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A> temaya özgü kaynakların konumunu belirten özellik.  
  
 Aşağıdaki örnek kümeleri <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> ve <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A> özelliklerine <xref:System.Windows.ResourceDictionaryLocation.SourceAssembly>, genel ve özel tema kaynakları aynı bütünleştirilmiş kodda denetim olarak kullanılabilir olduğunu belirlemek için.  
  
 [!code-csharp[CustomControlNumericUpDown#ThemesSection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/Properties/AssemblyInfo.cs#themessection)]
 [!code-vb[CustomControlNumericUpDown#ThemesSection](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/my project/assemblyinfo.vb#themessection)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF Tasarımcısı](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [WPF İçinde URI'leri Paketleme](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)  
 [Denetim Özelleştirme](../../../../docs/framework/wpf/controls/control-customization.md)
