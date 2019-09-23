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
# <a name="security-in-grpc-applications"></a><span data-ttu-id="2c640-103">GRPC uygulamalarında güvenlik</span><span class="sxs-lookup"><span data-stu-id="2c640-103">Security in gRPC applications</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="2c640-104">Herhangi bir gerçek Dünya senaryosunda, uygulamaların ve hizmetlerin güvenliğini sağlamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="2c640-104">In any real-world scenario, securing applications and services is essential.</span></span> <span data-ttu-id="2c640-105">Güvenlik üç temel alanı ele alır: ağ trafiğini, kötü aktörler tarafından kesilmesini engelleyecek şekilde şifreleme; kimlik ve güven sağlamak için istemcilerin ve sunucuların kimliğini doğrulama; ve istemcilere erişimi denetlemek ve kimlik tabanlı izinleri uygulamak için istemcileri yetkilendirin.</span><span class="sxs-lookup"><span data-stu-id="2c640-105">Security covers three key areas: encrypting network traffic to prevent it from being intercepted by bad actors; authenticating clients and servers to establish identity and trust; and authorizing clients to control access to systems and apply permissions based on identity.</span></span>

> [!NOTE]
> <span data-ttu-id="2c640-106">**Kimlik doğrulaması** , bir istemci veya sunucu kimliğini kurmaya önem vermez.</span><span class="sxs-lookup"><span data-stu-id="2c640-106">**Authentication** is concerned with establishing the identity of a client or server.</span></span> <span data-ttu-id="2c640-107">**Yetkilendirme** , bir istemcinin bir kaynağa erişme izni olup olmadığını belirlemekten ve bir komut sormasından endişe edilir.</span><span class="sxs-lookup"><span data-stu-id="2c640-107">**Authorization** is concerned with determining whether a client has permission to access a resource or issue a command.</span></span>

<span data-ttu-id="2c640-108">Bu bölümde, ASP.NET Core için gRPC 'de kimlik doğrulama ve yetkilendirme olanakları ele alınmaktadır ve TLS şifreli bağlantıları kullanarak ağ güvenliği tartışılecektir.</span><span class="sxs-lookup"><span data-stu-id="2c640-108">This chapter will cover the facilities for authentication and authorization in gRPC for ASP.NET Core, and discuss network security using TLS encrypted connections.</span></span>

## <a name="wcf-authentication-and-authorization"></a><span data-ttu-id="2c640-109">WCF kimlik doğrulaması ve yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="2c640-109">WCF authentication and authorization</span></span>

<span data-ttu-id="2c640-110">WCF 'de, kimlik doğrulama ve yetkilendirme, kullanılan aktarımlara ve bağlamalara bağlı olarak farklı şekillerde işlenmekte.</span><span class="sxs-lookup"><span data-stu-id="2c640-110">In WCF, authentication and authorization were handled in different ways depending on the transports and bindings being used.</span></span> <span data-ttu-id="2c640-111">WCF, çeşitli WS-\* Security standartları ve IIS veya Windows sistemleri arasında NetTcp hizmetlerinde çalışan http Hizmetleri için Windows kimlik doğrulaması 'nı destekliyordu.</span><span class="sxs-lookup"><span data-stu-id="2c640-111">WCF supported various WS-\* security standards, as well as Windows authentication for HTTP services running in IIS or NetTCP services between Windows systems.</span></span>

## <a name="grpc-authentication-and-authorization"></a><span data-ttu-id="2c640-112">gRPC kimlik doğrulaması ve yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="2c640-112">gRPC authentication and authorization</span></span>

<span data-ttu-id="2c640-113">gRPC kimlik doğrulaması ve yetkilendirme iki düzeyde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2c640-113">gRPC authentication and authorization works on two levels.</span></span> <span data-ttu-id="2c640-114">Çağrı düzeyi kimlik doğrulaması/yetkilendirme genellikle, çağrı yapıldığında meta verilerde uygulanan belirteçler kullanılarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="2c640-114">Call-level authentication/authorization is usually handled using tokens that are applied in metadata when the call is made.</span></span> <span data-ttu-id="2c640-115">Kanal düzeyinde kimlik doğrulaması, bağlantı düzeyinde uygulanan bir istemci sertifikası kullanır ve kanaldaki her çağrıya otomatik olarak uygulanacak çağrı düzeyi kimlik doğrulama/yetkilendirme kimlik bilgilerini de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="2c640-115">Channel-level authentication uses a client certificate that is applied at the connection level, and can also include call-level authentication/authorization credentials to be applied to every call on the channel automatically.</span></span> <span data-ttu-id="2c640-116">Hizmetinizi güvenli hale getirmek için bu mekanizmalardan birini ya da her ikisini birden kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2c640-116">You can use either or both of these mechanisms to secure your service.</span></span>

