---
title: 'Nasıl yapılır: Güvenli Oturumlarla İletileri Güvenli Hale Getirme'
ms.date: 03/30/2017
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
ms.openlocfilehash: 306d0f96b5163fe5c24d270b4b9a7c1d3f499e7e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596961"
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a><span data-ttu-id="32594-102">Nasıl yapılır: Güvenli Oturumlarla İletileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="32594-102">How to: Secure Messages within Reliable Sessions</span></span>

<span data-ttu-id="32594-103">Bu konu, bu tür bir oturumu destekleyen, ancak varsayılan olarak değil, sistem tarafından belirtilen bağlamalardan birini kullanarak güvenilir bir oturumda değiştirilen iletiler için ileti düzeyi güvenliği etkinleştirmek için gereken adımları açıklar.</span><span class="sxs-lookup"><span data-stu-id="32594-103">This topic outlines the steps required to enable message-level security for messages exchanged within a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="32594-104">Yapılandırma dosyasında kod kullanarak güvenli, güvenilir bir oturumu imperatively veya bildirimli olarak etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="32594-104">Enable a secure, reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="32594-105">Bu yordam, güvenli, güvenilir oturumu etkinleştirmek için istemci ve hizmet yapılandırma dosyalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="32594-105">This procedure uses the client and service configuration files to enable the secure, reliable session.</span></span>

<span data-ttu-id="32594-106">Bu yordam aşağıdaki üç temel görevden oluşur:</span><span class="sxs-lookup"><span data-stu-id="32594-106">This procedure consists of the following three key tasks:</span></span>

1. <span data-ttu-id="32594-107">İstemci ve hizmet iletilerinin güvenilir bir oturum içinde Exchange 'e ait olduğunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="32594-107">Specify that the client and service exchange messages within a reliable session.</span></span>

1. <span data-ttu-id="32594-108">Güvenilir oturum içinde ileti düzeyinde güvenlik gerektir.</span><span class="sxs-lookup"><span data-stu-id="32594-108">Require message-level security within the reliable session.</span></span>

1. <span data-ttu-id="32594-109">İstemcinin, hizmette kimlik doğrulaması yapmak için kullanması gereken istemci kimlik bilgisi türünü belirtin.</span><span class="sxs-lookup"><span data-stu-id="32594-109">Specify the client credential type that the client must use to be authenticated with the service.</span></span>

<span data-ttu-id="32594-110">Uç nokta yapılandırma öğesinin adlı bir bağlama yapılandırmasına başvuran bir öznitelik içerdiği ilk görevde `bindingConfiguration` (Bu örnekte) önemlidir `MessageSecurity` .</span><span class="sxs-lookup"><span data-stu-id="32594-110">It's important in the first task that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named (in this example) `MessageSecurity`.</span></span> <span data-ttu-id="32594-111">[**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md)Sonra yapılandırma öğesi, `enabled` öğesinin özniteliğini olarak ayarlayarak güvenilir oturumları etkinleştirmek için bu ada başvurur [**\<reliableSession>**](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) `true` .</span><span class="sxs-lookup"><span data-stu-id="32594-111">The [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md) configuration element then references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) element to `true`.</span></span> <span data-ttu-id="32594-112">Özniteliğini olarak ayarlayarak, sıralı teslimat güveninin güvenilir bir oturum dahilinde kullanılabilir olmasını zorunlu kılabilirsiniz `ordered` `true` .</span><span class="sxs-lookup"><span data-stu-id="32594-112">You can require that the ordered delivery assurances are available within a reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="32594-113">Bu yapılandırma yordamının temel aldığı örnek kaynak kopyası için, bkz. [WS güvenilir oturumu](../samples/ws-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="32594-113">For the source copy of the example on which this configuration procedure is based, see the [WS Reliable Session](../samples/ws-reliable-session.md).</span></span>

<span data-ttu-id="32594-114">İkinci görevin temel öğeleri, `mode` **\<security>** **\<binding>** istemci ve hizmetin öğesinde bulunan öğesinin özniteliği olarak ayarlanarak gerçekleştirilir `Message` .</span><span class="sxs-lookup"><span data-stu-id="32594-114">The essential items of the second task are accomplished by setting the `mode` attribute of the **\<security>** element contained in the **\<binding>** element of the client and service to `Message`.</span></span>

