---
title: DataGridView denetiminde satır eklemeyi ve silmeyi engelleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], disabling data entry
- data entry [Windows Forms], disabling in grids
- data grids [Windows Forms], disabling data entry
ms.assetid: ef9539ce-539b-404e-84b6-ac282b64b88c
ms.openlocfilehash: de8e0412faf8c3731f9356771b35a4a5d31b6ec7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728726"
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Satır Ekleme ve Silmeyi Engelleme
Bazen, kullanıcıların <xref:System.Windows.Forms.DataGridView> denetiinizden yeni veri satırları girmesini veya mevcut satırları silmelerini engellemek isteyebilirsiniz. <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> özelliği, denetimin alt kısmında yeni kayıtların satırının mevcut olup olmadığını gösterir, ancak <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> özelliği satırların kaldırılıp kaldırılamayacağını gösterir. Aşağıdaki kod örneği bu özellikleri kullanır ve ayrıca denetimi tamamen Salt okunabilir hale getirmek için <xref:System.Windows.Forms.DataGridView.ReadOnly%2A> özelliğini ayarlar.  
  
 Visual Studio 'da bu görev için destek vardır. Ayrıca bkz. [nasıl yapılır: tasarımcı kullanarak Windows Forms DataGridView denetiminde satır eklemeyi ve silmeyi engelleme](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#090](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#090)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#090](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#090)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- `dataGridView1`adlı <xref:System.Windows.Forms.DataGridView> denetim.  
  
- <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ReadOnly%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri](basic-column-row-and-cell-features-wf-datagridview-control.md)
