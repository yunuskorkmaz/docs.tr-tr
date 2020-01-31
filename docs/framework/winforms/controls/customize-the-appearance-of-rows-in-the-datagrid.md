---
title: DataGridView Denetimindeki satırların görünümünü özelleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- rows [Windows Forms], customizing in DataGridView control
- DataGridView control [Windows Forms], customizing rows
ms.assetid: d40b53d2-7e7c-48c5-8570-6e79d15c3bbb
ms.openlocfilehash: 099b2104e7a4887aa846c4d65273db2dd4f60559
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744033"
---
# <a name="how-to-customize-the-appearance-of-rows-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Satırların Görünüşünü Özelleştirme
<xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> ve <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> olaylarının bir veya her ikisini de işleyerek <xref:System.Windows.Forms.DataGridView> satırlarının görünümünü denetleyebilirsiniz. Bu olaylar, <xref:System.Windows.Forms.DataGridView> denetimine geri kalanı boyamak için yalnızca istediğiniz şeyi boyamak üzere tasarlanmıştır. Örneğin, özel bir arka plan boyamak isterseniz, <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> olayını işleyebilir ve tek tek hücrelerin kendi ön plan içeriğini boyamasına izin verebilirsiniz. Alternatif olarak, hücrelerin kendilerini boyamasına izin verebilir ve <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType> olayı için bir işleyiciye özel ön plan içeriği ekleyebilirsiniz. Ayrıca, hücre boyamayı devre dışı bırakıp <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType> olay işleyicisindeki her şeyi boyayabilirsiniz.  
  
 Aşağıdaki kod örneği, bir gradyan seçim arka planı ve birden çok sütuna yayılan bazı özel ön plan içerikleri sağlamak için her iki olay için işleyicileri uygular.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridViewRowPainting#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/CS/datagridviewrowpainting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewRowPainting#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/VB/datagridviewrowpainting.vb#00)]  
  
## <a name="compiling-the-code"></a>Kod Derleme  
 Bu örnek şunları gerektirir:  
  
- System, System. Drawing ve System. Windows. Forms derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>
- [Windows Forms DataGridView Denetimini Özelleştirme](customizing-the-windows-forms-datagridview-control.md)
- [DataGridView Denetimi Mimarisi](datagridview-control-architecture-windows-forms.md)
