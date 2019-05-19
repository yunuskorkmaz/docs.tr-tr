---
title: 'Nasıl yapılır: ASP.NET Üyelik Sağlayıcısını Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: 61324bbc5ea07dd19e23589bfc90f9ea44a6b331
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880179"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a><span data-ttu-id="8ee21-102">Nasıl yapılır: ASP.NET Üyelik Sağlayıcısını Kullanma</span><span class="sxs-lookup"><span data-stu-id="8ee21-102">How to: Use the ASP.NET Membership Provider</span></span>
<span data-ttu-id="8ee21-103">ASP.NET üyelik sağlayıcısı benzersiz kullanıcı adı ve parola birleşimlerini oluşturmak için kullanıcıların Web siteleri oluşturmak ASP.NET geliştiricilerinin sağlayan bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="8ee21-103">The ASP.NET membership provider is a feature that enables ASP.NET developers to create Web sites that allow users to create unique user name and password combinations.</span></span> <span data-ttu-id="8ee21-104">Bu özelliği sayesinde, herhangi bir kullanıcı sitesine sahip bir hesabı oluşturabilir ve site ve Hizmetleri özel erişim için oturum açın.</span><span class="sxs-lookup"><span data-stu-id="8ee21-104">With this facility, any user can establish an account with the site, and sign in for exclusive access to the site and its services.</span></span> <span data-ttu-id="8ee21-105">Kullanıcıların hesaplarını bir Windows etki alanına sahip olmasını gerektiren Windows Güvenlik aksine budur.</span><span class="sxs-lookup"><span data-stu-id="8ee21-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="8ee21-106">Bunun yerine, kendi kimlik bilgilerini (kullanıcı adı/parola birleşimini) karşılayan herhangi bir kullanıcı, site ve hizmetlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ee21-106">Instead, any user that supplies his or her credentials (the user name/password combination) can use the site and its services.</span></span>  
  
 <span data-ttu-id="8ee21-107">Örnek bir uygulama için bkz: [üyelik ve rol sağlayıcısı](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span><span class="sxs-lookup"><span data-stu-id="8ee21-107">For a sample application, see [Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="8ee21-108">ASP.NET rol sağlayıcısını özelliğini kullanma hakkında daha fazla bilgi için bkz: [nasıl yapılır: ASP.NET rol sağlayıcısını bir hizmetle kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="8ee21-108">For information about using the ASP.NET role provider feature, see [How to: Use the ASP.NET Role Provider with a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span>  
  
 <span data-ttu-id="8ee21-109">Üyelik özelliği, kullanıcı bilgilerini depolamak için SQL Server veritabanı kullanma gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8ee21-109">The membership feature requires using a SQL Server database to store the user information.</span></span> <span data-ttu-id="8ee21-110">Bu özellik ayrıca parolasını unutmuş kullanıcılar soru sormak için yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="8ee21-110">The feature also includes methods for prompting with a question any users who have forgotten their password.</span></span>  
  
 <span data-ttu-id="8ee21-111">Windows Communication Foundation (WCF) geliştiriciler güvenlik amacıyla bu özelliklerden yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ee21-111">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="8ee21-112">Bir WCF uygulamaya entegre edildiğinde, kullanıcılar WCF istemci uygulaması için bir kullanıcı adı/parola birleşimini sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ee21-112">When integrated into an WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="8ee21-113">WCF hizmetine veri aktarmak için kullanıcı adı/parola kimlik bilgileri gibi destekleyen bir bağlama kullanın <xref:System.ServiceModel.WSHttpBinding> (yapılandırmada [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) ve istemci kimlik bilgisi türü içinayarlayın`UserName`.</span><span class="sxs-lookup"><span data-stu-id="8ee21-113">To transfer the data to the WCF service, use a binding that supports user name/password credentials, such as the <xref:System.ServiceModel.WSHttpBinding> (in configuration, the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) and set the client credential type to `UserName`.</span></span> <span data-ttu-id="8ee21-114">Hizmet WCF güvenlik kullanıcı adı ve parolasına dayalı kullanıcının kimliğini doğrular ve ayrıca ASP.NET rol tarafından belirtilen rolü atar.</span><span class="sxs-lookup"><span data-stu-id="8ee21-114">On the service, WCF security authenticates the user based on the user name and password, and also assigns the role specified by the ASP.NET role.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ee21-115">WCF kullanıcı adı/parola birleşimleri veritabanıyla veya diğer kullanıcı bilgilerini doldurmak için bir yöntem sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="8ee21-115">WCF does not provide methods to populate the database with user name/password combinations or other user information.</span></span>  
  
### <a name="to-configure-the-membership-provider"></a><span data-ttu-id="8ee21-116">Üyelik sağlayıcısı yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="8ee21-116">To configure the membership provider</span></span>  
  
1. <span data-ttu-id="8ee21-117">Web.config dosyasında altında <`system.web`> öğesi oluşturmak bir <`membership`> öğesi.</span><span class="sxs-lookup"><span data-stu-id="8ee21-117">In the Web.config file, under the <`system.web`> element, create a <`membership`> element.</span></span>  
  
2. <span data-ttu-id="8ee21-118">Altında `<membership>` öğesi oluşturmak bir `<providers>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="8ee21-118">Under the `<membership>` element, create a `<providers>` element.</span></span>  
  
3. <span data-ttu-id="8ee21-119">Alt öğesi olarak <`providers`> öğesini ekleyin bir `<clear />` sağlayıcıları koleksiyonunu temizlemek için öğesi.</span><span class="sxs-lookup"><span data-stu-id="8ee21-119">As a child to the <`providers`> element, add a `<clear />` element to flush the collection of providers.</span></span>  
  
4. <span data-ttu-id="8ee21-120">Altında `<clear />` öğesi oluşturmak bir <`add`> öğesi aşağıdaki özniteliklerle uygun değerlere ayarlayın: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer` , `requiresUniqueEmail`, ve `passwordFormat`.</span><span class="sxs-lookup"><span data-stu-id="8ee21-120">Under the `<clear />` element, create an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer`, `requiresUniqueEmail`, and `passwordFormat`.</span></span> <span data-ttu-id="8ee21-121">`name` Özniteliği kullanılır daha sonra yapılandırma dosyasındaki bir değer olarak.</span><span class="sxs-lookup"><span data-stu-id="8ee21-121">The `name` attribute is used later as a value in the configuration file.</span></span> <span data-ttu-id="8ee21-122">Aşağıdaki örnek ayarlar `SqlMembershipProvider`.</span><span class="sxs-lookup"><span data-stu-id="8ee21-122">The following example sets it to `SqlMembershipProvider`.</span></span>  
  
     <span data-ttu-id="8ee21-123">Aşağıdaki örnekte, yapılandırma bölümü gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8ee21-123">The following example shows the configuration section.</span></span>  
  
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
  
### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a><span data-ttu-id="8ee21-124">Hizmet güvenliği kullanıcı adı/parola birleşimini kabul edecek şekilde yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="8ee21-124">To configure service security to accept the user name/password combination</span></span>  
  
1. <span data-ttu-id="8ee21-125">Yapılandırma dosyasında altında [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) öğe, Ekle bir [ \<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="8ee21-125">In the configuration file, under the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
2. <span data-ttu-id="8ee21-126">Ekleme bir [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) bağlamalar bölümü için.</span><span class="sxs-lookup"><span data-stu-id="8ee21-126">Add a [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) to the bindings section.</span></span> <span data-ttu-id="8ee21-127">Bir WCF bağlama öğesi oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Yapılandırmada hizmet bağlaması belirtme](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="8ee21-127">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
3. <span data-ttu-id="8ee21-128">Ayarlama `mode` özniteliği `<security>` öğesine `Message`.</span><span class="sxs-lookup"><span data-stu-id="8ee21-128">Set the `mode` attribute of the `<security>` element to `Message`.</span></span>  
  
4. <span data-ttu-id="8ee21-129">Ayarlama `clientCredentialType` özniteliği <`message`> öğesine `UserName`.</span><span class="sxs-lookup"><span data-stu-id="8ee21-129">Set the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span> <span data-ttu-id="8ee21-130">Bu, istemcinin kimlik bilgisi olarak bir kullanıcı adı/parola çift kullanılacak belirtir.</span><span class="sxs-lookup"><span data-stu-id="8ee21-130">This specifies that a user name/password pair will be used as the client's credential.</span></span>  
  
     <span data-ttu-id="8ee21-131">Aşağıdaki örnek, bağlama için yapılandırma kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8ee21-131">The following example shows the configuration code for the binding.</span></span>  
  
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
  
### <a name="to-configure-a-service-to-use-the-membership-provider"></a><span data-ttu-id="8ee21-132">Bir hizmeti üyelik sağlayıcıyı kullanacak şekilde yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="8ee21-132">To configure a service to use the membership provider</span></span>  
  
1. <span data-ttu-id="8ee21-133">Alt öğesi olarak `<system.serviceModel>` öğe, Ekle bir [ \<davranışları >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) öğesi</span><span class="sxs-lookup"><span data-stu-id="8ee21-133">As a child to the `<system.serviceModel>` element, add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element</span></span>  
  
2. <span data-ttu-id="8ee21-134">Ekleme bir [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) için <`behaviors`> öğesi.</span><span class="sxs-lookup"><span data-stu-id="8ee21-134">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>  
  
3. <span data-ttu-id="8ee21-135">Ekleme bir [ \<davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) ayarlayıp `name` özniteliği için uygun bir değer.</span><span class="sxs-lookup"><span data-stu-id="8ee21-135">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>  
  
4. <span data-ttu-id="8ee21-136">Ekleme bir [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) için <`behavior`> öğesi.</span><span class="sxs-lookup"><span data-stu-id="8ee21-136">Add a [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) to the <`behavior`> element.</span></span>  
  
5. <span data-ttu-id="8ee21-137">Ekleme bir [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) için `<serviceCredentials>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="8ee21-137">Add a [\<userNameAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) to the `<serviceCredentials>` element.</span></span>  
  
6. <span data-ttu-id="8ee21-138">Ayarlama `userNamePasswordValidationMode` özniteliğini `MembershipProvider`.</span><span class="sxs-lookup"><span data-stu-id="8ee21-138">Set the `userNamePasswordValidationMode` attribute to `MembershipProvider`.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="8ee21-139">Varsa `userNamePasswordValidationMode` değeri ayarlanmazsa, WCF, Windows kimlik doğrulaması yerine ASP.NET üyelik sağlayıcısını kullanır.</span><span class="sxs-lookup"><span data-stu-id="8ee21-139">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the ASP.NET membership provider.</span></span>  
  
7. <span data-ttu-id="8ee21-140">Ayarlama `membershipProviderName` özniteliği için (Bu konunun ilk yordamındaki sağlayıcı eklerken belirtilir) sağlayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="8ee21-140">Set the `membershipProviderName` attribute to the name of the provider (specified when adding the provider in the first procedure in this topic).</span></span> <span data-ttu-id="8ee21-141">Aşağıdaki örnekte gösterildiği `<serviceCredentials>` bu noktaya parça.</span><span class="sxs-lookup"><span data-stu-id="8ee21-141">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="8ee21-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="8ee21-142">Example</span></span>  
 <span data-ttu-id="8ee21-143">Aşağıdaki kod, ASP üyelik özelliğini kullanan bir hizmet yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8ee21-143">The following code shows the configuration for a service that uses the ASP membership feature.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8ee21-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ee21-144">See also</span></span>

- [<span data-ttu-id="8ee21-145">Nasıl yapılır: ASP.NET rol sağlayıcısını bir hizmetle kullanma</span><span class="sxs-lookup"><span data-stu-id="8ee21-145">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [<span data-ttu-id="8ee21-146">Üyelik ve Rol Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="8ee21-146">Membership and Role Provider</span></span>](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
