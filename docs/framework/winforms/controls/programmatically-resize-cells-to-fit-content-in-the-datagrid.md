---
title: DataGridView Denetimindeki Içeriği sığdırmak için programlı olarak hücreleri yeniden boyutlandırma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], resizing cells to fit content
- cells [Windows Forms], resizing to fit contents
- DataGridView control [Windows Forms], resizing cells
- grids [Windows Forms], resizing cells to fit content
ms.assetid: 63d770dc-b3f5-462b-901a-3125b2753792
ms.openlocfilehash: df3b378a8ba358fa0bfe549a7901b3d59d53f556
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742454"
---
# <a name="how-to-programmatically-resize-cells-to-fit-content-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde İçeriği Sığdıracak Şekilde Hücreleri Programlı Olarak Yeniden Boyutlandırma
Satırları, sütunları ve başlıkları, tüm değerlerini kesme olmadan görüntüleyecek şekilde yeniden boyutlandırmak için <xref:System.Windows.Forms.DataGridView> denetim yöntemlerini kullanabilirsiniz. Bu yöntemleri, <xref:System.Windows.Forms.DataGridView> öğelerini seçtiğiniz zaman yeniden boyutlandırmak için kullanabilirsiniz. Alternatif olarak, içeriği her değiştiğinde bu öğeleri otomatik olarak yeniden boyutlandırmak için denetimi de yapılandırabilirsiniz. Bu, ancak büyük veri kümeleriyle çalışırken ya da verileriniz sıklıkla değiştiğinde verimsiz olabilir. Daha fazla bilgi için [Windows Forms DataGridView Denetimindeki Boyutlandırma Seçenekleri](sizing-options-in-the-windows-forms-datagridview-control.md)bölümüne bakın.  
  
 Genellikle <xref:System.Windows.Forms.DataGridView> öğelerini, yalnızca bir veri kaynağından yeni veri yüklediğinizde veya Kullanıcı bir değeri düzenlediğinde içeriğe uyacak şekilde ayarlayacaksınız. Bu, performansı iyileştirmek için yararlıdır, ancak kullanıcılarınızın satırları ve sütunları fareyle el ile yeniden boyutlandırmasını sağlamak istediğinizde de yararlıdır.  
  
 Aşağıdaki kod örneği, programlama için yeniden boyutlandırma için kullanabileceğiniz seçenekleri gösterir.  
  
## <a name="example"></a>Örnek  
 [!code-cpp[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/CPP/programmaticsizing.cpp#0)]
 [!code-csharp[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/CS/programmaticsizing.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/VB/programmaticsizing.vb#0)]  
  
## <a name="compiling-the-code"></a>Kod Derleme  
 Bu örnek şunları gerektirir:  
  
- System, System. Drawing ve System. Windows. Forms derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeRowMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>
- <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>
- <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>
- [Windows Forms DataGridView Denetiminde Hücre ve Satırları Yeniden Boyutlandırma](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimindeki Boyutlandırma Seçenekleri](sizing-options-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView Denetiminde İçerik Değiştiğinde Hücreleri Otomatik Olarak Yeniden Boyutlandırma](automatically-resize-cells-when-content-changes-in-the-datagrid.md)
