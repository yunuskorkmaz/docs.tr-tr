---
title: "Nasıl yapılır: ASP.NET Üyelik Sağlayıcısını Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6c5042e73945c54da2b1ee71fc5ea61727dc73c8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-aspnet-membership-provider"></a><span data-ttu-id="d85d7-102">Nasıl yapılır: ASP.NET Üyelik Sağlayıcısını Kullanma</span><span class="sxs-lookup"><span data-stu-id="d85d7-102">How to: Use the ASP.NET Membership Provider</span></span>
<span data-ttu-id="d85d7-103">[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Üyelik sağlayıcısı sağlayan bir özelliktir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] kullanıcıların benzersiz bir kullanıcı adı ve parola birleşimlerini oluşturmasına izin Web siteleri oluşturmak için geliştiriciler.</span><span class="sxs-lookup"><span data-stu-id="d85d7-103">The [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider is a feature that enables [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] developers to create Web sites that allow users to create unique user name and password combinations.</span></span> <span data-ttu-id="d85d7-104">Bu özelliği sayesinde, herhangi bir kullanıcı sitesi olan bir hesap oluşturun ve site ve hizmetlerini özel erişim için oturum açın.</span><span class="sxs-lookup"><span data-stu-id="d85d7-104">With this facility, any user can establish an account with the site, and sign in for exclusive access to the site and its services.</span></span> <span data-ttu-id="d85d7-105">Kullanıcıların bir Windows etki alanında hesaplarına sahip olmasını gerektiren Windows güvenliği aksine budur.</span><span class="sxs-lookup"><span data-stu-id="d85d7-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="d85d7-106">Bunun yerine, kendi kimlik bilgilerini (kullanıcı adı/parola birleşimini) sağlayan herhangi bir kullanıcı site ve hizmetlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d85d7-106">Instead, any user that supplies his or her credentials (the user name/password combination) can use the site and its services.</span></span>  
  
 <span data-ttu-id="d85d7-107">Örnek bir uygulama için bkz: [üyelik ve rol sağlayıcısı](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span><span class="sxs-lookup"><span data-stu-id="d85d7-107">For a sample application, see [Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="d85d7-108">Kullanma hakkında bilgi için [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] rol sağlayıcı özelliği, bkz: [nasıl yapılır: ASP.NET rol sağlayıcısını bir hizmetle kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="d85d7-108">For information about using the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider feature, see [How to: Use the ASP.NET Role Provider with a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span>  
  
 <span data-ttu-id="d85d7-109">Kullanıcı bilgilerini depolamak için bir SQL Server veritabanı kullanma üyelik özellik gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d85d7-109">The membership feature requires using a SQL Server database to store the user information.</span></span> <span data-ttu-id="d85d7-110">Özelliği de parolalarını unutmuş olan tüm kullanıcılar ile bir soru sormak için yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="d85d7-110">The feature also includes methods for prompting with a question any users who have forgotten their password.</span></span>  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="d85d7-111">Geliştiriciler güvenlik amacıyla bu özelliklerden yararlanabilir.</span><span class="sxs-lookup"><span data-stu-id="d85d7-111"> developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="d85d7-112">Tümleşik olduğunda bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulama, kullanıcıların gerekir sağlamak için bir kullanıcı adı/parola birleşimini [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci uygulaması.</span><span class="sxs-lookup"><span data-stu-id="d85d7-112">When integrated into an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application, users must supply a user name/password combination to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application.</span></span> <span data-ttu-id="d85d7-113">Veri aktarmasına izin [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet, kullanıcı adı/parola kimlik bilgileri gibi destekleyen bir bağlama kullanmak <xref:System.ServiceModel.WSHttpBinding> (yapılandırmada, [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) ve istemci kimlik bilgileri Ayarla için yazın `UserName`.</span><span class="sxs-lookup"><span data-stu-id="d85d7-113">To transfer the data to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service, use a binding that supports user name/password credentials, such as the <xref:System.ServiceModel.WSHttpBinding> (in configuration, the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) and set the client credential type to `UserName`.</span></span> <span data-ttu-id="d85d7-114">Hizmetinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenlik kullanıcı adı ve parolaya göre kullanıcının kimliğini doğrular ve ayrıca tarafından belirtilen rol atar [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] rol.</span><span class="sxs-lookup"><span data-stu-id="d85d7-114">On the service, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security authenticates the user based on the user name and password, and also assigns the role specified by the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d85d7-115">Kullanıcı adı/parola birleşimleri veritabanıyla veya diğer kullanıcı bilgilerini doldurmak için yöntem sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="d85d7-115"> does not provide methods to populate the database with user name/password combinations or other user information.</span></span>  
  
### <a name="to-configure-the-membership-provider"></a><span data-ttu-id="d85d7-116">Üyelik sağlayıcısı yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="d85d7-116">To configure the membership provider</span></span>  
  
1.  <span data-ttu-id="d85d7-117">Web.config dosyasındaki altında <`system.web`> öğesini oluşturmak bir <`membership`> öğesi.</span><span class="sxs-lookup"><span data-stu-id="d85d7-117">In the Web.config file, under the <`system.web`> element, create a <`membership`> element.</span></span>  
  
2.  <span data-ttu-id="d85d7-118">Altında `<membership>` öğesini oluşturmak bir `<providers>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="d85d7-118">Under the `<membership>` element, create a `<providers>` element.</span></span>  
  
3.  <span data-ttu-id="d85d7-119">Alt öğesi olarak <`providers`> öğesi ekleme bir `<clear />` sağlayıcıları koleksiyonu temizlemek için öğesi.</span><span class="sxs-lookup"><span data-stu-id="d85d7-119">As a child to the <`providers`> element, add a `<clear />` element to flush the collection of providers.</span></span>  
  
4.  <span data-ttu-id="d85d7-120">Altında `<clear />` öğesini oluşturmak bir <`add`> öğesi aşağıdaki özniteliklerle uygun değerlere ayarlayın: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer` , `requiresUniqueEmail`, ve `passwordFormat`.</span><span class="sxs-lookup"><span data-stu-id="d85d7-120">Under the `<clear />` element, create an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer`, `requiresUniqueEmail`, and `passwordFormat`.</span></span> <span data-ttu-id="d85d7-121">`name` Özniteliği kullanılır daha sonra yapılandırma dosyasındaki bir değer olarak.</span><span class="sxs-lookup"><span data-stu-id="d85d7-121">The `name` attribute is used later as a value in the configuration file.</span></span> <span data-ttu-id="d85d7-122">Aşağıdaki örnek, ayarlar `SqlMembershipProvider`.</span><span class="sxs-lookup"><span data-stu-id="d85d7-122">The following example sets it to `SqlMembershipProvider`.</span></span>  
  
     <span data-ttu-id="d85d7-123">Aşağıdaki örnek yapılandırma bölümü gösterir.</span><span class="sxs-lookup"><span data-stu-id="d85d7-123">The following example shows the configuration section.</span></span>  
  
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
  
### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a><span data-ttu-id="d85d7-124">Kullanıcı adı/parola birleşimini kabul etmek için hizmet güvenliği yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="d85d7-124">To configure service security to accept the user name/password combination</span></span>  
  
1.  <span data-ttu-id="d85d7-125">Yapılandırma dosyasında altında [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) öğesi ekleme bir [ \<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="d85d7-125">In the configuration file, under the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
2.  <span data-ttu-id="d85d7-126">Ekleme bir [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) bağlamaları bölümüne.</span><span class="sxs-lookup"><span data-stu-id="d85d7-126">Add a [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) to the bindings section.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="d85d7-127">oluşturma bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bağlama öğesi, bkz: [nasıl yapılır: yapılandırmada hizmet bağlama belirtme](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="d85d7-127"> creating an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
3.  <span data-ttu-id="d85d7-128">Ayarlama `mode` özniteliği `<security>` öğesine `Message`.</span><span class="sxs-lookup"><span data-stu-id="d85d7-128">Set the `mode` attribute of the `<security>` element to `Message`.</span></span>  
  
4.  <span data-ttu-id="d85d7-129">Ayarlama `clientCredentialType` özniteliği <`message`> öğesine `UserName`.</span><span class="sxs-lookup"><span data-stu-id="d85d7-129">Set the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span> <span data-ttu-id="d85d7-130">Bu, bir kullanıcı adı/parola çifti istemcinin kimlik bilgisi olarak kullanılacak belirtir.</span><span class="sxs-lookup"><span data-stu-id="d85d7-130">This specifies that a user name/password pair will be used as the client's credential.</span></span>  
  
     <span data-ttu-id="d85d7-131">Aşağıdaki örnek, bağlama için yapılandırma kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d85d7-131">The following example shows the configuration code for the binding.</span></span>  
  
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
  
### <a name="to-configure-a-service-to-use-the-membership-provider"></a><span data-ttu-id="d85d7-132">Bir hizmeti üyelik sağlayıcıyı kullanacak şekilde yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="d85d7-132">To configure a service to use the membership provider</span></span>  
  
1.  <span data-ttu-id="d85d7-133">Alt öğesi olarak `<system.serviceModel>` öğesi ekleme bir [ \<davranışları >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) öğesi</span><span class="sxs-lookup"><span data-stu-id="d85d7-133">As a child to the `<system.serviceModel>` element, add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element</span></span>  
  
2.  <span data-ttu-id="d85d7-134">Ekleme bir [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) için <`behaviors`> öğesi.</span><span class="sxs-lookup"><span data-stu-id="d85d7-134">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>  
  
3.  <span data-ttu-id="d85d7-135">Ekleme bir [ \<davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) ve `name` öznitelik için uygun bir değer.</span><span class="sxs-lookup"><span data-stu-id="d85d7-135">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>  
  
4.  <span data-ttu-id="d85d7-136">Ekleme bir [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) için <`behavior`> öğesi.</span><span class="sxs-lookup"><span data-stu-id="d85d7-136">Add a [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) to the <`behavior`> element.</span></span>  
  
5.  <span data-ttu-id="d85d7-137">Ekleme bir [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) için `<serviceCredentials>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="d85d7-137">Add a [\<userNameAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) to the `<serviceCredentials>` element.</span></span>  
  
6.  <span data-ttu-id="d85d7-138">Ayarlama `userNamePasswordValidationMode` özniteliğini `MembershipProvider`.</span><span class="sxs-lookup"><span data-stu-id="d85d7-138">Set the `userNamePasswordValidationMode` attribute to `MembershipProvider`.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="d85d7-139">Varsa `userNamePasswordValidationMode` değeri ayarlanmazsa, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yerine Windows kimlik doğrulamasını kullanan [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] üyelik sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="d85d7-139">If the `userNamePasswordValidationMode` value is not set, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses Windows authentication instead of the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider.</span></span>  
  
7.  <span data-ttu-id="d85d7-140">Ayarlama `membershipProviderName` (sağlayıcıyı bu konunun ilk yordamda eklerken belirtilir) sağlayıcısının adı özniteliği.</span><span class="sxs-lookup"><span data-stu-id="d85d7-140">Set the `membershipProviderName` attribute to the name of the provider (specified when adding the provider in the first procedure in this topic).</span></span> <span data-ttu-id="d85d7-141">Aşağıdaki örnekte gösterildiği `<serviceCredentials>` bu noktaya parça.</span><span class="sxs-lookup"><span data-stu-id="d85d7-141">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="d85d7-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="d85d7-142">Example</span></span>  
 <span data-ttu-id="d85d7-143">Aşağıdaki kod ASP üyelik özelliğini kullanan bir hizmet yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d85d7-143">The following code shows the configuration for a service that uses the ASP membership feature.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d85d7-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d85d7-144">See Also</span></span>  
 [<span data-ttu-id="d85d7-145">Nasıl yapılır: ASP.NET Rol Sağlayıcısını Bir Hizmetle Kullanma</span><span class="sxs-lookup"><span data-stu-id="d85d7-145">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 [<span data-ttu-id="d85d7-146">Üyelik ve Rol Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="d85d7-146">Membership and Role Provider</span></span>](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
