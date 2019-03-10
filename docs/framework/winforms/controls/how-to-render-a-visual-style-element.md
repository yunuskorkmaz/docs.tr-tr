---
title: 'Nasıl yapılır: Bir görsel stilde öğe işleme'
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
ms.openlocfilehash: 33c73bf8faa9dfafe5f4889875887dc3aef5985c
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714118"
---
# <a name="how-to-render-a-visual-style-element"></a>Nasıl yapılır: Bir görsel stilde öğe işleme
<xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> Ad alanı sunan <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> arabirimi (UI) öğeleri görsel stilleri tarafından desteklenen Windows kullanıcı temsil eden nesneleri. Bu konu nasıl kullanılacağını gösterir <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> sınıf, işlenecek <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> temsil eden **Oturumu Kapat** ve **Kapat** başlangıç menüsünde düğmeleri.  
  
### <a name="to-render-a-visual-style-element"></a>Bir görsel stilde öğe işleme için  
  
1.  Oluşturma bir <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> çizmek istediğiniz öğesine ayarlayın. Kullanımına dikkat edin <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A?displayProperty=nameWithType> özelliği ve <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.IsElementDefined%2A?displayProperty=nameWithType> yöntemi; <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor%2A> görsel stillerini devre dışı bırakıldı veya bir öğe tanımlanmamış Oluşturucusu bir özel durum oluşturur.  
  
     [!code-cpp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/cpp/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/VB/form1.vb#4)]  
  
2.  Çağrı <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.DrawBackground%2A> yöntem, öğe işleme <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> şu anda temsil eder.  
  
     [!code-cpp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/cpp/form1.cpp#6)]
     [!code-csharp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/VB/form1.vb#6)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Öğesinden türetilen özel denetim <xref:System.Windows.Forms.Control> sınıfı.  
  
-   A <xref:System.Windows.Forms.Form> özel denetimi barındıran.  
  
-   Başvurular <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, ve <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> ad alanları.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Denetimleri Görsel Stilde İşleme](rendering-controls-with-visual-styles.md)
