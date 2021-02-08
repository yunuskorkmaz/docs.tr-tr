---
description: 'Hakkında daha fazla bilgi edinin: <identity>'
title: <identity>
ms.date: 03/30/2017
ms.assetid: c1d2ae56-e231-4a07-9c3f-9f13381dc0d8
ms.openlocfilehash: ceb4dc0e7efa6cd01204253001432ed1ef2c048e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802261"
---
# \<identity>

<span data-ttu-id="ed5b9-102">Identity öğesi, bir istemci geliştiricisinin, hizmetin beklenen kimliği olan tasarım zamanında belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ed5b9-102">The identity element allows a client developer to specify at design time the expected identity of the service.</span></span> <span data-ttu-id="ed5b9-103">İstemci ve hizmet arasındaki el sıkışma işleminde, Windows Communication Foundation (WCF) altyapısı, beklenen hizmetin kimliğinin bu öğenin değerleriyle eşleştiğinden emin olur ve bu nedenle kimlik doğrulaması yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="ed5b9-103">In the handshake process between the client and service, the Windows Communication Foundation (WCF) infrastructure will ensure that the identity of the expected service matches the values of this element, and thus can be authenticated.</span></span> <span data-ttu-id="ed5b9-104">Daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="ed5b9-104">For more information, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<identity>**  
  
## <a name="syntax"></a><span data-ttu-id="ed5b9-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ed5b9-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ed5b9-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ed5b9-106">Attributes and Elements</span></span>  

 <span data-ttu-id="ed5b9-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ed5b9-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ed5b9-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ed5b9-108">Attributes</span></span>  

 <span data-ttu-id="ed5b9-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="ed5b9-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ed5b9-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ed5b9-110">Child Elements</span></span>  
  
|<span data-ttu-id="ed5b9-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="ed5b9-111">Element</span></span>|<span data-ttu-id="ed5b9-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed5b9-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ed5b9-113">sertifika</span><span class="sxs-lookup"><span data-stu-id="ed5b9-113">certificate</span></span>|<span data-ttu-id="ed5b9-114">X. 509.440 sertifikasının ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ed5b9-114">Specifies settings of an X.509 certificate.</span></span> <span data-ttu-id="ed5b9-115">Bu öğe türündedir <xref:System.ServiceModel.Configuration.CertificateElement> .</span><span class="sxs-lookup"><span data-stu-id="ed5b9-115">This element is of type <xref:System.ServiceModel.Configuration.CertificateElement>.</span></span> <span data-ttu-id="ed5b9-116">`encodedValue`Bu, bu sertifika tarafından kodlanan değeri belirten String olan bir özniteliği içerir.</span><span class="sxs-lookup"><span data-stu-id="ed5b9-116">It contains an attribute `encodedValue` that is a string, which specifies the value encoded by this certificate.</span></span>|  
|<span data-ttu-id="ed5b9-117">certificateReference</span><span class="sxs-lookup"><span data-stu-id="ed5b9-117">certificateReference</span></span>|<span data-ttu-id="ed5b9-118">X. 509.440 sertifika doğrulamasının ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ed5b9-118">Specifies settings for X.509 certificate validation.</span></span> <span data-ttu-id="ed5b9-119">Bu öğe türündedir <xref:System.ServiceModel.Configuration.CertificateReferenceElement> .</span><span class="sxs-lookup"><span data-stu-id="ed5b9-119">This element is of type <xref:System.ServiceModel.Configuration.CertificateReferenceElement>.</span></span>|  
|<span data-ttu-id="ed5b9-120">dns</span><span class="sxs-lookup"><span data-stu-id="ed5b9-120">dns</span></span>|<span data-ttu-id="ed5b9-121">Bir hizmetin kimliğini doğrulamak için kullanılan X. 509.440 sertifikasının DNS 'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ed5b9-121">Specifies the DNS of an X.509 certificate used to authenticate a service.</span></span> <span data-ttu-id="ed5b9-122">Bu öğe `value` , bir dize olan ve gerçek kimliği içeren bir özniteliği içerir.</span><span class="sxs-lookup"><span data-stu-id="ed5b9-122">This element contains an attribute `value` that is a string, and contains the actual identity.</span></span>|  
|<span data-ttu-id="ed5b9-123">rsa</span><span class="sxs-lookup"><span data-stu-id="ed5b9-123">rsa</span></span>|<span data-ttu-id="ed5b9-124">Bir istemciye bir hizmetin kimliğini doğrulamak için kullanılan X. 509.440 sertifikasının RSA alanının değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ed5b9-124">Specifies the value of the RSA field of an X.509 certificate used to authenticate a service to a client.</span></span> <span data-ttu-id="ed5b9-125">Bu öğe `value` , bir dize olan ve gerçek kimliği içeren bir özniteliği içerir</span><span class="sxs-lookup"><span data-stu-id="ed5b9-125">This element contains an attribute `value` that is a string, and contains the actual identity</span></span>|  
|<span data-ttu-id="ed5b9-126">servicePrincipalName</span><span class="sxs-lookup"><span data-stu-id="ed5b9-126">servicePrincipalName</span></span>|<span data-ttu-id="ed5b9-127">Bir hizmetin bir örneğini benzersiz bir şekilde tanımlamak için bir istemci tarafından kullanılan asıl ad olan bir sunucu asıl adı (SPN) kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ed5b9-127">Specifies a server principal name (SPN) identity, which is the principal name used by a client to uniquely identify an instance of a service.</span></span> <span data-ttu-id="ed5b9-128">Bu öğe `value` , bir dize olan ve asıl asıl adı içeren bir özniteliği içerir.</span><span class="sxs-lookup"><span data-stu-id="ed5b9-128">This element contains an attribute `value` that is a string, and contains the actual principal name.</span></span> <span data-ttu-id="ed5b9-129">Bu öğe türündedir <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement> .</span><span class="sxs-lookup"><span data-stu-id="ed5b9-129">This element is of type <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>.</span></span>|  
|<span data-ttu-id="ed5b9-130">userPrincipalName</span><span class="sxs-lookup"><span data-stu-id="ed5b9-130">userPrincipalName</span></span>|<span data-ttu-id="ed5b9-131">Bir ağdaki kullanıcının oturum açma adı türü olan bir Kullanıcı asıl adı (UPN) kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ed5b9-131">Specifies a user principal name (UPN) identity, which is the logon name type of a user on a network.</span></span> <span data-ttu-id="ed5b9-132">Kullanıcı asıl adı, Active Directory ' de kullanılan Kullanıcı nesne adından \@ ve ardından genellikle etki alanı adı sistemi üst etki alanına sahip.</span><span class="sxs-lookup"><span data-stu-id="ed5b9-132">The user principal name consists of the user object name used in Active Directory, followed by the at symbol (\@) and then, typically, the Domain Name System parent domain.</span></span> <span data-ttu-id="ed5b9-133">Örneğin, Fabrikam.com etki alanı ağacındaki Jeff, Kullanıcı asıl adına sahip olabilir [jeff@fabrikam.com](mailto:jeffsmith@fabrikam.com) .</span><span class="sxs-lookup"><span data-stu-id="ed5b9-133">For example, Jeff in the Fabrikam.com domain tree might have the user principal name [jeff@fabrikam.com](mailto:jeffsmith@fabrikam.com).</span></span>  <span data-ttu-id="ed5b9-134">Bu öğe `value` , bir dize olan ve asıl asıl adı içeren bir özniteliği içerir.</span><span class="sxs-lookup"><span data-stu-id="ed5b9-134">This element contains an attribute `value` that is a string, and contains the actual principal name.</span></span> <span data-ttu-id="ed5b9-135">Bu öğe türündedir <xref:System.ServiceModel.Configuration.UserPrincipalNameElement> .</span><span class="sxs-lookup"><span data-stu-id="ed5b9-135">This element is of type <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ed5b9-136">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ed5b9-136">Parent Elements</span></span>  
  
