---
title: GRPC uygulamalarında güvenlik-WCF geliştiricileri için gRPC
description: GRPC 'de çağrı ve kanal kimlik doğrulamasına ve yetkilendirmeye genel bakış.
ms.date: 09/02/2019
ms.openlocfilehash: d5804ad5de4a834eb81b90fa1ea7a61969a0b42f
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503412"
---
# <a name="security-in-grpc-applications"></a>gRPC uygulamalarında güvenlik

Herhangi bir gerçek Dünya senaryosunda, uygulamaların ve hizmetlerin güvenliğini sağlamak önemlidir. Güvenlik üç temel alan içerir: 

* Kötü amaçlı korsanların bunu kesintiye uğramasını engellemek için ağ trafiğini şifreleme.
* Kimlik ve güven sağlamak için istemcilerin ve sunucuların kimlik doğrulamasını yapın.
* İstemcilere erişimi denetlemek ve kimlik tabanlı izinleri uygulamak için istemcileri yetkilendirme.

> [!NOTE]
> *Kimlik doğrulaması* , bir istemci veya sunucu kimliğini kurmaya önem vermez. *Yetkilendirme* , bir istemcinin bir kaynağa erişme izni olup olmadığını belirlemekten ve bir komut sormasından endişe edilir.

Bu bölümde, ASP.NET Core için gRPC 'de kimlik doğrulama ve yetkilendirme olanakları ele alınacaktır. Ayrıca, TLS şifreli bağlantıları aracılığıyla ağ güvenliğini de tartışır.

## <a name="wcf-authentication-and-authorization"></a>WCF kimlik doğrulaması ve yetkilendirme

Windows Communication Foundation (WCF) ' de, kimlik doğrulama ve yetkilendirme, kullanılan aktarımlara ve bağlamalara bağlı olarak farklı yollarla işlenmekte. WCF, çeşitli WS-\* güvenlik standartlarını destekliyordu. Ayrıca, IIS veya Windows sistemleri arasında NetTCP hizmetlerinde çalışan HTTP Hizmetleri için Windows kimlik doğrulamasını da destekler.

## <a name="grpc-authentication-and-authorization"></a>gRPC kimlik doğrulaması ve yetkilendirme

gRPC kimlik doğrulaması ve yetkilendirme iki düzeyde geçerlidir:

* Çağrı düzeyi kimlik doğrulaması/yetkilendirme genellikle, çağrı yapıldığında meta verilerde uygulanan belirteçler aracılığıyla işlenir. 
* Kanal düzeyinde kimlik doğrulama, bağlantı düzeyinde uygulanan bir istemci sertifikası kullanır. Ayrıca, kanaldaki her çağrıya otomatik olarak uygulanacak çağrı düzeyi kimlik doğrulama/yetkilendirme kimlik bilgilerini de içerebilir. 

Hizmetinizin güvenliğini sağlamaya yardımcı olması için bu mekanizmalardan birini ya da her ikisini birden kullanabilirsiniz.

GRPC 'nin ASP.NET Core uygulanması, standart ASP.NET Core mekanizmalarının çoğunda kimlik doğrulama ve yetkilendirmeyi destekler:

- Kimlik doğrulama çağrısı
  - Azure Active Directory
  - IdentityServer
  - JWT taşıyıcı belirteci
  - OAuth 2.0
  - OpenID Connect
  - WS-Federation
- Kanal kimlik doğrulaması
  - istemci sertifikası

Çağrı kimlik doğrulama yöntemlerinin hepsi *belirteçleri*temel alır. Tek gerçek fark, belirteçlerin oluşturulma biçimi ve ASP.NET Core hizmetindeki belirteçleri doğrulamak için kullanılan kitaplıklardır.

Daha fazla bilgi için bkz. [kimlik doğrulama ve yetkilendirme](/aspnet/core/grpc/authn-and-authz) makalesi.

> [!NOTE]
> GRPC 'yi TLS şifreli HTTP/2 bağlantısı üzerinden kullandığınızda, kanal düzeyinde kimlik doğrulaması kullanmasanız bile istemciler ve sunucular arasındaki tüm trafik şifrelenir.

Bu bölümde, bir gRPC hizmetine çağrı kimlik bilgilerinin ve kanal kimlik bilgilerinin nasıl uygulanacağı gösterilmektedir. Ayrıca, hizmet ile kimlik doğrulamak için bir .NET Core gRPC istemcisinden kimlik bilgilerinin nasıl kullanılacağını gösterir.

>[!div class="step-by-step"]
>[Önceki](client-libraries.md)
>[İleri](call-credentials.md)
