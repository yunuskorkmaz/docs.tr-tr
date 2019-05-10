---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetiminde Sıralamayı Özelleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], sorting
- data grids [Windows Forms], customizing sorting
ms.assetid: 92fb5c14-afab-4cf5-a97e-924fd9cb99f5
ms.openlocfilehash: f82da44156ead690577046efa39aa3bbb60625dc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64666371"
---
# <a name="how-to-customize-sorting-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Sıralamayı Özelleştirme
<xref:System.Windows.Forms.DataGridView> Denetimi, Otomatik sıralama sağlar ancak gereksinimlerinize bağlı olarak, sıralama işlemlerinde özelleştirmeniz gerekebilir. Örneğin, bir diğer kullanıcı arabirimi (UI) oluşturmak için programlı sıralama kullanabilirsiniz. Alternatif olarak, işleyebileceği <xref:System.Windows.Forms.DataGridView.SortCompare> olay veya çağrı `Sort(IComparer)` aşırı yükünü <xref:System.Windows.Forms.DataGridView.Sort%2A> birden çok sütunu sıralama gibi sıralama esneklik için yöntemi.  
  
 Aşağıdaki kod örnekleri, özel sıralamak için üç bu yaklaşım gösterilmektedir. Daha fazla bilgi için [Windows Forms DataGridView denetiminde Sütun sıralama modları](column-sort-modes-in-the-windows-forms-datagridview-control.md).  
  
## <a name="programmatic-sorting"></a>Programlı sıralama  
 Aşağıdaki kod örneği kullanılarak programlı bir sıralama gösterir <xref:System.Windows.Forms.DataGridView.SortOrder%2A> ve <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> sıralama yönünü belirlemek için özellikleri ve <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> karakter Sırala el ile ayarlamak için özellik. `Sort(DataGridViewColumn,ListSortDirection)` Aşırı yükünü <xref:System.Windows.Forms.DataGridView.Sort%2A> yöntemi yalnızca tek bir sütunda verileri sıralamak için kullanılır.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewProgrammaticSort#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewProgrammaticSort#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-sortcompare-event"></a>Özel SortCompare olayını kullanarak sıralama  
 Aşağıdaki kod örneği kullanarak özel sıralama gösterir bir <xref:System.Windows.Forms.DataGridView.SortCompare> olay işleyicisi. Seçili <xref:System.Windows.Forms.DataGridViewColumn> sıralanır ve sütundaki yinelenen değerler varsa, kimlik sütunu son sırasını belirlemek için kullanılır.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.SortCompare#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.SortCompare#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-icomparer-interface"></a>Özel IComparer arabirimini kullanarak sıralama  
 Aşağıdaki kod örneği kullanarak özel sıralama gösterir `Sort(IComparer)` aşırı yükünü <xref:System.Windows.Forms.DataGridView.Sort%2A> uygulaması gereken yöntemini <xref:System.Collections.IComparer> birden çok sütunu sıralamayı gerçekleştirmek için arabirim.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewIComparerSort#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewIComparerSort#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/VB/form1.vb#00)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örneği gerektirir:  
  
- Sistem, System.Drawing ve System.Windows.Forms derlemelere başvuruları.  
  
 Bu örnekler komut satırından Visual Basic veya Visual C# için oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- [Windows Forms DataGridView Denetimindeki Verileri Sıralama](sorting-data-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Sütun Sıralama Modları](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView denetiminde sütunlar için sıralama modlarını ayarlama](set-the-sort-modes-for-columns-wf-datagridview-control.md)
