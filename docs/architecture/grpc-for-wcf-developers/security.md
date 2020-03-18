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
# <a name="security-in-grpc-applications"></a><span data-ttu-id="9816b-103">gRPC uygulamalarında güvenlik</span><span class="sxs-lookup"><span data-stu-id="9816b-103">Security in gRPC applications</span></span>

<span data-ttu-id="9816b-104">Herhangi bir gerçek dünya senaryosunda, uygulamaları ve hizmetleri güvence altına almak esastır.</span><span class="sxs-lookup"><span data-stu-id="9816b-104">In any real-world scenario, securing applications and services is essential.</span></span> <span data-ttu-id="9816b-105">Güvenlik üç önemli alanı kapsar:</span><span class="sxs-lookup"><span data-stu-id="9816b-105">Security covers three key areas:</span></span>

* <span data-ttu-id="9816b-106">Kötü amaçlı bilgisayar korsanlarının ağ trafiğini engellemesini önlemek için ağ trafiğini şifreleme.</span><span class="sxs-lookup"><span data-stu-id="9816b-106">Encrypting network traffic to prevent malicious hackers from intercepting it.</span></span>
* <span data-ttu-id="9816b-107">Kimlik ve güven oluşturmak için istemcilerin ve sunucuların kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="9816b-107">Authenticating clients and servers to establish identity and trust.</span></span>
* <span data-ttu-id="9816b-108">İstemcileri sistemlere erişimi denetleme ve kimlik durumuna göre izinleri uygulama yetkisi vermek.</span><span class="sxs-lookup"><span data-stu-id="9816b-108">Authorizing clients to control access to systems and apply permissions based on identity.</span></span>

> [!NOTE]
> <span data-ttu-id="9816b-109">*Kimlik doğrulama,* bir istemci nin veya sunucunun kimliğinin belirlenmesiyle ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="9816b-109">*Authentication* is concerned with establishing the identity of a client or server.</span></span> <span data-ttu-id="9816b-110">*Yetkilendirme,* istemcinin kaynağa erişmek veya bir komut verme izni olup olmadığını belirlemekle ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="9816b-110">*Authorization* is concerned with determining whether a client has permission to access a resource or issue a command.</span></span>

<span data-ttu-id="9816b-111">Bu bölüm, ASP.NET Core için gRPC'de kimlik doğrulama ve yetkilendirme olanaklarını kapsayacaktır.</span><span class="sxs-lookup"><span data-stu-id="9816b-111">This chapter will cover the facilities for authentication and authorization in gRPC for ASP.NET Core.</span></span> <span data-ttu-id="9816b-112">Ayrıca TLS şifreli bağlantılar üzerinden ağ güvenliği tartışacak.</span><span class="sxs-lookup"><span data-stu-id="9816b-112">It will also discuss network security through TLS encrypted connections.</span></span>

## <a name="wcf-authentication-and-authorization"></a><span data-ttu-id="9816b-113">WCF kimlik doğrulaması ve yetkilendirmesi</span><span class="sxs-lookup"><span data-stu-id="9816b-113">WCF authentication and authorization</span></span>

<span data-ttu-id="9816b-114">Windows Communication Foundation'da (WCF) kimlik doğrulama ve yetkilendirme, kullanılan taşımalara ve bağlamalara bağlı olarak farklı şekillerde ele alındı.</span><span class="sxs-lookup"><span data-stu-id="9816b-114">In Windows Communication Foundation (WCF), authentication and authorization were handled in different ways, depending on the transports and bindings being used.</span></span> <span data-ttu-id="9816b-115">WCF çeşitli WS\* güvenlik standartlarını desteklemiştir.</span><span class="sxs-lookup"><span data-stu-id="9816b-115">WCF supported various WS-\* security standards.</span></span> <span data-ttu-id="9816b-116">Ayrıca, Windows sistemleri arasında IIS veya NetTCP hizmetlerinde çalışan HTTP hizmetleri için Windows kimlik doğrulamasını da desteklemektedir.</span><span class="sxs-lookup"><span data-stu-id="9816b-116">It also supported Windows authentication for HTTP services running in IIS or NetTCP services between Windows systems.</span></span>

## <a name="grpc-authentication-and-authorization"></a><span data-ttu-id="9816b-117">gRPC kimlik doğrulama ve yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="9816b-117">gRPC authentication and authorization</span></span>

<span data-ttu-id="9816b-118">gRPC kimlik doğrulama ve yetkilendirme iki düzeyde çalışır:</span><span class="sxs-lookup"><span data-stu-id="9816b-118">gRPC authentication and authorization works on two levels:</span></span>

