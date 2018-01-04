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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1977a26f3185ad1ef85584b0da7d63826b7f93ea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-custom-authorization-manager-for-a-service"></a>Nasıl yapılır: Bir Hizmet için Özel Yetkilendirme Yöneticisi Oluşturma
Kimlik modeli altyapısında [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Genişletilebilir talep tabanlı yetkilendirme modelini destekler. Talep belirteçlerinden ayıklanan ve isteğe bağlı olarak özel yetkilendirme ilkeleri tarafından işlenir ve içine yerleştirilen bir <xref:System.IdentityModel.Policy.AuthorizationContext>. Bir Yetkilendirme Yöneticisi'ni Taleplerde inceler <xref:System.IdentityModel.Policy.AuthorizationContext> yetkilendirme kararları vermek için.  
  
 Varsayılan olarak, yetkilendirme kararları yapılan <xref:System.ServiceModel.ServiceAuthorizationManager> sınıfı; ancak bu kararlar özel Yetkilendirme Yöneticisi oluşturma tarafından geçersiz kılınabilir. Özel Yetkilendirme Yöneticisi oluşturma için türeyen bir sınıf oluşturun <xref:System.ServiceModel.ServiceAuthorizationManager> ve uygulamanıza <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> yöntemi. Yetkilendirme kararları yapılma <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> döndürür yöntemi `true` zaman erişimi verilir ve `false` zaman erişim reddedildi.  
  
 İleti gövdesinin içeriğine yetkilendirme kararı bağlıdır kullanırsanız <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemi.  
  
 Böylece yetkilendirme kararı ileti gövdesi erişimi gerektirmez performans sorunları nedeniyle Mümkünse, uygulamanızın yeniden tasarlamanız.  
  
 Bir hizmet için özel Yetkilendirme Yöneticisi'ni kaydı, kod veya yapılandırma yapılabilir.  
  
### <a name="to-create-a-custom-authorization-manager"></a>Özel Yetkilendirme Yöneticisi oluşturmak için  
  
1.  Öğesinden bir sınıf türetin <xref:System.ServiceModel.ServiceAuthorizationManager> sınıfı.  
  
     [!code-csharp[c_CustomAuthMgr#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#5)]
     [!code-vb[c_CustomAuthMgr#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#5)]  
  
2.  Geçersiz kılma <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> yöntemi.  
  
     Kullanım <xref:System.ServiceModel.OperationContext> için geçirilen <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> yetkilendirme kararları için yöntem.  
  
     Aşağıdaki kod örneğinde <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> özel talep bulmak için yöntem `http://www.contoso.com/claims/allowedoperation` bir yetkilendirme kararı almak için.  
  
     [!code-csharp[c_CustomAuthMgr#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#6)]
     [!code-vb[c_CustomAuthMgr#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#6)]  
  
### <a name="to-register-a-custom-authorization-manager-using-code"></a>Kod kullanarak bir özel Yetkilendirme Yöneticisi'ni kaydetmek için  
  
1.  Özel yetkilendirme örneği Yöneticisi oluşturabilir ve atayabilirsiniz <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> özelliği.  
  
     <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> Kullanılarak erişilebilir <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> özelliği.  
  
     Aşağıdaki kod örneği yazmaçlar `MyServiceAuthorizationManager` özel Yetkilendirme Yöneticisi.  
  
     [!code-csharp[c_CustomAuthMgr#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#4)]
     [!code-vb[c_CustomAuthMgr#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#4)]  
  
### <a name="to-register-a-custom-authorization-manager-using-configuration"></a>Yapılandırması'nı kullanarak bir özel Yetkilendirme Yöneticisi'ni kaydetmek için  
  
1.  Hizmeti için yapılandırma dosyasını açın.  
  
2.  Ekleme bir [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) için [ \<davranışları >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md).  
  
     İçin [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md), ekleme bir `serviceAuthorizationManagerType` özniteliği ve özel Yetkilendirme Yöneticisi'ni temsil eden tür için değerini ayarlayın.  
  
3.  Hizmet ve istemci arasındaki iletişimin güvenliğini sağlar bir bağlaması ekleyin.  
  
     Bu iletişim için eklenen talepleri belirler, seçilen bağlama <xref:System.IdentityModel.Policy.AuthorizationContext>, yetkilendirme kararları vermek için özel Yetkilendirme Yöneticisi'ni kullanır. Sistem tarafından sağlanan bağlamalar hakkında daha fazla ayrıntı için bkz: [System-Provided bağlamaları](../../../../docs/framework/wcf/system-provided-bindings.md).  
  
4.  Bir hizmet uç noktası için davranış ekleyerek ilişkilendirmek bir [ \<hizmet >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) öğesi ve değeri ayarlayın `behaviorConfiguration` özniteliği için name özniteliği değerini [ \<davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) öğesi.  
  
     Hizmet uç noktası yapılandırma hakkında daha fazla bilgi için bkz: [nasıl yapılır: yapılandırmada hizmet uç noktası oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md).  
  
     Aşağıdaki kod örneğinde özel Yetkilendirme Yöneticisi'ni kaydeder `Samples.MyServiceAuthorizationManager`.  
  
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
    >  ServiceAuthorizationManagerType belirttiğinizde, tam olarak nitelenmiş tür adını dize içermesi gerektiğini unutmayın. virgül ve türünün tanımlandığı derleme adını. Derleme adı değiştirmeden bırakırsanız, WCF System.ServiceModel.dll yük türü dener.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde temel bir uygulama ortaya koyar bir <xref:System.ServiceModel.ServiceAuthorizationManager> geçersiz kılma içeren sınıf <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> yöntemi. Örnek kod inceler <xref:System.IdentityModel.Policy.AuthorizationContext> için özel bir talep ve döndürür `true` zaman kaynağı bu özel talep için eşleşen eylem değerinden <xref:System.ServiceModel.OperationContext>. Daha eksiksiz bir uygulama için bir <xref:System.ServiceModel.ServiceAuthorizationManager> sınıfı için bkz: [yetkilendirme ilkesi](../../../../docs/framework/wcf/samples/authorization-policy.md).  
  
 [!code-csharp[c_CustomAuthMgr#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#2)]
 [!code-vb[c_CustomAuthMgr#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
 [Yetkilendirme İlkesi](../../../../docs/framework/wcf/samples/authorization-policy.md)  
 [Yetkilendirme İlkesi](../../../../docs/framework/wcf/samples/authorization-policy.md)
