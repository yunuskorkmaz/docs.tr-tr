---
title: 'Nasıl yapılır: Windows Forms ListView Denetiminde Ekleme İşareti Görüntüleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ListView control [Windows Forms], drag operations
- graphics [Windows Forms], insertion marks
- drop and drag [Windows Forms], insertion marks
- insertion marks
ms.assetid: 88d0a15b-25fd-4dc3-a685-297351311940
ms.openlocfilehash: f5de00fd41b24fc1a7f1ff4484c3a126e98952a1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967828"
---
# <a name="how-to-display-an-insertion-mark-in-a-windows-forms-listview-control"></a>Nasıl yapılır: Windows Forms ListView Denetiminde Ekleme İşareti Görüntüleme
<xref:System.Windows.Forms.ListView> Denetimdeki ekleme işareti kullanıcılara sürüklenen öğelerin ekleneceği noktayı gösterir. Bir Kullanıcı bir öğeyi diğer iki öğe arasındaki bir noktaya sürüklendiğinde, ekleme işareti öğenin beklenen yeni konumunu gösterir.  
  
> [!NOTE]
> Ekleme işareti özelliği yalnızca [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] uygulamanız <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> yöntemi çağırdığında kullanılabilir. Önceki işletim sistemlerinde, ekleme işaretiyle ilgili tüm kodlar etkisizdir ve ekleme işareti görünmez. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.ListViewInsertionMark>.  
  
 Aşağıdaki görüntüde bir ekleme işareti gösterilmektedir:  
  
 ![ListView ekleme işaretini gösteren ekran görüntüsü.](./media/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control/listview-insertion-mark.gif "ListViewInsertion")  
  
 Aşağıdaki kod örneğinde, bu özelliğin nasıl kullanılacağı gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 [!code-cpp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CPP/listviewinsertionmarkexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CS/listviewinsertionmarkexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/VB/listviewinsertionmarkexample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- System ve System. Windows. Forms derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.InsertionMark%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewInsertionMark>
- [ListView Denetimi](listview-control-windows-forms.md)
- [ListView Denetimine Genel Bakış](listview-control-overview-windows-forms.md)
- [İzlenecek yol: Windows Forms bir sürükle ve bırak Işlemi gerçekleştirme](../advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)
