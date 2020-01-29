---
title: CheckBox Denetimine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- CheckBox
helpviewer_keywords:
- CheckBox control [Windows Forms], about CheckBox control
- data binding [Windows Forms], checkbox controls
- check boxes [Windows Forms], about check boxes
ms.assetid: 085a4e0b-9046-473f-b141-d0edddfb2ebb
ms.openlocfilehash: b42816cf1bc0ce1ab6db0a2a436b17b0d4370d59
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737098"
---
# <a name="checkbox-control-overview-windows-forms"></a>CheckBox Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.CheckBox> denetimi, belirli bir koşulun açık veya kapalı olduğunu gösterir. Genellikle kullanıcıya Evet/Hayır veya doğru/yanlış seçimini sunmak için kullanılır. Kullanıcının bir veya daha fazla seçim yapabileceği birden çok seçeneği göstermek için gruplardaki onay kutusu denetimlerini kullanabilirsiniz.  
  
 Onay kutusu denetimi, ' deki, Kullanıcı tarafından yapılan bir seçimi göstermek için kullanılan radyo düğmesi denetimine benzer. Tek seferde bir gruptaki yalnızca bir radyo düğmesinin seçilebilecekleri farklılık gösterir. Ancak onay kutusu denetimiyle, herhangi bir sayıda onay kutusu seçilebilir.  
  
 Basit veri bağlama kullanan bir veritabanındaki öğelere bir onay kutusu bağlı olabilir. Birden çok onay kutusu, <xref:System.Windows.Forms.GroupBox> denetimi kullanılarak gruplandırılabilir. Bu, gruplanmış denetimlerin form tasarımcısında birlikte taşınabilmesi için görsel görünüm ve Kullanıcı arabirimi tasarımı için yararlıdır. Daha fazla bilgi için bkz. [Windows Forms veri bağlama](../windows-forms-data-binding.md) ve [GroupBox denetimi](groupbox-control-windows-forms.md).  
  
 <xref:System.Windows.Forms.CheckBox> denetimi iki önemli özelliğe sahiptir <xref:System.Windows.Forms.CheckBox.Checked%2A> ve <xref:System.Windows.Forms.CheckBox.CheckState%2A>. <xref:System.Windows.Forms.CheckBox.Checked%2A> özelliği `true` veya `false`döndürür. <xref:System.Windows.Forms.CheckBox.CheckState%2A> özelliği <xref:System.Windows.Forms.CheckState.Checked> veya <xref:System.Windows.Forms.CheckState.Unchecked>döndürür; ya da <xref:System.Windows.Forms.CheckBox.ThreeState%2A> özelliği `true`olarak ayarlanırsa <xref:System.Windows.Forms.CheckBox.CheckState%2A> de <xref:System.Windows.Forms.CheckState.Indeterminate>döndürebilir. Belirsiz durumda, Box seçeneğinin kullanılamaz olduğunu göstermek için soluk bir görünümle birlikte görüntülenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.CheckBox>
- [Nasıl yapılır: Windows Forms CheckBox Denetimleriyle Seçenekleri Ayarlama](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [Nasıl yapılır: Windows Forms CheckBox Tıklamalarına Yanıt Verme](how-to-respond-to-windows-forms-checkbox-clicks.md)
- [CheckBox Denetimi](checkbox-control-windows-forms.md)
