---
title: "CheckBox Denetimine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CheckBox
helpviewer_keywords:
- CheckBox control [Windows Forms], about CheckBox control
- data binding [Windows Forms], checkbox controls
- check boxes [Windows Forms], about check boxes
ms.assetid: 085a4e0b-9046-473f-b141-d0edddfb2ebb
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a154a3f639102e3f3e2acd62626379e12bbd1344
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="checkbox-control-overview-windows-forms"></a>CheckBox Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.CheckBox> denetimi, belirli bir koşula açık veya kapalı olduğunu gösterir. Evet sunmak için yaygın olarak kullanılan/yok veya kullanıcının True/False seçimi. Kullanıcı bir veya daha fazla seçebileceği birden çok seçenek göstermek için gruplarında onay kutusu denetimleri kullanabilirsiniz.  
  
 Her kullanıcı tarafından yapılan bir seçim göstermek için kullanılan onay kutusu denetimi için radyo düğmesi denetimini benzer. Bunlar, aynı anda yalnızca bir radyo düğmesi grubundaki seçilebilir farklılık gösterir. Onay kutusu denetimi ile ancak herhangi bir sayıda onay kutularını seçilmiş olabilir.  
  
 Bir onay kutusu, basit veri bağlama kullanarak bir veritabanındaki öğelere bağlı olabilir. Birden çok onay kutularını kullanarak gruplandırılabilir <xref:System.Windows.Forms.GroupBox> denetim. Gruplandırılmış denetimleri form Tasarımcısı üzerinde birlikte taşınabildiğinden beri bu görsel görünümünü ve ayrıca kullanıcı arabirimi tasarımı için kullanışlıdır. Daha fazla bilgi için bkz: [Windows Forms veri bağlama](../../../../docs/framework/winforms/windows-forms-data-binding.md) ve [GroupBox denetimi](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md).  
  
 <xref:System.Windows.Forms.CheckBox> Denetimi sahip iki önemli özellikleri <xref:System.Windows.Forms.CheckBox.Checked%2A> ve <xref:System.Windows.Forms.CheckBox.CheckState%2A>. <xref:System.Windows.Forms.CheckBox.Checked%2A> Özelliği döndürür ya da `true` veya `false`. <xref:System.Windows.Forms.CheckBox.CheckState%2A> Özelliği döndürür ya da <xref:System.Windows.Forms.CheckState.Checked> veya <xref:System.Windows.Forms.CheckState.Unchecked>; veya <xref:System.Windows.Forms.CheckBox.ThreeState%2A> özelliği ayarlanmış `true`, <xref:System.Windows.Forms.CheckBox.CheckState%2A> de döndürebilir <xref:System.Windows.Forms.CheckState.Indeterminate>. Belirsiz durumda kutusu seçeneği kullanılamaz belirtmek için devre dışı bir görünümü görüntülenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.CheckBox>  
 [Nasıl yapılır: seçenekleri ile Windows Forms CheckBox denetimlerini ayarlama](../../../../docs/framework/winforms/controls/how-to-set-options-with-windows-forms-checkbox-controls.md)  
 [Nasıl yapılır: Windows Forms CheckBox tıklamalarına yanıt verme](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-checkbox-clicks.md)  
 [CheckBox denetimi](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)
