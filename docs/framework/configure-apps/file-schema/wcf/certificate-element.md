---
title: <certificate> Öğesi
ms.date: 03/30/2017
ms.assetid: 9b3d9233-ef35-477a-bf5d-efd1e80a52f4
ms.openlocfilehash: 8cc0404a5896dd23cffce6f1f77b91a2f01f23d2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151096"
---
# <a name="certificate-element"></a><span data-ttu-id="ce062-102">\<certificate> Öğesi</span><span class="sxs-lookup"><span data-stu-id="ce062-102">\<certificate> Element</span></span>

<span data-ttu-id="ce062-103">Eşler arası istemciler için ileti imzalama ve şifreleme için kullanılacak bir X. 509.952 sertifikası belirtir.</span><span class="sxs-lookup"><span data-stu-id="ce062-103">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="ce062-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="ce062-104">Syntax</span></span>  
  
```xml  
<certificate findValue="String"
             storeLocation="LocalMachine/CurrentUser"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ce062-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ce062-105">Attributes and Elements</span></span>  

 <span data-ttu-id="ce062-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ce062-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ce062-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ce062-107">Attributes</span></span>  
  
|<span data-ttu-id="ce062-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ce062-108">Attribute</span></span>|<span data-ttu-id="ce062-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce062-109">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="ce062-110">X. 509.440 sertifika deposunda aranacak değeri içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="ce062-110">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="ce062-111">Özniteliğinde yer alan türün, belirtilen gereksinimleri karşılaması gerekir `x509FindType` .</span><span class="sxs-lookup"><span data-stu-id="ce062-111">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="ce062-112">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="ce062-112">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="ce062-113">İstemcinin eşin sertifikasını doğrulamak için kullandığı X. 509.952 sertifika deposunun konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ce062-113">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="ce062-114">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ce062-114">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ce062-115">-LocalMachine: yerel makineye atanan sertifika depolama alanı.</span><span class="sxs-lookup"><span data-stu-id="ce062-115">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="ce062-116">-CurrentUser: geçerli kullanıcıya atanmış sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="ce062-116">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="ce062-117">Varsayılan değer LocalMachine 'dir.</span><span class="sxs-lookup"><span data-stu-id="ce062-117">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="ce062-118">Açılacak X. 509.440 sertifika deposunun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ce062-118">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="ce062-119">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ce062-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ce062-120">-AddressBook: diğer kullanıcılar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="ce062-120">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="ce062-121">-AuthRoot: üçüncü taraf sertifika yetkilileri (CA 'Lar) için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="ce062-121">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="ce062-122">-CertificateAuthority: ara sertifika yetkilileri (CA 'Lar) için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="ce062-122">-   CertificateAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="ce062-123">-İzin verilmeyen: iptal edilen sertifikalar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="ce062-123">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="ce062-124">-My: kişisel sertifikalar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="ce062-124">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="ce062-125">-Root: güvenilen kök sertifika yetkilileri (CA 'Lar) için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="ce062-125">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="ce062-126">-Trustedkişiler: doğrudan güvenilen kişiler ve kaynaklar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="ce062-126">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="ce062-127">-TrustedPublisher: doğrudan güvenilen yayımcılar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="ce062-127">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="ce062-128">Varsayılan My şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="ce062-128">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="ce062-129">Yürütülecek X. 509.440 aramasının türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ce062-129">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="ce062-130">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ce062-130">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ce062-131">-Findbyparmak Izi</span><span class="sxs-lookup"><span data-stu-id="ce062-131">-   FindByThumbPrint</span></span><br /><span data-ttu-id="ce062-132">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="ce062-132">-   FindBySubjectName</span></span><br /><span data-ttu-id="ce062-133">- FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="ce062-133">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="ce062-134">-FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="ce062-134">-   FindByIssuerName</span></span><br /><span data-ttu-id="ce062-135">- FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="ce062-135">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="ce062-136">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="ce062-136">-   FindBySerialNumber</span></span><br /><span data-ttu-id="ce062-137">-FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="ce062-137">-   FindByTimeValid</span></span><br /><span data-ttu-id="ce062-138">-FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="ce062-138">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="ce062-139">-FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="ce062-139">-   FindByTemplateName</span></span><br /><span data-ttu-id="ce062-140">- FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="ce062-140">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="ce062-141">-FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="ce062-141">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="ce062-142">-FindByExtension</span><span class="sxs-lookup"><span data-stu-id="ce062-142">-   FindByExtension</span></span><br /><span data-ttu-id="ce062-143">-FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="ce062-143">-   FindByKeyUsage</span></span><br /><span data-ttu-id="ce062-144">-FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="ce062-144">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="ce062-145">Özniteliğinde yer alan türün, `findValue` belirtilen gereksinimleri karşılaması gerekir `X509FindType` .</span><span class="sxs-lookup"><span data-stu-id="ce062-145">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="ce062-146">Varsayılan değer FindBySubjectDistinguishedName ' dir.</span><span class="sxs-lookup"><span data-stu-id="ce062-146">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ce062-147">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ce062-147">Child Elements</span></span>  

 <span data-ttu-id="ce062-148">Yok.</span><span class="sxs-lookup"><span data-stu-id="ce062-148">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ce062-149">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ce062-149">Parent Elements</span></span>  
  
|<span data-ttu-id="ce062-150">Öğe</span><span class="sxs-lookup"><span data-stu-id="ce062-150">Element</span></span>|<span data-ttu-id="ce062-151">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce062-151">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="ce062-152">Eşler arası istemcilerin kimlik doğrulaması sırasında kullanılan kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ce062-152">Specifies credentials used when authenticating peer-to-peer clients.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce062-153">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ce062-153">Remarks</span></span>  

 <span data-ttu-id="ce062-154">Bu yapılandırma öğesi, eş kafeste komşuları doğrulanırken kullanılan bir X509Certificate2 örneği içeriyor.</span><span class="sxs-lookup"><span data-stu-id="ce062-154">This configuration element contains a X509Certificate2 instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="ce062-155">Eşler arası programlama hakkında daha fazla bilgi için bkz. eşler [arası ağ iletişimi](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="ce062-155">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce062-156">Örnek</span><span class="sxs-lookup"><span data-stu-id="ce062-156">Example</span></span>  

 <span data-ttu-id="ce062-157">Aşağıdaki kod, eşler arası bir senaryoda kullanılan sertifikanın nasıl bulunacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ce062-157">The following code specifies how to find the certificate used in a peer-to-peer scenario.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ce062-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce062-158">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>
- <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>
- [<span data-ttu-id="ce062-159">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="ce062-159">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="ce062-160">Eşler Arası Ağ</span><span class="sxs-lookup"><span data-stu-id="ce062-160">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="ce062-161">[Eş kanal Iletisi kimlik doğrulaması](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="ce062-161">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="ce062-162">[Eş kanal özel kimlik doğrulaması](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="ce062-162">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="ce062-163">Eş Kanalı Uygulamalarını Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="ce062-163">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
