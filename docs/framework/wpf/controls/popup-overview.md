---
title: Açılır Pencereye Genel Bakış
description: İçeriği geçerli uygulamanın üzerine gezinen bir pencerede görüntülemenin bir yolunu sağlayan Windows Presentation Foundation Popup denetimi hakkında bilgi edinin.
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Popup
- Popup control [WPF], about Popup control
ms.assetid: 774f53ca-bff8-470e-9ce9-3928b4cf3d4c
ms.openlocfilehash: 84eaddc53366df6d1da1a0a005d3618268f8cce2
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167537"
---
# <a name="popup-overview"></a>Açılır Pencereye Genel Bakış
<xref:System.Windows.Controls.Primitives.Popup>Denetim, belirli bir öğe veya ekran koordinatıyla ilişkili olarak geçerli uygulama penceresi üzerine gezinen ayrı bir pencerede içerik görüntülemenin bir yolunu sağlar. Bu konu, <xref:System.Windows.Controls.Primitives.Popup> denetimi tanıtır ve kullanımı hakkında bilgi sağlar.  

<a name="What_Is_a_Popup_"></a>
## <a name="what-is-a-popup"></a>Açılan pencere nedir?  
 Bir <xref:System.Windows.Controls.Primitives.Popup> Denetim, içeriği bir öğe veya ekrandaki bir noktaya göre ayrı bir pencerede görüntüler. Görünür olduğunda <xref:System.Windows.Controls.Primitives.Popup> , <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> özelliği olarak ayarlanır `true` .  
  
> [!NOTE]
> <xref:System.Windows.Controls.Primitives.Popup>Fare işaretçisi üst nesnenin üzerine geldiğinde bir otomatik olarak açılmaz. Bir <xref:System.Windows.Controls.Primitives.Popup> otomatik olarak açmak istiyorsanız <xref:System.Windows.Controls.ToolTip> veya <xref:System.Windows.Controls.ToolTipService> sınıfını kullanın. Daha fazla bilgi için bkz. [ToolTip Overview](tooltip-overview.md).  
  
