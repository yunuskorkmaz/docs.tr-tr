---
title: <certificate> Öğesi
ms.date: 03/30/2017
ms.assetid: 9b3d9233-ef35-477a-bf5d-efd1e80a52f4
ms.openlocfilehash: e28e7d16073a56f3b6126439644bfff86c9af18b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400548"
---
# <a name="certificate-element"></a><span data-ttu-id="16966-102">\<certificate> Öğesi</span><span class="sxs-lookup"><span data-stu-id="16966-102">\<certificate> Element</span></span>
<span data-ttu-id="16966-103">Eşler arası istemciler için ileti imzalama ve şifreleme için kullanılacak bir X. 509.952 sertifikası belirtir.</span><span class="sxs-lookup"><span data-stu-id="16966-103">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="16966-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="16966-104">Syntax</span></span>  
  
```xml  
<certificate findValue="String"
             storeLocation="LocalMachine/CurrentUser"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="16966-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="16966-105">Attributes and Elements</span></span>  
 <span data-ttu-id="16966-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="16966-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="16966-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="16966-107">Attributes</span></span>  
  
|<span data-ttu-id="16966-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="16966-108">Attribute</span></span>|<span data-ttu-id="16966-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16966-109">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="16966-110">X. 509.440 sertifika deposunda aranacak değeri içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="16966-110">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="16966-111">Özniteliğinde yer alan türün, belirtilen gereksinimleri karşılaması gerekir `x509FindType` .</span><span class="sxs-lookup"><span data-stu-id="16966-111">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="16966-112">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="16966-112">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="16966-113">İstemcinin eşin sertifikasını doğrulamak için kullandığı X. 509.952 sertifika deposunun konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="16966-113">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="16966-114">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="16966-114">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="16966-115">-LocalMachine: yerel makineye atanan sertifika depolama alanı.</span><span class="sxs-lookup"><span data-stu-id="16966-115">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="16966-116">-CurrentUser: geçerli kullanıcıya atanmış sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="16966-116">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="16966-117">Varsayılan değer LocalMachine 'dir.</span><span class="sxs-lookup"><span data-stu-id="16966-117">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="16966-118">Açılacak X. 509.440 sertifika deposunun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="16966-118">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="16966-119">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="16966-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="16966-120">-AddressBook: diğer kullanıcılar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="16966-120">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="16966-121">-AuthRoot: üçüncü taraf sertifika yetkilileri (CA 'Lar) için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="16966-121">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="16966-122">-CertificateAuthority: ara sertifika yetkilileri (CA 'Lar) için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="16966-122">-   CertificateAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="16966-123">-İzin verilmeyen: iptal edilen sertifikalar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="16966-123">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="16966-124">-My: kişisel sertifikalar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="16966-124">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="16966-125">-Root: güvenilen kök sertifika yetkilileri (CA 'Lar) için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="16966-125">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="16966-126">-Trustedkişiler: doğrudan güvenilen kişiler ve kaynaklar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="16966-126">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="16966-127">-TrustedPublisher: doğrudan güvenilen yayımcılar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="16966-127">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="16966-128">Varsayılan My şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="16966-128">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="16966-129">Yürütülecek X. 509.440 aramasının türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="16966-129">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="16966-130">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="16966-130">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="16966-131">-Findbyparmak Izi</span><span class="sxs-lookup"><span data-stu-id="16966-131">-   FindByThumbPrint</span></span><br /><span data-ttu-id="16966-132">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="16966-132">-   FindBySubjectName</span></span><br /><span data-ttu-id="16966-133">- FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="16966-133">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="16966-134">-FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="16966-134">-   FindByIssuerName</span></span><br /><span data-ttu-id="16966-135">- FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="16966-135">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="16966-136">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="16966-136">-   FindBySerialNumber</span></span><br /><span data-ttu-id="16966-137">-FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="16966-137">-   FindByTimeValid</span></span><br /><span data-ttu-id="16966-138">-FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="16966-138">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="16966-139">-FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="16966-139">-   FindByTemplateName</span></span><br /><span data-ttu-id="16966-140">- FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="16966-140">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="16966-141">-FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="16966-141">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="16966-142">-FindByExtension</span><span class="sxs-lookup"><span data-stu-id="16966-142">-   FindByExtension</span></span><br /><span data-ttu-id="16966-143">-FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="16966-143">-   FindByKeyUsage</span></span><br /><span data-ttu-id="16966-144">-FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="16966-144">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="16966-145">Özniteliğinde yer alan türün, `findValue` belirtilen gereksinimleri karşılaması gerekir `X509FindType` .</span><span class="sxs-lookup"><span data-stu-id="16966-145">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="16966-146">Varsayılan değer FindBySubjectDistinguishedName ' dir.</span><span class="sxs-lookup"><span data-stu-id="16966-146">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="16966-147">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="16966-147">Child Elements</span></span>  
 <span data-ttu-id="16966-148">Yok.</span><span class="sxs-lookup"><span data-stu-id="16966-148">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="16966-149">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="16966-149">Parent Elements</span></span>  
  
|<span data-ttu-id="16966-150">Öğe</span><span class="sxs-lookup"><span data-stu-id="16966-150">Element</span></span>|<span data-ttu-id="16966-151">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16966-151">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="16966-152">Eşler arası istemcilerin kimlik doğrulaması sırasında kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="16966-152">Specifies credentials used when authenticating peer-to-peer clients.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16966-153">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="16966-153">Remarks</span></span>  
 <span data-ttu-id="16966-154">Bu yapılandırma öğesi, eş kafeste komşuları doğrulanırken kullanılan bir X509Certificate2 örneği içeriyor.</span><span class="sxs-lookup"><span data-stu-id="16966-154">This configuration element contains a X509Certificate2 instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="16966-155">Eşler arası programlama hakkında daha fazla bilgi için bkz. eşler [arası ağ iletişimi](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="16966-155">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="16966-156">Örnek</span><span class="sxs-lookup"><span data-stu-id="16966-156">Example</span></span>  
 <span data-ttu-id="16966-157">Aşağıdaki kod, eşler arası bir senaryoda kullanılan sertifikanın nasıl bulunacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="16966-157">The following code specifies how to find the certificate used in a peer-to-peer scenario.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="16966-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16966-158">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>
- <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>
- [<span data-ttu-id="16966-159">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="16966-159">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="16966-160">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="16966-160">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="16966-161">[Eş kanal Iletisi kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="16966-161">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="16966-162">[Eş kanal özel kimlik doğrulaması](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="16966-162">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="16966-163">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="16966-163">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
