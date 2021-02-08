---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Visual Basic özel durumları günlüğe kaydetme'
title: 'Nasıl yapılır: Özel Durumları Günlüğe Kaydetme'
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, logging
- exceptions, tracking
ms.assetid: a26c60e2-ae39-444a-aebb-33eccadc0eeb
ms.openlocfilehash: a4155de4e73c632edf071256976161cfdbffba77
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775220"
---
# <a name="how-to-log-exceptions-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Günlük Özel Durumları

`My.Application.Log` `My.Log` Uygulamanızda oluşan özel durumlarla ilgili bilgileri günlüğe kaydetmek için ve nesnelerini kullanabilirsiniz. Bu örnekler, `My.Application.Log.WriteException` açıkça yakalayacak özel durumları ve işlenmemiş özel durumları günlüğe kaydetmek için yönteminin nasıl kullanılacağını gösterir.  
  
 İzleme bilgilerini günlüğe kaydetmek için yöntemini kullanın `My.Application.Log.WriteEntry` . Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>.  
  
### <a name="to-log-a-handled-exception"></a>İşlenmiş bir özel durumu günlüğe kaydetmek için  
  
1. Özel durum bilgilerini oluşturacak yöntemi oluşturun.  
  
     [!code-vb[VbVbalrMyApplicationLog#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#9)]  
  
2. `Try...Catch`Özel durumu yakalamak için bir blok kullanın.  
  
     [!code-vb[VbVbalrMyApplicationLog#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#6)]  
  
3. Bloğa özel durum üretebilen kodu koyun `Try` .  
  
     `Dim` `MsgBox` Özel duruma neden olacak şekilde ve satırlarının açıklamasını kaldırın <xref:System.NullReferenceException> .  
  
     [!code-vb[VbVbalrMyApplicationLog#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#7)]  
  
4. `Catch`Bloğunda, `My.Application.Log.WriteException` özel durum bilgilerini yazmak için yöntemini kullanın.  
  
     [!code-vb[VbVbalrMyApplicationLog#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#8)]  
  
     Aşağıdaki örnek, işlenmiş bir özel durumu günlüğe kaydetmek için tüm kodu gösterir.  
  
     [!code-vb[VbVbalrMyApplicationLog#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#10)]  
  
### <a name="to-log-an-unhandled-exception"></a>İşlenmeyen bir özel durumu günlüğe kaydetmek için  
  
1. **Çözüm Gezgini**' de bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' i seçin.  
  
2. **Uygulama** sekmesine tıklayın.  
  
3. Kod düzenleyicisini açmak için **uygulama olaylarını görüntüle** düğmesine tıklayın.  
  
     Bu, ApplicationEvents. vb dosyasını açar.  
  
4. ApplicationEvents. vb dosyasını kod düzenleyicisinde açın. **Genel** menüsünde **MyApplication olayları**' nı seçin.  
  
5. **Bildirimler** menüsünde **UnhandledException** öğesini seçin.  
  
     Uygulama, <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> ana uygulama çalışmadan önce olayı başlatır.  
  
6. `My.Application.Log.WriteException`Yöntemini `UnhandledException` olay işleyicisine ekleyin.  
  
     [!code-vb[VbVbalrMyApplicationLog#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#4)]  
  
     Aşağıdaki örnekte işlenmeyen bir özel durum günlüğe kaydetme için kodun tamamı gösterilmektedir.  
  
     [!code-vb[VbVbalrMyApplicationLog#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Uygulama Günlükleriyle Çalışma](working-with-application-logs.md)
- [Nasıl yapılır: Günlük İletileri Yazma](how-to-write-log-messages.md)
- [İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme](walkthrough-determining-where-my-application-log-writes-information.md)
- [İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme](walkthrough-changing-where-my-application-log-writes-information.md)
