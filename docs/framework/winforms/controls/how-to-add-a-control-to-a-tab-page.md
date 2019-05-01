---
title: 'Nasıl yapılır: Sekme Sayfasına Denetim Ekleme'
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
ms.openlocfilehash: 9806583fda60f1cb8a5ef2d97f42eba158593f61
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011235"
---
# <a name="how-to-add-a-control-to-a-tab-page"></a>Nasıl yapılır: Sekme Sayfasına Denetim Ekleme
Windows Forms kullanabileceğiniz <xref:System.Windows.Forms.TabControl> diğer denetimleri düzenli bir şekilde görüntülenecek. Aşağıdaki yordam, ilk sekme için bir düğme eklemek gösterilmektedir. Simge bir sekme sayfası etiket parçası ekleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms Tabcontrol'un görünüşünü değiştirme](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md).  
  
### <a name="to-add-a-control-programmatically"></a>Programlı olarak denetim ekleme  
  
1. Kullanım <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> yöntemi tarafından döndürülen koleksiyon <xref:System.Windows.Forms.Control.Controls%2A> özelliği <xref:System.Windows.Forms.TabPage>:  
  
     [!code-cpp[TabPageControlCollectionHowToAdd#1](~/samples/snippets/cpp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cpp/add.cpp#1)]
     [!code-csharp[TabPageControlCollectionHowToAdd#1](~/samples/snippets/csharp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cs/add.cs#1)]
     [!code-vb[TabPageControlCollectionHowToAdd#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/vb/add.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [TabControl Denetimi](tabcontrol-control-windows-forms.md)
- [TabControl Denetimine Genel Bakış](tabcontrol-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms Tabcontrol'un görünüşünü değiştirme](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
- [Nasıl yapılır: Sekme sayfalarını devre dışı bırak](how-to-disable-tab-pages.md)
- [Nasıl yapılır: Windows Forms TabControl ile sekme ekleyip](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
