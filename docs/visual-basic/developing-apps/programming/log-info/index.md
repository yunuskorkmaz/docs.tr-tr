---
description: 'Hakkında daha fazla bilgi edinin: uygulamadan bilgileri günlüğe kaydetme (Visual Basic)'
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
ms.openlocfilehash: 6e0adf45c12d98c8bc6d177d85accf9bee347f75
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775077"
---
# <a name="logging-information-from-the-application-visual-basic"></a>Uygulamadan Günlüğe Bilgi Kaydetme (Visual Basic)

Bu bölüm, veya nesnesini kullanarak uygulamanızdaki bilgilerin nasıl günlüğe alınacağını `My.Application.Log` `My.Log` ve uygulamanın günlüğe kaydetme yeteneklerini genişletmeyi kapsayan konuları içerir.  
  
 `Log`Nesnesi, uygulamanın günlük dinleyicilerine bilgi yazma yöntemleri sağlar ve `Log` nesnenin Gelişmiş `TraceSource` özelliği ayrıntılı yapılandırma bilgileri sağlar. `Log`Nesne, uygulamanın yapılandırma dosyası tarafından yapılandırılır.  
  
 `My.Log`Nesne yalnızca ASP.NET uygulamaları için kullanılabilir. İstemci uygulamaları için kullanın `My.Application.Log` . Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Logging.Log>.  
  
## <a name="tasks"></a>Görevler  
  
|Amaç|Bkz.|  
|--------|---------|  
|Olay bilgilerini uygulamanın günlüklerine yazın.|[Nasıl yapılır: Günlük İletileri Yazma](how-to-write-log-messages.md)|  
|Özel durum bilgilerini uygulamanın günlüklerine yazın.|[Nasıl yapılır: Özel Durumları Günlüğe Kaydetme](how-to-log-exceptions.md)|  
|Uygulama başlatıldığında ve kapandığında izleme bilgilerini uygulamanın günlüklerine yazın.|[Nasıl yapılır: Uygulama Başlarken veya Kapanırken İletileri Günlüğe Kaydetme](how-to-log-messages-when-the-application-starts-or-shuts-down.md)|  
|`My.Application.Log`Bir metin dosyasına bilgi yazmak için yapılandırın.|[Nasıl yapılır: Olay Bilgilerini Metin Dosyasına Yazma](how-to-write-event-information-to-a-text-file.md)|  
|`My.Application.Log`Bir olay günlüğüne bilgi yazmak için yapılandırın.|[Nasıl yapılır: Uygulama Olay Günlüğüne Yazma](how-to-write-to-an-application-event-log.md)|  
|Yazma bilgilerinin bulunduğu yeri değiştirin `My.Application.Log` .|[İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme](walkthrough-changing-where-my-application-log-writes-information.md)|  
|Nerede `My.Application.Log` yazma bilgileri belirlenir.|[İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme](walkthrough-determining-where-my-application-log-writes-information.md)|  
|İçin özel bir günlük dinleyicisi oluşturun `My.Application.Log` .|[İzlenecek yol: Özel Günlük Dinleyicileri Oluşturma](walkthrough-creating-custom-log-listeners.md)|  
|Günlüklerin çıkışını filtreleyin `My.Application.Log` .|[İzlenecek yol: My.Application.Log Çıktısını Filtreleme](walkthrough-filtering-my-application-log-output.md)|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Uygulama Günlükleriyle Çalışma](working-with-application-logs.md)
- [Sorun Giderme: Günlük Dinleyicileri](troubleshooting-log-listeners.md)
