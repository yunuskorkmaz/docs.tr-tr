---
title: <certificate> Öğesi
ms.date: 03/30/2017
ms.assetid: 9b3d9233-ef35-477a-bf5d-efd1e80a52f4
ms.openlocfilehash: e28e7d16073a56f3b6126439644bfff86c9af18b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400548"
---
# <a name="certificate-element"></a><span data-ttu-id="f9a47-102">\<Sertifika > öğesi</span><span class="sxs-lookup"><span data-stu-id="f9a47-102">\<certificate> Element</span></span>
<span data-ttu-id="f9a47-103">Eşler arası istemciler için ileti imzalama ve şifreleme için kullanılacak bir X. 509.952 sertifikası belirtir.</span><span class="sxs-lookup"><span data-stu-id="f9a47-103">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span>  
  
<span data-ttu-id="f9a47-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f9a47-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f9a47-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f9a47-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f9a47-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="f9a47-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="f9a47-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Endpointdavranışlar >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="f9a47-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="f9a47-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="f9a47-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="f9a47-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="f9a47-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="f9a47-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<eş >** ](peer-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="f9a47-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)</span></span>\
<span data-ttu-id="f9a47-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Sertifika >**</span><span class="sxs-lookup"><span data-stu-id="f9a47-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9a47-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f9a47-112">Syntax</span></span>  
  
