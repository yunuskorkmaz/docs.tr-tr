---
title: 'Nasıl yapılır: ASP.NET Üyelik Sağlayıcısını Kullanma'
description: ASP.NET üyelik sağlayıcısı 'nın, kullanıcıların bir Windows etki alanı hesabına sahip olmadan erişim için Kullanıcı adı ve parola oluşturmalarına izin veren Web sitelerini nasıl desteklediğini öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: 6d527993dcf1fc5d5cd39bf22c3e772baf60e62f
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246733"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a><span data-ttu-id="b7f12-103">Nasıl yapılır: ASP.NET Üyelik Sağlayıcısını Kullanma</span><span class="sxs-lookup"><span data-stu-id="b7f12-103">How to: Use the ASP.NET Membership Provider</span></span>

<span data-ttu-id="b7f12-104">ASP.NET üyelik sağlayıcısı, ASP.NET geliştiricilerinin kullanıcıların benzersiz Kullanıcı adı ve parola bileşimleri oluşturmalarına izin veren Web siteleri oluşturmalarına olanak tanıyan bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="b7f12-104">The ASP.NET membership provider is a feature that enables ASP.NET developers to create Web sites that allow users to create unique user name and password combinations.</span></span> <span data-ttu-id="b7f12-105">Bu tesisle, tüm kullanıcılar sitesiyle bir hesap oluşturabilir ve siteye ve hizmetlerine özel erişim için oturum açabilir.</span><span class="sxs-lookup"><span data-stu-id="b7f12-105">With this facility, any user can establish an account with the site, and sign in for exclusive access to the site and its services.</span></span> <span data-ttu-id="b7f12-106">Bu, kullanıcıların bir Windows etki alanında hesapları olmasını gerektiren Windows Güvenliği ' ne farklıdır.</span><span class="sxs-lookup"><span data-stu-id="b7f12-106">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="b7f12-107">Bunun yerine, kimlik bilgilerini (Kullanıcı adı/parola birleşimi) sağlayan tüm kullanıcılar siteyi ve hizmetlerini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="b7f12-107">Instead, any user that supplies their credentials (the user name/password combination) can use the site and its services.</span></span>

