---
title: "Nasıl yapılır: Bir Hizmet için Özel Yetkilendirme Yöneticisi Oluşturma"
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
helpviewer_keywords:
- Windows Communication Foundation, extending
- OperationRequirement class
ms.assetid: 6214afde-44c1-4bf5-ba07-5ad6493620ea
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7b8d934509940bf712ccb7463156c88540027407
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-custom-authorization-manager-for-a-service"></a><span data-ttu-id="4eb9b-102">Nasıl yapılır: Bir Hizmet için Özel Yetkilendirme Yöneticisi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4eb9b-102">How to: Create a Custom Authorization Manager for a Service</span></span>
<span data-ttu-id="4eb9b-103">Kimlik modeli altyapısında [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Genişletilebilir talep tabanlı yetkilendirme modelini destekler.</span><span class="sxs-lookup"><span data-stu-id="4eb9b-103">The Identity Model infrastructure in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] supports an extensible claims-based authorization model.</span></span> <span data-ttu-id="4eb9b-104">Talep belirteçlerinden ayıklanan ve isteğe bağlı olarak özel yetkilendirme ilkeleri tarafından işlenir ve içine yerleştirilen bir <xref:System.IdentityModel.Policy.AuthorizationContext>.</span><span class="sxs-lookup"><span data-stu-id="4eb9b-104">Claims are extracted from tokens and optionally processed by custom authorization policies and then placed into an <xref:System.IdentityModel.Policy.AuthorizationContext>.</span></span> <span data-ttu-id="4eb9b-105">Bir Yetkilendirme Yöneticisi'ni Taleplerde inceler <xref:System.IdentityModel.Policy.AuthorizationContext> yetkilendirme kararları vermek için.</span><span class="sxs-lookup"><span data-stu-id="4eb9b-105">An authorization manager examines the claims in the <xref:System.IdentityModel.Policy.AuthorizationContext> to make authorization decisions.</span></span>  
  
 <span data-ttu-id="4eb9b-106">Varsayılan olarak, yetkilendirme kararları yapılan <xref:System.ServiceModel.ServiceAuthorizationManager> sınıfı; ancak bu kararlar özel Yetkilendirme Yöneticisi oluşturma tarafından geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="4eb9b-106">By default, authorization decisions are made by the <xref:System.ServiceModel.ServiceAuthorizationManager> class; however these decisions can be overridden by creating a custom authorization manager.</span></span> <span data-ttu-id="4eb9b-107">Özel Yetkilendirme Yöneticisi oluşturma için türeyen bir sınıf oluşturun <xref:System.ServiceModel.ServiceAuthorizationManager> ve uygulamanıza <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4eb9b-107">To create a custom authorization manager, create a class that derives from <xref:System.ServiceModel.ServiceAuthorizationManager> and implement <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="4eb9b-108">Yetkilendirme kararları yapılma <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> döndürür yöntemi `true` zaman erişimi verilir ve `false` zaman erişim reddedildi.</span><span class="sxs-lookup"><span data-stu-id="4eb9b-108">Authorization decisions are made in the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method, which returns `true` when access is granted and `false` when access is denied.</span></span>  
  
 <span data-ttu-id="4eb9b-109">İleti gövdesinin içeriğine yetkilendirme kararı bağlıdır kullanırsanız <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4eb9b-109">If the authorization decision depends on the contents of the message body, use the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method.</span></span>  
  
 <span data-ttu-id="4eb9b-110">Böylece yetkilendirme kararı ileti gövdesi erişimi gerektirmez performans sorunları nedeniyle Mümkünse, uygulamanızın yeniden tasarlamanız.</span><span class="sxs-lookup"><span data-stu-id="4eb9b-110">Because of performance issues, if possible you should redesign your application so that the authorization decision does not require access to the message body.</span></span>  
  
 <span data-ttu-id="4eb9b-111">Bir hizmet için özel Yetkilendirme Yöneticisi'ni kaydı, kod veya yapılandırma yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="4eb9b-111">Registration of the custom authorization manager for a service can be done in code or configuration.</span></span>  
  
### <a name="to-create-a-custom-authorization-manager"></a><span data-ttu-id="4eb9b-112">Özel Yetkilendirme Yöneticisi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="4eb9b-112">To create a custom authorization manager</span></span>  
  
