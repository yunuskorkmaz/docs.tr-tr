---
title: 'Nasıl yapılır: Windows Communication Foundation Güvenlik Olaylarını Denetleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], auditing events
ms.assetid: e71e9587-3336-46a2-9a9e-d72a1743ecec
ms.openlocfilehash: 186dd4a7fc2beae848e5cbd167a204352ee6ed4e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601302"
---
# <a name="how-to-audit-windows-communication-foundation-security-events"></a>Nasıl yapılır: Windows Communication Foundation Güvenlik Olaylarını Denetleme
Windows Communication Foundation (WCF), Windows Olay Görüntüleyicisi kullanılarak görüntülenebilen Windows olay günlüğü 'nde güvenlik olaylarını günlüğe kaydetmenize izin verir. Bu konuda, güvenlik olaylarını günlüğe kaydetmeleri için bir uygulamanın nasıl ayarlanacağı açıklanmaktadır. WCF denetimi hakkında daha fazla bilgi için bkz. [Denetim](auditing-security-events.md).  
  
### <a name="to-audit-security-events-in-code"></a>Koddaki güvenlik olaylarını denetlemek için  
  
1. Denetim günlüğü konumunu belirtin. Bunu yapmak için, <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> <xref:System.ServiceModel.AuditLogLocation> aşağıdaki kodda gösterildiği gibi, sınıfının özelliğini sabit listesi değerlerinden birine ayarlayın.  
  
     [!code-csharp[AuditingSecurityEvents#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#2)]
     [!code-vb[AuditingSecurityEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#2)]  
  
     <xref:System.ServiceModel.AuditLogLocation>Numaralandırmada üç değer vardır: `Application` , `Security` , veya `Default` . Değer Olay Görüntüleyicisi, güvenlik günlüğü veya uygulama günlüğü ' nde görünür olan günlüklardan birini belirtir. `Default`Bu değeri kullanırsanız, gerçek günlük uygulamanın üzerinde çalıştığı işletim sistemine bağlıdır. Denetim etkinse ve günlük konumu belirtilmemişse, varsayılan olarak `Security` güvenlik günlüğüne yazmayı destekleyen platformların günlüğü olur; aksi takdirde, `Application` günlüğe yazılır. Yalnızca Windows Server 2003 ve Windows Vista, varsayılan olarak güvenlik günlüğüne yazmayı destekler.  
  
2. Denetlenecek olay türlerini ayarlayın. Hizmet düzeyi olaylarını veya ileti düzeyi yetkilendirme olaylarını eşzamanlı olarak denetleyebilirsiniz. Bunu yapmak için, <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> <xref:System.ServiceModel.AuditLevel> aşağıdaki kodda gösterildiği gibi, özelliği veya özelliğini sabit listesi değerlerinden birine ayarlayın.  
  
     [!code-csharp[AuditingSecurityEvents#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#3)]
     [!code-vb[AuditingSecurityEvents#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#3)]  
  
3. Günlük denetim olayları ile ilgili olarak uygulamanın başarısızlıklarını bastırıp göstermeyeceğinizi belirtin. Özelliği, <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> `true` `false` aşağıdaki kodda gösterildiği gibi ya da olarak ayarlayın.  
  
     [!code-csharp[AuditingSecurityEvents#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#4)]
     [!code-vb[AuditingSecurityEvents#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#4)]  
  
     Varsayılan `SuppressAuditFailure` özellik `true` , denetim hatasının uygulamayı etkilememesi için. Aksi takdirde, bir özel durum oluşturulur. Başarılı bir denetim için, ayrıntılı bir izleme yazılır. Denetlenecek herhangi bir hata için, izleme hata düzeyine yazılır.  
  
4. <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>Öğesinin açıklamasında bulunan davranışlar koleksiyonundan varolanı silin <xref:System.ServiceModel.ServiceHost> . Davranış koleksiyonuna özelliği tarafından erişilir <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> , buna karşılık <xref:System.ServiceModel.ServiceHostBase.Description%2A> özelliğinden erişilir. Ardından, <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> aşağıdaki kodda gösterildiği gibi yeni ' yi aynı koleksiyona ekleyin.  
  
     [!code-csharp[AuditingSecurityEvents#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#5)]
     [!code-vb[AuditingSecurityEvents#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#5)]  
  
### <a name="to-set-up-auditing-in-configuration"></a>Yapılandırmada denetim ayarlamak için  
  
1. Yapılandırmada denetim ayarlamak için, [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) Web. config dosyasının bölümüne bir öğesi ekleyin. Ardından bir [\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md) öğesi ekleyin ve aşağıdaki örnekte gösterildiği gibi çeşitli öznitelikleri ayarlayın.  
  
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
 Aşağıdaki kod, sınıfının bir örneğini oluşturur <xref:System.ServiceModel.ServiceHost> ve davranışları koleksiyonuna yeni bir ekler <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> .  
  
 [!code-csharp[AuditingSecurityEvents#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#1)]
 [!code-vb[AuditingSecurityEvents#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#1)]  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A>Özelliği olarak ayarlamak `true` , güvenlik denetimleri oluşturma başarısızlığını göstermez (olarak ayarlanırsa `false` , bir özel durum oluşturulur). Ancak, aşağıdaki Windows **yerel güvenlik ayarı** özelliğini etkinleştirirseniz, denetim olayları oluşturma hatası Windows 'un hemen kapatılmasına neden olur:  
  
 **Denetim: Güvenlik denetimleri günlüğe alınamıyorsa sistemi hemen kapat**  
  
 Özelliği ayarlamak için **yerel güvenlik ayarları** iletişim kutusunu açın. **Güvenlik ayarları**altında **Yerel ilkeler**' e tıklayın. Ardından **güvenlik seçenekleri**' ne tıklayın.  
  
 <xref:System.ServiceModel.AuditLogLocation>Özelliği olarak ayarlandıysa <xref:System.ServiceModel.AuditLogLocation.Security> ve **Denetim nesne erişimi** **yerel güvenlik Ilkesinde**ayarlanmamışsa, denetim olayları güvenlik günlüğüne yazılmaz. Hiçbir hata döndürülmediğini, ancak denetim girişlerinin güvenlik günlüğüne yazılmadığını unutmayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A>
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- <xref:System.ServiceModel.AuditLogLocation>
- [Denetim](auditing-security-events.md)
