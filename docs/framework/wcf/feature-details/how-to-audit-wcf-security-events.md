---
title: "Nasıl yapılır: Windows Communication Foundation Güvenlik Olaylarını Denetleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], auditing events
ms.assetid: e71e9587-3336-46a2-9a9e-d72a1743ecec
caps.latest.revision: 
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: d3456eb374add7768fa6f2d01bc1b7b610c9577e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-audit-windows-communication-foundation-security-events"></a><span data-ttu-id="20507-102">Nasıl yapılır: Windows Communication Foundation Güvenlik Olaylarını Denetleme</span><span class="sxs-lookup"><span data-stu-id="20507-102">How to: Audit Windows Communication Foundation Security Events</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="20507-103">güvenlik olaylarını Windows olay Windows Olay Görüntüleyicisi'ni kullanarak görüntülenebilen, günlüğüne olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="20507-103"> allows you to log security events to the Windows event log, which can be viewed using the Windows Event Viewer.</span></span> <span data-ttu-id="20507-104">Bu konuda, güvenlik olayları günlüğe kaydeder, böylece uygulama ayarlama açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="20507-104">This topic explains how to set up an application so that it logs security events.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="20507-105">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] denetleme, bkz: [denetim](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).</span><span class="sxs-lookup"><span data-stu-id="20507-105"> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] auditing, see [Auditing](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).</span></span>  
  
### <a name="to-audit-security-events-in-code"></a><span data-ttu-id="20507-106">Kodda güvenlik olaylarını denetleme</span><span class="sxs-lookup"><span data-stu-id="20507-106">To audit security events in code</span></span>  
  
