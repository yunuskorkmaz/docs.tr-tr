---
title: Açılır Pencereye Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Popup
- Popup control [WPF], about Popup control
ms.assetid: 774f53ca-bff8-470e-9ce9-3928b4cf3d4c
ms.openlocfilehash: 370970c80221e371db5a97303ef2650d14300b14
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59102784"
---
# <a name="popup-overview"></a>Açılır Pencereye Genel Bakış
<xref:System.Windows.Controls.Primitives.Popup> Denetimi geçerli uygulama penceresi göre belirlenen bir öğe veya Ekran koordinatı üzerinde gezinen ayrı bir pencerede içeriği görüntülemek için bir yol sağlar. Bu konu tanıtır <xref:System.Windows.Controls.Primitives.Popup> denetlemek ve kullanımı hakkında bilgi sağlar.  

<a name="What_Is_a_Popup_"></a>   
## <a name="what-is-a-popup"></a>Açılan pencere nedir?  
 A <xref:System.Windows.Controls.Primitives.Popup> denetim ekranda bir öğe veya göreli ayrı bir pencerede içeriğini görüntüler. Zaman <xref:System.Windows.Controls.Primitives.Popup> görünür durumda <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> özelliği `true`.  
  
> [!NOTE]
>  A <xref:System.Windows.Controls.Primitives.Popup> kendi üst nesnenin üzerine fare işaretçisi hareket ettirildiğinde otomatik olarak açılmaz. İsterseniz bir <xref:System.Windows.Controls.Primitives.Popup> otomatik olarak açmak için <xref:System.Windows.Controls.ToolTip> veya <xref:System.Windows.Controls.ToolTipService> sınıfı. Daha fazla bilgi için [ToolTip genel bakışı](tooltip-overview.md).  
  
