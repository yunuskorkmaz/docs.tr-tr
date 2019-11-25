---
title: 'Nasıl yapılır: Özel Bir Kullanıcı Adı ve Parola Doğrulayıcı Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
ms.openlocfilehash: 3d01a29671f42e80fdb7ca45223007aa60273ba9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283254"
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="405b0-102">Nasıl yapılır: Özel Bir Kullanıcı Adı ve Parola Doğrulayıcı Kullanma</span><span class="sxs-lookup"><span data-stu-id="405b0-102">How to: Use a Custom User Name and Password Validator</span></span>

<span data-ttu-id="405b0-103">Varsayılan olarak, kimlik doğrulaması için bir Kullanıcı adı ve parola kullanıldığında, Windows Communication Foundation (WCF) Kullanıcı adı ve parolayı doğrulamak için Windows 'u kullanır.</span><span class="sxs-lookup"><span data-stu-id="405b0-103">By default, when a user name and password is used for authentication, Windows Communication Foundation (WCF) uses Windows to validate the user name and password.</span></span> <span data-ttu-id="405b0-104">Ancak, WCF, Özel Kullanıcı adı ve parola kimlik doğrulama şemaları için, *doğrulayıcılar*olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="405b0-104">However, WCF allows for custom user name and password authentication schemes, also known as *validators*.</span></span> <span data-ttu-id="405b0-105">Özel bir Kullanıcı adı ve parola doğrulayıcısı eklemek için, <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> türeten bir sınıf oluşturun ve ardından yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="405b0-105">To incorporate a custom user name and password validator, create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> and then configure it.</span></span>

<span data-ttu-id="405b0-106">Örnek bir uygulama için bkz. [Kullanıcı adı parola doğrulayıcısı](../samples/user-name-password-validator.md).</span><span class="sxs-lookup"><span data-stu-id="405b0-106">For a sample application, see [User Name Password Validator](../samples/user-name-password-validator.md).</span></span>

### <a name="to-create-a-custom-user-name-and-password-validator"></a><span data-ttu-id="405b0-107">Özel bir Kullanıcı adı ve parola doğrulayıcısı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="405b0-107">To create a custom user name and password validator</span></span>

