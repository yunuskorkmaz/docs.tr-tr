---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: özel bir sertifika Doğrulayıcı kullanan bir hizmet oluşturma'
title: 'Nasıl yapılır: Özel Bir Sertifika Doğrulayıcı Kullanan Bir Hizmet Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: bb0190ff-0738-4e54-8d22-c97d343708bf
ms.openlocfilehash: 8ed5d23143b7b69768cc556d9fd5663e46fd7da7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668987"
---
# <a name="how-to-create-a-service-that-employs-a-custom-certificate-validator"></a><span data-ttu-id="c1312-103">Nasıl yapılır: Özel Bir Sertifika Doğrulayıcı Kullanan Bir Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c1312-103">How to: Create a Service that Employs a Custom Certificate Validator</span></span>

<span data-ttu-id="c1312-104">Bu konu, Özel Sertifika doğrulayıcı 'nın nasıl uygulanacağını ve istemci ya da hizmet kimlik bilgilerinin varsayılan sertifika doğrulama mantığını özel sertifika doğrulayıcısı ile değiştirecek şekilde nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c1312-104">This topic shows how to implement a custom certificate validator and how to configure client or service credentials to replace the default certificate validation logic with the custom certificate validator.</span></span>  
  
 <span data-ttu-id="c1312-105">X. 509.440 sertifikası bir istemcinin veya hizmetin kimliğini doğrulamak için kullanılıyorsa, varsayılan olarak Windows Communication Foundation (WCF) sertifikayı doğrulamak ve güvenilir olduğundan emin olmak için Windows sertifika deposu ve şifre API 'sini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c1312-105">If the X.509 certificate is used to authenticate a client or service, Windows Communication Foundation (WCF) by default uses the Windows certificate store and Crypto API to validate the certificate and to ensure that it is trusted.</span></span> <span data-ttu-id="c1312-106">Bazen yerleşik sertifika doğrulama işlevinin yeterince olmaması ve değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="c1312-106">Sometimes the built-in certificate validation functionality is not enough and must be changed.</span></span> <span data-ttu-id="c1312-107">WCF, kullanıcıların özel bir sertifika Doğrulayıcısı eklemesine izin vererek doğrulama mantığını değiştirmek için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1312-107">WCF provides an easy way to change the validation logic by allowing users to add a custom certificate validator.</span></span> <span data-ttu-id="c1312-108">Özel bir sertifika Doğrulayıcısı belirtilmişse, WCF yerleşik sertifika doğrulama mantığını kullanmaz, ancak bunun yerine özel Doğrulayıcısı kullanır.</span><span class="sxs-lookup"><span data-stu-id="c1312-108">If a custom certificate validator is specified, WCF does not use the built-in certificate validation logic but relies on the custom validator instead.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="c1312-109">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="c1312-109">Procedures</span></span>  
  
#### <a name="to-create-a-custom-certificate-validator"></a><span data-ttu-id="c1312-110">Özel bir sertifika Doğrulayıcısı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c1312-110">To create a custom certificate validator</span></span>  
  
1. <span data-ttu-id="c1312-111">Öğesinden türetilmiş yeni bir sınıf tanımlayın <xref:System.IdentityModel.Selectors.X509CertificateValidator> .</span><span class="sxs-lookup"><span data-stu-id="c1312-111">Define a new class derived from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span>  
  
