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
# <a name="how-to-create-a-custom-authorization-manager-for-a-service"></a>Nasıl yapılır: Bir Hizmet için Özel Yetkilendirme Yöneticisi Oluşturma

Windows Communication Foundation (WCF) içindeki kimlik modeli altyapısı, genişletilebilir bir talep tabanlı yetkilendirme modelini destekler. Talepler belirteçlerden ayıklanır ve isteğe bağlı olarak özel yetkilendirme ilkeleri tarafından işlenir ve ' a yerleştirilir <xref:System.IdentityModel.Policy.AuthorizationContext> . Yetkilendirme Yöneticisi, <xref:System.IdentityModel.Policy.AuthorizationContext> yetkilendirme kararları vermek için içindeki talepleri inceler.

Varsayılan olarak, yetkilendirme kararları sınıf tarafından yapılır <xref:System.ServiceModel.ServiceAuthorizationManager> ; ancak, özel bir Yetkilendirme Yöneticisi oluşturularak bu kararlar geçersiz kılınabilir. Özel bir Yetkilendirme Yöneticisi oluşturmak için, yönteminden türetilen ve uygulayan bir sınıf oluşturun <xref:System.ServiceModel.ServiceAuthorizationManager> <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> . Yetkilendirme kararları, <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> `true` erişim verildiğinde ve erişim reddedildiğinde döndüren yönteminde yapılır `false` .

Yetkilendirme kararı ileti gövdesinin içeriğine bağımlıysa, <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemini kullanın.

Performans sorunları nedeniyle, mümkünse, yetkilendirme kararının ileti gövdesine erişim gerektirmemesi için uygulamanızı yeniden tasarlamanız gerekir.

Bir hizmet için özel Yetkilendirme Yöneticisi kaydı, kod veya yapılandırmada yapılabilir.

### <a name="to-create-a-custom-authorization-manager"></a>Özel bir Yetkilendirme Yöneticisi oluşturmak için

1. Sınıfından bir sınıf türet <xref:System.ServiceModel.ServiceAuthorizationManager> .

    [!code-csharp[c_CustomAuthMgr#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#5)]
    [!code-vb[c_CustomAuthMgr#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#5)]

2. Yöntemini geçersiz kılın <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> .

    <xref:System.ServiceModel.OperationContext> <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> Yetkilendirme kararları almak için yöntemine geçirilen öğesini kullanın.

    Aşağıdaki kod örneği, <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> `http://www.contoso.com/claims/allowedoperation` bir yetkilendirme kararı vermek üzere özel talebi bulmak için yöntemini kullanır.

    [!code-csharp[c_CustomAuthMgr#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#6)]
    [!code-vb[c_CustomAuthMgr#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#6)]

### <a name="to-register-a-custom-authorization-manager-using-code"></a>Kodu kullanarak özel bir Yetkilendirme Yöneticisi kaydetmek için

1. Özel Yetkilendirme Yöneticisi 'nin bir örneğini oluşturun ve bunu <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> özelliğine atayın.

    , <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> Özelliği kullanılarak erişilebilir <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> .

    Aşağıdaki kod örneği `MyServiceAuthorizationManager` özel yetkilendirme yöneticisini kaydeder.

    [!code-csharp[c_CustomAuthMgr#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#4)]
    [!code-vb[c_CustomAuthMgr#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#4)]

### <a name="to-register-a-custom-authorization-manager-using-configuration"></a>Yapılandırma kullanarak özel bir Yetkilendirme Yöneticisi kaydetmek için

1. Hizmet için yapılandırma dosyasını açın.

2. [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md)Öğesine öğesine ekleyin [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) .

    Öğesine [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) bir `serviceAuthorizationManagerType` öznitelik ekleyin ve değerini özel yetkilendirme yöneticisini temsil eden türe ayarlayın.

3. İstemci ve hizmet arasındaki iletişimin güvenliğini sağlayan bir bağlama ekleyin.

    Bu iletişim için seçilen bağlama, <xref:System.IdentityModel.Policy.AuthorizationContext> Özel Yetkilendirme Yöneticisi 'nin yetkilendirme kararları almak için kullandığı, öğesine eklenen talepleri belirler. Sistem tarafından sağlanmış bağlamalar hakkında daha fazla bilgi için bkz. [sistem tarafından sunulan bağlamalar](../system-provided-bindings.md).

4. Bir [\<service>](../../configure-apps/file-schema/wcf/service.md) öğe ekleyerek ve `behaviorConfiguration` özniteliğin değerini öğesi için ad özniteliğinin değerine ayarlayarak, davranışı bir hizmet uç noktasıyla ilişkilendirin [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) .

    Hizmet uç noktası yapılandırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: yapılandırma Içinde hizmet uç noktası oluşturma](../feature-details/how-to-create-a-service-endpoint-in-configuration.md).

    Aşağıdaki kod örneği özel yetkilendirme yöneticisini kaydeder `Samples.MyServiceAuthorizationManager` .

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
    > ServiceAuthorizationManagerType belirttiğinizde, dizenin tam nitelikli tür adını içermesi gerektiğini unutmayın. bir virgül ve türün tanımlandığı derlemenin adı. Derleme adını bıraktığınızda, WCF System.ServiceModel.dll türü yüklemeyi dener.

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, <xref:System.ServiceModel.ServiceAuthorizationManager> yöntemini geçersiz kılmayı içeren bir sınıfın temel bir uygulamasını gösterir <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> . Örnek kod, <xref:System.IdentityModel.Policy.AuthorizationContext> özel bir talep için ' i inceler ve `true` Bu özel talep için kaynak, öğesinden eylem değeri ile eşleştiğinde döndürür <xref:System.ServiceModel.OperationContext> . Bir sınıfın daha kapsamlı bir uygulanması için <xref:System.ServiceModel.ServiceAuthorizationManager> bkz. [Yetkilendirme İlkesi](../samples/authorization-policy.md).

[!code-csharp[c_CustomAuthMgr#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#2)]
[!code-vb[c_CustomAuthMgr#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#2)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [Yetkilendirme İlkesi](../samples/authorization-policy.md)
