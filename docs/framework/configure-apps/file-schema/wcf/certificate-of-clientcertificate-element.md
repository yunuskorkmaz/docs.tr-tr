---
description: 'Hakkında daha fazla bilgi edinin: <certificate> <clientCertificate> öğe'
title: <certificate><clientCertificate>öğesinin
ms.date: 03/30/2017
ms.assetid: 00297efb-a7f2-4e03-bc2b-943d545610fc
ms.openlocfilehash: a677c04055016c77794dd99a8c237b5eb6c13f5f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639100"
---
# <a name="certificate-of-clientcertificate-element"></a><span data-ttu-id="b31eb-103">\<certificate>\<clientCertificate>öğesinin</span><span class="sxs-lookup"><span data-stu-id="b31eb-103">\<certificate> of \<clientCertificate> Element</span></span>

<span data-ttu-id="b31eb-104">İletileri imzalamak ve şifrelemek için kullanılan bir X. 509.440 sertifikası belirtir.</span><span class="sxs-lookup"><span data-stu-id="b31eb-104">Specifies an X.509 certificate used to sign and encrypt messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCertificate>**](clientcertificate-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="b31eb-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="b31eb-105">Syntax</span></span>  
  
```xml  
<certificate findValue="String"
             storeLocation = "CurrentUser/LocalMachine"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b31eb-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b31eb-106">Attributes and Elements</span></span>  

 <span data-ttu-id="b31eb-107">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="b31eb-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b31eb-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b31eb-108">Attributes</span></span>  
  
|<span data-ttu-id="b31eb-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b31eb-109">Attribute</span></span>|<span data-ttu-id="b31eb-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b31eb-110">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="b31eb-111">X. 509.440 sertifika deposunda aranacak değeri içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="b31eb-111">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="b31eb-112">Özniteliğinde yer alan türün belirtilen X509FindType gereksinimlerini karşılaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b31eb-112">The type contained in the attribute must satisfy the requirements of the specified X509FindType.</span></span> <span data-ttu-id="b31eb-113">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="b31eb-113">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="b31eb-114">İstemcinin sunucusunun sertifikasını doğrulamak için kullandığı X. 509.952 sertifika deposunun konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b31eb-114">Specifies the location of the X.509 certificate store that the client uses to validate the server’s certificate against.</span></span> <span data-ttu-id="b31eb-115">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b31eb-115">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b31eb-116">-LocalMachine: yerel makineye atanan sertifika depolama alanı.</span><span class="sxs-lookup"><span data-stu-id="b31eb-116">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="b31eb-117">-CurrentUser: geçerli kullanıcıya atanmış sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="b31eb-117">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="b31eb-118">Varsayılan değer LocalMachine 'dir.</span><span class="sxs-lookup"><span data-stu-id="b31eb-118">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="b31eb-119">Açılacak X. 509.440 sertifika deposunun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b31eb-119">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="b31eb-120">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b31eb-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b31eb-121">-AddressBook: diğer kullanıcılar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="b31eb-121">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="b31eb-122">-AuthRoot: üçüncü taraf sertifika yetkilileri (CA 'Lar) için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="b31eb-122">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="b31eb-123">-CertificationAuthority: ara sertifika yetkilileri (CA 'Lar) için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="b31eb-123">-   CertificationAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="b31eb-124">-İzin verilmeyen: iptal edilen sertifikalar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="b31eb-124">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="b31eb-125">-My: kişisel sertifikalar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="b31eb-125">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="b31eb-126">-Root: güvenilen kök sertifika yetkilileri (CA 'Lar) için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="b31eb-126">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="b31eb-127">-Trustedkişiler: doğrudan güvenilen kişiler ve kaynaklar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="b31eb-127">-   TrustedPeople: Certificate store for directly trusted people and resources.</span></span><br /><span data-ttu-id="b31eb-128">-TrustedPublisher: doğrudan güvenilen yayımcılar için sertifika deposu.</span><span class="sxs-lookup"><span data-stu-id="b31eb-128">-   TrustedPublisher: Certificate store for directly trusted publishers.</span></span><br /><br /> <span data-ttu-id="b31eb-129">Varsayılan My şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="b31eb-129">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="b31eb-130">Yürütülecek X. 509.440 aramasının türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b31eb-130">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="b31eb-131">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b31eb-131">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b31eb-132">-Findbyparmak Izi</span><span class="sxs-lookup"><span data-stu-id="b31eb-132">-   FindByThumbPrint</span></span><br /><span data-ttu-id="b31eb-133">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="b31eb-133">-   FindBySubjectName</span></span><br /><span data-ttu-id="b31eb-134">- FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="b31eb-134">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="b31eb-135">-FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="b31eb-135">-   FindByIssuerName</span></span><br /><span data-ttu-id="b31eb-136">- FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="b31eb-136">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="b31eb-137">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="b31eb-137">-   FindBySerialNumber</span></span><br /><span data-ttu-id="b31eb-138">-FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="b31eb-138">-   FindByTimeValid</span></span><br /><span data-ttu-id="b31eb-139">-FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="b31eb-139">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="b31eb-140">-FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="b31eb-140">-   FindByTemplateName</span></span><br /><span data-ttu-id="b31eb-141">- FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="b31eb-141">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="b31eb-142">-FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="b31eb-142">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="b31eb-143">-FindByExtension</span><span class="sxs-lookup"><span data-stu-id="b31eb-143">-   FindByExtension</span></span><br /><span data-ttu-id="b31eb-144">-FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="b31eb-144">-   FindByKeyUsage</span></span><br /><span data-ttu-id="b31eb-145">-FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="b31eb-145">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="b31eb-146">Özniteliğinde yer alan türün `findValue` belirtilen X509FindType gereksinimlerini karşılaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b31eb-146">The type contained in the `findValue` attribute must satisfy the requirements of the specified X509FindType.</span></span><br /><br /> <span data-ttu-id="b31eb-147">Varsayılan değer FindBySubjectDistinguishedName ' dir.</span><span class="sxs-lookup"><span data-stu-id="b31eb-147">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b31eb-148">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b31eb-148">Child Elements</span></span>  

 <span data-ttu-id="b31eb-149">Yok.</span><span class="sxs-lookup"><span data-stu-id="b31eb-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b31eb-150">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b31eb-150">Parent Elements</span></span>  
  
|<span data-ttu-id="b31eb-151">Öğe</span><span class="sxs-lookup"><span data-stu-id="b31eb-151">Element</span></span>|<span data-ttu-id="b31eb-152">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b31eb-152">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-servicecredentials.md)||  
  
## <a name="remarks"></a><span data-ttu-id="b31eb-153">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b31eb-153">Remarks</span></span>  

 <span data-ttu-id="b31eb-154">`<certificate>`İstemci ile güvenli iletişim kurmak için hizmetin istemci sertifikasının önceden olması gerektiğinde öğesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b31eb-154">The `<certificate>` element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="b31eb-155">Bu, çift yönlü iletişim deseninin kullanıldığı durumlarda oluşur.</span><span class="sxs-lookup"><span data-stu-id="b31eb-155">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="b31eb-156">Daha tipik istek/yanıt modelinde istemci, isteğin sertifikasını istemciye geri yanıtını şifrelemek ve imzalamak için kullandığı isteği içerir.</span><span class="sxs-lookup"><span data-stu-id="b31eb-156">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="b31eb-157">Çift yönlü iletişim modelinde, hizmette istemciden bir istek yoktur ve bu nedenle iletinin istemciye güvenmesi için istemcinin sertifikasının önceden olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b31eb-157">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="b31eb-158">Bu nedenle, istemcinin sertifikasını bant dışı bir anlaşmede edinmeniz ve bu öğeyi kullanarak sertifikayı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b31eb-158">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="b31eb-159">Çift yönlü hizmetler hakkında daha fazla bilgi için bkz. [nasıl yapılır: çift yönlü sözleşme oluşturma](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="b31eb-159">For more information about duplex services, see [How to: Create a Duplex Contract](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b31eb-160">Örnek</span><span class="sxs-lookup"><span data-stu-id="b31eb-160">Example</span></span>  

 <span data-ttu-id="b31eb-161">Aşağıdaki kod, öğesinde uygun bir X. 509.952 sertifikası ve özel bir doğrulama türü bulmayı belirtir `<authentication>` .</span><span class="sxs-lookup"><span data-stu-id="b31eb-161">The following code specifies how to find an appropriate X.509 certificate and a custom validation type in the `<authentication>` element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b31eb-162">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b31eb-162">See also</span></span>

- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509ClientCertificateCredentialsElement>
- [<span data-ttu-id="b31eb-163">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="b31eb-163">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="b31eb-164">Nasıl yapılır: Özel Bir Sertifika Doğrulayıcı Kullanan Bir Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b31eb-164">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [<span data-ttu-id="b31eb-165">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="b31eb-165">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
