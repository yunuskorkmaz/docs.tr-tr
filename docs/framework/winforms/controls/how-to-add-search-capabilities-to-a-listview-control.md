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
ms.openlocfilehash: 2049638998f7a8d099e14fab9c95384a49c67833
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-search-capabilities-to-a-listview-control"></a>Nasıl yapılır: ListView Denetimine Arama Yetenekleri Ekleme
Büyük bir liste öğelerinin görmemeleri çalışırken, bir <xref:System.Windows.Forms.ListView> denetimi istediğiniz kullanıcıya arama özellikleri sunar. <xref:System.Windows.Forms.ListView> Denetim iki farklı şekilde bu özellik sunar: eşleşen metni ve arama konumu.  
  
 <xref:System.Windows.Forms.ListView.FindItemWithText%2A> Yöntemi sağlar, üzerinde bir metin araması gerçekleştirmek bir <xref:System.Windows.Forms.ListView> ayrıntıları veya liste görünümünde, verilen arama dizesi ve isteğe bağlı bir başlangıç ve bitiş dizini. Buna karşılık, <xref:System.Windows.Forms.ListView.FindNearestItem%2A> yöntemi sağlar, bir öğeyi bulmak bir <xref:System.Windows.Forms.ListView> simgesine veya bölmesi görünümünde, bir dizi x ve y koordinatları ve aramak için bir yön verilen.  
  
### <a name="to-find-an-item-using-text"></a>Metin kullanarak bir öğeyi bulmak için  
  
1.  Oluşturma bir <xref:System.Windows.Forms.ListView> ile <xref:System.Windows.Forms.ListView.View%2A> özelliğini <xref:System.Windows.Forms.View.Details> veya <xref:System.Windows.Forms.View.List>ve ardından doldurmak <xref:System.Windows.Forms.ListView> öğeleriyle.  
  
2.  Çağrı <xref:System.Windows.Forms.ListView.FindItemWithText%2A> yöntemi, bulmak istediğiniz öğenin metnini geçirme.  
  
3.  Aşağıdaki kod örneğinde nasıl temel oluşturulduğunu gösteren <xref:System.Windows.Forms.ListView>öğeler ile doldurulur ve metin girişi kullanıcı bir öğeyi listede bulmak için kullanın.  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#1)]  
  
### <a name="to-find-an-item-using-x--and-y-coordinates"></a>X ve y koordinatları kullanarak bir öğeyi bulmak için  
  
1.  Oluşturma bir <xref:System.Windows.Forms.ListView> ile <xref:System.Windows.Forms.View> özelliğini <xref:System.Windows.Forms.View.SmallIcon> veya <xref:System.Windows.Forms.View.LargeIcon>ve ardından doldurmak <xref:System.Windows.Forms.ListView> öğeleriyle.  
  
2.  Çağrı <xref:System.Windows.Forms.ListView.FindNearestItem%2A> yöntemi, istenen x ve y-koordinatları ve aramak istediğiniz yönü geçirme.  
  
3.  Aşağıdaki kod örneği, temel bir simge oluşturulmaya gösterilmiştir <xref:System.Windows.Forms.ListView>, öğeleri ve yakalama doldurmak <xref:System.Windows.Forms.Control.MouseDown> yakın öğeyi yukarı yönde bulmak için olay.  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#2)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#2)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.FindItemWithText%2A>  
 <xref:System.Windows.Forms.ListView.FindNearestItem%2A>  
 [ListView Denetimi](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [ListView Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Nasıl yapılır: Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
