---
title: 'Nasıl Yapılır: Uygulama Başlarken veya Kapanırken İletileri Günlüğe Kaydetme'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, shutdown
- My.Application.Log object, logging
- Startup event [Visual Basic]
- event logs, startup
- Shutdown event [Visual Basic]
- My.Log object, logging
ms.assetid: 67624d05-cddf-48b7-8c36-5c99baa4c621
ms.openlocfilehash: 5a4ef3888ba8371d26204c3569b5fb9bae1f15f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74352093"
---
# <a name="how-to-log-messages-when-the-application-starts-or-shuts-down-visual-basic"></a>Nasıl Yapılır: Uygulama Başlarken veya Kapanırken İletileri Günlüğe Kaydetme (Visual Basic)

Uygulamanızda meydana `My.Application.Log` `My.Log` gelen olaylarla ilgili bilgileri günlüğe kaydetmek için nesneleri kullanabilirsiniz. Bu örnek, izleme `My.Application.Log.WriteEntry` bilgileri yazmak `Startup` `Shutdown` için yöntemin ve olayların nasıl kullanılacağını gösterir.  
  
### <a name="to-access-the-applications-event-handler-code"></a>Uygulamanın olay işleyici koduna erişmek için  
  
1. **Çözüm Gezgini'nde**bir proje seçili var. **Proje** menüsünde **Özellikler'i**seçin.  
  
2. **Uygulama** sekmesini tıklatın.  
  
3. Kod Düzenleyicisi'ni açmak için **Uygulama Etkinliklerini Görüntüle** düğmesini tıklatın.  
  
     Bu, ApplicationEvents.vb dosyasını açar.  
  
### <a name="to-log-messages-when-the-application-starts"></a>Uygulama başladığında iletileri günlüğe kaydetmek için  
  
1. Code Editor'da ApplicationEvents.vb dosyasını açık bulundurun. **Genel** menüde **MyApplication Events'i**seçin.  
  
2. **Bildirimler** menüsünde **Başlangıç'ı**seçin.  
  
     Uygulama, ana <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> uygulama çalışmadan önce olayı yükseltir.  
  
3. Yöntem `My.Application.Log.WriteEntry` olay işleyicisine `Startup` ekleyin.  
  
     [!code-vb[VbVbalrMyApplicationLog#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#1)]  
  
### <a name="to-log-messages-when-the-application-shuts-down"></a>Uygulama kapandığında iletileri günlüğe kaydetmek için  
  
1. Code Editor'da ApplicationEvents.vb dosyasını açık bulundurun. **Genel** menüde **MyApplication Events'i**seçin.  
  
2. **Bildirimler** menüsünde **Kapatma'yı**seçin.  
  
     Uygulama, ana <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> uygulama çalıştırdıktan sonra, ancak kapanmadan önce olayı yükseltir.  
  
3. Yöntem `My.Application.Log.WriteEntry` olay işleyicisine `Shutdown` ekleyin.  
  
     [!code-vb[VbVbalrMyApplicationLog#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#2)]  
  
## <a name="example"></a>Örnek  

 Kod Düzenleyicisi'ndeki uygulama olaylarına erişmek için **Proje Tasarımcısı'nı** kullanabilirsiniz. Daha fazla bilgi için [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)sayfasına bakın.  
  
 [!code-vb[VbVbalrMyApplicationLog#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Uygulama Günlükleriyle Çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