```xml  
<certificate findValue="String"
             storeLocation="LocalMachine/CurrentUser"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f9a47-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f9a47-113">Attributes and Elements</span></span>  
 <span data-ttu-id="f9a47-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f9a47-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f9a47-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f9a47-115">Attributes</span></span>  
  
|<span data-ttu-id="f9a47-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f9a47-116">Attribute</span></span>|<span data-ttu-id="f9a47-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9a47-117">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="f9a47-118">X. 509.440 sertifika deposunda aranacak değeri içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="f9a47-118">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="f9a47-119">Özniteliğinde yer alan türün, belirtilen `x509FindType`gereksinimleri karşılaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f9a47-119">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="f9a47-120">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="f9a47-120">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="f9a47-121">İstemcinin eşin sertifikasını doğrulamak için kullandığı X. 509.952 sertifika deposunun konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="f9a47-121">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="f9a47-122">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f9a47-122">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f9a47-123">-LocalMachine: yerel makineye atanan sertifika depolama alanı.</span><span class="sxs-lookup"><span data-stu-id="f9a47-123">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="f9a47-124">-CurrentUser: geçerli kullanıcıya atanmış sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="f9a47-124">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="f9a47-125">Varsayılan değer LocalMachine 'dir.</span><span class="sxs-lookup"><span data-stu-id="f9a47-125">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="f9a47-126">Açılacak X. 509.440 sertifika deposunun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f9a47-126">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="f9a47-127">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f9a47-127">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f9a47-128">-AddressBook: Diğer kullanıcılar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="f9a47-128">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="f9a47-129">-AuthRoot: Üçüncü taraf sertifika yetkilileri (CA 'Lar) için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="f9a47-129">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="f9a47-130">CertificateAuthority Ara sertifika yetkilileri (CA 'Lar) için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="f9a47-130">-   CertificateAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="f9a47-131">Veril İptal edilen sertifikalar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="f9a47-131">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="f9a47-132">My Kişisel Sertifikalar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="f9a47-132">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="f9a47-133">Asıl Güvenilen kök sertifika yetkilileri (CA 'Lar) için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="f9a47-133">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="f9a47-134">TrustedPeople Doğrudan güvenilen kişiler ve kaynaklar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="f9a47-134">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="f9a47-135">-TrustedPublisher: Doğrudan güvenilen yayımcılar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="f9a47-135">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="f9a47-136">Varsayılan My.</span><span class="sxs-lookup"><span data-stu-id="f9a47-136">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="f9a47-137">Yürütülecek X. 509.440 aramasının türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f9a47-137">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="f9a47-138">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f9a47-138">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f9a47-139">-Findbyparmak Izi</span><span class="sxs-lookup"><span data-stu-id="f9a47-139">-   FindByThumbPrint</span></span><br /><span data-ttu-id="f9a47-140">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="f9a47-140">-   FindBySubjectName</span></span><br /><span data-ttu-id="f9a47-141">- FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="f9a47-141">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="f9a47-142">-FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="f9a47-142">-   FindByIssuerName</span></span><br /><span data-ttu-id="f9a47-143">- FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="f9a47-143">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="f9a47-144">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="f9a47-144">-   FindBySerialNumber</span></span><br /><span data-ttu-id="f9a47-145">-FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="f9a47-145">-   FindByTimeValid</span></span><br /><span data-ttu-id="f9a47-146">-FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="f9a47-146">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="f9a47-147">-FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="f9a47-147">-   FindByTemplateName</span></span><br /><span data-ttu-id="f9a47-148">- FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="f9a47-148">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="f9a47-149">-FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="f9a47-149">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="f9a47-150">-FindByExtension</span><span class="sxs-lookup"><span data-stu-id="f9a47-150">-   FindByExtension</span></span><br /><span data-ttu-id="f9a47-151">-FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="f9a47-151">-   FindByKeyUsage</span></span><br /><span data-ttu-id="f9a47-152">-FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="f9a47-152">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="f9a47-153">`findValue` Özniteliğinde yer alan türün, belirtilen `X509FindType`gereksinimleri karşılaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f9a47-153">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="f9a47-154">Varsayılan değer FindBySubjectDistinguishedName ' dir.</span><span class="sxs-lookup"><span data-stu-id="f9a47-154">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f9a47-155">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f9a47-155">Child Elements</span></span>  
 <span data-ttu-id="f9a47-156">Yok.</span><span class="sxs-lookup"><span data-stu-id="f9a47-156">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f9a47-157">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f9a47-157">Parent Elements</span></span>  
  
|<span data-ttu-id="f9a47-158">Öğe</span><span class="sxs-lookup"><span data-stu-id="f9a47-158">Element</span></span>|<span data-ttu-id="f9a47-159">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9a47-159">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f9a47-160">\<eş ></span><span class="sxs-lookup"><span data-stu-id="f9a47-160">\<peer></span></span>](peer-of-clientcredentials-element.md)|<span data-ttu-id="f9a47-161">Eşler arası istemcilerin kimlik doğrulaması sırasında kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f9a47-161">Specifies credentials used when authenticating peer-to-peer clients.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9a47-162">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f9a47-162">Remarks</span></span>  
 <span data-ttu-id="f9a47-163">Bu yapılandırma öğesi, eş kafeste komşuları doğrulanırken kullanılan bir X509Certificate2 örneği içeriyor.</span><span class="sxs-lookup"><span data-stu-id="f9a47-163">This configuration element contains a X509Certificate2 instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="f9a47-164">Eşler arası programlama hakkında daha fazla bilgi için bkz. eşler [arası ağ iletişimi](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="f9a47-164">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9a47-165">Örnek</span><span class="sxs-lookup"><span data-stu-id="f9a47-165">Example</span></span>  
 <span data-ttu-id="f9a47-166">Aşağıdaki kod, eşler arası bir senaryoda kullanılan sertifikanın nasıl bulunacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f9a47-166">The following code specifies how to find the certificate used in a peer-to-peer scenario.</span></span>  
  
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
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="f9a47-167">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9a47-167">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>
- <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>
- [<span data-ttu-id="f9a47-168">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="f9a47-168">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="f9a47-169">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="f9a47-169">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="f9a47-170">[Eş kanal Iletisi kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="f9a47-170">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="f9a47-171">[Eş kanal özel kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="f9a47-171">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="f9a47-172">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="f9a47-172">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
