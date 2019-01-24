---
title: 'Nasıl yapılır: Bir hizmet için özel Yetkilendirme Yöneticisi oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Communication Foundation, extending
- OperationRequirement class
ms.assetid: 6214afde-44c1-4bf5-ba07-5ad6493620ea
ms.openlocfilehash: 64eb44c948f669ea5364cc38c7416fdd12cdabd6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573955"
---
# <a name="how-to-create-a-custom-authorization-manager-for-a-service"></a><span data-ttu-id="35bd3-102">Nasıl yapılır: Bir hizmet için özel Yetkilendirme Yöneticisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="35bd3-102">How to: Create a Custom Authorization Manager for a Service</span></span>
<span data-ttu-id="35bd3-103">Windows Communication Foundation (WCF) kimlik modeli altyapısı, bir Genişletilebilir beyana dayalı yetkilendirme modelini destekler.</span><span class="sxs-lookup"><span data-stu-id="35bd3-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) supports an extensible claims-based authorization model.</span></span> <span data-ttu-id="35bd3-104">Talep belirteçleri ayıklanır ve isteğe bağlı olarak özel yetkilendirme ilkeleri tarafından işlenir ve ardından yerleştirilip bir <xref:System.IdentityModel.Policy.AuthorizationContext>.</span><span class="sxs-lookup"><span data-stu-id="35bd3-104">Claims are extracted from tokens and optionally processed by custom authorization policies and then placed into an <xref:System.IdentityModel.Policy.AuthorizationContext>.</span></span> <span data-ttu-id="35bd3-105">Yetkilendirme Yöneticisi Taleplerde inceler <xref:System.IdentityModel.Policy.AuthorizationContext> yetkilendirme kararları vermek için.</span><span class="sxs-lookup"><span data-stu-id="35bd3-105">An authorization manager examines the claims in the <xref:System.IdentityModel.Policy.AuthorizationContext> to make authorization decisions.</span></span>  
  
 <span data-ttu-id="35bd3-106">Varsayılan olarak, yetkilendirme kararları tarafından yapılan <xref:System.ServiceModel.ServiceAuthorizationManager> sınıfı; ancak bu kararların bir özel Yetkilendirme Yöneticisi oluşturma tarafından geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="35bd3-106">By default, authorization decisions are made by the <xref:System.ServiceModel.ServiceAuthorizationManager> class; however these decisions can be overridden by creating a custom authorization manager.</span></span> <span data-ttu-id="35bd3-107">Özel Yetkilendirme Yöneticisi oluşturma için türetilen bir sınıf oluşturmanız <xref:System.ServiceModel.ServiceAuthorizationManager> ve uygulama <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="35bd3-107">To create a custom authorization manager, create a class that derives from <xref:System.ServiceModel.ServiceAuthorizationManager> and implement <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="35bd3-108">Yetkilendirme kararları içinde yapılan <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> döndüren yöntemi `true` erişim izni ne zaman ve `false` zaman erişim engellendi.</span><span class="sxs-lookup"><span data-stu-id="35bd3-108">Authorization decisions are made in the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method, which returns `true` when access is granted and `false` when access is denied.</span></span>  
  
 <span data-ttu-id="35bd3-109">İleti gövdesi içeriğini temel yetkilendirme kararı bağlıdır kullanırsanız <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="35bd3-109">If the authorization decision depends on the contents of the message body, use the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method.</span></span>  
  
 <span data-ttu-id="35bd3-110">Yetkilendirme kararı, ileti gövdesi erişimi gerektirmez, böylece performans sorunları nedeniyle Mümkünse, uygulamanızı yeniden tasarlamanız.</span><span class="sxs-lookup"><span data-stu-id="35bd3-110">Because of performance issues, if possible you should redesign your application so that the authorization decision does not require access to the message body.</span></span>  
  
 <span data-ttu-id="35bd3-111">Bir hizmet için özel Yetkilendirme Yöneticisi kaydı, kod veya yapılandırma yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="35bd3-111">Registration of the custom authorization manager for a service can be done in code or configuration.</span></span>  
  
### <a name="to-create-a-custom-authorization-manager"></a><span data-ttu-id="35bd3-112">Özel Yetkilendirme Yöneticisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="35bd3-112">To create a custom authorization manager</span></span>  
  
