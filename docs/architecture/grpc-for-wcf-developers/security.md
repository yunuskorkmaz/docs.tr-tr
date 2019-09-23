---
title: GRPC uygulamalarında güvenlik-WCF geliştiricileri için gRPC
description: GRPC 'de çağrı ve kanal kimlik doğrulamasına ve yetkilendirmeye genel bakış.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 5f3d32817ccb5d9f278d256c0ee135f0e2a17cf2
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184143"
---
# <a name="security-in-grpc-applications"></a>GRPC uygulamalarında güvenlik

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Herhangi bir gerçek Dünya senaryosunda, uygulamaların ve hizmetlerin güvenliğini sağlamak önemlidir. Güvenlik üç temel alanı ele alır: ağ trafiğini, kötü aktörler tarafından kesilmesini engelleyecek şekilde şifreleme; kimlik ve güven sağlamak için istemcilerin ve sunucuların kimliğini doğrulama; ve istemcilere erişimi denetlemek ve kimlik tabanlı izinleri uygulamak için istemcileri yetkilendirin.

> [!NOTE]
> **Kimlik doğrulaması** , bir istemci veya sunucu kimliğini kurmaya önem vermez. **Yetkilendirme** , bir istemcinin bir kaynağa erişme izni olup olmadığını belirlemekten ve bir komut sormasından endişe edilir.

Bu bölümde, ASP.NET Core için gRPC 'de kimlik doğrulama ve yetkilendirme olanakları ele alınmaktadır ve TLS şifreli bağlantıları kullanarak ağ güvenliği tartışılecektir.

## <a name="wcf-authentication-and-authorization"></a>WCF kimlik doğrulaması ve yetkilendirme

WCF 'de, kimlik doğrulama ve yetkilendirme, kullanılan aktarımlara ve bağlamalara bağlı olarak farklı şekillerde işlenmekte. WCF, çeşitli WS-\* Security standartları ve IIS veya Windows sistemleri arasında NetTcp hizmetlerinde çalışan http Hizmetleri için Windows kimlik doğrulaması 'nı destekliyordu.

## <a name="grpc-authentication-and-authorization"></a>gRPC kimlik doğrulaması ve yetkilendirme

gRPC kimlik doğrulaması ve yetkilendirme iki düzeyde kullanılabilir. Çağrı düzeyi kimlik doğrulaması/yetkilendirme genellikle, çağrı yapıldığında meta verilerde uygulanan belirteçler kullanılarak işlenir. Kanal düzeyinde kimlik doğrulaması, bağlantı düzeyinde uygulanan bir istemci sertifikası kullanır ve kanaldaki her çağrıya otomatik olarak uygulanacak çağrı düzeyi kimlik doğrulama/yetkilendirme kimlik bilgilerini de içerebilir. Hizmetinizi güvenli hale getirmek için bu mekanizmalardan birini ya da her ikisini birden kullanabilirsiniz.

GRPC 'nin ASP.NET Core uygulanması, standart ASP.NET Core mekanizmalarının çoğunu kullanarak kimlik doğrulaması ve yetkilendirmeyi destekler:

- Kimlik doğrulama çağrısı
  - Azure Active Directory
  - IdentityServer
  - JWT taşıyıcı belirteci
  - OAuth 2,0
  - OpenID Connect
  - WS-Federation
- Kanal kimlik doğrulaması
  - İstemci sertifikası

Çağrı kimlik doğrulama yöntemlerinin hepsi *belirteçleri*temel alır. Tek gerçek fark, belirtecin oluşturulma biçimi ve ASP.NET Core hizmetindeki belirteçleri doğrulamak için kullanılan kitaplıklardır.

Daha fazla bilgi için [Microsoft docs üzerindeki kimlik doğrulama ve yetkilendirme belgelerine](https://docs.microsoft.com/aspnet/core/grpc/authn-and-authz?view=aspnetcore-3.0)bakın.

> [!NOTE]
> GRPC 'yi TLS şifreli HTTP/2 bağlantısı üzerinden kullanırken, kanal düzeyinde kimlik doğrulaması kullanmasanız bile istemciler ve sunucular arasındaki tüm trafik şifrelenir.

Bu bölümde, bir gRPC hizmetine çağrı kimlik bilgileri ve kanal kimlik bilgilerinin nasıl uygulanacağı ve hizmet ile kimlik doğrulaması için bir .NET Core gRPC istemcisinden kimlik bilgilerinin nasıl kullanılacağı gösterilmektedir.

>[!div class="step-by-step"]
>[Önceki](client-libraries.md)
>[İleri](call-credentials.md)
