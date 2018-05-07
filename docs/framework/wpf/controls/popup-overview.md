---
title: Açılır Pencereye Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Popup
- Popup control [WPF], about Popup control
ms.assetid: 774f53ca-bff8-470e-9ce9-3928b4cf3d4c
ms.openlocfilehash: c9261e2151f116b46a0c25d8dc775bf41bf932b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="popup-overview"></a>Açılır Pencereye Genel Bakış
<xref:System.Windows.Controls.Primitives.Popup> Denetimi atanmış bir öğe veya ekran koordinat göre geçerli uygulama penceresi üzerinde gezinen ayrı bir pencerede içeriği görüntülemek için bir yol sağlar. Bu konu tanıtır <xref:System.Windows.Controls.Primitives.Popup> denetlemek ve kullanımı hakkında bilgi sağlar.  
  
 
  
<a name="What_Is_a_Popup_"></a>   
## <a name="what-is-a-popup"></a>Açılan pencere nedir?  
 A <xref:System.Windows.Controls.Primitives.Popup> denetimi içeriği bir öğe veya ekran noktasında göre ayrı bir pencerede görüntüler. Zaman <xref:System.Windows.Controls.Primitives.Popup> görünür durumda <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> özelliği ayarlanmış `true`.  
  
> [!NOTE]
>  A <xref:System.Windows.Controls.Primitives.Popup> fare işaretçisini, üst nesnenin üzerinde getirdiğinde otomatik olarak açılmaz. İsterseniz bir <xref:System.Windows.Controls.Primitives.Popup> otomatik olarak açmak için kullanmak <xref:System.Windows.Controls.ToolTip> veya <xref:System.Windows.Controls.ToolTipService> sınıfı. Daha fazla bilgi için bkz: [araç ipucu genel bakış](../../../../docs/framework/wpf/controls/tooltip-overview.md).  
  
