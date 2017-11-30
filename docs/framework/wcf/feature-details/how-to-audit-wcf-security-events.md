---
title: "Nasıl yapılır: Windows Communication Foundation Güvenlik Olaylarını Denetleme"
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
helpviewer_keywords: security [WCF], auditing events
ms.assetid: e71e9587-3336-46a2-9a9e-d72a1743ecec
caps.latest.revision: "19"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 67fca1af6a9e1fdd35051e8b289679677a0abd6b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-audit-windows-communication-foundation-security-events"></a>Nasıl yapılır: Windows Communication Foundation Güvenlik Olaylarını Denetleme
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]güvenlik olaylarını Windows olay Windows Olay Görüntüleyicisi'ni kullanarak görüntülenebilen, günlüğüne olanak sağlar. Bu konuda, güvenlik olayları günlüğe kaydeder, böylece uygulama ayarlama açıklanmaktadır. [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] denetleme, bkz: [denetim](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
### <a name="to-audit-security-events-in-code"></a>Kodda güvenlik olaylarını denetleme  
  
1.  Denetim günlüğü konumu belirtin. Bunu yapmak için ayarlayın <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> özelliği <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> birine sınıfı <xref:System.ServiceModel.AuditLogLocation> aşağıdaki kodda gösterildiği gibi numaralandırma değerleri.  
  
     [!code-csharp[AuditingSecurityEvents#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#2)]
     [!code-vb[AuditingSecurityEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#2)]  
  
     <xref:System.ServiceModel.AuditLogLocation> Numaralandırması üç değeri vardır: `Application`, `Security`, veya `Default`. Değer günlükleri Olay Görüntüleyicisi'nde görünür birini ya da güvenlik günlüğü veya Uygulama günlüğünü belirtir. Kullanırsanız `Default` değeri, gerçek günlük bağlı üzerinde uygulamayı çalıştırdığınız işletim sistemi. Denetim etkin ve günlük konumu belirtilmezse, varsayılan ise `Security` günlük yazma destekleyen platformlar için güvenlik günlüğü için; Aksi takdirde, Yazar `Application` günlük. Yalnızca [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wv](../../../../includes/wv-md.md)] güvenlik günlüğüne yazma varsayılan olarak destekler.  
  
2.  Denetlenecek olayların tiplerini ayarlayın. Hizmet düzeyi olayları veya ileti düzeyi yetkilendirme olayları aynı anda denetleyebilirsiniz. Bunu yapmak için ayarlayın <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> özelliği veya <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> özelliğini birine <xref:System.ServiceModel.AuditLevel> aşağıdaki kodda gösterildiği gibi numaralandırma değerleri.  
  
     [!code-csharp[AuditingSecurityEvents#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#3)]
     [!code-vb[AuditingSecurityEvents#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#3)]  
  
3.  Uygulama günlüğü denetim olaylarını ilgili hataları kullanıma sunmak belirtin. Ayarlama <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> ya da özellik `true` veya `false`aşağıdaki kodda gösterildiği gibi.  
  
     [!code-csharp[AuditingSecurityEvents#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#4)]
     [!code-vb[AuditingSecurityEvents#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#4)]  
  
     Varsayılan `SuppressAuditFailure` özelliği `true`, böylece denetim hatası uygulamayı etkilemez. Aksi takdirde, bir özel durum oluşturulur. Başarılı bir denetim için ayrıntılı izleme yazılır. Denetlemek herhangi bir hata için izleme ve hata düzeyde yazılır.  
  
4.  Varolan silme <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> açıklamasına bulunan davranışları koleksiyonundan bir <xref:System.ServiceModel.ServiceHost>. Davranış koleksiyon tarafından erişilen <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> buna karşılık gelen erişilen özellik <xref:System.ServiceModel.ServiceHostBase.Description%2A> özelliği. Yeni Ekle <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> aşağıdaki kodda gösterildiği gibi aynı koleksiyona.  
  
     [!code-csharp[AuditingSecurityEvents#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#5)]
     [!code-vb[AuditingSecurityEvents#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#5)]  
  
### <a name="to-set-up-auditing-in-configuration"></a>Yapılandırmada denetimini ayarlamak için  
  
1.  Yapılandırmada denetimini ayarlamak için ekleme bir [ \<davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) öğesine [ \<davranışları >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) web.config dosyasının bölümü. Ardından ekleyin bir [ \<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) öğesi ve çeşitli öznitelikler, aşağıdaki örnekte gösterildiği gibi kümesi.  
  
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
  
2.  Aşağıdaki örnekte gösterildiği gibi hizmet için davranış belirtmeniz gerekir.  
  
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
 Aşağıdaki kod örneği oluşturur <xref:System.ServiceModel.ServiceHost> sınıfı ve yeni bir ekler <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> davranışları kendi koleksiyonuna.  
  
 [!code-csharp[AuditingSecurityEvents#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#1)]
 [!code-vb[AuditingSecurityEvents#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#1)]  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Ayarı <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> özelliğine `true`, güvenlik denetimleri üretmek için herhangi bir hata bastırır (varsa kümesine `false`, bir özel durum). Ancak, aşağıdaki Windows etkinleştirirseniz **yerel güvenlik ayarları**özelliği, denetim olayları oluşturmak için bir hata neden olacak hemen kapatmak Windows:  
  
 **Denetleme: Alınamazsa sistemi hemen güvenlik denetimleri oturum kapatma**  
  
 Özellik set yapılmaya açmak **yerel güvenlik ayarları** iletişim kutusu. Altında **güvenlik ayarları**, tıklatın **yerel ilkeler**. Ardından **güvenlik seçenekleri**.  
  
 Varsa <xref:System.ServiceModel.AuditLogLocation> özelliği ayarlanmış <xref:System.ServiceModel.AuditLogLocation.Security> ve **Nesne erişimini denetle** ayarlanmadı **yerel güvenlik ilkesi**, denetim olaylarını güvenlik günlüğüne değil yazılır. Hiçbir hata döndürülür, ancak denetim girişlerini güvenlik günlüğü'ne yazılmaz unutmayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>  
 <xref:System.ServiceModel.AuditLogLocation>  
 [Denetleme](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
