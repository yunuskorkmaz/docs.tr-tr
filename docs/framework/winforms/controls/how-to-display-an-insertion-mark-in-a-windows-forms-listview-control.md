---
title: ListView denetiminde ekleme Işareti görüntüle
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
ms.openlocfilehash: eeae51223a21baaf4d2412de2ce11d0c6cbcae27
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742212"
---
# <a name="how-to-display-an-insertion-mark-in-a-windows-forms-listview-control"></a>Nasıl yapılır: Windows Forms ListView Denetiminde Ekleme İşareti Görüntüleme
<xref:System.Windows.Forms.ListView> denetimindeki ekleme işareti kullanıcılara sürüklenen öğelerin ekleneceği noktayı gösterir. Bir Kullanıcı bir öğeyi diğer iki öğe arasındaki bir noktaya sürüklendiğinde, ekleme işareti öğenin beklenen yeni konumunu gösterir.  
  
 Aşağıdaki görüntüde bir ekleme işareti gösterilmektedir:  
  
 ![ListView ekleme işaretini gösteren ekran görüntüsü.](./media/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control/listview-insertion-mark.gif "ListViewInsertion")  
  
 Aşağıdaki kod örneğinde, bu özelliğin nasıl kullanılacağı gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 [!code-cpp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CPP/listviewinsertionmarkexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CS/listviewinsertionmarkexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/VB/listviewinsertionmarkexample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleme  
 Bu örnek şunları gerektirir:  
  
- System ve System. Windows. Forms derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.InsertionMark%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewInsertionMark>
- [ListView Denetimi](listview-control-windows-forms.md)
- [ListView Denetimine Genel Bakış](listview-control-overview-windows-forms.md)
- [İzlenecek yol: Windows Forms'ta Sürükle ve Bırak İşlemi Gerçekleştirme](../advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)
