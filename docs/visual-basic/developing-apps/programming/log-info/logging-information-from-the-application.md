---
title: "Uygulamadan Günlüğe Bilgi Kaydetme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Log object
- My.Log object
- applications [Visual Basic], logging information from
- logging
- My.Application.Log object
- examples [Visual Basic], logging application information
ms.assetid: 8bf4f047-22d6-48d6-aec5-93b98ad5b8e8
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e52aaf4c26b4fa60ee04d7df6aa96980ebbf491
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="logging-information-from-the-application-visual-basic"></a>Uygulamadan Günlüğe Bilgi Kaydetme (Visual Basic)
Bu bölümde, uygulama kullanımından bilgileri günlüğe kaydetmek nasıl ele konuları bulunur `My.Application.Log` veya `My.Log` nesne ve uygulamanın günlüğe kaydetme özellikleri genişletme.  
  
 `Log` Nesnesi bilgileri uygulamanın günlük dinleyicileri için yazma yöntemleri sağlar ve `Log` nesnesi Gelişmiş `TraceSource` özelliği ayrıntılı yapılandırma bilgilerini sağlar. `Log` Nesnesi, uygulamanın yapılandırma dosyasına tarafından yapılandırılır.  
  
 `My.Log` Nesne yalnızca ASP.NET uygulamaları için kullanılabilir. İstemci uygulamaları için kullanmak `My.Application.Log`. Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Logging.Log>.  
  
## <a name="tasks"></a>Görevler  
  
|Bitiş|Bkz. |  
|--------|---------|  
|Olay bilgileri uygulamanın günlüklere yazılır.|[Nasıl yapılır: günlük iletileri yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)|  
|Özel durum bilgileri uygulamanın günlüklere yazılır.|[Nasıl yapılır: günlük özel durumları](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)|  
|Uygulamayı başlatır ve kapandığında izleme bilgilerini uygulamanın günlüklere yazılır.|[Nasıl yapılır: uygulama başlatır veya kapanırken iletileri günlüğe](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-messages-when-the-application-starts-or-shuts-down.md)|  
|Yapılandırma `My.Application.Log` bilgilerini metin dosyasına yazma.|[Nasıl yapılır: olay bilgilerini metin dosyasına yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)|  
|Yapılandırma `My.Application.Log` bilgilerini bir olay günlüğüne yazma.|[Nasıl yapılır: uygulama olay günlüğüne yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)|  
|Değiştirme nereye `My.Application.Log` bilgi yazar.|[İzlenecek yol: My.Application.Log günlüğünün bilgileri yazdığı değiştirme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)|  
|Nereye belirlemek `My.Application.Log` bilgi yazar.|[İzlenecek yol: My.Application.log günlüğünün bilgileri nereye yazdığını belirleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)|  
|İçin özel günlük dinleyicisi oluşturmak `My.Application.Log`.|[İzlenecek yol: Özel günlük dinleyicileri oluşturma](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)|  
|Çıktısını filtre `My.Application.Log` günlükleri.|[İzlenecek yol: My.Application.Log çıktısını filtreleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 [Uygulama günlükleriyle çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [Sorun giderme: Günlük dinleyicileri](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)
