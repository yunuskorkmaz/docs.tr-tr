---
title: 'Nasıl Yapılır: Günlük Özel Durumları'
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, logging
- exceptions, tracking
ms.assetid: a26c60e2-ae39-444a-aebb-33eccadc0eeb
ms.openlocfilehash: fe6949d727fae0c230ce7421b32fdaf2a498edbc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74352081"
---
# <a name="how-to-log-exceptions-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Günlük Özel Durumları

Uygulamanızda oluşan `My.Application.Log` `My.Log` özel durumlar hakkında bilgi günlüğe kaydetmek için nesneleri kullanabilirsiniz. Bu örnekler, açıkça `My.Application.Log.WriteException` yakaladığınız özel durumları ve işlenmemiş özel durumları günlüğe kaydetmek için yöntemin nasıl kullanılacağını gösterir.  
  
 İzleme bilgilerini günlüğe kaydetmek için `My.Application.Log.WriteEntry` yöntemi kullanın. Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>.  
  
### <a name="to-log-a-handled-exception"></a>İşlenen özel bir durumu günlüğe kaydetmek için  
  
1. Özel durum bilgilerini oluşturacak yöntemi oluşturun.  
  
     [!code-vb[VbVbalrMyApplicationLog#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#9)]  
  
2. Özel `Try...Catch` durumu yakalamak için bir blok kullanın.  
  
     [!code-vb[VbVbalrMyApplicationLog#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#6)]  
  
3. `Try` Blokta özel durum oluşturabilecek kodu koyun.  
  
     Özel <xref:System.NullReferenceException> durum `Dim` `MsgBox` neden olmak için açıklama ve satırları uncomment.  
  
     [!code-vb[VbVbalrMyApplicationLog#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#7)]  
  
4. Blokta, `Catch` özel `My.Application.Log.WriteException` durum bilgilerini yazmak için yöntemi kullanın.  
  
     [!code-vb[VbVbalrMyApplicationLog#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#8)]  
  
     Aşağıdaki örnek, işlenmiş bir özel durum günlüğe kaydetme için tam kodu gösterir.  
  
     [!code-vb[VbVbalrMyApplicationLog#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#10)]  
  
### <a name="to-log-an-unhandled-exception"></a>İşlenmemiş bir özel durumu günlüğe kaydetmek için  
  
1. **Çözüm Gezgini'nde**bir proje seçili var. **Proje** menüsünde **Özellikler'i**seçin.  
  
2. **Uygulama** sekmesini tıklatın.  
  
3. Kod Düzenleyicisi'ni açmak için **Uygulama Etkinliklerini Görüntüle** düğmesini tıklatın.  
  
     Bu, ApplicationEvents.vb dosyasını açar.  
  
4. Code Editor'da ApplicationEvents.vb dosyasını açık bulundurun. **Genel** menüde **MyApplication Events'i**seçin.  
  
5. **Bildirimler** **menüsünde, UnhandledException'ı**seçin.  
  
     Uygulama, ana <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> uygulama çalışmadan önce olayı yükseltir.  
  
6. Yöntem `My.Application.Log.WriteException` olay işleyicisine `UnhandledException` ekleyin.  
  
     [!code-vb[VbVbalrMyApplicationLog#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#4)]  
  
     Aşağıdaki örnek, işlenmemiş bir özel durum günlüğe kaydetmeiçin tam kodu gösterir.  
  
     [!code-vb[VbVbalrMyApplicationLog#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Uygulama Günlükleriyle Çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Nasıl Yapılır: Günlük İletileri Yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
