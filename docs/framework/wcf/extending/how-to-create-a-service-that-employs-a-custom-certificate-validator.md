---
title: 'Nasıl yapılır: Özel Bir Sertifika Doğrulayıcı Kullanan Bir Hizmet Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: bb0190ff-0738-4e54-8d22-c97d343708bf
ms.openlocfilehash: 156d661fd5602333fae8066f3062b442a1df19af
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951700"
---
# <a name="how-to-create-a-service-that-employs-a-custom-certificate-validator"></a><span data-ttu-id="ed92b-102">Nasıl yapılır: Özel Bir Sertifika Doğrulayıcı Kullanan Bir Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ed92b-102">How to: Create a Service that Employs a Custom Certificate Validator</span></span>
<span data-ttu-id="ed92b-103">Bu konu, Özel Sertifika doğrulayıcı 'nın nasıl uygulanacağını ve istemci ya da hizmet kimlik bilgilerinin varsayılan sertifika doğrulama mantığını özel sertifika doğrulayıcısı ile değiştirecek şekilde nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ed92b-103">This topic shows how to implement a custom certificate validator and how to configure client or service credentials to replace the default certificate validation logic with the custom certificate validator.</span></span>  
  
 <span data-ttu-id="ed92b-104">X. 509.440 sertifikası bir istemcinin veya hizmetin kimliğini doğrulamak için kullanılıyorsa, varsayılan olarak Windows Communication Foundation (WCF) sertifikayı doğrulamak ve güvenilir olduğundan emin olmak için Windows sertifika deposu ve şifre API 'sini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ed92b-104">If the X.509 certificate is used to authenticate a client or service, Windows Communication Foundation (WCF) by default uses the Windows certificate store and Crypto API to validate the certificate and to ensure that it is trusted.</span></span> <span data-ttu-id="ed92b-105">Bazen yerleşik sertifika doğrulama işlevinin yeterince olmaması ve değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="ed92b-105">Sometimes the built-in certificate validation functionality is not enough and must be changed.</span></span> <span data-ttu-id="ed92b-106">WCF, kullanıcıların özel bir sertifika Doğrulayıcısı eklemesine izin vererek doğrulama mantığını değiştirmek için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="ed92b-106">WCF provides an easy way to change the validation logic by allowing users to add a custom certificate validator.</span></span> <span data-ttu-id="ed92b-107">Özel bir sertifika Doğrulayıcısı belirtilmişse, WCF yerleşik sertifika doğrulama mantığını kullanmaz, ancak bunun yerine özel Doğrulayıcısı kullanır.</span><span class="sxs-lookup"><span data-stu-id="ed92b-107">If a custom certificate validator is specified, WCF does not use the built-in certificate validation logic but relies on the custom validator instead.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="ed92b-108">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="ed92b-108">Procedures</span></span>  
  
#### <a name="to-create-a-custom-certificate-validator"></a><span data-ttu-id="ed92b-109">Özel bir sertifika Doğrulayıcısı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="ed92b-109">To create a custom certificate validator</span></span>  
  
1. <span data-ttu-id="ed92b-110">Öğesinden <xref:System.IdentityModel.Selectors.X509CertificateValidator>türetilmiş yeni bir sınıf tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="ed92b-110">Define a new class derived from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span>  
  
