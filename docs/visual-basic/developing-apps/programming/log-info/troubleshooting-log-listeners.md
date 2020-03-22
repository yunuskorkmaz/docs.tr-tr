---
title: 'Sorun Giderme: Günlük Dinleyicileri'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, troubleshooting
- troubleshooting Visual Basic, event logs
- troubleshooting event logs
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
ms.openlocfilehash: dd139935dae7fe4d1334b861e6590df29bab7202
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74346864"
---
# <a name="troubleshooting-log-listeners-visual-basic"></a>Sorun Giderme: Günlük Dinleyicileri (Visual Basic)

Uygulamanızda meydana `My.Application.Log` `My.Log` gelen olaylarla ilgili bilgileri günlüğe kaydetmek için nesneleri kullanabilirsiniz.  
  
 Bu iletileri hangi log dinleyicilerinin aldığını belirlemek [için, Bkz. Walkthrough: My.Application.Log Yazma Bilgileri nerede belirleyin](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).  
  
 Nesne, `Log` günlük tutarını sınırlamak için günlük filtrelemesini kullanabilir. Filtreler yanlış yapılandırılmışsa, günlükler yanlış bilgiler içerebilir. Filtreleme hakkında daha fazla bilgi için [bkz.](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)  
  
 Ancak, bir günlük yanlış yapılandırılırsa, geçerli yapılandırması hakkında daha fazla bilgiye ihtiyacınız olabilir. Bu bilgilere günlüğün gelişmiş `TraceSource` özelliğinden ulaşabilirsiniz.  
  
### <a name="to-determine-the-log-listeners-for-the-log-object-in-code"></a>Koddaki Log nesnesinin günlük dinleyicilerini belirlemek için  
  
1. Kod <xref:System.Diagnostics> dosyasının başındaki ad alanını içeri aktarın. Daha fazla bilgi [için, Bkz. İçerme Bildirimi (.NET Ad Alanı ve Türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
     [!code-vb[VbVbalrMyApplicationLog#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#13)]  
  
2. Log'un dinleyicilerinin her biri için bilgilerden oluşan bir dize döndüren bir işlev oluşturun.  
  
     [!code-vb[VbVbalrMyApplicationLog#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#14)]  
  
3. Log'un izleme dinleyicilerinin koleksiyonunu işleve `GetListeners` geçirin ve iade değerini görüntüleyin.  
  
     [!code-vb[VbVbalrMyApplicationLog#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#19)]  
  
     Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Uygulama Günlükleriyle Çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
