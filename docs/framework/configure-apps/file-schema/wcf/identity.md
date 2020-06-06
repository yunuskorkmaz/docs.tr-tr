---
title: <identity>
ms.date: 03/30/2017
ms.assetid: c1d2ae56-e231-4a07-9c3f-9f13381dc0d8
ms.openlocfilehash: 15c9e38a141fc294c47863b1a932711444ac079a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855144"
---
# \<identity>
<span data-ttu-id="5eefd-101">Identity öğesi, bir istemci geliştiricisinin, hizmetin beklenen kimliği olan tasarım zamanında belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="5eefd-101">The identity element allows a client developer to specify at design time the expected identity of the service.</span></span> <span data-ttu-id="5eefd-102">İstemci ve hizmet arasındaki el sıkışma işleminde, Windows Communication Foundation (WCF) altyapısı, beklenen hizmetin kimliğinin bu öğenin değerleriyle eşleştiğinden emin olur ve bu nedenle kimlik doğrulaması yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="5eefd-102">In the handshake process between the client and service, the Windows Communication Foundation (WCF) infrastructure will ensure that the identity of the expected service matches the values of this element, and thus can be authenticated.</span></span> <span data-ttu-id="5eefd-103">Daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="5eefd-103">For more information, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<identity>**  
  
## <a name="syntax"></a><span data-ttu-id="5eefd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5eefd-104">Syntax</span></span>  
  
