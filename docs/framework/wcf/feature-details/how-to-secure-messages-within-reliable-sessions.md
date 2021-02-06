---
description: 'Daha fazla bilgi edinin: nasıl yapılır: güvenilir oturumlarda Iletileri güvenli hale getirme'
title: 'Nasıl yapılır: Güvenli Oturumlarla İletileri Güvenli Hale Getirme'
ms.date: 03/30/2017
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
ms.openlocfilehash: 73ca0d543edc2445dc72264e7eccf6c1eb616313
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643364"
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a><span data-ttu-id="912a4-103">Nasıl yapılır: Güvenli Oturumlarla İletileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="912a4-103">How to: Secure Messages within Reliable Sessions</span></span>

<span data-ttu-id="912a4-104">Bu konu, bu tür bir oturumu destekleyen, ancak varsayılan olarak değil, sistem tarafından belirtilen bağlamalardan birini kullanarak güvenilir bir oturumda değiştirilen iletiler için ileti düzeyi güvenliği etkinleştirmek için gereken adımları açıklar.</span><span class="sxs-lookup"><span data-stu-id="912a4-104">This topic outlines the steps required to enable message-level security for messages exchanged within a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="912a4-105">Yapılandırma dosyasında kod kullanarak güvenli, güvenilir bir oturumu imperatively veya bildirimli olarak etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="912a4-105">Enable a secure, reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="912a4-106">Bu yordam, güvenli, güvenilir oturumu etkinleştirmek için istemci ve hizmet yapılandırma dosyalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="912a4-106">This procedure uses the client and service configuration files to enable the secure, reliable session.</span></span>

<span data-ttu-id="912a4-107">Bu yordam aşağıdaki üç temel görevden oluşur:</span><span class="sxs-lookup"><span data-stu-id="912a4-107">This procedure consists of the following three key tasks:</span></span>

1. <span data-ttu-id="912a4-108">İstemci ve hizmet iletilerinin güvenilir bir oturum içinde Exchange 'e ait olduğunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="912a4-108">Specify that the client and service exchange messages within a reliable session.</span></span>

1. <span data-ttu-id="912a4-109">Güvenilir oturum içinde ileti düzeyinde güvenlik gerektir.</span><span class="sxs-lookup"><span data-stu-id="912a4-109">Require message-level security within the reliable session.</span></span>

1. <span data-ttu-id="912a4-110">İstemcinin, hizmette kimlik doğrulaması yapmak için kullanması gereken istemci kimlik bilgisi türünü belirtin.</span><span class="sxs-lookup"><span data-stu-id="912a4-110">Specify the client credential type that the client must use to be authenticated with the service.</span></span>

<span data-ttu-id="912a4-111">Uç nokta yapılandırma öğesinin adlı bir bağlama yapılandırmasına başvuran bir öznitelik içerdiği ilk görevde `bindingConfiguration` (Bu örnekte) önemlidir `MessageSecurity` .</span><span class="sxs-lookup"><span data-stu-id="912a4-111">It's important in the first task that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named (in this example) `MessageSecurity`.</span></span> <span data-ttu-id="912a4-112">[**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md)Sonra yapılandırma öğesi, `enabled` öğesinin özniteliğini olarak ayarlayarak güvenilir oturumları etkinleştirmek için bu ada başvurur [**\<reliableSession>**](/previous-versions/ms731375(v=vs.90)) `true` .</span><span class="sxs-lookup"><span data-stu-id="912a4-112">The [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md) configuration element then references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](/previous-versions/ms731375(v=vs.90)) element to `true`.</span></span> <span data-ttu-id="912a4-113">Özniteliğini olarak ayarlayarak, sıralı teslimat güveninin güvenilir bir oturum dahilinde kullanılabilir olmasını zorunlu kılabilirsiniz `ordered` `true` .</span><span class="sxs-lookup"><span data-stu-id="912a4-113">You can require that the ordered delivery assurances are available within a reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="912a4-114">Bu yapılandırma yordamının temel aldığı örnek kaynak kopyası için, bkz. [WS güvenilir oturumu](../samples/ws-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="912a4-114">For the source copy of the example on which this configuration procedure is based, see the [WS Reliable Session](../samples/ws-reliable-session.md).</span></span>

