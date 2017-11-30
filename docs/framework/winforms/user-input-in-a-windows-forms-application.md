---
title: "Bir Windows Forms Uygulamasında Kullanıcı Girdisi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Windows Forms, user input
ms.assetid: 9d61fa96-70f7-4754-885a-49a4a6316bdb
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fb6f832b77404b57ab22e4ac472e7707f0e10dd5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="user-input-in-a-windows-forms-application"></a>Bir Windows Forms Uygulamasında Kullanıcı Girdisi
Windows Forms'ta kullanıcı girdisi uygulamalar Windows iletileri biçiminde gönderilir. Geçersiz kılınabilir yöntemleri bir dizi uygulama, form, bu iletileri işlemek ve düzeyini denetleyebilirsiniz. Bu yöntemler, fare ve klavye iletileri aldığınızda, bunlar fare hakkında bilgi almak veya giriş klavye için işlenen olayların yükseltin. Çoğu durumda, Windows Forms uygulamaları bu olayları işleyerek tüm kullanıcı girişini işlemek mümkün olacaktır. Diğer durumlarda, bir uygulama uygulama, form veya denetim tarafından almadan önce belirli bir ileti müdahale için iletileri işlemek yöntemlerden birini geçersiz kılmanız gerekebilir.  
  
## <a name="mouse-and-keyboard-events"></a>Fare ve klavye olayları  
 Tüm Windows Forms denetimleri, fare ve klavye girdisi ilgili olayların kümesini devralırlar. Örneğin, bir denetim işleyebilir <xref:System.Windows.Forms.Control.KeyPress> basıldı bir anahtar karakter kodunu belirlemek için olay ya da denetiminin işleyebilir <xref:System.Windows.Forms.Control.MouseClick> fare konumunu tıklatın belirlemek için olay. Fare ve klavye olayları hakkında daha fazla bilgi için bkz: [kullanan klavye olayları](../../../docs/framework/winforms/using-keyboard-events.md) ve [Windows Forms'ta fare olayları](../../../docs/framework/winforms/mouse-events-in-windows-forms.md).  
  
## <a name="methods-that-process-user-input-messages"></a>Kullanıcı giriş iletileri işleme yöntemleri  
 Formlar ve denetimler erişiminiz <xref:System.Windows.Forms.IMessageFilter> arabirimi ve bir dizi ileti sırası farklı noktalarda Windows iletilerini işleme geçersiz kılınabilir yöntemleri. Tüm bu yöntemleri bir <xref:System.Windows.Forms.Message> Windows iletilerini düşük düzey ayrıntılarını yalıtan parametresi. Uygulama veya iletisini inceleyin ve sonra ileti kullanmak ya da ileti sırasındaki sonraki tüketici açın geçirmek için bu yöntemleri geçersiz kılın. Aşağıdaki tabloda Windows Forms'ta tüm Windows iletilerini işleme yöntemlerini gösterir.  
  
|Yöntem|Notlar|  
|------------|-----------|  
|<xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A>|Bu yöntem, uygulama düzeyinde sıraya alınan (gönderilen olarak da bilinir) Windows iletileri kesintiye uğratır.|  
|<xref:System.Windows.Forms.Control.PreProcessMessage%2A>|İşlenmiş durumda önce bu yöntem Windows iletilerini form ve denetim düzeyinde kesintiye uğratır.|  
|<xref:System.Windows.Forms.Control.WndProc%2A>|Bu yöntem Windows iletilerini form ve denetim düzeyinde işler.|  
|<xref:System.Windows.Forms.Control.DefWndProc%2A>|Bu yöntem Windows iletileri form ve denetim düzeyinde varsayılan işlemeyi gerçekleştirir. Bu, en az bir pencere işlevselliğini sağlar.|  
|<xref:System.Windows.Forms.Control.OnNotifyMessage%2A>|Bunlar işlendikten sonra bu yöntem form ve denetim düzeyinde iletileri kesintiye uğratır. <xref:System.Windows.Forms.ControlStyles.EnableNotifyMessage> Stili bit, bu yöntemin çağrılması için ayarlanmış olması gerekir.|  
  
 Klavye ve fare iletileri de bu iletileri türleri için özel geçersiz kılınabilir yöntemleri ek kümesi tarafından işlenir. Daha fazla bilgi için bkz: [nasıl klavye girişi çalışır](../../../docs/framework/winforms/how-keyboard-input-works.md) ve [nasıl fare giriş çalışır Windows Forms'ta](../../../docs/framework/winforms/how-mouse-input-works-in-windows-forms.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms uygulamasında kullanıcı girdisi](../../../docs/framework/winforms/user-input-in-windows-forms.md)  
 [Forms bir Windows uygulamasında klavye girdisi](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 [Forms bir Windows uygulamasında fare girdisi](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
