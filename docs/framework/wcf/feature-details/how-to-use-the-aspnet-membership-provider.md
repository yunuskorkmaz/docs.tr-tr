---
title: 'Nasıl yapılır: ASP.NET Üyelik Sağlayıcısını Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: b86287440b2265349b853265f12a2f6e48b4cff3
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045279"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a><span data-ttu-id="d8deb-102">Nasıl yapılır: ASP.NET Üyelik Sağlayıcısını Kullanma</span><span class="sxs-lookup"><span data-stu-id="d8deb-102">How to: Use the ASP.NET Membership Provider</span></span>

<span data-ttu-id="d8deb-103">ASP.NET üyelik sağlayıcısı, ASP.NET geliştiricilerinin kullanıcıların benzersiz Kullanıcı adı ve parola bileşimleri oluşturmalarına izin veren Web siteleri oluşturmalarına olanak tanıyan bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="d8deb-103">The ASP.NET membership provider is a feature that enables ASP.NET developers to create Web sites that allow users to create unique user name and password combinations.</span></span> <span data-ttu-id="d8deb-104">Bu tesisle, tüm kullanıcılar sitesiyle bir hesap oluşturabilir ve siteye ve hizmetlerine özel erişim için oturum açabilir.</span><span class="sxs-lookup"><span data-stu-id="d8deb-104">With this facility, any user can establish an account with the site, and sign in for exclusive access to the site and its services.</span></span> <span data-ttu-id="d8deb-105">Bu, kullanıcıların bir Windows etki alanında hesapları olmasını gerektiren Windows Güvenliği ' ne farklıdır.</span><span class="sxs-lookup"><span data-stu-id="d8deb-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="d8deb-106">Bunun yerine, kimlik bilgilerini (Kullanıcı adı/parola bileşimi) sağlayan tüm kullanıcılar siteyi ve hizmetlerini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="d8deb-106">Instead, any user that supplies his or her credentials (the user name/password combination) can use the site and its services.</span></span>

