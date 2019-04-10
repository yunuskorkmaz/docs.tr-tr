---
title: 'Nasıl yapılır: Özel Bir Sertifika Doğrulayıcı Kullanan Bir Hizmet Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: bb0190ff-0738-4e54-8d22-c97d343708bf
ms.openlocfilehash: b7e8e4a750aadd8a84a57cdf22c01f6b91e6256c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59296556"
---
# <a name="how-to-create-a-service-that-employs-a-custom-certificate-validator"></a><span data-ttu-id="5db22-102">Nasıl yapılır: Özel Bir Sertifika Doğrulayıcı Kullanan Bir Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5db22-102">How to: Create a Service that Employs a Custom Certificate Validator</span></span>
<span data-ttu-id="5db22-103">Bu konuda, özel bir sertifika Doğrulayıcı uygulama ve varsayılan sertifika doğrulama mantığı ile özel bir sertifika Doğrulayıcı değiştirmek için istemci veya hizmet kimlik bilgilerinin nasıl yapılandırılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5db22-103">This topic shows how to implement a custom certificate validator and how to configure client or service credentials to replace the default certificate validation logic with the custom certificate validator.</span></span>  
  
 <span data-ttu-id="5db22-104">X.509 Sertifika bir istemci veya hizmetin kimliğini doğrulamak için kullanılıyorsa, Windows Communication Foundation (WCF) varsayılan olarak Windows sertifika deposu ve şifreleme API'si günlük kaydını güvenilir olduğundan emin olun ve sertifikayı doğrulamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="5db22-104">If the X.509 certificate is used to authenticate a client or service, Windows Communication Foundation (WCF) by default uses the Windows certificate store and Crypto API to validate the certificate and to ensure that it is trusted.</span></span> <span data-ttu-id="5db22-105">Bazen yerleşik sertifika doğrulama işlevselliği yeterli değildir ve değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5db22-105">Sometimes the built-in certificate validation functionality is not enough and must be changed.</span></span> <span data-ttu-id="5db22-106">WCF özel bir sertifika Doğrulayıcı ekleme olanak tanıyarak Doğrulama mantığı değiştirmek için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="5db22-106">WCF provides an easy way to change the validation logic by allowing users to add a custom certificate validator.</span></span> <span data-ttu-id="5db22-107">Özel bir sertifika Doğrulayıcı belirtilirse, WCF yerleşik Sertifika Doğrulama mantığı kullanmaz, ancak bunun yerine özel doğrulayıcısındaki kullanır.</span><span class="sxs-lookup"><span data-stu-id="5db22-107">If a custom certificate validator is specified, WCF does not use the built-in certificate validation logic but relies on the custom validator instead.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="5db22-108">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="5db22-108">Procedures</span></span>  
  
#### <a name="to-create-a-custom-certificate-validator"></a><span data-ttu-id="5db22-109">Özel bir sertifika Doğrulayıcı oluşturma</span><span class="sxs-lookup"><span data-stu-id="5db22-109">To create a custom certificate validator</span></span>  
  
1. <span data-ttu-id="5db22-110">Türetilmiş yeni bir sınıf tanımlama <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="5db22-110">Define a new class derived from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span>  
  
