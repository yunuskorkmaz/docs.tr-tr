---
title: 'Nasıl yapılır: Görsel Stilde Öğe İşleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- visual themes [Windows Forms], applying to elements of Windows Forms applications
- professional appearance [Windows Forms], applying to elements of Windows Forms applications
- visual styles [Windows Forms], rendering Windows Forms controls
ms.assetid: a207781b-1baa-4ce9-b788-1e951bd4b5df
ms.openlocfilehash: 284fca2d3f2b8f47b60e4d9c639df4a6bd43c701
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537628"
---
# <a name="how-to-render-a-visual-style-element"></a>Nasıl yapılır: Görsel Stilde Öğe İşleme
<xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> Ad alanı sunan <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> Windows kullanıcısını temsil eden nesneler arabirimi (UI) öğeleri görsel stiller tarafından desteklenir. Bu konuda nasıl kullanılacağı gösterilir <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> işlemek için sınıf <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> temsil eden **Oturumu Kapat** ve **Kapat** Başlat menüsünün düğmeler.  
  
### <a name="to-render-a-visual-style-element"></a>Görsel stilde öğe işleme için  
  
1.  Oluşturma bir <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> ve istediğiniz çizmek için öğesini ayarlayın. Kullanımına dikkat edin <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A?displayProperty=nameWithType> özelliği ve <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.IsElementDefined%2A?displayProperty=nameWithType> yöntemi; <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor%2A> görsel stiller devre dışı bırakılır veya öğenin tanımsızdır Oluşturucusu bir özel durum oluşturur.  
  
     [!code-cpp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/cpp/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/VB/form1.vb#4)]  
  
2.  Çağrı <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.DrawBackground%2A> yönteme öğe işleme <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> şu anda temsil eder.  
  
     [!code-cpp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/cpp/form1.cpp#6)]
     [!code-csharp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/VB/form1.vb#6)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Özel bir denetim türetilmiş <xref:System.Windows.Forms.Control> sınıfı.  
  
-   A <xref:System.Windows.Forms.Form> özel denetim barındıran.  
  
-   Başvurular <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, ve <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> ad alanları.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Denetimleri Görsel Stilde İşleme](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)
