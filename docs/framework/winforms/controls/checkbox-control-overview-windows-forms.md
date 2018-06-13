---
title: CheckBox Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- CheckBox
helpviewer_keywords:
- CheckBox control [Windows Forms], about CheckBox control
- data binding [Windows Forms], checkbox controls
- check boxes [Windows Forms], about check boxes
ms.assetid: 085a4e0b-9046-473f-b141-d0edddfb2ebb
ms.openlocfilehash: 54a0bba3923626398fb4d1b0af753177dfaa09a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524150"
---
# <a name="checkbox-control-overview-windows-forms"></a>CheckBox Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.CheckBox> denetimi, belirli bir koşula açık veya kapalı olduğunu gösterir. Evet sunmak için yaygın olarak kullanılan/yok veya kullanıcının True/False seçimi. Kullanıcı bir veya daha fazla seçebileceği birden çok seçenek göstermek için gruplarında onay kutusu denetimleri kullanabilirsiniz.  
  
 Her kullanıcı tarafından yapılan bir seçim göstermek için kullanılan onay kutusu denetimi için radyo düğmesi denetimini benzer. Bunlar, aynı anda yalnızca bir radyo düğmesi grubundaki seçilebilir farklılık gösterir. Onay kutusu denetimi ile ancak herhangi bir sayıda onay kutularını seçilmiş olabilir.  
  
 Bir onay kutusu, basit veri bağlama kullanarak bir veritabanındaki öğelere bağlı olabilir. Birden çok onay kutularını kullanarak gruplandırılabilir <xref:System.Windows.Forms.GroupBox> denetim. Gruplandırılmış denetimleri form Tasarımcısı üzerinde birlikte taşınabildiğinden beri bu görsel görünümünü ve ayrıca kullanıcı arabirimi tasarımı için kullanışlıdır. Daha fazla bilgi için bkz: [Windows Forms veri bağlama](../../../../docs/framework/winforms/windows-forms-data-binding.md) ve [GroupBox denetimi](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md).  
  
 <xref:System.Windows.Forms.CheckBox> Denetimi sahip iki önemli özellikleri <xref:System.Windows.Forms.CheckBox.Checked%2A> ve <xref:System.Windows.Forms.CheckBox.CheckState%2A>. <xref:System.Windows.Forms.CheckBox.Checked%2A> Özelliği döndürür ya da `true` veya `false`. <xref:System.Windows.Forms.CheckBox.CheckState%2A> Özelliği döndürür ya da <xref:System.Windows.Forms.CheckState.Checked> veya <xref:System.Windows.Forms.CheckState.Unchecked>; veya <xref:System.Windows.Forms.CheckBox.ThreeState%2A> özelliği ayarlanmış `true`, <xref:System.Windows.Forms.CheckBox.CheckState%2A> de döndürebilir <xref:System.Windows.Forms.CheckState.Indeterminate>. Belirsiz durumda kutusu seçeneği kullanılamaz belirtmek için devre dışı bir görünümü görüntülenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.CheckBox>  
 [Nasıl yapılır: Windows Forms CheckBox Denetimleriyle Seçenekleri Ayarlama](../../../../docs/framework/winforms/controls/how-to-set-options-with-windows-forms-checkbox-controls.md)  
 [Nasıl yapılır: Windows Forms CheckBox Tıklamalarına Yanıt Verme](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-checkbox-clicks.md)  
 [CheckBox Denetimi](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)
