---
title: <certificate><clientCertificate>öğesinin
ms.date: 03/30/2017
ms.assetid: 00297efb-a7f2-4e03-bc2b-943d545610fc
ms.openlocfilehash: 35ea3814e208921abaf44e6ef431c4e1b44cde60
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151148"
---
# <a name="certificate-of-clientcertificate-element"></a><span data-ttu-id="27c0b-102">\<certificate>\<clientCertificate>öğesinin</span><span class="sxs-lookup"><span data-stu-id="27c0b-102">\<certificate> of \<clientCertificate> Element</span></span>

<span data-ttu-id="27c0b-103">İletileri imzalamak ve şifrelemek için kullanılan bir X. 509.440 sertifikası belirtir.</span><span class="sxs-lookup"><span data-stu-id="27c0b-103">Specifies an X.509 certificate used to sign and encrypt messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCertificate>**](clientcertificate-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="27c0b-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="27c0b-104">Syntax</span></span>  
  
```xml  
<certificate findValue="String"
             storeLocation = "CurrentUser/LocalMachine"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="27c0b-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="27c0b-105">Attributes and Elements</span></span>  

 <span data-ttu-id="27c0b-106">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="27c0b-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="27c0b-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="27c0b-107">Attributes</span></span>  
  
|<span data-ttu-id="27c0b-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="27c0b-108">Attribute</span></span>|<span data-ttu-id="27c0b-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27c0b-109">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="27c0b-110">X. 509.440 sertifika deposunda aranacak değeri içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="27c0b-110">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="27c0b-111">Özniteliğinde yer alan türün belirtilen X509FindType gereksinimlerini karşılaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="27c0b-111">The type contained in the attribute must satisfy the requirements of the specified X509FindType.</span></span> <span data-ttu-id="27c0b-112">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="27c0b-112">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="27c0b-113">İstemcinin sunucusunun sertifikasını doğrulamak için kullandığı X. 509.952 sertifika deposunun konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="27c0b-113">Specifies the location of the X.509 certificate store that the client uses to validate the server’s certificate against.</span></span> <span data-ttu-id="27c0b-114">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="27c0b-114">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="27c0b-115">-LocalMachine: yerel makineye atanan sertifika depolama alanı.</span><span class="sxs-lookup"><span data-stu-id="27c0b-115">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="27c0b-116">-CurrentUser: geçerli kullanıcıya atanmış sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="27c0b-116">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="27c0b-117">Varsayılan değer LocalMachine 'dir.</span><span class="sxs-lookup"><span data-stu-id="27c0b-117">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="27c0b-118">Açılacak X. 509.440 sertifika deposunun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="27c0b-118">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="27c0b-119">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="27c0b-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="27c0b-120">-AddressBook: diğer kullanıcılar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="27c0b-120">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="27c0b-121">-AuthRoot: üçüncü taraf sertifika yetkilileri (CA 'Lar) için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="27c0b-121">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="27c0b-122">-CertificationAuthority: ara sertifika yetkilileri (CA 'Lar) için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="27c0b-122">-   CertificationAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="27c0b-123">-İzin verilmeyen: iptal edilen sertifikalar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="27c0b-123">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="27c0b-124">-My: kişisel sertifikalar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="27c0b-124">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="27c0b-125">-Root: güvenilen kök sertifika yetkilileri (CA 'Lar) için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="27c0b-125">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="27c0b-126">-Trustedkişiler: doğrudan güvenilen kişiler ve kaynaklar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="27c0b-126">-   TrustedPeople: Certificate store for directly trusted people and resources.</span></span><br /><span data-ttu-id="27c0b-127">-TrustedPublisher: doğrudan güvenilen yayımcılar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="27c0b-127">-   TrustedPublisher: Certificate store for directly trusted publishers.</span></span><br /><br /> <span data-ttu-id="27c0b-128">Varsayılan My şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="27c0b-128">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="27c0b-129">Yürütülecek X. 509.440 aramasının türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="27c0b-129">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="27c0b-130">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="27c0b-130">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="27c0b-131">-Findbyparmak Izi</span><span class="sxs-lookup"><span data-stu-id="27c0b-131">-   FindByThumbPrint</span></span><br /><span data-ttu-id="27c0b-132">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="27c0b-132">-   FindBySubjectName</span></span><br /><span data-ttu-id="27c0b-133">- FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="27c0b-133">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="27c0b-134">-FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="27c0b-134">-   FindByIssuerName</span></span><br /><span data-ttu-id="27c0b-135">- FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="27c0b-135">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="27c0b-136">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="27c0b-136">-   FindBySerialNumber</span></span><br /><span data-ttu-id="27c0b-137">-FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="27c0b-137">-   FindByTimeValid</span></span><br /><span data-ttu-id="27c0b-138">-FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="27c0b-138">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="27c0b-139">-FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="27c0b-139">-   FindByTemplateName</span></span><br /><span data-ttu-id="27c0b-140">- FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="27c0b-140">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="27c0b-141">-FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="27c0b-141">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="27c0b-142">-FindByExtension</span><span class="sxs-lookup"><span data-stu-id="27c0b-142">-   FindByExtension</span></span><br /><span data-ttu-id="27c0b-143">-FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="27c0b-143">-   FindByKeyUsage</span></span><br /><span data-ttu-id="27c0b-144">-FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="27c0b-144">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="27c0b-145">Özniteliğinde yer alan türün `findValue` belirtilen X509FindType gereksinimlerini karşılaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="27c0b-145">The type contained in the `findValue` attribute must satisfy the requirements of the specified X509FindType.</span></span><br /><br /> <span data-ttu-id="27c0b-146">Varsayılan değer FindBySubjectDistinguishedName ' dir.</span><span class="sxs-lookup"><span data-stu-id="27c0b-146">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="27c0b-147">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="27c0b-147">Child Elements</span></span>  

 <span data-ttu-id="27c0b-148">Yok.</span><span class="sxs-lookup"><span data-stu-id="27c0b-148">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="27c0b-149">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="27c0b-149">Parent Elements</span></span>  
  
|<span data-ttu-id="27c0b-150">Öğe</span><span class="sxs-lookup"><span data-stu-id="27c0b-150">Element</span></span>|<span data-ttu-id="27c0b-151">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27c0b-151">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-servicecredentials.md)||  
  
## <a name="remarks"></a><span data-ttu-id="27c0b-152">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="27c0b-152">Remarks</span></span>  

 <span data-ttu-id="27c0b-153">`<certificate>`İstemci ile güvenli iletişim kurmak için hizmetin istemci sertifikasının önceden olması gerektiğinde öğesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="27c0b-153">The `<certificate>` element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="27c0b-154">Bu, çift yönlü iletişim deseninin kullanıldığı durumlarda oluşur.</span><span class="sxs-lookup"><span data-stu-id="27c0b-154">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="27c0b-155">Daha tipik istek/yanıt modelinde istemci, isteğin sertifikasını istemciye geri yanıtını şifrelemek ve imzalamak için kullandığı isteği içerir.</span><span class="sxs-lookup"><span data-stu-id="27c0b-155">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="27c0b-156">Çift yönlü iletişim modelinde, hizmette istemciden bir istek yoktur ve bu nedenle iletinin istemciye güvenmesi için istemcinin sertifikasının önceden olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="27c0b-156">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="27c0b-157">Bu nedenle, istemcinin sertifikasını bant dışı bir anlaşmede edinmeniz ve bu öğeyi kullanarak sertifikayı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="27c0b-157">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="27c0b-158">Çift yönlü hizmetler hakkında daha fazla bilgi için bkz. [nasıl yapılır: çift yönlü sözleşme oluşturma](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="27c0b-158">For more information about duplex services, see [How to: Create a Duplex Contract](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="27c0b-159">Örnek</span><span class="sxs-lookup"><span data-stu-id="27c0b-159">Example</span></span>  

 <span data-ttu-id="27c0b-160">Aşağıdaki kod, öğesinde uygun bir X. 509.952 sertifikası ve özel bir doğrulama türü bulmayı belirtir `<authentication>` .</span><span class="sxs-lookup"><span data-stu-id="27c0b-160">The following code specifies how to find an appropriate X.509 certificate and a custom validation type in the `<authentication>` element.</span></span>  
  
```xml  
<serviceBehaviors>
  <behavior name="myServiceBehavior">
    <clientCertificate>
      <certificate findValue="www.cohowinery.com"
                   storeLocation="CurrentUser"
                   storeName="TrustedPeople"
                   x509FindType="FindByIssuerName" />
      <authentication customCertificateValidatorType="MyTypes.Coho"
                      certificateValidationMode="Custom"
                      revocationMode="Offline"
                      includeWindowsGroups="false"
                      mapClientCertificateToWindowsAccount="true" />
    </clientCertificate>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="27c0b-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27c0b-161">See also</span></span>

- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509ClientCertificateCredentialsElement>
- [<span data-ttu-id="27c0b-162">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="27c0b-162">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="27c0b-163">Nasıl yapılır: Özel Bir Sertifika Doğrulayıcı Kullanan Bir Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="27c0b-163">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [<span data-ttu-id="27c0b-164">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="27c0b-164">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
