---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunların Sırasını Değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], changing order
- DataGridView control [Windows Forms], column order
- data grids [Windows Forms], changing column order
ms.assetid: 5e9ac3bc-b0f0-48cb-a3d5-b005af905395
ms.openlocfilehash: 90d262e738f092215e88e38e31169d74059e4401
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781231"
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunların Sırasını Değiştirme
Kullandığınızda, bir <xref:System.Windows.Forms.DataGridView> bir veri kaynağından verileri görüntülemek için veri kaynağı şemasındaki bazen sütunları görüntülemek istediğiniz sırayla görünmez. Görüntülenen sütunların sırasını kullanarak değiştirebileceğiniz <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A> özelliği <xref:System.Windows.Forms.DataGridViewColumn> sınıfı.  
  
 Aşağıdaki kod örneği Northwind örnek veritabanındaki Müşteriler tablosunu bağlama zaman otomatik olarak oluşturulan sütunların bazıları yeniden konumlandırır. Bağlama hakkında daha fazla bilgi için <xref:System.Windows.Forms.DataGridView> denetlemek için bir veritabanı tablosu, bkz: [nasıl yapılır: Veri bağlama Windows Forms DataGridView denetiminde](how-to-bind-data-to-the-windows-forms-datagridview-control.md).  
  
 Visual Studio'da bu görevi için desteği yoktur.  Ayrıca bkz: [nasıl yapılır: Tasarımcı kullanarak Windows Forms DataGridView denetiminde sütunların sırasını değiştirme](change-the-order-of-columns-in-the-datagrid-using-the-designer.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#040](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#040)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#040](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#040)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
- A <xref:System.Windows.Forms.DataGridView> adlı Denetim `customersDataGridView` bağlanan belirtilen sütun adları içeren bir tablo gibi `Customers` Northwind örnek veritabanındaki tablo.  
  
- Başvurular <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>, ve <xref:System.Xml?displayProperty=nameWithType> derlemeler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView Denetiminde Verileri Görüntüleme](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView denetimine veri bağlama](how-to-bind-data-to-the-windows-forms-datagridview-control.md)
