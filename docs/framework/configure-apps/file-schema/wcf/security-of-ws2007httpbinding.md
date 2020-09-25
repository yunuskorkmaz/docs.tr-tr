---
title: <security> / <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
ms.openlocfilehash: 48b49bf69f791f90ed5b2eea8e6d412438cd9519
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169849"
---
# <a name="security-of-ws2007httpbinding"></a><span data-ttu-id="a1d6c-102">\<security> / \<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="a1d6c-102">\<security> of \<ws2007HttpBinding></span></span>

<span data-ttu-id="a1d6c-103">Öğesiyle kullanılan güvenlik ayarlarını temsil eder [\<ws2007HttpBinding>](ws2007httpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="a1d6c-103">Represents the security settings used with the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="a1d6c-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="a1d6c-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a1d6c-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a1d6c-105">Attributes and Elements</span></span>  

 <span data-ttu-id="a1d6c-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a1d6c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a1d6c-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a1d6c-107">Attributes</span></span>  
  
|<span data-ttu-id="a1d6c-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a1d6c-108">Attribute</span></span>|<span data-ttu-id="a1d6c-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a1d6c-109">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="a1d6c-110">Seçim.</span><span class="sxs-lookup"><span data-stu-id="a1d6c-110">-   Optional.</span></span> <span data-ttu-id="a1d6c-111">Uygulanan güvenlik türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="a1d6c-111">Specifies the type of security that is applied.</span></span> <span data-ttu-id="a1d6c-112">Varsayılan değer: `Message`.</span><span class="sxs-lookup"><span data-stu-id="a1d6c-112">The default is `Message`.</span></span><br /><br /> <span data-ttu-id="a1d6c-113">Bu öznitelik türü <xref:System.ServiceModel.SecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="a1d6c-113">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="a1d6c-114">Mode özniteliği</span><span class="sxs-lookup"><span data-stu-id="a1d6c-114">Mode Attribute</span></span>  
  
|<span data-ttu-id="a1d6c-115">Değer</span><span class="sxs-lookup"><span data-stu-id="a1d6c-115">Value</span></span>|<span data-ttu-id="a1d6c-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a1d6c-116">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="a1d6c-117">Güvenlik devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="a1d6c-117">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="a1d6c-118">Güvenlik, HTTPS kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="a1d6c-118">Security is provided using HTTPS.</span></span> <span data-ttu-id="a1d6c-119">Hizmetin Güvenli Yuva Katmanı (SSL) sertifikalarıyla yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a1d6c-119">The service must be configured with Secure Sockets Layer (SSL) certificates.</span></span> <span data-ttu-id="a1d6c-120">İleti HTTPS kullanılarak tamamen güvenli hale getirilir ve hizmetin SSL sertifikası kullanılarak istemcinin kimliği doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="a1d6c-120">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="a1d6c-121">İstemci kimlik doğrulaması, `ClientCredentials` öğesinin özniteliği aracılığıyla denetlenir [\<transport>](transport-of-ws2007httpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="a1d6c-121">The client authentication is controlled through the `ClientCredentials` attribute of the [\<transport>](transport-of-ws2007httpbinding.md) element.</span></span>|  
|`Message`|<span data-ttu-id="a1d6c-122">Güvenlik, SOAP iletisi güvenliği kullanılarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="a1d6c-122">Security is provided using SOAP message security.</span></span> <span data-ttu-id="a1d6c-123">Varsayılan olarak, SOAP gövdesi şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="a1d6c-123">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="a1d6c-124">Bu mod, hizmet kimlik bilgilerinin, istemci bant dışı, kullanılacak algoritma paketini ve ileti gövdesine hangi koruma düzeyi üzerinden uygulanacağını gibi çeşitli özellikler sunar <xref:System.ServiceModel.Security.SecurityMessageProperty> .</span><span class="sxs-lookup"><span data-stu-id="a1d6c-124">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span></span> <span data-ttu-id="a1d6c-125">İstemci kimlik doğrulaması her oturum için bir kez gerçekleştirilir ve kimlik doğrulama sonuçları oturum süresince önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="a1d6c-125">Client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="a1d6c-126">Bu modda, HTTPS bütünlük, gizlilik ve sunucu kimlik doğrulaması sağlar ve SOAP iletisi güvenliği istemci kimlik doğrulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="a1d6c-126">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="a1d6c-127">Varsayılan olarak, istemci kimlik doğrulaması her oturum için bir kez gerçekleştirilir ve kimlik doğrulama sonuçları oturum süresince önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="a1d6c-127">By default, client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a1d6c-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a1d6c-128">Child Elements</span></span>  
  
|<span data-ttu-id="a1d6c-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="a1d6c-129">Element</span></span>|<span data-ttu-id="a1d6c-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a1d6c-130">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-ws2007httpbinding.md)|<span data-ttu-id="a1d6c-131">Taşıma güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a1d6c-131">Defines the transport security settings.</span></span> <span data-ttu-id="a1d6c-132">Bu öğe türüne karşılık gelir <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="a1d6c-132">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span> <span data-ttu-id="a1d6c-133">Bu ayarlar yalnızca, mod aktarım olarak ayarlandığında uygulanır.</span><span class="sxs-lookup"><span data-stu-id="a1d6c-133">These settings are applied only when the mode is set to Transport.</span></span>|  
|[\<message>](message-of-ws2007httpbinding.md)|<span data-ttu-id="a1d6c-134">İleti için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a1d6c-134">Defines the security settings for the message.</span></span> <span data-ttu-id="a1d6c-135">Bu öğe türüne karşılık gelir <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> .</span><span class="sxs-lookup"><span data-stu-id="a1d6c-135">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span> <span data-ttu-id="a1d6c-136">Bu ayarlar, mod aktarım olarak ayarlandığında uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="a1d6c-136">These settings are not applied when the mode is set to Transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a1d6c-137">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a1d6c-137">Parent Elements</span></span>  
  
|<span data-ttu-id="a1d6c-138">Öğe</span><span class="sxs-lookup"><span data-stu-id="a1d6c-138">Element</span></span>|<span data-ttu-id="a1d6c-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a1d6c-139">Description</span></span>|  
|-------------|-----------------|  
|[\<ws2007HttpBinding>](ws2007httpbinding.md)|<span data-ttu-id="a1d6c-140">HTTP taşıma uygulamaları için güvenli bağlama.</span><span class="sxs-lookup"><span data-stu-id="a1d6c-140">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1d6c-141">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a1d6c-141">Remarks</span></span>  

 <span data-ttu-id="a1d6c-142">Bu öğe, WS-\* belirtimlerini uygulayan hizmetlerle birlikte çalışabilirlik için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a1d6c-142">This element is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="a1d6c-143">Bu bağlama için taşıma güvenliği HTTP veya HTTPS üzerinden Güvenli Yuva Katmanı (SSL).</span><span class="sxs-lookup"><span data-stu-id="a1d6c-143">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1d6c-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a1d6c-144">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="a1d6c-145">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="a1d6c-145">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="a1d6c-146">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="a1d6c-146">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a1d6c-147">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a1d6c-147">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a1d6c-148">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="a1d6c-148">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
