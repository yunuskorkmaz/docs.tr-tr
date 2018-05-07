---
title: 'Nasıl yapılır: Windows Forms ListView Denetiminde Öğe Seçme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lists [Windows Forms], selecting items
- ListView control [Windows Forms], selecting items
- selection [Windows Forms], in list views
- list views [Windows Forms], selecting items
ms.assetid: ddea918e-1ddf-47f4-bd09-1e9b4c9d0c39
ms.openlocfilehash: 8256eaeddf98c5a0dd80357bcd562e8f66db85b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-select-an-item-in-the-windows-forms-listview-control"></a>Nasıl yapılır: Windows Forms ListView Denetiminde Öğe Seçme
Bu örnek program aracılığıyla bir Windows Forms öğeyi seçmek gösterilmiştir <xref:System.Windows.Forms.ListView> denetim. Bir öğe program aracılığıyla seçme otomatik olarak değişmez odağı <xref:System.Windows.Forms.ListView> denetim. Bu nedenle, genellikle aynı zamanda öğesi bir öğeyi seçerken odaklanmış olarak ayarlamak istediğiniz.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.ListView.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   A <xref:System.Windows.Forms.ListView> adlı Denetim `listView1` en az bir öğe içeriyor.  
  
-   Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> ad alanları.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListViewItem.Selected%2A?displayProperty=nameWithType>
