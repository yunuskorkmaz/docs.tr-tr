---
title: "UI Otomasyonu Kullanarak Katıştırılmış Nesnelere Erişme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- embedded objects, accessing
- accessing embedded objects
- UI Automation, accessing embedded objects
ms.assetid: a5b513ec-7fa6-4460-869f-c18ff04f7cf2
caps.latest.revision: "17"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 37110708efa49912d0ed9c81746d125167e17985
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="access-embedded-objects-using-ui-automation"></a>UI Otomasyonu Kullanarak Katıştırılmış Nesnelere Erişme
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konuda gösterilmektedir nasıl [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] metin denetiminin içeriğine katıştırılmış nesneler kullanıma sunmak için kullanılabilir.  
  
> [!NOTE]
>  Katıştırılmış nesneler içerebilir görüntüleri, köprüler, düğmeleri, tablolar veya ActiveX denetimleri.  
  
 Katıştırılmış nesneler alt olarak kabul edilir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] metin sağlayıcısı. Bu aynı UI Otomasyonu ağaç yapısını diğer tüm aracılığıyla gösterilmesine izin veren [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] öğeleri. İşlevselliği, buna karşılık, genellikle katıştırılmış nesneler denetim türü tarafından gerekli denetim düzenleri aracılığıyla gösterilir (örneğin, köprü metin tabanlı olduğundan destekledikleri <xref:System.Windows.Automation.TextPattern>).  
  
 ![Katıştırılmış nesneler metin kapsayıcısında. ] (../../../docs/framework/ui-automation/media/uia-textpattern-embeddedobjects.PNG "UIA_TextPattern_EmbeddedObjects")  
Örnek bir belge içerikle metinsel ("vermedi biliyor?" ...) ve iki kod örnekleri için hedef olarak kullanılan nesneler (uygulanýr ve bir köprü resim), katıştırılmış.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde katıştırılmış nesneler koleksiyonunu içinden almak nasıl gösteren bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] metin sağlayıcısı. Giriş sağlanan örnek belge için iki nesne (bir görüntü öğesi ve bir metin öğesi) döndürülür.  
  
> [!NOTE]
>  Bir görüntü öğesi içinde görüntüyü genellikle açıklayan ilişkili bazı iç metin olmalıdır, <xref:System.Windows.Automation.AutomationElement.NameProperty> (örneğin, "bir mavi içinde."). Ancak, resim nesnesi yayılan bir metin aralığını alındığında, görüntünün ne bu açıklama metni metin akışında döndürülür.  
  
 [!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
 [!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#GetChildren](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#getchildren)]
[!code-vb[FindText#GetChildren](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#getchildren)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde içinde katıştırılmış bir nesneden bir metin aralığını edinme gösteren bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] metin sağlayıcısı. Alınan metin boş bir aralığın başlangıç endpoint izleyen "... burada aralığı Okyanusu. (boşluk) "ve kapanış bitiş endpoint önündeki". "katıştırılmış köprüyü temsil eden (giriş sağlanan görüntüsü gösterildiği gibi). Bu boş bir aralığın olsa da, sıfır olmayan span içerdiğinden, bozuk bir aralığı dikkate alınmaz.  
  
> [!NOTE]
>  <xref:System.Windows.Automation.TextPattern>bir metin tabanlı katıştırılmış nesne bir köprü gibi alabilirsiniz; Ancak, ikincil bir <xref:System.Windows.Automation.TextPattern> tam işlevselliğini kullanıma sunmak için katıştırılmış nesneden alınması gerekir.  
  
 [!code-csharp[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#getrangefromchild)]
 [!code-vb[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#getrangefromchild)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UI Otomasyonu TextPattern Öğesine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)  
 [UI Otomasyonu Denetim Desenlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [UI Otomasyonu Kullanarak Metin Kutusuna İçerik Ekleme](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)  
 [UI Otomasyonunu Kullanarak Metin Bulma ve Vurgulama](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)
