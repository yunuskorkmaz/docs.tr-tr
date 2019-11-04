---
title: Denetimlerde Odak için Stil Oluşturma ve FocusVisualStyle
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard focus [WPF]
- focus [WPF], visual styling
- styles [WPF], focus visual style
ms.assetid: 786ac576-011b-4d72-913b-558deccb9b35
ms.openlocfilehash: 988b084144532df6f7a6073184fcf035b0813bfd
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458683"
---
# <a name="styling-for-focus-in-controls-and-focusvisualstyle"></a>Denetimlerde Odak için Stil Oluşturma ve FocusVisualStyle
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], klavye odağını aldığında bir denetimin görsel görünümünü değiştirmek için iki paralel mekanizma sağlar. İlk mekanizma, denetime uygulanan stil veya şablon içinde <xref:System.Windows.UIElement.IsKeyboardFocused%2A> gibi özellikler için özellik ayarlayıcıları kullanmaktır. İkinci mekanizma, <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> özelliğinin değeri olarak ayrı bir stil sağlamaktır; "odak görsel stili", denetimin veya diğer kullanıcı arabirimi öğesinin görsel ağacını değiştirmek yerine denetimin üzerine çizen bir donatıcı için ayrı bir görsel ağaç oluşturur. Bu konuda, bu mekanizmaların her birinin uygun olduğu senaryolar ele alınmaktadır.  

<a name="Purpose"></a>   
## <a name="the-purpose-of-focus-visual-style"></a>Odak görsel stilinin amacı  
 Odak görsel stili özelliği, herhangi bir kullanıcı arabirimi öğesine yönelik klavye gezintisini temel alan görsel Kullanıcı geri bildirimlerine giriş için ortak bir "nesne modeli" sağlar. Bu, denetime yeni bir şablon uygulamadan veya belirli şablon birleşimini bilmeden mümkündür.  
  
 Bununla birlikte, odak görsel stil özelliği denetim şablonlarını bilmeden çalışacağından, odak görsel stili kullanan bir denetim için görüntülenebilen görsel geri bildirimin sınırlı olması gerekir. Özelliğin gerçekten ne yaptığı, bir denetimin işlemesi tarafından şablonu aracılığıyla oluşturulan farklı bir görsel ağacı (bir donatıcı) görsel ağacın üzerine kaplatabileridir. Bu ayrı görsel ağacı, <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> özelliğini dolduran bir stil kullanarak tanımlarsınız.  
  
<a name="Default"></a>   
## <a name="default-focus-visual-style-behavior"></a>Varsayılan odak görsel stil davranışı  
 Odak görsel stilleri, yalnızca odak eylemi klavye tarafından başlatıldığında çalışır. Herhangi bir fare eylemi veya programlı odak değişikliği, odak görsel stillerinin modunu devre dışı bırakır. Odak modları arasındaki farklılıklar hakkında daha fazla bilgi için bkz. [odağa genel bakış](focus-overview.md).  
  
 Denetimlerin temaları, temadaki tüm denetimler için odak görsel stili haline gelen bir varsayılan odak görsel stil davranışı içerir. Bu tema stili, statik anahtar <xref:System.Windows.SystemParameters.FocusVisualStyleKey%2A>değeri tarafından tanımlanır. Uygulama düzeyinde kendi odak görsel stilinizi bildirdiğinizde, bu varsayılan stil davranışını temalardan değiştirirsiniz. Alternatif olarak, tüm temayı tanımlarsanız, tüm temanız için varsayılan davranışın stilini tanımlamak üzere bu anahtarı kullanmanız gerekir.  
  
 Temalarda, varsayılan odak görsel stili genellikle çok basittir. Aşağıda kabaca bir yaklaşık değer verilmiştir:  
  
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
## <a name="when-to-use-focus-visual-styles"></a>Odak görsel stillerinin ne zaman kullanılacağı  
 Kavramsal olarak, denetimlere uygulanan odak görsel stillerinin görünümü denetimden denetime tutarlı olmalıdır. Tutarlı bir şekilde emin olmanın bir yolu, yalnızca bir temanın tanımlanmış olduğu her bir denetimin çok aynı odak görsel stilini ya da denetimden devamı ile görsel olarak ilişkili bir stil varyasyonunu rol. Alternatif olarak, bir sayfada veya bir kullanıcı arabirimindeki her klavye odakındaki öğesinde stil eklemek için aynı stili (veya benzer stilleri) kullanabilirsiniz.  
  
 Bir temanın parçası olmayan bireysel denetim stillerinde <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> ayarlama, odak görsel stillerinin amaçlanan kullanımı değildir. Bunun nedeni, denetimler arasındaki tutarsız görsel davranışların klavye odağıyla ilgili karmaşık bir kullanıcı deneyimine yol açabilir. Bir temaya uygun olmayan klavye odağı için denetime özgü davranışları çok daha iyi hale getirebiliyorsanız, <xref:System.Windows.UIElement.IsFocused%2A> veya <xref:System.Windows.UIElement.IsKeyboardFocused%2A>gibi ayrı giriş durumu özelliklerinin stillerinde tetiklerinin kullanılması çok daha iyi bir yaklaşımdır.  
  
 Odak görsel stilleri, klavye odağı için özel olarak davranır. Bu nedenle, odak görsel stilleri bir erişilebilirlik özelliği türüdür. Her tür odak için fare, klavye veya programlama yoluyla kullanıcı arabirimi değişikliği yapmak istiyorsanız, odak görsel stillerini kullanmamalısınız ve bunun yerine genel odak özelliklerinin değerinden çalışan stillerde veya şablonlarda ayarlayıcılar ve Tetikleyiciler kullanmanız gerekir <xref:System.Windows.UIElement.IsFocused%2A> veya <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>gibi.  
  
