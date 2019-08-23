---
title: Açılır Pencereye Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Popup
- Popup control [WPF], about Popup control
ms.assetid: 774f53ca-bff8-470e-9ce9-3928b4cf3d4c
ms.openlocfilehash: 7e6977737d362fd0df6321702bb8a1ac6cad66e0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951435"
---
# <a name="popup-overview"></a>Açılır Pencereye Genel Bakış
Denetim <xref:System.Windows.Controls.Primitives.Popup> , belirli bir öğe veya ekran koordinatıyla ilişkili olarak geçerli uygulama penceresi üzerine gezinen ayrı bir pencerede içerik görüntülemenin bir yolunu sağlar. Bu konu, <xref:System.Windows.Controls.Primitives.Popup> denetimi tanıtır ve kullanımı hakkında bilgi sağlar.  

<a name="What_Is_a_Popup_"></a>   
## <a name="what-is-a-popup"></a>Açılan pencere nedir?  
 Bir <xref:System.Windows.Controls.Primitives.Popup> denetim, içeriği bir öğe veya ekrandaki bir noktaya göre ayrı bir pencerede görüntüler. Görünür olduğunda, özelliği olarak `true`ayarlanır. <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> <xref:System.Windows.Controls.Primitives.Popup>  
  
> [!NOTE]
> Fare <xref:System.Windows.Controls.Primitives.Popup> işaretçisi üst nesnenin üzerine geldiğinde bir otomatik olarak açılmaz. Bir <xref:System.Windows.Controls.Primitives.Popup> otomatik olarak açmak istiyorsanız <xref:System.Windows.Controls.ToolTip> veya <xref:System.Windows.Controls.ToolTipService> sınıfını kullanın. Daha fazla bilgi için bkz. [ToolTip Overview](tooltip-overview.md).  
  