<a name="APopupExample"></a>
## <a name="creating-a-popup"></a>Açılan pencere oluşturma  
 Aşağıdaki örnek, <xref:System.Windows.Controls.Primitives.Popup> bir denetimin alt öğesi olan bir denetimin nasıl tanımlanacağını gösterir <xref:System.Windows.Controls.Button> . Yalnızca bir <xref:System.Windows.Controls.Button> alt öğesi olabileceğinden, bu örnek, <xref:System.Windows.Controls.Button> içindeki ve denetimleri için metnini koyar <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.StackPanel> . Öğesinin içeriği, <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.TextBlock> ilgili denetimin yakınında yer alan uygulama penceresi üzerinde gezinen ayrı bir pencerede görüntülenir <xref:System.Windows.Controls.Button> .  
  
 [!code-xaml[PopupSimple#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#1)]  
  
 [!code-xaml[PopupSimple#CreatePopupCodeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#createpopupcodexaml)]  
  
<a name="PopupUses"></a>
## <a name="controls-that-implement-a-popup"></a>Açılan menü uygulayan denetimler  
 <xref:System.Windows.Controls.Primitives.Popup>Denetimleri diğer denetimlerde oluşturabilirsiniz. Aşağıdaki denetimler, <xref:System.Windows.Controls.Primitives.Popup> belirli kullanımlar için denetimi uygular:  
  
- <xref:System.Windows.Controls.ToolTip>. Bir öğe için araç ipucu oluşturmak isterseniz, <xref:System.Windows.Controls.ToolTip> ve <xref:System.Windows.Controls.ToolTipService> sınıflarını kullanın. Daha fazla bilgi için bkz. [ToolTip Overview](tooltip-overview.md).  
  
- <xref:System.Windows.Controls.ContextMenu>. Bir öğe için bağlam menüsü oluşturmak istiyorsanız, <xref:System.Windows.Controls.ContextMenu> denetimi kullanın. Daha fazla bilgi için bkz. [ContextMenu Genel Bakış](contextmenu-overview.md).  
  
- <xref:System.Windows.Controls.ComboBox>. Görüntülenen veya gizlenen bir açılan liste kutusu olan bir seçim denetimi oluşturmak istiyorsanız, <xref:System.Windows.Controls.ComboBox> denetimi kullanın.  
  
- <xref:System.Windows.Controls.Expander>. İçeriği görüntüleyen daraltılabilir bir alanla üst bilgi görüntüleyen bir denetim oluşturmak istiyorsanız, <xref:System.Windows.Controls.Expander> denetimi kullanın. Daha fazla bilgi için bkz. [genişleticiye genel bakış](expander-overview.md).  
  
<a name="PopupBehaviorandAppearance"></a>
## <a name="popup-behavior-and-appearance"></a>Açılan pencere davranışı ve görünümü  
 <xref:System.Windows.Controls.Primitives.Popup>Denetim, davranışını ve görünümünü özelleştirmenizi sağlayan işlevler sağlar. Örneğin, açma ve kapatma davranışı, animasyon, opaklık ve bit eşlem efektlerini ve <xref:System.Windows.Controls.Primitives.Popup> boyutunu ve konumunu ayarlayabilirsiniz.  
  
<a name="OpenandCloseBehavior"></a>
### <a name="open-and-close-behavior"></a>Açma ve kapatma davranışı  
 Bir <xref:System.Windows.Controls.Primitives.Popup> Denetim, <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> özelliği olarak ayarlandığında içeriğini görüntüler `true` . Varsayılan olarak, <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> özelliği olarak ayarlanana kadar açık kalır `false` . Ancak, özelliğini olarak ayarlayarak varsayılan davranışı değiştirebilirsiniz <xref:System.Windows.Controls.Primitives.Popup.StaysOpen%2A> `false` . Bu özelliği olarak ayarlarsanız `false` , <xref:System.Windows.Controls.Primitives.Popup> içerik penceresinde fare yakalaması vardır. <xref:System.Windows.Controls.Primitives.Popup>Fare yakalamayı kaybeder ve pencere, pencerenin dışında bir fare olayı oluştuğunda kapanır <xref:System.Windows.Controls.Primitives.Popup> .  
  
 <xref:System.Windows.Controls.Primitives.Popup.Opened>Ve <xref:System.Windows.Controls.Primitives.Popup.Closed> olayları, <xref:System.Windows.Controls.Primitives.Popup> içerik penceresi açık veya kapalı olduğunda tetiklenir.  
  
<a name="Animation"></a>
### <a name="animation"></a>Animasyon  
 <xref:System.Windows.Controls.Primitives.Popup>Denetimde, genellikle Soldur ve Slide gibi davranışlar ile ilişkili animasyonlar için yerleşik destek bulunur. <xref:System.Windows.Controls.Primitives.Popup.PopupAnimation%2A>Özelliği bir sabit listesi değeri olarak ayarlayarak bu animasyonları açabilirsiniz <xref:System.Windows.Controls.Primitives.PopupAnimation> . <xref:System.Windows.Controls.Primitives.Popup>Animasyonların düzgün çalışması için <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> özelliği olarak ayarlamanız gerekir `true` .  
  
 Ayrıca, denetime benzer animasyonlar uygulayabilirsiniz <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Controls.Primitives.Popup> .  
  
<a name="OpacityandBitmapEffects"></a>
### <a name="opacity-and-bitmap-effects"></a>Opaklık ve bit eşlem efektleri  
 <xref:System.Windows.UIElement.Opacity%2A>Bir <xref:System.Windows.Controls.Primitives.Popup> denetimin özelliği içeriğine hiçbir etkiye sahip değildir. Varsayılan olarak, <xref:System.Windows.Controls.Primitives.Popup> içerik penceresi donuk olur. Saydam oluşturmak için <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> özelliğini olarak ayarlayın `true` .  
  
 Bir öğesinin içeriği, <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> doğrudan <xref:System.Windows.Controls.Primitives.Popup> denetimde veya üst penceredeki diğer herhangi bir öğe üzerinde ayarladığınız gibi bit eşlem efektlerini uygulamaz. Bit eşlem efektlerinin bir ' ın içeriğinde görünmesi için <xref:System.Windows.Controls.Primitives.Popup> , bit eşlem efektini doğrudan içeriğinde ayarlamanız gerekir. Örneğin, öğesinin alt öğesi <xref:System.Windows.Controls.Primitives.Popup> bir ise, <xref:System.Windows.Controls.StackPanel> bit eşlem efektini ' de ayarlayın <xref:System.Windows.Controls.StackPanel> .  
  
<a name="PopupSize"></a>
### <a name="popup-size"></a>Açılan pencere boyutu  
 Varsayılan olarak, bir <xref:System.Windows.Controls.Primitives.Popup> otomatik olarak içeriğine boyutlandırılır. Otomatik boyutlandırma gerçekleştiğinde, içerik için tanımlanan ekran alanının varsayılan boyutu, <xref:System.Windows.Controls.Primitives.Popup> bit eşlem efektlerinin görüntülemesi için yeterli alan sağlamadığından bazı bit eşlem efektleri gizlenmiş olabilir.  
  
 <xref:System.Windows.Controls.Primitives.Popup>içerik üzerinde bir ayarladığınızda, içerik de görünmeyebilir <xref:System.Windows.UIElement.RenderTransform%2A> . Bu senaryoda, dönüştürülmüş içeriğinin <xref:System.Windows.Controls.Primitives.Popup> orijinal alanının ötesine uzatabileceğini bazı içerikler gizlenebilir <xref:System.Windows.Controls.Primitives.Popup> . Bit eşlem efekti veya dönüştürme daha fazla alan gerektiriyorsa, <xref:System.Windows.Controls.Primitives.Popup> denetimin daha fazla alanını sağlamak için içeriğin etrafında bir kenar boşluğu tanımlayabilirsiniz.  
  
<a name="DefiningPopupPosition"></a>
## <a name="defining-the-popup-position"></a>Açılan pencere konumunu tanımlama  
 ,,, <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> Ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffsetProperty> özelliklerini ayarlayarak bir açılan pencereyi yerleştirebilirsiniz. Daha fazla bilgi için bkz. [açılan yerleştirme davranışı](popup-placement-behavior.md). <xref:System.Windows.Controls.Primitives.Popup>Ekranda görüntülendiğinde, üst öğesi yeniden konumlandırıldığında kendisini değiştirmez.  
  
<a name="CustomizingPopupPlacement"></a>
### <a name="customizing-popup-placement"></a>Açılan pencere yerleşimini özelleştirme  
 Bir denetimin yerleşimini, <xref:System.Windows.Controls.Primitives.Popup> görünmesini istediğiniz yere göre bir dizi koordinat belirterek özelleştirebilirsiniz <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> <xref:System.Windows.Controls.Primitives.Popup> .  
  
 Yerleşimi özelleştirmek için <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliğini olarak ayarlayın <xref:System.Windows.Controls.Primitives.PlacementMode.Custom> . Ardından <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> , için olası bir yerleştirme noktaları kümesi ve birincil eksenler (tercih sırasına göre) döndüren bir temsilci tanımlayın <xref:System.Windows.Controls.Primitives.Popup> . Öğesinin en büyük bölümünü gösteren nokta <xref:System.Windows.Controls.Primitives.Popup> otomatik olarak seçilir. Bir örnek için bkz. [özel bir açılan pencere konumu belirtme](how-to-specify-a-custom-popup-position.md).  
  
<a name="PopupandtheVisualTree"></a>
## <a name="popup-and-the-visual-tree"></a>Açılan pencere ve görsel ağaç  
 Bir <xref:System.Windows.Controls.Primitives.Popup> denetimin kendi görsel ağacı yoktur; Bunun yerine, yöntemi çağrıldığında 0 (sıfır) boyutunda bir değer döndürür <xref:System.Windows.Controls.Primitives.Popup.MeasureOverride%2A> <xref:System.Windows.Controls.Primitives.Popup> . Ancak, <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> özelliğini <xref:System.Windows.Controls.Primitives.Popup> olarak ayarladığınızda `true` , kendi görsel ağacı ile yeni bir pencere oluşturulur. Yeni pencere <xref:System.Windows.Controls.Primitives.Popup.Child%2A> içeriğini içerir <xref:System.Windows.Controls.Primitives.Popup> . Yeni pencerenin genişliği ve yüksekliği, ekranın genişliğinin veya yüksekliğinin yüzde 75 ' inden büyük olamaz.  
  
 <xref:System.Windows.Controls.Primitives.Popup>Denetim, <xref:System.Windows.Controls.Primitives.Popup.Child%2A> içeriğine mantıksal alt öğe olarak bir başvuru tutar. Yeni pencere oluşturulduğunda, içeriği <xref:System.Windows.Controls.Primitives.Popup> pencerenin görsel alt öğesi haline gelir ve öğesinin mantıksal alt öğesi kalır <xref:System.Windows.Controls.Primitives.Popup> . Aksine, <xref:System.Windows.Controls.Primitives.Popup> içeriğinin mantıksal üst öğesi kalır <xref:System.Windows.Controls.Primitives.Popup.Child%2A> .  
  
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
