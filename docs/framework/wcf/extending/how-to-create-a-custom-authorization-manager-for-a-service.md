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
# <a name="how-to-create-a-custom-authorization-manager-for-a-service"></a>Nasıl yapılır: Bir Hizmet için Özel Yetkilendirme Yöneticisi Oluşturma

Windows Communication Foundation (WCF) içindeki kimlik modeli altyapısı, genişletilebilir bir talep tabanlı yetkilendirme modelini destekler. Talepler belirteçlerden ayıklanır ve isteğe bağlı olarak özel yetkilendirme ilkeleri tarafından işlenir ve ' a <xref:System.IdentityModel.Policy.AuthorizationContext>yerleştirilir. Yetkilendirme Yöneticisi, <xref:System.IdentityModel.Policy.AuthorizationContext> yetkilendirme kararları vermek için içindeki talepleri inceler.

Varsayılan olarak, yetkilendirme kararları <xref:System.ServiceModel.ServiceAuthorizationManager> sınıf tarafından yapılır; ancak, özel bir Yetkilendirme Yöneticisi oluşturularak bu kararlar geçersiz kılınabilir. Özel bir Yetkilendirme Yöneticisi oluşturmak için, yönteminden türetilen <xref:System.ServiceModel.ServiceAuthorizationManager> ve uygulayan <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> bir sınıf oluşturun. Yetkilendirme kararları, erişim verildiğinde ve <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> `false` erişim reddedildiğinde döndüren `true` yönteminde yapılır.

Yetkilendirme kararı ileti gövdesinin içeriğine bağımlıysa, <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemini kullanın.

Performans sorunları nedeniyle, mümkünse, yetkilendirme kararının ileti gövdesine erişim gerektirmemesi için uygulamanızı yeniden tasarlamanız gerekir.

Bir hizmet için özel Yetkilendirme Yöneticisi kaydı, kod veya yapılandırmada yapılabilir.

### <a name="to-create-a-custom-authorization-manager"></a>Özel bir Yetkilendirme Yöneticisi oluşturmak için

1. <xref:System.ServiceModel.ServiceAuthorizationManager> Sınıfından bir sınıf türet.

    [!code-csharp[c_CustomAuthMgr#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#5)]
    [!code-vb[c_CustomAuthMgr#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#5)]

2. Geçersiz kılma <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> yöntemi.

    Yetkilendirme kararları almak için <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> yöntemine geçirilen öğesini kullanın. <xref:System.ServiceModel.OperationContext>

    Aşağıdaki kod örneği, bir yetkilendirme <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> kararı vermek üzere özel talebi `http://www.contoso.com/claims/allowedoperation` bulmak için yöntemini kullanır.

    [!code-csharp[c_CustomAuthMgr#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#6)]
    [!code-vb[c_CustomAuthMgr#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#6)]

### <a name="to-register-a-custom-authorization-manager-using-code"></a>Kodu kullanarak özel bir Yetkilendirme Yöneticisi kaydetmek için

1. Özel Yetkilendirme Yöneticisi 'nin bir örneğini oluşturun ve bunu <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> özelliğine atayın.

    , <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> Özelliği kullanılarak <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> erişilebilir.

    Aşağıdaki kod örneği `MyServiceAuthorizationManager` özel yetkilendirme yöneticisini kaydeder.

    [!code-csharp[c_CustomAuthMgr#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#4)]
    [!code-vb[c_CustomAuthMgr#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#4)]

### <a name="to-register-a-custom-authorization-manager-using-configuration"></a>Yapılandırma kullanarak özel bir Yetkilendirme Yöneticisi kaydetmek için

1. Hizmet için yapılandırma dosyasını açın.

2. Davranışlara > bir [ \<ServiceAuthorization>ekleyin](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) . [ \<](../../configure-apps/file-schema/wcf/behaviors.md)

    ServiceAuthorization `serviceAuthorizationManagerType` >, bir öznitelik ekleyin ve değerini özel yetkilendirme yöneticisini temsil eden türe ayarlayın. [ \<](../../configure-apps/file-schema/wcf/serviceauthorization-element.md)

3. İstemci ve hizmet arasındaki iletişimin güvenliğini sağlayan bir bağlama ekleyin.

    Bu iletişim için seçilen bağlama, Özel Yetkilendirme Yöneticisi 'nin yetkilendirme kararları almak için kullandığı, <xref:System.IdentityModel.Policy.AuthorizationContext>öğesine eklenen talepleri belirler. Sistem tarafından sağlanmış bağlamalar hakkında daha fazla bilgi için bkz. [sistem tarafından sunulan bağlamalar](../system-provided-bindings.md).

4. `behaviorConfiguration` [ Bir\<Service >](../../configure-apps/file-schema/wcf/service.md) öğesi ekleyerek ve öznitelik değerini [ \<davranış >](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) öğesi için ad özniteliğinin değerine ayarlayarak, davranışı bir hizmet uç noktasıyla ilişkilendirin.

    Hizmet uç noktası yapılandırma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Yapılandırmada](../feature-details/how-to-create-a-service-endpoint-in-configuration.md)bir hizmet uç noktası oluşturun.

    Aşağıdaki kod örneği özel yetkilendirme Yöneticisini `Samples.MyServiceAuthorizationManager`kaydeder.

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
    > ServiceAuthorizationManagerType belirttiğinizde, dizenin tam nitelikli tür adını içermesi gerektiğini unutmayın. bir virgül ve türün tanımlandığı derlemenin adı. Derleme adını bıraktığınızda, WCF türü System. ServiceModel. dll ' den yüklemeyi dener.

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, <xref:System.ServiceModel.ServiceAuthorizationManager> <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> yöntemini geçersiz kılmayı içeren bir sınıfın temel bir uygulamasını gösterir. Örnek kod, <xref:System.IdentityModel.Policy.AuthorizationContext> özel bir talep için ' i inceler ve `true` bu özel talep için kaynak, <xref:System.ServiceModel.OperationContext>öğesinden eylem değeri ile eşleştiğinde döndürür. Bir <xref:System.ServiceModel.ServiceAuthorizationManager> sınıfın daha kapsamlı bir uygulanması için bkz. [Yetkilendirme İlkesi](../samples/authorization-policy.md).

[!code-csharp[c_CustomAuthMgr#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#2)]
[!code-vb[c_CustomAuthMgr#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#2)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [Yetkilendirme İlkesi](../samples/authorization-policy.md)