2. <span data-ttu-id="c1312-112">Soyut yöntemi uygulayın <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> .</span><span class="sxs-lookup"><span data-stu-id="c1312-112">Implement the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> method.</span></span> <span data-ttu-id="c1312-113">Doğrulanması gereken sertifika, yöntemine bir bağımsız değişken olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="c1312-113">The certificate that must be validated is passed as an argument to the method.</span></span> <span data-ttu-id="c1312-114">Geçirilen sertifika doğrulama mantığına göre geçerli değilse, bu yöntem bir oluşturur <xref:System.IdentityModel.Tokens.SecurityTokenValidationException> .</span><span class="sxs-lookup"><span data-stu-id="c1312-114">If the passed certificate is not valid according to the validation logic, this method throws a <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>.</span></span> <span data-ttu-id="c1312-115">Sertifika geçerliyse, yöntemi çağırana döner.</span><span class="sxs-lookup"><span data-stu-id="c1312-115">If the certificate is valid, the method returns to the caller.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c1312-116">Kimlik doğrulama hatalarını istemciye geri döndürmek için yönteminde bir oluşturun <xref:System.ServiceModel.FaultException> <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> .</span><span class="sxs-lookup"><span data-stu-id="c1312-116">To return authentication errors back to the client, throw a <xref:System.ServiceModel.FaultException> in the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>  
  
 [!code-csharp[c_CustomCertificateValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#2)]
 [!code-vb[c_CustomCertificateValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#2)]  
  
#### <a name="to-specify-a-custom-certificate-validator-in-service-configuration"></a><span data-ttu-id="c1312-117">Hizmet yapılandırmasında özel bir sertifika Doğrulayıcısı belirtmek için</span><span class="sxs-lookup"><span data-stu-id="c1312-117">To specify a custom certificate validator in service configuration</span></span>  
  
1. <span data-ttu-id="c1312-118">Öğesine bir [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) öğesi ve öğesi ekleyin [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) .</span><span class="sxs-lookup"><span data-stu-id="c1312-118">Add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element and a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2. <span data-ttu-id="c1312-119">Bir ekleyin [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) ve `name` özniteliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c1312-119">Add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>  
  
3. <span data-ttu-id="c1312-120">Öğesi öğesine ekleyin [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) `<behavior>` .</span><span class="sxs-lookup"><span data-stu-id="c1312-120">Add a [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) to the `<behavior>` element.</span></span>  
  
4. <span data-ttu-id="c1312-121">Öğeye bir `<clientCertificate>` öğe ekleyin `<serviceCredentials>` .</span><span class="sxs-lookup"><span data-stu-id="c1312-121">Add a `<clientCertificate>` element to the `<serviceCredentials>` element.</span></span>  
  
5. <span data-ttu-id="c1312-122">[\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) `<clientCertificate>` Öğesini öğesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c1312-122">Add an [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) to the `<clientCertificate>` element.</span></span>  
  
6. <span data-ttu-id="c1312-123">`customCertificateValidatorType`Özniteliği Doğrulayıcı türü olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c1312-123">Set the `customCertificateValidatorType` attribute to the validator type.</span></span> <span data-ttu-id="c1312-124">Aşağıdaki örnek, özniteliğini ad alanına ve türün adına ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c1312-124">The following example sets the attribute to the namespace and name of the type.</span></span>  
  
7. <span data-ttu-id="c1312-125">`certificateValidationMode`Özniteliğini olarak ayarlayın `Custom` .</span><span class="sxs-lookup"><span data-stu-id="c1312-125">Set the `certificateValidationMode` attribute to `Custom`.</span></span>  
  
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
  
#### <a name="to-specify-a-custom-certificate-validator-using-configuration-on-the-client"></a><span data-ttu-id="c1312-126">İstemcideki yapılandırmayı kullanarak özel bir sertifika Doğrulayıcısı belirtmek için</span><span class="sxs-lookup"><span data-stu-id="c1312-126">To specify a custom certificate validator using configuration on the client</span></span>  
  
1. <span data-ttu-id="c1312-127">Öğesine bir [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) öğesi ve öğesi ekleyin [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) .</span><span class="sxs-lookup"><span data-stu-id="c1312-127">Add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element and a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2. <span data-ttu-id="c1312-128">Bir [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c1312-128">Add an [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) element.</span></span>  
  
3. <span data-ttu-id="c1312-129">Bir `<behavior>` öğesi ekleyin ve `name` özniteliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c1312-129">Add a `<behavior>` element and set the `name` attribute to an appropriate value.</span></span>  
  
4. <span data-ttu-id="c1312-130">Bir [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c1312-130">Add a [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) element.</span></span>  
  
5. <span data-ttu-id="c1312-131">Bir ekleyin [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) .</span><span class="sxs-lookup"><span data-stu-id="c1312-131">Add a [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md).</span></span>  
  
6. <span data-ttu-id="c1312-132">[\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)Aşağıdaki örnekte gösterildiği gibi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c1312-132">Add an [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) as shown on the following example.</span></span>  
  
7. <span data-ttu-id="c1312-133">`customCertificateValidatorType`Özniteliği Doğrulayıcı türü olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c1312-133">Set the `customCertificateValidatorType` attribute to the validator type.</span></span>  
  
8. <span data-ttu-id="c1312-134">`certificateValidationMode`Özniteliğini olarak ayarlayın `Custom` .</span><span class="sxs-lookup"><span data-stu-id="c1312-134">Set the `certificateValidationMode` attribute to `Custom`.</span></span> <span data-ttu-id="c1312-135">Aşağıdaki örnek, özniteliğini ad alanına ve türün adına ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c1312-135">The following example sets the attribute to the namespace and name of the type.</span></span>  
  
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
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-service"></a><span data-ttu-id="c1312-136">Hizmette kod kullanarak özel bir sertifika Doğrulayıcısı belirtmek için</span><span class="sxs-lookup"><span data-stu-id="c1312-136">To specify a custom certificate validator using code on the service</span></span>  
  
1. <span data-ttu-id="c1312-137">Özellikte özel sertifika Doğrulayıcısı ' nı belirtin <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> .</span><span class="sxs-lookup"><span data-stu-id="c1312-137">Specify the custom certificate validator on the <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> property.</span></span> <span data-ttu-id="c1312-138">Özelliğini kullanarak hizmet kimlik bilgilerine erişebilirsiniz <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> .</span><span class="sxs-lookup"><span data-stu-id="c1312-138">You can access the service credentials using the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property.</span></span>  
  
2. <span data-ttu-id="c1312-139"><xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A>Özelliğini olarak ayarlayın <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom> .</span><span class="sxs-lookup"><span data-stu-id="c1312-139">Set the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> property to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span></span>  
  
 [!code-csharp[c_CustomCertificateValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#1)]
 [!code-vb[c_CustomCertificateValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#1)]  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-client"></a><span data-ttu-id="c1312-140">İstemcideki kodu kullanarak özel bir sertifika Doğrulayıcısı belirtmek için</span><span class="sxs-lookup"><span data-stu-id="c1312-140">To specify a custom certificate validator using code on the client</span></span>  
  
1. <span data-ttu-id="c1312-141">Özelliğini kullanarak özel sertifika Doğrulayıcısı belirtin <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> .</span><span class="sxs-lookup"><span data-stu-id="c1312-141">Specify the custom certificate validator using the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> property.</span></span> <span data-ttu-id="c1312-142">Özelliğini kullanarak istemci kimlik bilgilerine erişebilirsiniz <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> .</span><span class="sxs-lookup"><span data-stu-id="c1312-142">You can access the client credentials using the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property.</span></span> <span data-ttu-id="c1312-143">( [ServiceModel meta veri yardımcı programı](../servicemodel-metadata-utility-tool-svcutil-exe.md) tarafından oluşturulan istemci sınıfı (Svcutil.exe) her zaman sınıfından türetilir <xref:System.ServiceModel.ClientBase%601> .)</span><span class="sxs-lookup"><span data-stu-id="c1312-143">(The client class generated by [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) always derives from the <xref:System.ServiceModel.ClientBase%601> class.)</span></span>  
  
2. <span data-ttu-id="c1312-144"><xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A>Özelliğini olarak ayarlayın <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom> .</span><span class="sxs-lookup"><span data-stu-id="c1312-144">Set the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> property to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1312-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="c1312-145">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="c1312-146">Description</span><span class="sxs-lookup"><span data-stu-id="c1312-146">Description</span></span>  

 <span data-ttu-id="c1312-147">Aşağıdaki örnek, bir özel sertifika doğrulayıcının ve hizmet üzerindeki kullanımının bir uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c1312-147">The following sample shows an implementation of a custom certificate validator and its usage on the service.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c1312-148">Kod</span><span class="sxs-lookup"><span data-stu-id="c1312-148">Code</span></span>  

 [!code-csharp[c_CustomCertificateValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#3)]
 [!code-vb[c_CustomCertificateValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="c1312-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1312-149">See also</span></span>

- <xref:System.IdentityModel.Selectors.X509CertificateValidator>
