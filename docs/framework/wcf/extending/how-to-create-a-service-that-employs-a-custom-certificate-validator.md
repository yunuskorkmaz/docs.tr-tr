---
title: 'Nasıl yapılır: Özel Bir Sertifika Doğrulayıcı Kullanan Bir Hizmet Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: bb0190ff-0738-4e54-8d22-c97d343708bf
ms.openlocfilehash: af1bb9b2ff793f6e6854c1b253dd445a35a5076f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185571"
---
# <a name="how-to-create-a-service-that-employs-a-custom-certificate-validator"></a><span data-ttu-id="2f629-102">Nasıl yapılır: Özel Bir Sertifika Doğrulayıcı Kullanan Bir Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2f629-102">How to: Create a Service that Employs a Custom Certificate Validator</span></span>
<span data-ttu-id="2f629-103">Bu konu, özel sertifika doğrulayıcısının nasıl uygulanacağını ve varsayılan sertifika doğrulama mantığını özel sertifika doğrulayıcısıyla değiştirmek için istemci veya hizmet kimlik bilgilerini nasıl yapılandıracağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2f629-103">This topic shows how to implement a custom certificate validator and how to configure client or service credentials to replace the default certificate validation logic with the custom certificate validator.</span></span>  
  
 <span data-ttu-id="2f629-104">X.509 sertifikası bir istemcinin veya hizmetin kimliğini doğrulamak için kullanılırsa, Windows Communication Foundation (WCF) varsayılan olarak sertifikayı doğrulamak ve güvenilir olduğundan emin olmak için Windows sertifika deposunu ve Crypto API'yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="2f629-104">If the X.509 certificate is used to authenticate a client or service, Windows Communication Foundation (WCF) by default uses the Windows certificate store and Crypto API to validate the certificate and to ensure that it is trusted.</span></span> <span data-ttu-id="2f629-105">Bazen yerleşik sertifika doğrulama işlevi yeterli değildir ve değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="2f629-105">Sometimes the built-in certificate validation functionality is not enough and must be changed.</span></span> <span data-ttu-id="2f629-106">WCF, kullanıcıların özel sertifika doğrulayıcısı eklemesine izin vererek doğrulama mantığını değiştirmenin kolay bir yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="2f629-106">WCF provides an easy way to change the validation logic by allowing users to add a custom certificate validator.</span></span> <span data-ttu-id="2f629-107">Özel sertifika doğrulayıcısı belirtilmişse, WCF yerleşik sertifika doğrulama mantığını kullanmaz, ancak bunun yerine özel doğrulayıcıya dayanır.</span><span class="sxs-lookup"><span data-stu-id="2f629-107">If a custom certificate validator is specified, WCF does not use the built-in certificate validation logic but relies on the custom validator instead.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="2f629-108">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="2f629-108">Procedures</span></span>  
  
#### <a name="to-create-a-custom-certificate-validator"></a><span data-ttu-id="2f629-109">Özel sertifika doğrulayıcısı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="2f629-109">To create a custom certificate validator</span></span>  
  
1. <span data-ttu-id="2f629-110">Türetilen yeni bir <xref:System.IdentityModel.Selectors.X509CertificateValidator>sınıf tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="2f629-110">Define a new class derived from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span>  
  