1.  <span data-ttu-id="4eb9b-113">Öğesinden bir sınıf türetin <xref:System.ServiceModel.ServiceAuthorizationManager> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4eb9b-113">Derive a class from the <xref:System.ServiceModel.ServiceAuthorizationManager> class.</span></span>  
  
     [!code-csharp[c_CustomAuthMgr#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#5)]
     [!code-vb[c_CustomAuthMgr#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#5)]  
  
2.  <span data-ttu-id="4eb9b-114">Geçersiz kılma <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4eb9b-114">Override the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> method.</span></span>  
  
     <span data-ttu-id="4eb9b-115">Kullanım <xref:System.ServiceModel.OperationContext> için geçirilen <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> yetkilendirme kararları için yöntem.</span><span class="sxs-lookup"><span data-stu-id="4eb9b-115">Use the <xref:System.ServiceModel.OperationContext> that is passed to the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> method to make authorization decisions.</span></span>  
  
     <span data-ttu-id="4eb9b-116">Aşağıdaki kod örneğinde <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> özel talep bulmak için yöntem `http://www.contoso.com/claims/allowedoperation` bir yetkilendirme kararı almak için.</span><span class="sxs-lookup"><span data-stu-id="4eb9b-116">The following code example uses the <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> method to find the custom claim `http://www.contoso.com/claims/allowedoperation` to make an authorization decision.</span></span>  
  
     [!code-csharp[c_CustomAuthMgr#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#6)]
     [!code-vb[c_CustomAuthMgr#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#6)]  
  
### <a name="to-register-a-custom-authorization-manager-using-code"></a><span data-ttu-id="4eb9b-117">Kod kullanarak bir özel Yetkilendirme Yöneticisi'ni kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="4eb9b-117">To register a custom authorization manager using code</span></span>  
  
1.  <span data-ttu-id="4eb9b-118">Özel yetkilendirme örneği Yöneticisi oluşturabilir ve atayabilirsiniz <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="4eb9b-118">Create an instance of the custom authorization manager and assign it to the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> property.</span></span>  
  
     <span data-ttu-id="4eb9b-119"><xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> Kullanılarak erişilebilir <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="4eb9b-119">The <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> can be accessed using <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> property.</span></span>  
  
     <span data-ttu-id="4eb9b-120">Aşağıdaki kod örneği yazmaçlar `MyServiceAuthorizationManager` özel Yetkilendirme Yöneticisi.</span><span class="sxs-lookup"><span data-stu-id="4eb9b-120">The following code example registers the `MyServiceAuthorizationManager` custom authorization manager.</span></span>  
  
     [!code-csharp[c_CustomAuthMgr#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#4)]
     [!code-vb[c_CustomAuthMgr#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#4)]  
  
### <a name="to-register-a-custom-authorization-manager-using-configuration"></a><span data-ttu-id="4eb9b-121">Yapılandırması'nı kullanarak bir özel Yetkilendirme Yöneticisi'ni kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="4eb9b-121">To register a custom authorization manager using configuration</span></span>  
  
1.  <span data-ttu-id="4eb9b-122">Hizmeti için yapılandırma dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="4eb9b-122">Open the configuration file for the service.</span></span>  
  
2.  <span data-ttu-id="4eb9b-123">Ekleme bir [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) için [ \<davranışları >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="4eb9b-123">Add a [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md).</span></span>  
  
     <span data-ttu-id="4eb9b-124">İçin [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md), ekleme bir `serviceAuthorizationManagerType` özniteliği ve özel Yetkilendirme Yöneticisi'ni temsil eden tür için değerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4eb9b-124">To the [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md), add a `serviceAuthorizationManagerType` attribute and set its value to the type that represents the custom authorization manager.</span></span>  
  
3.  <span data-ttu-id="4eb9b-125">Hizmet ve istemci arasındaki iletişimin güvenliğini sağlar bir bağlaması ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4eb9b-125">Add a binding that secures the communication between the client and service.</span></span>  
  
     <span data-ttu-id="4eb9b-126">Bu iletişim için eklenen talepleri belirler, seçilen bağlama <xref:System.IdentityModel.Policy.AuthorizationContext>, yetkilendirme kararları vermek için özel Yetkilendirme Yöneticisi'ni kullanır.</span><span class="sxs-lookup"><span data-stu-id="4eb9b-126">The binding that is chosen for this communication determines the claims that are added to the <xref:System.IdentityModel.Policy.AuthorizationContext>, which the custom authorization manager uses to make authorization decisions.</span></span> <span data-ttu-id="4eb9b-127">Sistem tarafından sağlanan bağlamalar hakkında daha fazla ayrıntı için bkz: [System-Provided bağlamaları](../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="4eb9b-127">For more details about the system-provided bindings, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
4.  <span data-ttu-id="4eb9b-128">Bir hizmet uç noktası için davranış ekleyerek ilişkilendirmek bir [ \<hizmet >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) öğesi ve değeri ayarlayın `behaviorConfiguration` özniteliği için name özniteliği değerini [ \<davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="4eb9b-128">Associate the behavior to a service endpoint, by adding a [\<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) element and set the value of the `behaviorConfiguration` attribute to the value of the name attribute for the [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span></span>  
  
     <span data-ttu-id="4eb9b-129">Hizmet uç noktası yapılandırma hakkında daha fazla bilgi için bkz: [nasıl yapılır: yapılandırmada hizmet uç noktası oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="4eb9b-129">For more information about configuring a service endpoint, see [How to: Create a Service Endpoint in Configuration](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md).</span></span>  
  
     <span data-ttu-id="4eb9b-130">Aşağıdaki kod örneğinde özel Yetkilendirme Yöneticisi'ni kaydeder `Samples.MyServiceAuthorizationManager`.</span><span class="sxs-lookup"><span data-stu-id="4eb9b-130">The following code example registers the custom authorization manager `Samples.MyServiceAuthorizationManager`.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service   
              name="Microsoft.ServiceModel.Samples.CalculatorService"  
              behaviorConfiguration="CalculatorServiceBehavior">  
            <host>  
              <baseAddresses>  
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
              </baseAddresses>  
            </host>  
            <endpoint address=""  
                      binding="wsHttpBinding_Calculator"  
                      contract="Microsoft.ServiceModel.Samples.ICalculator" />  
          </service>  
        </services>  
        <bindings>  
          <WSHttpBinding>  
           <binding name = "wsHttpBinding_Calculator">  
             <security mode="Message">  
               <message clientCredentialType="Windows"/>  
             </security>  
            </binding>  
          </WSHttpBinding>  
    </bindings>  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="CalculatorServiceBehavior">  
              <serviceAuthorization serviceAuthorizationManagerType="Samples.MyServiceAuthorizationManager,MyAssembly" />  
             </behavior>  
         </serviceBehaviors>  
       </behaviors>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
    > [!WARNING]
    >  <span data-ttu-id="4eb9b-131">ServiceAuthorizationManagerType belirttiğinizde, tam olarak nitelenmiş tür adını dize içermesi gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4eb9b-131">Note that when you specify the serviceAuthorizationManagerType, the string must contain the fully qualified type name.</span></span> <span data-ttu-id="4eb9b-132">virgül ve türünün tanımlandığı derleme adını.</span><span class="sxs-lookup"><span data-stu-id="4eb9b-132">a comma, and the name of the assembly in which the type is defined.</span></span> <span data-ttu-id="4eb9b-133">Derleme adı değiştirmeden bırakırsanız, WCF System.ServiceModel.dll yük türü dener.</span><span class="sxs-lookup"><span data-stu-id="4eb9b-133">If you leave out the assembly name, WCF will attempt to load the type from System.ServiceModel.dll.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4eb9b-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="4eb9b-134">Example</span></span>  
 <span data-ttu-id="4eb9b-135">Aşağıdaki kod örneğinde temel bir uygulama ortaya koyar bir <xref:System.ServiceModel.ServiceAuthorizationManager> geçersiz kılma içeren sınıf <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4eb9b-135">The following code example demonstrates a basic implementation of a <xref:System.ServiceModel.ServiceAuthorizationManager> class that includes overriding the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="4eb9b-136">Örnek kod inceler <xref:System.IdentityModel.Policy.AuthorizationContext> için özel bir talep ve döndürür `true` zaman kaynağı bu özel talep için eşleşen eylem değerinden <xref:System.ServiceModel.OperationContext>.</span><span class="sxs-lookup"><span data-stu-id="4eb9b-136">The example code examines the <xref:System.IdentityModel.Policy.AuthorizationContext> for a custom claim and returns `true` when the resource for that custom claim matches the action value from the <xref:System.ServiceModel.OperationContext>.</span></span> <span data-ttu-id="4eb9b-137">Daha eksiksiz bir uygulama için bir <xref:System.ServiceModel.ServiceAuthorizationManager> sınıfı için bkz: [yetkilendirme ilkesi](../../../../docs/framework/wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="4eb9b-137">For a more complete implementation of a <xref:System.ServiceModel.ServiceAuthorizationManager> class, see [Authorization Policy](../../../../docs/framework/wcf/samples/authorization-policy.md).</span></span>  
  
 [!code-csharp[c_CustomAuthMgr#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#2)]
 [!code-vb[c_CustomAuthMgr#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="4eb9b-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4eb9b-138">See Also</span></span>  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
 [<span data-ttu-id="4eb9b-139">Yetkilendirme İlkesi</span><span class="sxs-lookup"><span data-stu-id="4eb9b-139">Authorization Policy</span></span>](../../../../docs/framework/wcf/samples/authorization-policy.md)  
 [<span data-ttu-id="4eb9b-140">Yetkilendirme İlkesi</span><span class="sxs-lookup"><span data-stu-id="4eb9b-140">Authorization Policy</span></span>](../../../../docs/framework/wcf/samples/authorization-policy.md)
