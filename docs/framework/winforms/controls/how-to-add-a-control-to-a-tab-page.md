---
title: 'Nasıl yapılır: Sekme sayfasına denetim ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TabPage control
- tab controls [Windows Forms], tab order
- tab pages [Windows Forms], adding controls
ms.assetid: b092532e-7346-469f-b9a1-897f9bea4fb7
ms.openlocfilehash: 42f0be64a6ac050fe8873588263b1faf7e2491a6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710189"
---
# <a name="how-to-add-a-control-to-a-tab-page"></a>Nasıl yapılır: Sekme sayfasına denetim ekleme
Windows Forms kullanabileceğiniz <xref:System.Windows.Forms.TabControl> diğer denetimleri düzenli bir şekilde görüntülenecek. Aşağıdaki yordam, ilk sekme için bir düğme eklemek gösterilmektedir. Simge bir sekme sayfası etiket parçası ekleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms Tabcontrol'un görünüşünü değiştirme](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md).  
  
### <a name="to-add-a-control-programmatically"></a>Programlı olarak denetim ekleme  
  
1.  Kullanım <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> yöntemi tarafından döndürülen koleksiyon <xref:System.Windows.Forms.Control.Controls%2A> özelliği <xref:System.Windows.Forms.TabPage>:  
  
     [!code-cpp[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cpp/add.cpp#1)]
     [!code-csharp[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cs/add.cs#1)]
     [!code-vb[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/vb/add.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [TabControl Denetimi](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)
- [TabControl Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms Tabcontrol'un görünüşünü değiştirme](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
- [Nasıl yapılır: Sekme sayfalarını devre dışı bırak](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)
- [Nasıl yapılır: Windows Forms TabControl ile sekme ekleyip](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