2. <span data-ttu-id="2f629-111">Soyut <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> yöntemi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="2f629-111">Implement the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> method.</span></span> <span data-ttu-id="2f629-112">Doğrulanması gereken sertifika yönteme bağımsız değişken olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="2f629-112">The certificate that must be validated is passed as an argument to the method.</span></span> <span data-ttu-id="2f629-113">Geçirilen sertifika doğrulama mantığına göre geçerli değilse, bu yöntem <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>bir .</span><span class="sxs-lookup"><span data-stu-id="2f629-113">If the passed certificate is not valid according to the validation logic, this method throws a <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>.</span></span> <span data-ttu-id="2f629-114">Sertifika geçerliyse, yöntem arayana döner.</span><span class="sxs-lookup"><span data-stu-id="2f629-114">If the certificate is valid, the method returns to the caller.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="2f629-115">Kimlik doğrulama hatalarını istemciye geri <xref:System.ServiceModel.FaultException> döndürmek <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> için yönteme bir a atın.</span><span class="sxs-lookup"><span data-stu-id="2f629-115">To return authentication errors back to the client, throw a <xref:System.ServiceModel.FaultException> in the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>  
  
 [!code-csharp[c_CustomCertificateValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#2)]
 [!code-vb[c_CustomCertificateValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#2)]  
  
#### <a name="to-specify-a-custom-certificate-validator-in-service-configuration"></a><span data-ttu-id="2f629-116">Hizmet yapılandırmasında özel sertifika doğrulayıcısı belirtmek için</span><span class="sxs-lookup"><span data-stu-id="2f629-116">To specify a custom certificate validator in service configuration</span></span>  
  
1. <span data-ttu-id="2f629-117">Bir [ \<davranış>](../../configure-apps/file-schema/wcf/behaviors.md) öğesi ve bir [ \<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) [ \<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2f629-117">Add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element and a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2. <span data-ttu-id="2f629-118">[ \<Davranış>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) ekleyin ve `name` özniteliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2f629-118">Add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>  
  
3. <span data-ttu-id="2f629-119">Öğeye [ \<>bir hizmet Kimlik Bilgileri](../../configure-apps/file-schema/wcf/servicecredentials.md) ekleyin. `<behavior>`</span><span class="sxs-lookup"><span data-stu-id="2f629-119">Add a [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) to the `<behavior>` element.</span></span>  
  
4. <span data-ttu-id="2f629-120">`<serviceCredentials>` Öğeye bir `<clientCertificate>` öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2f629-120">Add a `<clientCertificate>` element to the `<serviceCredentials>` element.</span></span>  
  
5. <span data-ttu-id="2f629-121">Öğeye [ \<kimlik doğrulama>](../../configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) ekleyin. `<clientCertificate>`</span><span class="sxs-lookup"><span data-stu-id="2f629-121">Add an [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) to the `<clientCertificate>` element.</span></span>  
  
6. <span data-ttu-id="2f629-122">`customCertificateValidatorType` Özniteliği doğrulayıcı türüne ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2f629-122">Set the `customCertificateValidatorType` attribute to the validator type.</span></span> <span data-ttu-id="2f629-123">Aşağıdaki örnek, ad alanı ve türün adı özniteliğini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2f629-123">The following example sets the attribute to the namespace and name of the type.</span></span>  
  
7. <span data-ttu-id="2f629-124">Özniteliği `certificateValidationMode` `Custom`' ne göre ayarlayın</span><span class="sxs-lookup"><span data-stu-id="2f629-124">Set the `certificateValidationMode` attribute to `Custom`.</span></span>  
  
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
  
#### <a name="to-specify-a-custom-certificate-validator-using-configuration-on-the-client"></a><span data-ttu-id="2f629-125">İstemci üzerinde yapılandırma yı kullanarak özel sertifika doğrulayıcıbelirtmek için</span><span class="sxs-lookup"><span data-stu-id="2f629-125">To specify a custom certificate validator using configuration on the client</span></span>  
  
1. <span data-ttu-id="2f629-126">Bir [ \<davranış>](../../configure-apps/file-schema/wcf/behaviors.md) öğesi ve bir [ \<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) [ \<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2f629-126">Add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element and a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2. <span data-ttu-id="2f629-127">[ \<Bir bitiş noktasıDavranışı>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2f629-127">Add an [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) element.</span></span>  
  
3. <span data-ttu-id="2f629-128">Bir `<behavior>` öğe ekleyin `name` ve özniteliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2f629-128">Add a `<behavior>` element and set the `name` attribute to an appropriate value.</span></span>  
  
4. <span data-ttu-id="2f629-129">[ \<Bir istemci kimlik bilgileri>](../../configure-apps/file-schema/wcf/clientcredentials.md) öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2f629-129">Add a [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) element.</span></span>  
  
5. <span data-ttu-id="2f629-130">[ \<ServiceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)ekle.</span><span class="sxs-lookup"><span data-stu-id="2f629-130">Add a [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md).</span></span>  
  
6. <span data-ttu-id="2f629-131">Aşağıdaki örnekte gösterildiği gibi [ \<kimlik doğrulama>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2f629-131">Add an [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) as shown on the following example.</span></span>  
  
7. <span data-ttu-id="2f629-132">`customCertificateValidatorType` Özniteliği doğrulayıcı türüne ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2f629-132">Set the `customCertificateValidatorType` attribute to the validator type.</span></span>  
  
8. <span data-ttu-id="2f629-133">Özniteliği `certificateValidationMode` `Custom`' ne göre ayarlayın</span><span class="sxs-lookup"><span data-stu-id="2f629-133">Set the `certificateValidationMode` attribute to `Custom`.</span></span> <span data-ttu-id="2f629-134">Aşağıdaki örnek, ad alanı ve türün adı özniteliğini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2f629-134">The following example sets the attribute to the namespace and name of the type.</span></span>  
  
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
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-service"></a><span data-ttu-id="2f629-135">Hizmette kodu kullanarak özel sertifika doğrulayıcı belirtmek için</span><span class="sxs-lookup"><span data-stu-id="2f629-135">To specify a custom certificate validator using code on the service</span></span>  
  
1. <span data-ttu-id="2f629-136">Özellikteki özel sertifika doğrulayıcısını belirtin. <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A></span><span class="sxs-lookup"><span data-stu-id="2f629-136">Specify the custom certificate validator on the <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> property.</span></span> <span data-ttu-id="2f629-137">Özelliği kullanarak hizmet kimlik <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> bilgilerine erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f629-137">You can access the service credentials using the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property.</span></span>  
  
2. <span data-ttu-id="2f629-138">Özelliği <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> ' <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>ye ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2f629-138">Set the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> property to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span></span>  
  
 [!code-csharp[c_CustomCertificateValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#1)]
 [!code-vb[c_CustomCertificateValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#1)]  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-client"></a><span data-ttu-id="2f629-139">İstemci üzerinde kod kullanarak özel bir sertifika doğrulayıcı belirtmek için</span><span class="sxs-lookup"><span data-stu-id="2f629-139">To specify a custom certificate validator using code on the client</span></span>  
  
1. <span data-ttu-id="2f629-140">Özelliği kullanarak özel sertifika doğrulayıcısını belirtin. <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A></span><span class="sxs-lookup"><span data-stu-id="2f629-140">Specify the custom certificate validator using the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> property.</span></span> <span data-ttu-id="2f629-141">Özelliği kullanarak istemci kimlik <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> bilgilerine erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f629-141">You can access the client credentials using the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property.</span></span> <span data-ttu-id="2f629-142">[(ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) tarafından oluşturulan istemci <xref:System.ServiceModel.ClientBase%601> sınıfı her zaman sınıftan türetilmiştir.)</span><span class="sxs-lookup"><span data-stu-id="2f629-142">(The client class generated by [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) always derives from the <xref:System.ServiceModel.ClientBase%601> class.)</span></span>  
  
2. <span data-ttu-id="2f629-143">Özelliği <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> ' <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>ye ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2f629-143">Set the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> property to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f629-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="2f629-144">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="2f629-145">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2f629-145">Description</span></span>  
 <span data-ttu-id="2f629-146">Aşağıdaki örnek, özel sertifika doğrulayıcısının uygulanmasını ve hizmetüzerindeki kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2f629-146">The following sample shows an implementation of a custom certificate validator and its usage on the service.</span></span>  
  
### <a name="code"></a><span data-ttu-id="2f629-147">Kod</span><span class="sxs-lookup"><span data-stu-id="2f629-147">Code</span></span>  
 [!code-csharp[c_CustomCertificateValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#3)]
 [!code-vb[c_CustomCertificateValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="2f629-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f629-148">See also</span></span>

- <xref:System.IdentityModel.Selectors.X509CertificateValidator>
