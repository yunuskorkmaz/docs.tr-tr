---
title: '&lt;sertifika&gt; Öğesi'
ms.date: 03/30/2017
ms.assetid: 9b3d9233-ef35-477a-bf5d-efd1e80a52f4
ms.openlocfilehash: 5329fb276766ca2bd24f0fd3aef793fbb3b1f8b8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43515401"
---
# <a name="ltcertificategt-element"></a><span data-ttu-id="57dd2-102">&lt;sertifika&gt; Öğesi</span><span class="sxs-lookup"><span data-stu-id="57dd2-102">&lt;certificate&gt; Element</span></span>
<span data-ttu-id="57dd2-103">İmzalama ve eşler arası istemcileri için iletileri şifrelemek için bir X.509 sertifikasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="57dd2-103">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="57dd2-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="57dd2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="57dd2-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="57dd2-105">\<behaviors></span></span>  
<span data-ttu-id="57dd2-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="57dd2-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="57dd2-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="57dd2-107">\<behavior></span></span>  
<span data-ttu-id="57dd2-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="57dd2-108">\<clientCredentials></span></span>  
<span data-ttu-id="57dd2-109">\<Eş ></span><span class="sxs-lookup"><span data-stu-id="57dd2-109">\<peer></span></span>  
<span data-ttu-id="57dd2-110">\<Sertifika ></span><span class="sxs-lookup"><span data-stu-id="57dd2-110">\<certificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57dd2-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="57dd2-111">Syntax</span></span>  
  
