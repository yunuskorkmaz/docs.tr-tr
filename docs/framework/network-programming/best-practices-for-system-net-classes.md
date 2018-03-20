---
title: "System.Net sınıfları için en iyi yöntemler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sending data, best practices
- requesting data from Internet, best practices
- WebRequest class, best practices
- data requests, best practices
- WebResponse class, best practices
- best practices, data requests
- receiving data, best practices
ms.assetid: 716decc6-5952-47b7-9c5a-ba6fc5698684
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: 90722abbdb4568be115c0ac77007d5f18984df6f
ms.sourcegitcommit: 32172ca05d5dcce7ef3d327b9c8639c736e0fe2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2018
---
# <a name="best-practices-for-systemnet-classes"></a>System.Net sınıfları için en iyi yöntemler
Aşağıdaki önerileri bulunan sınıflar kullanmanıza yardımcı <xref:System.Net> en iyi kendi yararınıza:  
  
-   Aktarım Katmanı Güvenliği (TLS) en iyi yöntemler için bkz: [Aktarım Katmanı Güvenliği (TLS) en iyi uygulamalar .NET Framework ile](tls.md).

-   Kullanım <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> alt sınıflar için tür atama yerine mümkün. Kullanan uygulamalar **WebRequest** ve **WebResponse** yeni Internet protokolleri kapsamlı bir kod değişiklikleri olmadan yararlanabilirsiniz.  
  
-   Bir sunucu kullanarak çalıştırın ASP.NET uygulamaları yazarken **System.Net** sınıfları, bu genellikle için zaman uyumsuz yöntemleri kullanmak için bir performans açısından iyi <xref:System.Net.WebRequest.GetResponse%2A> ve <xref:System.Net.WebResponse.GetResponseStream%2A>.  
  
-   Bir Internet kaynağına açılan bağlantı sayısı, ağ performansı ve verimliliği hakkında önemli bir etkisi olabilir. **System.Net** varsayılan uygulama ana bilgisayar başına başına iki bağlantı kullanır. Ayarı <xref:System.Net.ServicePoint.ConnectionLimit%2A> özelliğinde <xref:System.Net.ServicePoint> için uygulamanızı belirli bir ana bilgisayar için bu sayıyı artırabilirsiniz. Ayar <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> özelliği, tüm ana bilgisayarlar için bu varsayılan artırabilirsiniz.  
  
-   Yuva düzeyi protokolleri yazılırken kullanmaya çalıştığınızda <xref:System.Net.Sockets.TcpClient> veya <xref:System.Net.Sockets.UdpClient> mümkün olduğunda doğrudan yazmak yerine bir <xref:System.Net.Sockets.Socket>. Bu iki istemci sınıfları bağlantı ayrıntılarını işlemek gerek kalmadan TCP ve UDP yuva oluşturulmasını kapsüller.  
  
-   Kimlik bilgileri gerektiren sitelerine erişirken <xref:System.Net.CredentialCache> sahip her isteği sağladığını yerine kimlik bilgilerinin önbellek oluşturmak için sınıfı. **CredentialCache** sınıfı oluşturma ve URL temel alınarak kimlik bilgileri sunan sorumluluk gereksinimini azaltır, bir istekle sunmak için uygun kimlik bilgilerini bulmak için önbellek arar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.NET Framework'te Ağ Programlaması](../../../docs/framework/network-programming/index.md)
