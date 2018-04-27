---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetiminde Sıralamayı Özelleştirme'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], sorting
- data grids [Windows Forms], customizing sorting
ms.assetid: 92fb5c14-afab-4cf5-a97e-924fd9cb99f5
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e35e340b786e078b5b1264d3f321ff952d52b439
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-customize-sorting-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Sıralamayı Özelleştirme
<xref:System.Windows.Forms.DataGridView> Denetimi sağlar Otomatik sıralama ancak gereksinimlerinize bağlı olarak, sıralama işlemi özelleştirmeniz gerekebilir. Örneğin, bir alternatif kullanıcı arabirimi (UI) oluşturmak için programlı sıralama kullanabilirsiniz. Alternatif olarak, işleyebilir <xref:System.Windows.Forms.DataGridView.SortCompare> olay veya çağrı `Sort(IComparer)` , aşırı <xref:System.Windows.Forms.DataGridView.Sort%2A> birden çok sütun sıralama gibi sıralama esneklik için yöntem.  
  
 Aşağıdaki kod örneğinde özel sıralama için bu üç yaklaşım gösterilir. Daha fazla bilgi için bkz: [Windows Forms DataGridView denetiminde Sütun sıralama modları](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md).  
  
## <a name="programmatic-sorting"></a>Programsal sıralama  
 Aşağıdaki kod örneğinde kullanarak programlı bir sıralama gösterilmektedir <xref:System.Windows.Forms.DataGridView.SortOrder%2A> ve <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> sıralama yönünü belirlemek için özellikler ve <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> sıralama karakter el ile ayarlamak için özellik. `Sort(DataGridViewColumn,ListSortDirection)` , Aşırı <xref:System.Windows.Forms.DataGridView.Sort%2A> yöntemi yalnızca tek bir sütundaki verileri sıralamak için kullanılır.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewProgrammaticSort#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewProgrammaticSort#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-sortcompare-event"></a>Özel SortCompare olayını kullanarak sıralama  
 Aşağıdaki kod örneğinde özel kullanarak sıralama gösterilmektedir bir <xref:System.Windows.Forms.DataGridView.SortCompare> olay işleyicisi. Seçili <xref:System.Windows.Forms.DataGridViewColumn> sıralanır ve sütunda yinelenen değerler varsa, kimlik sütunu son sırayı belirlemek için kullanılır.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.SortCompare#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.SortCompare#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-icomparer-interface"></a>Özel IComparer arabirimini kullanarak sıralama  
 Aşağıdaki kod örneğinde özel kullanarak sıralama gösterilmektedir `Sort(IComparer)` , aşırı <xref:System.Windows.Forms.DataGridView.Sort%2A> uygulaması gereken yöntemi <xref:System.Collections.IComparer> birden çok sütun sıralama gerçekleştirmek için arabirim.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewIComparerSort#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewIComparerSort#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/VB/form1.vb#00)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnekler gerektirir:  
  
-   Sistem, System.Drawing ve System.Windows.Forms derlemelerine başvurular.  
  
 Visual Basic veya Visual C# için bu örnekler komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Bu örnek ayrıca oluşturmak [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] yeni bir proje kodunu yapıştırma tarafından.  Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 [Windows Forms DataGridView Denetimindeki Verileri Sıralama](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView Denetiminde Sütun Sıralama Modları](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
 [Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunlar için Sıralama Modlarını Ayarlama](../../../../docs/framework/winforms/controls/set-the-sort-modes-for-columns-wf-datagridview-control.md)