<a name="APopupExample"></a>   
## <a name="creating-a-popup"></a>Açılan pencere oluşturma  
 Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.Primitives.Popup> denetim alt öğesi olan bir <xref:System.Windows.Controls.Button> denetimi. Çünkü bir <xref:System.Windows.Controls.Button> yalnızca bir alt öğesi olabilir, bu örnek için metin yerleştirir <xref:System.Windows.Controls.Button> ve <xref:System.Windows.Controls.Primitives.Popup> denetimlerini bir <xref:System.Windows.Controls.StackPanel>. İçeriği <xref:System.Windows.Controls.Primitives.Popup> görünür bir <xref:System.Windows.Controls.TextBlock> yakın ilgili uygulama penceresi üzerinde gezinen ayrı bir pencerede metnini görüntüleyen denetimi <xref:System.Windows.Controls.Button> denetimi.  
  
 [!code-xaml[PopupSimple#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#1)]  
  
 [!code-xaml[PopupSimple#CreatePopupCodeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#createpopupcodexaml)]  
  
<a name="PopupUses"></a>   
## <a name="controls-that-implement-a-popup"></a>Açılan pencere uygulama denetimleri  
 Oluşturabileceğinizi <xref:System.Windows.Controls.Primitives.Popup> diğer denetimlere denetimleri. Aşağıdaki denetimler uygulamak <xref:System.Windows.Controls.Primitives.Popup> denetimi belirli kullanımlar için:  
  
-   <xref:System.Windows.Controls.ToolTip>. Bir öğe için bir araç ipucu oluşturmak istediğiniz kullanırsanız <xref:System.Windows.Controls.ToolTip> ve <xref:System.Windows.Controls.ToolTipService> sınıfları. Daha fazla bilgi için [ToolTip genel bakışı](tooltip-overview.md).  
  
-   <xref:System.Windows.Controls.ContextMenu>. Bir öğe için bir bağlam menüsü oluşturmak istediğiniz kullanırsanız <xref:System.Windows.Controls.ContextMenu> denetimi. Daha fazla bilgi için [ContextMenu genel bakış](contextmenu-overview.md).  
  
-   <xref:System.Windows.Controls.ComboBox>. Gösterilen veya gizlenen, kullanım olabilir bir açılan liste kutusu olan bir seçim denetim oluşturmak istiyorsanız <xref:System.Windows.Controls.ComboBox> denetimi.  
  
-   <xref:System.Windows.Controls.Expander>. İçerik görüntüleyen daraltılabilir bir alana sahip bir üstbilgi görüntüleyen bir denetimi oluşturmak istiyorsanız, kullanın <xref:System.Windows.Controls.Expander> denetimi. Daha fazla bilgi için [genişleticiye genel bakış](expander-overview.md).  
  
<a name="PopupBehaviorandAppearance"></a>   
## <a name="popup-behavior-and-appearance"></a>Açılan pencere davranışı ve görünümü  
 <xref:System.Windows.Controls.Primitives.Popup> Denetim kendi davranış ve görünümünü özelleştirmenize olanak sağlayan işlevselliği sağlar. Örneğin, ayarlayabilirsiniz açma ve kapama davranışı, animasyon, saydamlık, bit eşlem efektleri, ve <xref:System.Windows.Controls.Primitives.Popup> boyut ve konum.  
  
<a name="OpenandCloseBehavior"></a>   
### <a name="open-and-close-behavior"></a>Açma ve kapama davranışı  
 A <xref:System.Windows.Controls.Primitives.Popup> denetiminin içeriğini görüntüler olduğunda <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> özelliği `true`. Varsayılan olarak, <xref:System.Windows.Controls.Primitives.Popup> kadar açık kalır <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> özelliği `false`. Ancak, ayarlayarak varsayılan davranışı değiştirebilirsiniz <xref:System.Windows.Controls.Primitives.Popup.StaysOpen%2A> özelliğini `false`. Bu özelliği ayarlandığında `false`, <xref:System.Windows.Controls.Primitives.Popup> içerik pencere fare yakalamayı sahiptir. <xref:System.Windows.Controls.Primitives.Popup> Bir fare olayına dışında oluştuğunda fare yakalama ve pencereyi kapatır kaybeder <xref:System.Windows.Controls.Primitives.Popup> penceresi.  
  
 <xref:System.Windows.Controls.Primitives.Popup.Opened> Ve <xref:System.Windows.Controls.Primitives.Popup.Closed> olayları oluştuğunda, <xref:System.Windows.Controls.Primitives.Popup> içerik penceresi açık veya kapalı.  
  
<a name="Animation"></a>   
### <a name="animation"></a>Animasyon  
 <xref:System.Windows.Controls.Primitives.Popup> Denetim belirme ve slayt açma gibi davranışları ile ilişkili genellikle animasyonlar için yerleşik desteği vardır. Ayarlayarak bu animasyonları etkinleştirebilirsiniz <xref:System.Windows.Controls.Primitives.Popup.PopupAnimation%2A> özelliğini bir <xref:System.Windows.Controls.Primitives.PopupAnimation> numaralandırma değeri. İçin <xref:System.Windows.Controls.Primitives.Popup> animasyonlarının doğru çalışması için ayarlamanız gerekir <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> özelliğini `true`.  
  
 Ayrıca gibi animasyon uygulayabilirsiniz <xref:System.Windows.Media.Animation.Storyboard> için <xref:System.Windows.Controls.Primitives.Popup> denetimi.  
  
<a name="OpacityandBitmapEffects"></a>   
### <a name="opacity-and-bitmap-effects"></a>Opaklık ve bit eşlem efektleri  
 <xref:System.Windows.UIElement.Opacity%2A> Özelliği için bir <xref:System.Windows.Controls.Primitives.Popup> denetim içeriği üzerinde hiçbir etkisi. Varsayılan olarak, <xref:System.Windows.Controls.Primitives.Popup> donuk içerik penceresi. Saydam oluşturmak için <xref:System.Windows.Controls.Primitives.Popup>ayarlayın <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> özelliğini `true`.  
  
 İçeriği bir <xref:System.Windows.Controls.Primitives.Popup> bit eşlem efektleri gibi devralmıyor <xref:System.Windows.Media.Effects.DropShadowBitmapEffect>, doğrudan üzerinde ayarladığınız <xref:System.Windows.Controls.Primitives.Popup> denetim veya herhangi bir üst pencere öğesinde. Bit eşlem efektleri içeriğine görünmesi için bir <xref:System.Windows.Controls.Primitives.Popup>, içeriği doğrudan bit eşlem etkisini ayarlamanız gerekir. Örneğin, alt öğesi olan bir <xref:System.Windows.Controls.Primitives.Popup> olduğu bir <xref:System.Windows.Controls.StackPanel>, bit eşlem etkisi ayarlayın <xref:System.Windows.Controls.StackPanel>.  
  
<a name="PopupSize"></a>   
### <a name="popup-size"></a>Açılan pencere boyutu  
 Varsayılan olarak, bir <xref:System.Windows.Controls.Primitives.Popup> için içeriği otomatik olarak boyutlandırılır. Otomatik boyutlandırma ortaya çıktığında, bazı bit eşlem efektleri için gizlenebilir ekran alan için tanımlanan varsayılan boyutu <xref:System.Windows.Controls.Primitives.Popup> içeriği görüntülemek bit eşlem efektleri için yeterli alanı sağlamaz.  
  
 <xref:System.Windows.Controls.Primitives.Popup> İçerik ayrıca ayarladığınızda görünmeyebilir bir <xref:System.Windows.UIElement.RenderTransform%2A> içeriğe. Bu senaryoda, bazı içeriklerin gizlenmiş olabilir dönüştürülmüş içeriğini <xref:System.Windows.Controls.Primitives.Popup> özgün alan genişletir <xref:System.Windows.Controls.Primitives.Popup>. Daha fazla alan bir bit eşlem etkisi veya dönüştürme gerektiriyorsa, geçici bir kenar boşluğu tanımlayabilirsiniz <xref:System.Windows.Controls.Primitives.Popup> içerik için bir denetim alanı sağlamak için.  
  
<a name="DefiningPopupPosition"></a>   
## <a name="defining-the-popup-position"></a>Açılan pencerenin konumunu tanımlama  
 Popup ayarlayarak konumlandırabilirsiniz <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, ve <xref:System.Windows.Controls.Primitives.Popup.VerticalOffsetProperty> özellikleri. Daha fazla bilgi için [açılan pencere yerleştirme davranışı](popup-placement-behavior.md). Zaman <xref:System.Windows.Controls.Primitives.Popup> görüntülenen üst yeniden konumlandırıldığında varsa ekranda, kendisi yeniden konumlandırmıyor.  
  
<a name="CustomizingPopupPlacement"></a>   
### <a name="customizing-popup-placement"></a>Açılan Pencere yerleştirme özelleştirme  
 Yerleşimini özelleştirebilirsiniz bir <xref:System.Windows.Controls.Primitives.Popup> denetimi için göreli koordinatları kümesini belirterek <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> istediğiniz <xref:System.Windows.Controls.Primitives.Popup> görüntülenecek.  
  
 Yerleştirme özelleştirmek için ayarlanmış <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> özelliğini <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>. Ardından tanımlayan bir <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> için bir dizi olası yerleştirme noktası ve birincil eksenleri (tercih sırasına göre) döndüren bir temsilci <xref:System.Windows.Controls.Primitives.Popup>. En büyük bölümünü gösteren noktası <xref:System.Windows.Controls.Primitives.Popup> otomatik olarak seçilir. Bir örnek için bkz. [özel açılan pencerenin konumunu belirtme](how-to-specify-a-custom-popup-position.md).  
  
<a name="PopupandtheVisualTree"></a>   
## <a name="popup-and-the-visual-tree"></a>Açılır ve görsel ağaç  
 A <xref:System.Windows.Controls.Primitives.Popup> kendi görsel ağacı denetimi sahip değil; bunun yerine bir boyutu 0 döndürür (sıfır) <xref:System.Windows.Controls.Primitives.Popup.MeasureOverride%2A> yöntemi <xref:System.Windows.Controls.Primitives.Popup> çağrılır. Ancak, ayarladığınızda <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> özelliği <xref:System.Windows.Controls.Primitives.Popup> için `true`, kendi görsel ağacını içeren yeni bir pencere oluşturulur. Yeni pencere içerir <xref:System.Windows.Controls.Primitives.Popup.Child%2A> içeriğini <xref:System.Windows.Controls.Primitives.Popup>. Genişlik ve yükseklik yeni pencerenin genişliğini yüzde 75'i veya ekran yüksekliği daha büyük olamaz.  
  
 <xref:System.Windows.Controls.Primitives.Popup> Denetimi bir başvuru tutar, <xref:System.Windows.Controls.Primitives.Popup.Child%2A> mantıksal alt öğe olarak içerik. Yeni pencere oluşturulduğunda, içeriğini <xref:System.Windows.Controls.Primitives.Popup> görsel alt pencerenin olur ve mantıksal alt kalan <xref:System.Windows.Controls.Primitives.Popup>. Buna karşılık, <xref:System.Windows.Controls.Primitives.Popup> mantıksal üst kalır, <xref:System.Windows.Controls.Primitives.Popup.Child%2A> içeriği.  
  
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
