---
title: 'Nasıl yapılır: Özel Bir Kullanıcı Adı ve Parola Doğrulayıcı Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
ms.openlocfilehash: 5ada34ca2d0d757ea333fed60aef179d6578356c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601185"
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="ae291-102">Nasıl yapılır: Özel Bir Kullanıcı Adı ve Parola Doğrulayıcı Kullanma</span><span class="sxs-lookup"><span data-stu-id="ae291-102">How to: Use a Custom User Name and Password Validator</span></span>

<span data-ttu-id="ae291-103">Varsayılan olarak, kimlik doğrulaması için bir Kullanıcı adı ve parola kullanıldığında, Windows Communication Foundation (WCF) Kullanıcı adı ve parolayı doğrulamak için Windows 'u kullanır.</span><span class="sxs-lookup"><span data-stu-id="ae291-103">By default, when a user name and password is used for authentication, Windows Communication Foundation (WCF) uses Windows to validate the user name and password.</span></span> <span data-ttu-id="ae291-104">Ancak, WCF, Özel Kullanıcı adı ve parola kimlik doğrulama şemaları için, *doğrulayıcılar*olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="ae291-104">However, WCF allows for custom user name and password authentication schemes, also known as *validators*.</span></span> <span data-ttu-id="ae291-105">Özel bir Kullanıcı adı ve parola doğrulayıcısı eklemek için, öğesinden türeten bir sınıf oluşturun <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> ve ardından yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="ae291-105">To incorporate a custom user name and password validator, create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> and then configure it.</span></span>

<span data-ttu-id="ae291-106">Örnek bir uygulama için bkz. [Kullanıcı adı parola doğrulayıcısı](../samples/user-name-password-validator.md).</span><span class="sxs-lookup"><span data-stu-id="ae291-106">For a sample application, see [User Name Password Validator](../samples/user-name-password-validator.md).</span></span>

### <a name="to-create-a-custom-user-name-and-password-validator"></a><span data-ttu-id="ae291-107">Özel bir Kullanıcı adı ve parola doğrulayıcısı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="ae291-107">To create a custom user name and password validator</span></span>

