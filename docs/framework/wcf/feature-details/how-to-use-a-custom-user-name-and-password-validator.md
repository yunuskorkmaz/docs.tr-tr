---
title: "Nasıl yapılır: Özel Bir Kullanıcı Adı ve Parola Doğrulayıcı Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9086489d7b48b459ad92f1712809406cbde7e074
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="96a67-102">Nasıl yapılır: Özel Bir Kullanıcı Adı ve Parola Doğrulayıcı Kullanma</span><span class="sxs-lookup"><span data-stu-id="96a67-102">How to: Use a Custom User Name and Password Validator</span></span>
<span data-ttu-id="96a67-103">Bir kullanıcı adı ve parola kullanıldığında kimlik doğrulaması için varsayılan olarak, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Windows kullanıcı adı ve parolayı doğrulamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="96a67-103">By default, when a user name and password is used for authentication, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] uses Windows to validate the user name and password.</span></span> <span data-ttu-id="96a67-104">Ancak, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] özel kullanıcı adı ve parola kimlik doğrulaması düzeni için olarak da bilinen sağlar *doğrulayıcıları*.</span><span class="sxs-lookup"><span data-stu-id="96a67-104">However, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] allows for custom user name and password authentication schemes, also known as *validators*.</span></span> <span data-ttu-id="96a67-105">Özel kullanıcı adı ve parola Doğrulayıcı içerecek şekilde türeyen bir sınıf oluşturun <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> ve ardından yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="96a67-105">To incorporate a custom user name and password validator, create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> and then configure it.</span></span>  
  
 <span data-ttu-id="96a67-106">Örnek bir uygulama için bkz: [kullanıcı Adıparola Doğrulayıcı](../../../../docs/framework/wcf/samples/user-name-password-validator.md).</span><span class="sxs-lookup"><span data-stu-id="96a67-106">For a sample application, see [User Name Password Validator](../../../../docs/framework/wcf/samples/user-name-password-validator.md).</span></span>  
  
### <a name="to-create-a-custom-user-name-and-password-validator"></a><span data-ttu-id="96a67-107">Özel kullanıcı adı ve parola Doğrulayıcı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="96a67-107">To create a custom user name and password validator</span></span>  
  
1.  <span data-ttu-id="96a67-108">Türeyen bir sınıf oluşturun <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span><span class="sxs-lookup"><span data-stu-id="96a67-108">Create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span>  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]  
  
2.  <span data-ttu-id="96a67-109">Özel kimlik doğrulama şeması geçersiz kılarak uygulamak <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="96a67-109">Implement the custom authentication scheme by overriding the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>  
  
     <span data-ttu-id="96a67-110">Kodu geçersiz kılar aşağıdaki örnekte kullanmayın <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> bir üretim ortamında yöntemi.</span><span class="sxs-lookup"><span data-stu-id="96a67-110">Do not use the code in the following example that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="96a67-111">Kullanıcı adı ve parola çiftleri veritabanından alma de girer, özel kullanıcı adı ve parola doğrulama düzeni, kodu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="96a67-111">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>  
  
     <span data-ttu-id="96a67-112">Kimlik doğrulama hataları istemciye geri dönmek için throw bir <xref:System.ServiceModel.FaultException> içinde <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="96a67-112">To return authentication errors back to the client, throw a <xref:System.ServiceModel.FaultException> in the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]  
  
### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="96a67-113">Özel kullanıcı adı ve parola Doğrulayıcı kullanmak için bir hizmeti yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="96a67-113">To configure a service to use a custom user name and password validator</span></span>  
  
