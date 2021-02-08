---
description: 'Daha fazla bilgi edinin: sorun giderme: günlük dinleyicileri (Visual Basic)'
title: 'Sorun Giderme: Günlük Dinleyicileri'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, troubleshooting
- troubleshooting Visual Basic, event logs
- troubleshooting event logs
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
ms.openlocfilehash: dc40f88a19e9cb205c6adb290c1ed48d40eabf5b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775051"
---
# <a name="troubleshooting-log-listeners-visual-basic"></a>Sorun Giderme: Günlük Dinleyicileri (Visual Basic)

`My.Application.Log` `My.Log` Uygulamanızda gerçekleşen olaylar hakkındaki bilgileri günlüğe kaydetmek için ve nesnelerini kullanabilirsiniz.  
  
 Bu iletileri hangi günlük dinleyicilerinin alacağını belirlemek için bkz. [Walkthrough: My. Application. log bilgisinin nereden yazabileceğini belirleme](walkthrough-determining-where-my-application-log-writes-information.md).  
  
 `Log`Nesnesi, günlük filtrelemeyi günlüğe kaydettiği bilgi miktarını sınırlamak için kullanabilir. Filtreler yanlış yapılandırılmış ise, günlüklerde yanlış bilgiler bulunabilir. Filtreleme hakkında daha fazla bilgi için bkz. [Izlenecek yol: My. Application. log çıktısını filtreleme](walkthrough-filtering-my-application-log-output.md).  
  
 Ancak, bir günlük yanlış yapılandırılmışsa, geçerli yapılandırması hakkında daha fazla bilgiye ihtiyacınız olabilir. Bu bilgilere günlüğün gelişmiş özelliğini kullanarak ulaşabilirsiniz `TraceSource` .  
  
### <a name="to-determine-the-log-listeners-for-the-log-object-in-code"></a>Koddaki günlük nesnesinin günlük dinleyicilerini belirleme  
  
1. <xref:System.Diagnostics>Kod dosyasının başındaki ad alanını içeri aktarın. Daha fazla bilgi için bkz. [Imports açıklaması (.net ad alanı ve türü)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
     [!code-vb[VbVbalrMyApplicationLog#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#13)]  
  
2. Günlük dinleyicilerinin her biri için bilgilerden oluşan bir dize döndüren bir işlev oluşturun.  
  
     [!code-vb[VbVbalrMyApplicationLog#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#14)]  
  
3. Günlük izleme dinleyicilerinin koleksiyonunu `GetListeners` işleve geçirin ve dönüş değerini görüntüleyin.  
  
     [!code-vb[VbVbalrMyApplicationLog#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#19)]  
  
     Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Uygulama Günlükleriyle Çalışma](working-with-application-logs.md)
- [İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme](walkthrough-determining-where-my-application-log-writes-information.md)
