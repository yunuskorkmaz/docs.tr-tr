---
title: 'Nasıl yapılır: Özel Durumları Günlüğe Kaydetme'
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

Uygulamanızda oluşan özel durumlarla `My.Application.Log` ilgili `My.Log` bilgileri günlüğe kaydetmek için ve nesnelerini kullanabilirsiniz. Bu örnekler, `My.Application.Log.WriteException` açıkça yakalayacak özel durumları ve işlenmemiş özel durumları günlüğe kaydetmek için yönteminin nasıl kullanılacağını gösterir.  
  
 İzleme bilgilerini günlüğe kaydetmek için `My.Application.Log.WriteEntry` yöntemini kullanın. Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>.  
  
### <a name="to-log-a-handled-exception"></a>İşlenmiş bir özel durumu günlüğe kaydetmek için  
  
1. Özel durum bilgilerini oluşturacak yöntemi oluşturun.  
  
     [!code-vb[VbVbalrMyApplicationLog#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#9)]  
  
2. Özel durumu `Try...Catch` yakalamak için bir blok kullanın.  
  
     [!code-vb[VbVbalrMyApplicationLog#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#6)]  
  
3. `Try` Bloğa özel durum üretebilen kodu koyun.  
  
     Özel duruma `Dim` neden `MsgBox` olacak şekilde ve satırlarının açıklamasını kaldırın. <xref:System.NullReferenceException>  
  
     [!code-vb[VbVbalrMyApplicationLog#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#7)]  
  
4. `Catch` Bloğunda, özel durum bilgilerini yazmak `My.Application.Log.WriteException` için yöntemini kullanın.  
  
     [!code-vb[VbVbalrMyApplicationLog#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#8)]  
  
     Aşağıdaki örnek, işlenmiş bir özel durumu günlüğe kaydetmek için tüm kodu gösterir.  
  
     [!code-vb[VbVbalrMyApplicationLog#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#10)]  
  
### <a name="to-log-an-unhandled-exception"></a>İşlenmeyen bir özel durumu günlüğe kaydetmek için  
  
1. **Çözüm Gezgini**' de bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' i seçin.  
  
2. **Uygulama** sekmesine tıklayın.  
  
3. Kod düzenleyicisini açmak için **uygulama olaylarını görüntüle** düğmesine tıklayın.  
  
     Bu, ApplicationEvents. vb dosyasını açar.  
  
4. ApplicationEvents. vb dosyasını kod düzenleyicisinde açın. **Genel** menüsünde **MyApplication olayları**' nı seçin.  
  
5. **Bildirimler** menüsünde **UnhandledException**öğesini seçin.  
  
     Uygulama, ana uygulama <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> çalışmadan önce olayı başlatır.  
  
6. `My.Application.Log.WriteException` Yöntemini `UnhandledException` olay işleyicisine ekleyin.  
  
     [!code-vb[VbVbalrMyApplicationLog#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#4)]  
  
     Aşağıdaki örnekte işlenmeyen bir özel durum günlüğe kaydetme için kodun tamamı gösterilmektedir.  
  
     [!code-vb[VbVbalrMyApplicationLog#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Uygulama Günlükleriyle Çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Nasıl yapılır: Günlük İletileri Yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
