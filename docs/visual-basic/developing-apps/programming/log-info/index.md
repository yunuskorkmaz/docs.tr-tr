---
title: Uygulamadan Günlüğe Bilgi Kaydetme
ms.date: 07/20/2015
helpviewer_keywords:
- Log object
- My.Log object
- applications [Visual Basic], logging information from
- logging
- My.Application.Log object
- examples [Visual Basic], logging application information
ms.assetid: 8bf4f047-22d6-48d6-aec5-93b98ad5b8e8
ms.openlocfilehash: dace4bac3bf7529b8c50a492a092ad478f4d9e2d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74353249"
---
# <a name="logging-information-from-the-application-visual-basic"></a>Uygulamadan Günlüğe Bilgi Kaydetme (Visual Basic)

Bu bölüm, `My.Application.Log` veya `My.Log` nesnesini kullanarak uygulamanızdaki bilgilerin nasıl günlüğe alınacağını ve uygulamanın günlüğe kaydetme yeteneklerini genişletmeyi kapsayan konuları içerir.  
  
 `Log` Nesnesi, uygulamanın günlük dinleyicilerine bilgi yazma yöntemleri sağlar ve `Log` nesnenin Gelişmiş `TraceSource` özelliği ayrıntılı yapılandırma bilgileri sağlar. `Log` Nesne, uygulamanın yapılandırma dosyası tarafından yapılandırılır.  
  
 `My.Log` Nesne yalnızca ASP.NET uygulamaları için kullanılabilir. İstemci uygulamaları için kullanın `My.Application.Log`. Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Logging.Log>.  
  
## <a name="tasks"></a>Görevler  
  
|Alıcı|Bkz.|  
|--------|---------|  
|Olay bilgilerini uygulamanın günlüklerine yazın.|[Nasıl yapılır: Günlük İletileri Yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)|  
|Özel durum bilgilerini uygulamanın günlüklerine yazın.|[Nasıl yapılır: Özel Durumları Günlüğe Kaydetme](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)|  
|Uygulama başlatıldığında ve kapandığında izleme bilgilerini uygulamanın günlüklerine yazın.|[Nasıl yapılır: Uygulama Başlarken veya Kapanırken İletileri Günlüğe Kaydetme](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-messages-when-the-application-starts-or-shuts-down.md)|  
|Bir `My.Application.Log` metin dosyasına bilgi yazmak için yapılandırın.|[Nasıl yapılır: Olay Bilgilerini Metin Dosyasına Yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)|  
|Bir `My.Application.Log` olay günlüğüne bilgi yazmak için yapılandırın.|[Nasıl yapılır: Uygulama Olay Günlüğüne Yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)|  
|Yazma bilgilerinin `My.Application.Log` bulunduğu yeri değiştirin.|[İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)|  
|Nerede `My.Application.Log` yazma bilgileri belirlenir.|[İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)|  
|İçin `My.Application.Log`özel bir günlük dinleyicisi oluşturun.|[İzlenecek yol: Özel Günlük Dinleyicileri Oluşturma](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)|  
|`My.Application.Log` Günlüklerin çıkışını filtreleyin.|[İzlenecek yol: My.Application.Log Çıktısını Filtreleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Uygulama Günlükleriyle Çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Sorun Giderme: Günlük Dinleyicileri](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)
