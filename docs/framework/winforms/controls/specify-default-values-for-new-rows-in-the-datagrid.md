---
title: DataGridView Denetimindeki yeni satırlar için varsayılan değerleri belirtme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], default values for new rows
- DataGridView control [Windows Forms], data entry
- rows [Windows Forms], specifying default values
- DataGridView control [Windows Forms], default values for new rows
ms.assetid: 8d127963-d9f8-4e4e-9f7f-beb66688f1f2
ms.openlocfilehash: 364f922aefc10e57f2ed7f3a0c2a5b25c922d87a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742938"
---
# <a name="how-to-specify-default-values-for-new-rows-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Yeni Satırlar İçin Varsayılan Değerleri Belirtme
Uygulama yeni eklenen satırlar için varsayılan değerleri doldurduğunda, veri girişini daha uygun hale getirebilirsiniz. <xref:System.Windows.Forms.DataGridView> sınıfıyla, varsayılan değerleri <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> olayı ile doldurabilirsiniz. Bu olay, Kullanıcı yeni kayıtlar için satırı girdiğinde tetiklenir. Kodunuz bu olayı işlediğinde, istediğiniz hücreleri tercih ettiğiniz değerlerle doldurabilirsiniz.  
  
 Aşağıdaki kod örneğinde, <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> olayını kullanarak yeni satırlar için varsayılan değerlerin nasıl belirtileceği gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#120)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#120)]  
  
## <a name="compiling-the-code"></a>Kod Derleme  
 Bu örnek şunları gerektirir:  
  
- `dataGridView1`adlı <xref:System.Windows.Forms.DataGridView> denetim.  
  
- Benzersiz `CustomerID` değerleri oluşturmak için `NewCustomerId` işlevi.  
  
- <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>
- [Windows Forms DataGridView Denetiminde Veri Girişi](data-entry-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Yeni Kayıtlar için Satır Kullanma](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
