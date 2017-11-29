---
title: "Nasıl yapılır: Güvenli Oturumlarla İletileri Güvenli Hale Getirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 3f27b1a4de2019660e0facb081300a79eae65b99
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a><span data-ttu-id="b7f16-102">Nasıl yapılır: Güvenli Oturumlarla İletileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="b7f16-102">How to: Secure Messages within Reliable Sessions</span></span>

<span data-ttu-id="b7f16-103">Bu konuda bu tür bir oturum desteği sistem tarafından sağlanan bağlamalar, ancak varsayılan kullanarak güvenilir bir oturumu içinde değiştirilen iletileri için ileti düzeyi güvenlik etkinleştirmek için gereken adımlar açıklanır.</span><span class="sxs-lookup"><span data-stu-id="b7f16-103">This topic outlines the steps required to enable message-level security for messages exchanged within a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="b7f16-104">Güvenli, güvenilir oturum kodu kullanarak imperatively ya da bildirimli olarak yapılandırma dosyasında etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="b7f16-104">Enable a secure, reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="b7f16-105">Bu yordam, güvenli, güvenilir oturum etkinleştirmek için istemci ve hizmet yapılandırma dosyalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="b7f16-105">This procedure uses the client and service configuration files to enable the secure, reliable session.</span></span>

<span data-ttu-id="b7f16-106">Bu yordam, aşağıdaki üç anahtar görevleri oluşur:</span><span class="sxs-lookup"><span data-stu-id="b7f16-106">This procedure consists of the following three key tasks:</span></span>

1. <span data-ttu-id="b7f16-107">İstemci ve hizmet iletileri güvenilir oturum içinde exchange belirtin.</span><span class="sxs-lookup"><span data-stu-id="b7f16-107">Specify that the client and service exchange messages within a reliable session.</span></span>

1. <span data-ttu-id="b7f16-108">İleti düzeyi güvenlik güvenilir oturum içinde gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b7f16-108">Require message-level security within the reliable session.</span></span>

1. <span data-ttu-id="b7f16-109">İstemci hizmetiyle kimlik doğrulaması için kullanması gereken istemci kimlik bilgisi türü belirtin.</span><span class="sxs-lookup"><span data-stu-id="b7f16-109">Specify the client credential type that the client must use to be authenticated with the service.</span></span>

<span data-ttu-id="b7f16-110">Uç nokta yapılandırma öğesi içerir ilk görevde önemli bir `bindingConfiguration` (Bu örnekte) adlı bir bağlama yapılandırması başvuran özniteliği `MessageSecurity`.</span><span class="sxs-lookup"><span data-stu-id="b7f16-110">It's important in the first task that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named (in this example) `MessageSecurity`.</span></span> <span data-ttu-id="b7f16-111">[  **\<Bağlama >** ](../../../../docs/framework/misc/binding.md) yapılandırma öğesi sonra ayarlayarak güvenilir oturumlar etkinleştirmek için bu ad başvuran `enabled` özniteliği [  **\<reliableSession >** ](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) öğesine `true`.</span><span class="sxs-lookup"><span data-stu-id="b7f16-111">The [**\<binding>**](../../../../docs/framework/misc/binding.md) configuration element then references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) element to `true`.</span></span> <span data-ttu-id="b7f16-112">Sıralı teslim Güvenceleri güvenilir oturum içinde ayarlayarak kullanılabilir olmasını gerektiren `ordered` özniteliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="b7f16-112">You can require that the ordered delivery assurances are available within a reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="b7f16-113">Bu yapılandırma yordamı temel örnek kaynak kopyası için bkz: [WS güvenilir oturum](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="b7f16-113">For the source copy of the example on which this configuration procedure is based, see the [WS Reliable Session](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span></span>

