---
title: "Nasıl yapılır: Tasarımcı Kullanarak Kabul Düğmesi olarak bir Windows Formları Düğmesi Atama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: a1da0590-755f-49f2-aca7-609fac6351bf
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 044fa4ab2e9a37038e9db9a2784fad4190713806
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Kabul Düğmesi olarak bir Windows Formları Düğmesi Atama
Herhangi bir Windows formunda tanımladığınız bir <xref:System.Windows.Forms.Button> kabul et düğmesi olarak da bilinen varsayılan düğme olarak denetim. Her kullanıcı ENTER tuşuna bastığında, bağımsız olarak form üzerindeki diğer denetim odağı olan varsayılan düğme tıklatıldığında. Başka bir düğme denetimi odağa sahip olduğunda bu öğeler için özel durumlar — odaklanılan düğmesine tıklandığında bu durumda, — veya çok satırlı metin kutusu veya ENTER tuşuna yakalar özel bir denetim.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-designate-the-accept-button"></a>Kabul Et düğmesi atamak için  
  
1.  Düğme bulunduğu formu seçin.  
  
2.  İçinde **özellikleri** penceresinde, formun ayarlamak <xref:System.Windows.Forms.Form.AcceptButton%2A> özelliğine <xref:System.Windows.Forms.Button> denetimin adı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Form.AcceptButton%2A>  
 [Düğme denetimine genel bakış](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [Windows Forms düğme denetimi seçmenin yolları](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [Nasıl yapılır: Windows Forms düğme tıklamalarına yanıt verme](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [Nasıl yapılır: Tasarımcı kullanarak iptal düğmesi olarak bir Windows Formları düğmesi atama](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-cancel-button-using-the-designer.md)  
 [Düğme denetimi](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
