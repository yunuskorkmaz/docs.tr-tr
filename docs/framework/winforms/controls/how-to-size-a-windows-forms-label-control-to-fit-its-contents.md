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
ms.workload: dotnet
ms.openlocfilehash: a2c34506ca33af80b83f365893e56a5a9d437b89
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a>Nasıl yapılır: Windows Forms Etiket Denetimini İçeriğini Sığdıracak Şekilde Boyutlandırma
Windows Forms <xref:System.Windows.Forms.Label> denetim tek satırlı veya çok satırlı olabilir ve ya da boyutu sabit ya da otomatik olarak kendisini yazısına uyum sağlayacak şekilde boyutlandırabilirsiniz. <xref:System.Windows.Forms.Label.AutoSize%2A> Özelliği resim yazısını çalışma zamanında değişecekse özellikle yararlı olduğu daha büyük veya küçük resim yazıları, sığması için denetimleri boyut yardımcı olur.  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a>Bir etiket denetimini içeriğini sığdıracak şekilde dinamik olarak yeniden boyutlandırma yapmak için  
  
1.  Ayarlama, <xref:System.Windows.Forms.Label.AutoSize%2A> özelliğine `true`.  
  
 Varsa <xref:System.Windows.Forms.Label.AutoSize%2A> ayarlanır `false`, belirtilen sözcükler <xref:System.Windows.Forms.Label.Text%2A> özelliği mümkünse sonraki satıra kaydır, ancak denetim yok büyüyecektir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Windows Forms Etiket Denetimleri ile Erişim Tuşları Oluşturma](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md)  
 [Etiket Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)  
 [Etiket Denetimi](../../../../docs/framework/winforms/controls/label-control-windows-forms.md)
