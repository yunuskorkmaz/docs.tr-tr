---
title: Denetimlerde Odak için Stil Oluşturma ve FocusVisualStyle
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard focus [WPF]
- focus [WPF], visual styling
- styles [WPF], focus visual style
ms.assetid: 786ac576-011b-4d72-913b-558deccb9b35
ms.openlocfilehash: 07dd5f015624e934ceb4fd38f23f7e780d185dfc
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43672637"
---
# <a name="styling-for-focus-in-controls-and-focusvisualstyle"></a>Denetimlerde Odak için Stil Oluşturma ve FocusVisualStyle
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] klavye odağı aldığında, bir denetimin görünümünü değiştirmek için iki paralel mekanizmaları sağlar. Gibi özellikler için özellik ayarlayıcılarına kullanılacak ilk mekanizmadır <xref:System.Windows.UIElement.IsKeyboardFocused%2A> stil veya denetime uygulanan şablon içinde. Değeri olarak ayrı bir stil sağlamak için ikinci mekanizmadır <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> özelliği; "odak görsel stili" denetimi, üstünde denetimi veya diğer kullanıcı Arabirimi görsel ağacını değiştirmek yerine çizen donatıcı için ayrı bir görsel ağaç oluşturur Bunu değiştirerek öğesi. Bu konuda, bu mekanizmaların her biri uygun olduğu senaryolar açıklanmaktadır.  
   
  
<a name="Purpose"></a>   
## <a name="the-purpose-of-focus-visual-style"></a>Odak görsel stili amacı  
 Odak görsel stili özelliği, klavye ile gezinme herhangi bir kullanıcı Arabirimi öğesi için temel görsel kullanıcı geri bildirim tanıtımı için ortak bir "nesne modeli" sağlar. Bu, yeni şablonu denetime uygulamak veya belirli bir şablon oluşturmayı bilmeden olmadan mümkün olur.  
  
 Bununla birlikte, denetim şablonları bilmeden odak görsel stili özelliği tam olarak çalıştığı için odak görsel stili kullanan bir denetim için görüntülenen görsel geri bildirim mutlaka sınırlıdır. Özelliğin gerçekten ne yaptığını denetimin işleyerek, kendi şablon aracılığıyla oluşturulan görsel ağacı üzerinde farklı görsel ağaç (donatıcı) yardımcı olmaktır. Bu ayrı görsel ağacı dolduran bir stil kullanarak tanımladığınız <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> özelliği.  
  
<a name="Default"></a>   
## <a name="default-focus-visual-style-behavior"></a>Odak görsel stili davranışı  
 Yalnızca odak eylemi klavye tarafından başlatıldığı zaman, odak görsel stilleri işlevi görür. Fare eylemi veya programlama odak değişiklik görsel stilleri odak modunu devre dışı bırakır. Odak Modu arasındaki farklılıklar hakkında daha fazla bilgi için bkz. [odağa genel bakış](../../../../docs/framework/wpf/advanced/focus-overview.md).  
  
 Denetimlerin temaları temayı tüm denetimlerde odak görsel stili olur bir varsayılan odak görsel stili davranışını içerir. Bu tema stili statik anahtar değeri tarafından tanımlanan <xref:System.Windows.SystemParameters.FocusVisualStyleKey%2A>. Uygulama düzeyinde kendi odak görsel stili bildirdiğinizde, bu varsayılan stili davranışı temalardan değiştirin. Tüm tema tanımlarsanız, alternatif olarak, ardından bu anahtarı tüm tema için varsayılan davranışı stil tanımlamak için kullanmanız gerekir.  
  
 Temalar, varsayılan odak görsel stili genellikle çok basit bir işlemdir. Yaklaşık bir tahmin verilmiştir:  
  
```xaml  
<Style x:Key="{x:Static SystemParameters.FocusVisualStyleKey}">  
  <Setter Property="Control.Template">  
    <Setter.Value>  
      <ControlTemplate>  
        <Rectangle StrokeThickness="1"  
          Stroke="Black"  
          StrokeDashArray="1 2"  
          SnapsToDevicePixels="true"/>  
      </ControlTemplate>  
    </Setter.Value>  
  </Setter>  
</Style>  
```  
  
<a name="When"></a>   
## <a name="when-to-use-focus-visual-styles"></a>Odak görsel stilleri kullanmak ne zaman  
 Kavramsal olarak, denetimi başka bir denetim odağı görsel stilleri denetimlere uygulanan görünümünü tutarlı olmalıdır. Burada tema içinde tanımlanan her denetimi çok aynı odak görsel stili ya da bir stil bazı çeşitlemesi alır, tüm bir temayı oluşturuyorsanız görsel stil görsel olarak ilgili olan denetiminden sürekli teslim için değiştirmek için modellenmiş emin olmanın bir yolu olan Rol. Alternatif olarak, aynı stili (veya benzer stilleri) klavye odaklanabilir her öğe bir sayfa ya da bir kullanıcı Arabirimi stilini belirlemek için kullanabilirsiniz.  
  
 Ayar <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> tema parçası olmayan tek denetim stilleri değil hedeflenen odak görsel stilleri kullanımdır. Denetimler arasındaki tutarsız bir görsel davranışını klavye odağı ilgili karmaşık bir kullanıcı deneyimine yol açabilir olmasıdır. Bir tema arasında kasıtlı olarak değil klavye odağı için özel denetim davranışlarını amaçlanıyorsa, bir daha iyi bir yaklaşımdır Tetikleyicileri stillerde tek giriş durumu özelliklerinin gibi kullanmaktır <xref:System.Windows.UIElement.IsFocused%2A> veya <xref:System.Windows.UIElement.IsKeyboardFocused%2A>.  
  
 Odak görsel stilleri klavye odağını özel olarak davranır. Bu nedenle, odak görsel stilleri bir erişilebilirlik özelliği türüdür. Fare odak noktası, herhangi bir türü için UI değişikliklerin istiyorsanız, klavye, veya programlı olarak odak görsel stilleri kullanmamanız gerekir ve bunun yerine, ayarlayıcılar ve stilleri veya şablonları genel odak özelliklerinin değerden çalıştığınız Tetikleyicileri kullanmanız gerekir gibi <xref:System.Windows.UIElement.IsFocused%2A> veya <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>.  
  
