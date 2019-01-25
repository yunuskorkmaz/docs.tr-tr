---
title: Bir Windows Forms Uygulamasında Kullanıcı Girdisi
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, user input
ms.assetid: 9d61fa96-70f7-4754-885a-49a4a6316bdb
ms.openlocfilehash: a47a35cffb99648737245031a558db884024c011
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54684086"
---
# <a name="user-input-in-a-windows-forms-application"></a>Bir Windows Forms Uygulamasında Kullanıcı Girdisi
Windows Forms'ta kullanıcı girdisi uygulamaları Windows iletilerini biçiminde gönderilir. Geçersiz kılınabilir yöntemleri bir dizi, form, uygulama bu iletileri işlemek ve düzeyini denetleyebilirsiniz. Bu yöntemler, fare ve klavye mesajlarının aldığınızda, bunlar giriş klavye veya fare hakkında bilgi almak için işlenen olaylar da oluşturur. Çoğu durumda, Windows Forms uygulamaları bu olayları işleyerek tüm kullanıcı girişini işlemek mümkün olacaktır. Diğer durumlarda, bir uygulama belirli bir iletiyi uygulama, form veya denetim alınmadan önce ıntercept iletileri işleyen yöntemi geçersiz kılmanız gerekebilir.  
  
## <a name="mouse-and-keyboard-events"></a>Fare ve klavye olayları  
 Tüm Windows Forms denetimleri fare ve klavye ile ilgili olayları kümesini devralırlar. Örneğin, bir denetim işleyebilir <xref:System.Windows.Forms.Control.KeyPress> karakter kodunu basıldığını bir anahtar belirlemek için olay veya denetimin işleyebilir <xref:System.Windows.Forms.Control.MouseClick> konumu fare tıklatın belirlemek için olay. Fare ve klavye olayları hakkında daha fazla bilgi için bkz. [kullanan klavye olayları](../../../docs/framework/winforms/using-keyboard-events.md) ve [Windows Forms'ta fare olayları](../../../docs/framework/winforms/mouse-events-in-windows-forms.md).  
  
## <a name="methods-that-process-user-input-messages"></a>Kullanıcı giriş iletileri işleyen yöntemleri  
 Formlar ve denetimler için erişim sahibi <xref:System.Windows.Forms.IMessageFilter> arabirimi ve bir dizi ileti kuyruğu farklı noktalarda Windows iletileri işleyen geçersiz kılınabilir yöntemleri. Tüm bu yöntemler bir <xref:System.Windows.Forms.Message> Windows iletilerini alt düzey ayrıntıları parametresi. Uygulama veya iletisini inceleyin ve ardından iletiyi kullanmak veya sonraki tüketici ileti sırasına açın geçirmek için bu yöntemleri geçersiz kılın. Windows Forms'ta tüm Windows iletileri işleyen yöntemler aşağıdaki tabloda sunulmaktadır.  
  
|Yöntem|Notlar|  
|------------|-----------|  
|<xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A>|Bu yöntem, uygulama düzeyinde sıraya alınan (gönderilen olarak da bilinir) Windows iletileri kesintiye uğratır.|  
|<xref:System.Windows.Forms.Control.PreProcessMessage%2A>|Bu yöntem, işlenen önce Windows iletileri form ve denetimi düzeyinde kesintiye uğratır.|  
|<xref:System.Windows.Forms.Control.WndProc%2A>|Bu yöntem, form ve denetim düzeyinde Windows iletilerini işler.|  
|<xref:System.Windows.Forms.Control.DefWndProc%2A>|Bu yöntem Windows iletileri form ve denetimi düzeyinde varsayılan işlemeyi gerçekleştirir. Bu pencerenin en az işlevlerini sağlar.|  
|<xref:System.Windows.Forms.Control.OnNotifyMessage%2A>|Bu yöntem, bunlar işlendikten sonra iletileri form ve denetim düzeyinde kesintiye uğratır. <xref:System.Windows.Forms.ControlStyles.EnableNotifyMessage> Stil bit, bu yöntemin çağrılması için ayarlanmış olması gerekir.|  
  
 Klavye ve fare iletileri de bu iletileri türlerine özgü geçersiz kılınabilir yöntemleri ek kümesi tarafından işlenir. Daha fazla bilgi için [nasıl klavye girişi çalışır](../../../docs/framework/winforms/how-keyboard-input-works.md) ve [nasıl Windows Forms'ta fare girdisi çalışır](../../../docs/framework/winforms/how-mouse-input-works-in-windows-forms.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Windows Forms'ta Kullanıcı Girdisi](../../../docs/framework/winforms/user-input-in-windows-forms.md)
- [Bir Windows Forms Uygulamasında Klavye Girdisi](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)
- [Bir Windows Forms Uygulamasında Fare Girdisi](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