<a name="How"></a>   
## <a name="how-to-create-a-focus-visual-style"></a>Odak görsel stili oluşturma  
 Odak görsel stili için oluşturduğunuz stil her zaman <xref:System.Windows.Controls.Control><xref:System.Windows.Style.TargetType%2A> sahip olmalıdır. Stil çoğunlukla bir <xref:System.Windows.Controls.ControlTemplate>oluşmalıdır. Hedef türünü, odak görsel stilinin <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>atandığı tür olarak belirtmeyin.  
  
 Hedef türü her zaman <xref:System.Windows.Controls.Control>olduğundan, tüm denetimlerde ortak olan özellikleri kullanarak stil oluşturmanız gerekir (<xref:System.Windows.Controls.Control> sınıfının ve temel sınıflarının özelliklerini kullanarak). Bir UI öğesine bir kaplama olarak düzgün şekilde çalışacak ve denetimin işlevsel alanını gizlememe bir şablon oluşturmanız gerekir. Genellikle, bu, görsel geri bildirimin denetim kenar boşluklarının dışında görünmesi ya da odak görsel stilinin uygulandığı denetimde isabet sınamasını engellememe geçici ya da unobtrusive etkileri olarak görünmeyeceği anlamına gelir. Şablon bağlamasında kullanabileceğiniz özellikler, yer paylaşımı şablonunuzun boyutlandırma ve yerleşimini belirlemek için faydalı olan <xref:System.Windows.FrameworkElement.ActualHeight%2A>, <xref:System.Windows.FrameworkElement.ActualWidth%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>ve <xref:System.Windows.Controls.Control.Padding%2A>içerir.  
  
<a name="Alternatives"></a>   
## <a name="alternatives-to-using-a-focus-visual-style"></a>Odak görsel stili kullanma alternatifleri  
 Yalnızca tek denetimlerin stillendirilmesini veya denetim şablonu üzerinde daha fazla denetim olmasını istediğiniz için odak görsel stilinin kullanılması uygun değildir, ancak görsel oluşturabilecek birçok farklı erişilebilir özellik ve teknik vardır odadaki değişikliklere yanıt olarak davranış.  
  
 Tetikleyiciler, ayarlayıcılar ve olay ayarlayıcıları, [Stil ve şablon](../../../desktop-wpf/fundamentals/styles-templates-overview.md)oluşturma bölümünde ayrıntılı olarak ele alınmıştır. Yönlendirilmiş olay işleme, [yönlendirilmiş olaylara genel bakış](routed-events-overview.md)bölümünde ele alınmıştır.  
  
### <a name="iskeyboardfocused"></a>Üzerindeki IsKeyboardFocused  
 Klavye odağıyla özellikle ilgileniyorsanız, <xref:System.Windows.UIElement.IsKeyboardFocused%2A> bağımlılık özelliği bir özellik <xref:System.Windows.Trigger>için kullanılabilir. Bir stil veya şablondaki bir özellik tetikleyicisi, tek bir denetim için özel olarak bir klavye odağı davranışı tanımlamaya yönelik daha uygun bir tekniktir ve bu, diğer denetimlerin klavye odağı davranışına görsel olarak eşleşmeyebilir.  
  
 Başka bir benzer bağımlılık özelliği <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>, bu klavye odağının birleştirme içinde veya denetimin işlevsel alanındaki bir yerde olduğunu görsel olarak çağırmak istiyorsanız kullanılması uygun olabilir. Örneğin, çok sayıda denetimi gruplandıran bir panelin farklı görünmesini sağlayan bir <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> tetikleyicisi yerleştirebilirsiniz, ancak klavye odağı bu panelde tek bir öğe üzerinde daha hassas olabilir.  
  
 Ayrıca, <xref:System.Windows.UIElement.GotKeyboardFocus> ve <xref:System.Windows.UIElement.LostKeyboardFocus> (Önizleme eşdeğerleriyle birlikte) olayları da kullanabilirsiniz. Bu olayları bir <xref:System.Windows.EventSetter>için temel olarak kullanabilir veya arka plan kodundaki olaylara yönelik işleyiciler yazabilirsiniz.  
  
### <a name="other-focus-properties"></a>Diğer odak özellikleri  
 Odak değiştirmenin tüm olası nedenlerini görsel bir davranış üretmede kullanmak istiyorsanız, <xref:System.Windows.UIElement.IsFocused%2A> bağımlılık özelliğinde bir ayarlayıcı veya tetikleyiciyi temel almalıdır veya bir <xref:System.Windows.EventSetter>için kullanılan <xref:System.Windows.UIElement.GotFocus> veya <xref:System.Windows.UIElement.LostFocus> olaylarına bir veya daha fazla olay oluşturmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Odağa Genel Bakış](focus-overview.md)
- [Girişe Genel Bakış](input-overview.md)
