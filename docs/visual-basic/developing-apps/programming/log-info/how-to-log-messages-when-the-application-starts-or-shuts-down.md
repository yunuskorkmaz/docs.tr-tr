---
title: 'Nasıl yapılır: Uygulama başladığında günlük iletileri ya da kapatıldığında çalıştırılmalıdır (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, shutdown
- My.Application.Log object, logging
- Startup event [Visual Basic]
- event logs, startup
- Shutdown event [Visual Basic]
- My.Log object, logging
ms.assetid: 67624d05-cddf-48b7-8c36-5c99baa4c621
ms.openlocfilehash: 8fc7b441c6e19d70ceefa3422cf9823007280b64
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052501"
---
# <a name="how-to-log-messages-when-the-application-starts-or-shuts-down-visual-basic"></a>Nasıl yapılır: Uygulama başladığında günlük iletileri ya da kapatıldığında çalıştırılmalıdır (Visual Basic)
Kullanabileceğiniz `My.Application.Log` ve `My.Log` gerçekleşen olaylar hakkında bilgileri, uygulamanızda oturum nesneleri. Bu örnek nasıl kullanılacağını gösterir `My.Application.Log.WriteEntry` yöntemiyle `Startup` ve `Shutdown` olayları izleme bilgileri yazın.  
  
### <a name="to-access-the-applications-event-handler-code"></a>Uygulama olay işleyici kodunun erişmek için  
  
1. Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünde seçin **özellikleri**.  
  
2. Tıklayın **uygulama** sekmesi.  
  
3. Tıklayın **uygulama olaylarını görüntüle** düğmesine Kod Düzenleyicisi'ni açın.  
  
     Bu ApplicationEvents.vb dosyasını açar.  
  
### <a name="to-log-messages-when-the-application-starts"></a>Uygulama başladığında iletilerini günlüğe kaydetmek için  
  
1. Kod Düzenleyicisi'nde açın ApplicationEvents.vb dosyasına sahiptir. Üzerinde **genel** menüsünde seçin **MyApplication olayları**.  
  
2. Üzerinde **bildirimleri** menüsünde seçin **başlangıç**.  
  
     Uygulama başlatır <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> ana uygulama çalışmadan önce olay.  
  
3. Ekleme `My.Application.Log.WriteEntry` yönteme `Startup` olay işleyicisi.  
  
     [!code-vb[VbVbalrMyApplicationLog#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#1)]  
  
### <a name="to-log-messages-when-the-application-shuts-down"></a>Uygulama kapatıldığında iletilerini günlüğe kaydetmek için  
  
1. Kod Düzenleyicisi'nde açın ApplicationEvents.vb dosyasına sahiptir. Üzerinde **genel** menüsünde seçin **MyApplication olayları**.  
  
2. Üzerinde **bildirimleri** menüsünde seçin **kapatma**.  
  
     Uygulama başlatır <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> olay ana uygulama çalıştırıldıktan sonra ancak önce nasıl kapanıyorsa öyle kapanır.  
  
3. Ekleme `My.Application.Log.WriteEntry` yönteme `Shutdown` olay işleyicisi.  
  
     [!code-vb[VbVbalrMyApplicationLog#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#2)]  
  
## <a name="example"></a>Örnek  
 Kullanabileceğiniz **Proje Tasarımcısı** Kod Düzenleyicisi'nde uygulama olaylarını erişmek için. Daha fazla bilgi için [uygulama sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
 [!code-vb[VbVbalrMyApplicationLog#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Uygulama Günlükleriyle Çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
