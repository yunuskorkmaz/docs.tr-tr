---
title: Örnekleri - WCF hizmetleri
ms.date: 03/30/2017
ms.assetid: 462a2218-f8c6-4fb7-95bc-64765459c429
ms.openlocfilehash: 4531e72711d17c57bb4e365b458f0b35d6b42577
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65637593"
---
# <a name="services"></a><span data-ttu-id="40e37-102">Hizmetler</span><span class="sxs-lookup"><span data-stu-id="40e37-102">Services</span></span>

<span data-ttu-id="40e37-103">Bu bölüm, Windows Communication Foundation (WCF) hizmetlerini gösteren örnekler içerir.</span><span class="sxs-lookup"><span data-stu-id="40e37-103">This section contains samples that demonstrate Windows Communication Foundation (WCF) services.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="40e37-104">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="40e37-104">In this section</span></span>

- <span data-ttu-id="40e37-105">[Barındırma](../../../../docs/framework/wcf/feature-details/hosting.md)\\</span><span class="sxs-lookup"><span data-stu-id="40e37-105">[Hosting](../../../../docs/framework/wcf/feature-details/hosting.md)\\</span></span>
<span data-ttu-id="40e37-106">Barındırma WCF hizmetleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="40e37-106">Demonstrates hosting WCF services.</span></span>

- <span data-ttu-id="40e37-107">[Hizmet birlikte çalışabilirliği](service-interoperability.md)\\</span><span class="sxs-lookup"><span data-stu-id="40e37-107">[Service Interoperability](service-interoperability.md)\\</span></span>
<span data-ttu-id="40e37-108">WCF ve diğer hizmet teknolojiler arasındaki etkileşim gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="40e37-108">Demonstrates interaction between WCF and other service technologies.</span></span>

- <span data-ttu-id="40e37-109">[Davranışlar](behaviors.md)\\</span><span class="sxs-lookup"><span data-stu-id="40e37-109">[Behaviors](behaviors.md)\\</span></span>
<span data-ttu-id="40e37-110">WCF hizmet davranışları gösterir.</span><span class="sxs-lookup"><span data-stu-id="40e37-110">Demonstrates WCF service behaviors.</span></span>

- <span data-ttu-id="40e37-111">[Hizmet güvenliği](service-security.md)\\</span><span class="sxs-lookup"><span data-stu-id="40e37-111">[Service Security](service-security.md)\\</span></span>
<span data-ttu-id="40e37-112">WCF Hizmeti Güvenlik gösterir.</span><span class="sxs-lookup"><span data-stu-id="40e37-112">Demonstrates WCF service security.</span></span>

- <span data-ttu-id="40e37-113">[WCF hizmetleri için Basitleştirilmiş yapılandırma](simplified-configuration-for-wcf-services.md)\\</span><span class="sxs-lookup"><span data-stu-id="40e37-113">[Simplified Configuration for WCF Services](simplified-configuration-for-wcf-services.md)\\</span></span>
<span data-ttu-id="40e37-114">Uygulama ve tipik hizmeti ve WCF kullanarak istemci yapılandırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="40e37-114">Demonstrates how to implement and configure a typical service and client using WCF.</span></span>

- <span data-ttu-id="40e37-115">[Standart uç noktaları kullanma](usage-of-standard-endpoints.md)\\</span><span class="sxs-lookup"><span data-stu-id="40e37-115">[Usage of Standard Endoints](usage-of-standard-endpoints.md)\\</span></span>
<span data-ttu-id="40e37-116">Standart uç noktaları hizmet yapılandırma dosyalarında nasıl yapılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="40e37-116">Demonstrates how to use standard endpoints in service configuration files.</span></span>

- <span data-ttu-id="40e37-117">[Genişletilmiş Koruma İlkesi](extended-protection-policy.md)\\</span><span class="sxs-lookup"><span data-stu-id="40e37-117">[Extended Protection Policy](extended-protection-policy.md)\\</span></span>
<span data-ttu-id="40e37-118">Genişletilmiş koruma, ADAM-de-adam (MITM) saldırılarına karşı korumaya yönelik güvenlik girişimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="40e37-118">Demonstrates Extended Protection, a security initiative for protecting against man-in-the-middle (MITM) attacks.</span></span>

- <span data-ttu-id="40e37-119">[Yapılandırma kanal fabrikası](configuration-channel-factory.md)\\</span><span class="sxs-lookup"><span data-stu-id="40e37-119">[Configuration Channel Factory](configuration-channel-factory.md)\\</span></span>
<span data-ttu-id="40e37-120">Kullanımını gösteren <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span><span class="sxs-lookup"><span data-stu-id="40e37-120">Demonstrates the usage of the <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span></span>

