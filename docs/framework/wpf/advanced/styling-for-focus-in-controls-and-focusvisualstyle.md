---
title: "Denetimlerde Odak için Stil Oluşturma ve FocusVisualStyle"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- keyboard focus [WPF]
- focus [WPF], visual styling
- styles [WPF], focus visual style
ms.assetid: 786ac576-011b-4d72-913b-558deccb9b35
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4d29fda788aa4ec79ad4278beefa16ee14208832
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="styling-for-focus-in-controls-and-focusvisualstyle"></a>Denetimlerde Odak için Stil Oluşturma ve FocusVisualStyle
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]klavye odağı aldığında bir denetim görsel görünümünü değiştirmek için iki paralel mekanizma sağlar. Özellik ayarlayıcıları gibi özellikleri kullanmak için ilk mekanizmasıdır <xref:System.Windows.UIElement.IsKeyboardFocused%2A> stil veya denetime uygulanan şablon içinde. İkinci mekanizma değeri olarak ayrı bir stil sağlamaktır <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> özellik; "odak görsel stili" denetimi yerine üzerinde denetim ya da diğer UI görsel ağaç değiştirme çizer donatıcı için ayrı bir görsel ağaç oluşturur Bunu değiştirerek öğesi. Bu konuda, bu mekanizmaların her biri uygun olduğu senaryolar açıklanmaktadır.  
   
  
<a name="Purpose"></a>   
## <a name="the-purpose-of-focus-visual-style"></a>Odak görsel stili amacı  
 Odak görsel stil özelliği, klavye gezinti herhangi bir kullanıcı Arabirimi öğeye dayalı görsel kullanıcı geribildirim tanıtımı için ortak bir "nesne modeli" sağlar. Bu denetim için yeni bir şablon uygulama veya belirli bir şablon oluşturmayı bilmeden olmadan mümkündür.  
  
 Ancak, tam denetim şablonlarını bilmeden odak görsel stil özelliği çalıştığı için odak görsel stili kullanan bir denetim için görüntülenen görsel geribildirim mutlaka sınırlıdır. Özellik gerçekte yaptığı denetimin işlemesi tarafından kendi şablon yoluyla tarafından oluşturulan gibi farklı bir görsel ağaca (donatıcı) üstünde görsel ağaç yardımcı olmaktır. Dolduran stili kullanarak bu ayrı görsel ağacı tanımlayın <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> özelliği.  
  
<a name="Default"></a>   
## <a name="default-focus-visual-style-behavior"></a>Varsayılan odak görsel stil davranışı  
 Yalnızca klavye tarafından odak eylemi başlatıldığı zaman odak görsel stiller görür. Fare eylemi veya programlı odak değişimi odak görsel stiller modunu devre dışı bırakır. Odak modları arasındaki farklılıklar hakkında daha fazla bilgi için bkz: [odak genel bakış](../../../../docs/framework/wpf/advanced/focus-overview.md).  
  
 Denetimlerin temaları tema içindeki tüm denetimler için odak görsel stil hale bir varsayılan odak görsel stil davranışını içerir. Bu tema stili statik anahtar değeri tarafından tanımlanır <xref:System.Windows.SystemParameters.FocusVisualStyleKey%2A>. Kendi odak görsel stil uygulama düzeyinde bildirirken bu varsayılan stil davranışını temalardan değiştirin. Tüm temayı tanımlarsanız, alternatif olarak, daha sonra bu anahtarı tüm tema için varsayılan davranış stil tanımlamak için kullanmalısınız.  
  
 Temalar, varsayılan odak görsel stili genellikle çok basittir. Kaba yaklaşık verilmiştir:  
  
