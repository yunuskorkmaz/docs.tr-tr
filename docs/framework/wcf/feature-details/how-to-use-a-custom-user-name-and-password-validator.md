---
title: 'Nasıl yapılır: Özel Bir Kullanıcı Adı ve Parola Doğrulayıcı Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
ms.openlocfilehash: a7573e14d224e2ec861b301816d6d886fd147180
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401035"
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="170b5-102">Nasıl yapılır: Özel Bir Kullanıcı Adı ve Parola Doğrulayıcı Kullanma</span><span class="sxs-lookup"><span data-stu-id="170b5-102">How to: Use a Custom User Name and Password Validator</span></span>
<span data-ttu-id="170b5-103">Varsayılan olarak, Windows Communication Foundation (WCF) Windows kullanıcı adı ve parola kullanılabilir olduğunda kimlik doğrulaması için kullanıcı adını ve parolasını doğrulamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="170b5-103">By default, when a user name and password is used for authentication, Windows Communication Foundation (WCF) uses Windows to validate the user name and password.</span></span> <span data-ttu-id="170b5-104">Ancak, WCF özel kullanıcı adı ve parola kimlik doğrulaması düzeni için olarak da bilinen tanır *doğrulayıcıları*.</span><span class="sxs-lookup"><span data-stu-id="170b5-104">However, WCF allows for custom user name and password authentication schemes, also known as *validators*.</span></span> <span data-ttu-id="170b5-105">Özel kullanıcı adı ve parola Doğrulayıcı eklemek için türetilen bir sınıf oluşturma <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> ve ardından yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="170b5-105">To incorporate a custom user name and password validator, create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> and then configure it.</span></span>  
  
 <span data-ttu-id="170b5-106">Örnek bir uygulama için bkz: [kullanıcı Adıparola Doğrulayıcı](../../../../docs/framework/wcf/samples/user-name-password-validator.md).</span><span class="sxs-lookup"><span data-stu-id="170b5-106">For a sample application, see [User Name Password Validator](../../../../docs/framework/wcf/samples/user-name-password-validator.md).</span></span>  
  
### <a name="to-create-a-custom-user-name-and-password-validator"></a><span data-ttu-id="170b5-107">Özel kullanıcı adı ve parola Doğrulayıcı oluşturma</span><span class="sxs-lookup"><span data-stu-id="170b5-107">To create a custom user name and password validator</span></span>  
  
1.  <span data-ttu-id="170b5-108">Türetilen bir sınıf oluşturmanız <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span><span class="sxs-lookup"><span data-stu-id="170b5-108">Create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span>  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]  
  
2.  <span data-ttu-id="170b5-109">Özel kimlik doğrulama şeması geçersiz kılarak uygulamak <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="170b5-109">Implement the custom authentication scheme by overriding the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>  
  
     <span data-ttu-id="170b5-110">Kodu geçersiz kılan aşağıdaki örnekte kullanmayın <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> bir üretim ortamında yöntemi.</span><span class="sxs-lookup"><span data-stu-id="170b5-110">Do not use the code in the following example that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="170b5-111">Kullanıcı adı ve parola çiftleri veritabanından alınırken gerektirebilir, özel kullanıcı adı ve parola doğrulama şeması ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="170b5-111">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>  
  
     <span data-ttu-id="170b5-112">Kimlik doğrulama hataları istemciye geri dönmek için throw bir <xref:System.ServiceModel.FaultException> içinde <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="170b5-112">To return authentication errors back to the client, throw a <xref:System.ServiceModel.FaultException> in the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]  
  
### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="170b5-113">Özel kullanıcı adı ve parola Doğrulayıcı kullanmak için bir hizmeti yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="170b5-113">To configure a service to use a custom user name and password validator</span></span>  
  