<a name="APopupExample"></a>   
## <a name="creating-a-popup"></a>Açılan pencere oluşturma  
 Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Controls.Primitives.Popup> denetiminin alt öğesi olan bir <xref:System.Windows.Controls.Button> denetim. Çünkü bir <xref:System.Windows.Controls.Button> yalnızca bir alt öğesi olabilir, bu örnek için metin yerleştirir <xref:System.Windows.Controls.Button> ve <xref:System.Windows.Controls.Primitives.Popup> denetimlerini bir <xref:System.Windows.Controls.StackPanel>. İçeriği <xref:System.Windows.Controls.Primitives.Popup> görünür bir <xref:System.Windows.Controls.TextBlock> metnini ilgili yakın uygulama penceresi üzerinde gezinen ayrı bir pencerede görüntüler denetim <xref:System.Windows.Controls.Button> denetim.  
  
 [!code-xaml[PopupSimple#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#1)]  
  
 [!code-xaml[PopupSimple#CreatePopupCodeXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#createpopupcodexaml)]  
  
<a name="PopupUses"></a>   
## <a name="controls-that-implement-a-popup"></a>Açılan pencere uygulamak denetimleri  
 Oluşturabileceğiniz <xref:System.Windows.Controls.Primitives.Popup> denetimlerini diğer denetimlerde. Aşağıdaki denetimleri uygulayın <xref:System.Windows.Controls.Primitives.Popup> denetimi belirli kullanımlar için:  
  
-   <xref:System.Windows.Controls.ToolTip>. Bir öğe için araç ipucu oluşturmak istiyorsanız, kullanmak <xref:System.Windows.Controls.ToolTip> ve <xref:System.Windows.Controls.ToolTipService> sınıfları. Daha fazla bilgi için bkz: [araç ipucu genel bakış](../../../../docs/framework/wpf/controls/tooltip-overview.md).  
  
-   <xref:System.Windows.Controls.ContextMenu>. Bir öğe için bir bağlam menüsü oluşturmak istiyorsanız, kullanmak <xref:System.Windows.Controls.ContextMenu> denetim. Daha fazla bilgi için bkz: [ContextMenu genel bakış](../../../../docs/framework/wpf/controls/contextmenu-overview.md).  
  
-   <xref:System.Windows.Controls.ComboBox>. Gösterilen ya da gizli, kullanım olabilir bir açılır liste kutusu olan seçim denetimini oluşturmak istiyorsanız, <xref:System.Windows.Controls.ComboBox> denetim.  
  
-   <xref:System.Windows.Controls.Expander>. İçeriği görüntüler daraltılabilir bir alana sahip bir üstbilgi görüntüleyen bir denetim oluşturmak istiyorsanız, kullanmak <xref:System.Windows.Controls.Expander> denetim. Daha fazla bilgi için bkz: [genişletici genel bakış](../../../../docs/framework/wpf/controls/expander-overview.md).  
  
<a name="PopupBehaviorandAppearance"></a>   
## <a name="popup-behavior-and-appearance"></a>Açılan davranışı ve görünümü  
 <xref:System.Windows.Controls.Primitives.Popup> Denetimi kendi davranış ve görünümünü özelleştirmenize olanak tanıyan işlevselliği sağlar. Örneğin, ayarlayabileceğiniz açma ve kapama davranışı, animasyon, opaklık ve bit eşlem efektleri ve <xref:System.Windows.Controls.Primitives.Popup> boyut ve konum.  
  
<a name="OpenandCloseBehavior"></a>   
### <a name="open-and-close-behavior"></a>Açma ve kapama davranışı  
 A <xref:System.Windows.Controls.Primitives.Popup> denetimi içeriğini görüntüler zaman <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> özelliği ayarlanmış `true`. Varsayılan olarak, <xref:System.Windows.Controls.Primitives.Popup> kadar açık kalır <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> özelliği ayarlanmış `false`. Ancak, varsayılan davranışı ayarlayarak değiştirebileceğiniz <xref:System.Windows.Controls.Primitives.Popup.StaysOpen%2A> özelliğine `false`. Bu özelliği ayarlandığında `false`, <xref:System.Windows.Controls.Primitives.Popup> içerik penceresinin fare yakalaması vardır. <xref:System.Windows.Controls.Primitives.Popup> Dışında bir fare olayı meydana geldiğinde fare yakalama ve pencere kapanır kaybeder <xref:System.Windows.Controls.Primitives.Popup> penceresi.  
  
 <xref:System.Windows.Controls.Primitives.Popup.Opened> Ve <xref:System.Windows.Controls.Primitives.Popup.Closed> olayları ortaya çıkar zaman <xref:System.Windows.Controls.Primitives.Popup> içerik penceresi açık veya kapalı.  
  
<a name="Animation"></a>   
### <a name="animation"></a>Animasyon  
 <xref:System.Windows.Controls.Primitives.Popup> Denetimi belirme ve slayt bileşenini gibi davranışlar ile genellikle ilişkili animasyonları için yerleşik destek vardır. Ayarlayarak bu animasyonları etkinleştirebilirsiniz <xref:System.Windows.Controls.Primitives.Popup.PopupAnimation%2A> özelliğine bir <xref:System.Windows.Controls.Primitives.PopupAnimation> numaralandırma değeri. İçin <xref:System.Windows.Controls.Primitives.Popup> doğru çalışması için animasyonları ayarlamalısınız <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> özelliğine `true`.  
  
 Ayrıca gibi animasyonları uygulayabilirsiniz <xref:System.Windows.Media.Animation.Storyboard> için <xref:System.Windows.Controls.Primitives.Popup> denetim.  
  
<a name="OpacityandBitmapEffects"></a>   
### <a name="opacity-and-bitmap-effects"></a>Opaklık ve bit eşlem etkileri  
 <xref:System.Windows.UIElement.Opacity%2A> Özelliği için bir <xref:System.Windows.Controls.Primitives.Popup> denetimi içeriğini hiçbir etkisi. Varsayılan olarak, <xref:System.Windows.Controls.Primitives.Popup> içerik penceresi donuk. Saydam oluşturmak için <xref:System.Windows.Controls.Primitives.Popup>ayarlayın <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> özelliğine `true`.  
  
 İçeriği bir <xref:System.Windows.Controls.Primitives.Popup> bit eşlem efektleri gibi devralmıyor <xref:System.Windows.Media.Effects.DropShadowBitmapEffect>, doğrudan üzerinde ayarladığınız <xref:System.Windows.Controls.Primitives.Popup> denetim veya herhangi bir üst pencere öğesinde. Bit eşlem efektleri içeriğine görünmesi için bir <xref:System.Windows.Controls.Primitives.Popup>, içeriği doğrudan bit eşlem etkisini ayarlamanız gerekir. Örneğin, varsa alt bir <xref:System.Windows.Controls.Primitives.Popup> olan bir <xref:System.Windows.Controls.StackPanel>, bit eşlem etkisi ayarlayın <xref:System.Windows.Controls.StackPanel>.  
  
<a name="PopupSize"></a>   
### <a name="popup-size"></a>Açılan pencere boyutu  
 Varsayılan olarak, bir <xref:System.Windows.Controls.Primitives.Popup> için içeriği otomatik olarak boyutlandırılır. Otomatik boyutlandırma oluştuğunda bazı bit eşlem efektleri çünkü gizlenebilir için tanımlanan ekran alanının varsayılan boyutu <xref:System.Windows.Controls.Primitives.Popup> içeriği görüntülemek bit eşlem efektleri için yeterli alan sağlamaz.  
  
 <xref:System.Windows.Controls.Primitives.Popup> içerik de ayarladığınızda görünmeyebilir bir <xref:System.Windows.UIElement.RenderTransform%2A> içerik üzerinde. Bu senaryoda, bazı içerikler gizlenmiş olabilir dönüştürülmüş içeriğini <xref:System.Windows.Controls.Primitives.Popup> özgün alanı genişleterek <xref:System.Windows.Controls.Primitives.Popup>. Bir bit eşlem efekti veya dönüşümü daha fazla alan gerektiriyorsa, çevresindeki kenar boşluğu tanımlayabilirsiniz <xref:System.Windows.Controls.Primitives.Popup> içerik denetimi için daha fazla alan sağlamak için.  
  
<a name="DefiningPopupPosition"></a>   
## <a name="defining-the-popup-position"></a>Popup konumu tanımlama  
 Ayarlayarak popup yerleştirebilirsiniz <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffsetProperty> özellikleri. Daha fazla bilgi için bkz: [açılan yerleştirme davranışını](../../../../docs/framework/wpf/controls/popup-placement-behavior.md). Zaman <xref:System.Windows.Controls.Primitives.Popup> görüntülenir, üst yeniden konumlandırılır, ekranda, kendisi yeniden konumlandırmayı sağlamaz.  
  
<a name="CustomizingPopupPlacement"></a>   
### <a name="customizing-popup-placement"></a>Açılan yerleştirme özelleştirme  
 Yerleşimini özelleştirebileceğiniz bir <xref:System.Windows.Controls.Primitives.Popup> göreli üzeresiniz koordinatları kümesi belirterek denetim <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> istediğiniz <xref:System.Windows.Controls.Primitives.Popup> görünmesi.  
  
 Yerleştirme özelleştirmek için ayarlanmış <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliğine <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>. Ardından tanımlayan bir <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> için olası yerleştirme noktaları ve birincil eksenler (tercih sırasına göre) kümesini döndürür temsilci <xref:System.Windows.Controls.Primitives.Popup>. En büyük bölümünü gösteren noktası <xref:System.Windows.Controls.Primitives.Popup> otomatik olarak seçilir. Bir örnek için bkz: [özel açılan konumunu belirtin](../../../../docs/framework/wpf/controls/how-to-specify-a-custom-popup-position.md).  
  
<a name="PopupandtheVisualTree"></a>   
## <a name="popup-and-the-visual-tree"></a>Açılır ve görsel ağaç  
 A <xref:System.Windows.Controls.Primitives.Popup> denetim kendi görsel ağaç sahip değildir; bunun yerine bir boyutu 0 döndürür (sıfır) <xref:System.Windows.Controls.Primitives.Popup.MeasureOverride%2A> yöntemi <xref:System.Windows.Controls.Primitives.Popup> olarak adlandırılır. Ancak, belirlediğinizde <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> özelliği <xref:System.Windows.Controls.Primitives.Popup> için `true`, kendi görsel ağaç içeren yeni bir pencere oluşturulur. Yeni pencerede içeren <xref:System.Windows.Controls.Primitives.Popup.Child%2A> içeriğini <xref:System.Windows.Controls.Primitives.Popup>. Genişlik ve yükseklik yeni penceresinin genişliği yüzde 75'ini veya ekran yüksekliğini daha büyük olamaz.  
  
 <xref:System.Windows.Controls.Primitives.Popup> Denetim tutan bir başvuru kendi <xref:System.Windows.Controls.Primitives.Popup.Child%2A> mantıksal alt öğe olarak içerik. Yeni pencere oluşturulduğunda, içeriği <xref:System.Windows.Controls.Primitives.Popup> penceresinin görsel alt olur ve mantıksal alt öğesi kalır <xref:System.Windows.Controls.Primitives.Popup>. Buna karşılık, <xref:System.Windows.Controls.Primitives.Popup> mantıksal üstü olarak kalır, <xref:System.Windows.Controls.Primitives.Popup.Child%2A> içeriği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.Primitives.Popup>  
 <xref:System.Windows.Controls.Primitives.PopupPrimaryAxis>  
 <xref:System.Windows.Controls.Primitives.PlacementMode>  
 <xref:System.Windows.Controls.Primitives.CustomPopupPlacement>  
 <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipService>  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)