* <span data-ttu-id="9816b-119">Çağrı düzeyinde kimlik doğrulama/yetkilendirme genellikle arama yapıldığında meta verilerde uygulanan belirteçler aracılığıyla işlenir.</span><span class="sxs-lookup"><span data-stu-id="9816b-119">Call-level authentication/authorization is usually handled through tokens that are applied in metadata when the call is made.</span></span>
* <span data-ttu-id="9816b-120">Kanal düzeyinde kimlik doğrulaması, bağlantı düzeyinde uygulanan bir istemci sertifikası kullanır.</span><span class="sxs-lookup"><span data-stu-id="9816b-120">Channel-level authentication uses a client certificate that's applied at the connection level.</span></span> <span data-ttu-id="9816b-121">Ayrıca, kanaldaki her çağrıya otomatik olarak uygulanacak çağrı düzeyinde kimlik doğrulama/yetkilendirme kimlik bilgilerini de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="9816b-121">It can also include call-level authentication/authorization credentials to be applied to every call on the channel automatically.</span></span>

<span data-ttu-id="9816b-122">Hizmetinizin güvenliğini sağlamak için bu mekanizmalardan birini veya her ikisini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9816b-122">You can use either or both of these mechanisms to help secure your service.</span></span>

<span data-ttu-id="9816b-123">gRPC'nin ASP.NET Core uygulaması, standart ASP.NET Çekirdek mekanizmalarının çoğu aracılığıyla kimlik doğrulamave yetkilendirmeyi destekler:</span><span class="sxs-lookup"><span data-stu-id="9816b-123">The ASP.NET Core implementation of gRPC supports authentication and authorization through most of the standard ASP.NET Core mechanisms:</span></span>

- <span data-ttu-id="9816b-124">Arama kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="9816b-124">Call authentication</span></span>
  - <span data-ttu-id="9816b-125">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="9816b-125">Azure Active Directory</span></span>
  - <span data-ttu-id="9816b-126">IdentityServer</span><span class="sxs-lookup"><span data-stu-id="9816b-126">IdentityServer</span></span>
  - <span data-ttu-id="9816b-127">JWT Taşıyıcı Belirteci</span><span class="sxs-lookup"><span data-stu-id="9816b-127">JWT Bearer Token</span></span>
  - <span data-ttu-id="9816b-128">OAuth 2.0</span><span class="sxs-lookup"><span data-stu-id="9816b-128">OAuth 2.0</span></span>
  - <span data-ttu-id="9816b-129">OpenID Connect</span><span class="sxs-lookup"><span data-stu-id="9816b-129">OpenID Connect</span></span>
  - <span data-ttu-id="9816b-130">WS-Federation</span><span class="sxs-lookup"><span data-stu-id="9816b-130">WS-Federation</span></span>
- <span data-ttu-id="9816b-131">Kanal kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="9816b-131">Channel authentication</span></span>
  - <span data-ttu-id="9816b-132">İstemci sertifikası</span><span class="sxs-lookup"><span data-stu-id="9816b-132">Client certificate</span></span>

<span data-ttu-id="9816b-133">Arama kimlik doğrulama yöntemlerinin tümü *belirteçlere*dayanır.</span><span class="sxs-lookup"><span data-stu-id="9816b-133">The call authentication methods are all based on *tokens*.</span></span> <span data-ttu-id="9816b-134">Tek gerçek fark, belirteçlerin nasıl oluşturulduğu ve ASP.NET Core hizmetindeki belirteçleri doğrulamak için kullanılan kitaplıklardır.</span><span class="sxs-lookup"><span data-stu-id="9816b-134">The only real difference is how the tokens are generated and the libraries that are used to validate the tokens in the ASP.NET Core service.</span></span>

<span data-ttu-id="9816b-135">Daha fazla bilgi için [Kimlik Doğrulama ve yetkilendirme](/aspnet/core/grpc/authn-and-authz) makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="9816b-135">For more information, see the [Authentication and authorization](/aspnet/core/grpc/authn-and-authz) article.</span></span>

> [!NOTE]
> <span data-ttu-id="9816b-136">TLS şifreli http/2 bağlantısı üzerinden gRPC kullanıyorsanız, kanal düzeyinde kimlik doğrulama kullanmasanız bile istemciler ve sunucular arasındaki tüm trafik şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="9816b-136">When you're using gRPC over a TLS-encrypted HTTP/2 connection, all traffic between clients and servers is encrypted, even if you don't use channel-level authentication.</span></span>

<span data-ttu-id="9816b-137">Bu bölümde, bir gRPC hizmetine çağrı kimlik bilgileri ve kanal kimlik bilgileri nasıl uygulanacağı gösterecektir.</span><span class="sxs-lookup"><span data-stu-id="9816b-137">This chapter will show how to apply call credentials and channel credentials to a gRPC service.</span></span> <span data-ttu-id="9816b-138">Ayrıca, hizmetle ilgili kimlik doğrulamaiçin bir .NET Core gRPC istemcisinden kimlik bilgilerinin nasıl kullanılacağını da gösterir.</span><span class="sxs-lookup"><span data-stu-id="9816b-138">It will also show how to use credentials from a .NET Core gRPC client to authenticate with the service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="9816b-139">[Önceki](client-libraries.md)
>[Sonraki](call-credentials.md)</span><span class="sxs-lookup"><span data-stu-id="9816b-139">[Previous](client-libraries.md)
[Next](call-credentials.md)</span></span>
