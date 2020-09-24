---
title: <identity>
ms.date: 03/30/2017
ms.assetid: c1d2ae56-e231-4a07-9c3f-9f13381dc0d8
ms.openlocfilehash: bb9468b6005361a2a480f7c0ebfb2cbb9e9199c2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157388"
---
# \<identity>

<span data-ttu-id="c4068-101">Identity öğesi, bir istemci geliştiricisinin, hizmetin beklenen kimliği olan tasarım zamanında belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="c4068-101">The identity element allows a client developer to specify at design time the expected identity of the service.</span></span> <span data-ttu-id="c4068-102">İstemci ve hizmet arasındaki el sıkışma işleminde, Windows Communication Foundation (WCF) altyapısı, beklenen hizmetin kimliğinin bu öğenin değerleriyle eşleştiğinden emin olur ve bu nedenle kimlik doğrulaması yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="c4068-102">In the handshake process between the client and service, the Windows Communication Foundation (WCF) infrastructure will ensure that the identity of the expected service matches the values of this element, and thus can be authenticated.</span></span> <span data-ttu-id="c4068-103">Daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c4068-103">For more information, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<identity>**  
  
## <a name="syntax"></a><span data-ttu-id="c4068-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="c4068-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c4068-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c4068-105">Attributes and Elements</span></span>  

 <span data-ttu-id="c4068-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c4068-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c4068-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c4068-107">Attributes</span></span>  

 <span data-ttu-id="c4068-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="c4068-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c4068-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c4068-109">Child Elements</span></span>  
  
|<span data-ttu-id="c4068-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="c4068-110">Element</span></span>|<span data-ttu-id="c4068-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c4068-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c4068-112">sertifika</span><span class="sxs-lookup"><span data-stu-id="c4068-112">certificate</span></span>|<span data-ttu-id="c4068-113">X. 509.440 sertifikasının ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4068-113">Specifies settings of an X.509 certificate.</span></span> <span data-ttu-id="c4068-114">Bu öğe türündedir <xref:System.ServiceModel.Configuration.CertificateElement> .</span><span class="sxs-lookup"><span data-stu-id="c4068-114">This element is of type <xref:System.ServiceModel.Configuration.CertificateElement>.</span></span> <span data-ttu-id="c4068-115">`encodedValue`Bu, bu sertifika tarafından kodlanan değeri belirten String olan bir özniteliği içerir.</span><span class="sxs-lookup"><span data-stu-id="c4068-115">It contains an attribute `encodedValue` that is a string, which specifies the value encoded by this certificate.</span></span>|  
|<span data-ttu-id="c4068-116">certificateReference</span><span class="sxs-lookup"><span data-stu-id="c4068-116">certificateReference</span></span>|<span data-ttu-id="c4068-117">X. 509.440 sertifika doğrulamasının ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4068-117">Specifies settings for X.509 certificate validation.</span></span> <span data-ttu-id="c4068-118">Bu öğe türündedir <xref:System.ServiceModel.Configuration.CertificateReferenceElement> .</span><span class="sxs-lookup"><span data-stu-id="c4068-118">This element is of type <xref:System.ServiceModel.Configuration.CertificateReferenceElement>.</span></span>|  
|<span data-ttu-id="c4068-119">dns</span><span class="sxs-lookup"><span data-stu-id="c4068-119">dns</span></span>|<span data-ttu-id="c4068-120">Bir hizmetin kimliğini doğrulamak için kullanılan X. 509.440 sertifikasının DNS 'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4068-120">Specifies the DNS of an X.509 certificate used to authenticate a service.</span></span> <span data-ttu-id="c4068-121">Bu öğe `value` , bir dize olan ve gerçek kimliği içeren bir özniteliği içerir.</span><span class="sxs-lookup"><span data-stu-id="c4068-121">This element contains an attribute `value` that is a string, and contains the actual identity.</span></span>|  
|<span data-ttu-id="c4068-122">rsa</span><span class="sxs-lookup"><span data-stu-id="c4068-122">rsa</span></span>|<span data-ttu-id="c4068-123">Bir istemciye bir hizmetin kimliğini doğrulamak için kullanılan X. 509.440 sertifikasının RSA alanının değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4068-123">Specifies the value of the RSA field of an X.509 certificate used to authenticate a service to a client.</span></span> <span data-ttu-id="c4068-124">Bu öğe `value` , bir dize olan ve gerçek kimliği içeren bir özniteliği içerir</span><span class="sxs-lookup"><span data-stu-id="c4068-124">This element contains an attribute `value` that is a string, and contains the actual identity</span></span>|  
|<span data-ttu-id="c4068-125">servicePrincipalName</span><span class="sxs-lookup"><span data-stu-id="c4068-125">servicePrincipalName</span></span>|<span data-ttu-id="c4068-126">Bir hizmetin bir örneğini benzersiz bir şekilde tanımlamak için bir istemci tarafından kullanılan asıl ad olan bir sunucu asıl adı (SPN) kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4068-126">Specifies a server principal name (SPN) identity, which is the principal name used by a client to uniquely identify an instance of a service.</span></span> <span data-ttu-id="c4068-127">Bu öğe `value` , bir dize olan ve asıl asıl adı içeren bir özniteliği içerir.</span><span class="sxs-lookup"><span data-stu-id="c4068-127">This element contains an attribute `value` that is a string, and contains the actual principal name.</span></span> <span data-ttu-id="c4068-128">Bu öğe türündedir <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement> .</span><span class="sxs-lookup"><span data-stu-id="c4068-128">This element is of type <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>.</span></span>|  
|<span data-ttu-id="c4068-129">userPrincipalName</span><span class="sxs-lookup"><span data-stu-id="c4068-129">userPrincipalName</span></span>|<span data-ttu-id="c4068-130">Bir ağdaki kullanıcının oturum açma adı türü olan bir Kullanıcı asıl adı (UPN) kimliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4068-130">Specifies a user principal name (UPN) identity, which is the logon name type of a user on a network.</span></span> <span data-ttu-id="c4068-131">Kullanıcı asıl adı, Active Directory ' de kullanılan Kullanıcı nesne adından \@ ve ardından genellikle etki alanı adı sistemi üst etki alanına sahip.</span><span class="sxs-lookup"><span data-stu-id="c4068-131">The user principal name consists of the user object name used in Active Directory, followed by the at symbol (\@) and then, typically, the Domain Name System parent domain.</span></span> <span data-ttu-id="c4068-132">Örneğin, Fabrikam.com etki alanı ağacındaki Jeff, Kullanıcı asıl adına sahip olabilir [jeff@fabrikam.com](mailto:jeffsmith@fabrikam.com) .</span><span class="sxs-lookup"><span data-stu-id="c4068-132">For example, Jeff in the Fabrikam.com domain tree might have the user principal name [jeff@fabrikam.com](mailto:jeffsmith@fabrikam.com).</span></span>  <span data-ttu-id="c4068-133">Bu öğe `value` , bir dize olan ve asıl asıl adı içeren bir özniteliği içerir.</span><span class="sxs-lookup"><span data-stu-id="c4068-133">This element contains an attribute `value` that is a string, and contains the actual principal name.</span></span> <span data-ttu-id="c4068-134">Bu öğe türündedir <xref:System.ServiceModel.Configuration.UserPrincipalNameElement> .</span><span class="sxs-lookup"><span data-stu-id="c4068-134">This element is of type <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c4068-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c4068-135">Parent Elements</span></span>  
  