<span data-ttu-id="32594-115">Üçüncü görevin temel öğeleri, `clientCredentialType` **\<message>** **\<security>** istemci ve hizmetin öğesinde bulunan öğesinin özniteliği ayarlanarak gerçekleştirilir `Certificate` .</span><span class="sxs-lookup"><span data-stu-id="32594-115">The essential items of the third task are accomplished by setting the `clientCredentialType` attribute of the **\<message>** element contained in the **\<security>** element of the client and service to `Certificate`.</span></span>

> [!NOTE]
> <span data-ttu-id="32594-116">Güvenilir oturumlarla ileti güvenliği kullanılırken, ilk hata durumunda özel durum oluşturmak yerine bir zaman aşımı gerçekleşene kadar, güvenilir mesajlaşma kimliği doğrulanmamış bir istemcinin kimliğini doğrulamaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="32594-116">When using message security with reliable sessions, Reliable Messaging attempts to authenticate an unauthenticated client until a timeout occurs instead of throwing an exception upon first failure.</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="32594-117">Güvenli bir oturum kullanmak için bir WSHttpBinding ile hizmeti yapılandırma</span><span class="sxs-lookup"><span data-stu-id="32594-117">Configure the service with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="32594-118">Bu yordam, [nasıl yapılır: güvenilir bir oturumda Ileti alışverişi konusunda](how-to-exchange-messages-within-a-reliable-session.md)açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="32594-118">This procedure is described in [How to: Exchange Messages Within a Reliable Session](how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="32594-119">Güvenli bir oturum kullanmak için istemciyi bir WSHttpBinding ile yapılandırma</span><span class="sxs-lookup"><span data-stu-id="32594-119">Configure the client with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="32594-120">Bu yordam, [nasıl yapılır: güvenilir bir oturumda Ileti alışverişi konusunda](how-to-exchange-messages-within-a-reliable-session.md)açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="32594-120">This procedure is described in [How to: Exchange Messages Within a Reliable Session](how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a><span data-ttu-id="32594-121">Yapılandırmada Mode ve ClientCredentialType ayarla</span><span class="sxs-lookup"><span data-stu-id="32594-121">Set the mode and ClientCredentialType in configuration</span></span>

1. <span data-ttu-id="32594-122">Yapılandırma dosyasının öğesine uygun bir bağlama öğesi ekleyin [**\<bindings>**](../../configure-apps/file-schema/wcf/bindings.md) .</span><span class="sxs-lookup"><span data-stu-id="32594-122">Add an appropriate binding element to the [**\<bindings>**](../../configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="32594-123">Aşağıdaki örnek bir öğesi ekler [**\<wsHttpBinding>**](../../configure-apps/file-schema/wcf/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="32594-123">The following example adds a [**\<wsHttpBinding>**](../../configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>

1. <span data-ttu-id="32594-124">Bir **\<binding>** öğesi ekleyin ve `name` özniteliğini uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="32594-124">Add a **\<binding>** element and set its `name` attribute to an appropriate value.</span></span> <span data-ttu-id="32594-125">Örnek, adını kullanır `MessageSecurity` .</span><span class="sxs-lookup"><span data-stu-id="32594-125">The example uses the name `MessageSecurity`.</span></span>

1. <span data-ttu-id="32594-126">Bir **\<security>** öğesi ekleyin ve `mode` özniteliğini olarak ayarlayın `Message` .</span><span class="sxs-lookup"><span data-stu-id="32594-126">Add a **\<security>** element and set the `mode` attribute to `Message`.</span></span>

1. <span data-ttu-id="32594-127">Öğesi içinde **\<security>** , bir öğesi ekleyin **\<message>** ve `clientCredentialType` özniteliğini olarak ayarlayın `Certificate` .</span><span class="sxs-lookup"><span data-stu-id="32594-127">Within the **\<security>** element, add a **\<message>** element and set the `clientCredentialType` attribute to `Certificate`.</span></span>

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
