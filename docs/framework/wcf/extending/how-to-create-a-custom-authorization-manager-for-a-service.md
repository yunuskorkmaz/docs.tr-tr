---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: bir hizmet için özel Yetkilendirme Yöneticisi oluşturma'
title: 'Nasıl yapılır: Bir Hizmet için Özel Yetkilendirme Yöneticisi Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Communication Foundation, extending
- OperationRequirement class
ms.assetid: 6214afde-44c1-4bf5-ba07-5ad6493620ea
ms.openlocfilehash: e5b5655bb8cd087e2c5140f45e80f8b079cf06c0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743726"
---
# <a name="how-to-create-a-custom-authorization-manager-for-a-service"></a><span data-ttu-id="258a3-103">Nasıl yapılır: Bir Hizmet için Özel Yetkilendirme Yöneticisi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="258a3-103">How to: Create a Custom Authorization Manager for a Service</span></span>

<span data-ttu-id="258a3-104">Windows Communication Foundation (WCF) içindeki kimlik modeli altyapısı, genişletilebilir bir talep tabanlı yetkilendirme modelini destekler.</span><span class="sxs-lookup"><span data-stu-id="258a3-104">The Identity Model infrastructure in Windows Communication Foundation (WCF) supports an extensible claims-based authorization model.</span></span> <span data-ttu-id="258a3-105">Talepler belirteçlerden ayıklanır ve isteğe bağlı olarak özel yetkilendirme ilkeleri tarafından işlenir ve ' a yerleştirilir <xref:System.IdentityModel.Policy.AuthorizationContext> .</span><span class="sxs-lookup"><span data-stu-id="258a3-105">Claims are extracted from tokens and optionally processed by custom authorization policies and then placed into an <xref:System.IdentityModel.Policy.AuthorizationContext>.</span></span> <span data-ttu-id="258a3-106">Yetkilendirme Yöneticisi, <xref:System.IdentityModel.Policy.AuthorizationContext> yetkilendirme kararları vermek için içindeki talepleri inceler.</span><span class="sxs-lookup"><span data-stu-id="258a3-106">An authorization manager examines the claims in the <xref:System.IdentityModel.Policy.AuthorizationContext> to make authorization decisions.</span></span>

<span data-ttu-id="258a3-107">Varsayılan olarak, yetkilendirme kararları sınıf tarafından yapılır <xref:System.ServiceModel.ServiceAuthorizationManager> ; ancak, özel bir Yetkilendirme Yöneticisi oluşturularak bu kararlar geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="258a3-107">By default, authorization decisions are made by the <xref:System.ServiceModel.ServiceAuthorizationManager> class; however these decisions can be overridden by creating a custom authorization manager.</span></span> <span data-ttu-id="258a3-108">Özel bir Yetkilendirme Yöneticisi oluşturmak için, yönteminden türetilen ve uygulayan bir sınıf oluşturun <xref:System.ServiceModel.ServiceAuthorizationManager> <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> .</span><span class="sxs-lookup"><span data-stu-id="258a3-108">To create a custom authorization manager, create a class that derives from <xref:System.ServiceModel.ServiceAuthorizationManager> and implement <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="258a3-109">Yetkilendirme kararları, <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> `true` erişim verildiğinde ve erişim reddedildiğinde döndüren yönteminde yapılır `false` .</span><span class="sxs-lookup"><span data-stu-id="258a3-109">Authorization decisions are made in the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method, which returns `true` when access is granted and `false` when access is denied.</span></span>

<span data-ttu-id="258a3-110">Yetkilendirme kararı ileti gövdesinin içeriğine bağımlıysa, <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="258a3-110">If the authorization decision depends on the contents of the message body, use the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method.</span></span>

<span data-ttu-id="258a3-111">Performans sorunları nedeniyle, mümkünse, yetkilendirme kararının ileti gövdesine erişim gerektirmemesi için uygulamanızı yeniden tasarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="258a3-111">Because of performance issues, if possible you should redesign your application so that the authorization decision does not require access to the message body.</span></span>

<span data-ttu-id="258a3-112">Bir hizmet için özel Yetkilendirme Yöneticisi kaydı, kod veya yapılandırmada yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="258a3-112">Registration of the custom authorization manager for a service can be done in code or configuration.</span></span>

### <a name="to-create-a-custom-authorization-manager"></a><span data-ttu-id="258a3-113">Özel bir Yetkilendirme Yöneticisi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="258a3-113">To create a custom authorization manager</span></span>