|<span data-ttu-id="ed5b9-137">Öğe</span><span class="sxs-lookup"><span data-stu-id="ed5b9-137">Element</span></span>|<span data-ttu-id="ed5b9-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed5b9-138">Description</span></span>|  
|-------------|-----------------|  
|[\<custom>](custom.md)|<span data-ttu-id="ed5b9-139">NetPeerTcpBinding için özel bir eş çözümleyici belirtir.</span><span class="sxs-lookup"><span data-stu-id="ed5b9-139">Specifies a custom peer resolver for a netPeerTcpBinding.</span></span>|  
|[\<endpoint>](endpoint-element.md)|<span data-ttu-id="ed5b9-140">Hizmet uç noktalarını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="ed5b9-140">Configures service endpoints.</span></span>|  
|[<span data-ttu-id="ed5b9-141">\<endpoint> durumunu \<client></span><span class="sxs-lookup"><span data-stu-id="ed5b9-141">\<endpoint> of \<client></span></span>](endpoint-of-client.md)|<span data-ttu-id="ed5b9-142">Kanal uç noktalarını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="ed5b9-142">Configures channel endpoints.</span></span>|  
|[\<issuer>](issuer.md)|<span data-ttu-id="ed5b9-143">Federasyon Hizmeti için güvenlik belirteci hizmetini (STS) belirtir.</span><span class="sxs-lookup"><span data-stu-id="ed5b9-143">Specifies the Security Token Service (STS) for the federated service.</span></span>|  
|[\<issuerMetadata>](issuermetadata.md)|<span data-ttu-id="ed5b9-144">Federasyon Hizmeti 'nin güvenlik belirteci hizmeti (STS) için meta veri uç noktasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ed5b9-144">Specifies the metadata endpoint for the Security Token Service (STS) of a federated service.</span></span>|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|<span data-ttu-id="ed5b9-145">Özel bağlamadaki verilen belirtecin parametrelerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ed5b9-145">Defines parameters for an issued token in a custom binding.</span></span>|  
|[\<localIssuer>](localissuer.md)|<span data-ttu-id="ed5b9-146">Yerel bir güvenlik belirteci hizmetini (STS) belirtir.</span><span class="sxs-lookup"><span data-stu-id="ed5b9-146">Specifies a local Security Token Service (STS).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ed5b9-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed5b9-147">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- [<span data-ttu-id="ed5b9-148">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="ed5b9-148">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="ed5b9-149">Uç Noktalar: Adresler, Bağlamalar ve Sözleşmeler</span><span class="sxs-lookup"><span data-stu-id="ed5b9-149">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
