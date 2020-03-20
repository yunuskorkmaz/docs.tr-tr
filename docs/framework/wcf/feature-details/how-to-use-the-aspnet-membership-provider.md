---
title: 'Nasıl yapılır: ASP.NET Üyelik Sağlayıcısını Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: 5b15d56c7150a8478bc32651538903778e3b877d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184790"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a><span data-ttu-id="79967-102">Nasıl yapılır: ASP.NET Üyelik Sağlayıcısını Kullanma</span><span class="sxs-lookup"><span data-stu-id="79967-102">How to: Use the ASP.NET Membership Provider</span></span>

<span data-ttu-id="79967-103">ASP.NET üyelik sağlayıcısı, ASP.NET geliştiricilerin kullanıcıların benzersiz kullanıcı adı ve parola kombinasyonları oluşturmasına olanak tanıyan Web siteleri oluşturmasına olanak tanıyan bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="79967-103">The ASP.NET membership provider is a feature that enables ASP.NET developers to create Web sites that allow users to create unique user name and password combinations.</span></span> <span data-ttu-id="79967-104">Bu tesis sayesinde, herhangi bir kullanıcı site ile bir hesap kurabilir ve siteye ve hizmetlerine özel erişim için oturum açabilir.</span><span class="sxs-lookup"><span data-stu-id="79967-104">With this facility, any user can establish an account with the site, and sign in for exclusive access to the site and its services.</span></span> <span data-ttu-id="79967-105">Bu, kullanıcıların windows etki alanında hesapları olmasını gerektiren Windows güvenliğinin tam tersidir.</span><span class="sxs-lookup"><span data-stu-id="79967-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="79967-106">Bunun yerine, kimlik bilgilerini (kullanıcı adı/parola kombinasyonu) sağlayan herhangi bir kullanıcı siteyi ve hizmetlerini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="79967-106">Instead, any user that supplies their credentials (the user name/password combination) can use the site and its services.</span></span>