<a name="How"></a>   
## <a name="how-to-create-a-focus-visual-style"></a>Odak görsel stili oluşturma  
 Odak görsel stili her zaman olmalıdır için oluşturduğunuz stili <xref:System.Windows.Style.TargetType%2A> , <xref:System.Windows.Controls.Control>. Stil çoğunlukla oluşmalıdır bir <xref:System.Windows.Controls.ControlTemplate>. Hedef türü burada odak görsel stili atanır türünde belirtmeyin <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>.  
  
 Hedef türü her zaman olduğundan <xref:System.Windows.Controls.Control>, tüm denetimler için ortak olan özellikleri'ni kullanarak stil gerekir (özelliklerini kullanarak <xref:System.Windows.Controls.Control> sınıfı ve temel sınıfları). Bir kullanıcı Arabirimi öğesi için bir kaplama olarak düzgün çalışmaz ve bu denetimin işlevsel alanları gizlememeniz değil bir şablon oluşturmanız gerekir. Genellikle, bu görsel geri bildirim denetimi isabet sınaması engellemez geçici ya da örtük efektleri ya da Denetim kenar boşluklarını dışında odak görsel stili uygulandığı görüntüleneceğini anlamına gelir. Boyutlandırma ve konumlandırma paylaşımı şablonunuzun belirlemek için yararlıdır, şablon bağlama kullanabileceğiniz özellikleri içeren <xref:System.Windows.FrameworkElement.ActualHeight%2A>, <xref:System.Windows.FrameworkElement.ActualWidth%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, ve <xref:System.Windows.Controls.Control.Padding%2A>.  
  
<a name="Alternatives"></a>   
## <a name="alternatives-to-using-a-focus-visual-style"></a>Odak görsel stili kullanımına alternatifler  
 Odak görsel stili kullanarak yalnızca tek denetimleri stillendirme olduğundan veya büyük denetim şablonu denetime istediğinden değil uygun olduğu durumlarda, vardır diğer birçok erişilebilir özellikler ve görsel olarak oluşturabilirsiniz teknikleri Odak değişikliklere yanıt davranışı.  
  
 Tetikleyiciler ve ayarlayıcılar olay ayarlayıcılar ele alınmıştır ayrıntılı olarak [stil ve şablon oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md). Yönlendirilmiş olay işleme ele alınmıştır [yönlendirilmiş olaylara genel bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
### <a name="iskeyboardfocused"></a>IsKeyboardFocused  
 Klavye odağı özellikle ilgileniyorsanız <xref:System.Windows.UIElement.IsKeyboardFocused%2A> bağımlılık özelliği için bir özellik kullanılabilir <xref:System.Windows.Trigger>. Bir stil veya şablon içinde bir özellik tetikleyicisi, özellikle çok tek bir denetim için ve hangi görsel olarak diğer denetimlerin klavye odağı davranışı eşleşmeyebilir bir klavye odağı davranışını tanımlamak için daha uygun bir tekniktir.  
  
 Başka bir benzer bağımlılık özelliği <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>, hangi görsel olarak, klavye odağının aramak istediğiniz durumlarda kullanmak üzere yere işlevsel alan denetimi veya birleştirme içinde uygundur. Örneğin, yerleştirebilirsiniz bir <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> klavye odağı daha kesin olsa bile çeşitli denetimler gruplandıran bir paneli farklı şekilde görüntülenir, tetikleyici olmalıdır, panel içinde tek bir öğe üzerinde.  
  
 Olayları kullanabilirsiniz <xref:System.Windows.UIElement.GotKeyboardFocus> ve <xref:System.Windows.UIElement.LostKeyboardFocus> (yanı sıra Önizleme eşdeğerleri). Bu olaylar için temel olarak kullanabileceğiniz bir <xref:System.Windows.EventSetter>, veya kod arka plan olayları için işleyiciler yazabilirsiniz.  
  
### <a name="other-focus-properties"></a>Diğer odak özellikleri  
 Görsel bir davranış üretmek için odak değiştirme tüm olası nedenlerini istiyorsanız, temel bir ayarlayıcı veya tetiklenecek <xref:System.Windows.UIElement.IsFocused%2A> bağımlılık özelliği veya alternatif olarak üzerinde <xref:System.Windows.UIElement.GotFocus> veya <xref:System.Windows.UIElement.LostFocus> olaylar için kullanılan bir <xref:System.Windows.EventSetter>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>  
 [Stil ve Şablon Oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Odağa Genel Bakış](../../../../docs/framework/wpf/advanced/focus-overview.md)  
 [Girişe Genel Bakış](../../../../docs/framework/wpf/advanced/input-overview.md)
