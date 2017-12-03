---
title: "&lt;sertifika&gt; Öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b3d9233-ef35-477a-bf5d-efd1e80a52f4
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 00f1b1f93836f3890a4c3f3797b583a15aeb599f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltcertificategt-element"></a><span data-ttu-id="d31bf-102">&lt;sertifika&gt; Öğesi</span><span class="sxs-lookup"><span data-stu-id="d31bf-102">&lt;certificate&gt; Element</span></span>
<span data-ttu-id="d31bf-103">İmzalama ve eşler arası istemcileri için iletileri şifrelemek için kullanılacak bir X.509 sertifikası belirtir.</span><span class="sxs-lookup"><span data-stu-id="d31bf-103">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="d31bf-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="d31bf-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d31bf-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="d31bf-105">\<behaviors></span></span>  
<span data-ttu-id="d31bf-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="d31bf-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="d31bf-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="d31bf-107">\<behavior></span></span>  
<span data-ttu-id="d31bf-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="d31bf-108">\<clientCredentials></span></span>  
<span data-ttu-id="d31bf-109">\<Eş ></span><span class="sxs-lookup"><span data-stu-id="d31bf-109">\<peer></span></span>  
<span data-ttu-id="d31bf-110">\<Sertifika ></span><span class="sxs-lookup"><span data-stu-id="d31bf-110">\<certificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d31bf-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d31bf-111">Syntax</span></span>  
  
