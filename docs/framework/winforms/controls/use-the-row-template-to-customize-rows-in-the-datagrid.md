---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetimindeki Satırları Özelleştirmek için Satır Şablonunu Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- DataGridView control [Windows Forms], customizing rows
ms.assetid: 6db61607-7e57-4a84-8d63-9d6a7ed7f9ff
ms.openlocfilehash: cb3a826262a49a8653e3a344bd126d434f2522dd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59073066"
---
# <a name="how-to-use-the-row-template-to-customize-rows-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetimindeki Satırları Özelleştirmek için Satır Şablonunu Kullanma
<xref:System.Windows.Forms.DataGridView> Denetimi denetimine veri bağlama aracılığıyla ya da çağırdığınızda ekler tüm satırlar için temel olarak satır şablonunu kullanır <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> kullanmak için mevcut bir satırı belirtmeden yöntemi.  
  
 Satır şablonunu görünümünü ve davranışını satır üzerinde daha fazla denetim verir <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> özelliği sağlar. Satır şablonla herhangi ayarlayabilirsiniz <xref:System.Windows.Forms.DataGridViewRow> özellikleri dahil olmak üzere, <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>.  
  
 Burada belirli etkiyi elde etmek için satır şablonunu kullanma gerekir bazı durumlar vardır. Örneğin, satır yüksekliğini bilgi içinde depolanamaz bir <xref:System.Windows.Forms.DataGridViewCellStyle>, tüm satırları tarafından kullanılan varsayılan yükseklik değiştirmek için satır şablonunu kullanmanız gerekir. Satır şablonunu de kendi sınıflar türetilmiş oluşturduğunuzda yararlıdır <xref:System.Windows.Forms.DataGridViewRow> ve denetime yeni satır eklendiğinde kullanılan özel türünüzü istediğiniz.  
  
> [!NOTE]
>  Yalnızca satır eklendiğinde satır şablonunu kullanılır. Var olan satır satır şablonunu değiştirerek değiştiremezsiniz.  
  
### <a name="to-use-the-row-template"></a>İçin satır şablonunu kullanma  
  
-   Alınan nesne üzerindeki özellikleri ayarlamak <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> özelliği.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CPP/datagridviewrowtemplate.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CS/datagridviewrowtemplate.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/VB/datagridviewrowtemplate.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.  
  
-   Başvurular <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimindeki Hücre Stilleri](cell-styles-in-the-windows-forms-datagridview-control.md)