2. <span data-ttu-id="5db22-111">Özet uygulama <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5db22-111">Implement the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> method.</span></span> <span data-ttu-id="5db22-112">Doğrulanması gereken sertifikayı yönteme bağımsız değişken olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="5db22-112">The certificate that must be validated is passed as an argument to the method.</span></span> <span data-ttu-id="5db22-113">Geçirilen sertifika doğrulama mantığı göre geçerli değilse, bu yöntemin oluşturduğu bir <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>.</span><span class="sxs-lookup"><span data-stu-id="5db22-113">If the passed certificate is not valid according to the validation logic, this method throws a <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>.</span></span> <span data-ttu-id="5db22-114">Sertifika geçerliyse, metodu çağırana döner.</span><span class="sxs-lookup"><span data-stu-id="5db22-114">If the certificate is valid, the method returns to the caller.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5db22-115">Kimlik doğrulama hataları istemciye geri dönmek için throw bir <xref:System.ServiceModel.FaultException> içinde <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5db22-115">To return authentication errors back to the client, throw a <xref:System.ServiceModel.FaultException> in the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>  
  
 [!code-csharp[c_CustomCertificateValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#2)]
 [!code-vb[c_CustomCertificateValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#2)]  
  
#### <a name="to-specify-a-custom-certificate-validator-in-service-configuration"></a><span data-ttu-id="5db22-116">Hizmet yapılandırmasında özel bir sertifika Doğrulayıcı belirtmek için</span><span class="sxs-lookup"><span data-stu-id="5db22-116">To specify a custom certificate validator in service configuration</span></span>  
  
1. <span data-ttu-id="5db22-117">Ekleme bir [ \<davranışları >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) öğesi ve bir [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) için [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="5db22-117">Add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element and a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2. <span data-ttu-id="5db22-118">Ekleme bir [ \<davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) ayarlayıp `name` özniteliği için uygun bir değer.</span><span class="sxs-lookup"><span data-stu-id="5db22-118">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>  
  
3. <span data-ttu-id="5db22-119">Ekleme bir [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) için `<behavior>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="5db22-119">Add a [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) to the `<behavior>` element.</span></span>  
  
4. <span data-ttu-id="5db22-120">Ekleme bir `<clientCertificate>` öğesine `<serviceCredentials>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="5db22-120">Add a `<clientCertificate>` element to the `<serviceCredentials>` element.</span></span>  
  
5. <span data-ttu-id="5db22-121">Ekleme bir [ \<kimlik doğrulama >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) için `<clientCertificate>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="5db22-121">Add an [\<authentication>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) to the `<clientCertificate>` element.</span></span>  
  
6. <span data-ttu-id="5db22-122">Ayarlama `customCertificateValidatorType` öznitelik için Doğrulayıcı türü.</span><span class="sxs-lookup"><span data-stu-id="5db22-122">Set the `customCertificateValidatorType` attribute to the validator type.</span></span> <span data-ttu-id="5db22-123">Aşağıdaki örnekte, öznitelik ad alanı ve tür adını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5db22-123">The following example sets the attribute to the namespace and name of the type.</span></span>  
  
7. <span data-ttu-id="5db22-124">Ayarlama `certificateValidationMode` özniteliğini `Custom`.</span><span class="sxs-lookup"><span data-stu-id="5db22-124">Set the `certificateValidationMode` attribute to `Custom`.</span></span>  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
       <serviceBehaviors>  
        <behavior name="ServiceBehavior">  
         <serviceCredentials>  
          <clientCertificate>  
          <authentication certificateValidationMode="Custom" customCertificateValidatorType="Samples.MyValidator, service" />  
          </clientCertificate>  
         </serviceCredentials>  
        </behavior>  
       </serviceBehaviors>  
      </behaviors>  
    </system.serviceModel>  
    </configuration>  
    ```  
  
#### <a name="to-specify-a-custom-certificate-validator-using-configuration-on-the-client"></a><span data-ttu-id="5db22-125">İstemcide yapılandırmayı kullanarak özel bir sertifika Doğrulayıcı belirtmek için</span><span class="sxs-lookup"><span data-stu-id="5db22-125">To specify a custom certificate validator using configuration on the client</span></span>  
  
1. <span data-ttu-id="5db22-126">Ekleme bir [ \<davranışları >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) öğesi ve bir [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) için [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="5db22-126">Add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element and a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2. <span data-ttu-id="5db22-127">Ekleme bir [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="5db22-127">Add an [\<endpointBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) element.</span></span>  
  
3. <span data-ttu-id="5db22-128">Ekleme bir `<behavior>` öğesi ve kümesi `name` özniteliği için uygun bir değer.</span><span class="sxs-lookup"><span data-stu-id="5db22-128">Add a `<behavior>` element and set the `name` attribute to an appropriate value.</span></span>  
  
4. <span data-ttu-id="5db22-129">Ekleme bir [ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="5db22-129">Add a [\<clientCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element.</span></span>  
  
5. <span data-ttu-id="5db22-130">Ekleme bir [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md).</span><span class="sxs-lookup"><span data-stu-id="5db22-130">Add a [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md).</span></span>  
  
6. <span data-ttu-id="5db22-131">Ekleme bir [ \<kimlik doğrulama >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) üzerinde aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="5db22-131">Add an [\<authentication>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) as shown on the following example.</span></span>  
  
7. <span data-ttu-id="5db22-132">Ayarlama `customCertificateValidatorType` öznitelik için Doğrulayıcı türü.</span><span class="sxs-lookup"><span data-stu-id="5db22-132">Set the `customCertificateValidatorType` attribute to the validator type.</span></span>  
  
8. <span data-ttu-id="5db22-133">Ayarlama `certificateValidationMode` özniteliğini `Custom`.</span><span class="sxs-lookup"><span data-stu-id="5db22-133">Set the `certificateValidationMode` attribute to `Custom`.</span></span> <span data-ttu-id="5db22-134">Aşağıdaki örnekte, öznitelik ad alanı ve tür adını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5db22-134">The following example sets the attribute to the namespace and name of the type.</span></span>  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
       <endpointBehaviors>  
        <behavior name="clientBehavior">  
         <clientCredentials>  
          <serviceCertificate>  
           <authentication certificateValidationMode="Custom"   
                  customCertificateValidatorType=  
             "Samples.CustomX509CertificateValidator, client"/>  
          </serviceCertificate>  
         </clientCredentials>  
        </behavior>  
       </endpointBehaviors>  
      </behaviors>  
     </system.serviceModel>  
    </configuration>  
    ```  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-service"></a><span data-ttu-id="5db22-135">Hizmette kod kullanarak özel bir sertifika Doğrulayıcı belirtmek için</span><span class="sxs-lookup"><span data-stu-id="5db22-135">To specify a custom certificate validator using code on the service</span></span>  
  
1. <span data-ttu-id="5db22-136">Özel bir sertifika Doğrulayıcı belirtin <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="5db22-136">Specify the custom certificate validator on the <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> property.</span></span> <span data-ttu-id="5db22-137">Hizmet kimlik bilgilerini kullanarak erişebileceğiniz <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="5db22-137">You can access the service credentials using the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property.</span></span>  
  
2. <span data-ttu-id="5db22-138">Ayarlama <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> özelliğini <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="5db22-138">Set the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> property to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span></span>  
  
 [!code-csharp[c_CustomCertificateValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#1)]
 [!code-vb[c_CustomCertificateValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#1)]  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-client"></a><span data-ttu-id="5db22-139">İstemcide kod kullanarak özel bir sertifika Doğrulayıcı belirtmek için</span><span class="sxs-lookup"><span data-stu-id="5db22-139">To specify a custom certificate validator using code on the client</span></span>  
  
1. <span data-ttu-id="5db22-140">Kullanarak özel bir sertifika Doğrulayıcı belirtin <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="5db22-140">Specify the custom certificate validator using the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> property.</span></span> <span data-ttu-id="5db22-141">İstemci kimlik bilgileri ile erişebileceğiniz <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="5db22-141">You can access the client credentials using the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property.</span></span> <span data-ttu-id="5db22-142">(Tarafından oluşturulan istemci sınıfını [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) her zaman türetilen <xref:System.ServiceModel.ClientBase%601> sınıfı.)</span><span class="sxs-lookup"><span data-stu-id="5db22-142">(The client class generated by [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) always derives from the <xref:System.ServiceModel.ClientBase%601> class.)</span></span>  
  
2. <span data-ttu-id="5db22-143">Ayarlama <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> özelliğini <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="5db22-143">Set the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> property to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5db22-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="5db22-144">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="5db22-145">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5db22-145">Description</span></span>  
 <span data-ttu-id="5db22-146">Aşağıdaki örnek, hizmette özel bir sertifika Doğrulayıcı ve bunun kullanımını uygulanışı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5db22-146">The following sample shows an implementation of a custom certificate validator and its usage on the service.</span></span>  
  
### <a name="code"></a><span data-ttu-id="5db22-147">Kod</span><span class="sxs-lookup"><span data-stu-id="5db22-147">Code</span></span>  
 [!code-csharp[c_CustomCertificateValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#3)]
 [!code-vb[c_CustomCertificateValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="5db22-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5db22-148">See also</span></span>

- <xref:System.IdentityModel.Selectors.X509CertificateValidator>
