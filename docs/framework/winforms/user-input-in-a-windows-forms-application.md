---
title: Windows Forms uygulamasında kullanıcı girişi
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, user input
ms.assetid: 9d61fa96-70f7-4754-885a-49a4a6316bdb
ms.openlocfilehash: 8e82276f14519c4ef54948744c93014232bdff52
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734814"
---
# <a name="user-input-in-a-windows-forms-application"></a>Bir Windows Forms Uygulamasında Kullanıcı Girdisi
Windows Forms, Kullanıcı girişi Windows iletileri biçimindeki uygulamalara gönderilir. Geçersiz kılınabilir Yöntemler dizisi, bu iletileri uygulama, form ve Denetim düzeyinde işler. Bu yöntemler fare ve klavye iletileri alırken, fare veya klavye girişi hakkında bilgi almak için işlenebilen olayları yükseltir. Çoğu durumda, Windows Forms uygulamalar bu olayları işleyerek yalnızca tüm kullanıcı girişlerini işleyebilir. Diğer durumlarda, bir uygulamanın, uygulama, form veya denetim tarafından alınmadan önce belirli bir iletiyi ele almak için iletileri işleyen yöntemlerden birini geçersiz kılması gerekebilir.  
  
## <a name="mouse-and-keyboard-events"></a>Fare ve klavye olayları  
 Tüm Windows Forms denetimleri, fare ve klavye girişiyle ilgili bir olay kümesini miras alır. Örneğin, bir denetim, basılan bir anahtarın karakter kodunu belirleyebilmek için <xref:System.Windows.Forms.Control.KeyPress> olayını işleyebilir veya bir denetim, fare tıklaması konumunu belirleyebilmek için <xref:System.Windows.Forms.Control.MouseClick> olayını işleyebilir. Fare ve klavye olayları hakkında daha fazla bilgi için, bkz. Windows Forms [klavye olaylarını](using-keyboard-events.md) ve [fare olaylarını](mouse-events-in-windows-forms.md)kullanma.  
  
## <a name="methods-that-process-user-input-messages"></a>Kullanıcı girişi Iletilerini Işleyen Yöntemler  
 Form ve denetimlerin <xref:System.Windows.Forms.IMessageFilter> arabirimine erişimi vardır ve ileti sırasındaki farklı noktalarda Windows iletilerini işleyen geçersiz kılınabilir yöntemler kümesi. Bu yöntemlerin hepsi, Windows iletilerinin alt düzey ayrıntılarını kapsülleyen bir <xref:System.Windows.Forms.Message> parametresine sahiptir. İletiyi incelemek için bu yöntemleri uygulayabilir veya geçersiz kılabilir, sonra iletiyi kullanabilir veya ileti sırasındaki bir sonraki tüketiciye geçirebilirsiniz. Aşağıdaki tabloda Windows Forms içindeki tüm Windows iletilerini işleyen yöntemler sunulmaktadır.  
  
|Yöntem|Notlar|  
|------------|-----------|  
|<xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A>|Bu yöntem, uygulama düzeyinde sıraya alınan (Ayrıca, gönderilen) Windows iletilerini karşılar.|  
|<xref:System.Windows.Forms.Control.PreProcessMessage%2A>|Bu yöntem, Windows iletilerini işlenmeden önce form ve Denetim düzeyinde keser.|  
|<xref:System.Windows.Forms.Control.WndProc%2A>|Bu yöntem, form ve Denetim düzeyinde Windows iletilerini işler.|  
|<xref:System.Windows.Forms.Control.DefWndProc%2A>|Bu yöntem, Windows iletilerinin varsayılan işlemesini form ve Denetim düzeyinde gerçekleştirir. Bu, bir pencerenin en düşük işlevlerini sağlar.|  
|<xref:System.Windows.Forms.Control.OnNotifyMessage%2A>|Bu yöntem, iletileri işlendikten sonra form ve Denetim düzeyinde keser. Bu yöntemin çağrılması için <xref:System.Windows.Forms.ControlStyles.EnableNotifyMessage> stil biti ayarlanmalıdır.|  
  
 Klavye ve fare iletileri Ayrıca, bu tür iletilere özgü ek bir geçersiz kılınabilir yöntemler kümesi tarafından işlenir. Daha fazla bilgi için bkz. [klavye girişinin nasıl çalıştığı](how-keyboard-input-works.md) ve [fare girişinin Windows Forms nasıl çalıştığı](how-mouse-input-works-in-windows-forms.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms'ta Kullanıcı Girdisi](user-input-in-windows-forms.md)
- [Bir Windows Forms Uygulamasında Klavye Girdisi](keyboard-input-in-a-windows-forms-application.md)
- [Bir Windows Forms Uygulamasında Fare Girdisi](mouse-input-in-a-windows-forms-application.md)
