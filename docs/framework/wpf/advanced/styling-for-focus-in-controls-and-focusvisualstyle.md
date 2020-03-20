---
title: Denetimlerde Odak için Stil Oluşturma ve FocusVisualStyle
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard focus [WPF]
- focus [WPF], visual styling
- styles [WPF], focus visual style
ms.assetid: 786ac576-011b-4d72-913b-558deccb9b35
ms.openlocfilehash: fda7ed12d232af5a7cfb8eb43cbb09eb793da171
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141205"
---
# <a name="styling-for-focus-in-controls-and-focusvisualstyle"></a>Denetimlerde Odak için Stil Oluşturma ve FocusVisualStyle
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]klavye odağı aldığında denetimin görsel görünümünü değiştirmek için iki paralel mekanizma sağlar. İlk mekanizma, denetime uygulanan stil veya <xref:System.Windows.UIElement.IsKeyboardFocused%2A> şablon gibi özellikler için özellik ayarlayıcıları kullanmaktır. İkinci mekanizma <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> özelliğin değeri olarak ayrı bir stil sağlamaktır; "odak görsel stil" yerine kontrol veya diğer UI öğesigörsel ağacı değiştirerek yerine, denetimüstüne çizer için ayrı bir görsel ağaç oluşturur. Bu konu, bu mekanizmaların her birinin uygun olduğu senaryoları tartışır.  

<a name="Purpose"></a>
## <a name="the-purpose-of-focus-visual-style"></a>Odak Görsel Stil Amacı  
 Odak görsel stil özelliği, herhangi bir Kullanıcı Arabirimi öğesine klavye gezintisine dayalı görsel kullanıcı geri bildirimini tanıtmak için ortak bir "nesne modeli" sağlar. Bu, denetime yeni bir şablon uygulamadan veya belirli şablon kompozisyonu bilmeden mümkündür.  
  
 Ancak, odak görsel stil özelliği denetim şablonlarını bilmeden çalıştığından, odak görsel stili kullanılarak bir denetim için görüntülenebilen görsel geri bildirim mutlaka sınırlıdır. Özelliğin aslında yaptığı şey, bir denetimin şablonu aracılığıyla görüntülenmesi yle oluşturulan görsel ağacın üstüne farklı bir görsel ağacı (bir süsleyici) yerle bir etmektir. Bu ayrı görsel ağacı <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> özelliği dolduran bir stil kullanarak tanımlarsınız.  
  
