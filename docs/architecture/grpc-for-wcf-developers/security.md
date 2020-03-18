---
title: gRPC uygulamalarında güvenlik - WCF geliştiricileri için gRPC
description: gRPC'de arama ve kanal kimlik doğrulama ve yetkilendirmeye genel bakış.
ms.date: 09/02/2019
ms.openlocfilehash: 70cbf441bbc1b299b997f7d1f02bcd2bf7fde60c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147821"
---
# <a name="security-in-grpc-applications"></a>gRPC uygulamalarında güvenlik

Herhangi bir gerçek dünya senaryosunda, uygulamaları ve hizmetleri güvence altına almak esastır. Güvenlik üç önemli alanı kapsar:

* Kötü amaçlı bilgisayar korsanlarının ağ trafiğini engellemesini önlemek için ağ trafiğini şifreleme.
* Kimlik ve güven oluşturmak için istemcilerin ve sunucuların kimlik doğrulaması.
* İstemcileri sistemlere erişimi denetleme ve kimlik durumuna göre izinleri uygulama yetkisi vermek.

> [!NOTE]
> *Kimlik doğrulama,* bir istemci nin veya sunucunun kimliğinin belirlenmesiyle ilgilidir. *Yetkilendirme,* istemcinin kaynağa erişmek veya bir komut verme izni olup olmadığını belirlemekle ilgilidir.

Bu bölüm, ASP.NET Core için gRPC'de kimlik doğrulama ve yetkilendirme olanaklarını kapsayacaktır. Ayrıca TLS şifreli bağlantılar üzerinden ağ güvenliği tartışacak.

## <a name="wcf-authentication-and-authorization"></a>WCF kimlik doğrulaması ve yetkilendirmesi

Windows Communication Foundation'da (WCF) kimlik doğrulama ve yetkilendirme, kullanılan taşımalara ve bağlamalara bağlı olarak farklı şekillerde ele alındı. WCF çeşitli WS\* güvenlik standartlarını desteklemiştir. Ayrıca, Windows sistemleri arasında IIS veya NetTCP hizmetlerinde çalışan HTTP hizmetleri için Windows kimlik doğrulamasını da desteklemektedir.

## <a name="grpc-authentication-and-authorization"></a>gRPC kimlik doğrulama ve yetkilendirme

gRPC kimlik doğrulama ve yetkilendirme iki düzeyde çalışır:

* Çağrı düzeyinde kimlik doğrulama/yetkilendirme genellikle arama yapıldığında meta verilerde uygulanan belirteçler aracılığıyla işlenir.
* Kanal düzeyinde kimlik doğrulaması, bağlantı düzeyinde uygulanan bir istemci sertifikası kullanır. Ayrıca, kanaldaki her çağrıya otomatik olarak uygulanacak çağrı düzeyinde kimlik doğrulama/yetkilendirme kimlik bilgilerini de içerebilir.

Hizmetinizin güvenliğini sağlamak için bu mekanizmalardan birini veya her ikisini de kullanabilirsiniz.

gRPC'nin ASP.NET Core uygulaması, standart ASP.NET Çekirdek mekanizmalarının çoğu aracılığıyla kimlik doğrulamave yetkilendirmeyi destekler:

- Arama kimlik doğrulaması
  - Azure Active Directory
  - IdentityServer
  - JWT Taşıyıcı Belirteci
  - OAuth 2.0
  - OpenID Connect
  - WS-Federation
- Kanal kimlik doğrulaması
  - İstemci sertifikası

Arama kimlik doğrulama yöntemlerinin tümü *belirteçlere*dayanır. Tek gerçek fark, belirteçlerin nasıl oluşturulduğu ve ASP.NET Core hizmetindeki belirteçleri doğrulamak için kullanılan kitaplıklardır.

Daha fazla bilgi için [Kimlik Doğrulama ve yetkilendirme](/aspnet/core/grpc/authn-and-authz) makalesine bakın.

> [!NOTE]
> TLS şifreli http/2 bağlantısı üzerinden gRPC kullanıyorsanız, kanal düzeyinde kimlik doğrulama kullanmasanız bile istemciler ve sunucular arasındaki tüm trafik şifrelenir.

Bu bölümde, bir gRPC hizmetine çağrı kimlik bilgileri ve kanal kimlik bilgileri nasıl uygulanacağı gösterecektir. Ayrıca, hizmetle ilgili kimlik doğrulamaiçin bir .NET Core gRPC istemcisinden kimlik bilgilerinin nasıl kullanılacağını da gösterir.

>[!div class="step-by-step"]
>[Önceki](client-libraries.md)
>[Sonraki](call-credentials.md)
