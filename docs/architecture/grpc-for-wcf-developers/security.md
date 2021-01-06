---
title: GRPC uygulamalarında güvenlik-WCF geliştiricileri için gRPC
description: GRPC 'de çağrı ve kanal kimlik doğrulamasına ve yetkilendirmeye genel bakış.
ms.date: 12/15/2020
ms.openlocfilehash: a5c16a4a4f7567e23bf4f9e3049fe116086daf12
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938097"
---
# <a name="security-in-grpc-applications"></a><span data-ttu-id="c8103-103">gRPC uygulamalarında güvenlik</span><span class="sxs-lookup"><span data-stu-id="c8103-103">Security in gRPC applications</span></span>

<span data-ttu-id="c8103-104">Herhangi bir gerçek Dünya senaryosunda, uygulamaların ve hizmetlerin güvenliğini sağlamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="c8103-104">In any real-world scenario, securing applications and services are essential.</span></span> <span data-ttu-id="c8103-105">Güvenlik üç temel alan içerir:</span><span class="sxs-lookup"><span data-stu-id="c8103-105">Security covers three key areas:</span></span>

* <span data-ttu-id="c8103-106">Kötü amaçlı korsanların bunu kesintiye uğramasını engellemek için ağ trafiğini şifreleme.</span><span class="sxs-lookup"><span data-stu-id="c8103-106">Encrypting network traffic to prevent malicious hackers from intercepting it.</span></span>
* <span data-ttu-id="c8103-107">Kimlik ve güven sağlamak için istemcilerin ve sunucuların kimlik doğrulamasını yapın.</span><span class="sxs-lookup"><span data-stu-id="c8103-107">Authenticating clients and servers to establish identity and trust.</span></span>
* <span data-ttu-id="c8103-108">İstemcilere erişimi denetlemek ve kimlik tabanlı izinleri uygulamak için istemcileri yetkilendirme.</span><span class="sxs-lookup"><span data-stu-id="c8103-108">Authorizing clients to control access to systems and apply permissions based on identity.</span></span>

> [!NOTE]
> <span data-ttu-id="c8103-109">*Kimlik doğrulaması* , bir istemci veya sunucu kimliğini kurmaya önem vermez.</span><span class="sxs-lookup"><span data-stu-id="c8103-109">*Authentication* is concerned with establishing the identity of a client or server.</span></span> <span data-ttu-id="c8103-110">*Yetkilendirme* , bir istemcinin bir kaynağa erişme izni olup olmadığını belirlemekten ve bir komut sormasından endişe edilir.</span><span class="sxs-lookup"><span data-stu-id="c8103-110">*Authorization* is concerned with determining whether a client has permission to access a resource or issue a command.</span></span>

<span data-ttu-id="c8103-111">Bu bölümde, ASP.NET Core için gRPC 'de kimlik doğrulama ve yetkilendirme olanakları ele alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="c8103-111">This chapter will cover the facilities for authentication and authorization in gRPC for ASP.NET Core.</span></span> <span data-ttu-id="c8103-112">Ayrıca, TLS şifreli bağlantıları aracılığıyla ağ güvenliğini de tartışır.</span><span class="sxs-lookup"><span data-stu-id="c8103-112">It will also discuss network security through TLS encrypted connections.</span></span>

## <a name="wcf-authentication-and-authorization"></a><span data-ttu-id="c8103-113">WCF kimlik doğrulaması ve yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="c8103-113">WCF authentication and authorization</span></span>

<span data-ttu-id="c8103-114">Windows Communication Foundation (WCF) ' de, kimlik doğrulama ve yetkilendirme, kullanılan aktarımlara ve bağlamalara bağlı olarak farklı yollarla işlenmekte.</span><span class="sxs-lookup"><span data-stu-id="c8103-114">In Windows Communication Foundation (WCF), authentication and authorization were handled in different ways, depending on the transports and bindings being used.</span></span> <span data-ttu-id="c8103-115">WCF, çeşitli WS- \* Security standartları destekliyordu.</span><span class="sxs-lookup"><span data-stu-id="c8103-115">WCF supported various WS-\* security standards.</span></span> <span data-ttu-id="c8103-116">Ayrıca, IIS veya Windows sistemleri arasında NetTCP hizmetlerinde çalışan HTTP Hizmetleri için Windows kimlik doğrulamasını da destekler.</span><span class="sxs-lookup"><span data-stu-id="c8103-116">It also supported Windows authentication for HTTP services running in IIS or NetTCP services between Windows systems.</span></span>

## <a name="grpc-authentication-and-authorization"></a><span data-ttu-id="c8103-117">gRPC kimlik doğrulaması ve yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="c8103-117">gRPC authentication and authorization</span></span>

<span data-ttu-id="c8103-118">gRPC kimlik doğrulaması ve yetkilendirme iki düzeyde geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="c8103-118">gRPC authentication and authorization works on two levels:</span></span>