1. <span data-ttu-id="258a3-114">Sınıfından bir sınıf türet <xref:System.ServiceModel.ServiceAuthorizationManager> .</span><span class="sxs-lookup"><span data-stu-id="258a3-114">Derive a class from the <xref:System.ServiceModel.ServiceAuthorizationManager> class.</span></span>

    [!code-csharp[c_CustomAuthMgr#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#5)]
    [!code-vb[c_CustomAuthMgr#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#5)]

2. <span data-ttu-id="258a3-115">Yöntemini geçersiz kılın <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> .</span><span class="sxs-lookup"><span data-stu-id="258a3-115">Override the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> method.</span></span>

    <span data-ttu-id="258a3-116"><xref:System.ServiceModel.OperationContext> <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> Yetkilendirme kararları almak için yöntemine geçirilen öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="258a3-116">Use the <xref:System.ServiceModel.OperationContext> that is passed to the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> method to make authorization decisions.</span></span>

    <span data-ttu-id="258a3-117">Aşağıdaki kod örneği, <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> `http://www.contoso.com/claims/allowedoperation` bir yetkilendirme kararı vermek üzere özel talebi bulmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="258a3-117">The following code example uses the <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> method to find the custom claim `http://www.contoso.com/claims/allowedoperation` to make an authorization decision.</span></span>

    [!code-csharp[c_CustomAuthMgr#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#6)]
    [!code-vb[c_CustomAuthMgr#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#6)]

### <a name="to-register-a-custom-authorization-manager-using-code"></a><span data-ttu-id="258a3-118">Kodu kullanarak özel bir Yetkilendirme Yöneticisi kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="258a3-118">To register a custom authorization manager using code</span></span>

1. <span data-ttu-id="258a3-119">Özel Yetkilendirme Yöneticisi 'nin bir örneğini oluşturun ve bunu <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> özelliğine atayın.</span><span class="sxs-lookup"><span data-stu-id="258a3-119">Create an instance of the custom authorization manager and assign it to the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> property.</span></span>

    <span data-ttu-id="258a3-120">, <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> Özelliği kullanılarak erişilebilir <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> .</span><span class="sxs-lookup"><span data-stu-id="258a3-120">The <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> can be accessed using <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> property.</span></span>

    <span data-ttu-id="258a3-121">Aşağıdaki kod örneği `MyServiceAuthorizationManager` özel yetkilendirme yöneticisini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="258a3-121">The following code example registers the `MyServiceAuthorizationManager` custom authorization manager.</span></span>

    [!code-csharp[c_CustomAuthMgr#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#4)]
    [!code-vb[c_CustomAuthMgr#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#4)]

### <a name="to-register-a-custom-authorization-manager-using-configuration"></a><span data-ttu-id="258a3-122">Yapılandırma kullanarak özel bir Yetkilendirme Yöneticisi kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="258a3-122">To register a custom authorization manager using configuration</span></span>

1. <span data-ttu-id="258a3-123">Hizmet için yapılandırma dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="258a3-123">Open the configuration file for the service.</span></span>

2. <span data-ttu-id="258a3-124">[\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md)Öğesine öğesine ekleyin [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) .</span><span class="sxs-lookup"><span data-stu-id="258a3-124">Add a [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) to the [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md).</span></span>

    <span data-ttu-id="258a3-125">Öğesine [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) bir `serviceAuthorizationManagerType` öznitelik ekleyin ve değerini özel yetkilendirme yöneticisini temsil eden türe ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="258a3-125">To the [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md), add a `serviceAuthorizationManagerType` attribute and set its value to the type that represents the custom authorization manager.</span></span>

3. <span data-ttu-id="258a3-126">İstemci ve hizmet arasındaki iletişimin güvenliğini sağlayan bir bağlama ekleyin.</span><span class="sxs-lookup"><span data-stu-id="258a3-126">Add a binding that secures the communication between the client and service.</span></span>

    <span data-ttu-id="258a3-127">Bu iletişim için seçilen bağlama, <xref:System.IdentityModel.Policy.AuthorizationContext> Özel Yetkilendirme Yöneticisi 'nin yetkilendirme kararları almak için kullandığı, öğesine eklenen talepleri belirler.</span><span class="sxs-lookup"><span data-stu-id="258a3-127">The binding that is chosen for this communication determines the claims that are added to the <xref:System.IdentityModel.Policy.AuthorizationContext>, which the custom authorization manager uses to make authorization decisions.</span></span> <span data-ttu-id="258a3-128">Sistem tarafından sağlanmış bağlamalar hakkında daha fazla bilgi için bkz. [sistem tarafından sunulan bağlamalar](../system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="258a3-128">For more details about the system-provided bindings, see [System-Provided Bindings](../system-provided-bindings.md).</span></span>

4. <span data-ttu-id="258a3-129">Bir [\<service>](../../configure-apps/file-schema/wcf/service.md) öğe ekleyerek ve `behaviorConfiguration` özniteliğin değerini öğesi için ad özniteliğinin değerine ayarlayarak, davranışı bir hizmet uç noktasıyla ilişkilendirin [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) .</span><span class="sxs-lookup"><span data-stu-id="258a3-129">Associate the behavior to a service endpoint, by adding a [\<service>](../../configure-apps/file-schema/wcf/service.md) element and set the value of the `behaviorConfiguration` attribute to the value of the name attribute for the [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span></span>

    <span data-ttu-id="258a3-130">Hizmet uç noktası yapılandırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: yapılandırma Içinde hizmet uç noktası oluşturma](../feature-details/how-to-create-a-service-endpoint-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="258a3-130">For more information about configuring a service endpoint, see [How to: Create a Service Endpoint in Configuration](../feature-details/how-to-create-a-service-endpoint-in-configuration.md).</span></span>

    <span data-ttu-id="258a3-131">Aşağıdaki kod örneği özel yetkilendirme yöneticisini kaydeder `Samples.MyServiceAuthorizationManager` .</span><span class="sxs-lookup"><span data-stu-id="258a3-131">The following code example registers the custom authorization manager `Samples.MyServiceAuthorizationManager`.</span></span>

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
    > <span data-ttu-id="258a3-132">ServiceAuthorizationManagerType belirttiğinizde, dizenin tam nitelikli tür adını içermesi gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="258a3-132">Note that when you specify the serviceAuthorizationManagerType, the string must contain the fully qualified type name.</span></span> <span data-ttu-id="258a3-133">bir virgül ve türün tanımlandığı derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="258a3-133">a comma, and the name of the assembly in which the type is defined.</span></span> <span data-ttu-id="258a3-134">Derleme adını bıraktığınızda, WCF System.ServiceModel.dll türü yüklemeyi dener.</span><span class="sxs-lookup"><span data-stu-id="258a3-134">If you leave out the assembly name, WCF will attempt to load the type from System.ServiceModel.dll.</span></span>

## <a name="example"></a><span data-ttu-id="258a3-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="258a3-135">Example</span></span>

<span data-ttu-id="258a3-136">Aşağıdaki kod örneği, <xref:System.ServiceModel.ServiceAuthorizationManager> yöntemini geçersiz kılmayı içeren bir sınıfın temel bir uygulamasını gösterir <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> .</span><span class="sxs-lookup"><span data-stu-id="258a3-136">The following code example demonstrates a basic implementation of a <xref:System.ServiceModel.ServiceAuthorizationManager> class that includes overriding the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="258a3-137">Örnek kod, <xref:System.IdentityModel.Policy.AuthorizationContext> özel bir talep için ' i inceler ve `true` Bu özel talep için kaynak, öğesinden eylem değeri ile eşleştiğinde döndürür <xref:System.ServiceModel.OperationContext> .</span><span class="sxs-lookup"><span data-stu-id="258a3-137">The example code examines the <xref:System.IdentityModel.Policy.AuthorizationContext> for a custom claim and returns `true` when the resource for that custom claim matches the action value from the <xref:System.ServiceModel.OperationContext>.</span></span> <span data-ttu-id="258a3-138">Bir sınıfın daha kapsamlı bir uygulanması için <xref:System.ServiceModel.ServiceAuthorizationManager> bkz. [Yetkilendirme İlkesi](../samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="258a3-138">For a more complete implementation of a <xref:System.ServiceModel.ServiceAuthorizationManager> class, see [Authorization Policy](../samples/authorization-policy.md).</span></span>

[!code-csharp[c_CustomAuthMgr#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#2)]
[!code-vb[c_CustomAuthMgr#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#2)]

## <a name="see-also"></a><span data-ttu-id="258a3-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="258a3-139">See also</span></span>

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [<span data-ttu-id="258a3-140">Yetkilendirme İlkesi</span><span class="sxs-lookup"><span data-stu-id="258a3-140">Authorization Policy</span></span>](../samples/authorization-policy.md)
