---
title: 'Nasıl Yapılır: Uygulama Başlarken veya Kapanırken İletileri Günlüğe Kaydetme (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, shutdown
- My.Application.Log object, logging
- Startup event [Visual Basic]
- event logs, startup
- Shutdown event [Visual Basic]
- My.Log object, logging
ms.assetid: 67624d05-cddf-48b7-8c36-5c99baa4c621
ms.openlocfilehash: 80b07e67cb307d461e63df9f94c9d0962eb6374a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-log-messages-when-the-application-starts-or-shuts-down-visual-basic"></a>Nasıl Yapılır: Uygulama Başlarken veya Kapanırken İletileri Günlüğe Kaydetme (Visual Basic)
Kullanabileceğiniz `My.Application.Log` ve `My.Log` uygulamanızda oluşan olaylarla ilgili bilgileri günlüğe kaydetmek için nesneleri. Bu örnek nasıl kullanılacağını gösterir `My.Application.Log.WriteEntry` yöntemiyle `Startup` ve `Shutdown` olayları izleme bilgilerini yazar.  
  
### <a name="to-access-the-applications-event-handler-code"></a>Uygulamanın olay işleyici kodu erişmek için  
  
1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünde seçin **özellikleri**.  
  
2.  Tıklatın **uygulama** sekmesi.  
  
3.  Tıklatın **uygulama olaylarını görüntüle** düğmesi kod düzenleyicisini açın.  
  
     Bu ApplicationEvents.vb dosyasını açar.  
  
### <a name="to-log-messages-when-the-application-starts"></a>Uygulama başladığında iletilerini günlüğe kaydetmek için  
  
1.  Kod düzenleyicisinde açın ApplicationEvents.vb dosyası vardır. Üzerinde **genel** menüsünde seçin **MyApplication olayları**.  
  
2.  Üzerinde **bildirimleri** menüsünde seçin **başlangıç**.  
  
     Uygulama başlatır <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> ana uygulama çalıştırılmadan önce olay.  
  
3.  Ekleme `My.Application.Log.WriteEntry` yönteme `Startup` olay işleyicisi.  
  
     [!code-vb[VbVbalrMyApplicationLog#1](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_1.vb)]  
  
### <a name="to-log-messages-when-the-application-shuts-down"></a>Uygulama kapatıldığında iletilerini günlüğe kaydetmek için  
  
1.  Kod düzenleyicisinde açın ApplicationEvents.vb dosyası vardır. Üzerinde **genel** menüsünde seçin **MyApplication olayları**.  
  
2.  Üzerinde **bildirimleri** menüsünde seçin **kapatma**.  
  
     Uygulama başlatır <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> olay ana uygulama çalıştırıldıktan sonra ancak bunu kapatılmadan önce.  
  
3.  Ekleme `My.Application.Log.WriteEntry` yönteme `Shutdown` olay işleyicisi.  
  
     [!code-vb[VbVbalrMyApplicationLog#2](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_2.vb)]  
  
## <a name="example"></a>Örnek  
 Kullanabileceğiniz **Proje Tasarımcısı** Kod Düzenleyicisi'nde uygulama olayları erişmek için. Daha fazla bilgi için bkz: [uygulama sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
 [!code-vb[VbVbalrMyApplicationLog#3](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_3.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>  
 [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)  
 [Uygulama Günlükleriyle Çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