```xml  
<certificate findValue="String"   
  
storeLocation="LocalMachine/CurrentUser"  
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
      X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57dd2-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="57dd2-112">Attributes and Elements</span></span>  
 <span data-ttu-id="57dd2-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="57dd2-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57dd2-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="57dd2-114">Attributes</span></span>  
  
|<span data-ttu-id="57dd2-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="57dd2-115">Attribute</span></span>|<span data-ttu-id="57dd2-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57dd2-116">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="57dd2-117">X.509 sertifika deposunda aranacak değeri içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="57dd2-117">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="57dd2-118">Özniteliğinde bulunan türü belirtilen gereksinimleri karşılaması gerekir `x509FindType`.</span><span class="sxs-lookup"><span data-stu-id="57dd2-118">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="57dd2-119">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="57dd2-119">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="57dd2-120">Eşin sertifikasını doğrulamak için istemcinin kullandığı X.509 Sertifika deposunun konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="57dd2-120">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="57dd2-121">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="57dd2-121">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="57dd2-122">-LocalMachine: yerel makineye atanmış sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="57dd2-122">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="57dd2-123">-CurrentUser: geçerli kullanıcıya atanmış sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="57dd2-123">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="57dd2-124">LocalMachine varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="57dd2-124">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="57dd2-125">Açılacak X.509 Sertifika deposunun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="57dd2-125">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="57dd2-126">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="57dd2-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="57dd2-127">-Adres Defteri: Diğer kullanıcılar için sertifika deposuna.</span><span class="sxs-lookup"><span data-stu-id="57dd2-127">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="57dd2-128">-AuthRoot: sertifika deposunu için üçüncü taraf sertifika yetkilileri (CA).</span><span class="sxs-lookup"><span data-stu-id="57dd2-128">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="57dd2-129">-CertificateAuthority: Ara sertifika yetkilileri (CA'lar) sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="57dd2-129">-   CertificateAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="57dd2-130">-İzin verilmedi: iptal edilen sertifikalar deposuna sertifika.</span><span class="sxs-lookup"><span data-stu-id="57dd2-130">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="57dd2-131">-My: Kişisel Sertifikalar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="57dd2-131">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="57dd2-132">-Kök: Güvenilen kök sertifika yetkilileri (CA'lar) için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="57dd2-132">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="57dd2-133">-TrustedPeople: Sertifika deposu-doğrudan güvenilen kişiler ve kaynaklar.</span><span class="sxs-lookup"><span data-stu-id="57dd2-133">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="57dd2-134">-TrustedPublisher: Doğrudan Güvenilen Yayımcılar sertifika deposuna.</span><span class="sxs-lookup"><span data-stu-id="57dd2-134">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="57dd2-135">Varsayılan değer benim.</span><span class="sxs-lookup"><span data-stu-id="57dd2-135">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="57dd2-136">Yürütülecek X.509 arama türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="57dd2-136">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="57dd2-137">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="57dd2-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="57dd2-138">-FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="57dd2-138">-   FindByThumbPrint</span></span><br /><span data-ttu-id="57dd2-139">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="57dd2-139">-   FindBySubjectName</span></span><br /><span data-ttu-id="57dd2-140">-FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="57dd2-140">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="57dd2-141">-FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="57dd2-141">-   FindByIssuerName</span></span><br /><span data-ttu-id="57dd2-142">-FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="57dd2-142">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="57dd2-143">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="57dd2-143">-   FindBySerialNumber</span></span><br /><span data-ttu-id="57dd2-144">-FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="57dd2-144">-   FindByTimeValid</span></span><br /><span data-ttu-id="57dd2-145">-FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="57dd2-145">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="57dd2-146">-FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="57dd2-146">-   FindByTemplateName</span></span><br /><span data-ttu-id="57dd2-147">-FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="57dd2-147">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="57dd2-148">-FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="57dd2-148">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="57dd2-149">-FindByExtension</span><span class="sxs-lookup"><span data-stu-id="57dd2-149">-   FindByExtension</span></span><br /><span data-ttu-id="57dd2-150">-FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="57dd2-150">-   FindByKeyUsage</span></span><br /><span data-ttu-id="57dd2-151">-FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="57dd2-151">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="57dd2-152">Bulunan tür `findValue` öznitelik belirtilen gereksinimleri karşılaması gerekir `X509FindType`.</span><span class="sxs-lookup"><span data-stu-id="57dd2-152">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="57dd2-153">FindBySubjectDistinguishedName varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="57dd2-153">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="57dd2-154">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="57dd2-154">Child Elements</span></span>  
 <span data-ttu-id="57dd2-155">Yok.</span><span class="sxs-lookup"><span data-stu-id="57dd2-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="57dd2-156">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="57dd2-156">Parent Elements</span></span>  
  
|<span data-ttu-id="57dd2-157">Öğe</span><span class="sxs-lookup"><span data-stu-id="57dd2-157">Element</span></span>|<span data-ttu-id="57dd2-158">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57dd2-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57dd2-159">\<Eş ></span><span class="sxs-lookup"><span data-stu-id="57dd2-159">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="57dd2-160">Eşler arası istemcilerin kimlik doğrulaması için kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="57dd2-160">Specifies credentials used when authenticating peer-to-peer clients.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57dd2-161">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="57dd2-161">Remarks</span></span>  
 <span data-ttu-id="57dd2-162">Bu yapılandırma öğesi içinde Eş Ağ Komşuları kimlik doğrulaması için kullanılan bir X509Certificate2 örneği içerir.</span><span class="sxs-lookup"><span data-stu-id="57dd2-162">This configuration element contains a X509Certificate2 instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="57dd2-163">Eşler arası programlama hakkında daha fazla bilgi için bkz. [eşler arası ağ](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="57dd2-163">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="57dd2-164">Örnek</span><span class="sxs-lookup"><span data-stu-id="57dd2-164">Example</span></span>  
 <span data-ttu-id="57dd2-165">Aşağıdaki kod, bir eşler arası senaryosunda kullanılan sertifikanın nasıl belirtir.</span><span class="sxs-lookup"><span data-stu-id="57dd2-165">The following code specifies how to find the certificate used in a peer-to-peer scenario.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="57dd2-166">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="57dd2-166">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>  
 <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>  
 [<span data-ttu-id="57dd2-167">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="57dd2-167">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="57dd2-168">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="57dd2-168">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="57dd2-169">Eş kanal ileti kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="57dd2-169">Peer Channel Message Authentication</span></span>](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="57dd2-170">Eş kanal özel kimlik doğrulama</span><span class="sxs-lookup"><span data-stu-id="57dd2-170">Peer Channel Custom Authentication</span></span>](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="57dd2-171">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="57dd2-171">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