1. <span data-ttu-id="405b0-108"><xref:System.IdentityModel.Selectors.UserNamePasswordValidator>türeten bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="405b0-108">Create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span>

    [!code-csharp[C_CustomUsernameAndPasswordValidator#3](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]

2. <span data-ttu-id="405b0-109"><xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> yöntemini geçersiz kılarak özel kimlik doğrulama düzenini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="405b0-109">Implement the custom authentication scheme by overriding the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>

    <span data-ttu-id="405b0-110">Aşağıdaki örnekte, bir üretim ortamındaki <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> yöntemini geçersiz kılan kodu kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="405b0-110">Do not use the code in the following example that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="405b0-111">Kodu, bir veritabanından Kullanıcı adı ve parola çiftleri almayı içerebilecek özel Kullanıcı adı ve parola doğrulama şemanızın yerine koyun.</span><span class="sxs-lookup"><span data-stu-id="405b0-111">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>

    <span data-ttu-id="405b0-112">Kimlik doğrulama hatalarını istemciye geri döndürmek için <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> yönteminde bir <xref:System.ServiceModel.FaultException> oluşturun.</span><span class="sxs-lookup"><span data-stu-id="405b0-112">To return authentication errors back to the client, throw a <xref:System.ServiceModel.FaultException> in the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>

    [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]

### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="405b0-113">Bir hizmeti özel Kullanıcı adı ve parola doğrulayıcısı kullanacak şekilde yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="405b0-113">To configure a service to use a custom user name and password validator</span></span>

1. <span data-ttu-id="405b0-114">HTTP (S) üzerinden herhangi bir aktarım veya aktarım düzeyi güvenliği üzerinde ileti güvenliği kullanan bir bağlama yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="405b0-114">Configure a binding that uses message security over any transport or transport-level security over HTTP(S).</span></span>

    <span data-ttu-id="405b0-115">İleti güvenliği kullanırken, [\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)gibi sistem tarafından belirtilen bağlamalardan birini veya ileti güvenliğini ve `UserName` kimlik bilgisi türünü destekleyen bir [\<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="405b0-115">When using message security, add one of the system-provided bindings, such as a  [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), or a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) that supports message security and the `UserName` credential type.</span></span>

    <span data-ttu-id="405b0-116">HTTP (S) üzerinden aktarım düzeyi güvenliği kullanırken, [\<wshttpbinding >](../../configure-apps/file-schema/wcf/wshttpbinding.md) veya [\<basicHttpBinding >](../../configure-apps/file-schema/wcf/basichttpbinding.md), [\<NETTCPBINDING >](../../configure-apps/file-schema/wcf/nettcpbinding.md) veya http (S) ve\<kimlik doğrulama düzenini kullanan bir [> CustomBinding `Basic`](../../configure-apps/file-schema/wcf/custombinding.md) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="405b0-116">When using transport-level security over HTTP(S), add either the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md), a [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) or a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) that uses HTTP(S) and the `Basic` authentication scheme.</span></span>

    > [!NOTE]
    > <span data-ttu-id="405b0-117">.NET Framework 3,5 veya sonraki sürümleri kullanırken ileti ve aktarım güvenliği ile özel bir Kullanıcı adı ve parola doğrulayıcısı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="405b0-117">When using .NET Framework 3.5 or later versions, you can use a custom username and password validator with message and transport security.</span></span> <span data-ttu-id="405b0-118">WinFX ile özel bir Kullanıcı adı ve parola doğrulayıcısı yalnızca ileti güvenliği ile birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="405b0-118">With WinFX, a custom username and password validator can only be used with message security.</span></span>

    > [!TIP]
    > <span data-ttu-id="405b0-119">Bu bağlamda \<netTcpBinding > kullanma hakkında daha fazla bilgi için bkz [\<güvenlik >](../../configure-apps/file-schema/wcf/security-of-nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="405b0-119">For more information on using \<netTcpBinding> in this context, see [\<security>](../../configure-apps/file-schema/wcf/security-of-nettcpbinding.md).</span></span>

    1. <span data-ttu-id="405b0-120">Yapılandırma dosyasında, [\<System. serviceModel >](../../configure-apps/file-schema/wcf/system-servicemodel.md) öğesinin altında, bir [\<bağlamaları >](../../configure-apps/file-schema/wcf/bindings.md) öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="405b0-120">In the configuration file, under the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) element.</span></span>

    2. <span data-ttu-id="405b0-121">Bağlamalar bölümüne [\<wsHttpBinding >](../../configure-apps/file-schema/wcf/wshttpbinding.md) veya [\<BasicHttpBinding >](../../configure-apps/file-schema/wcf/basichttpbinding.md) öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="405b0-121">Add a [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) element to the bindings section.</span></span> <span data-ttu-id="405b0-122">WCF bağlama öğesi oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: yapılandırmada hizmet bağlaması belirtme](../how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="405b0-122">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../how-to-specify-a-service-binding-in-configuration.md).</span></span>

    3. <span data-ttu-id="405b0-123">[\<güvenlik >](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) `mode` özniteliğini veya [\<güvenlik >](../../configure-apps/file-schema/wcf/security-of-basichttpbinding.md) `Message`, `Transport`veya `TransportWithMessageCredential`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="405b0-123">Set the `mode` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) or [\<security>](../../configure-apps/file-schema/wcf/security-of-basichttpbinding.md) to `Message`, `Transport`, or `TransportWithMessageCredential`.</span></span>

    4. <span data-ttu-id="405b0-124">[\<iletisinin >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) veya [\<taşıma >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md)`clientCredentialType` özniteliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="405b0-124">Set the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) or [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span></span>

        <span data-ttu-id="405b0-125">İleti güvenliği kullanırken, [\<iletisinin >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) `clientCredentialType` özniteliğini `UserName`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="405b0-125">When using message security, set the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) to `UserName`.</span></span>

        <span data-ttu-id="405b0-126">HTTP (S) üzerinden aktarım düzeyi güvenliği kullanırken, [\<taşıma >](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) veya [\<taşıma >](../../configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) `clientCredentialType` özniteliğini `Basic`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="405b0-126">When using transport-level security over HTTP(S), set the `clientCredentialType` attribute of the [\<transport>](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) or [\<transport>](../../configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) to `Basic`.</span></span>

        > [!NOTE]
        > <span data-ttu-id="405b0-127">Bir WCF hizmeti, aktarım düzeyi güvenlik kullanarak Internet Information Services (IIS) içinde barındırılıyorsa ve <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> özelliği <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>olarak ayarlandığında, özel kimlik doğrulama düzeni Windows kimlik doğrulamasının bir alt kümesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="405b0-127">When a WCF service is hosted in Internet Information Services (IIS) using transport-level security and the <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> property is set to <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, the custom authentication scheme uses a subset of Windows authentication.</span></span> <span data-ttu-id="405b0-128">Bunun nedeni, bu senaryoda IIS, özel kimlik doğrulayıcı çağırma WCF öncesinde Windows kimlik doğrulaması gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="405b0-128">That is because in this scenario, IIS performs Windows authentication prior to WCF invoking the custom authenticator.</span></span>

    <span data-ttu-id="405b0-129">WCF bağlama öğesi oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: yapılandırmada hizmet bağlaması belirtme](../how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="405b0-129">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../how-to-specify-a-service-binding-in-configuration.md).</span></span>

    <span data-ttu-id="405b0-130">Aşağıdaki örnekte, bağlama için yapılandırma kodu gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="405b0-130">The following example shows the configuration code for the binding:</span></span>

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