<a name="Default"></a>
## <a name="default-focus-visual-style-behavior"></a>Varsayılan Odak Görsel Stil Davranışı  
 Odak görsel stilleri yalnızca odak eylemi klavye tarafından başlatıldığında hareket edin. Herhangi bir fare eylemi veya programlı odak değişikliği, odak görsel stilleri için modu devre dışı kılabilir. Odak modları arasındaki ayrımlar hakkında daha fazla bilgi için [Focus Genel Bakış'a](focus-overview.md)bakın.  
  
 Denetimler için temalar tema tüm denetimler için odak görsel stil olur varsayılan odak görsel stil davranışı içerir. Bu tema stili statik anahtarın <xref:System.Windows.SystemParameters.FocusVisualStyleKey%2A>değeri ile tanımlanır. Uygulama düzeyinde kendi odak görsel stilinizi beyan ettiğinizde, temalardan bu varsayılan stil davranışını değiştirirsiniz. Alternatif olarak, temanın tamamını tanımlarsanız, tüm temanız için varsayılan davranışın stilini tanımlamak için aynı anahtarı kullanmanız gerekir.  
  
 Temalarda, varsayılan odak görsel stili genellikle çok basittir. Aşağıdaki kaba bir yaklaşımdır:  
  
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
## <a name="when-to-use-focus-visual-styles"></a>Odak Görsel Stilleri Ne Zaman Kullanılır  
 Kavramsal olarak, denetimlere uygulanan odak görsel stillerinin görünümü denetimden denetime tutarlı olmalıdır. Tutarlılık sağlamak için bir yolu, tema tanımlanan her denetim ya çok aynı odak görsel stili alır, ya da görsel olarak denetimden bir stil in bazı varyasyonu, bütün bir tema oluştururken odak görsel stili değiştirmektir Denetim. Alternatif olarak, bir sayfadaki veya ui'deki her klavye odaklı öğeyi stillemek için aynı stili (veya benzer stilleri) kullanabilirsiniz.  
  
 Bir <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> temanın parçası olmayan tek tek denetim stilleri üzerinde ayarlama, odak görsel stillerinin amaçlanan kullanımı değildir. Bunun nedeni, denetimler arasında tutarsız bir görsel davranışın klavye odağıyla ilgili kafa karıştırıcı bir kullanıcı deneyimine yol açabiliyor olmasıdır. Bir tema üzerinde kasıtlı olarak tutarlı olmayan klavye odağı için denetime özgü davranışlar planlıyorsanız, çok daha iyi bir yaklaşım, tek tek <xref:System.Windows.UIElement.IsFocused%2A> giriş <xref:System.Windows.UIElement.IsKeyboardFocused%2A>durumu özellikleri için tetikleyicileri kullanmaktır, örneğin veya .  
  
 Odak görsel stilleri yalnızca klavye odağı için hareket. Bu nedenle, odak görsel stilleri erişilebilirlik özelliği türüdür. Fare, klavye veya programlı olarak olsun, herhangi bir odak türü için UI değişiklikleri istiyorsanız, odak görsel stilleri kullanmamalısınız ve bunun yerine, genel <xref:System.Windows.UIElement.IsFocused%2A> odak özellikleri nin değerinden <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>çalışan stiller veya şablonlarda ayarlayıcılar ve tetikleyiciler kullanmalısınız.  
  
<a name="How"></a>
## <a name="how-to-create-a-focus-visual-style"></a>Odak Görsel Stil Oluşturma  
 Bir odak görsel stil için oluşturduğunuz <xref:System.Windows.Style.TargetType%2A> stil <xref:System.Windows.Controls.Control>her zaman olmalıdır. Stil esas olarak bir <xref:System.Windows.Controls.ControlTemplate>. Odak görsel stilinin atandığı tür olacak hedef türünü <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>belirtmezsiniz.  
  
 Hedef türü her <xref:System.Windows.Controls.Control>zaman olduğundan, tüm denetimlerde ortak olan özellikleri <xref:System.Windows.Controls.Control> (sınıfın ve taban sınıflarının özelliklerini kullanarak) kullanarak stil gerekir. Bir UI öğesine bindirme olarak düzgün çalışacak ve denetimin işlevsel alanlarını gizlemeyen bir şablon oluşturmanız gerekir. Genel olarak, bu, görsel geri bildirimin denetim kenar boşluklarının dışında veya odak görsel stilinin uygulandığı denetimüzerindeki isabet testini engellemeyecek geçici veya göze batmayan efektler olarak görünmesi gerektiği anlamına gelir. Bindirme şablonunuzun boyutlandırma ve konumlandırmayı belirlemek için yararlı olan şablon <xref:System.Windows.FrameworkElement.ActualHeight%2A> <xref:System.Windows.FrameworkElement.ActualWidth%2A>bağlamada kullanabileceğiniz özellikler , , <xref:System.Windows.FrameworkElement.Margin%2A>, ve <xref:System.Windows.Controls.Control.Padding%2A>.  
  
<a name="Alternatives"></a>
## <a name="alternatives-to-using-a-focus-visual-style"></a>Odak Görsel Stil Kullanma Alternatifleri  
 Odak görsel stili kullanmanın uygun olmadığı durumlarda, yalnızca tek denetimler oluşturduğunuz dan veya denetim şablonu üzerinde daha fazla denetim istediğinizden, görsel oluşturabilecek diğer birçok erişilebilir özellik ve teknik vardır odak değişikliklerine yanıt olarak davranış.  
  
 Tetikleyiciler, ayarlayıcılar ve olay ayarlayıcıları [Stil ve Templating](../../../desktop-wpf/fundamentals/styles-templates-overview.md)ayrıntılı olarak ele alınmıştır. Yönlendirilen olay [işleme, Yönlendirilmiş Olaylara Genel Bakış'ta](routed-events-overview.md)tartışılır.  
  
### <a name="iskeyboardfocused"></a>ıskeyboardfocused  
 Özellikle klavye odağıyla ilgileniyorsanız, <xref:System.Windows.UIElement.IsKeyboardFocused%2A> bağımlılık özelliği bir özellik <xref:System.Windows.Trigger>için kullanılabilir. Stil veya şablondaki özellik tetikleyicisi, tek bir denetim için çok özel olan ve diğer denetimler için klavye odağı davranışıyla görsel olarak eşleşmeyebilecek bir klavye odağı davranışını tanımlamak için daha uygun bir tekniktir.  
  
 Başka bir benzer <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>bağımlılık özelliği, görsel olarak klavye odakbirleştirme içinde veya denetimişlevsel alan içinde bir yerde olduğunu çağırmak istiyorsanız kullanmak için uygun olabilir. Örneğin, klavye odağı <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> daha kesin olarak bu panelin içindeki tek bir öğeüzerinde olsa da, birkaç denetimi gruplayan bir panelin farklı görünmesini sağlayacak bir tetikleyici yerleştirebilirsiniz.  
  
 Ayrıca olayları <xref:System.Windows.UIElement.GotKeyboardFocus> ve <xref:System.Windows.UIElement.LostKeyboardFocus> (önizleme eşdeğerlerini) de kullanabilirsiniz. Bu olayları bir <xref:System.Windows.EventSetter>,' nin temeli olarak kullanabilir veya kod arkasında olaylar için işleyiciler yazabilirsiniz.  
  
### <a name="other-focus-properties"></a>Diğer Odak Özellikleri  
 Görsel bir davranış oluşturmak için odak değiştirmenin tüm olası nedenlerini istiyorsanız, <xref:System.Windows.UIElement.IsFocused%2A> bağımlılık özelliğine veya alternatif <xref:System.Windows.UIElement.GotFocus> olarak <xref:System.Windows.UIElement.LostFocus> bir <xref:System.Windows.EventSetter>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Odağa Genel Bakış](focus-overview.md)
- [Girişe Genel Bakış](input-overview.md)
