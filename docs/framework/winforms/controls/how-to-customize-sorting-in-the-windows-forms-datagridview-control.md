---
title: DataGridView Denetiminde Sıralamayı Özelleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], sorting
- data grids [Windows Forms], customizing sorting
ms.assetid: 92fb5c14-afab-4cf5-a97e-924fd9cb99f5
ms.openlocfilehash: 20f581b2df6fd172a0a1998aed60c56b0306f2eb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743185"
---
# <a name="how-to-customize-sorting-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Sıralamayı Özelleştirme
<xref:System.Windows.Forms.DataGridView> denetimi otomatik sıralama sağlar, ancak gereksinimlerinize bağlı olarak sıralama işlemlerini özelleştirmeniz gerekebilir. Örneğin, alternatif bir kullanıcı arabirimi (UI) oluşturmak için programlı sıralama kullanabilirsiniz. Alternatif olarak, <xref:System.Windows.Forms.DataGridView.SortCompare> olayını işleyebilir veya birden çok sütunu sıralama gibi daha fazla sıralama esnekliği için <xref:System.Windows.Forms.DataGridView.Sort%2A> yönteminin `Sort(IComparer)` aşırı yüklemesini çağırabilirsiniz.  
  
 Aşağıdaki kod örneklerinde özel sıralamaya yönelik bu üç yaklaşım gösterilmektedir. Daha fazla bilgi için, [Windows Forms DataGridView Denetimindeki sütun sıralama modları](column-sort-modes-in-the-windows-forms-datagridview-control.md)bölümüne bakın.  
  
## <a name="programmatic-sorting"></a>Programlı sıralama  
 Aşağıdaki kod örneği, sıralamayı ve sıralama karakterini el ile ayarlamak için <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> özelliğini kullanarak <xref:System.Windows.Forms.DataGridView.SortOrder%2A> ve <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> özellikleri kullanılarak programlı bir sıralama gösterir. <xref:System.Windows.Forms.DataGridView.Sort%2A> yönteminin `Sort(DataGridViewColumn,ListSortDirection)` aşırı yüklemesi, verileri yalnızca tek bir sütunda sıralamak için kullanılır.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewProgrammaticSort#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewProgrammaticSort#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-sortcompare-event"></a>SortCompare olayını kullanarak özel sıralama  
 Aşağıdaki kod örneği, bir <xref:System.Windows.Forms.DataGridView.SortCompare> olay işleyicisi kullanarak özel sıralamayı gösterir. Seçilen <xref:System.Windows.Forms.DataGridViewColumn> sıralanır ve sütunda yinelenen değerler varsa, son sırayı belirlemede KIMLIK sütunu kullanılır.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.SortCompare#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.SortCompare#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-icomparer-interface"></a>IComparer arabirimini kullanarak özel sıralama  
 Aşağıdaki kod örneği, birden çok sütunlu sıralama gerçekleştirmek için <xref:System.Collections.IComparer> arabiriminin bir uygulamasını Alan <xref:System.Windows.Forms.DataGridView.Sort%2A> yönteminin `Sort(IComparer)` aşırı yüklemesini kullanarak özel sıralamayı gösterir.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewIComparerSort#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewIComparerSort#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/VB/form1.vb#00)]  
  
## <a name="compiling-the-code"></a>Kod Derleme  
 Bu örneklerde şunlar gerekir:  
  
- System, System. Drawing ve System. Windows. Forms derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- [Windows Forms DataGridView Denetimindeki Verileri Sıralama](sorting-data-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Sütun Sıralama Modları](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunlar için Sıralama Modlarını Ayarlama](set-the-sort-modes-for-columns-wf-datagridview-control.md)