```  
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
## <a name="when-to-use-focus-visual-styles"></a>Odak görsel stiller kullanma zamanı  
 Kavramsal olarak, Denetim denetimi denetimlere uygulanmış odak görsel stiller görünümünü tutarlı olmalıdır. Tutarlılık sağlamak için bir yalnızca burada temada tanımlanan her denetim çok aynı odak görsel stil ya da bir stil bazı çeşitlemesi alır tüm temayı oluşturuyorsanız görsel stil görsel olarak ilgili Odak denetimden erişecek değiştirmek için yoludur Rol. Alternatif olarak, bir sayfada veya bir kullanıcı Arabirimi klavye odaklanabilir her öğesinin stilini belirlemek için aynı stili (veya benzer stilleri) kullanabilirsiniz.  
  
 Ayarı <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> temanın parçası olmayan tek denetim stillerinde değil hedeflenen odak görsel stiller kullanımdır. Denetimler arasındaki tutarsız görsel davranışların klavye odağını ilgili karmaşık bir kullanıcı deneyimine açabilir olmasıdır. Bir tema arasında kasıtlı olarak değil klavye odağı için özel denetim davranışlarını amaçlanıyorsa, bir daha iyi bir yaklaşımdır Tetikleyicileri stillerde bağımsız giriş durumu özelliklerini gibi kullanmaktır <xref:System.Windows.UIElement.IsFocused%2A> veya <xref:System.Windows.UIElement.IsKeyboardFocused%2A>.  
  
 Odak görsel stiller klavye odağını özel olarak davranır. Bu nedenle, odak görsel stiller erişilebilirlik özelliği türüdür. Fare olup olmadığını aracılığıyla odağı her tür için UI değişiklikleri istiyorsanız, klavye, veya program aracılığıyla, odak görsel stiller kullanmamanız gerekir ve ayarlayıcılar ve stilleri veya genel odak özelliklerinin değerinden çalışan şablonlarındaki Tetikleyicileri kullanmalısınız gibi `IsFocused` veya `IsFocusWithin`.  
  
<a name="How"></a>   
## <a name="how-to-create-a-focus-visual-style"></a>Odak görsel bir stil oluşturma  
 Odak görsel stili her zaman gerekir için oluşturduğunuz stil <xref:System.Windows.Style.TargetType%2A> , <xref:System.Windows.Controls.Control>. Stil çoğunlukla oluşmalıdır bir <xref:System.Windows.Controls.ControlTemplate>. Burada odak görsel stil atanması türünde olmasını hedef türü belirtmeyin <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>.  
  
 Hedef türü her zaman olduğundan <xref:System.Windows.Controls.Control>, tüm denetimler için ortak olan özellikleri kullanarak stil gerekir (özelliklerini kullanarak <xref:System.Windows.Controls.Control> sınıfı ve temel sınıflarından). Bir kullanıcı Arabirimi öğesi bir katmana olarak düzgün ve, denetimin işlevsel alanlara soyutlamaması olmayan bir şablon oluşturmanız gerekir. Genellikle, bu görsel geribildirim denetim kenar boşluklarını dışında veya denetimde isabet testi engellemez geçici ya da örtük efektleri olarak odak görsel stil burada uygulanan görüntüleneceğini anlamına gelir. Boyutlandırma ve katmana şablonunuzun konumlandırmasını belirlemek için yararlı olan şablon bağlamada kullanabileceğiniz özellikler dahil <xref:System.Windows.FrameworkElement.ActualHeight%2A>, <xref:System.Windows.FrameworkElement.ActualWidth%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, ve <xref:System.Windows.Controls.Control.Padding%2A>.  
  
<a name="Alternatives"></a>   
## <a name="alternatives-to-using-a-focus-visual-style"></a>Odak görsel stili kullanımına alternatifler  
 Odak görsel stili kullanarak, yalnızca tek denetimlere stil ekleme olmadığından veya denetim şablonu üzerinde daha fazla denetim istediğiniz uygun olmayan olduğu durumlar için vardır diğer birçok erişilebilir özellikleri ve görsel oluşturabilirsiniz teknikleri davranış odaktaki değişikliklere yanıt.  
  
 Tetikleyiciler, ayarlayıcılar ve olay ayarlayıcıları ele alınmıştır ayrıntılı olarak [stil ve şablon](../../../../docs/framework/wpf/controls/styling-and-templating.md). Yönlendirilmiş olay işleme ele alınmıştır [yönlendirilmiş olaylara genel bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
### <a name="iskeyboardfocused"></a>IsKeyboardFocused  
 Klavye odağı özellikle ilgileniyorsanız <xref:System.Windows.UIElement.IsKeyboardFocused%2A> bağımlılık özelliği için bir özellik kullanılabilir <xref:System.Windows.Trigger>. Bir stil veya şablon özellik tetikleyici, özellikle çok tek bir denetim için ve hangi görsel olarak diğer denetimler için klavye odağı davranışını eşleşmeyebilir bir klavye odağı davranışını tanımlamak için daha uygun bir tekniktir.  
  
 Başka bir benzer bağımlılık özelliği <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>, hangi o klavye odağını görsel olarak çağrı istiyorsanız kullanmak uygun olabilir yere birleştirme içinde veya denetimin işlevsel alanı içinde olduğu. Örneğin, yerleştirebilirsiniz bir <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> tetikleyici klavye odağı daha kesin olarak olsa bile birkaç denetimleri gruplandıran bir panel farklı şekilde göründüğü gibi olması panelin içindeki tek bir öğe üzerinde.  
  
 Olayları de kullanabilirsiniz <xref:System.Windows.UIElement.GotKeyboardFocus> ve <xref:System.Windows.UIElement.LostKeyboardFocus> (yanı sıra Önizleme eşdeğerleri). Bu olaylar için temel olarak kullanabileceğiniz bir <xref:System.Windows.EventSetter>, veya kod arkasında olayları için işleyiciler yazabilirsiniz.  
  
### <a name="other-focus-properties"></a>Diğer odak özellikleri  
 Görsel bir davranış üretmek için odak değiştirmenin tüm olası nedenlerini istiyorsanız, ayarlayıcı veya tetikleyiciyi temel <xref:System.Windows.UIElement.IsFocused%2A> bağımlılık özelliği veya alternatif olarak üzerinde <xref:System.Windows.UIElement.GotFocus> veya <xref:System.Windows.UIElement.LostFocus> için kullanılan olayları bir <xref:System.Windows.EventSetter>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>  
 [Stil ve Şablon Oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Odağa Genel Bakış](../../../../docs/framework/wpf/advanced/focus-overview.md)  
 [Girişe Genel Bakış](../../../../docs/framework/wpf/advanced/input-overview.md)