- <span data-ttu-id="40e37-121">[Adresleme](addressing.md)\\</span><span class="sxs-lookup"><span data-stu-id="40e37-121">[Addressing](addressing.md)\\</span></span>
<span data-ttu-id="40e37-122">Çeşitli yönleri ve uç nokta adresleri özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="40e37-122">Demonstrates various aspects and features of endpoint addresses.</span></span>

- <span data-ttu-id="40e37-123">[Kesinliği](imperative.md)\\</span><span class="sxs-lookup"><span data-stu-id="40e37-123">[Imperative](imperative.md)\\</span></span>
<span data-ttu-id="40e37-124">Nasıl tanımlanacağını gösterir bir <xref:System.ServiceModel.WSHttpBinding> tanımlamak yerine kod kullanarak bir hizmet için `wsHttpBinding` yapılandırmasında bağlama.</span><span class="sxs-lookup"><span data-stu-id="40e37-124">Demonstrates how to define a <xref:System.ServiceModel.WSHttpBinding> for a service using code, instead of defining the `wsHttpBinding` binding in configuration.</span></span>

- <span data-ttu-id="40e37-125">[Birden fazla anlaşma](multiple-contracts.md)\\</span><span class="sxs-lookup"><span data-stu-id="40e37-125">[Multiple Contracts](multiple-contracts.md)\\</span></span>
<span data-ttu-id="40e37-126">Bir hizmet birden fazla sözleşme gerçekleştirme ve her uygulanan sözleşmelerin ile iletişim kurmak için uç noktaları yapılandırmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="40e37-126">Demonstrates how to implement more than one contract on a service and how to configure endpoints for communicating with each of the implemented contracts.</span></span>

- <span data-ttu-id="40e37-127">[Birden fazla uç noktası](multiple-endpoints.md)\\</span><span class="sxs-lookup"><span data-stu-id="40e37-127">[Multiple Endpoints](multiple-endpoints.md)\\</span></span>
<span data-ttu-id="40e37-128">Bir hizmet birden fazla uç nokta yapılandırma ve bir istemciden alınan her bir uç noktası ile iletişim kurmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="40e37-128">Demonstrates how to configure multiple endpoints on a service and how to communicate with each endpoint from a client.</span></span>

- <span data-ttu-id="40e37-129">[Tek listenuri'de birden fazla uç noktası](multiple-endpoints-at-a-single-listenuri.md)\\</span><span class="sxs-lookup"><span data-stu-id="40e37-129">[Multiple Endpoints at a Single ListenUri](multiple-endpoints-at-a-single-listenuri.md)\\</span></span>
<span data-ttu-id="40e37-130">Birden çok uç tek bir noktada barındıran bir hizmeti gösterir `ListenUri`.</span><span class="sxs-lookup"><span data-stu-id="40e37-130">Demonstrates a service that hosts multiple endpoints at a single `ListenUri`.</span></span>

- <span data-ttu-id="40e37-131">[OperationContextScope, bozuk](operationcontextscope.md)\\</span><span class="sxs-lookup"><span data-stu-id="40e37-131">[OperationContextScope](operationcontextscope.md)\\</span></span>
<span data-ttu-id="40e37-132">Üst bilgileri kullanarak bir WCF arama hakkında ek bilgi gönderme işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="40e37-132">Demonstrates how to send extra information on a WCF call using headers.</span></span>

- <span data-ttu-id="40e37-133">[Hizmet açıklaması](service-description.md)\\</span><span class="sxs-lookup"><span data-stu-id="40e37-133">[Service Description](service-description.md)\\</span></span>
<span data-ttu-id="40e37-134">Bir hizmet, hizmet açıklaması bilgilerini, çalışma zamanında nasıl alabileceğiniz gösterilir.</span><span class="sxs-lookup"><span data-stu-id="40e37-134">Demonstrates how a service can retrieve its service description information at runtime.</span></span>

- <span data-ttu-id="40e37-135">[ConcurrencyMode.Reentrant](concurrencymode-reentrant.md)\\</span><span class="sxs-lookup"><span data-stu-id="40e37-135">[ConcurrencyMode.Reentrant](concurrencymode-reentrant.md)\\</span></span>
<span data-ttu-id="40e37-136">Yeniden girilen eşzamanlılık modu bir hizmet uygulamasına nasıl yapılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="40e37-136">Demonstrates how to use the Reentrant concurrency mode on a service implementation.</span></span>
