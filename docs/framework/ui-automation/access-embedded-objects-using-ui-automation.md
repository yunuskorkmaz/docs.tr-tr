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
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 4c7896cb8472ddf7037532707974380bf77e3b93
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54733135"
---
# <a name="access-embedded-objects-using-ui-automation"></a>UI Otomasyonu Kullanarak Katıştırılmış Nesnelere Erişme
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu başlığı altında gösterilir nasıl [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] bir metin denetiminin içeriğini katıştırılmış nesneleri göstermek için kullanılabilir.  
  
> [!NOTE]
>  Katıştırılmış nesneler içerebilir görüntüleri, köprüleri, düğmeler, tablolar veya ActiveX denetimlerini.  
  
 Katıştırılmış nesneler alt değerlendirilir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] metin sağlayıcısı. Bu aynı UI Otomasyonu ağaç yapısı olarak diğer tüm aracılığıyla kullanıma olanak tanıyan [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] öğeleri. İşlevleri, buna genellikle katıştırılmış nesneleri denetim türüne göre gerekli denetim desenleri aracılığıyla gösterilir (köprü metin tabanlı olduğundan, örneğin, destekleyecek <xref:System.Windows.Automation.TextPattern>).  
  
 ![Bir metin kapsayıcı katıştırılmış nesneler. ](../../../docs/framework/ui-automation/media/uia-textpattern-embeddedobjects.PNG "UIA_TextPattern_EmbeddedObjects")  
Bir örnek belge ile metinsel içeriği ("yaptığınız biliyor?" ...) ve kod örnekleri için bir hedef olarak kullanılan iki katıştırılmış nesneler (bir Whale'ı ve bir köprü bir resim).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, katıştırılmış nesneler koleksiyonunu içinden almak gösterilmiştir bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] metin sağlayıcısı. Giriş sağlanan örnek belge için iki nesne (bir görüntü öğesi ve bir metin öğesi) döndürülür.  
  
> [!NOTE]
>  Görüntü öğesi, genellikle görüntünün açıklayan ilişkili bazı iç metin olmalıdır, <xref:System.Windows.Automation.AutomationElement.NameProperty> (örneğin, "bir mavi whale."). Ancak, görüntünün ne bu açıklayıcı metin resim nesnesi kapsayan bir metin aralığını alındığında, metin akışında döndürülür.  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#GetChildren](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#getchildren)]
[!code-vb[FindText#GetChildren](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#getchildren)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bir metin aralığı içinde katıştırılmış bir nesne almak gösterilmiştir bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] metin sağlayıcısı. Alınan metin boş bir aralığın başlangıç uç noktası aşağıdaki "... yere aralığı Okyanusu. (boşluk) "ve kapatma bitiş uç nokta önündeki". "(giriş sağlanan görüntü gösterildiği gibi) katıştırılmış köprüyü temsil eden. Bu boş bir aralığın olsa da, sıfır olmayan bir aralık olduğundan, bozuk bir aralık olarak kabul edilmez.  
  
> [!NOTE]
>  <xref:System.Windows.Automation.TextPattern> bir metin tabanlı katıştırılmış nesne köprü gibi alabilirsiniz; Ancak, ikincil <xref:System.Windows.Automation.TextPattern> tam işlevselliğini kullanıma sunmak için katıştırılmış nesneden alınması gerekir.  
  
 [!code-csharp[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#getrangefromchild)]
 [!code-vb[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#getrangefromchild)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [UI Otomasyonu TextPattern Öğesine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)
- [UI Otomasyonu Denetim Desenlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [UI Otomasyonu Kullanarak Metin Kutusuna İçerik Ekleme](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)
- [UI Otomasyonunu Kullanarak Metin Bulma ve Vurgulama](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)