<span data-ttu-id="912a4-115">İkinci görevin temel öğeleri, `mode` **\<security>** **\<binding>** istemci ve hizmetin öğesinde bulunan öğesinin özniteliği olarak ayarlanarak gerçekleştirilir `Message` .</span><span class="sxs-lookup"><span data-stu-id="912a4-115">The essential items of the second task are accomplished by setting the `mode` attribute of the **\<security>** element contained in the **\<binding>** element of the client and service to `Message`.</span></span>

<span data-ttu-id="912a4-116">Üçüncü görevin temel öğeleri, `clientCredentialType` **\<message>** **\<security>** istemci ve hizmetin öğesinde bulunan öğesinin özniteliği ayarlanarak gerçekleştirilir `Certificate` .</span><span class="sxs-lookup"><span data-stu-id="912a4-116">The essential items of the third task are accomplished by setting the `clientCredentialType` attribute of the **\<message>** element contained in the **\<security>** element of the client and service to `Certificate`.</span></span>

> [!NOTE]
> <span data-ttu-id="912a4-117">Güvenilir oturumlarla ileti güvenliği kullanılırken, ilk hata durumunda özel durum oluşturmak yerine bir zaman aşımı gerçekleşene kadar, güvenilir mesajlaşma kimliği doğrulanmamış bir istemcinin kimliğini doğrulamaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="912a4-117">When using message security with reliable sessions, Reliable Messaging attempts to authenticate an unauthenticated client until a timeout occurs instead of throwing an exception upon first failure.</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="912a4-118">Güvenli bir oturum kullanmak için bir WSHttpBinding ile hizmeti yapılandırma</span><span class="sxs-lookup"><span data-stu-id="912a4-118">Configure the service with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="912a4-119">Bu yordam, [nasıl yapılır: güvenilir bir oturumda Ileti alışverişi konusunda](how-to-exchange-messages-within-a-reliable-session.md)açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="912a4-119">This procedure is described in [How to: Exchange Messages Within a Reliable Session](how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="912a4-120">Güvenli bir oturum kullanmak için istemciyi bir WSHttpBinding ile yapılandırma</span><span class="sxs-lookup"><span data-stu-id="912a4-120">Configure the client with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="912a4-121">Bu yordam, [nasıl yapılır: güvenilir bir oturumda Ileti alışverişi konusunda](how-to-exchange-messages-within-a-reliable-session.md)açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="912a4-121">This procedure is described in [How to: Exchange Messages Within a Reliable Session](how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a><span data-ttu-id="912a4-122">Yapılandırmada Mode ve ClientCredentialType ayarla</span><span class="sxs-lookup"><span data-stu-id="912a4-122">Set the mode and ClientCredentialType in configuration</span></span>

1. <span data-ttu-id="912a4-123">Yapılandırma dosyasının öğesine uygun bir bağlama öğesi ekleyin [**\<bindings>**](../../configure-apps/file-schema/wcf/bindings.md) .</span><span class="sxs-lookup"><span data-stu-id="912a4-123">Add an appropriate binding element to the [**\<bindings>**](../../configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="912a4-124">Aşağıdaki örnek bir öğesi ekler [**\<wsHttpBinding>**](../../configure-apps/file-schema/wcf/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="912a4-124">The following example adds a [**\<wsHttpBinding>**](../../configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>

1. <span data-ttu-id="912a4-125">Bir **\<binding>** öğesi ekleyin ve `name` özniteliğini uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="912a4-125">Add a **\<binding>** element and set its `name` attribute to an appropriate value.</span></span> <span data-ttu-id="912a4-126">Örnek, adını kullanır `MessageSecurity` .</span><span class="sxs-lookup"><span data-stu-id="912a4-126">The example uses the name `MessageSecurity`.</span></span>

1. <span data-ttu-id="912a4-127">Bir **\<security>** öğesi ekleyin ve `mode` özniteliğini olarak ayarlayın `Message` .</span><span class="sxs-lookup"><span data-stu-id="912a4-127">Add a **\<security>** element and set the `mode` attribute to `Message`.</span></span>

1. <span data-ttu-id="912a4-128">Öğesi içinde **\<security>** , bir öğesi ekleyin **\<message>** ve `clientCredentialType` özniteliğini olarak ayarlayın `Certificate` .</span><span class="sxs-lookup"><span data-stu-id="912a4-128">Within the **\<security>** element, add a **\<message>** element and set the `clientCredentialType` attribute to `Certificate`.</span></span>

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