```xml  
<identity>
  <certificate encodedValue="String" />
  <certificateReference findValue="String"
                        isChainIncluded="Boolean"
                        storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                        storeLocation="LocalMachine/CurrentUser"
                        X509FindType="Enumeration" />
  <dns value="String" />
  <rsa value="String" />
  <servicePrincipalName value="String" />
  <userPrincipalName value="String" />
</identity>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5eefd-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5eefd-105">Attributes and Elements</span></span>  
 <span data-ttu-id="5eefd-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5eefd-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5eefd-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5eefd-107">Attributes</span></span>  
 <span data-ttu-id="5eefd-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="5eefd-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5eefd-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5eefd-109">Child Elements</span></span>  
  
|<span data-ttu-id="5eefd-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="5eefd-110">Element</span></span>|<span data-ttu-id="5eefd-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5eefd-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5eefd-112">sertifika</span><span class="sxs-lookup"><span data-stu-id="5eefd-112">certificate</span></span>|<span data-ttu-id="5eefd-113">X. 509.440 sertifikasının ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5eefd-113">Specifies settings of an X.509 certificate.</span></span> <span data-ttu-id="5eefd-114">Bu öğe türündedir <xref:System.ServiceModel.Configuration.CertificateElement> .</span><span class="sxs-lookup"><span data-stu-id="5eefd-114">This element is of type <xref:System.ServiceModel.Configuration.CertificateElement>.</span></span> <span data-ttu-id="5eefd-115">`encodedValue`Bu, bu sertifika tarafından kodlanan değeri belirten String olan bir özniteliği içerir.</span><span class="sxs-lookup"><span data-stu-id="5eefd-115">It contains an attribute `encodedValue` that is a string, which specifies the value encoded by this certificate.</span></span>|  
|<span data-ttu-id="5eefd-116">certificateReference</span><span class="sxs-lookup"><span data-stu-id="5eefd-116">certificateReference</span></span>|<span data-ttu-id="5eefd-117">X. 509.440 sertifika doğrulamasının ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5eefd-117">Specifies settings for X.509 certificate validation.</span></span> <span data-ttu-id="5eefd-118">Bu öğe türündedir <xref:System.ServiceModel.Configuration.CertificateReferenceElement> .</span><span class="sxs-lookup"><span data-stu-id="5eefd-118">This element is of type <xref:System.ServiceModel.Configuration.CertificateReferenceElement>.</span></span>|  
|<span data-ttu-id="5eefd-119">dns</span><span class="sxs-lookup"><span data-stu-id="5eefd-119">dns</span></span>|<span data-ttu-id="5eefd-120">Bir hizmetin kimliğini doğrulamak için kullanılan X. 509.440 sertifikasının DNS 'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5eefd-120">Specifies the DNS of an X.509 certificate used to authenticate a service.</span></span> <span data-ttu-id="5eefd-121">Bu öğe `value` , bir dize olan ve gerçek kimliği içeren bir özniteliği içerir.</span><span class="sxs-lookup"><span data-stu-id="5eefd-121">This element contains an attribute `value` that is a string, and contains the actual identity.</span></span>|  
|<span data-ttu-id="5eefd-122">rsa</span><span class="sxs-lookup"><span data-stu-id="5eefd-122">rsa</span></span>|<span data-ttu-id="5eefd-123">Bir istemciye bir hizmetin kimliğini doğrulamak için kullanılan X. 509.440 sertifikasının RSA alanının değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5eefd-123">Specifies the value of the RSA field of an X.509 certificate used to authenticate a service to a client.</span></span> <span data-ttu-id="5eefd-124">Bu öğe `value` , bir dize olan ve gerçek kimliği içeren bir özniteliği içerir</span><span class="sxs-lookup"><span data-stu-id="5eefd-124">This element contains an attribute `value` that is a string, and contains the actual identity</span></span>|  
|<span data-ttu-id="5eefd-125">servicePrincipalName</span><span class="sxs-lookup"><span data-stu-id="5eefd-125">servicePrincipalName</span></span>|<span data-ttu-id="5eefd-126">Bir hizmetin bir örneğini benzersiz bir şekilde tanımlamak için bir istemci tarafından kullanılan asıl ad olan bir sunucu asıl adı (SPN) kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5eefd-126">Specifies a server principal name (SPN) identity, which is the principal name used by a client to uniquely identify an instance of a service.</span></span> <span data-ttu-id="5eefd-127">Bu öğe `value` , bir dize olan ve asıl asıl adı içeren bir özniteliği içerir.</span><span class="sxs-lookup"><span data-stu-id="5eefd-127">This element contains an attribute `value` that is a string, and contains the actual principal name.</span></span> <span data-ttu-id="5eefd-128">Bu öğe türündedir <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement> .</span><span class="sxs-lookup"><span data-stu-id="5eefd-128">This element is of type <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>.</span></span>|  
|<span data-ttu-id="5eefd-129">userPrincipalName</span><span class="sxs-lookup"><span data-stu-id="5eefd-129">userPrincipalName</span></span>|<span data-ttu-id="5eefd-130">Bir ağdaki kullanıcının oturum açma adı türü olan bir Kullanıcı asıl adı (UPN) kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5eefd-130">Specifies a user principal name (UPN) identity, which is the logon name type of a user on a network.</span></span> <span data-ttu-id="5eefd-131">Kullanıcı asıl adı, Active Directory ' de kullanılan Kullanıcı nesne adından \@ ve ardından genellikle etki alanı adı sistemi üst etki alanına sahip.</span><span class="sxs-lookup"><span data-stu-id="5eefd-131">The user principal name consists of the user object name used in Active Directory, followed by the at symbol (\@) and then, typically, the Domain Name System parent domain.</span></span> <span data-ttu-id="5eefd-132">Örneğin, Fabrikam.com etki alanı ağacındaki Jeff, Kullanıcı asıl adına sahip olabilir [jeff@fabrikam.com](mailto:jeffsmith@fabrikam.com) .</span><span class="sxs-lookup"><span data-stu-id="5eefd-132">For example, Jeff in the Fabrikam.com domain tree might have the user principal name [jeff@fabrikam.com](mailto:jeffsmith@fabrikam.com).</span></span>  <span data-ttu-id="5eefd-133">Bu öğe `value` , bir dize olan ve asıl asıl adı içeren bir özniteliği içerir.</span><span class="sxs-lookup"><span data-stu-id="5eefd-133">This element contains an attribute `value` that is a string, and contains the actual principal name.</span></span> <span data-ttu-id="5eefd-134">Bu öğe türündedir <xref:System.ServiceModel.Configuration.UserPrincipalNameElement> .</span><span class="sxs-lookup"><span data-stu-id="5eefd-134">This element is of type <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5eefd-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5eefd-135">Parent Elements</span></span>  
  
|<span data-ttu-id="5eefd-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="5eefd-136">Element</span></span>|<span data-ttu-id="5eefd-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5eefd-137">Description</span></span>|  
|-------------|-----------------|  
|[\<custom>](custom.md)|<span data-ttu-id="5eefd-138">NetPeerTcpBinding için özel bir eş çözümleyici belirtir.</span><span class="sxs-lookup"><span data-stu-id="5eefd-138">Specifies a custom peer resolver for a netPeerTcpBinding.</span></span>|  
|[\<endpoint>](endpoint-element.md)|<span data-ttu-id="5eefd-139">Hizmet uç noktalarını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="5eefd-139">Configures service endpoints.</span></span>|  
|[<span data-ttu-id="5eefd-140">\<endpoint>durumunu\<client></span><span class="sxs-lookup"><span data-stu-id="5eefd-140">\<endpoint> of \<client></span></span>](endpoint-of-client.md)|<span data-ttu-id="5eefd-141">Kanal uç noktalarını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="5eefd-141">Configures channel endpoints.</span></span>|  
|[\<issuer>](issuer.md)|<span data-ttu-id="5eefd-142">Federasyon Hizmeti için güvenlik belirteci hizmetini (STS) belirtir.</span><span class="sxs-lookup"><span data-stu-id="5eefd-142">Specifies the Security Token Service (STS) for the federated service.</span></span>|  
|[\<issuerMetadata>](issuermetadata.md)|<span data-ttu-id="5eefd-143">Federasyon Hizmeti 'nin güvenlik belirteci hizmeti (STS) için meta veri uç noktasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5eefd-143">Specifies the metadata endpoint for the Security Token Service (STS) of a federated service.</span></span>|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|<span data-ttu-id="5eefd-144">Özel bağlamadaki verilen belirtecin parametrelerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5eefd-144">Defines parameters for an issued token in a custom binding.</span></span>|  
|[\<localIssuer>](localissuer.md)|<span data-ttu-id="5eefd-145">Yerel bir güvenlik belirteci hizmetini (STS) belirtir.</span><span class="sxs-lookup"><span data-stu-id="5eefd-145">Specifies a local Security Token Service (STS).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5eefd-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5eefd-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- [<span data-ttu-id="5eefd-147">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="5eefd-147">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="5eefd-148">Uç Noktalar: Adresler, Bağlamalar ve Anlaşmalar</span><span class="sxs-lookup"><span data-stu-id="5eefd-148">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
