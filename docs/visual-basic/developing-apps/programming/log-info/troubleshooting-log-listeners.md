---
title: 'Sorun Giderme: Günlük Dinleyicileri'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, troubleshooting
- troubleshooting Visual Basic, event logs
- troubleshooting event logs
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
ms.openlocfilehash: dd139935dae7fe4d1334b861e6590df29bab7202
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346864"
---
# <a name="troubleshooting-log-listeners-visual-basic"></a>Sorun Giderme: Günlük Dinleyicileri (Visual Basic)

Uygulamanızda oluşan olaylarla ilgili bilgileri günlüğe kaydetmek için `My.Application.Log` ve `My.Log` nesnelerini kullanabilirsiniz.  
  
 Bu iletileri hangi günlük dinleyicilerinin alacağını belirlemek için bkz. [Walkthrough: My. Application. log bilgisinin nereden yazabileceğini belirleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).  
  
 `Log` nesnesi, günlük filtrelemeyi günlüğe kaydettiği bilgi miktarını sınırlamak için kullanabilir. Filtreler yanlış yapılandırılmış ise, günlüklerde yanlış bilgiler bulunabilir. Filtreleme hakkında daha fazla bilgi için bkz. [Izlenecek yol: My. Application. log çıktısını filtreleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).  
  
 Ancak, bir günlük yanlış yapılandırılmışsa, geçerli yapılandırması hakkında daha fazla bilgiye ihtiyacınız olabilir. Bu bilgilere günlüğün gelişmiş `TraceSource` özelliği aracılığıyla ulaşabilirsiniz.  
  
### <a name="to-determine-the-log-listeners-for-the-log-object-in-code"></a>Koddaki günlük nesnesinin günlük dinleyicilerini belirleme  
  
1. Kod dosyasının başındaki <xref:System.Diagnostics> ad alanını içeri aktarın. Daha fazla bilgi için bkz. [Imports açıklaması (.net ad alanı ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
     [!code-vb[VbVbalrMyApplicationLog#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#13)]  
  
2. Günlük dinleyicilerinin her biri için bilgilerden oluşan bir dize döndüren bir işlev oluşturun.  
  
     [!code-vb[VbVbalrMyApplicationLog#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#14)]  
  
3. Günlük izleme dinleyicilerinin koleksiyonunu `GetListeners` işlevine geçirin ve dönüş değerini görüntüleyin.  
  
     [!code-vb[VbVbalrMyApplicationLog#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#19)]  
  
     Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Uygulama Günlükleriyle Çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
