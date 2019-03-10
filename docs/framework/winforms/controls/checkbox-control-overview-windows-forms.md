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
ms.openlocfilehash: 003e57db16c35b519d3948fc24e82a94a5c3744d
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713455"
---
# <a name="checkbox-control-overview-windows-forms"></a>CheckBox Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.CheckBox> denetimi, belirli bir koşul açıp olup olmadığını gösterir. Evet sunmak için yaygın olarak kullanılan/yok veya kullanıcının True/False seçimi. Birden çok seçenek, bir veya daha fazla kullanıcının seçim yapabileceği görüntülenecek gruplarında onay kutusu denetimleri kullanabilirsiniz.  
  
 Her kullanıcı tarafından yapılan bir seçim belirtmek için kullanılır, onay kutusu denetimi için radyo düğmesi denetimini benzerdir. Bunlar, bir kerede yalnızca bir radyo düğmesi grubundaki seçilebilir farklılık gösterir. Onay kutusu denetimi ile ancak herhangi bir sayıda onay kutularının seçilmiş olabilir.  
  
 Bir onay kutusu basit veri bağlama kullanarak veritabanı öğelere bağlı olabilir. Birden çok onay kutularını kullanarak gruplandırılabilir <xref:System.Windows.Forms.GroupBox> denetimi. Gruplandırılmış denetimleri form Tasarımcısı üzerinde birlikte taşınabildiğinden olduğundan bu görsel görünümünü ve ayrıca kullanıcı arabirimi tasarımı için kullanışlıdır. Daha fazla bilgi için [Windows Forms veri bağlama](../windows-forms-data-binding.md) ve [GroupBox denetimiyle](groupbox-control-windows-forms.md).  
  
 <xref:System.Windows.Forms.CheckBox> Denetime sahip iki önemli özellikleri <xref:System.Windows.Forms.CheckBox.Checked%2A> ve <xref:System.Windows.Forms.CheckBox.CheckState%2A>. <xref:System.Windows.Forms.CheckBox.Checked%2A> Özelliği döndürür ya da `true` veya `false`. <xref:System.Windows.Forms.CheckBox.CheckState%2A> Özelliği döndürür ya da <xref:System.Windows.Forms.CheckState.Checked> veya <xref:System.Windows.Forms.CheckState.Unchecked>; veya <xref:System.Windows.Forms.CheckBox.ThreeState%2A> özelliği `true`, <xref:System.Windows.Forms.CheckBox.CheckState%2A> döndürebilir <xref:System.Windows.Forms.CheckState.Indeterminate>. Belirsiz durumda seçeneği kullanılamaz göstermek için soluk bir görünüm kutusu görüntülenir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.CheckBox>
- [Nasıl yapılır: Windows Forms CheckBox denetimleriyle seçenekleri ayarlama](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [Nasıl yapılır: Windows Forms CheckBox tıklamalarına yanıt verme](how-to-respond-to-windows-forms-checkbox-clicks.md)
- [CheckBox Denetimi](checkbox-control-windows-forms.md)
