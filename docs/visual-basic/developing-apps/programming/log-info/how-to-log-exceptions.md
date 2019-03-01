---
title: "Nasıl yapılır: Visual Basic'te günlük özel durumları"
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, logging
- exceptions, tracking
ms.assetid: a26c60e2-ae39-444a-aebb-33eccadc0eeb
ms.openlocfilehash: 10d1d25f830ff563cf70369e7b9d4c66f639c121
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969797"
---
# <a name="how-to-log-exceptions-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te günlük özel durumları
Kullanabileceğiniz `My.Application.Log` ve `My.Log` oluşan özel durumları hakkında bilgi uygulamanızda oturum nesneleri. Bu örneklerin nasıl kullanabileceğinizi gösteren `My.Application.Log.WriteException` açıkça catch özel durumları ve işlenmeyen özel durumları günlüğe kaydetmek için yöntemi.  
  
 İzleme bilgilerini günlüğe kaydetme için kullanmak `My.Application.Log.WriteEntry` yöntemi. Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
  
### <a name="to-log-a-handled-exception"></a>İşlenen özel durum oturum için  
  
1.  Özel durum bilgileri oluşturan bir yöntem oluşturun.  
  
     [!code-vb[VbVbalrMyApplicationLog#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#9)]  
  
2.  Kullanım bir `Try...Catch` istisna yakalamak için blok.  
  
     [!code-vb[VbVbalrMyApplicationLog#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#6)]  
  
3.  Bir özel durum oluşturabilir kodu put `Try` blok.  
  
     Açıklamadan çıkarın `Dim` ve `MsgBox` neden satırları bir <xref:System.NullReferenceException> özel durum.  
  
     [!code-vb[VbVbalrMyApplicationLog#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#7)]  
  
4.  İçinde `Catch` engelleme, kullanın `My.Application.Log.WriteException` özel durum bilgilerini yazmak için yöntemi.  
  
     [!code-vb[VbVbalrMyApplicationLog#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#8)]  
  
     Aşağıdaki örnek, işlenen özel durum günlüğe kaydetme için tam kod gösterilir.  
  
     [!code-vb[VbVbalrMyApplicationLog#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#10)]  
  
### <a name="to-log-an-unhandled-exception"></a>İşlenmeyen bir özel durum oturum için  
  
1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünde seçin **özellikleri**.  
  
2.  Tıklayın **uygulama** sekmesi.  
  
3.  Tıklayın **uygulama olaylarını görüntüle** düğmesine Kod Düzenleyicisi'ni açın.  
  
     Bu ApplicationEvents.vb dosyasını açar.  
  
4.  Kod Düzenleyicisi'nde açın ApplicationEvents.vb dosyasına sahiptir. Üzerinde **genel** menüsünde seçin **MyApplication olayları**.  
  
5.  Üzerinde **bildirimleri** menüsünde seçin **UnhandledException**.  
  
     Uygulama başlatır <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> ana uygulama çalışmadan önce olay.  
  
6.  Ekleme `My.Application.Log.WriteException` yönteme `UnhandledException` olay işleyicisi.  
  
     [!code-vb[VbVbalrMyApplicationLog#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#4)]  
  
     Aşağıdaki örnek, işlenmeyen bir özel durum günlüğe kaydetme için tam kod gösterilir.  
  
     [!code-vb[VbVbalrMyApplicationLog#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Uygulama Günlükleriyle Çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Nasıl yapılır: Günlük iletileri yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [İzlenecek yol: My.Application.log günlüğünün bilgileri nereye yazdığını belirleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [İzlenecek yol: My.Application.Log günlüğünün bilgileri yazdığı yeri değiştirme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