<span data-ttu-id="2c640-117">GRPC 'nin ASP.NET Core uygulanması, standart ASP.NET Core mekanizmalarının çoğunu kullanarak kimlik doğrulaması ve yetkilendirmeyi destekler:</span><span class="sxs-lookup"><span data-stu-id="2c640-117">The ASP.NET Core implementation of gRPC supports authentication and authorization using most of the standard ASP.NET Core mechanisms:</span></span>

- <span data-ttu-id="2c640-118">Kimlik doğrulama çağrısı</span><span class="sxs-lookup"><span data-stu-id="2c640-118">Call authentication</span></span>
  - <span data-ttu-id="2c640-119">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="2c640-119">Azure Active Directory</span></span>
  - <span data-ttu-id="2c640-120">IdentityServer</span><span class="sxs-lookup"><span data-stu-id="2c640-120">IdentityServer</span></span>
  - <span data-ttu-id="2c640-121">JWT taşıyıcı belirteci</span><span class="sxs-lookup"><span data-stu-id="2c640-121">JWT Bearer Token</span></span>
  - <span data-ttu-id="2c640-122">OAuth 2,0</span><span class="sxs-lookup"><span data-stu-id="2c640-122">OAuth 2.0</span></span>
  - <span data-ttu-id="2c640-123">OpenID Connect</span><span class="sxs-lookup"><span data-stu-id="2c640-123">OpenID Connect</span></span>
  - <span data-ttu-id="2c640-124">WS-Federation</span><span class="sxs-lookup"><span data-stu-id="2c640-124">WS-Federation</span></span>
- <span data-ttu-id="2c640-125">Kanal kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="2c640-125">Channel authentication</span></span>
  - <span data-ttu-id="2c640-126">İstemci sertifikası</span><span class="sxs-lookup"><span data-stu-id="2c640-126">Client Certificate</span></span>

<span data-ttu-id="2c640-127">Çağrı kimlik doğrulama yöntemlerinin hepsi *belirteçleri*temel alır.</span><span class="sxs-lookup"><span data-stu-id="2c640-127">The call authentication methods are all based on *tokens*.</span></span> <span data-ttu-id="2c640-128">Tek gerçek fark, belirtecin oluşturulma biçimi ve ASP.NET Core hizmetindeki belirteçleri doğrulamak için kullanılan kitaplıklardır.</span><span class="sxs-lookup"><span data-stu-id="2c640-128">The only real difference is how the token is generated and the libraries that are used to validate the tokens in the ASP.NET Core service.</span></span>

<span data-ttu-id="2c640-129">Daha fazla bilgi için [Microsoft docs üzerindeki kimlik doğrulama ve yetkilendirme belgelerine](https://docs.microsoft.com/aspnet/core/grpc/authn-and-authz?view=aspnetcore-3.0)bakın.</span><span class="sxs-lookup"><span data-stu-id="2c640-129">For more information, see the [Authentication and authorization documentation on Microsoft Docs](https://docs.microsoft.com/aspnet/core/grpc/authn-and-authz?view=aspnetcore-3.0).</span></span>

> [!NOTE]
> <span data-ttu-id="2c640-130">GRPC 'yi TLS şifreli HTTP/2 bağlantısı üzerinden kullanırken, kanal düzeyinde kimlik doğrulaması kullanmasanız bile istemciler ve sunucular arasındaki tüm trafik şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="2c640-130">When using gRPC over a TLS-encrypted HTTP/2 connection, all traffic between clients and servers is encrypted, even if you don't use channel-level authentication.</span></span>

<span data-ttu-id="2c640-131">Bu bölümde, bir gRPC hizmetine çağrı kimlik bilgileri ve kanal kimlik bilgilerinin nasıl uygulanacağı ve hizmet ile kimlik doğrulaması için bir .NET Core gRPC istemcisinden kimlik bilgilerinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2c640-131">This chapter will show how to apply call credentials and channel credentials to a gRPC service, and how to use credentials from a .NET Core gRPC client to authenticate with the service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="2c640-132">[Önceki](client-libraries.md)
>[İleri](call-credentials.md)</span><span class="sxs-lookup"><span data-stu-id="2c640-132">[Previous](client-libraries.md)
[Next](call-credentials.md)</span></span>
