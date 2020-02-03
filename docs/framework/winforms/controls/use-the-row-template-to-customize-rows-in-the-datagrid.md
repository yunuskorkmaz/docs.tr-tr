---
title: DataGridView Denetimindeki satırları özelleştirmek için satır şablonunu kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- DataGridView control [Windows Forms], customizing rows
ms.assetid: 6db61607-7e57-4a84-8d63-9d6a7ed7f9ff
ms.openlocfilehash: 35cb95f22c0caa654bf149b5fc4fd0395696a411
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728389"
---
# <a name="how-to-use-the-row-template-to-customize-rows-in-the-windows-forms-datagridview-control"></a>Nasıl Yapılır: Windows Forms DataGridView Denetimindeki Satırları Özelleştirmek için Satır Şablonunu Kullanma
<xref:System.Windows.Forms.DataGridView> denetimi, veri bağlama yoluyla veya kullanılacak varolan bir satırı belirtmeden <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> yöntemini çağırdığınızda, satır şablonunu denetime eklediği tüm satırların temeli olarak kullanır.  
  
 Satır şablonu, <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> özelliğin sağladığı satırların görünümü ve davranışı üzerinde daha fazla denetim sağlar. Satır şablonuyla, <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>dahil olmak üzere herhangi bir <xref:System.Windows.Forms.DataGridViewRow> özelliğini ayarlayabilirsiniz.  
  
 Belirli bir etkiye ulaşmak için satır şablonunu kullanmanız gereken bazı durumlar vardır. Örneğin, satır yüksekliği bilgileri bir <xref:System.Windows.Forms.DataGridViewCellStyle>depolanamaz, bu nedenle tüm satırlar tarafından kullanılan varsayılan yüksekliği değiştirmek için bir satır şablonu kullanmanız gerekir. Satır şablonu Ayrıca, <xref:System.Windows.Forms.DataGridViewRow> türetilen kendi sınıflarınızı oluşturduğunuzda ve denetime yeni satırlar eklendiğinde özel türü kullanmak istediğinizde de yararlı olur.  
  
> [!NOTE]
> Satır şablonu yalnızca satırlar eklendiğinde kullanılır. Satır şablonunu değiştirerek mevcut satırları değiştiremezsiniz.  
  
### <a name="to-use-the-row-template"></a>Satır şablonunu kullanmak için  
  
- <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> özelliğinden alınan nesnedeki özellikleri ayarlayın.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CPP/datagridviewrowtemplate.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CS/datagridviewrowtemplate.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/VB/datagridviewrowtemplate.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- `dataGridView1`adlı <xref:System.Windows.Forms.DataGridView> denetim.  
  
- <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimindeki Hücre Stilleri](cell-styles-in-the-windows-forms-datagridview-control.md)