<span data-ttu-id="b7f12-108">Örnek bir uygulama için bkz. [Üyelik ve rol sağlayıcısı](../samples/membership-and-role-provider.md).</span><span class="sxs-lookup"><span data-stu-id="b7f12-108">For a sample application, see [Membership and Role Provider](../samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="b7f12-109">ASP.NET rol sağlayıcısı özelliğini kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir hizmetle ASP.NET rol sağlayıcısını kullanma](how-to-use-the-aspnet-role-provider-with-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="b7f12-109">For information about using the ASP.NET role provider feature, see [How to: Use the ASP.NET Role Provider with a Service](how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span>

<span data-ttu-id="b7f12-110">Üyelik özelliği, Kullanıcı bilgilerini depolamak için bir SQL Server veritabanı kullanılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b7f12-110">The membership feature requires using a SQL Server database to store the user information.</span></span> <span data-ttu-id="b7f12-111">Bu özellik ayrıca, parolasını unutduğunuz tüm kullanıcılar için soru sorma yöntemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="b7f12-111">The feature also includes methods for prompting with a question any users who have forgotten their password.</span></span>

<span data-ttu-id="b7f12-112">Windows Communication Foundation (WCF) geliştiricileri, güvenlik amacıyla bu özelliklerden yararlanabilir.</span><span class="sxs-lookup"><span data-stu-id="b7f12-112">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="b7f12-113">Bir WCF uygulamasıyla tümleştirildiğinde, kullanıcıların WCF istemci uygulamasına bir Kullanıcı adı/parola bileşimi sağlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b7f12-113">When integrated into an WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="b7f12-114">Verileri WCF hizmetine aktarmak için, (yapılandırmada, içinde) gibi Kullanıcı adı/parola kimlik bilgilerini destekleyen bir bağlama kullanın <xref:System.ServiceModel.WSHttpBinding> [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) ve istemci kimlik bilgisi türünü olarak ayarlayın `UserName` .</span><span class="sxs-lookup"><span data-stu-id="b7f12-114">To transfer the data to the WCF service, use a binding that supports user name/password credentials, such as the <xref:System.ServiceModel.WSHttpBinding> (in configuration, the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md)) and set the client credential type to `UserName`.</span></span> <span data-ttu-id="b7f12-115">Hizmette, WCF güvenliği kullanıcının kimliğini Kullanıcı adı ve parolaya göre doğrular ve ayrıca ASP.NET rolü tarafından belirtilen rolü de atar.</span><span class="sxs-lookup"><span data-stu-id="b7f12-115">On the service, WCF security authenticates the user based on the user name and password, and also assigns the role specified by the ASP.NET role.</span></span>

> [!NOTE]
> <span data-ttu-id="b7f12-116">WCF, veritabanını Kullanıcı adı/parola birleşimleri veya diğer kullanıcı bilgileriyle doldurmak için yöntemler sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="b7f12-116">WCF does not provide methods to populate the database with user name/password combinations or other user information.</span></span>

### <a name="to-configure-the-membership-provider"></a><span data-ttu-id="b7f12-117">Üyelik sağlayıcısını yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="b7f12-117">To configure the membership provider</span></span>

1. <span data-ttu-id="b7f12-118">Web.config dosyasında, <`system.web`> öğesinin altında bir <`membership`> öğesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b7f12-118">In the Web.config file, under the <`system.web`> element, create a <`membership`> element.</span></span>

2. <span data-ttu-id="b7f12-119">Öğesi altında `<membership>` bir `<providers>` öğesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b7f12-119">Under the `<membership>` element, create a `<providers>` element.</span></span>

3. <span data-ttu-id="b7f12-120"><> öğesinin bir alt öğesi olarak `providers` , `<clear />` sağlayıcı koleksiyonunu temizlemek için bir öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b7f12-120">As a child to the <`providers`> element, add a `<clear />` element to flush the collection of providers.</span></span>

4. <span data-ttu-id="b7f12-121">Öğesi altında `<clear />` , `add` aşağıdaki öznitelikleri uygun değerlere ayarlanmış bir <> öğesi oluşturun: `name` , `type` ,, `connectionStringName` `applicationName` , `enablePasswordRetrieval` , `enablePasswordReset` , `requiresQuestionAndAnswer` , `requiresUniqueEmail` , ve `passwordFormat` .</span><span class="sxs-lookup"><span data-stu-id="b7f12-121">Under the `<clear />` element, create an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer`, `requiresUniqueEmail`, and `passwordFormat`.</span></span> <span data-ttu-id="b7f12-122">`name`Özniteliği daha sonra yapılandırma dosyasında bir değer olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b7f12-122">The `name` attribute is used later as a value in the configuration file.</span></span> <span data-ttu-id="b7f12-123">Aşağıdaki örnek olarak ayarlanır `SqlMembershipProvider` .</span><span class="sxs-lookup"><span data-stu-id="b7f12-123">The following example sets it to `SqlMembershipProvider`.</span></span>

    <span data-ttu-id="b7f12-124">Aşağıdaki örnek yapılandırma bölümünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="b7f12-124">The following example shows the configuration section.</span></span>

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

### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a><span data-ttu-id="b7f12-125">Hizmet güvenliğini Kullanıcı adı/parola birleşimini kabul edecek şekilde yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="b7f12-125">To configure service security to accept the user name/password combination</span></span>

1. <span data-ttu-id="b7f12-126">Yapılandırma dosyasında, [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) öğesinin altına bir [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b7f12-126">In the configuration file, under the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) element.</span></span>

2. <span data-ttu-id="b7f12-127">[\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md)Bağlamalar bölümüne bir ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b7f12-127">Add a [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) to the bindings section.</span></span> <span data-ttu-id="b7f12-128">WCF bağlama öğesi oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: yapılandırmada hizmet bağlaması belirtme](../how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="b7f12-128">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../how-to-specify-a-service-binding-in-configuration.md).</span></span>

3. <span data-ttu-id="b7f12-129">`mode` `<security>` Öğesinin özniteliğini olarak ayarlayın `Message` .</span><span class="sxs-lookup"><span data-stu-id="b7f12-129">Set the `mode` attribute of the `<security>` element to `Message`.</span></span>

4. <span data-ttu-id="b7f12-130">`clientCredentialType`<`message`> öğesinin özniteliğini olarak ayarlayın `UserName` .</span><span class="sxs-lookup"><span data-stu-id="b7f12-130">Set the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span> <span data-ttu-id="b7f12-131">Bu, bir Kullanıcı adı/parola çiftinin istemci kimlik bilgileri olarak kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b7f12-131">This specifies that a user name/password pair will be used as the client's credential.</span></span>

    <span data-ttu-id="b7f12-132">Aşağıdaki örnek, bağlamanın yapılandırma kodunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b7f12-132">The following example shows the configuration code for the binding.</span></span>

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

### <a name="to-configure-a-service-to-use-the-membership-provider"></a><span data-ttu-id="b7f12-133">Üyelik sağlayıcısını kullanmak üzere bir hizmeti yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="b7f12-133">To configure a service to use the membership provider</span></span>

1. <span data-ttu-id="b7f12-134">Öğesi için alt öğe olarak `<system.serviceModel>` , bir öğe ekleyin [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="b7f12-134">As a child to the `<system.serviceModel>` element, add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element</span></span>

2. <span data-ttu-id="b7f12-135">[\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md)<`behaviors`> öğesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b7f12-135">Add a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>

3. <span data-ttu-id="b7f12-136">Bir ekleyin [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) ve `name` özniteliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b7f12-136">Add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>

4. <span data-ttu-id="b7f12-137">[\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md)<`behavior`> öğesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b7f12-137">Add a [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) to the <`behavior`> element.</span></span>

5. <span data-ttu-id="b7f12-138">Öğesi öğesine ekleyin [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) `<serviceCredentials>` .</span><span class="sxs-lookup"><span data-stu-id="b7f12-138">Add a [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) to the `<serviceCredentials>` element.</span></span>

6. <span data-ttu-id="b7f12-139">`userNamePasswordValidationMode`Özniteliğini olarak ayarlayın `MembershipProvider` .</span><span class="sxs-lookup"><span data-stu-id="b7f12-139">Set the `userNamePasswordValidationMode` attribute to `MembershipProvider`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="b7f12-140">`userNamePasswordValidationMode`Değer ayarlanmamışsa, WCF ASP.NET üyelik sağlayıcısı yerine Windows kimlik doğrulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="b7f12-140">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the ASP.NET membership provider.</span></span>

7. <span data-ttu-id="b7f12-141">`membershipProviderName`Özniteliğini sağlayıcının adına ayarlayın (Bu konunun ilk yordamında sağlayıcı eklenirken belirtilir).</span><span class="sxs-lookup"><span data-stu-id="b7f12-141">Set the `membershipProviderName` attribute to the name of the provider (specified when adding the provider in the first procedure in this topic).</span></span> <span data-ttu-id="b7f12-142">Aşağıdaki örnek `<serviceCredentials>` Bu noktaya olan parçayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="b7f12-142">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>

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

## <a name="example"></a><span data-ttu-id="b7f12-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="b7f12-143">Example</span></span>

<span data-ttu-id="b7f12-144">Aşağıdaki kod, ASP üyeliği özelliğini kullanan bir hizmetin yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b7f12-144">The following code shows the configuration for a service that uses the ASP membership feature.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b7f12-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7f12-145">See also</span></span>

- [<span data-ttu-id="b7f12-146">Nasıl yapılır: ASP.NET Rol Sağlayıcısını Bir Hizmetle Kullanma</span><span class="sxs-lookup"><span data-stu-id="b7f12-146">How to: Use the ASP.NET Role Provider with a Service</span></span>](how-to-use-the-aspnet-role-provider-with-a-service.md)
- [<span data-ttu-id="b7f12-147">Üyelik ve Rol Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="b7f12-147">Membership and Role Provider</span></span>](../samples/membership-and-role-provider.md)