1.  <span data-ttu-id="20507-107">Denetim günlüğü konumu belirtin.</span><span class="sxs-lookup"><span data-stu-id="20507-107">Specify the audit log location.</span></span> <span data-ttu-id="20507-108">Bunu yapmak için ayarlayın <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> özelliği <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> birine sınıfı <xref:System.ServiceModel.AuditLogLocation> aşağıdaki kodda gösterildiği gibi numaralandırma değerleri.</span><span class="sxs-lookup"><span data-stu-id="20507-108">To do this, set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> property of the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> class to one of the <xref:System.ServiceModel.AuditLogLocation> enumeration values, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#2)]
     [!code-vb[AuditingSecurityEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#2)]  
  
     <span data-ttu-id="20507-109"><xref:System.ServiceModel.AuditLogLocation> Numaralandırması üç değeri vardır: `Application`, `Security`, veya `Default`.</span><span class="sxs-lookup"><span data-stu-id="20507-109">The <xref:System.ServiceModel.AuditLogLocation> enumeration has three values: `Application`, `Security`, or `Default`.</span></span> <span data-ttu-id="20507-110">Değer günlükleri Olay Görüntüleyicisi'nde görünür birini ya da güvenlik günlüğü veya Uygulama günlüğünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="20507-110">The value specifies one of the logs visible in the Event Viewer, either the Security log or the Application log.</span></span> <span data-ttu-id="20507-111">Kullanırsanız `Default` değeri, gerçek günlük bağlı üzerinde uygulamayı çalıştırdığınız işletim sistemi.</span><span class="sxs-lookup"><span data-stu-id="20507-111">If you use the `Default` value, the actual log will depend on the operating system the application is running on.</span></span> <span data-ttu-id="20507-112">Denetim etkin ve günlük konumu belirtilmezse, varsayılan ise `Security` günlük yazma destekleyen platformlar için güvenlik günlüğü için; Aksi takdirde, Yazar `Application` günlük.</span><span class="sxs-lookup"><span data-stu-id="20507-112">If auditing is enabled and the log location is not specified, the default is the `Security` log for platforms that support writing to the Security log; otherwise, it will write to the `Application` log.</span></span> <span data-ttu-id="20507-113">Yalnızca [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wv](../../../../includes/wv-md.md)] güvenlik günlüğüne yazma varsayılan olarak destekler.</span><span class="sxs-lookup"><span data-stu-id="20507-113">Only [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] and [!INCLUDE[wv](../../../../includes/wv-md.md)] support writing to the Security log by default.</span></span>  
  
2.  <span data-ttu-id="20507-114">Denetlenecek olayların tiplerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="20507-114">Set up the types of events to audit.</span></span> <span data-ttu-id="20507-115">Hizmet düzeyi olayları veya ileti düzeyi yetkilendirme olayları aynı anda denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="20507-115">You can simultaneously audit service-level events or message-level authorization events.</span></span> <span data-ttu-id="20507-116">Bunu yapmak için ayarlayın <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> özelliği veya <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> özelliğini birine <xref:System.ServiceModel.AuditLevel> aşağıdaki kodda gösterildiği gibi numaralandırma değerleri.</span><span class="sxs-lookup"><span data-stu-id="20507-116">To do this, set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> property or the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> property to one of the <xref:System.ServiceModel.AuditLevel> enumeration values, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#3)]
     [!code-vb[AuditingSecurityEvents#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#3)]  
  
3.  <span data-ttu-id="20507-117">Uygulama günlüğü denetim olaylarını ilgili hataları kullanıma sunmak belirtin.</span><span class="sxs-lookup"><span data-stu-id="20507-117">Specify whether to suppress or expose failures to the application regarding log audit events.</span></span> <span data-ttu-id="20507-118">Ayarlama <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> ya da özellik `true` veya `false`aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="20507-118">Set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> property to either `true` or `false`, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#4)]
     [!code-vb[AuditingSecurityEvents#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#4)]  
  
     <span data-ttu-id="20507-119">Varsayılan `SuppressAuditFailure` özelliği `true`, böylece denetim hatası uygulamayı etkilemez.</span><span class="sxs-lookup"><span data-stu-id="20507-119">The default `SuppressAuditFailure` property is `true`, so that the failure to audit does not affect the application.</span></span> <span data-ttu-id="20507-120">Aksi takdirde, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="20507-120">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="20507-121">Başarılı bir denetim için ayrıntılı izleme yazılır.</span><span class="sxs-lookup"><span data-stu-id="20507-121">For any successful audit, a verbose trace is written.</span></span> <span data-ttu-id="20507-122">Denetlemek herhangi bir hata için izleme ve hata düzeyde yazılır.</span><span class="sxs-lookup"><span data-stu-id="20507-122">For any failure to audit, the trace is written at the Error level.</span></span>  
  
4.  <span data-ttu-id="20507-123">Varolan silme <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> açıklamasına bulunan davranışları koleksiyonundan bir <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="20507-123">Delete the existing <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> from the collection of behaviors found in the description of a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="20507-124">Davranış koleksiyon tarafından erişilen <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> buna karşılık gelen erişilen özellik <xref:System.ServiceModel.ServiceHostBase.Description%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="20507-124">The behavior collection is accessed by the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> property, which in turn is accessed from the <xref:System.ServiceModel.ServiceHostBase.Description%2A> property.</span></span> <span data-ttu-id="20507-125">Yeni Ekle <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> aşağıdaki kodda gösterildiği gibi aynı koleksiyona.</span><span class="sxs-lookup"><span data-stu-id="20507-125">Then add the new <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to the same collection, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#5)]
     [!code-vb[AuditingSecurityEvents#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#5)]  
  
### <a name="to-set-up-auditing-in-configuration"></a><span data-ttu-id="20507-126">Yapılandırmada denetimini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="20507-126">To set up auditing in configuration</span></span>  
  
1.  <span data-ttu-id="20507-127">Yapılandırmada denetimini ayarlamak için ekleme bir [ \<davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) öğesine [ \<davranışları >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) web.config dosyasının bölümü.</span><span class="sxs-lookup"><span data-stu-id="20507-127">To set up auditing in configuration, add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) section of the web.config file.</span></span> <span data-ttu-id="20507-128">Ardından ekleyin bir [ \<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) öğesi ve çeşitli öznitelikler, aşağıdaki örnekte gösterildiği gibi kümesi.</span><span class="sxs-lookup"><span data-stu-id="20507-128">Then add a [\<serviceSecurityAudit>](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) element and set the various attributes, as shown in the following example.</span></span>  
  
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
  
2.  <span data-ttu-id="20507-129">Aşağıdaki örnekte gösterildiği gibi hizmet için davranış belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="20507-129">You must specify the behavior for the service, as shown in the following example.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="20507-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="20507-130">Example</span></span>  
 <span data-ttu-id="20507-131">Aşağıdaki kod örneği oluşturur <xref:System.ServiceModel.ServiceHost> sınıfı ve yeni bir ekler <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> davranışları kendi koleksiyonuna.</span><span class="sxs-lookup"><span data-stu-id="20507-131">The following code creates an instance of the <xref:System.ServiceModel.ServiceHost> class and adds a new <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to its collection of behaviors.</span></span>  
  
 [!code-csharp[AuditingSecurityEvents#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#1)]
 [!code-vb[AuditingSecurityEvents#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#1)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="20507-132">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="20507-132">.NET Framework Security</span></span>  
 <span data-ttu-id="20507-133">Ayarı <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> özelliğine `true`, güvenlik denetimleri üretmek için herhangi bir hata bastırır (varsa kümesine `false`, bir özel durum).</span><span class="sxs-lookup"><span data-stu-id="20507-133">Setting the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> property to `true`, suppresses any failure to generate security audits (if set to `false`, an exception is thrown).</span></span> <span data-ttu-id="20507-134">Ancak, aşağıdaki Windows etkinleştirirseniz **yerel güvenlik ayarları**özelliği, denetim olayları oluşturmak için bir hata neden olacak hemen kapatmak Windows:</span><span class="sxs-lookup"><span data-stu-id="20507-134">However, if you enable the following Windows **Local Security Setting**property, a failure to generate audit events will cause Windows to shut down immediately:</span></span>  
  
 <span data-ttu-id="20507-135">**Denetleme: Alınamazsa sistemi hemen güvenlik denetimleri oturum kapatma**</span><span class="sxs-lookup"><span data-stu-id="20507-135">**Audit: Shut down system immediately if unable to log security audits**</span></span>  
  
 <span data-ttu-id="20507-136">Özellik set yapılmaya açmak **yerel güvenlik ayarları** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="20507-136">To set the property, open the **Local Security Settings** dialog box.</span></span> <span data-ttu-id="20507-137">Altında **güvenlik ayarları**, tıklatın **yerel ilkeler**.</span><span class="sxs-lookup"><span data-stu-id="20507-137">Under **Security Settings**, click **Local Policies**.</span></span> <span data-ttu-id="20507-138">Ardından **güvenlik seçenekleri**.</span><span class="sxs-lookup"><span data-stu-id="20507-138">Then click **Security Options**.</span></span>  
  
 <span data-ttu-id="20507-139">Varsa <xref:System.ServiceModel.AuditLogLocation> özelliği ayarlanmış <xref:System.ServiceModel.AuditLogLocation.Security> ve **Nesne erişimini denetle** ayarlanmadı **yerel güvenlik ilkesi**, denetim olaylarını güvenlik günlüğüne değil yazılır.</span><span class="sxs-lookup"><span data-stu-id="20507-139">If the <xref:System.ServiceModel.AuditLogLocation> property is set to <xref:System.ServiceModel.AuditLogLocation.Security> and **Audit Object Access** is not set in the **Local Security Policy**, audit events will not be written to the Security log.</span></span> <span data-ttu-id="20507-140">Hiçbir hata döndürülür, ancak denetim girişlerini güvenlik günlüğü'ne yazılmaz unutmayın.</span><span class="sxs-lookup"><span data-stu-id="20507-140">Note that no failure is returned, but audit entries are not written to the Security log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20507-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="20507-141">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>  
 <xref:System.ServiceModel.AuditLogLocation>  
 [<span data-ttu-id="20507-142">Denetim</span><span class="sxs-lookup"><span data-stu-id="20507-142">Auditing</span></span>](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
