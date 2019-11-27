---
title: UI Otomasyonu Kullanarak Katıştırılmış Nesnelere Erişme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- embedded objects, accessing
- accessing embedded objects
- UI Automation, accessing embedded objects
ms.assetid: a5b513ec-7fa6-4460-869f-c18ff04f7cf2
ms.openlocfilehash: 75c63360eab2cde95698bdaded5c5249a3ca89fd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447260"
---
# <a name="access-embedded-objects-using-ui-automation"></a>UI Otomasyonu Kullanarak Katıştırılmış Nesnelere Erişme
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, bir metin denetiminin içeriği içine katıştırılmış nesneleri göstermek için [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] nasıl kullanılabileceğini gösterir.  
  
> [!NOTE]
> Katıştırılmış nesneler görüntüleri, köprüleri, düğmeleri, tabloları ya da ActiveX denetimlerini içerebilir.  
  
 Katıştırılmış nesneler [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] metin sağlayıcısının alt öğeleri olarak değerlendirilir. Bu, diğer tüm [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] öğeleriyle aynı UI Otomasyon ağacı yapısıyla açığa çıkmalarını sağlar. İşlevsellik, genellikle katıştırılmış nesneler denetim türü için gerekli olan denetim desenleri aracılığıyla sunulur (örneğin, köprüler metin tabanlı olduğundan <xref:System.Windows.Automation.TextPattern>destekleyecektir).  
  
 ![Metin kapsayıcısındaki katıştırılmış nesneler.](./media/uia-textpattern-embeddedobjects.PNG "UIA_TextPattern_EmbeddedObjects")  
Metinsel içeriğe sahip bir örnek belge ("tanıyor muydunuz?" ...) ve kod örnekleri için hedef olarak kullanılan iki katıştırılmış nesne (bir Haale ve bir metin köprüsü resmi).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] metin sağlayıcısından katıştırılmış nesneler koleksiyonunun nasıl alınacağını gösterir. Giriş bölümünde belirtilen örnek belge için iki nesne döndürülür (bir görüntü öğesi ve bir metin öğesi).  
  
> [!NOTE]
> Görüntü öğesi, genellikle <xref:System.Windows.Automation.AutomationElement.NameProperty> (örneğin, "mavi bir Whale") görüntüsünü açıklayan, onunla ilişkilendirilmiş bazı iç metinleri içermelidir. Ancak, görüntü nesnesini kapsayan bir metin aralığı elde edildiğinde, görüntü ne de metin akışında bu açıklayıcı metin döndürülmez.  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#GetChildren](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#getchildren)]
[!code-vb[FindText#GetChildren](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#getchildren)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bir metin aralığının bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] metin sağlayıcısı içinde katıştırılmış bir nesneden nasıl alınacağını gösterir. Alınan metin aralığı, başlangıç uç noktasının izlediği boş bir aralıktır "... Hint. (boşluk) "ve bitiş bitiş noktası, katıştırılmış köprüyü temsil eden". "işaretinden önce gelir (giriş bölümünde verilen görüntüde gösterildiği gibi). Bu boş bir Aralık olsa da, sıfır olmayan bir span içerdiğinden, bir bozuk aralığı olarak kabul edilmez.  
  
> [!NOTE]
> <xref:System.Windows.Automation.TextPattern> köprü gibi metin tabanlı gömülü bir nesne alabilir; Ancak, tam işlevselliğini göstermek için gömülü nesneden bir ikincil <xref:System.Windows.Automation.TextPattern> alınması gerekecektir.  
  
 [!code-csharp[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#getrangefromchild)]
 [!code-vb[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#getrangefromchild)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu TextPattern Öğesine Genel Bakış](ui-automation-textpattern-overview.md)
- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyonu Kullanarak Metin Kutusuna İçerik Ekleme](add-content-to-a-text-box-using-ui-automation.md)
- [UI Otomasyonunu Kullanarak Metin Bulma ve Vurgulama](find-and-highlight-text-using-ui-automation.md)
