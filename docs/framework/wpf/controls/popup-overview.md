---
title: Açılır Pencereye Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Popup
- Popup control [WPF], about Popup control
ms.assetid: 774f53ca-bff8-470e-9ce9-3928b4cf3d4c
ms.openlocfilehash: 911130d52744c5ba54750f214829a5d1900e083c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185950"
---
# <a name="popup-overview"></a>Açılır Pencereye Genel Bakış
Denetim, <xref:System.Windows.Controls.Primitives.Popup> içeriği, geçerli uygulama penceresiüzerinde, belirlenmiş bir öğeye veya ekran koordinatına göre yüzen ayrı bir pencerede görüntülemek için bir yol sağlar. Bu konu <xref:System.Windows.Controls.Primitives.Popup> denetimi tanır ve kullanımı hakkında bilgi sağlar.  

<a name="What_Is_a_Popup_"></a>
## <a name="what-is-a-popup"></a>Popup Nedir?  
 Denetim, <xref:System.Windows.Controls.Primitives.Popup> içeriği ekrandaki bir öğeye veya noktaya göre ayrı bir pencerede görüntüler. Görünür <xref:System.Windows.Controls.Primitives.Popup> olduğunda, <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> özellik . `true`  
  
> [!NOTE]
> Fare <xref:System.Windows.Controls.Primitives.Popup> işaretçisi ana nesnesinin üzerinde hareket ettiğinde A otomatik olarak açılmaz. A'nın <xref:System.Windows.Controls.Primitives.Popup> otomatik olarak açılmasını istiyorsanız, sınıfı <xref:System.Windows.Controls.ToolTip> veya sınıfı <xref:System.Windows.Controls.ToolTipService> kullanın. Daha fazla bilgi için [Bkz. Araç İpucu Genel Bakış.](tooltip-overview.md)  
  
