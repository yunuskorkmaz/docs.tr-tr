---
title: 'Nasıl yapılır: Bir Hizmet için Özel Yetkilendirme Yöneticisi Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Communication Foundation, extending
- OperationRequirement class
ms.assetid: 6214afde-44c1-4bf5-ba07-5ad6493620ea
ms.openlocfilehash: 9c28cb81b78f80505cfcf5f7e4dfdba083bd0793
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797113"
---
# <a name="how-to-create-a-custom-authorization-manager-for-a-service"></a><span data-ttu-id="a98cd-102">Nasıl yapılır: Bir Hizmet için Özel Yetkilendirme Yöneticisi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a98cd-102">How to: Create a Custom Authorization Manager for a Service</span></span>

<span data-ttu-id="a98cd-103">Windows Communication Foundation (WCF) içindeki kimlik modeli altyapısı, genişletilebilir bir talep tabanlı yetkilendirme modelini destekler.</span><span class="sxs-lookup"><span data-stu-id="a98cd-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) supports an extensible claims-based authorization model.</span></span> <span data-ttu-id="a98cd-104">Talepler belirteçlerden ayıklanır ve isteğe bağlı olarak özel yetkilendirme ilkeleri tarafından işlenir ve ' a <xref:System.IdentityModel.Policy.AuthorizationContext>yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a98cd-104">Claims are extracted from tokens and optionally processed by custom authorization policies and then placed into an <xref:System.IdentityModel.Policy.AuthorizationContext>.</span></span> <span data-ttu-id="a98cd-105">Yetkilendirme Yöneticisi, <xref:System.IdentityModel.Policy.AuthorizationContext> yetkilendirme kararları vermek için içindeki talepleri inceler.</span><span class="sxs-lookup"><span data-stu-id="a98cd-105">An authorization manager examines the claims in the <xref:System.IdentityModel.Policy.AuthorizationContext> to make authorization decisions.</span></span>

<span data-ttu-id="a98cd-106">Varsayılan olarak, yetkilendirme kararları <xref:System.ServiceModel.ServiceAuthorizationManager> sınıf tarafından yapılır; ancak, özel bir Yetkilendirme Yöneticisi oluşturularak bu kararlar geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="a98cd-106">By default, authorization decisions are made by the <xref:System.ServiceModel.ServiceAuthorizationManager> class; however these decisions can be overridden by creating a custom authorization manager.</span></span> <span data-ttu-id="a98cd-107">Özel bir Yetkilendirme Yöneticisi oluşturmak için, yönteminden türetilen <xref:System.ServiceModel.ServiceAuthorizationManager> ve uygulayan <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a98cd-107">To create a custom authorization manager, create a class that derives from <xref:System.ServiceModel.ServiceAuthorizationManager> and implement <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="a98cd-108">Yetkilendirme kararları, erişim verildiğinde ve <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> `false` erişim reddedildiğinde döndüren `true` yönteminde yapılır.</span><span class="sxs-lookup"><span data-stu-id="a98cd-108">Authorization decisions are made in the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method, which returns `true` when access is granted and `false` when access is denied.</span></span>

<span data-ttu-id="a98cd-109">Yetkilendirme kararı ileti gövdesinin içeriğine bağımlıysa, <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a98cd-109">If the authorization decision depends on the contents of the message body, use the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method.</span></span>

<span data-ttu-id="a98cd-110">Performans sorunları nedeniyle, mümkünse, yetkilendirme kararının ileti gövdesine erişim gerektirmemesi için uygulamanızı yeniden tasarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a98cd-110">Because of performance issues, if possible you should redesign your application so that the authorization decision does not require access to the message body.</span></span>

<span data-ttu-id="a98cd-111">Bir hizmet için özel Yetkilendirme Yöneticisi kaydı, kod veya yapılandırmada yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="a98cd-111">Registration of the custom authorization manager for a service can be done in code or configuration.</span></span>

### <a name="to-create-a-custom-authorization-manager"></a><span data-ttu-id="a98cd-112">Özel bir Yetkilendirme Yöneticisi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a98cd-112">To create a custom authorization manager</span></span>

