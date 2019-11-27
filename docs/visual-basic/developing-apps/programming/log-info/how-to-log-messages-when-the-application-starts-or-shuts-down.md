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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352093"
---
# <a name="how-to-log-messages-when-the-application-starts-or-shuts-down-visual-basic"></a>Nasıl Yapılır: Uygulama Başlarken veya Kapanırken İletileri Günlüğe Kaydetme (Visual Basic)

Uygulamanızda oluşan olaylarla ilgili bilgileri günlüğe kaydetmek için `My.Application.Log` ve `My.Log` nesnelerini kullanabilirsiniz. Bu örnek, izleme bilgilerini yazmak için `Startup` ve `Shutdown` olaylarıyla `My.Application.Log.WriteEntry` yönteminin nasıl kullanılacağını gösterir.  
  
### <a name="to-access-the-applications-event-handler-code"></a>Uygulamanın olay işleyicisi koduna erişmek için  
  
1. **Çözüm Gezgini**' de bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' i seçin.  
  
2. **Uygulama** sekmesine tıklayın.  
  
3. Kod düzenleyicisini açmak için **uygulama olaylarını görüntüle** düğmesine tıklayın.  
  
     Bu, ApplicationEvents. vb dosyasını açar.  
  
### <a name="to-log-messages-when-the-application-starts"></a>Uygulama başladığında iletileri günlüğe kaydetmek için  
  
1. ApplicationEvents. vb dosyasını kod düzenleyicisinde açın. **Genel** menüsünde **MyApplication olayları**' nı seçin.  
  
2. **Bildirimler** menüsünde, **Başlangıç**' ı seçin.  
  
     Uygulama, ana uygulama çalışmadan önce <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> olayını başlatır.  
  
3. `My.Application.Log.WriteEntry` yöntemini `Startup` olay işleyicisine ekleyin.  
  
     [!code-vb[VbVbalrMyApplicationLog#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#1)]  
  
### <a name="to-log-messages-when-the-application-shuts-down"></a>Uygulama kapandığında iletileri günlüğe kaydetmek için  
  
1. ApplicationEvents. vb dosyasını kod düzenleyicisinde açın. **Genel** menüsünde **MyApplication olayları**' nı seçin.  
  
2. **Bildirimler** menüsünde, **kapatır**' ı seçin.  
  
     Uygulama, ana uygulama çalıştırıldıktan sonra, ancak kapatılmadan önce <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> olayını başlatır.  
  
3. `My.Application.Log.WriteEntry` yöntemini `Shutdown` olay işleyicisine ekleyin.  
  
     [!code-vb[VbVbalrMyApplicationLog#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#2)]  
  
## <a name="example"></a>Örnek  

 Kod düzenleyicisinde uygulama olaylarına erişmek için **Proje tasarımcısını** kullanabilirsiniz. Daha fazla bilgi için bkz. [uygulama sayfası, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
 [!code-vb[VbVbalrMyApplicationLog#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Uygulama Günlükleriyle Çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