* <span data-ttu-id="c8103-119">Çağrı düzeyi kimlik doğrulaması/yetkilendirme genellikle, çağrı yapıldığında meta verilerde uygulanan belirteçler aracılığıyla işlenir.</span><span class="sxs-lookup"><span data-stu-id="c8103-119">Call-level authentication/authorization is usually handled through tokens that are applied in metadata when the call is made.</span></span>
* <span data-ttu-id="c8103-120">Kanal düzeyinde kimlik doğrulama, bağlantı düzeyinde uygulanan bir istemci sertifikası kullanır.</span><span class="sxs-lookup"><span data-stu-id="c8103-120">Channel-level authentication uses a client certificate that's applied at the connection level.</span></span> <span data-ttu-id="c8103-121">Ayrıca, kanaldaki her çağrıya otomatik olarak uygulanacak çağrı düzeyi kimlik doğrulama/yetkilendirme kimlik bilgilerini de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="c8103-121">It can also include call-level authentication/authorization credentials to be applied to every call on the channel automatically.</span></span>

<span data-ttu-id="c8103-122">Hizmetinizin güvenliğini sağlamaya yardımcı olması için bu mekanizmalardan birini ya da her ikisini birden kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8103-122">You can use either or both of these mechanisms to help secure your service.</span></span>

<span data-ttu-id="c8103-123">GRPC 'nin ASP.NET Core uygulanması, standart ASP.NET Core mekanizmalarının çoğunda kimlik doğrulama ve yetkilendirmeyi destekler:</span><span class="sxs-lookup"><span data-stu-id="c8103-123">The ASP.NET Core implementation of gRPC supports authentication and authorization through most of the standard ASP.NET Core mechanisms:</span></span>

- <span data-ttu-id="c8103-124">Kimlik doğrulama çağrısı</span><span class="sxs-lookup"><span data-stu-id="c8103-124">Call authentication</span></span>
  - <span data-ttu-id="c8103-125">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="c8103-125">Azure Active Directory</span></span>
  - <span data-ttu-id="c8103-126">IdentityServer</span><span class="sxs-lookup"><span data-stu-id="c8103-126">IdentityServer</span></span>
  - <span data-ttu-id="c8103-127">JWT taşıyıcı belirteci</span><span class="sxs-lookup"><span data-stu-id="c8103-127">JWT Bearer Token</span></span>
  - <span data-ttu-id="c8103-128">OAuth 2.0</span><span class="sxs-lookup"><span data-stu-id="c8103-128">OAuth 2.0</span></span>
  - <span data-ttu-id="c8103-129">OpenID Connect</span><span class="sxs-lookup"><span data-stu-id="c8103-129">OpenID Connect</span></span>
  - <span data-ttu-id="c8103-130">WS-Federation</span><span class="sxs-lookup"><span data-stu-id="c8103-130">WS-Federation</span></span>
- <span data-ttu-id="c8103-131">Kanal kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="c8103-131">Channel authentication</span></span>
  - <span data-ttu-id="c8103-132">İstemci sertifikası</span><span class="sxs-lookup"><span data-stu-id="c8103-132">Client certificate</span></span>

<span data-ttu-id="c8103-133">Çağrı kimlik doğrulama yöntemlerinin hepsi *belirteçleri* temel alır.</span><span class="sxs-lookup"><span data-stu-id="c8103-133">The call authentication methods are all based on *tokens*.</span></span> <span data-ttu-id="c8103-134">Tek gerçek fark, belirteçlerin oluşturulma biçimi ve ASP.NET Core hizmetindeki belirteçleri doğrulamak için kullanılan kitaplıklardır.</span><span class="sxs-lookup"><span data-stu-id="c8103-134">The only real difference is how the tokens are generated and the libraries that are used to validate the tokens in the ASP.NET Core service.</span></span>

<span data-ttu-id="c8103-135">Daha fazla bilgi için bkz. [kimlik doğrulama ve yetkilendirme](/aspnet/core/grpc/authn-and-authz) makalesi.</span><span class="sxs-lookup"><span data-stu-id="c8103-135">For more information, see the [Authentication and authorization](/aspnet/core/grpc/authn-and-authz) article.</span></span>

> [!NOTE]
> <span data-ttu-id="c8103-136">GRPC 'yi TLS şifreli HTTP/2 bağlantısı üzerinden kullandığınızda, kanal düzeyinde kimlik doğrulaması kullanmasanız bile istemciler ve sunucular arasındaki tüm trafik şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="c8103-136">When you're using gRPC over a TLS-encrypted HTTP/2 connection, all traffic between clients and servers is encrypted, even if you don't use channel-level authentication.</span></span>

<span data-ttu-id="c8103-137">Bu bölümde, bir gRPC hizmetine çağrı kimlik bilgilerinin ve kanal kimlik bilgilerinin nasıl uygulanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c8103-137">This chapter will show how to apply call credentials and channel credentials to a gRPC service.</span></span> <span data-ttu-id="c8103-138">Ayrıca, hizmette kimlik doğrulaması yapmak için bir .NET gRPC istemcisinden kimlik bilgilerinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c8103-138">It will also show how to use credentials from a .NET gRPC client to authenticate with the service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c8103-139">[Önceki](client-libraries.md) 
> [Sonraki](call-credentials.md)</span><span class="sxs-lookup"><span data-stu-id="c8103-139">[Previous](client-libraries.md)
[Next](call-credentials.md)</span></span>