1.  <span data-ttu-id="96a67-114">İleti güvenliği HTTP (S) üzerinden herhangi bir aktarım veya aktarım düzeyinde güvenlik kullanan bir bağlama yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="96a67-114">Configure a binding that uses message security over any transport or transport-level security over HTTP(S).</span></span>  
  
     <span data-ttu-id="96a67-115">İleti güvenliği kullanırken, sistem tarafından sağlanan bağlamalar birini gibi ekleyin. bir [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), veya bir [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) ileti güvenliği destekler ve `UserName` kimlik bilgisi türü.</span><span class="sxs-lookup"><span data-stu-id="96a67-115">When using message security, add one of the system-provided bindings, such as a  [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), or a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) that supports message security and the `UserName` credential type.</span></span>  
  
     <span data-ttu-id="96a67-116">HTTP (S) üzerinden aktarım düzeyinde güvenlik kullanırken, ekleyip ya da [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) veya [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), [ \< netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) veya [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) HTTP (S) kullanan ve `Basic` kimlik doğrulama düzeni.</span><span class="sxs-lookup"><span data-stu-id="96a67-116">When using transport-level security over HTTP(S), add either the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), a [\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) or a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) that uses HTTP(S) and the `Basic` authentication scheme.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="96a67-117">Zaman [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] veya daha sonraki bir sürümü kullanıldığında, özel bir kullanıcı adı ve parola Doğrulayıcı ileti ve taşıma güvenliği ile kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96a67-117">When [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] or later is used, you can use a custom username and password validator with message and transport security.</span></span> <span data-ttu-id="96a67-118">İle [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], özel bir kullanıcı adı ve parola Doğrulayıcı ile ileti güvenliği yalnızca kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="96a67-118">With [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], a custom username and password validator can only be used with message security.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="96a67-119">Kullanma hakkında daha fazla bilgi için \<netTcpBinding > Bu bağlamda bkz [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="96a67-119">For more information on using \<netTcpBinding> in this context, see [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)</span></span>  
  
    1.  <span data-ttu-id="96a67-120">Yapılandırma dosyasında altında [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) öğesi ekleme bir [ \<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="96a67-120">In the configuration file, under the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
    2.  <span data-ttu-id="96a67-121">Ekleme bir [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) veya [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) bağlamaları bölümüne öğesi.</span><span class="sxs-lookup"><span data-stu-id="96a67-121">Add a [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element to the bindings section.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="96a67-122">oluşturma bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bağlama öğesi, bkz: [nasıl yapılır: yapılandırmada hizmet bağlama belirtme](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="96a67-122"> creating an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
    3.  <span data-ttu-id="96a67-123">Ayarlama `mode` özniteliği [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) veya [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) için `Message`, `Transport`, `or``TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="96a67-123">Set the `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) or [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) to `Message`, `Transport`, `or``TransportWithMessageCredential`.</span></span>  
  
    4.  <span data-ttu-id="96a67-124">Ayarlama `clientCredentialType` özniteliği [ \<ileti >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) veya [ \<aktarım >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="96a67-124">Set the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) or [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span></span>  
  
         <span data-ttu-id="96a67-125">İleti güvenliği kullanırken ayarlayın `clientCredentialType` özniteliği [ \<ileti >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) için `UserName`.</span><span class="sxs-lookup"><span data-stu-id="96a67-125">When using message security, set the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) to `UserName`.</span></span>  
  
         <span data-ttu-id="96a67-126">HTTP (S) üzerinden aktarım düzeyinde güvenlik kullanırken, ayarlayın `clientCredentialType` özniteliği [ \<aktarım >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) veya [ \<aktarım >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) için `Basic`.</span><span class="sxs-lookup"><span data-stu-id="96a67-126">When using transport-level security over HTTP(S), set the `clientCredentialType` attribute of the [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) or [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) to `Basic`.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="96a67-127">Zaman bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Internet Information Services (aktarım düzeyi güvenlik kullanarak IIS içinde) barındırılan hizmetin ve <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> özelliği ayarlanmış <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, özel kimlik doğrulama şeması bir alt kümesini Windows kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="96a67-127">When a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is hosted in Internet Information Services (IIS) using transport-level security and the <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> property is set to <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, the custom authentication scheme uses a subset of Windows authentication.</span></span> <span data-ttu-id="96a67-128">Bu senaryoda, IIS Windows kimlik doğrulaması öncesinde gerçekleştirdiğinden olan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] özel Doğrulayıcı çağırma.</span><span class="sxs-lookup"><span data-stu-id="96a67-128">That is because in this scenario, IIS performs Windows authentication prior to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] invoking the custom authenticator.</span></span>  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="96a67-129">oluşturma bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bağlama öğesi, bkz: [nasıl yapılır: yapılandırmada hizmet bağlama belirtme](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="96a67-129"> creating an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
     <span data-ttu-id="96a67-130">Aşağıdaki örnek, bağlama için yapılandırma kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="96a67-130">The following example shows the configuration code for the binding.</span></span>  
  
    ```xml  
    <system.serviceModel>   
      <bindings>  
      <wsHttpBinding>  
          <binding name="Binding1">  
            <security mode="Message">  
              <message clientCredentialType="UserName" />  
            </security>  
          </binding>          
        </wsHttpBinding>  
      </bindings>  
    </system.serviceModel>  
    ```  
  
2.  <span data-ttu-id="96a67-131">Özel kullanıcı adı ve parola Doğrulayıcı gelen için kullanıcı adı ve parola çiftlerini doğrulamak için kullanıldığını belirtir davranışını yapılandırma <xref:System.IdentityModel.Tokens.UserNameSecurityToken> güvenlik belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="96a67-131">Configure a behavior that specifies that a custom user name and password validator is used to validate user name and password pairs for incoming <xref:System.IdentityModel.Tokens.UserNameSecurityToken> security tokens.</span></span>  
  
    1.  <span data-ttu-id="96a67-132">Alt öğesi olarak [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) öğesi ekleme bir [ \<davranışları >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="96a67-132">As a child to the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>  
  
    2.  <span data-ttu-id="96a67-133">Ekleme bir [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) için [ \<davranışları >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="96a67-133">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>  
  
    3.  <span data-ttu-id="96a67-134">Ekleme bir [ \<davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) öğesi ve kümesi `name` öznitelik için uygun bir değer.</span><span class="sxs-lookup"><span data-stu-id="96a67-134">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>  
  
    4.  <span data-ttu-id="96a67-135">Ekleme bir [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) için [ \<davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="96a67-135">Add a [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) to the [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span></span>  
  
    5.  <span data-ttu-id="96a67-136">Ekleme bir [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) için [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="96a67-136">Add a [\<userNameAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) to the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>  
  
    6.  <span data-ttu-id="96a67-137">Ayarlama `userNamePasswordValidationMode` için `Custom`.</span><span class="sxs-lookup"><span data-stu-id="96a67-137">Set the `userNamePasswordValidationMode` to `Custom`.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="96a67-138">Varsa `userNamePasswordValidationMode` değeri ayarlanmazsa, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yerine özel bir kullanıcı adı ve parola Doğrulayıcı Windows kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="96a67-138">If the `userNamePasswordValidationMode` value is not set, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses Windows authentication instead of the custom user name and password validator.</span></span>  
  
    7.  <span data-ttu-id="96a67-139">Ayarlama `customUserNamePasswordValidatorType` için özel bir kullanıcı adı ve parola Doğrulayıcı temsil eden tür.</span><span class="sxs-lookup"><span data-stu-id="96a67-139">Set the `customUserNamePasswordValidatorType` to the type that represents your custom user name and password validator.</span></span>  
  
     <span data-ttu-id="96a67-140">Aşağıdaki örnekte gösterildiği `<serviceCredentials>` bu noktaya parça.</span><span class="sxs-lookup"><span data-stu-id="96a67-140">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>  
  
    ```xml  
    <serviceCredentials>  
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />  
    </serviceCredentials>  
    ```  
  
## <a name="example"></a><span data-ttu-id="96a67-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="96a67-141">Example</span></span>  
 <span data-ttu-id="96a67-142">Aşağıdaki kod örneğinde nasıl özel bir kullanıcı adı ve parola Doğrulayıcı oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="96a67-142">The following code example demonstrates how to create a custom user name and password validator.</span></span> <span data-ttu-id="96a67-143">Geçersiz kılmaları kod kullanmayın <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> bir üretim ortamında yöntemi.</span><span class="sxs-lookup"><span data-stu-id="96a67-143">Do not use the code that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="96a67-144">Kullanıcı adı ve parola çiftleri veritabanından alma de girer, özel kullanıcı adı ve parola doğrulama düzeni, kodu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="96a67-144">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>  
  
 [!code-csharp[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
 [!code-vb[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]  
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="96a67-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="96a67-145">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>  
 [<span data-ttu-id="96a67-146">Nasıl yapılır: ASP.NET üyelik sağlayıcısı kullanın</span><span class="sxs-lookup"><span data-stu-id="96a67-146">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 [<span data-ttu-id="96a67-147">Kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="96a67-147">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)