<a name="APopupExample"></a>   
## <a name="creating-a-popup"></a>Açılan pencere oluşturma  
 Aşağıdaki örnek, bir <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Button> denetimin alt öğesi olan bir denetimin nasıl tanımlanacağını gösterir. Yalnızca bir alt öğesi olabileceğinden, bu örnek, <xref:System.Windows.Controls.Button> içindeki <xref:System.Windows.Controls.StackPanel>ve <xref:System.Windows.Controls.Primitives.Popup> denetimleri için metnini koyar. <xref:System.Windows.Controls.Button> Öğesinin <xref:System.Windows.Controls.Primitives.Popup> içeriği, <xref:System.Windows.Controls.TextBlock> ilgili<xref:System.Windows.Controls.Button> denetimin yakınında yer alan uygulama penceresi üzerinde gezinen ayrı bir pencerede görüntülenir.  
  
 [!code-xaml[PopupSimple#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#1)]  
  
 [!code-xaml[PopupSimple#CreatePopupCodeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#createpopupcodexaml)]  
  
<a name="PopupUses"></a>   
## <a name="controls-that-implement-a-popup"></a>Açılan menü uygulayan denetimler  
 <xref:System.Windows.Controls.Primitives.Popup> Denetimleri diğer denetimlerde oluşturabilirsiniz. Aşağıdaki denetimler, belirli kullanımlar <xref:System.Windows.Controls.Primitives.Popup> için denetimi uygular:  
  
- <xref:System.Windows.Controls.ToolTip>. Bir öğe için araç ipucu oluşturmak isterseniz, <xref:System.Windows.Controls.ToolTip> ve <xref:System.Windows.Controls.ToolTipService> sınıflarını kullanın. Daha fazla bilgi için bkz. [ToolTip Overview](tooltip-overview.md).  
  
- <xref:System.Windows.Controls.ContextMenu>. Bir öğe için bağlam menüsü oluşturmak istiyorsanız, <xref:System.Windows.Controls.ContextMenu> denetimi kullanın. Daha fazla bilgi için bkz. [ContextMenu Genel Bakış](contextmenu-overview.md).  
  
- <xref:System.Windows.Controls.ComboBox>. Görüntülenen veya gizlenen bir açılan liste kutusu olan bir seçim denetimi oluşturmak istiyorsanız, <xref:System.Windows.Controls.ComboBox> denetimi kullanın.  
  
- <xref:System.Windows.Controls.Expander>. İçeriği görüntüleyen daraltılabilir bir alanla üst bilgi görüntüleyen bir denetim oluşturmak istiyorsanız, <xref:System.Windows.Controls.Expander> denetimi kullanın. Daha fazla bilgi için bkz. [genişleticiye genel bakış](expander-overview.md).  
  
<a name="PopupBehaviorandAppearance"></a>   
## <a name="popup-behavior-and-appearance"></a>Açılan pencere davranışı ve görünümü  
 Denetim <xref:System.Windows.Controls.Primitives.Popup> , davranışını ve görünümünü özelleştirmenizi sağlayan işlevler sağlar. Örneğin, açma ve kapatma davranışı, animasyon, opaklık ve bit eşlem efektlerini ve <xref:System.Windows.Controls.Primitives.Popup> boyutunu ve konumunu ayarlayabilirsiniz.  
  
<a name="OpenandCloseBehavior"></a>   
### <a name="open-and-close-behavior"></a>Açma ve kapatma davranışı  
 Bir <xref:System.Windows.Controls.Primitives.Popup> denetim, <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> özelliği olarak `true`ayarlandığında içeriğini görüntüler. Varsayılan olarak, <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> özelliği olarak `false`ayarlanana kadar açık kalır. Ancak, <xref:System.Windows.Controls.Primitives.Popup.StaysOpen%2A> özelliğini olarak `false`ayarlayarak varsayılan davranışı değiştirebilirsiniz. Bu özelliği olarak `false`ayarlarsanız <xref:System.Windows.Controls.Primitives.Popup> , içerik penceresinde fare yakalaması vardır. <xref:System.Windows.Controls.Primitives.Popup> Fare yakalamayı <xref:System.Windows.Controls.Primitives.Popup> kaybeder ve pencere, pencerenin dışında bir fare olayı oluştuğunda kapanır.  
  
 Ve <xref:System.Windows.Controls.Primitives.Popup.Opened> olayları<xref:System.Windows.Controls.Primitives.Popup.Closed>,içerikpenceresiaçık veyakapalıolduğundatetiklenir.<xref:System.Windows.Controls.Primitives.Popup>  
  
<a name="Animation"></a>   
### <a name="animation"></a>Animasyon  
 <xref:System.Windows.Controls.Primitives.Popup> Denetimde, genellikle Soldur ve Slide gibi davranışlar ile ilişkili animasyonlar için yerleşik destek bulunur. <xref:System.Windows.Controls.Primitives.Popup.PopupAnimation%2A> Özelliği bir<xref:System.Windows.Controls.Primitives.PopupAnimation> sabit listesi değeri olarak ayarlayarak bu animasyonları açabilirsiniz. Animasyonların <xref:System.Windows.Controls.Primitives.Popup> düzgün çalışması için <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> özelliği olarak `true`ayarlamanız gerekir.  
  
 Ayrıca, <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Controls.Primitives.Popup> denetime benzer animasyonlar uygulayabilirsiniz.  
  
<a name="OpacityandBitmapEffects"></a>   
### <a name="opacity-and-bitmap-effects"></a>Opaklık ve bit eşlem efektleri  
 <xref:System.Windows.UIElement.Opacity%2A> Bir<xref:System.Windows.Controls.Primitives.Popup> denetimin özelliği içeriğine hiçbir etkiye sahip değildir. Varsayılan olarak, <xref:System.Windows.Controls.Primitives.Popup> içerik penceresi donuk olur. Saydam <xref:System.Windows.Controls.Primitives.Popup>oluşturmak için <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> özelliğini olarak `true`ayarlayın.  
  
 Bir <xref:System.Windows.Controls.Primitives.Popup> öğesinin içeriği, doğrudan <xref:System.Windows.Controls.Primitives.Popup> denetimde veya üst penceredeki diğer herhangi bir <xref:System.Windows.Media.Effects.DropShadowBitmapEffect>öğe üzerinde ayarladığınız gibi bit eşlem efektlerini uygulamaz. Bit eşlem efektlerinin bir <xref:System.Windows.Controls.Primitives.Popup>' ın içeriğinde görünmesi için, bit eşlem efektini doğrudan içeriğinde ayarlamanız gerekir. Örneğin, öğesinin <xref:System.Windows.Controls.Primitives.Popup> alt öğesi bir <xref:System.Windows.Controls.StackPanel>ise, bit eşlem efektini <xref:System.Windows.Controls.StackPanel>' de ayarlayın.  
  
<a name="PopupSize"></a>   
### <a name="popup-size"></a>Açılan pencere boyutu  
 Varsayılan olarak, bir <xref:System.Windows.Controls.Primitives.Popup> otomatik olarak içeriğine boyutlandırılır. Otomatik boyutlandırma gerçekleştiğinde, <xref:System.Windows.Controls.Primitives.Popup> içerik için tanımlanan ekran alanının varsayılan boyutu, bit eşlem efektlerinin görüntülemesi için yeterli alan sağlamadığından bazı bit eşlem efektleri gizlenmiş olabilir.  
  
 <xref:System.Windows.Controls.Primitives.Popup>içerik üzerinde bir <xref:System.Windows.UIElement.RenderTransform%2A> ayarladığınızda, içerik de görünmeyebilir. Bu senaryoda, dönüştürülmüş <xref:System.Windows.Controls.Primitives.Popup> içeriğinin orijinal <xref:System.Windows.Controls.Primitives.Popup>alanının ötesine uzatabileceğini bazı içerikler gizlenebilir. Bit eşlem efekti veya dönüştürme daha fazla alan gerektiriyorsa, denetimin daha fazla alanını sağlamak için <xref:System.Windows.Controls.Primitives.Popup> içeriğin etrafında bir kenar boşluğu tanımlayabilirsiniz.  
  
<a name="DefiningPopupPosition"></a>   
## <a name="defining-the-popup-position"></a>Açılan pencere konumunu tanımlama  
 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, ,,<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>Ve özellikleriniayarlayarakbir<xref:System.Windows.Controls.Primitives.Popup.VerticalOffsetProperty> açılan pencereyi yerleştirebilirsiniz. <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> Daha fazla bilgi için bkz. [açılan yerleştirme davranışı](popup-placement-behavior.md). Ekranda <xref:System.Windows.Controls.Primitives.Popup> görüntülendiğinde, üst öğesi yeniden konumlandırıldığında kendisini değiştirmez.  
  
<a name="CustomizingPopupPlacement"></a>   
### <a name="customizing-popup-placement"></a>Açılan pencere yerleşimini özelleştirme  
 Bir <xref:System.Windows.Controls.Primitives.Popup> denetimin yerleşimini, görünmesini istediğiniz <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> yere <xref:System.Windows.Controls.Primitives.Popup> göre bir dizi koordinat belirterek özelleştirebilirsiniz.  
  
 Yerleşimi özelleştirmek için <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliğini olarak <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>ayarlayın. Ardından, <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> <xref:System.Windows.Controls.Primitives.Popup>için olası bir yerleştirme noktaları kümesi ve birincil eksenler (tercih sırasına göre) döndüren bir temsilci tanımlayın. Öğesinin <xref:System.Windows.Controls.Primitives.Popup> en büyük bölümünü gösteren nokta otomatik olarak seçilir. Bir örnek için bkz. [özel bir açılan pencere konumu belirtme](how-to-specify-a-custom-popup-position.md).  
  
<a name="PopupandtheVisualTree"></a>   
## <a name="popup-and-the-visual-tree"></a>Açılan pencere ve görsel ağaç  
 Bir <xref:System.Windows.Controls.Primitives.Popup> denetimin kendi görsel ağacı yoktur; Bunun yerine, <xref:System.Windows.Controls.Primitives.Popup.MeasureOverride%2A> yöntemi <xref:System.Windows.Controls.Primitives.Popup> çağrıldığında 0 (sıfır) boyutunda bir değer döndürür. Ancak, <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> <xref:System.Windows.Controls.Primitives.Popup> özelliğini olarak`true`ayarladığınızda, kendi görsel ağacı ile yeni bir pencere oluşturulur. Yeni pencere <xref:System.Windows.Controls.Primitives.Popup.Child%2A> <xref:System.Windows.Controls.Primitives.Popup>içeriğini içerir. Yeni pencerenin genişliği ve yüksekliği, ekranın genişliğinin veya yüksekliğinin yüzde 75 ' inden büyük olamaz.  
  
 Denetim <xref:System.Windows.Controls.Primitives.Popup> , <xref:System.Windows.Controls.Primitives.Popup.Child%2A> içeriğine mantıksal alt öğe olarak bir başvuru tutar. Yeni pencere oluşturulduğunda, içeriği <xref:System.Windows.Controls.Primitives.Popup> pencerenin görsel alt öğesi haline gelir ve öğesinin mantıksal <xref:System.Windows.Controls.Primitives.Popup>alt öğesi kalır. Aksine, <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.Popup.Child%2A> içeriğinin mantıksal üst öğesi kalır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.Primitives.Popup>
- <xref:System.Windows.Controls.Primitives.PopupPrimaryAxis>
- <xref:System.Windows.Controls.Primitives.PlacementMode>
- <xref:System.Windows.Controls.Primitives.CustomPopupPlacement>
- <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [Nasıl Yapılır Konuları](popup-how-to-topics.md)
- [Nasıl Yapılır Konuları](tooltip-how-to-topics.md)