```xml  
<certificate findValue="String"   
  
storeLocation="LocalMachine/CurrentUser"  
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
      X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d31bf-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d31bf-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d31bf-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d31bf-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d31bf-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d31bf-114">Attributes</span></span>  
  
|<span data-ttu-id="d31bf-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d31bf-115">Attribute</span></span>|<span data-ttu-id="d31bf-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d31bf-116">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="d31bf-117">X.509 sertifika deposunda arama için değer içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="d31bf-117">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="d31bf-118">Özniteliğinde bulunan türü belirtilen gereksinimleri karşılaması gerekir `x509FindType`.</span><span class="sxs-lookup"><span data-stu-id="d31bf-118">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="d31bf-119">Varsayılan boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="d31bf-119">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="d31bf-120">İstemcinin karşı eşin sertifikasını doğrulamak için kullandığı X.509 sertifika depolama konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d31bf-120">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="d31bf-121">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d31bf-121">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d31bf-122">-LocalMachine: Yerel Makine sertifika deposuna.</span><span class="sxs-lookup"><span data-stu-id="d31bf-122">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="d31bf-123">-Currentuser'a: sertifika deposuna geçerli kullanıcıya atanmış.</span><span class="sxs-lookup"><span data-stu-id="d31bf-123">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="d31bf-124">LocalMachine varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="d31bf-124">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="d31bf-125">Açmak için X.509 Sertifika deposu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d31bf-125">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="d31bf-126">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d31bf-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d31bf-127">-Adres Defteri: Diğer kullanıcılar sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="d31bf-127">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="d31bf-128">-AuthRoot: sertifika deposunu üçüncü taraf sertifika yetkilileri (CA'lar) için.</span><span class="sxs-lookup"><span data-stu-id="d31bf-128">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="d31bf-129">-CertificateAuthority: Ara sertifika yetkilileri (CA'lar) sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="d31bf-129">-   CertificateAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="d31bf-130">-İzin verilmeyen: mağaza iptal edilen sertifikaları için sertifika.</span><span class="sxs-lookup"><span data-stu-id="d31bf-130">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="d31bf-131">-My: Sertifika deposunda kişisel sertifikalar için.</span><span class="sxs-lookup"><span data-stu-id="d31bf-131">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="d31bf-132">-Kök: Güvenilen kök sertifika yetkilileri (CA'lar) sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="d31bf-132">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="d31bf-133">-TrustedPeople: Doğrudan-güvenilir kişiler ve kaynaklar sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="d31bf-133">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="d31bf-134">-TrustedPublisher: Doğrudan-Güvenilen Yayımcılar sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="d31bf-134">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="d31bf-135">Varsayılan değer My.</span><span class="sxs-lookup"><span data-stu-id="d31bf-135">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="d31bf-136">Yürütülecek X.509 arama türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d31bf-136">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="d31bf-137">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d31bf-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d31bf-138">-FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="d31bf-138">-   FindByThumbPrint</span></span><br /><span data-ttu-id="d31bf-139">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="d31bf-139">-   FindBySubjectName</span></span><br /><span data-ttu-id="d31bf-140">-FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="d31bf-140">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="d31bf-141">-FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="d31bf-141">-   FindByIssuerName</span></span><br /><span data-ttu-id="d31bf-142">-FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="d31bf-142">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="d31bf-143">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="d31bf-143">-   FindBySerialNumber</span></span><br /><span data-ttu-id="d31bf-144">-FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="d31bf-144">-   FindByTimeValid</span></span><br /><span data-ttu-id="d31bf-145">-FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="d31bf-145">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="d31bf-146">-FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="d31bf-146">-   FindByTemplateName</span></span><br /><span data-ttu-id="d31bf-147">-FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="d31bf-147">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="d31bf-148">-FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="d31bf-148">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="d31bf-149">-FindByExtension</span><span class="sxs-lookup"><span data-stu-id="d31bf-149">-   FindByExtension</span></span><br /><span data-ttu-id="d31bf-150">-FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="d31bf-150">-   FindByKeyUsage</span></span><br /><span data-ttu-id="d31bf-151">-FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="d31bf-151">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="d31bf-152">İçinde yer alan türü `findValue` özniteliği belirtilen gereksinimleri karşılaması gerekir `X509FindType`.</span><span class="sxs-lookup"><span data-stu-id="d31bf-152">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="d31bf-153">FindBySubjectDistinguishedName varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="d31bf-153">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d31bf-154">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d31bf-154">Child Elements</span></span>  
 <span data-ttu-id="d31bf-155">Yok.</span><span class="sxs-lookup"><span data-stu-id="d31bf-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d31bf-156">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d31bf-156">Parent Elements</span></span>  
  
|<span data-ttu-id="d31bf-157">Öğe</span><span class="sxs-lookup"><span data-stu-id="d31bf-157">Element</span></span>|<span data-ttu-id="d31bf-158">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d31bf-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d31bf-159">\<Eş ></span><span class="sxs-lookup"><span data-stu-id="d31bf-159">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="d31bf-160">Eşler arası istemcileri kimlik doğrulaması yapılırken kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d31bf-160">Specifies credentials used when authenticating peer-to-peer clients.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d31bf-161">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d31bf-161">Remarks</span></span>  
 <span data-ttu-id="d31bf-162">Bu yapılandırma öğesi eş kafes Komşuları doğrulanırken kullanılan X509Certificate2 örneğini içerir.</span><span class="sxs-lookup"><span data-stu-id="d31bf-162">This configuration element contains a X509Certificate2 instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="d31bf-163">Eşler arası programlama hakkında daha fazla bilgi için bkz: [eşler arası ağ](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="d31bf-163">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d31bf-164">Örnek</span><span class="sxs-lookup"><span data-stu-id="d31bf-164">Example</span></span>  
 <span data-ttu-id="d31bf-165">Aşağıdaki kod bir eşler arası senaryosunda kullanılan sertifikayı bulmak nasıl belirtir.</span><span class="sxs-lookup"><span data-stu-id="d31bf-165">The following code specifies how to find the certificate used in a peer-to-peer scenario.</span></span>  
  
```xml  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <peer>  
     <certificate findValue="www.contoso.com"   
                   storeLocation="LocalMachine"  
                   x509FindType="FindByIssuerName" />  
    </peer>  
   </clientCredentials>  
  </behavior>  
</endpointBehaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d31bf-166">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d31bf-166">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>  
 <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>  
 [<span data-ttu-id="d31bf-167">Sertifikalar ile çalışma</span><span class="sxs-lookup"><span data-stu-id="d31bf-167">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="d31bf-168">Eşler arası ağ</span><span class="sxs-lookup"><span data-stu-id="d31bf-168">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="d31bf-169">Eş kanal ileti kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="d31bf-169">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="d31bf-170">Eş kanal özel kimlik doğrulama</span><span class="sxs-lookup"><span data-stu-id="d31bf-170">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="d31bf-171">Eş kanalı uygulamalarını güvenli hale getirme</span><span class="sxs-lookup"><span data-stu-id="d31bf-171">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