2. <span data-ttu-id="405b0-131">Gelen <xref:System.IdentityModel.Tokens.UserNameSecurityToken> güvenlik belirteçleri için Kullanıcı adı ve parola çiftlerini doğrulamak üzere özel bir Kullanıcı adı ve parola doğrulayıcısı kullanıldığını belirten bir davranış yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="405b0-131">Configure a behavior that specifies that a custom user name and password validator is used to validate user name and password pairs for incoming <xref:System.IdentityModel.Tokens.UserNameSecurityToken> security tokens.</span></span>

    1. <span data-ttu-id="405b0-132">[\<System. serviceModel >](../../configure-apps/file-schema/wcf/system-servicemodel.md) öğesinin bir alt öğesi olarak [\<davranışlar >](../../configure-apps/file-schema/wcf/behaviors.md) öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="405b0-132">As a child to the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

    2. <span data-ttu-id="405b0-133">[\<davranışlar >](../../configure-apps/file-schema/wcf/behaviors.md) öğesine [>\<servicedavranışlar](../../configure-apps/file-schema/wcf/servicebehaviors.md) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="405b0-133">Add a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

    3. <span data-ttu-id="405b0-134">[\<behavior >](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) öğesi ekleyin ve `name` özniteliğini uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="405b0-134">Add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>

    4. <span data-ttu-id="405b0-135">[\<behavior >](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) öğesine [\<ServiceCredentials >](../../configure-apps/file-schema/wcf/servicecredentials.md) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="405b0-135">Add a [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) to the [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span></span>

    5. <span data-ttu-id="405b0-136">[\<serviceCredentials >](../../configure-apps/file-schema/wcf/servicecredentials.md) [\<UserNameAuthentication >](../../configure-apps/file-schema/wcf/usernameauthentication.md) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="405b0-136">Add a [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) to the [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md).</span></span>

    6. <span data-ttu-id="405b0-137">`userNamePasswordValidationMode` `Custom`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="405b0-137">Set the `userNamePasswordValidationMode` to `Custom`.</span></span>

        > [!IMPORTANT]
        > <span data-ttu-id="405b0-138">`userNamePasswordValidationMode` değeri ayarlanmamışsa, WCF özel Kullanıcı adı ve parola doğrulayıcısı yerine Windows kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="405b0-138">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the custom user name and password validator.</span></span>

    7. <span data-ttu-id="405b0-139">`customUserNamePasswordValidatorType`, Özel Kullanıcı adınızı ve parola doğrulayıcılarınızı temsil eden türe ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="405b0-139">Set the `customUserNamePasswordValidatorType` to the type that represents your custom user name and password validator.</span></span>

    <span data-ttu-id="405b0-140">Aşağıdaki örnek, `<serviceCredentials>` parçasını bu noktaya gösterir:</span><span class="sxs-lookup"><span data-stu-id="405b0-140">The following example shows the `<serviceCredentials>` fragment to this point:</span></span>

    ```xml
    <serviceCredentials>
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />
    </serviceCredentials>
    ```

## <a name="example"></a><span data-ttu-id="405b0-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="405b0-141">Example</span></span>

<span data-ttu-id="405b0-142">Aşağıdaki kod örneği, özel bir Kullanıcı adı ve parola doğrulayıcısı oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="405b0-142">The following code example demonstrates how to create a custom user name and password validator.</span></span> <span data-ttu-id="405b0-143">Bir üretim ortamındaki <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> yöntemi geçersiz kılan kodu kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="405b0-143">Do not use the code that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="405b0-144">Kodu, bir veritabanından Kullanıcı adı ve parola çiftleri almayı içerebilecek özel Kullanıcı adı ve parola doğrulama şemanızın yerine koyun.</span><span class="sxs-lookup"><span data-stu-id="405b0-144">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>

[!code-csharp[C_CustomUsernameAndPasswordValidator#1](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
[!code-vb[C_CustomUsernameAndPasswordValidator#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]

## <a name="see-also"></a><span data-ttu-id="405b0-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="405b0-145">See also</span></span>

- <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>
- [<span data-ttu-id="405b0-146">Nasıl yapılır: ASP.NET Üyelik Sağlayıcısını Kullanma</span><span class="sxs-lookup"><span data-stu-id="405b0-146">How to: Use the ASP.NET Membership Provider</span></span>](how-to-use-the-aspnet-membership-provider.md)
- [<span data-ttu-id="405b0-147">Kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="405b0-147">Authentication</span></span>](authentication-in-wcf.md)