1. <span data-ttu-id="a98cd-113"><xref:System.ServiceModel.ServiceAuthorizationManager> Sınıfından bir sınıf türet.</span><span class="sxs-lookup"><span data-stu-id="a98cd-113">Derive a class from the <xref:System.ServiceModel.ServiceAuthorizationManager> class.</span></span>

    [!code-csharp[c_CustomAuthMgr#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#5)]
    [!code-vb[c_CustomAuthMgr#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#5)]

2. <span data-ttu-id="a98cd-114">Geçersiz kılma <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a98cd-114">Override the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> method.</span></span>

    <span data-ttu-id="a98cd-115">Yetkilendirme kararları almak için <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> yöntemine geçirilen öğesini kullanın. <xref:System.ServiceModel.OperationContext></span><span class="sxs-lookup"><span data-stu-id="a98cd-115">Use the <xref:System.ServiceModel.OperationContext> that is passed to the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> method to make authorization decisions.</span></span>

    <span data-ttu-id="a98cd-116">Aşağıdaki kod örneği, bir yetkilendirme <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> kararı vermek üzere özel talebi `http://www.contoso.com/claims/allowedoperation` bulmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a98cd-116">The following code example uses the <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> method to find the custom claim `http://www.contoso.com/claims/allowedoperation` to make an authorization decision.</span></span>

    [!code-csharp[c_CustomAuthMgr#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#6)]
    [!code-vb[c_CustomAuthMgr#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#6)]

### <a name="to-register-a-custom-authorization-manager-using-code"></a><span data-ttu-id="a98cd-117">Kodu kullanarak özel bir Yetkilendirme Yöneticisi kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="a98cd-117">To register a custom authorization manager using code</span></span>

1. <span data-ttu-id="a98cd-118">Özel Yetkilendirme Yöneticisi 'nin bir örneğini oluşturun ve bunu <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> özelliğine atayın.</span><span class="sxs-lookup"><span data-stu-id="a98cd-118">Create an instance of the custom authorization manager and assign it to the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> property.</span></span>

    <span data-ttu-id="a98cd-119">, <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> Özelliği kullanılarak <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="a98cd-119">The <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> can be accessed using <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> property.</span></span>

    <span data-ttu-id="a98cd-120">Aşağıdaki kod örneği `MyServiceAuthorizationManager` özel yetkilendirme yöneticisini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a98cd-120">The following code example registers the `MyServiceAuthorizationManager` custom authorization manager.</span></span>

    [!code-csharp[c_CustomAuthMgr#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#4)]
    [!code-vb[c_CustomAuthMgr#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#4)]

### <a name="to-register-a-custom-authorization-manager-using-configuration"></a><span data-ttu-id="a98cd-121">Yapılandırma kullanarak özel bir Yetkilendirme Yöneticisi kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="a98cd-121">To register a custom authorization manager using configuration</span></span>

1. <span data-ttu-id="a98cd-122">Hizmet için yapılandırma dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="a98cd-122">Open the configuration file for the service.</span></span>

2. <span data-ttu-id="a98cd-123">Davranışlara > bir [ \<ServiceAuthorization>ekleyin](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) . [ \<](../../configure-apps/file-schema/wcf/behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a98cd-123">Add a [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) to the [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md).</span></span>

    <span data-ttu-id="a98cd-124">ServiceAuthorization `serviceAuthorizationManagerType` >, bir öznitelik ekleyin ve değerini özel yetkilendirme yöneticisini temsil eden türe ayarlayın. [ \<](../../configure-apps/file-schema/wcf/serviceauthorization-element.md)</span><span class="sxs-lookup"><span data-stu-id="a98cd-124">To the [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md), add a `serviceAuthorizationManagerType` attribute and set its value to the type that represents the custom authorization manager.</span></span>

3. <span data-ttu-id="a98cd-125">İstemci ve hizmet arasındaki iletişimin güvenliğini sağlayan bir bağlama ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a98cd-125">Add a binding that secures the communication between the client and service.</span></span>

    <span data-ttu-id="a98cd-126">Bu iletişim için seçilen bağlama, Özel Yetkilendirme Yöneticisi 'nin yetkilendirme kararları almak için kullandığı, <xref:System.IdentityModel.Policy.AuthorizationContext>öğesine eklenen talepleri belirler.</span><span class="sxs-lookup"><span data-stu-id="a98cd-126">The binding that is chosen for this communication determines the claims that are added to the <xref:System.IdentityModel.Policy.AuthorizationContext>, which the custom authorization manager uses to make authorization decisions.</span></span> <span data-ttu-id="a98cd-127">Sistem tarafından sağlanmış bağlamalar hakkında daha fazla bilgi için bkz. [sistem tarafından sunulan bağlamalar](../system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="a98cd-127">For more details about the system-provided bindings, see [System-Provided Bindings](../system-provided-bindings.md).</span></span>

4. <span data-ttu-id="a98cd-128">`behaviorConfiguration` [ Bir\<Service >](../../configure-apps/file-schema/wcf/service.md) öğesi ekleyerek ve öznitelik değerini [ \<davranış >](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) öğesi için ad özniteliğinin değerine ayarlayarak, davranışı bir hizmet uç noktasıyla ilişkilendirin.</span><span class="sxs-lookup"><span data-stu-id="a98cd-128">Associate the behavior to a service endpoint, by adding a [\<service>](../../configure-apps/file-schema/wcf/service.md) element and set the value of the `behaviorConfiguration` attribute to the value of the name attribute for the [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span></span>

    <span data-ttu-id="a98cd-129">Hizmet uç noktası yapılandırma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Yapılandırmada](../feature-details/how-to-create-a-service-endpoint-in-configuration.md)bir hizmet uç noktası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a98cd-129">For more information about configuring a service endpoint, see [How to: Create a Service Endpoint in Configuration](../feature-details/how-to-create-a-service-endpoint-in-configuration.md).</span></span>

    <span data-ttu-id="a98cd-130">Aşağıdaki kod örneği özel yetkilendirme Yöneticisini `Samples.MyServiceAuthorizationManager`kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a98cd-130">The following code example registers the custom authorization manager `Samples.MyServiceAuthorizationManager`.</span></span>

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
    > <span data-ttu-id="a98cd-131">ServiceAuthorizationManagerType belirttiğinizde, dizenin tam nitelikli tür adını içermesi gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a98cd-131">Note that when you specify the serviceAuthorizationManagerType, the string must contain the fully qualified type name.</span></span> <span data-ttu-id="a98cd-132">bir virgül ve türün tanımlandığı derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="a98cd-132">a comma, and the name of the assembly in which the type is defined.</span></span> <span data-ttu-id="a98cd-133">Derleme adını bıraktığınızda, WCF türü System. ServiceModel. dll ' den yüklemeyi dener.</span><span class="sxs-lookup"><span data-stu-id="a98cd-133">If you leave out the assembly name, WCF will attempt to load the type from System.ServiceModel.dll.</span></span>

## <a name="example"></a><span data-ttu-id="a98cd-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="a98cd-134">Example</span></span>

<span data-ttu-id="a98cd-135">Aşağıdaki kod örneği, <xref:System.ServiceModel.ServiceAuthorizationManager> <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> yöntemini geçersiz kılmayı içeren bir sınıfın temel bir uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a98cd-135">The following code example demonstrates a basic implementation of a <xref:System.ServiceModel.ServiceAuthorizationManager> class that includes overriding the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="a98cd-136">Örnek kod, <xref:System.IdentityModel.Policy.AuthorizationContext> özel bir talep için ' i inceler ve `true` bu özel talep için kaynak, <xref:System.ServiceModel.OperationContext>öğesinden eylem değeri ile eşleştiğinde döndürür.</span><span class="sxs-lookup"><span data-stu-id="a98cd-136">The example code examines the <xref:System.IdentityModel.Policy.AuthorizationContext> for a custom claim and returns `true` when the resource for that custom claim matches the action value from the <xref:System.ServiceModel.OperationContext>.</span></span> <span data-ttu-id="a98cd-137">Bir <xref:System.ServiceModel.ServiceAuthorizationManager> sınıfın daha kapsamlı bir uygulanması için bkz. [Yetkilendirme İlkesi](../samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="a98cd-137">For a more complete implementation of a <xref:System.ServiceModel.ServiceAuthorizationManager> class, see [Authorization Policy](../samples/authorization-policy.md).</span></span>

[!code-csharp[c_CustomAuthMgr#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#2)]
[!code-vb[c_CustomAuthMgr#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#2)]

## <a name="see-also"></a><span data-ttu-id="a98cd-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a98cd-138">See also</span></span>

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [<span data-ttu-id="a98cd-139">Yetkilendirme İlkesi</span><span class="sxs-lookup"><span data-stu-id="a98cd-139">Authorization Policy</span></span>](../samples/authorization-policy.md)
