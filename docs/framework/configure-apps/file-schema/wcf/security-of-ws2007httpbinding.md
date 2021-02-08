---
description: 'Hakkında daha fazla bilgi <security> edinin: <ws2007HttpBinding>'
title: <security> / <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
ms.openlocfilehash: ef8b82d34b318db79db061b9c01b147e619d39c4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786817"
---
# <a name="security-of-ws2007httpbinding"></a><span data-ttu-id="aaebd-103">\<security> / \<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="aaebd-103">\<security> of \<ws2007HttpBinding></span></span>

<span data-ttu-id="aaebd-104">Öğesiyle kullanılan güvenlik ayarlarını temsil eder [\<ws2007HttpBinding>](ws2007httpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="aaebd-104">Represents the security settings used with the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="aaebd-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="aaebd-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <bindings>
    <ws2007HttpBinding>
      <binding name = "String">
        <security mode="None/Message/Transport/TransportWithMessageCredential">
          <transport>
          </transport>
          <message>
          </message>
        </security>
      </binding>
    </ws2007HttpBinding>
  </bindings>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aaebd-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="aaebd-106">Attributes and Elements</span></span>  

 <span data-ttu-id="aaebd-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="aaebd-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aaebd-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="aaebd-108">Attributes</span></span>  
  
|<span data-ttu-id="aaebd-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="aaebd-109">Attribute</span></span>|<span data-ttu-id="aaebd-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aaebd-110">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="aaebd-111">Seçim.</span><span class="sxs-lookup"><span data-stu-id="aaebd-111">-   Optional.</span></span> <span data-ttu-id="aaebd-112">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="aaebd-112">Specifies the type of security that is applied.</span></span> <span data-ttu-id="aaebd-113">Varsayılan değer: `Message`.</span><span class="sxs-lookup"><span data-stu-id="aaebd-113">The default is `Message`.</span></span><br /><br /> <span data-ttu-id="aaebd-114">Bu öznitelik türü <xref:System.ServiceModel.SecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="aaebd-114">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="aaebd-115">Mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="aaebd-115">Mode Attribute</span></span>  
  
|<span data-ttu-id="aaebd-116">Değer</span><span class="sxs-lookup"><span data-stu-id="aaebd-116">Value</span></span>|<span data-ttu-id="aaebd-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aaebd-117">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="aaebd-118">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="aaebd-118">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="aaebd-119">Güvenlik, HTTPS kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="aaebd-119">Security is provided using HTTPS.</span></span> <span data-ttu-id="aaebd-120">Hizmetin Güvenli Yuva Katmanı (SSL) sertifikalarıyla yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="aaebd-120">The service must be configured with Secure Sockets Layer (SSL) certificates.</span></span> <span data-ttu-id="aaebd-121">İleti HTTPS kullanılarak tamamen güvenli hale getirilir ve hizmetin SSL sertifikası kullanılarak istemcinin kimliği doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="aaebd-121">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="aaebd-122">İstemci kimlik doğrulaması, `ClientCredentials` öğesinin özniteliği aracılığıyla denetlenir [\<transport>](transport-of-ws2007httpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="aaebd-122">The client authentication is controlled through the `ClientCredentials` attribute of the [\<transport>](transport-of-ws2007httpbinding.md) element.</span></span>|  
|`Message`|<span data-ttu-id="aaebd-123">Güvenlik, SOAP iletisi güvenliği kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="aaebd-123">Security is provided using SOAP message security.</span></span> <span data-ttu-id="aaebd-124">Varsayılan olarak, SOAP gövdesi şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="aaebd-124">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="aaebd-125">Bu mod, hizmet kimlik bilgilerinin, istemci bant dışı, kullanılacak algoritma paketini ve ileti gövdesine hangi koruma düzeyi üzerinden uygulanacağını gibi çeşitli özellikler sunar <xref:System.ServiceModel.Security.SecurityMessageProperty> .</span><span class="sxs-lookup"><span data-stu-id="aaebd-125">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span></span> <span data-ttu-id="aaebd-126">İstemci kimlik doğrulaması her oturum için bir kez gerçekleştirilir ve kimlik doğrulama sonuçları oturum süresince önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="aaebd-126">Client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="aaebd-127">Bu modda, HTTPS bütünlük, gizlilik ve sunucu kimlik doğrulaması sağlar ve SOAP iletisi güvenliği istemci kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="aaebd-127">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="aaebd-128">Varsayılan olarak, istemci kimlik doğrulaması her oturum için bir kez gerçekleştirilir ve kimlik doğrulama sonuçları oturum süresince önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="aaebd-128">By default, client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aaebd-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="aaebd-129">Child Elements</span></span>  
  
|<span data-ttu-id="aaebd-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="aaebd-130">Element</span></span>|<span data-ttu-id="aaebd-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aaebd-131">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-ws2007httpbinding.md)|<span data-ttu-id="aaebd-132">Taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="aaebd-132">Defines the transport security settings.</span></span> <span data-ttu-id="aaebd-133">Bu öğe türüne karşılık gelir <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="aaebd-133">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span> <span data-ttu-id="aaebd-134">Bu ayarlar yalnızca, mod aktarım olarak ayarlandığında uygulanır.</span><span class="sxs-lookup"><span data-stu-id="aaebd-134">These settings are applied only when the mode is set to Transport.</span></span>|  
|[\<message>](message-of-ws2007httpbinding.md)|<span data-ttu-id="aaebd-135">İleti için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="aaebd-135">Defines the security settings for the message.</span></span> <span data-ttu-id="aaebd-136">Bu öğe türüne karşılık gelir <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> .</span><span class="sxs-lookup"><span data-stu-id="aaebd-136">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span> <span data-ttu-id="aaebd-137">Bu ayarlar, mod aktarım olarak ayarlandığında uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="aaebd-137">These settings are not applied when the mode is set to Transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="aaebd-138">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="aaebd-138">Parent Elements</span></span>  
  
|<span data-ttu-id="aaebd-139">Öğe</span><span class="sxs-lookup"><span data-stu-id="aaebd-139">Element</span></span>|<span data-ttu-id="aaebd-140">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aaebd-140">Description</span></span>|  
|-------------|-----------------|  
|[\<ws2007HttpBinding>](ws2007httpbinding.md)|<span data-ttu-id="aaebd-141">HTTP taşıma uygulamaları için güvenli bağlama.</span><span class="sxs-lookup"><span data-stu-id="aaebd-141">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aaebd-142">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aaebd-142">Remarks</span></span>  

 <span data-ttu-id="aaebd-143">Bu öğe, WS-\* belirtimlerini uygulayan hizmetlerle birlikte çalışabilirlik için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="aaebd-143">This element is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="aaebd-144">Bu bağlama için taşıma güvenliği HTTP veya HTTPS üzerinden Güvenli Yuva Katmanı (SSL).</span><span class="sxs-lookup"><span data-stu-id="aaebd-144">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaebd-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aaebd-145">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="aaebd-146">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="aaebd-146">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="aaebd-147">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="aaebd-147">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="aaebd-148">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="aaebd-148">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="aaebd-149">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="aaebd-149">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
