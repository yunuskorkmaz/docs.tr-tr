---
title: 'Sorun giderme: Günlük dinleyicileri (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, troubleshooting
- troubleshooting Visual Basic, event logs
- troubleshooting event logs
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
ms.openlocfilehash: f2dba14ed883b428e47b71533bcb51506167fd49
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979014"
---
# <a name="troubleshooting-log-listeners-visual-basic"></a>Sorun giderme: Günlük dinleyicileri (Visual Basic)
Kullanabileceğiniz `My.Application.Log` ve `My.Log` gerçekleşen olaylar hakkında bilgileri, uygulamanızda oturum nesneleri.  
  
 Hangi günlük dinleyicileri bu iletileri almak belirlemek için bkz: [izlenecek yol: My.Application.log günlüğünün bilgileri nereye yazdığını belirleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).  
  
 `Log` Nesne günlük filtreleme kaydeder bilgi tutarını sınırlamak için kullanabilirsiniz. Filtreler yanlış, günlükleri yanlış bilgi içerebilir. Filtreleme hakkında daha fazla bilgi için bkz. [izlenecek yol: My.Application.Log çıktısını filtreleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).  
  
 Ancak, bir günlük hatalı yapılandırıldıysa, geçerli yapılandırma hakkında daha fazla bilgi gerekebilir. Ulaşmak için bu bilgileri günlüğe aracılığıyla Gelişmiş `TraceSource` özelliği.  
  
### <a name="to-determine-the-log-listeners-for-the-log-object-in-code"></a>Kod günlük nesneye için günlük dinleyicileri belirlemek için  
  
1.  İçeri aktarma <xref:System.Diagnostics> kod dosyasının başında ad alanı. Daha fazla bilgi için [Imports deyimi (.NET Namespace ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
     [!code-vb[VbVbalrMyApplicationLog#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#13)]  
  
2.  Her bir günlüğün dinleyicileri için bilgi içeren bir dize döndüren bir işlev oluşturun.  
  
     [!code-vb[VbVbalrMyApplicationLog#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#14)]  
  
3.  Günlüğün izleme dinleyicilerine koleksiyonunu geçirmek `GetListeners` işlev ve dönüş değeri görüntüler.  
  
     [!code-vb[VbVbalrMyApplicationLog#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#19)]  
  
     Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Uygulama Günlükleriyle Çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [İzlenecek yol: My.Application.log günlüğünün bilgileri nereye yazdığını belirleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
