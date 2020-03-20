---
title: 'Nasıl yapılır: Windows Communication Foundation Güvenlik Olaylarını Denetleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], auditing events
ms.assetid: e71e9587-3336-46a2-9a9e-d72a1743ecec
ms.openlocfilehash: 62d26b24b5d46427c1871fccf48b063c45781beb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185120"
---
# <a name="how-to-audit-windows-communication-foundation-security-events"></a>Nasıl yapılır: Windows Communication Foundation Güvenlik Olaylarını Denetleme
Windows Communication Foundation (WCF), güvenlik olaylarını Windows Olay Görüntüleyicisi kullanılarak görüntülenebilen Windows olay günlüğüne günlüğe kaydetmenizi sağlar. Bu konu, güvenlik olaylarını günlüğe kaydedecek şekilde bir uygulamanın nasıl ayarlanışsüreceğini açıklar. WCF denetimi hakkında daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
  
### <a name="to-audit-security-events-in-code"></a>Güvenlik olaylarını kodda denetlemek için  
  
1. Denetim günlüğü konumunu belirtin. Bunu yapmak için, <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> sınıfın <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> özelliğini aşağıdaki <xref:System.ServiceModel.AuditLogLocation> kodda gösterildiği gibi numaralandırma değerlerinden birine ayarlayın.  
  
     [!code-csharp[AuditingSecurityEvents#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#2)]
     [!code-vb[AuditingSecurityEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#2)]  
  
     Numaralandırmanın <xref:System.ServiceModel.AuditLogLocation> üç değeri `Application`vardır: `Security`, `Default`, veya . Değer, Olay Görüntüleyicisi'nde görünen günlüklerden birini, Güvenlik günlüğü veya Uygulama günlüğünü belirtir. `Default` Değeri kullanırsanız, gerçek günlük uygulamanın çalıştığı işletim sistemine bağlıdır. Denetim etkinleştirilmişse ve günlük konumu belirtilmemişse, varsayılan değer Güvenlik günlüğüne yazmayı destekleyen platformlar için `Security` günlükolur; aksi takdirde, `Application` günlük yazacaktır. Yalnızca Windows Server 2003 ve Windows Vista varsayılan olarak Güvenlik günlüğüne yazmayı destekler.  
  
2. Denetlemek için etkinlik türlerini ayarlayın. Hizmet düzeyi etkinlikleri veya ileti düzeyinde yetkilendirme olaylarını aynı anda denetleyebilirsiniz. Bunu yapmak için, <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> aşağıdaki <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> kodda gösterildiği <xref:System.ServiceModel.AuditLevel> gibi özelliği veya özelliği numaralandırma değerlerinden birine ayarlayın.  
  
     [!code-csharp[AuditingSecurityEvents#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#3)]
     [!code-vb[AuditingSecurityEvents#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#3)]  
  
3. Günlük denetimi olaylarıyla ilgili hataları bastırıp bastırmayyacağınızı veya uygulamada hataları ortaya çıkartıp göstermeyeceğini belirtin. Aşağıdaki <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> kodda `true` gösterildiği `false`gibi özelliği aşağıdaki koddan biri veya  
  
     [!code-csharp[AuditingSecurityEvents#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#4)]
     [!code-vb[AuditingSecurityEvents#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#4)]  
  
     Varsayılan `SuppressAuditFailure` `true`özellik, böylece denetim başarısızlığı uygulamayı etkilemez. Aksi takdirde, bir özel durum oluşturulur. Başarılı bir denetim için ayrıntılı bir izleme yazılır. Herhangi bir denetim hatası için izleme Hata düzeyinde yazılır.  
  
4. Bir <xref:System.ServiceModel.ServiceHost>' <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> nin açıklamasında bulunan davranışlar koleksiyonundan varolan ları silin. Davranış koleksiyonuna, özellikten <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> <xref:System.ServiceModel.ServiceHostBase.Description%2A> erişilen özellik tarafından erişilir. Ardından, aşağıdaki <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> kodda gösterildiği gibi, yeniyi aynı koleksiyona ekleyin.  
  
     [!code-csharp[AuditingSecurityEvents#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#5)]
     [!code-vb[AuditingSecurityEvents#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#5)]  
  
### <a name="to-set-up-auditing-in-configuration"></a>Yapılandırmada denetim kurmak için  
  
1. Yapılandırmada denetim ayarlamak için, web.config dosyasının [ \<>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) bölümüne davranış [ \<>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) öğesi ekleyin. Ardından bir [ \<serviceSecurityAudit>](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) öğesi ekleyin ve aşağıdaki örnekte gösterildiği gibi çeşitli öznitelikleri ayarlayın.  
  
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
  
2. Aşağıdaki örnekte gösterildiği gibi hizmetin davranışını belirtmeniz gerekir.  
  
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
 Aşağıdaki kod sınıfın bir örneğini <xref:System.ServiceModel.ServiceHost> oluşturur ve <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> davranış koleksiyonuna yeni bir yeni ekler.  
  
 [!code-csharp[AuditingSecurityEvents#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#1)]
 [!code-vb[AuditingSecurityEvents#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#1)]  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> Özelliği `true`ayarlamak, güvenlik denetimleri oluşturmadaki tüm hataları bastırır `false`(ayarlanmışsa, bir özel durum atılır). Ancak, aşağıdaki Windows **Yerel Güvenlik Ayarı** özelliğini etkinleştiriseniz, denetim olayları nın oluşturulmasında başarısız olmak Windows'un hemen kapanmasına neden olur:  
  
 **Denetim: Güvenlik denetimleri günlüğe alınamıyorsa sistemi hemen kapat**  
  
 Özelliği ayarlamak için **Yerel Güvenlik Ayarları** iletişim kutusunu açın. **Güvenlik Ayarları**altında, **Yerel İlkeler'i**tıklatın. Ardından **Güvenlik Seçenekleri'ni**tıklatın.  
  
 Özellik ayarlanırsa <xref:System.ServiceModel.AuditLogLocation.Security> ve **Denetim Nesnesi Erişimi** **Yerel Güvenlik İlkesi'nde**ayarlanmazsa, denetim olayları Güvenlik günlüğüne yazılmaz. <xref:System.ServiceModel.AuditLogLocation> Hata döndürülmediğini, ancak denetim girişlerinin Güvenlik günlüğüne yazıldığını unutmayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A>
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- <xref:System.ServiceModel.AuditLogLocation>
- [Denetim](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
