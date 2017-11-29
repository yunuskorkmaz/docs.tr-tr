---
title: "Nasıl yapılır: Sekme Sayfasına Denetim Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TabPage control
- tab controls [Windows Forms], tab order
- tab pages [Windows Forms], adding controls
ms.assetid: b092532e-7346-469f-b9a1-897f9bea4fb7
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3ac6e436aeeafcaa66ff0e3bec213c2316302fd6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-a-control-to-a-tab-page"></a>Nasıl yapılır: Sekme Sayfasına Denetim Ekleme
Windows Forms kullanabilirsiniz <xref:System.Windows.Forms.TabControl> diğer denetimlerini düzenli bir şekilde görüntülemek için. Aşağıdaki yordamda, ilk sekmeye düğme ekleme gösterilmiştir. Simge bir sekme sayfası etiket parçası ekleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms Tabcontrol'nin görünüşünü değiştirme](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md).  
  
### <a name="to-add-a-control-programmatically"></a>Bir denetim programlı olarak eklemek için  
  
1.  Kullanım <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> yöntemi tarafından döndürülen koleksiyonunun <xref:System.Windows.Forms.Control.Controls%2A> özelliği <xref:System.Windows.Forms.TabPage>:  
  
     [!code-cpp[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cpp/add.cpp#1)]
     [!code-csharp[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cs/add.cs#1)]
     [!code-vb[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/vb/add.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [TabControl denetimi](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)  
 [TabControl denetimine genel bakış](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [Nasıl yapılır: Windows Forms Tabcontrol'nin görünüşünü değiştirme](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)  
 [Nasıl yapılır: sekme sayfalarını devre dışı bırak](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 [Nasıl yapılır: Windows Forms TabControl ile sekme ekleme ve kaldırma](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