|<span data-ttu-id="c4068-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="c4068-136">Element</span></span>|<span data-ttu-id="c4068-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c4068-137">Description</span></span>|  
|-------------|-----------------|  
|[\<custom>](custom.md)|<span data-ttu-id="c4068-138">NetPeerTcpBinding için özel bir eş çözümleyici belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4068-138">Specifies a custom peer resolver for a netPeerTcpBinding.</span></span>|  
|[\<endpoint>](endpoint-element.md)|<span data-ttu-id="c4068-139">Hizmet uç noktalarını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="c4068-139">Configures service endpoints.</span></span>|  
|[<span data-ttu-id="c4068-140">\<endpoint> durumunu \<client></span><span class="sxs-lookup"><span data-stu-id="c4068-140">\<endpoint> of \<client></span></span>](endpoint-of-client.md)|<span data-ttu-id="c4068-141">Kanal uç noktalarını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="c4068-141">Configures channel endpoints.</span></span>|  
|[\<issuer>](issuer.md)|<span data-ttu-id="c4068-142">Federasyon Hizmeti için güvenlik belirteci hizmetini (STS) belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4068-142">Specifies the Security Token Service (STS) for the federated service.</span></span>|  
|[\<issuerMetadata>](issuermetadata.md)|<span data-ttu-id="c4068-143">Federasyon Hizmeti 'nin güvenlik belirteci hizmeti (STS) için meta veri uç noktasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4068-143">Specifies the metadata endpoint for the Security Token Service (STS) of a federated service.</span></span>|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|<span data-ttu-id="c4068-144">Özel bağlamadaki verilen belirtecin parametrelerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c4068-144">Defines parameters for an issued token in a custom binding.</span></span>|  
|[\<localIssuer>](localissuer.md)|<span data-ttu-id="c4068-145">Yerel bir güvenlik belirteci hizmetini (STS) belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4068-145">Specifies a local Security Token Service (STS).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c4068-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4068-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- [<span data-ttu-id="c4068-147">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="c4068-147">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="c4068-148">Uç Noktalar: Adresler, Bağlamalar ve Sözleşmeler</span><span class="sxs-lookup"><span data-stu-id="c4068-148">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