2. <span data-ttu-id="ed92b-111">Soyut <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> yöntemi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="ed92b-111">Implement the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> method.</span></span> <span data-ttu-id="ed92b-112">Doğrulanması gereken sertifika, yöntemine bir bağımsız değişken olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="ed92b-112">The certificate that must be validated is passed as an argument to the method.</span></span> <span data-ttu-id="ed92b-113">Geçirilen sertifika doğrulama mantığına göre geçerli değilse, bu yöntem bir <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ed92b-113">If the passed certificate is not valid according to the validation logic, this method throws a <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>.</span></span> <span data-ttu-id="ed92b-114">Sertifika geçerliyse, yöntemi çağırana döner.</span><span class="sxs-lookup"><span data-stu-id="ed92b-114">If the certificate is valid, the method returns to the caller.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ed92b-115">Kimlik doğrulama hatalarını istemciye geri döndürmek için <xref:System.ServiceModel.FaultException> <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> yönteminde bir oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ed92b-115">To return authentication errors back to the client, throw a <xref:System.ServiceModel.FaultException> in the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>  
  
 [!code-csharp[c_CustomCertificateValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#2)]
 [!code-vb[c_CustomCertificateValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#2)]  
  
#### <a name="to-specify-a-custom-certificate-validator-in-service-configuration"></a><span data-ttu-id="ed92b-116">Hizmet yapılandırmasında özel bir sertifika Doğrulayıcısı belirtmek için</span><span class="sxs-lookup"><span data-stu-id="ed92b-116">To specify a custom certificate validator in service configuration</span></span>  
  
1. <span data-ttu-id="ed92b-117">[System. ServiceModel > öğesine bir > öğesi ve servicedavranışlar > ekleyin. \<](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ed92b-117">Add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element and a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2. <span data-ttu-id="ed92b-118">`name` [ Bir\<davranış >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) ekleyin ve özniteliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ed92b-118">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>  
  
3. <span data-ttu-id="ed92b-119">Öğeye`<behavior>` bir [ \<ServiceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ed92b-119">Add a [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) to the `<behavior>` element.</span></span>  
  
4. <span data-ttu-id="ed92b-120">`<serviceCredentials>` Öğeye bir `<clientCertificate>` öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ed92b-120">Add a `<clientCertificate>` element to the `<serviceCredentials>` element.</span></span>  
  
5. <span data-ttu-id="ed92b-121">`<clientCertificate>` Öğeye bir [ \<kimlik doğrulaması >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ed92b-121">Add an [\<authentication>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) to the `<clientCertificate>` element.</span></span>  
  
6. <span data-ttu-id="ed92b-122">`customCertificateValidatorType` Özniteliği Doğrulayıcı türü olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ed92b-122">Set the `customCertificateValidatorType` attribute to the validator type.</span></span> <span data-ttu-id="ed92b-123">Aşağıdaki örnek, özniteliğini ad alanına ve türün adına ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ed92b-123">The following example sets the attribute to the namespace and name of the type.</span></span>  
  
7. <span data-ttu-id="ed92b-124">`certificateValidationMode` Özniteliğini olarak`Custom`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ed92b-124">Set the `certificateValidationMode` attribute to `Custom`.</span></span>  
  
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
  
#### <a name="to-specify-a-custom-certificate-validator-using-configuration-on-the-client"></a><span data-ttu-id="ed92b-125">İstemcideki yapılandırmayı kullanarak özel bir sertifika Doğrulayıcısı belirtmek için</span><span class="sxs-lookup"><span data-stu-id="ed92b-125">To specify a custom certificate validator using configuration on the client</span></span>  
  
1. <span data-ttu-id="ed92b-126">[System. ServiceModel > öğesine bir > öğesi ve servicedavranışlar > ekleyin. \<](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ed92b-126">Add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element and a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2. <span data-ttu-id="ed92b-127">[ Bir\<endpointdavranışlar >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ed92b-127">Add an [\<endpointBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) element.</span></span>  
  
3. <span data-ttu-id="ed92b-128">Bir `<behavior>` öğesi ekleyin ve `name` özniteliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ed92b-128">Add a `<behavior>` element and set the `name` attribute to an appropriate value.</span></span>  
  
4. <span data-ttu-id="ed92b-129">[ Bir\<ClientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ed92b-129">Add a [\<clientCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element.</span></span>  
  
5. <span data-ttu-id="ed92b-130">[ Bir\<ServiceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ed92b-130">Add a [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md).</span></span>  
  
6. <span data-ttu-id="ed92b-131">Aşağıdaki örnekte gösterildiği gibi bir [ \<kimlik doğrulama >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ed92b-131">Add an [\<authentication>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) as shown on the following example.</span></span>  
  
7. <span data-ttu-id="ed92b-132">`customCertificateValidatorType` Özniteliği Doğrulayıcı türü olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ed92b-132">Set the `customCertificateValidatorType` attribute to the validator type.</span></span>  
  
8. <span data-ttu-id="ed92b-133">`certificateValidationMode` Özniteliğini olarak`Custom`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ed92b-133">Set the `certificateValidationMode` attribute to `Custom`.</span></span> <span data-ttu-id="ed92b-134">Aşağıdaki örnek, özniteliğini ad alanına ve türün adına ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ed92b-134">The following example sets the attribute to the namespace and name of the type.</span></span>  
  
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
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-service"></a><span data-ttu-id="ed92b-135">Hizmette kod kullanarak özel bir sertifika Doğrulayıcısı belirtmek için</span><span class="sxs-lookup"><span data-stu-id="ed92b-135">To specify a custom certificate validator using code on the service</span></span>  
  
1. <span data-ttu-id="ed92b-136"><xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> Özellikte özel sertifika Doğrulayıcısı ' nı belirtin.</span><span class="sxs-lookup"><span data-stu-id="ed92b-136">Specify the custom certificate validator on the <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> property.</span></span> <span data-ttu-id="ed92b-137"><xref:System.ServiceModel.ServiceHostBase.Credentials%2A> Özelliğini kullanarak hizmet kimlik bilgilerine erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed92b-137">You can access the service credentials using the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property.</span></span>  
  
2. <span data-ttu-id="ed92b-138">Ayarlama <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> özelliğini <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="ed92b-138">Set the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> property to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span></span>  
  
 [!code-csharp[c_CustomCertificateValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#1)]
 [!code-vb[c_CustomCertificateValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#1)]  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-client"></a><span data-ttu-id="ed92b-139">İstemcideki kodu kullanarak özel bir sertifika Doğrulayıcısı belirtmek için</span><span class="sxs-lookup"><span data-stu-id="ed92b-139">To specify a custom certificate validator using code on the client</span></span>  
  
1. <span data-ttu-id="ed92b-140"><xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> Özelliğini kullanarak özel sertifika Doğrulayıcısı belirtin.</span><span class="sxs-lookup"><span data-stu-id="ed92b-140">Specify the custom certificate validator using the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> property.</span></span> <span data-ttu-id="ed92b-141"><xref:System.ServiceModel.ServiceHostBase.Credentials%2A> Özelliğini kullanarak istemci kimlik bilgilerine erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed92b-141">You can access the client credentials using the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property.</span></span> <span data-ttu-id="ed92b-142">( [ServiceModel meta veri yardımcı programı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tarafından oluşturulan istemci sınıfı her zaman <xref:System.ServiceModel.ClientBase%601> sınıfından türetilir.)</span><span class="sxs-lookup"><span data-stu-id="ed92b-142">(The client class generated by [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) always derives from the <xref:System.ServiceModel.ClientBase%601> class.)</span></span>  
  
2. <span data-ttu-id="ed92b-143">Ayarlama <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> özelliğini <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="ed92b-143">Set the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> property to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed92b-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="ed92b-144">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="ed92b-145">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed92b-145">Description</span></span>  
 <span data-ttu-id="ed92b-146">Aşağıdaki örnek, bir özel sertifika doğrulayıcının ve hizmet üzerindeki kullanımının bir uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ed92b-146">The following sample shows an implementation of a custom certificate validator and its usage on the service.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ed92b-147">Kod</span><span class="sxs-lookup"><span data-stu-id="ed92b-147">Code</span></span>  
 [!code-csharp[c_CustomCertificateValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#3)]
 [!code-vb[c_CustomCertificateValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="ed92b-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed92b-148">See also</span></span>

- <xref:System.IdentityModel.Selectors.X509CertificateValidator>
