---
title: "Sorun Giderme: Günlük Dinleyicileri (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- event logs, troubleshooting
- troubleshooting Visual Basic, event logs
- troubleshooting event logs
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 14db7019415405af89e9f5e317da617debeb0a19
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="troubleshooting-log-listeners-visual-basic"></a>Sorun Giderme: Günlük Dinleyicileri (Visual Basic)
Kullanabileceğiniz `My.Application.Log` ve `My.Log` uygulamanızda oluşan olaylarla ilgili bilgileri günlüğe kaydetmek için nesneleri.  
  
 Hangi günlük dinleyicileri bu iletilerini belirlemek için bkz: [izlenecek yol: belirleme nerede My.Application.Log Yazar bilgisini](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).  
  
 `Log` Nesne günlük filtreleme, günlükleri bilgi tutarını sınırlamak için kullanabilirsiniz. Filtreler yanlış olmadığını günlükleri yanlış bilgiler içerebilir. Filtreleme hakkında daha fazla bilgi için bkz: [izlenecek yol: My.Application.Log çıktısını filtreleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).  
  
 Ancak, bir günlük hatalı yapılandırıldıysa, geçerli yapılandırması hakkında daha fazla bilgi gerekebilir. İçin edinebilirsiniz bu bilgileri günlük aracılığıyla Gelişmiş `TraceSource` özelliği.  
  
### <a name="to-determine-the-log-listeners-for-the-log-object-in-code"></a>Kod günlük nesnesinde günlük dinleyicileri belirlemek için  
  
1.  İçeri aktarma <xref:System.Diagnostics> kod dosyasının başında ad alanı. Daha fazla bilgi için bkz: [Imports deyimi (.NET Namespace ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
     [!code-vb[VbVbalrMyApplicationLog#13](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_1.vb)]  
  
2.  Her günlüğün dinleyicileri için bilgileri içeren bir dize döndüren bir işlev oluşturun.  
  
     [!code-vb[VbVbalrMyApplicationLog#14](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_2.vb)]  
  
3.  Günlüğün izleme dinleyicileri koleksiyonu geçirmek `GetListeners` işlev ve dönüş değeri görüntüler.  
  
     [!code-vb[VbVbalrMyApplicationLog#19](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_3.vb)]  
  
     Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 [Uygulama günlükleriyle çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [İzlenecek yol: My.Application.log günlüğünün bilgileri nereye yazdığını belirleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
