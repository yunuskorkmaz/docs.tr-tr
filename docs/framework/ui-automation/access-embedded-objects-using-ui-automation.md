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
ms.openlocfilehash: 83e54da5fdb75e3da44009ec700102d6bd7ae5e9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937962"
---
# <a name="access-embedded-objects-using-ui-automation"></a>UI Otomasyonu Kullanarak Katıştırılmış Nesnelere Erişme
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu başlığı altında [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] , bir metin denetiminin içeriği içine katıştırılmış nesneleri ortaya çıkarmak için nasıl kullanılabilecekleri gösterilmektedir.  
  
> [!NOTE]
> Katıştırılmış nesneler görüntüleri, köprüleri, düğmeleri, tabloları ya da ActiveX denetimlerini içerebilir.  
  
 Katıştırılmış nesneler [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] metin sağlayıcısının alt öğeleri olarak değerlendirilir. Bu, diğer [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] tüm öğeler ile aynı UI Otomasyon ağacı yapısıyla açığa çıkmalarını sağlar. İşlevsellik, genellikle katıştırılmış nesneler denetim türü için gerekli olan denetim desenleri aracılığıyla gösterilir (örneğin, köprüler, metin tabanlı <xref:System.Windows.Automation.TextPattern>olduğundan).  
  
 ![Metin kapsayıcısındaki katıştırılmış nesneler.](../../../docs/framework/ui-automation/media/uia-textpattern-embeddedobjects.PNG "UIA_TextPattern_EmbeddedObjects")  
Metinsel içeriğe sahip bir örnek belge ("tanıyor muydunuz?" ...) ve kod örnekleri için hedef olarak kullanılan iki katıştırılmış nesne (bir Haale ve bir metin köprüsü resmi).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] metin sağlayıcısı içinden katıştırılmış nesneler koleksiyonunun nasıl alınacağını gösterir. Giriş bölümünde belirtilen örnek belge için iki nesne döndürülür (bir görüntü öğesi ve bir metin öğesi).  
  
> [!NOTE]
> Görüntü öğesi, görüntüyü açıklayan, genellikle <xref:System.Windows.Automation.AutomationElement.NameProperty> (örneğin, "mavi bir Whale"), onunla ilişkilendirilmiş bir iç metin içermelidir. Ancak, görüntü nesnesini kapsayan bir metin aralığı elde edildiğinde, görüntü ne de metin akışında bu açıklayıcı metin döndürülmez.  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#GetChildren](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#getchildren)]
[!code-vb[FindText#GetChildren](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#getchildren)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] metin sağlayıcısı içindeki katıştırılmış bir nesneden bir metin aralığının nasıl alınacağını gösterir. Alınan metin aralığı, başlangıç uç noktasının izlediği boş bir aralıktır "... Hint. (boşluk) "ve bitiş bitiş noktası, katıştırılmış köprüyü temsil eden". "işaretinden önce gelir (giriş bölümünde verilen görüntüde gösterildiği gibi). Bu boş bir Aralık olsa da, sıfır olmayan bir span içerdiğinden, bir bozuk aralığı olarak kabul edilmez.  
  
> [!NOTE]
> <xref:System.Windows.Automation.TextPattern>köprü gibi metin tabanlı katıştırılmış bir nesne alabilir; Ancak, tam işlevselliğini <xref:System.Windows.Automation.TextPattern> göstermek için, ikincil nesnenin gömülü nesneden alınması gerekir.  
  
 [!code-csharp[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#getrangefromchild)]
 [!code-vb[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#getrangefromchild)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu TextPattern Öğesine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)
- [UI Otomasyonu Denetim Desenlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [UI Otomasyonu Kullanarak Metin Kutusuna İçerik Ekleme](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)
- [UI Otomasyonunu Kullanarak Metin Bulma ve Vurgulama](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)