<span data-ttu-id="b7f16-114">İkinci görev temel öğeler ayarlayarak yapılır `mode` özniteliği  **\<Güvenlik >** öğesi içinde yer alan  **\<bağlama >** öğesi, istemci ve hizmet için `Message`.</span><span class="sxs-lookup"><span data-stu-id="b7f16-114">The essential items of the second task are accomplished by setting the `mode` attribute of the **\<security>** element contained in the **\<binding>** element of the client and service to `Message`.</span></span>

<span data-ttu-id="b7f16-115">Üçüncü görev temel öğeler ayarlayarak yapılır `clientCredentialType` özniteliği  **\<ileti >** öğesi içinde yer alan  **\<Güvenlik >** öğesi, istemci ve hizmet için `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="b7f16-115">The essential items of the third task are accomplished by setting the `clientCredentialType` attribute of the **\<message>** element contained in the **\<security>** element of the client and service to `Certificate`.</span></span>

> [!NOTE]
> <span data-ttu-id="b7f16-116">İleti güvenliği ile güvenilir oturumlar kullanırken, ilk başarısızlık durumunda bir özel durum atma yerine bir zaman aşımı gerçekleşene kadar kimliği doğrulanmamış bir istemci kimlik doğrulaması güvenilir Mesajlaşma çalışır.</span><span class="sxs-lookup"><span data-stu-id="b7f16-116">When using message security with reliable sessions, Reliable Messaging attempts to authenticate an unauthenticated client until a timeout occurs instead of throwing an exception upon first failure.</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="b7f16-117">Güvenilir oturum kullanmak için bir WSHttpBinding hizmetini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b7f16-117">Configure the service with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="b7f16-118">Bu yordamda açıklanan [nasıl yapılır: Exchange iletileri içinde bir güvenilir oturum](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="b7f16-118">This procedure is described in [How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="b7f16-119">Güvenilir oturum kullanmak için bir WSHttpBinding istemciyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b7f16-119">Configure the client with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="b7f16-120">Bu yordamda açıklanan [nasıl yapılır: Exchange iletileri içinde bir güvenilir oturum](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="b7f16-120">This procedure is described in [How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a><span data-ttu-id="b7f16-121">Mod ve ClientCredentialType yapılandırmasında ayarlayın</span><span class="sxs-lookup"><span data-stu-id="b7f16-121">Set the mode and ClientCredentialType in configuration</span></span>

1. <span data-ttu-id="b7f16-122">Bir uygun bağlama öğesi ekleme [  **\<bağlamaları >** ](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) yapılandırma dosyası öğesi.</span><span class="sxs-lookup"><span data-stu-id="b7f16-122">Add an appropriate binding element to the [**\<bindings>**](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="b7f16-123">Aşağıdaki örnek, bir [  **\<wsHttpBinding >** ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="b7f16-123">The following example adds a [**\<wsHttpBinding>**](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>

1. <span data-ttu-id="b7f16-124">Ekleme bir  **\<bağlama >** öğesi ve kümesi kendi `name` öznitelik için uygun bir değer.</span><span class="sxs-lookup"><span data-stu-id="b7f16-124">Add a **\<binding>** element and set its `name` attribute to an appropriate value.</span></span> <span data-ttu-id="b7f16-125">Örnek adı kullanır `MessageSecurity`.</span><span class="sxs-lookup"><span data-stu-id="b7f16-125">The example uses the name `MessageSecurity`.</span></span>

1. <span data-ttu-id="b7f16-126">Ekleme bir  **\<Güvenlik >** öğesi ve kümesi `mode` özniteliğini `Message`.</span><span class="sxs-lookup"><span data-stu-id="b7f16-126">Add a **\<security>** element and set the `mode` attribute to `Message`.</span></span>

1. <span data-ttu-id="b7f16-127">İçinde  **\<Güvenlik >** öğesi ekleme bir  **\<ileti >** öğesi ve kümesi `clientCredentialType` özniteliğini `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="b7f16-127">Within the **\<security>** element, add a **\<message>** element and set the `clientCredentialType` attribute to `Certificate`.</span></span>

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