1.  <span data-ttu-id="35bd3-113">Öğesinden bir sınıf türetin <xref:System.ServiceModel.ServiceAuthorizationManager> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="35bd3-113">Derive a class from the <xref:System.ServiceModel.ServiceAuthorizationManager> class.</span></span>  
  
     [!code-csharp[c_CustomAuthMgr#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#5)]
     [!code-vb[c_CustomAuthMgr#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#5)]  
  
2.  <span data-ttu-id="35bd3-114">Geçersiz kılma <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="35bd3-114">Override the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> method.</span></span>  
  
     <span data-ttu-id="35bd3-115">Kullanım <xref:System.ServiceModel.OperationContext> yapan <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> yetkilendirme kararları vermek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="35bd3-115">Use the <xref:System.ServiceModel.OperationContext> that is passed to the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> method to make authorization decisions.</span></span>  
  
     <span data-ttu-id="35bd3-116">Aşağıdaki kod örneğinde <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> özel talep bulmak için yöntem `http://www.contoso.com/claims/allowedoperation` bir yetkilendirme kararı almak için.</span><span class="sxs-lookup"><span data-stu-id="35bd3-116">The following code example uses the <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> method to find the custom claim `http://www.contoso.com/claims/allowedoperation` to make an authorization decision.</span></span>  
  
     [!code-csharp[c_CustomAuthMgr#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#6)]
     [!code-vb[c_CustomAuthMgr#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#6)]  
  
### <a name="to-register-a-custom-authorization-manager-using-code"></a><span data-ttu-id="35bd3-117">Kod kullanarak bir özel Yetkilendirme Yöneticisi kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="35bd3-117">To register a custom authorization manager using code</span></span>  
  
1.  <span data-ttu-id="35bd3-118">Özel yetkilendirme örneği Yöneticisi oluşturun ve atayın <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="35bd3-118">Create an instance of the custom authorization manager and assign it to the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> property.</span></span>  
  
     <span data-ttu-id="35bd3-119"><xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> Kullanılarak erişilebilir <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="35bd3-119">The <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> can be accessed using <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> property.</span></span>  
  
     <span data-ttu-id="35bd3-120">Aşağıdaki kod örneği kayıtları `MyServiceAuthorizationManager` özel Yetkilendirme Yöneticisi.</span><span class="sxs-lookup"><span data-stu-id="35bd3-120">The following code example registers the `MyServiceAuthorizationManager` custom authorization manager.</span></span>  
  
     [!code-csharp[c_CustomAuthMgr#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#4)]
     [!code-vb[c_CustomAuthMgr#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#4)]  
  
### <a name="to-register-a-custom-authorization-manager-using-configuration"></a><span data-ttu-id="35bd3-121">Yapılandırması'nı kullanarak bir özel Yetkilendirme Yöneticisi kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="35bd3-121">To register a custom authorization manager using configuration</span></span>  
  
1.  <span data-ttu-id="35bd3-122">Hizmet yapılandırma dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="35bd3-122">Open the configuration file for the service.</span></span>  
  
2.  <span data-ttu-id="35bd3-123">Ekleme bir [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) için [ \<davranışları >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="35bd3-123">Add a [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md).</span></span>  
  
     <span data-ttu-id="35bd3-124">İçin [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md), ekleme bir `serviceAuthorizationManagerType` özniteliği ve değerini ayarlama için özel Yetkilendirme Yöneticisi'ni temsil eden türdür.</span><span class="sxs-lookup"><span data-stu-id="35bd3-124">To the [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md), add a `serviceAuthorizationManagerType` attribute and set its value to the type that represents the custom authorization manager.</span></span>  
  
3.  <span data-ttu-id="35bd3-125">Hizmet ve istemci arasındaki iletişimin güvenliğini sağlar bir bağlaması ekleyin.</span><span class="sxs-lookup"><span data-stu-id="35bd3-125">Add a binding that secures the communication between the client and service.</span></span>  
  
     <span data-ttu-id="35bd3-126">Bu iletişim için eklenen talepleri belirler seçilir bağlama <xref:System.IdentityModel.Policy.AuthorizationContext>, yetkilendirme kararları vermek için özel Yetkilendirme Yöneticisi'ni kullanır.</span><span class="sxs-lookup"><span data-stu-id="35bd3-126">The binding that is chosen for this communication determines the claims that are added to the <xref:System.IdentityModel.Policy.AuthorizationContext>, which the custom authorization manager uses to make authorization decisions.</span></span> <span data-ttu-id="35bd3-127">Sistem tarafından sağlanan bağlamalar hakkında daha fazla ayrıntı için bkz. [System-Provided bağlamaları](../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="35bd3-127">For more details about the system-provided bindings, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
4.  <span data-ttu-id="35bd3-128">Hizmet uç noktası, davranıştır ekleyerek ilişkilendirmek bir [ \<hizmet >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) öğesi ve değerini ayarlama `behaviorConfiguration` özniteliği name özniteliği değerine [ \<davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="35bd3-128">Associate the behavior to a service endpoint, by adding a [\<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) element and set the value of the `behaviorConfiguration` attribute to the value of the name attribute for the [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span></span>  
  
     <span data-ttu-id="35bd3-129">Hizmet uç noktasını yapılandırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Yapılandırma içinde hizmet uç noktası oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="35bd3-129">For more information about configuring a service endpoint, see [How to: Create a Service Endpoint in Configuration](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md).</span></span>  
  
     <span data-ttu-id="35bd3-130">Aşağıdaki kod örneği, özel Yetkilendirme Yöneticisi'ni kaydeder `Samples.MyServiceAuthorizationManager`.</span><span class="sxs-lookup"><span data-stu-id="35bd3-130">The following code example registers the custom authorization manager `Samples.MyServiceAuthorizationManager`.</span></span>  
  
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
    >  <span data-ttu-id="35bd3-131">Dize serviceAuthorizationManagerType belirttiğinizde, tam olarak nitelenmiş tür adını içermesi gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="35bd3-131">Note that when you specify the serviceAuthorizationManagerType, the string must contain the fully qualified type name.</span></span> <span data-ttu-id="35bd3-132">virgül koyun ve türünün tanımlandığı derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="35bd3-132">a comma, and the name of the assembly in which the type is defined.</span></span> <span data-ttu-id="35bd3-133">Derleme adı değiştirmeden bırakırsanız, WCF yük türü System.ServiceModel.dll dener.</span><span class="sxs-lookup"><span data-stu-id="35bd3-133">If you leave out the assembly name, WCF will attempt to load the type from System.ServiceModel.dll.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35bd3-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="35bd3-134">Example</span></span>  
 <span data-ttu-id="35bd3-135">Aşağıdaki kod örneği temel bir uygulamasını gösterir. bir <xref:System.ServiceModel.ServiceAuthorizationManager> geçersiz kılma içeren sınıf <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="35bd3-135">The following code example demonstrates a basic implementation of a <xref:System.ServiceModel.ServiceAuthorizationManager> class that includes overriding the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="35bd3-136">Örnek kodu inceler <xref:System.IdentityModel.Policy.AuthorizationContext> döndürür ve bir özel talep `true` zaman kaynağı bu özel talep için eşleşen eylem değerini <xref:System.ServiceModel.OperationContext>.</span><span class="sxs-lookup"><span data-stu-id="35bd3-136">The example code examines the <xref:System.IdentityModel.Policy.AuthorizationContext> for a custom claim and returns `true` when the resource for that custom claim matches the action value from the <xref:System.ServiceModel.OperationContext>.</span></span> <span data-ttu-id="35bd3-137">Daha eksiksiz bir uygulama için bir <xref:System.ServiceModel.ServiceAuthorizationManager> sınıfı [yetkilendirme ilkesi](../../../../docs/framework/wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="35bd3-137">For a more complete implementation of a <xref:System.ServiceModel.ServiceAuthorizationManager> class, see [Authorization Policy](../../../../docs/framework/wcf/samples/authorization-policy.md).</span></span>  
  
 [!code-csharp[c_CustomAuthMgr#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#2)]
 [!code-vb[c_CustomAuthMgr#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="35bd3-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35bd3-138">See also</span></span>
- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [<span data-ttu-id="35bd3-139">Yetkilendirme İlkesi</span><span class="sxs-lookup"><span data-stu-id="35bd3-139">Authorization Policy</span></span>](../../../../docs/framework/wcf/samples/authorization-policy.md)
- [<span data-ttu-id="35bd3-140">Yetkilendirme İlkesi</span><span class="sxs-lookup"><span data-stu-id="35bd3-140">Authorization Policy</span></span>](../../../../docs/framework/wcf/samples/authorization-policy.md)
