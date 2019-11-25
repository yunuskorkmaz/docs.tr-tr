---
title: 'Nasıl yapılır: Güvenli Oturumlarla İletileri Güvenli Hale Getirme'
ms.date: 03/30/2017
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
ms.openlocfilehash: edff27fe9649387c1922c34e72ef59d615e52b90
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141670"
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a><span data-ttu-id="1773b-102">Nasıl yapılır: Güvenli Oturumlarla İletileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="1773b-102">How to: Secure Messages within Reliable Sessions</span></span>

<span data-ttu-id="1773b-103">Bu konu, bu tür bir oturumu destekleyen, ancak varsayılan olarak değil, sistem tarafından belirtilen bağlamalardan birini kullanarak güvenilir bir oturumda değiştirilen iletiler için ileti düzeyi güvenliği etkinleştirmek için gereken adımları açıklar.</span><span class="sxs-lookup"><span data-stu-id="1773b-103">This topic outlines the steps required to enable message-level security for messages exchanged within a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="1773b-104">Yapılandırma dosyasında kod kullanarak güvenli, güvenilir bir oturumu imperatively veya bildirimli olarak etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="1773b-104">Enable a secure, reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="1773b-105">Bu yordam, güvenli, güvenilir oturumu etkinleştirmek için istemci ve hizmet yapılandırma dosyalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="1773b-105">This procedure uses the client and service configuration files to enable the secure, reliable session.</span></span>

<span data-ttu-id="1773b-106">Bu yordam aşağıdaki üç temel görevden oluşur:</span><span class="sxs-lookup"><span data-stu-id="1773b-106">This procedure consists of the following three key tasks:</span></span>

1. <span data-ttu-id="1773b-107">İstemci ve hizmet iletilerinin güvenilir bir oturum içinde Exchange 'e ait olduğunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="1773b-107">Specify that the client and service exchange messages within a reliable session.</span></span>

1. <span data-ttu-id="1773b-108">Güvenilir oturum içinde ileti düzeyinde güvenlik gerektir.</span><span class="sxs-lookup"><span data-stu-id="1773b-108">Require message-level security within the reliable session.</span></span>

1. <span data-ttu-id="1773b-109">İstemcinin, hizmette kimlik doğrulaması yapmak için kullanması gereken istemci kimlik bilgisi türünü belirtin.</span><span class="sxs-lookup"><span data-stu-id="1773b-109">Specify the client credential type that the client must use to be authenticated with the service.</span></span>

<span data-ttu-id="1773b-110">Uç nokta yapılandırma öğesinin, adlı bir bağlama yapılandırmasına (Bu örnekte `MessageSecurity`) başvuran bir `bindingConfiguration` özniteliği içerdiği ilk görevde önemlidir.</span><span class="sxs-lookup"><span data-stu-id="1773b-110">It's important in the first task that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named (in this example) `MessageSecurity`.</span></span> <span data-ttu-id="1773b-111">[ **\<bağlama >** ](../../configure-apps/file-schema/wcf/bindings.md) yapılandırma öğesi, [ **\<reliablesession >** ](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) öğesinin `enabled` özniteliğini `true`olarak ayarlayarak güvenilir oturumları etkinleştirmek için bu ada başvurur.</span><span class="sxs-lookup"><span data-stu-id="1773b-111">The [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md) configuration element then references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) element to `true`.</span></span> <span data-ttu-id="1773b-112">`ordered` özniteliğini `true`olarak ayarlayarak, sıralı teslimat güvenlerini güvenilir bir oturum dahilinde kullanılabilir olmasını zorunlu kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1773b-112">You can require that the ordered delivery assurances are available within a reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="1773b-113">Bu yapılandırma yordamının temel aldığı örnek kaynak kopyası için, bkz. [WS güvenilir oturumu](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="1773b-113">For the source copy of the example on which this configuration procedure is based, see the [WS Reliable Session](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span></span>

<span data-ttu-id="1773b-114">İkinci görevin temel öğeleri, istemci ve hizmetin **\<binding >** öğesinde bulunan **\<security >** öğesinin `mode` özniteliği `Message`' a ayarlanarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1773b-114">The essential items of the second task are accomplished by setting the `mode` attribute of the **\<security>** element contained in the **\<binding>** element of the client and service to `Message`.</span></span>

<span data-ttu-id="1773b-115">Üçüncü görevin temel öğeleri, istemci ve hizmetin **\<güvenlik >** öğesinde bulunan **\<message >** öğesinin `clientCredentialType` özniteliği `Certificate`olarak ayarlanarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1773b-115">The essential items of the third task are accomplished by setting the `clientCredentialType` attribute of the **\<message>** element contained in the **\<security>** element of the client and service to `Certificate`.</span></span>

> [!NOTE]
> <span data-ttu-id="1773b-116">Güvenilir oturumlarla ileti güvenliği kullanılırken, ilk hata durumunda özel durum oluşturmak yerine bir zaman aşımı gerçekleşene kadar, güvenilir mesajlaşma kimliği doğrulanmamış bir istemcinin kimliğini doğrulamaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="1773b-116">When using message security with reliable sessions, Reliable Messaging attempts to authenticate an unauthenticated client until a timeout occurs instead of throwing an exception upon first failure.</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="1773b-117">Güvenli bir oturum kullanmak için bir WSHttpBinding ile hizmeti yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1773b-117">Configure the service with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="1773b-118">Bu yordam, [nasıl yapılır: güvenilir bir oturumda Ileti alışverişi konusunda](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md)açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1773b-118">This procedure is described in [How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="1773b-119">Güvenli bir oturum kullanmak için istemciyi bir WSHttpBinding ile yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1773b-119">Configure the client with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="1773b-120">Bu yordam, [nasıl yapılır: güvenilir bir oturumda Ileti alışverişi konusunda](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md)açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1773b-120">This procedure is described in [How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a><span data-ttu-id="1773b-121">Yapılandırmada Mode ve ClientCredentialType ayarla</span><span class="sxs-lookup"><span data-stu-id="1773b-121">Set the mode and ClientCredentialType in configuration</span></span>

1. <span data-ttu-id="1773b-122">Yapılandırma dosyasının [ **\<bindings >** ](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) öğesine uygun bir bağlama öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1773b-122">Add an appropriate binding element to the [**\<bindings>**](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="1773b-123">Aşağıdaki örnek [ **\<wsHttpBinding >** ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) öğesi ekler.</span><span class="sxs-lookup"><span data-stu-id="1773b-123">The following example adds a [**\<wsHttpBinding>**](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>

1. <span data-ttu-id="1773b-124">**\<bağlama >** öğesi ekleyin ve `name` özniteliğini uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1773b-124">Add a **\<binding>** element and set its `name` attribute to an appropriate value.</span></span> <span data-ttu-id="1773b-125">Örnek, `MessageSecurity`adını kullanır.</span><span class="sxs-lookup"><span data-stu-id="1773b-125">The example uses the name `MessageSecurity`.</span></span>

1. <span data-ttu-id="1773b-126">\<bir **güvenlik >** öğesi ekleyin ve `mode` özniteliğini `Message`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1773b-126">Add a **\<security>** element and set the `mode` attribute to `Message`.</span></span>

1. <span data-ttu-id="1773b-127">**\<security >** öğesi içinde, bir **\<ileti >** öğesi ekleyin ve `clientCredentialType` özniteliğini `Certificate`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1773b-127">Within the **\<security>** element, add a **\<message>** element and set the `clientCredentialType` attribute to `Certificate`.</span></span>

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
