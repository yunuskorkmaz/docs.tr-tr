---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunları Salt Okunur Yapma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], read-only columns
- DataGridView control [Windows Forms], read-only columns
ms.assetid: 2bb73ebb-1a55-4362-9fda-e50574c087d5
ms.openlocfilehash: c865db5caf33b34f12c7acf8078995b12db3c970
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649275"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunları Salt Okunur Yapma
Tüm veri düzenleme amacıyla yöneliktir. İçinde <xref:System.Windows.Forms.DataGridView> denetimindeki sütun <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> özellik değeri, kullanıcılar söz konusu sütundaki hücrelerin düzenleyip düzenleyemeyeceğini belirler. Salt okunur tamamen denetimi yapma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Önlemek satır eklemeyi ve silmeyi Windows Forms DataGridView denetiminde](prevent-row-addition-and-deletion-datagridview.md).  
  
 Visual Studio'da bu görevi için desteği yoktur.  Ayrıca bkz: [nasıl yapılır: Sütunları yapma salt okunur Windows Forms DataGridView denetiminde'nın Tasarımcı kullanarak](make-columns-read-only-in-the-datagrid-using-the-designer.md).  
  
### <a name="to-make-a-column-read-only-programmatically"></a>Salt okunur bir sütunu programlı bir şekilde yapmak için  
  
- Ayarlama <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType> özelliğini `true`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#064](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#064)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#064](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#064)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
- A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1` adlı bir sütunun `CompanyName`.  
  
- Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Nasıl yapılır: Satır eklemeyi ve silmeyi Windows Forms DataGridView denetiminde engelle](prevent-row-addition-and-deletion-datagridview.md)