<span data-ttu-id="d8deb-107">Örnek bir uygulama için bkz. [Üyelik ve rol sağlayıcısı](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span><span class="sxs-lookup"><span data-stu-id="d8deb-107">For a sample application, see [Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="d8deb-108">ASP.NET rol sağlayıcısı özelliğini kullanma hakkında daha fazla bilgi için bkz [. nasıl yapılır: ASP.NET rol sağlayıcısını bir hizmetle](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)birlikte kullanın.</span><span class="sxs-lookup"><span data-stu-id="d8deb-108">For information about using the ASP.NET role provider feature, see [How to: Use the ASP.NET Role Provider with a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span>

<span data-ttu-id="d8deb-109">Üyelik özelliği, Kullanıcı bilgilerini depolamak için bir SQL Server veritabanı kullanılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d8deb-109">The membership feature requires using a SQL Server database to store the user information.</span></span> <span data-ttu-id="d8deb-110">Bu özellik ayrıca, parolasını unutduğunuz tüm kullanıcılar için soru sorma yöntemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="d8deb-110">The feature also includes methods for prompting with a question any users who have forgotten their password.</span></span>

<span data-ttu-id="d8deb-111">Windows Communication Foundation (WCF) geliştiricileri, güvenlik amacıyla bu özelliklerden yararlanabilir.</span><span class="sxs-lookup"><span data-stu-id="d8deb-111">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="d8deb-112">Bir WCF uygulamasıyla tümleştirildiğinde, kullanıcıların WCF istemci uygulamasına bir Kullanıcı adı/parola bileşimi sağlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d8deb-112">When integrated into an WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="d8deb-113">Verileri WCF hizmetine aktarmak için, <xref:System.ServiceModel.WSHttpBinding> (yapılandırmada `UserName` [ \<, WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) gibi Kullanıcı adı/parola kimlik bilgilerini destekleyen bir bağlama kullanın ve istemci kimlik bilgileri türünü olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d8deb-113">To transfer the data to the WCF service, use a binding that supports user name/password credentials, such as the <xref:System.ServiceModel.WSHttpBinding> (in configuration, the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) and set the client credential type to `UserName`.</span></span> <span data-ttu-id="d8deb-114">Hizmette, WCF güvenliği kullanıcının kimliğini Kullanıcı adı ve parolaya göre doğrular ve ayrıca ASP.NET rolü tarafından belirtilen rolü de atar.</span><span class="sxs-lookup"><span data-stu-id="d8deb-114">On the service, WCF security authenticates the user based on the user name and password, and also assigns the role specified by the ASP.NET role.</span></span>

> [!NOTE]
> <span data-ttu-id="d8deb-115">WCF, veritabanını Kullanıcı adı/parola birleşimleri veya diğer kullanıcı bilgileriyle doldurmak için yöntemler sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="d8deb-115">WCF does not provide methods to populate the database with user name/password combinations or other user information.</span></span>

### <a name="to-configure-the-membership-provider"></a><span data-ttu-id="d8deb-116">Üyelik sağlayıcısını yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="d8deb-116">To configure the membership provider</span></span>

1. <span data-ttu-id="d8deb-117">Web. config dosyasında, <`system.web`> öğesi altında, bir <`membership`> öğesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d8deb-117">In the Web.config file, under the <`system.web`> element, create a <`membership`> element.</span></span>

2. <span data-ttu-id="d8deb-118">Öğesi altında bir `<providers>` öğesi oluşturun. `<membership>`</span><span class="sxs-lookup"><span data-stu-id="d8deb-118">Under the `<membership>` element, create a `<providers>` element.</span></span>

3. <span data-ttu-id="d8deb-119"><`providers`> Öğesinin bir alt öğesi olarak, sağlayıcı koleksiyonunu temizlemek `<clear />` için bir öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d8deb-119">As a child to the <`providers`> element, add a `<clear />` element to flush the collection of providers.</span></span>

4. <span data-ttu-id="d8deb-120">`connectionStringName` `name` `enablePasswordRetrieval` `requiresQuestionAndAnswer` Öğesialtında`applicationName`, aşağıdaki öznitelikleri uygun değerlere`add`ayarlanmış bir < > öğesi oluşturun:, `type`,,,, `enablePasswordReset`, `<clear />` , `requiresUniqueEmail`ve .`passwordFormat`</span><span class="sxs-lookup"><span data-stu-id="d8deb-120">Under the `<clear />` element, create an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer`, `requiresUniqueEmail`, and `passwordFormat`.</span></span> <span data-ttu-id="d8deb-121">`name` Özniteliği daha sonra yapılandırma dosyasında bir değer olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d8deb-121">The `name` attribute is used later as a value in the configuration file.</span></span> <span data-ttu-id="d8deb-122">Aşağıdaki örnek olarak `SqlMembershipProvider`ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d8deb-122">The following example sets it to `SqlMembershipProvider`.</span></span>

    <span data-ttu-id="d8deb-123">Aşağıdaki örnek yapılandırma bölümünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="d8deb-123">The following example shows the configuration section.</span></span>

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

### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a><span data-ttu-id="d8deb-124">Hizmet güvenliğini Kullanıcı adı/parola birleşimini kabul edecek şekilde yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="d8deb-124">To configure service security to accept the user name/password combination</span></span>

1. <span data-ttu-id="d8deb-125">Yapılandırma dosyasında, [ \<System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) öğesinin altında bir [ \<Bindings >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d8deb-125">In the configuration file, under the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>

2. <span data-ttu-id="d8deb-126">Bağlamalar bölümüne bir [ \<WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d8deb-126">Add a [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) to the bindings section.</span></span> <span data-ttu-id="d8deb-127">WCF bağlama öğesi oluşturma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Yapılandırmada](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)bir hizmet bağlaması belirtin.</span><span class="sxs-lookup"><span data-stu-id="d8deb-127">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>

3. <span data-ttu-id="d8deb-128">Ayarlama `mode` özniteliği `<security>` öğesine `Message`.</span><span class="sxs-lookup"><span data-stu-id="d8deb-128">Set the `mode` attribute of the `<security>` element to `Message`.</span></span>

4. <span data-ttu-id="d8deb-129">`UserName`< `clientCredentialType` >Öğesininözniteliğiniolarakayarlayın`message`.</span><span class="sxs-lookup"><span data-stu-id="d8deb-129">Set the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span> <span data-ttu-id="d8deb-130">Bu, bir Kullanıcı adı/parola çiftinin istemci kimlik bilgileri olarak kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d8deb-130">This specifies that a user name/password pair will be used as the client's credential.</span></span>

    <span data-ttu-id="d8deb-131">Aşağıdaki örnek, bağlamanın yapılandırma kodunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d8deb-131">The following example shows the configuration code for the binding.</span></span>

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

### <a name="to-configure-a-service-to-use-the-membership-provider"></a><span data-ttu-id="d8deb-132">Üyelik sağlayıcısını kullanmak üzere bir hizmeti yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="d8deb-132">To configure a service to use the membership provider</span></span>

1. <span data-ttu-id="d8deb-133">`<system.serviceModel>` Öğesi için alt öğe olarak, [ \<> bir davranış](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) ekleyin</span><span class="sxs-lookup"><span data-stu-id="d8deb-133">As a child to the `<system.serviceModel>` element, add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element</span></span>

2. <span data-ttu-id="d8deb-134"><`behaviors`> Öğesine bir [ \<servicedavranışlar >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d8deb-134">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>

3. <span data-ttu-id="d8deb-135">`name` [ Bir\<davranış >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) ekleyin ve özniteliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d8deb-135">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>

4. <span data-ttu-id="d8deb-136"><`behavior`> Öğesine bir [ \<ServiceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d8deb-136">Add a [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) to the <`behavior`> element.</span></span>

5. <span data-ttu-id="d8deb-137">`<serviceCredentials>` Öğesine bir [ \<UserNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d8deb-137">Add a [\<userNameAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) to the `<serviceCredentials>` element.</span></span>

6. <span data-ttu-id="d8deb-138">`userNamePasswordValidationMode` Özniteliğini olarak`MembershipProvider`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d8deb-138">Set the `userNamePasswordValidationMode` attribute to `MembershipProvider`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="d8deb-139">`userNamePasswordValidationMode` Değer ayarlanmamışsa, WCF ASP.NET üyelik sağlayıcısı yerine Windows kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="d8deb-139">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the ASP.NET membership provider.</span></span>

7. <span data-ttu-id="d8deb-140">`membershipProviderName` Özniteliğini sağlayıcının adına ayarlayın (Bu konunun ilk yordamında sağlayıcı eklenirken belirtilir).</span><span class="sxs-lookup"><span data-stu-id="d8deb-140">Set the `membershipProviderName` attribute to the name of the provider (specified when adding the provider in the first procedure in this topic).</span></span> <span data-ttu-id="d8deb-141">Aşağıdaki örnek bu noktaya olan `<serviceCredentials>` parçayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="d8deb-141">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>

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

## <a name="example"></a><span data-ttu-id="d8deb-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="d8deb-142">Example</span></span>

<span data-ttu-id="d8deb-143">Aşağıdaki kod, ASP üyeliği özelliğini kullanan bir hizmetin yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d8deb-143">The following code shows the configuration for a service that uses the ASP membership feature.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d8deb-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8deb-144">See also</span></span>

- [<span data-ttu-id="d8deb-145">Nasıl yapılır: ASP.NET rol sağlayıcısını bir hizmetle kullanma</span><span class="sxs-lookup"><span data-stu-id="d8deb-145">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [<span data-ttu-id="d8deb-146">Üyelik ve Rol Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="d8deb-146">Membership and Role Provider</span></span>](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
