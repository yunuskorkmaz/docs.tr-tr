---
title: 'Nasıl yapılır: ListView Denetimine Arama Yetenekleri Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- lists [Windows Forms], enabling searching
- list views [Windows Forms], enabling searching
- ListView control [Windows Forms], adding search capabilities
- searching [Windows Forms], adding search capabilities to ListView control
ms.assetid: 557782d9-b705-4bab-b496-9938afddac82
ms.openlocfilehash: d5d4dae55fc9f0613ab6535b2fe57e262d0ef141
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011040"
---
# <a name="how-to-add-search-capabilities-to-a-listview-control"></a>Nasıl yapılır: ListView Denetimine Arama Yetenekleri Ekleme
Önerilmesine öğeleri büyük listesiyle çalışırken bir <xref:System.Windows.Forms.ListView> kullanıcıya arama özellikleri sunmak istediğiniz denetimi. <xref:System.Windows.Forms.ListView> Denetim, iki farklı şekilde bu özellik sunar: eşleşen metin ve arama konumu.  
  
 <xref:System.Windows.Forms.ListView.FindItemWithText%2A> Yöntemi bir metin araması gerçekleştirmek sağlayan bir <xref:System.Windows.Forms.ListView> verilen arama dizesi ve isteğe bağlı bir başlangıç ve bitiş dizini, liste veya ayrıntı görünümü'nde. Buna karşılık, <xref:System.Windows.Forms.ListView.FindNearestItem%2A> yöntemi içindeki bir öğeyi bulmak sağlayan bir <xref:System.Windows.Forms.ListView> simgesini veya kutucuk görünümünde, bir dizi x ve y koordinatları ve aramak için bir yön verilen.  
  
### <a name="to-find-an-item-using-text"></a>Metin kullanarak bir öğeyi bulmak için  
  
1. Oluşturma bir <xref:System.Windows.Forms.ListView> ile <xref:System.Windows.Forms.ListView.View%2A> özelliğini <xref:System.Windows.Forms.View.Details> veya <xref:System.Windows.Forms.View.List>ve ardından doldurmak <xref:System.Windows.Forms.ListView> öğeleri.  
  
2. Çağrı <xref:System.Windows.Forms.ListView.FindItemWithText%2A> yöntemini bulmak için istediğiniz öğenin metni.  
  
3. Aşağıdaki kod örneği, bir temel oluşturmak gösterilmiştir <xref:System.Windows.Forms.ListView>öğeleriyle doldurun ve metin girişi kullanıcı listede bir öğeyi bulmak için kullanın.  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#1)]  
  
### <a name="to-find-an-item-using-x--and-y-coordinates"></a>X ve y koordinatları kullanarak bir öğeyi bulmak için  
  
1. Oluşturma bir <xref:System.Windows.Forms.ListView> ile <xref:System.Windows.Forms.View> özelliğini <xref:System.Windows.Forms.View.SmallIcon> veya <xref:System.Windows.Forms.View.LargeIcon>ve ardından doldurmak <xref:System.Windows.Forms.ListView> öğeleri.  
  
2. Çağrı <xref:System.Windows.Forms.ListView.FindNearestItem%2A> yöntemini, istenen x ve y- ve arama yapmak istediğiniz yönü.  
  
3. Aşağıdaki kod örneği temel bir simge oluşturulmaya gösterilmektedir <xref:System.Windows.Forms.ListView>, öğeleri ve yakalama ile doldurmak <xref:System.Windows.Forms.Control.MouseDown> yukarı yönde yakın öğeyi bulmak için olay.  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#2](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#2)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#2)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.FindItemWithText%2A>
- <xref:System.Windows.Forms.ListView.FindNearestItem%2A>
- [ListView Denetimi](listview-control-windows-forms.md)
- [ListView Denetimine Genel Bakış](listview-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms ListView denetimi ile öğe ekleyip](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