1. <span data-ttu-id="ae291-108">Öğesinden türetilen bir sınıf oluşturun <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> .</span><span class="sxs-lookup"><span data-stu-id="ae291-108">Create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span>

    [!code-csharp[C_CustomUsernameAndPasswordValidator#3](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]

2. <span data-ttu-id="ae291-109">Yöntemi geçersiz kılarak özel kimlik doğrulama düzenini uygulayın <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> .</span><span class="sxs-lookup"><span data-stu-id="ae291-109">Implement the custom authentication scheme by overriding the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>

    <span data-ttu-id="ae291-110">Aşağıdaki örnekte, <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> bir üretim ortamındaki yöntemi geçersiz kılan kodu kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="ae291-110">Do not use the code in the following example that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="ae291-111">Kodu, bir veritabanından Kullanıcı adı ve parola çiftleri almayı içerebilecek özel Kullanıcı adı ve parola doğrulama şemanızın yerine koyun.</span><span class="sxs-lookup"><span data-stu-id="ae291-111">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>

    <span data-ttu-id="ae291-112">Kimlik doğrulama hatalarını istemciye geri döndürmek için yönteminde bir oluşturun <xref:System.ServiceModel.FaultException> <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> .</span><span class="sxs-lookup"><span data-stu-id="ae291-112">To return authentication errors back to the client, throw a <xref:System.ServiceModel.FaultException> in the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>

    [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]

### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="ae291-113">Bir hizmeti özel Kullanıcı adı ve parola doğrulayıcısı kullanacak şekilde yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="ae291-113">To configure a service to use a custom user name and password validator</span></span>

1. <span data-ttu-id="ae291-114">HTTP (S) üzerinden herhangi bir aktarım veya aktarım düzeyi güvenliği üzerinde ileti güvenliği kullanan bir bağlama yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="ae291-114">Configure a binding that uses message security over any transport or transport-level security over HTTP(S).</span></span>

    <span data-ttu-id="ae291-115">İleti güvenliği kullanırken, [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) ileti güvenliğini ve kimlik bilgisi türünü destekleyen bir veya gibi sistem tarafından belirtilen bağlamalardan birini ekleyin `UserName` .</span><span class="sxs-lookup"><span data-stu-id="ae291-115">When using message security, add one of the system-provided bindings, such as a  [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md), or a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) that supports message security and the `UserName` credential type.</span></span>

    <span data-ttu-id="ae291-116">HTTP (S) üzerinden aktarım düzeyi güvenliği kullanırken, [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) http (s) ve kimlik doğrulama düzeni kullanan veya, a ya da bir öğesini ekleyin `Basic` .</span><span class="sxs-lookup"><span data-stu-id="ae291-116">When using transport-level security over HTTP(S), add either the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md), a [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) or a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) that uses HTTP(S) and the `Basic` authentication scheme.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ae291-117">.NET Framework 3,5 veya sonraki sürümleri kullanırken ileti ve aktarım güvenliği ile özel bir Kullanıcı adı ve parola doğrulayıcısı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ae291-117">When using .NET Framework 3.5 or later versions, you can use a custom username and password validator with message and transport security.</span></span> <span data-ttu-id="ae291-118">WinFX ile özel bir Kullanıcı adı ve parola doğrulayıcısı yalnızca ileti güvenliği ile birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ae291-118">With WinFX, a custom username and password validator can only be used with message security.</span></span>

    > [!TIP]
    > <span data-ttu-id="ae291-119">Bu bağlamda kullanma hakkında daha fazla bilgi için \<netTcpBinding> bkz [\<security>](../../configure-apps/file-schema/wcf/security-of-nettcpbinding.md) ..</span><span class="sxs-lookup"><span data-stu-id="ae291-119">For more information on using \<netTcpBinding> in this context, see [\<security>](../../configure-apps/file-schema/wcf/security-of-nettcpbinding.md).</span></span>

    1. <span data-ttu-id="ae291-120">Yapılandırma dosyasında, [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) öğesinin altına bir [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ae291-120">In the configuration file, under the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) element.</span></span>

    2. <span data-ttu-id="ae291-121">[\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) Bağlamalar bölümüne or öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ae291-121">Add a [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) element to the bindings section.</span></span> <span data-ttu-id="ae291-122">WCF bağlama öğesi oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: yapılandırmada hizmet bağlaması belirtme](../how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="ae291-122">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../how-to-specify-a-service-binding-in-configuration.md).</span></span>

    3. <span data-ttu-id="ae291-123">`mode` [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) Veya özniteliğini [\<security>](../../configure-apps/file-schema/wcf/security-of-basichttpbinding.md) `Message` , `Transport` veya `TransportWithMessageCredential` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ae291-123">Set the `mode` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) or [\<security>](../../configure-apps/file-schema/wcf/security-of-basichttpbinding.md) to `Message`, `Transport`, or `TransportWithMessageCredential`.</span></span>

    4. <span data-ttu-id="ae291-124">`clientCredentialType`Veya özniteliğini ayarlayın [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) [\<transport>](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="ae291-124">Set the `clientCredentialType` attribute of the [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) or [\<transport>](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span></span>

        <span data-ttu-id="ae291-125">İleti güvenliği kullanırken `clientCredentialType` , öğesinin özniteliğini [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) olarak ayarlayın `UserName` .</span><span class="sxs-lookup"><span data-stu-id="ae291-125">When using message security, set the `clientCredentialType` attribute of the [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) to `UserName`.</span></span>

        <span data-ttu-id="ae291-126">HTTP (S) üzerinden aktarım düzeyi güvenliği kullanırken, `clientCredentialType` [\<transport>](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) veya özniteliğini olarak ayarlayın [\<transport>](../../configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) `Basic` .</span><span class="sxs-lookup"><span data-stu-id="ae291-126">When using transport-level security over HTTP(S), set the `clientCredentialType` attribute of the [\<transport>](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) or [\<transport>](../../configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) to `Basic`.</span></span>

        > [!NOTE]
        > <span data-ttu-id="ae291-127">Bir WCF hizmeti, aktarım düzeyi güvenlik kullanılarak Internet Information Services (IIS) içinde barındırılıyorsa ve <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> özelliği olarak ayarlandığında <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom> , özel kimlik doğrulama düzeni Windows kimlik doğrulamasının bir alt kümesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ae291-127">When a WCF service is hosted in Internet Information Services (IIS) using transport-level security and the <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> property is set to <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, the custom authentication scheme uses a subset of Windows authentication.</span></span> <span data-ttu-id="ae291-128">Bunun nedeni, bu senaryoda IIS, özel kimlik doğrulayıcı çağırma WCF öncesinde Windows kimlik doğrulaması gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="ae291-128">That is because in this scenario, IIS performs Windows authentication prior to WCF invoking the custom authenticator.</span></span>

    <span data-ttu-id="ae291-129">WCF bağlama öğesi oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: yapılandırmada hizmet bağlaması belirtme](../how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="ae291-129">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../how-to-specify-a-service-binding-in-configuration.md).</span></span>

    <span data-ttu-id="ae291-130">Aşağıdaki örnekte, bağlama için yapılandırma kodu gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ae291-130">The following example shows the configuration code for the binding:</span></span>

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

2. <span data-ttu-id="ae291-131">Gelen güvenlik belirteçleri için Kullanıcı adı ve parola çiftlerini doğrulamak üzere özel bir Kullanıcı adı ve parola doğrulayıcısı kullanıldığını belirten bir davranış yapılandırın <xref:System.IdentityModel.Tokens.UserNameSecurityToken> .</span><span class="sxs-lookup"><span data-stu-id="ae291-131">Configure a behavior that specifies that a custom user name and password validator is used to validate user name and password pairs for incoming <xref:System.IdentityModel.Tokens.UserNameSecurityToken> security tokens.</span></span>

    1. <span data-ttu-id="ae291-132">Öğesi için alt öğe olarak [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) bir [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ae291-132">As a child to the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

    2. <span data-ttu-id="ae291-133">Öğesi öğesine ekleyin [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) .</span><span class="sxs-lookup"><span data-stu-id="ae291-133">Add a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

    3. <span data-ttu-id="ae291-134">Bir [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) öğesi ekleyin ve `name` özniteliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ae291-134">Add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>

    4. <span data-ttu-id="ae291-135">Öğesi öğesine ekleyin [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) .</span><span class="sxs-lookup"><span data-stu-id="ae291-135">Add a [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) to the [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span></span>

    5. <span data-ttu-id="ae291-136">[\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md)Öğesine öğesine ekleyin [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="ae291-136">Add a [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) to the [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md).</span></span>

    6. <span data-ttu-id="ae291-137">Öğesini `userNamePasswordValidationMode` olarak ayarlayın `Custom` .</span><span class="sxs-lookup"><span data-stu-id="ae291-137">Set the `userNamePasswordValidationMode` to `Custom`.</span></span>

        > [!IMPORTANT]
        > <span data-ttu-id="ae291-138">`userNamePasswordValidationMode`Değer ayarlanmamışsa, WCF özel Kullanıcı adı ve parola doğrulayıcısı yerine Windows kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="ae291-138">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the custom user name and password validator.</span></span>

    7. <span data-ttu-id="ae291-139">Öğesini `customUserNamePasswordValidatorType` Özel Kullanıcı adınızı ve parola doğrulayıcılarınızı temsil eden türe ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ae291-139">Set the `customUserNamePasswordValidatorType` to the type that represents your custom user name and password validator.</span></span>

    <span data-ttu-id="ae291-140">Aşağıdaki örnek `<serviceCredentials>` Bu noktaya olan parçayı gösterir:</span><span class="sxs-lookup"><span data-stu-id="ae291-140">The following example shows the `<serviceCredentials>` fragment to this point:</span></span>

    ```xml
    <serviceCredentials>
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />
    </serviceCredentials>
    ```

## <a name="example"></a><span data-ttu-id="ae291-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="ae291-141">Example</span></span>

<span data-ttu-id="ae291-142">Aşağıdaki kod örneği, özel bir Kullanıcı adı ve parola doğrulayıcısı oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="ae291-142">The following code example demonstrates how to create a custom user name and password validator.</span></span> <span data-ttu-id="ae291-143">Bir üretim ortamındaki yöntemi geçersiz kılan kodu kullanmayın <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> .</span><span class="sxs-lookup"><span data-stu-id="ae291-143">Do not use the code that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="ae291-144">Kodu, bir veritabanından Kullanıcı adı ve parola çiftleri almayı içerebilecek özel Kullanıcı adı ve parola doğrulama şemanızın yerine koyun.</span><span class="sxs-lookup"><span data-stu-id="ae291-144">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>

[!code-csharp[C_CustomUsernameAndPasswordValidator#1](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
[!code-vb[C_CustomUsernameAndPasswordValidator#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]

## <a name="see-also"></a><span data-ttu-id="ae291-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae291-145">See also</span></span>

- <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>
- [<span data-ttu-id="ae291-146">Nasıl yapılır: ASP.NET Üyelik Sağlayıcısını Kullanma</span><span class="sxs-lookup"><span data-stu-id="ae291-146">How to: Use the ASP.NET Membership Provider</span></span>](how-to-use-the-aspnet-membership-provider.md)
- [<span data-ttu-id="ae291-147">Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="ae291-147">Authentication</span></span>](authentication-in-wcf.md)
