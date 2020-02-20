---
title: WS-* Protocols-WCF geliştiricileri için gRPC
description: WCF tarafından desteklenen WS-* protokollerini ve gRPC ile kullanılabilen alternatifleri gözden geçirme
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: c8c06a5e23a4d7859165e1c562032055d63d76f7
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503293"
---
# <a name="ws--protocols"></a>WS-\* protokolleri

Windows Communication Foundation (WCF) ile çalışmanın gerçek avantajlarından biri, var olan _WS-\*_ standart protokollerinin çoğunu destekliyordu. Bu bölüm, gRPC 'nin aynı WS-\* protokollerini nasıl yönettiğini kısaca kapsar ve alternatif olmadığında hangi seçeneklerin kullanılabilir olduğunu tartışır.

## <a name="metadata-exchange-ws-policy-ws-discovery-and-so-on"></a>Meta veri değişimi: WS-Policy, WS-Discovery, vb.

SOAP Hizmetleri, veri biçimleri, işlemler veya iletişim seçenekleri gibi bilgilerle Web Hizmetleri Açıklama Dili (WSDL) şema belgelerini kullanıma sunar. Bu şemayı, istemci kodunu oluşturmak için kullanabilirsiniz.

gRPC, sunucular ve istemciler aynı `.proto` dosyalarından oluşturulduğunda en iyi şekilde çalışır, ancak sunucu yansıması isteğe bağlı uzantısı, çalışan bir sunucudan dinamik bilgileri açığa çıkarmak için bir yol sağlar. Daha fazla bilgi için bkz. [GRPC. Reflection](https://nuget.org/packages/Grpc.Reflection) NuGet paketi ve [GRPC C# sunucusu yansıma](https://github.com/grpc/grpc/blob/master/doc/csharp/server_reflection.md) makalesi.

WS-Discovery protokolü, yerel bir ağdaki hizmetleri bulmak için kullanılır. gRPC Hizmetleri genellikle DNS veya Tüketil veya ZooKeeper gibi bir hizmet kayıt defteri aracılığıyla bulunur.

## <a name="security-ws-security-ws-federation-xml-encryption-and-so-on"></a>Güvenlik: WS-Security, WS-Federation, XML şifrelemesi, vb.

Güvenlik, kimlik doğrulaması ve yetkilendirme, [Bölüm 6](security.md)' da çok daha ayrıntılı olarak ele alınmıştır. Ancak, WCF 'nin aksine gRPC WS-Security, WS-Federation veya XML şifrelemesini desteklemediğinden buraya dikkat edin. Bu nedenle, gRPC harika güvenlik sağlar. TLS üzerinden HTTP/2 kullanırken tüm gRPC ağ trafiği otomatik olarak şifrelenir. Karşılıklı istemci/sunucu kimlik doğrulaması için x509 sertifikaları kullanabilirsiniz.

## <a name="ws-reliablemessaging"></a>WS-ReliableMessaging

gRPC, WS-ReliableMessaging ' e eşdeğer değildir. Yeniden deneme semantiği, muhtemelen [Polly](https://github.com/App-vNext/Polly)gibi bir kitaplıkla birlikte kodda işlenmelidir. Kubernetes veya benzer düzenleme ortamlarında çalışırken [hizmet kafesleri](service-mesh.md) , hizmetler arasında güvenilir mesajlaşma sağlamaya da yardımcı olabilir.

## <a name="ws-transaction-ws-coordination"></a>WS-Işlem, WS koordinasyonu

WCF 'nin dağıtılmış işlemlerin uygulanması Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) kullanır. Bu, SQL Server, MSMQ veya Windows dosya sistemleri gibi, özellikle destekleyen kaynak yöneticileriyle birlikte kullanılabilir. Modern mikro hizmetler dünyasında, kullanımda olan daha geniş teknoloji yelpazüsüne bağlı olarak henüz eşdeğer değildir. İşlem tartışması için bkz. [ek a](appendix.md).

>[!div class="step-by-step"]
>[Önceki](error-handling.md)
>[İleri](migrate-wcf-to-grpc.md)