1.  <span data-ttu-id="170b5-114">HTTP (S) üzerinden herhangi bir aktarım veya aktarım düzeyi güvenlik ileti güvenliği kullanan bir bağlama yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="170b5-114">Configure a binding that uses message security over any transport or transport-level security over HTTP(S).</span></span>  
  
     <span data-ttu-id="170b5-115">İleti güveliği kullanarak, bir sistem tarafından sağlanan bağlamalar gibi ekleyin. bir [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), veya bir [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) ileti güvenliği destekler ve `UserName` kimlik bilgisi türü.</span><span class="sxs-lookup"><span data-stu-id="170b5-115">When using message security, add one of the system-provided bindings, such as a  [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), or a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) that supports message security and the `UserName` credential type.</span></span>  
  
     <span data-ttu-id="170b5-116">HTTP (S) üzerinden aktarım düzeyi güvenlik kullanılırken ekleyin ya da [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) veya [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), [ \< netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) veya [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) HTTP (S) kullanan ve `Basic` kimlik doğrulama düzeni.</span><span class="sxs-lookup"><span data-stu-id="170b5-116">When using transport-level security over HTTP(S), add either the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), a [\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) or a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) that uses HTTP(S) and the `Basic` authentication scheme.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="170b5-117">Zaman [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] veya daha sonra kullanıldığında özel bir kullanıcı adı ve parola Doğrulayıcı ileti ve aktarım güvenliği ile kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="170b5-117">When [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] or later is used, you can use a custom username and password validator with message and transport security.</span></span> <span data-ttu-id="170b5-118">İle [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], özel bir kullanıcı adı ve parola Doğrulayıcı ile ileti güvenliği yalnızca kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="170b5-118">With [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], a custom username and password validator can only be used with message security.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="170b5-119">Kullanma hakkında daha fazla bilgi için \<netTcpBinding > Bu bağlam içinde görebilir [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="170b5-119">For more information on using \<netTcpBinding> in this context, see [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)</span></span>  
  
    1.  <span data-ttu-id="170b5-120">Yapılandırma dosyasında altında [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) öğe, Ekle bir [ \<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="170b5-120">In the configuration file, under the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
    2.  <span data-ttu-id="170b5-121">Ekleme bir [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) veya [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) bağlamalar bölümü öğesi.</span><span class="sxs-lookup"><span data-stu-id="170b5-121">Add a [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element to the bindings section.</span></span> <span data-ttu-id="170b5-122">Bir WCF bağlama öğesi oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: yapılandırmada hizmet bağlaması belirtme](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="170b5-122">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
    3.  <span data-ttu-id="170b5-123">Ayarlama `mode` özniteliği [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) veya [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) için `Message`, `Transport`, veya `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="170b5-123">Set the `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) or [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) to `Message`, `Transport`, or `TransportWithMessageCredential`.</span></span>  
  
    4.  <span data-ttu-id="170b5-124">Ayarlama `clientCredentialType` özniteliği [ \<ileti >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) veya [ \<aktarım >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="170b5-124">Set the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) or [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span></span>  
  
         <span data-ttu-id="170b5-125">İleti güveliği kullanarak, ayarlama `clientCredentialType` özniteliği [ \<ileti >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) için `UserName`.</span><span class="sxs-lookup"><span data-stu-id="170b5-125">When using message security, set the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) to `UserName`.</span></span>  
  
         <span data-ttu-id="170b5-126">HTTP (S) üzerinden aktarım düzeyi güvenlik kullanılırken ayarlamak `clientCredentialType` özniteliği [ \<aktarım >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) veya [ \<aktarım >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) için `Basic`.</span><span class="sxs-lookup"><span data-stu-id="170b5-126">When using transport-level security over HTTP(S), set the `clientCredentialType` attribute of the [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) or [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) to `Basic`.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="170b5-127">Bir WCF hizmeti Internet Information Services (aktarım düzeyi güvenlik kullanarak IIS içinde) barındırılan ne zaman ve <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> özelliği <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, Windows kimlik doğrulama kümesini özel kimlik doğrulama şeması kullanır.</span><span class="sxs-lookup"><span data-stu-id="170b5-127">When a WCF service is hosted in Internet Information Services (IIS) using transport-level security and the <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> property is set to <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, the custom authentication scheme uses a subset of Windows authentication.</span></span> <span data-ttu-id="170b5-128">Bu senaryoda, IIS WCF özel authenticator çağırmadan önce Windows kimlik doğrulaması gerçekleştirdiğinden olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="170b5-128">That is because in this scenario, IIS performs Windows authentication prior to WCF invoking the custom authenticator.</span></span>  
  
     <span data-ttu-id="170b5-129">Bir WCF bağlama öğesi oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: yapılandırmada hizmet bağlaması belirtme](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="170b5-129">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
     <span data-ttu-id="170b5-130">Aşağıdaki örnek, bağlama için yapılandırma kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="170b5-130">The following example shows the configuration code for the binding.</span></span>  
  
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
  
2.  <span data-ttu-id="170b5-131">Özel kullanıcı adı ve parola Doğrulayıcı gelen kullanıcı adı ve parola çiftlerini doğrulamak için kullanıldığını belirten bir davranış yapılandırma <xref:System.IdentityModel.Tokens.UserNameSecurityToken> güvenlik belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="170b5-131">Configure a behavior that specifies that a custom user name and password validator is used to validate user name and password pairs for incoming <xref:System.IdentityModel.Tokens.UserNameSecurityToken> security tokens.</span></span>  
  
    1.  <span data-ttu-id="170b5-132">Alt öğesi olarak [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) öğe, Ekle bir [ \<davranışları >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="170b5-132">As a child to the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>  
  
    2.  <span data-ttu-id="170b5-133">Ekleme bir [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) için [ \<davranışları >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="170b5-133">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>  
  
    3.  <span data-ttu-id="170b5-134">Ekleme bir [ \<davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) öğesi ve kümesi `name` özniteliği için uygun bir değer.</span><span class="sxs-lookup"><span data-stu-id="170b5-134">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>  
  
    4.  <span data-ttu-id="170b5-135">Ekleme bir [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) için [ \<davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="170b5-135">Add a [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) to the [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span></span>  
  
    5.  <span data-ttu-id="170b5-136">Ekleme bir [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) için [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="170b5-136">Add a [\<userNameAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) to the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>  
  
    6.  <span data-ttu-id="170b5-137">Ayarlama `userNamePasswordValidationMode` için `Custom`.</span><span class="sxs-lookup"><span data-stu-id="170b5-137">Set the `userNamePasswordValidationMode` to `Custom`.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="170b5-138">Varsa `userNamePasswordValidationMode` değeri ayarlanmazsa, WCF, Windows kimlik doğrulaması yerine özel bir kullanıcı adı ve parola Doğrulayıcı kullanır.</span><span class="sxs-lookup"><span data-stu-id="170b5-138">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the custom user name and password validator.</span></span>  
  
    7.  <span data-ttu-id="170b5-139">Ayarlama `customUserNamePasswordValidatorType` için özel kullanıcı adı ve parola Doğrulayıcı temsil eden tür.</span><span class="sxs-lookup"><span data-stu-id="170b5-139">Set the `customUserNamePasswordValidatorType` to the type that represents your custom user name and password validator.</span></span>  
  
     <span data-ttu-id="170b5-140">Aşağıdaki örnekte gösterildiği `<serviceCredentials>` bu noktaya parça.</span><span class="sxs-lookup"><span data-stu-id="170b5-140">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>  
  
    ```xml  
    <serviceCredentials>  
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />  
    </serviceCredentials>  
    ```  
  
## <a name="example"></a><span data-ttu-id="170b5-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="170b5-141">Example</span></span>  
 <span data-ttu-id="170b5-142">Aşağıdaki kod örneği, özel kullanıcı adı ve parola Doğrulayıcı oluşturma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="170b5-142">The following code example demonstrates how to create a custom user name and password validator.</span></span> <span data-ttu-id="170b5-143">Geçersiz kılmalar kod kullanmayın <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> bir üretim ortamında yöntemi.</span><span class="sxs-lookup"><span data-stu-id="170b5-143">Do not use the code that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="170b5-144">Kullanıcı adı ve parola çiftleri veritabanından alınırken gerektirebilir, özel kullanıcı adı ve parola doğrulama şeması ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="170b5-144">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>  
  
 [!code-csharp[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
 [!code-vb[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]  
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="170b5-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="170b5-145">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>  
 [<span data-ttu-id="170b5-146">Nasıl yapılır: ASP.NET Üyelik Sağlayıcısını Kullanma</span><span class="sxs-lookup"><span data-stu-id="170b5-146">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 [<span data-ttu-id="170b5-147">Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="170b5-147">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)
