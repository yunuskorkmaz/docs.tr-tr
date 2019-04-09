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
ms.openlocfilehash: 6a168902b79bd27345c9d9e2371947cc9d64233c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59156500"
---
# <a name="how-to-create-a-custom-authorization-manager-for-a-service"></a>Nasıl yapılır: Bir Hizmet için Özel Yetkilendirme Yöneticisi Oluşturma
Windows Communication Foundation (WCF) kimlik modeli altyapısı, bir Genişletilebilir beyana dayalı yetkilendirme modelini destekler. Talep belirteçleri ayıklanır ve isteğe bağlı olarak özel yetkilendirme ilkeleri tarafından işlenir ve ardından yerleştirilip bir <xref:System.IdentityModel.Policy.AuthorizationContext>. Yetkilendirme Yöneticisi Taleplerde inceler <xref:System.IdentityModel.Policy.AuthorizationContext> yetkilendirme kararları vermek için.  
  
 Varsayılan olarak, yetkilendirme kararları tarafından yapılan <xref:System.ServiceModel.ServiceAuthorizationManager> sınıfı; ancak bu kararların bir özel Yetkilendirme Yöneticisi oluşturma tarafından geçersiz kılınabilir. Özel Yetkilendirme Yöneticisi oluşturma için türetilen bir sınıf oluşturmanız <xref:System.ServiceModel.ServiceAuthorizationManager> ve uygulama <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> yöntemi. Yetkilendirme kararları içinde yapılan <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> döndüren yöntemi `true` erişim izni ne zaman ve `false` zaman erişim engellendi.  
  
 İleti gövdesi içeriğini temel yetkilendirme kararı bağlıdır kullanırsanız <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemi.  
  
 Yetkilendirme kararı, ileti gövdesi erişimi gerektirmez, böylece performans sorunları nedeniyle Mümkünse, uygulamanızı yeniden tasarlamanız.  
  
 Bir hizmet için özel Yetkilendirme Yöneticisi kaydı, kod veya yapılandırma yapılabilir.  
  
### <a name="to-create-a-custom-authorization-manager"></a>Özel Yetkilendirme Yöneticisi oluşturma  
  
1.  Öğesinden bir sınıf türetin <xref:System.ServiceModel.ServiceAuthorizationManager> sınıfı.  
  
     [!code-csharp[c_CustomAuthMgr#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#5)]
     [!code-vb[c_CustomAuthMgr#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#5)]  
  
2.  Geçersiz kılma <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> yöntemi.  
  
     Kullanım <xref:System.ServiceModel.OperationContext> yapan <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> yetkilendirme kararları vermek için yöntemi.  
  
     Aşağıdaki kod örneğinde <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> özel talep bulmak için yöntem `http://www.contoso.com/claims/allowedoperation` bir yetkilendirme kararı almak için.  
  
     [!code-csharp[c_CustomAuthMgr#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#6)]
     [!code-vb[c_CustomAuthMgr#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#6)]  
  
### <a name="to-register-a-custom-authorization-manager-using-code"></a>Kod kullanarak bir özel Yetkilendirme Yöneticisi kaydetmek için  
  
1.  Özel yetkilendirme örneği Yöneticisi oluşturun ve atayın <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> özelliği.  
  
     <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> Kullanılarak erişilebilir <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> özelliği.  
  
     Aşağıdaki kod örneği kayıtları `MyServiceAuthorizationManager` özel Yetkilendirme Yöneticisi.  
  
     [!code-csharp[c_CustomAuthMgr#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#4)]
     [!code-vb[c_CustomAuthMgr#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#4)]  
  
### <a name="to-register-a-custom-authorization-manager-using-configuration"></a>Yapılandırması'nı kullanarak bir özel Yetkilendirme Yöneticisi kaydetmek için  
  
1.  Hizmet yapılandırma dosyasını açın.  
  
2.  Ekleme bir [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) için [ \<davranışları >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md).  
  
     İçin [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md), ekleme bir `serviceAuthorizationManagerType` özniteliği ve değerini ayarlama için özel Yetkilendirme Yöneticisi'ni temsil eden türdür.  
  
3.  Hizmet ve istemci arasındaki iletişimin güvenliğini sağlar bir bağlaması ekleyin.  
  
     Bu iletişim için eklenen talepleri belirler seçilir bağlama <xref:System.IdentityModel.Policy.AuthorizationContext>, yetkilendirme kararları vermek için özel Yetkilendirme Yöneticisi'ni kullanır. Sistem tarafından sağlanan bağlamalar hakkında daha fazla ayrıntı için bkz. [System-Provided bağlamaları](../../../../docs/framework/wcf/system-provided-bindings.md).  
  
4.  Hizmet uç noktası, davranıştır ekleyerek ilişkilendirmek bir [ \<hizmet >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) öğesi ve değerini ayarlama `behaviorConfiguration` özniteliği name özniteliği değerine [ \<davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) öğesi.  
  
     Hizmet uç noktasını yapılandırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Yapılandırma içinde hizmet uç noktası oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md).  
  
     Aşağıdaki kod örneği, özel Yetkilendirme Yöneticisi'ni kaydeder `Samples.MyServiceAuthorizationManager`.  
  
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
    >  Dize serviceAuthorizationManagerType belirttiğinizde, tam olarak nitelenmiş tür adını içermesi gerektiğini unutmayın. virgül koyun ve türünün tanımlandığı derlemenin adı. Derleme adı değiştirmeden bırakırsanız, WCF yük türü System.ServiceModel.dll dener.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği temel bir uygulamasını gösterir. bir <xref:System.ServiceModel.ServiceAuthorizationManager> geçersiz kılma içeren sınıf <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> yöntemi. Örnek kodu inceler <xref:System.IdentityModel.Policy.AuthorizationContext> döndürür ve bir özel talep `true` zaman kaynağı bu özel talep için eşleşen eylem değerini <xref:System.ServiceModel.OperationContext>. Daha eksiksiz bir uygulama için bir <xref:System.ServiceModel.ServiceAuthorizationManager> sınıfı [yetkilendirme ilkesi](../../../../docs/framework/wcf/samples/authorization-policy.md).  
  
 [!code-csharp[c_CustomAuthMgr#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#2)]
 [!code-vb[c_CustomAuthMgr#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [Yetkilendirme İlkesi](../../../../docs/framework/wcf/samples/authorization-policy.md)
