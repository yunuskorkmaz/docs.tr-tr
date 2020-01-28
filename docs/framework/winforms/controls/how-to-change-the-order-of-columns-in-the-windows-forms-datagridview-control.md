---
title: DataGridView Denetimindeki sütunların sırasını değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], changing order
- DataGridView control [Windows Forms], column order
- data grids [Windows Forms], changing column order
ms.assetid: 5e9ac3bc-b0f0-48cb-a3d5-b005af905395
ms.openlocfilehash: 2aef196e9544a81f42a563783ce6c357869aa247
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746549"
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunların Sırasını Değiştirme
Bir veri kaynağındaki verileri göstermek için <xref:System.Windows.Forms.DataGridView> kullandığınızda, veri kaynağının şemasındaki sütunların bazen bunları göstermek istediğiniz sırada görünmemelidir. <xref:System.Windows.Forms.DataGridViewColumn> sınıfının <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A> özelliğini kullanarak sütunların görüntülenme sırasını değiştirebilirsiniz.  
  
 Aşağıdaki kod örneği, Northwind örnek veritabanındaki Customers tablosuna bağlanırken otomatik olarak oluşturulan sütunlardan bazılarını konumlandırır. <xref:System.Windows.Forms.DataGridView> denetimini bir veritabanı tablosuna bağlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: verileri Windows Forms DataGridView denetimine bağlama](how-to-bind-data-to-the-windows-forms-datagridview-control.md).  
  
 Visual Studio 'da bu görev için destek vardır.  Ayrıca bkz. [nasıl yapılır: Tasarımcıyı kullanarak Windows Forms DataGridView Denetimindeki sütunların sırasını değiştirme](change-the-order-of-columns-in-the-datagrid-using-the-designer.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#040](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#040)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#040](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#040)]  
  
## <a name="compiling-the-code"></a>Kod Derleme  
 Bu örnek şunları gerektirir:  
  
- Northwind örnek veritabanındaki `Customers` tablosu gibi, belirtilen sütun adlarıyla bir tabloya bağlanan `customersDataGridView` adlı <xref:System.Windows.Forms.DataGridView> denetim.  
  
- <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>ve <xref:System.Xml?displayProperty=nameWithType> derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView Denetiminde Verileri Görüntüleme](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView Denetimine Veri Bağlama](how-to-bind-data-to-the-windows-forms-datagridview-control.md)