<span data-ttu-id="79967-107">Örnek bir uygulama için [Üyelik ve Rol Sağlayıcısı'na](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="79967-107">For a sample application, see [Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="79967-108">ASP.NET rol sağlayıcısının kullanımı hakkında bilgi için [bkz: ASP.NET Rol Sağlayıcısı'nı Hizmetle birlikte kullanın.](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)</span><span class="sxs-lookup"><span data-stu-id="79967-108">For information about using the ASP.NET role provider feature, see [How to: Use the ASP.NET Role Provider with a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span>

<span data-ttu-id="79967-109">Üyelik özelliği, kullanıcı bilgilerini depolamak için bir SQL Server veritabanı nı kullanmayı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="79967-109">The membership feature requires using a SQL Server database to store the user information.</span></span> <span data-ttu-id="79967-110">Bu özellik, parolalarını unutan kullanıcılara soru sorma yöntemlerini de içerir.</span><span class="sxs-lookup"><span data-stu-id="79967-110">The feature also includes methods for prompting with a question any users who have forgotten their password.</span></span>

<span data-ttu-id="79967-111">Windows Communication Foundation (WCF) geliştiricileri bu özelliklerden güvenlik amacıyla yararlanabilir.</span><span class="sxs-lookup"><span data-stu-id="79967-111">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="79967-112">Bir WCF uygulamasına entegre edildiğinde, kullanıcıların WCF istemci uygulamasına bir kullanıcı adı/parola kombinasyonu sağlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="79967-112">When integrated into an WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="79967-113">Verileri WCF hizmetine aktarmak için, <xref:System.ServiceModel.WSHttpBinding> (yapılandırmada, [ \<wsHttpBinding>) ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)gibi kullanıcı adı/parola kimlik bilgilerini destekleyen bir bağlama kullanın ve istemci kimlik bilgilerini . `UserName`</span><span class="sxs-lookup"><span data-stu-id="79967-113">To transfer the data to the WCF service, use a binding that supports user name/password credentials, such as the <xref:System.ServiceModel.WSHttpBinding> (in configuration, the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) and set the client credential type to `UserName`.</span></span> <span data-ttu-id="79967-114">Hizmette, WCF güvenliği kullanıcı adını ve parolasını temel alarak kullanıcının kimliğini doğrular ve ASP.NET rolütarafından belirtilen rolü atar.</span><span class="sxs-lookup"><span data-stu-id="79967-114">On the service, WCF security authenticates the user based on the user name and password, and also assigns the role specified by the ASP.NET role.</span></span>

> [!NOTE]
> <span data-ttu-id="79967-115">WCF, veritabanını kullanıcı adı/parola birleşimleri veya diğer kullanıcı bilgileriyle doldurmak için yöntemler sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="79967-115">WCF does not provide methods to populate the database with user name/password combinations or other user information.</span></span>

### <a name="to-configure-the-membership-provider"></a><span data-ttu-id="79967-116">Üyelik sağlayıcısını yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="79967-116">To configure the membership provider</span></span>

1. <span data-ttu-id="79967-117">Web.config dosyasında, <`system.web`> öğesi altında, `membership` <bir> öğesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="79967-117">In the Web.config file, under the <`system.web`> element, create a <`membership`> element.</span></span>

2. <span data-ttu-id="79967-118">Öğenin `<membership>` altında, `<providers>` bir öğe oluşturun.</span><span class="sxs-lookup"><span data-stu-id="79967-118">Under the `<membership>` element, create a `<providers>` element.</span></span>

3. <span data-ttu-id="79967-119"><`providers`> öğesi için bir çocuk `<clear />` olarak, sağlayıcıların toplama floş için bir öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="79967-119">As a child to the <`providers`> element, add a `<clear />` element to flush the collection of providers.</span></span>

4. <span data-ttu-id="79967-120">Öğe `<clear />` altında, uygun `add` değerlere ayarlanmış aşağıdaki öznitelikleri ile `name` `type`<`connectionStringName` `applicationName`> `enablePasswordRetrieval` `enablePasswordReset`öğesi `requiresQuestionAndAnswer` `requiresUniqueEmail`oluşturmak: `passwordFormat`, , , , , , , , ve .</span><span class="sxs-lookup"><span data-stu-id="79967-120">Under the `<clear />` element, create an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer`, `requiresUniqueEmail`, and `passwordFormat`.</span></span> <span data-ttu-id="79967-121">Öznitelik `name` daha sonra yapılandırma dosyasında bir değer olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="79967-121">The `name` attribute is used later as a value in the configuration file.</span></span> <span data-ttu-id="79967-122">Aşağıdaki örnekte , `SqlMembershipProvider`''</span><span class="sxs-lookup"><span data-stu-id="79967-122">The following example sets it to `SqlMembershipProvider`.</span></span>

    <span data-ttu-id="79967-123">Aşağıdaki örnekte yapılandırma bölümü gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="79967-123">The following example shows the configuration section.</span></span>

    ```xml
    <!-- Configure the Sql Membership Provider -->
    <membership defaultProvider="SqlMembershipProvider" userIsOnlineTimeWindow="15">
      <providers>
        <clear />
          <add
            name="SqlMembershipProvider"
            type="System.Web.Security.SqlMembershipProvider"
            connectionStringName="SqlConn"
            applicationName="MembershipAndRoleProviderSample"
            enablePasswordRetrieval="false"
            enablePasswordReset="false"
            requiresQuestionAndAnswer="false"
            requiresUniqueEmail="true"
            passwordFormat="Hashed" />
      </providers>
    </membership>
    ```

### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a><span data-ttu-id="79967-124">Kullanıcı adı/parola birleşimini kabul etmek için hizmet güvenliğini yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="79967-124">To configure service security to accept the user name/password combination</span></span>

1. <span data-ttu-id="79967-125">Yapılandırma dosyasında, [ \<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) öğesi altında, [ \<bir bağlama>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="79967-125">In the configuration file, under the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>

2. <span data-ttu-id="79967-126">Bağlayıcılar bölümüne [ \<bir wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="79967-126">Add a [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) to the bindings section.</span></span> <span data-ttu-id="79967-127">WCF bağlama öğesi oluşturma hakkında daha fazla bilgi için [bkz: Yapılandırmada Hizmet Bağlama belirtin.](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="79967-127">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>

3. <span data-ttu-id="79967-128">Öğenin `mode` özniteliğini `<security>` `Message`.</span><span class="sxs-lookup"><span data-stu-id="79967-128">Set the `mode` attribute of the `<security>` element to `Message`.</span></span>

4. <span data-ttu-id="79967-129"><`clientCredentialType` `message`> öğesinin özniteliğini `UserName`.</span><span class="sxs-lookup"><span data-stu-id="79967-129">Set the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span> <span data-ttu-id="79967-130">Bu, istemcinin kimlik bilgisi olarak bir kullanıcı adı/parola çiftinin kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="79967-130">This specifies that a user name/password pair will be used as the client's credential.</span></span>

    <span data-ttu-id="79967-131">Aşağıdaki örnek, bağlama için yapılandırma kodunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="79967-131">The following example shows the configuration code for the binding.</span></span>

    ```xml
    <system.serviceModel>
    <bindings>
      <wsHttpBinding>
      <!-- Set up a binding that uses UserName as the client credential type -->
        <binding name="MembershipBinding">
          <security mode ="Message">
            <message clientCredentialType ="UserName"/>
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    </system.serviceModel>
    ```

### <a name="to-configure-a-service-to-use-the-membership-provider"></a><span data-ttu-id="79967-132">Üyelik sağlayıcısını kullanmak için bir hizmeti yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="79967-132">To configure a service to use the membership provider</span></span>

1. <span data-ttu-id="79967-133">Öğeye bir alt öğe [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) olarak, bir davranış>öğesi ekleyin `<system.serviceModel>`</span><span class="sxs-lookup"><span data-stu-id="79967-133">As a child to the `<system.serviceModel>` element, add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element</span></span>

2. <span data-ttu-id="79967-134"><`behaviors`> öğesine [ \<bir hizmetDavranışı>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="79967-134">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>

3. <span data-ttu-id="79967-135">[ \<Davranış>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) ekleyin ve `name` özniteliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="79967-135">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>

4. <span data-ttu-id="79967-136"><`behavior`> öğesine [ \<>bir hizmet Kimlik Bilgileri](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="79967-136">Add a [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) to the <`behavior`> element.</span></span>

5. <span data-ttu-id="79967-137">Öğeye bir [ \<kullanıcıAdıKimlik>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) ekleyin. `<serviceCredentials>`</span><span class="sxs-lookup"><span data-stu-id="79967-137">Add a [\<userNameAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) to the `<serviceCredentials>` element.</span></span>

6. <span data-ttu-id="79967-138">Özniteliği `userNamePasswordValidationMode` `MembershipProvider`' ne göre ayarlayın</span><span class="sxs-lookup"><span data-stu-id="79967-138">Set the `userNamePasswordValidationMode` attribute to `MembershipProvider`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="79967-139">`userNamePasswordValidationMode` Değer ayarlı değilse, WCF ASP.NET üyelik sağlayıcısı yerine Windows kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="79967-139">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the ASP.NET membership provider.</span></span>

7. <span data-ttu-id="79967-140">`membershipProviderName` Özniteliği sağlayıcının adına ayarlayın (bu konudaki ilk yordamda sağlayıcı eklerken belirtin).</span><span class="sxs-lookup"><span data-stu-id="79967-140">Set the `membershipProviderName` attribute to the name of the provider (specified when adding the provider in the first procedure in this topic).</span></span> <span data-ttu-id="79967-141">Aşağıdaki örnek, `<serviceCredentials>` bu noktaya parçayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="79967-141">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>

    ```xml
    <behaviors>
       <serviceBehaviors>
          <behavior name="MyServiceBehavior">
             <serviceCredentials>
                <userNameAuthentication
                userNamePasswordValidationMode="MembershipProvider"
                membershipProviderName="SqlMembershipProvider" />
             </serviceCredentials>
          </behavior>
       </serviceBehaviors>
    </behaviors>
    ```

## <a name="example"></a><span data-ttu-id="79967-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="79967-142">Example</span></span>

<span data-ttu-id="79967-143">Aşağıdaki kod, ASP üyelik özelliğini kullanan bir hizmetin yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="79967-143">The following code shows the configuration for a service that uses the ASP membership feature.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service behaviorConfiguration="MyServiceBehavior" name="Microsoft.Samples.GettingStarted.CalculatorService">
        <endpoint address="http://microsoft.com/WCFservices/Calculator"
          binding="wsHttpBinding" bindingConfiguration="MembershipBinding"
          name="ASPmemberUserName" contract="Microsoft.Samples.GettingStarted.ICalculator" />
      </service>
    </services>
    <behaviors>
      <serviceBehaviors>
        <behavior name="MyServiceBehavior">
          <serviceCredentials>
            <userNameAuthentication
              userNamePasswordValidationMode="MembershipProvider"
              membershipProviderName="SqlMembershipProvider" />
          </serviceCredentials>
        </behavior>
          </serviceBehaviors>
    </behaviors>
    <bindings>
      <wsHttpBinding>
        <binding name="MembershipBinding">
          <security mode="Message">
            <message clientCredentialType="UserName" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="79967-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79967-144">See also</span></span>

- [<span data-ttu-id="79967-145">Nasıl yapılır: ASP.NET Rol Sağlayıcısını Bir Hizmetle Kullanma</span><span class="sxs-lookup"><span data-stu-id="79967-145">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [<span data-ttu-id="79967-146">Üyelik ve Rol Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="79967-146">Membership and Role Provider</span></span>](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
