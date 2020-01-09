---
title: 'Nasıl yapılır: Windows Communication Foundation Güvenlik Olaylarını Denetleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], auditing events
ms.assetid: e71e9587-3336-46a2-9a9e-d72a1743ecec
ms.openlocfilehash: 7071aaf88346ee217226632501ebd6c82cfc1cb8
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346752"
---
# <a name="how-to-audit-windows-communication-foundation-security-events"></a>Nasıl yapılır: Windows Communication Foundation Güvenlik Olaylarını Denetleme
Windows Communication Foundation (WCF), Windows Olay Görüntüleyicisi kullanılarak görüntülenebilen Windows olay günlüğü 'nde güvenlik olaylarını günlüğe kaydetmenize izin verir. Bu konuda, güvenlik olaylarını günlüğe kaydetmeleri için bir uygulamanın nasıl ayarlanacağı açıklanmaktadır. WCF denetimi hakkında daha fazla bilgi için bkz. [Denetim](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
### <a name="to-audit-security-events-in-code"></a>Koddaki güvenlik olaylarını denetlemek için  
  
1. Denetim günlüğü konumunu belirtin. Bunu yapmak için, aşağıdaki kodda gösterildiği gibi, <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> sınıfının <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> özelliğini <xref:System.ServiceModel.AuditLogLocation> sabit listesi değerlerinden biri olarak ayarlayın.  
  
     [!code-csharp[AuditingSecurityEvents#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#2)]
     [!code-vb[AuditingSecurityEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#2)]  
  
     <xref:System.ServiceModel.AuditLogLocation> numaralandırması üç değere sahiptir: `Application`, `Security`veya `Default`. Değer Olay Görüntüleyicisi, güvenlik günlüğü veya uygulama günlüğü ' nde görünür olan günlüklardan birini belirtir. `Default` değerini kullanırsanız, gerçek günlük uygulamanın üzerinde çalıştığı işletim sistemine bağlıdır. Denetim etkinse ve günlük konumu belirtilmemişse, varsayılan olarak güvenlik günlüğüne yazmayı destekleyen platformlar için `Security` günlüğü vardır; Aksi takdirde, `Application` günlüğüne yazılır. Yalnızca Windows Server 2003 ve Windows Vista, varsayılan olarak güvenlik günlüğüne yazmayı destekler.  
  
2. Denetlenecek olay türlerini ayarlayın. Hizmet düzeyi olaylarını veya ileti düzeyi yetkilendirme olaylarını eşzamanlı olarak denetleyebilirsiniz. Bunu yapmak için, aşağıdaki kodda gösterildiği gibi <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> özelliğini veya <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> özelliğini <xref:System.ServiceModel.AuditLevel> sabit listesi değerlerinden birine ayarlayın.  
  
     [!code-csharp[AuditingSecurityEvents#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#3)]
     [!code-vb[AuditingSecurityEvents#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#3)]  
  
3. Günlük denetim olayları ile ilgili olarak uygulamanın başarısızlıklarını bastırıp göstermeyeceğinizi belirtin. <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> özelliğini aşağıdaki kodda gösterildiği gibi `true` ya da `false`olarak ayarlayın.  
  
     [!code-csharp[AuditingSecurityEvents#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#4)]
     [!code-vb[AuditingSecurityEvents#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#4)]  
  
     Varsayılan `SuppressAuditFailure` özelliği `true`, bu sayede denetim hatası uygulamayı etkilemez. Aksi takdirde, bir özel durum oluşturulur. Başarılı bir denetim için, ayrıntılı bir izleme yazılır. Denetlenecek herhangi bir hata için, izleme hata düzeyine yazılır.  
  
4. Mevcut <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>, bir <xref:System.ServiceModel.ServiceHost>açıklamasında bulunan davranışlar koleksiyonundan silin. Davranış koleksiyonuna, <xref:System.ServiceModel.ServiceHostBase.Description%2A> özelliğinden erişilen <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> özelliği tarafından erişilir. Ardından, aşağıdaki kodda gösterildiği gibi yeni <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> aynı koleksiyona ekleyin.  
  
     [!code-csharp[AuditingSecurityEvents#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#5)]
     [!code-vb[AuditingSecurityEvents#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#5)]  
  
### <a name="to-set-up-auditing-in-configuration"></a>Yapılandırmada denetim ayarlamak için  
  
1. Yapılandırmada denetim ayarlamak için, Web. config dosyasının [\<davranışları >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) bölümüne [\<Behavior >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) öğesi ekleyin. Sonra bir [\<Servicesecurityaudıt >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) öğesi ekleyin ve aşağıdaki örnekte gösterildiği gibi çeşitli öznitelikleri ayarlayın.  
  
    ```xml  
    <behaviors>  
       <behavior name="myAuditBehavior">  
          <serviceSecurityAudit auditLogLocation="Application"  
                suppressAuditFailure="false"   
                serviceAuthorizationAuditLevel="None"   
                messageAuthenticationAuditLevel="SuccessOrFailure" />  
          </behavior>  
    </behaviors>  
    ```  
  
2. Aşağıdaki örnekte gösterildiği gibi, hizmet için davranışı belirtmeniz gerekir.  
  
    ```xml  
    <services>  
        <service type="WCS.Samples.Service.Echo"   
        behaviorConfiguration=" myAuditBehavior">  
           <endpoint address=""  
                    binding="wsHttpBinding"  
                    bindingConfiguration="CertificateDefault"   
                    contract="WCS.Samples.Service.IEcho" />  
        </service>  
    </services>  
    ```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod <xref:System.ServiceModel.ServiceHost> sınıfının bir örneğini oluşturur ve davranışları koleksiyonuna yeni bir <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> ekler.  
  
 [!code-csharp[AuditingSecurityEvents#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#1)]
 [!code-vb[AuditingSecurityEvents#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#1)]  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> özelliğini `true`olarak ayarlama, güvenlik denetimleri üretme başarısızlığını göstermez (`false`olarak ayarlanırsa, bir özel durum oluşturulur). Ancak, aşağıdaki Windows **yerel güvenlik ayarı** özelliğini etkinleştirirseniz, denetim olayları oluşturma hatası Windows 'un hemen kapatılmasına neden olur:  
  
 **Denetim: güvenlik denetimleri günlüğe kaydedilemezse sistemi hemen kapat**  
  
 Özelliği ayarlamak için **yerel güvenlik ayarları** iletişim kutusunu açın. **Güvenlik ayarları**altında **Yerel ilkeler**' e tıklayın. Ardından **güvenlik seçenekleri**' ne tıklayın.  
  
 <xref:System.ServiceModel.AuditLogLocation> Özellik <xref:System.ServiceModel.AuditLogLocation.Security> olarak ayarlanırsa ve **denetim nesnesi erişimi** **yerel güvenlik ilkesinde**ayarlanmamışsa, denetim olayları güvenlik günlüğüne yazılmaz. Hiçbir hata döndürülmediğini, ancak denetim girişlerinin güvenlik günlüğüne yazılmadığını unutmayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A>
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- <xref:System.ServiceModel.AuditLogLocation>
- [Denetim](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
