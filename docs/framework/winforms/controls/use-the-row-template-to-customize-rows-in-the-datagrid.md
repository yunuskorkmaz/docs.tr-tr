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
ms.openlocfilehash: 0dba318e6aa35761f4e9471fdb13b65644747b57
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966499"
---
# <a name="how-to-use-the-row-template-to-customize-rows-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetimindeki Satırları Özelleştirmek için Satır Şablonunu Kullanma
Denetim, veri bağlama yoluyla veya kullanmak üzere varolan bir satırı belirtmeden <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> yöntemi çağırdığınızda denetime eklediği tüm satırların temeli olarak satır şablonunu kullanır. <xref:System.Windows.Forms.DataGridView>  
  
 Satır şablonu, <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> özelliğin sağladığı satırların görünümü ve davranışı üzerinde daha fazla denetim sağlar. Satır şablonuyla, dahil olmak üzere <xref:System.Windows.Forms.DataGridViewRow> <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>herhangi bir özelliği ayarlayabilirsiniz.  
  
 Belirli bir etkiye ulaşmak için satır şablonunu kullanmanız gereken bazı durumlar vardır. Örneğin, satır yüksekliği bilgileri bir <xref:System.Windows.Forms.DataGridViewCellStyle>içinde depolanamaz, bu nedenle tüm satırlar tarafından kullanılan varsayılan yüksekliği değiştirmek için bir satır şablonu kullanmanız gerekir. Satır şablonu Ayrıca, ' dan <xref:System.Windows.Forms.DataGridViewRow> türetilmiş kendi sınıflarınızı oluşturduğunuz ve denetime yeni satırlar eklendiğinde özel türü kullanmak istediğiniz zaman da yararlıdır.  
  
> [!NOTE]
> Satır şablonu yalnızca satırlar eklendiğinde kullanılır. Satır şablonunu değiştirerek mevcut satırları değiştiremezsiniz.  
  
### <a name="to-use-the-row-template"></a>Satır şablonunu kullanmak için  
  
- <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> Özelliğinden alınan nesnedeki özellikleri ayarlayın.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CPP/datagridviewrowtemplate.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CS/datagridviewrowtemplate.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/VB/datagridviewrowtemplate.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- <xref:System.Windows.Forms.DataGridView> Adlı`dataGridView1`bir denetim.  
  
- <xref:System?displayProperty=nameWithType> ,<xref:System.Drawing?displayProperty=nameWithType>Ve derlemelerinin<xref:System.Windows.Forms?displayProperty=nameWithType> başvuruları.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimindeki Hücre Stilleri](cell-styles-in-the-windows-forms-datagridview-control.md)