<a name="APopupExample"></a>
## <a name="creating-a-popup"></a>Pop-up Oluşturma  
 Aşağıdaki örnek, denetimin <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Button> alt öğesi olan bir denetimin nasıl tanımlandığını gösterir. <xref:System.Windows.Controls.Button> A'nın yalnızca bir alt öğesi olabileceğinden, <xref:System.Windows.Controls.Button> bu <xref:System.Windows.Controls.Primitives.Popup> örnekte <xref:System.Windows.Controls.StackPanel>metin ve denetimler bir . İçeriği, metnini ilgili <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.Button> denetimin yanındaki uygulama penceresinin üzerinde yüzen ayrı bir pencerede görüntüleyen bir denetimde görünür.  
  
 [!code-xaml[PopupSimple#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#1)]  
  
 [!code-xaml[PopupSimple#CreatePopupCodeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#createpopupcodexaml)]  
  
<a name="PopupUses"></a>
## <a name="controls-that-implement-a-popup"></a>Açılır Pencere Uygulayan Denetimler  
 Denetimleri <xref:System.Windows.Controls.Primitives.Popup> diğer denetimlere oluşturabilirsiniz. Aşağıdaki denetimler <xref:System.Windows.Controls.Primitives.Popup> belirli kullanımlar için denetimi uygular:  
  
- <xref:System.Windows.Controls.ToolTip>. Bir öğe için bir araç ipucu oluşturmak <xref:System.Windows.Controls.ToolTip> istiyorsanız, sınıfları ve sınıfları <xref:System.Windows.Controls.ToolTipService> kullanın. Daha fazla bilgi için [Bkz. Araç İpucu Genel Bakış.](tooltip-overview.md)  
  
- <xref:System.Windows.Controls.ContextMenu>. Bir öğe için bağlam menüsü oluşturmak istiyorsanız, <xref:System.Windows.Controls.ContextMenu> denetimi kullanın. Daha fazla bilgi için [ContextMenu Genel Bakış'a](contextmenu-overview.md)bakın.  
  
- <xref:System.Windows.Controls.ComboBox>. Gösterilebilen veya gizlenebilen açılır liste kutusu olan bir seçim denetimi oluşturmak <xref:System.Windows.Controls.ComboBox> istiyorsanız, denetimi kullanın.  
  
- <xref:System.Windows.Controls.Expander>. İçeriği görüntüleyen katlanabilir alana sahip bir üstbilgi görüntüleyen bir denetim <xref:System.Windows.Controls.Expander> oluşturmak istiyorsanız, denetimi kullanın. Daha fazla bilgi için [Genişletici Genel Bakış'a](expander-overview.md)bakın.  
  
<a name="PopupBehaviorandAppearance"></a>
## <a name="popup-behavior-and-appearance"></a>Pop-up Davranış ve Görünüm  
 Denetim, <xref:System.Windows.Controls.Primitives.Popup> davranış ını ve görünümünü özelleştirmenize olanak tanıyan işlevsellik sağlar. Örneğin, açık ve kapalı davranış, animasyon, opaklık ve bitmap <xref:System.Windows.Controls.Primitives.Popup> efektleri ve boyut ve konum ayarlayabilirsiniz.  
  
<a name="OpenandCloseBehavior"></a>
### <a name="open-and-close-behavior"></a>Davranışı Açma ve Kapatma  
 Bir <xref:System.Windows.Controls.Primitives.Popup> denetim, <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> özellik ' olarak `true`ayarlandığında içeriğini görüntüler. Varsayılan olarak, <xref:System.Windows.Controls.Primitives.Popup> özellik <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> 'e ayarlanana `false`kadar açık kalır. Ancak, <xref:System.Windows.Controls.Primitives.Popup.StaysOpen%2A> özelliği `false`' ye ayarlayarak varsayılan davranışı değiştirebilirsiniz. Bu özelliği , `false` <xref:System.Windows.Controls.Primitives.Popup> içerik penceresi fare yakalama'ya ayarladığınızda. Fare <xref:System.Windows.Controls.Primitives.Popup> yakalama kaybeder ve pencerenin <xref:System.Windows.Controls.Primitives.Popup> dışında bir fare olayı oluştuğunda pencere kapanır.  
  
 İçerik <xref:System.Windows.Controls.Primitives.Popup.Opened> <xref:System.Windows.Controls.Primitives.Popup.Closed> penceresi açık veya <xref:System.Windows.Controls.Primitives.Popup> kapalı olduğunda olaylar ve olaylar yükseltilir.  
  
<a name="Animation"></a>
### <a name="animation"></a>Animasyon  
 Denetim, <xref:System.Windows.Controls.Primitives.Popup> genellikle solma ve slayt-in gibi davranışlarla ilişkili animasyonlar için yerleşik destek vardır. <xref:System.Windows.Controls.Primitives.Popup.PopupAnimation%2A> Özelliği numaralandırma <xref:System.Windows.Controls.Primitives.PopupAnimation> değerine ayarlayarak bu animasyonları açabilirsiniz. <xref:System.Windows.Controls.Primitives.Popup> Animasyonların düzgün çalışması için <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> özelliği `true`'ye ayarlamanız gerekir.  
  
 <xref:System.Windows.Controls.Primitives.Popup> Denetim gibi <xref:System.Windows.Media.Animation.Storyboard> animasyonları da uygulayabilirsiniz.  
  
<a name="OpacityandBitmapEffects"></a>
### <a name="opacity-and-bitmap-effects"></a>Opaklık ve Bitmap Etkileri  
 Denetim <xref:System.Windows.UIElement.Opacity%2A> <xref:System.Windows.Controls.Primitives.Popup> özelliğinin içeriği üzerinde hiçbir etkisi yoktur. Varsayılan olarak, <xref:System.Windows.Controls.Primitives.Popup> içerik penceresi opaktır. Saydam <xref:System.Windows.Controls.Primitives.Popup>oluşturmak için <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> `true`özelliği .  
  
 A'nın <xref:System.Windows.Controls.Primitives.Popup> içeriği, <xref:System.Windows.Media.Effects.DropShadowBitmapEffect>doğrudan <xref:System.Windows.Controls.Primitives.Popup> denetime veya üst penceredeki herhangi bir öğeye ayarladığınız bit eşlemi efektlerini devralmaz. Bitmap efektlerinin içeriğinde <xref:System.Windows.Controls.Primitives.Popup>görünmesi için bitmap efektini doğrudan içeriğine ayarlamanız gerekir. Örneğin, a'nın <xref:System.Windows.Controls.Primitives.Popup> alt kümesi <xref:System.Windows.Controls.StackPanel>bir ise, bitmap <xref:System.Windows.Controls.StackPanel>efektini .  
  
<a name="PopupSize"></a>
### <a name="popup-size"></a>Popup Boyutu  
 Varsayılan olarak, <xref:System.Windows.Controls.Primitives.Popup> a otomatik olarak içeriğine boyutlandırılır. Otomatik boyutlandırma oluştuğunda, <xref:System.Windows.Controls.Primitives.Popup> içerik için tanımlanan ekran alanının varsayılan boyutu bit eşleme efektlerinin görüntülenmesi için yeterli alan sağlamadığından, bazı bitmap efektleri gizlenmiş olabilir.  
  
 <xref:System.Windows.Controls.Primitives.Popup>içerik üzerinde bir <xref:System.Windows.UIElement.RenderTransform%2A> ayar yaptığınızda içerik de gizlenebilir. Bu senaryoda, dönüştürülen <xref:System.Windows.Controls.Primitives.Popup> içeriğin içeriği orijinal <xref:System.Windows.Controls.Primitives.Popup>alanın ötesine uzanırsa, bazı içerik gizli olabilir. Bitmap efekti veya dönüşümü daha fazla alan gerektiriyorsa, denetim için daha fazla alan sağlamak için içeriğin <xref:System.Windows.Controls.Primitives.Popup> etrafında bir kenar boşluğu tanımlayabilirsiniz.  
  
<a name="DefiningPopupPosition"></a>
## <a name="defining-the-popup-position"></a>Popup Konumunu Tanımlama  
 Pop-up'ı <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, , <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffsetProperty> özelliklerini ayarlayarak konumlandırabilirsiniz. Daha fazla bilgi için [Bkz. Popup Yerleştirme Davranışı.](popup-placement-behavior.md) Ekranda <xref:System.Windows.Controls.Primitives.Popup> görüntülendiğinde, üst öğesi yeniden konumlandırılırsa kendisini yeniden konumlandırmaz.  
  
<a name="CustomizingPopupPlacement"></a>
### <a name="customizing-popup-placement"></a>Popup Yerleşimini Özelleştirme  
 Görünmesini istediğiniz <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> yere göreli bir koordinat kümesi belirterek denetimin yerleşimini <xref:System.Windows.Controls.Primitives.Popup> özelleştirebilirsiniz.  
  
 Yerleşimi özelleştirmek için <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>özelliği ' ye göre ayarlayın. Daha sonra <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> olası yerleşim noktaları ve birincil eksenler kümesi (tercih sırasına <xref:System.Windows.Controls.Primitives.Popup>göre) döndüren bir temsilci tanımlayın. En büyük bölümünü <xref:System.Windows.Controls.Primitives.Popup> gösteren nokta otomatik olarak seçilir. Örneğin, bkz. [Özel Açılır Pencere Konumu Belirtin.](how-to-specify-a-custom-popup-position.md)  
  
<a name="PopupandtheVisualTree"></a>
## <a name="popup-and-the-visual-tree"></a>Pop-up ve Görsel Ağaç  
 Bir <xref:System.Windows.Controls.Primitives.Popup> denetimin kendi görsel ağacı yoktur; bunun yerine <xref:System.Windows.Controls.Primitives.Popup.MeasureOverride%2A> yöntem <xref:System.Windows.Controls.Primitives.Popup> çağrıldığında 0 (sıfır) boyutu döndürür. Ancak, <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> kendi görsel ağacı <xref:System.Windows.Controls.Primitives.Popup> `true`ile yeni bir pencere özelliğini ayarladığınızda oluşturulur. Yeni pencere' <xref:System.Windows.Controls.Primitives.Popup.Child%2A> nin <xref:System.Windows.Controls.Primitives.Popup>içeriği . Yeni pencerenin genişliği ve yüksekliği ekranın genişliğinin veya yüksekliğinin yüzde 75'inden büyük olamaz.  
  
 Denetim, <xref:System.Windows.Controls.Primitives.Popup> mantıksal bir alt <xref:System.Windows.Controls.Primitives.Popup.Child%2A> bilgi olarak içeriğine bir başvuru tutar. Yeni pencere oluşturulduğunda, içeriği <xref:System.Windows.Controls.Primitives.Popup> pencerenin görsel bir alt olur ve mantıksal <xref:System.Windows.Controls.Primitives.Popup>alt kalır. Tersine, <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.Popup.Child%2A> içeriğinin mantıksal üst kalır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.Primitives.Popup>
- <xref:System.Windows.Controls.Primitives.PopupPrimaryAxis>
- <xref:System.Windows.Controls.Primitives.PlacementMode>
- <xref:System.Windows.Controls.Primitives.CustomPopupPlacement>
- <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [Nasıl Dır Konular](popup-how-to-topics.md)
- [Nasıl Dır Konular](tooltip-how-to-topics.md)
