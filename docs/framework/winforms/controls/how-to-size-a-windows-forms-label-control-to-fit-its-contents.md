---
title: "Nasıl yapılır: Windows Forms Etiket Denetimini İçeriğini Sığdıracak Şekilde Boyutlandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- captions [Windows Forms], sizing
- sizing controls
- size [Windows Forms], controls
- labels [Windows Forms], sizing to fit contents
- Label control [Windows Forms], sizing to fit contents
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bd89d72264e5837d2c41fcb0ab024a7b16f4205b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a>Nasıl yapılır: Windows Forms Etiket Denetimini İçeriğini Sığdıracak Şekilde Boyutlandırma
Windows Forms <xref:System.Windows.Forms.Label> denetim tek satırlı veya çok satırlı olabilir ve ya da boyutu sabit ya da otomatik olarak kendisini yazısına uyum sağlayacak şekilde boyutlandırabilirsiniz. <xref:System.Windows.Forms.Label.AutoSize%2A> Özelliği resim yazısını çalışma zamanında değişecekse özellikle yararlı olduğu daha büyük veya küçük resim yazıları, sığması için denetimleri boyut yardımcı olur.  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a>Bir etiket denetimini içeriğini sığdıracak şekilde dinamik olarak yeniden boyutlandırma yapmak için  
  
1.  Ayarlama, <xref:System.Windows.Forms.Label.AutoSize%2A> özelliğine `true`.  
  
 Varsa <xref:System.Windows.Forms.Label.AutoSize%2A> ayarlanır `false`, belirtilen sözcükler <xref:System.Windows.Forms.Label.Text%2A> özelliği mümkünse sonraki satıra kaydır, ancak denetim yok büyüyecektir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Windows Forms etiket denetimleri ile erişim tuşları oluşturma](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md)  
 [Etiket denetimine genel bakış](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)  
 [Etiket denetimi](../../../../docs/framework/winforms/controls/label-control-windows-forms.md)
