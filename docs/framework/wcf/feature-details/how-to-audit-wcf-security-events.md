---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: denetim Windows Communication Foundation güvenlik olayları'
title: 'Nasıl yapılır: Windows Communication Foundation Güvenlik Olaylarını Denetleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], auditing events
ms.assetid: e71e9587-3336-46a2-9a9e-d72a1743ecec
ms.openlocfilehash: b9cd258f51dbc726108fef0bbf173c7ee26c1d0f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780212"
---
# <a name="how-to-audit-windows-communication-foundation-security-events"></a><span data-ttu-id="bfaf5-103">Nasıl yapılır: Windows Communication Foundation Güvenlik Olaylarını Denetleme</span><span class="sxs-lookup"><span data-stu-id="bfaf5-103">How to: Audit Windows Communication Foundation Security Events</span></span>

<span data-ttu-id="bfaf5-104">Windows Communication Foundation (WCF), Windows Olay Görüntüleyicisi kullanılarak görüntülenebilen Windows olay günlüğü 'nde güvenlik olaylarını günlüğe kaydetmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="bfaf5-104">Windows Communication Foundation (WCF) allows you to log security events to the Windows event log, which can be viewed using the Windows Event Viewer.</span></span> <span data-ttu-id="bfaf5-105">Bu konuda, güvenlik olaylarını günlüğe kaydetmeleri için bir uygulamanın nasıl ayarlanacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bfaf5-105">This topic explains how to set up an application so that it logs security events.</span></span> <span data-ttu-id="bfaf5-106">WCF denetimi hakkında daha fazla bilgi için bkz. [Denetim](auditing-security-events.md).</span><span class="sxs-lookup"><span data-stu-id="bfaf5-106">For more information about WCF auditing, see [Auditing](auditing-security-events.md).</span></span>  
  
### <a name="to-audit-security-events-in-code"></a><span data-ttu-id="bfaf5-107">Koddaki güvenlik olaylarını denetlemek için</span><span class="sxs-lookup"><span data-stu-id="bfaf5-107">To audit security events in code</span></span>  
  
1. <span data-ttu-id="bfaf5-108">Denetim günlüğü konumunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="bfaf5-108">Specify the audit log location.</span></span> <span data-ttu-id="bfaf5-109">Bunu yapmak için, <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> <xref:System.ServiceModel.AuditLogLocation> aşağıdaki kodda gösterildiği gibi, sınıfının özelliğini sabit listesi değerlerinden birine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bfaf5-109">To do this, set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> property of the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> class to one of the <xref:System.ServiceModel.AuditLogLocation> enumeration values, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#2)]
     [!code-vb[AuditingSecurityEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#2)]  
  
     <span data-ttu-id="bfaf5-110"><xref:System.ServiceModel.AuditLogLocation>Numaralandırmada üç değer vardır: `Application` , `Security` , veya `Default` .</span><span class="sxs-lookup"><span data-stu-id="bfaf5-110">The <xref:System.ServiceModel.AuditLogLocation> enumeration has three values: `Application`, `Security`, or `Default`.</span></span> <span data-ttu-id="bfaf5-111">Değer Olay Görüntüleyicisi, güvenlik günlüğü veya uygulama günlüğü ' nde görünür olan günlüklardan birini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bfaf5-111">The value specifies one of the logs visible in the Event Viewer, either the Security log or the Application log.</span></span> <span data-ttu-id="bfaf5-112">`Default`Bu değeri kullanırsanız, gerçek günlük uygulamanın üzerinde çalıştığı işletim sistemine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="bfaf5-112">If you use the `Default` value, the actual log will depend on the operating system the application is running on.</span></span> <span data-ttu-id="bfaf5-113">Denetim etkinse ve günlük konumu belirtilmemişse, varsayılan olarak `Security` güvenlik günlüğüne yazmayı destekleyen platformların günlüğü olur; aksi takdirde, `Application` günlüğe yazılır.</span><span class="sxs-lookup"><span data-stu-id="bfaf5-113">If auditing is enabled and the log location is not specified, the default is the `Security` log for platforms that support writing to the Security log; otherwise, it will write to the `Application` log.</span></span> <span data-ttu-id="bfaf5-114">Yalnızca Windows Server 2003 ve Windows Vista, varsayılan olarak güvenlik günlüğüne yazmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="bfaf5-114">Only Windows Server 2003 and Windows Vista support writing to the Security log by default.</span></span>  
  
2. <span data-ttu-id="bfaf5-115">Denetlenecek olay türlerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bfaf5-115">Set up the types of events to audit.</span></span> <span data-ttu-id="bfaf5-116">Hizmet düzeyi olaylarını veya ileti düzeyi yetkilendirme olaylarını eşzamanlı olarak denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bfaf5-116">You can simultaneously audit service-level events or message-level authorization events.</span></span> <span data-ttu-id="bfaf5-117">Bunu yapmak için, <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> <xref:System.ServiceModel.AuditLevel> aşağıdaki kodda gösterildiği gibi, özelliği veya özelliğini sabit listesi değerlerinden birine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bfaf5-117">To do this, set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> property or the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> property to one of the <xref:System.ServiceModel.AuditLevel> enumeration values, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#3)]
     [!code-vb[AuditingSecurityEvents#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#3)]  
  
3. <span data-ttu-id="bfaf5-118">Günlük denetim olayları ile ilgili olarak uygulamanın başarısızlıklarını bastırıp göstermeyeceğinizi belirtin.</span><span class="sxs-lookup"><span data-stu-id="bfaf5-118">Specify whether to suppress or expose failures to the application regarding log audit events.</span></span> <span data-ttu-id="bfaf5-119">Özelliği, <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> `true` `false` aşağıdaki kodda gösterildiği gibi ya da olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bfaf5-119">Set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> property to either `true` or `false`, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#4)]
     [!code-vb[AuditingSecurityEvents#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#4)]  
  
     <span data-ttu-id="bfaf5-120">Varsayılan `SuppressAuditFailure` özellik `true` , denetim hatasının uygulamayı etkilememesi için.</span><span class="sxs-lookup"><span data-stu-id="bfaf5-120">The default `SuppressAuditFailure` property is `true`, so that the failure to audit does not affect the application.</span></span> <span data-ttu-id="bfaf5-121">Aksi takdirde, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="bfaf5-121">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="bfaf5-122">Başarılı bir denetim için, ayrıntılı bir izleme yazılır.</span><span class="sxs-lookup"><span data-stu-id="bfaf5-122">For any successful audit, a verbose trace is written.</span></span> <span data-ttu-id="bfaf5-123">Denetlenecek herhangi bir hata için, izleme hata düzeyine yazılır.</span><span class="sxs-lookup"><span data-stu-id="bfaf5-123">For any failure to audit, the trace is written at the Error level.</span></span>  
  
4. <span data-ttu-id="bfaf5-124"><xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>Öğesinin açıklamasında bulunan davranışlar koleksiyonundan varolanı silin <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="bfaf5-124">Delete the existing <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> from the collection of behaviors found in the description of a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="bfaf5-125">Davranış koleksiyonuna özelliği tarafından erişilir <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> , buna karşılık <xref:System.ServiceModel.ServiceHostBase.Description%2A> özelliğinden erişilir.</span><span class="sxs-lookup"><span data-stu-id="bfaf5-125">The behavior collection is accessed by the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> property, which in turn is accessed from the <xref:System.ServiceModel.ServiceHostBase.Description%2A> property.</span></span> <span data-ttu-id="bfaf5-126">Ardından, <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> aşağıdaki kodda gösterildiği gibi yeni ' yi aynı koleksiyona ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bfaf5-126">Then add the new <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to the same collection, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#5)]
     [!code-vb[AuditingSecurityEvents#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#5)]  
  
### <a name="to-set-up-auditing-in-configuration"></a><span data-ttu-id="bfaf5-127">Yapılandırmada denetim ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="bfaf5-127">To set up auditing in configuration</span></span>  
  
1. <span data-ttu-id="bfaf5-128">Yapılandırmada denetim ayarlamak için [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) web.config dosyanın bölümüne bir öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bfaf5-128">To set up auditing in configuration, add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element to the [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) section of the web.config file.</span></span> <span data-ttu-id="bfaf5-129">Ardından bir [\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md) öğesi ekleyin ve aşağıdaki örnekte gösterildiği gibi çeşitli öznitelikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bfaf5-129">Then add a [\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md) element and set the various attributes, as shown in the following example.</span></span>  
  
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
  
2. <span data-ttu-id="bfaf5-130">Aşağıdaki örnekte gösterildiği gibi, hizmet için davranışı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="bfaf5-130">You must specify the behavior for the service, as shown in the following example.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="bfaf5-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="bfaf5-131">Example</span></span>  

 <span data-ttu-id="bfaf5-132">Aşağıdaki kod, sınıfının bir örneğini oluşturur <xref:System.ServiceModel.ServiceHost> ve davranışları koleksiyonuna yeni bir ekler <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> .</span><span class="sxs-lookup"><span data-stu-id="bfaf5-132">The following code creates an instance of the <xref:System.ServiceModel.ServiceHost> class and adds a new <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to its collection of behaviors.</span></span>  
  
 [!code-csharp[AuditingSecurityEvents#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#1)]
 [!code-vb[AuditingSecurityEvents#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#1)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="bfaf5-133">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="bfaf5-133">.NET Framework Security</span></span>  

 <span data-ttu-id="bfaf5-134"><xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A>Özelliği olarak ayarlamak `true` , güvenlik denetimleri oluşturma başarısızlığını göstermez (olarak ayarlanırsa `false` , bir özel durum oluşturulur).</span><span class="sxs-lookup"><span data-stu-id="bfaf5-134">Setting the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> property to `true`, suppresses any failure to generate security audits (if set to `false`, an exception is thrown).</span></span> <span data-ttu-id="bfaf5-135">Ancak, aşağıdaki Windows **yerel güvenlik ayarı** özelliğini etkinleştirirseniz, denetim olayları oluşturma hatası Windows 'un hemen kapatılmasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="bfaf5-135">However, if you enable the following Windows **Local Security Setting** property, a failure to generate audit events will cause Windows to shut down immediately:</span></span>  
  
 <span data-ttu-id="bfaf5-136">**Denetim: Güvenlik denetimleri günlüğe alınamıyorsa sistemi hemen kapat**</span><span class="sxs-lookup"><span data-stu-id="bfaf5-136">**Audit: Shut down system immediately if unable to log security audits**</span></span>  
  
 <span data-ttu-id="bfaf5-137">Özelliği ayarlamak için **yerel güvenlik ayarları** iletişim kutusunu açın.</span><span class="sxs-lookup"><span data-stu-id="bfaf5-137">To set the property, open the **Local Security Settings** dialog box.</span></span> <span data-ttu-id="bfaf5-138">**Güvenlik ayarları** altında **Yerel ilkeler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="bfaf5-138">Under **Security Settings**, click **Local Policies**.</span></span> <span data-ttu-id="bfaf5-139">Ardından **güvenlik seçenekleri**' ne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="bfaf5-139">Then click **Security Options**.</span></span>  
  
 <span data-ttu-id="bfaf5-140"><xref:System.ServiceModel.AuditLogLocation>Özelliği olarak ayarlandıysa <xref:System.ServiceModel.AuditLogLocation.Security> ve **Denetim nesne erişimi** **yerel güvenlik Ilkesinde** ayarlanmamışsa, denetim olayları güvenlik günlüğüne yazılmaz.</span><span class="sxs-lookup"><span data-stu-id="bfaf5-140">If the <xref:System.ServiceModel.AuditLogLocation> property is set to <xref:System.ServiceModel.AuditLogLocation.Security> and **Audit Object Access** is not set in the **Local Security Policy**, audit events will not be written to the Security log.</span></span> <span data-ttu-id="bfaf5-141">Hiçbir hata döndürülmediğini, ancak denetim girişlerinin güvenlik günlüğüne yazılmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="bfaf5-141">Note that no failure is returned, but audit entries are not written to the Security log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfaf5-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bfaf5-142">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A>
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- <xref:System.ServiceModel.AuditLogLocation>
- [<span data-ttu-id="bfaf5-143">Denetim</span><span class="sxs-lookup"><span data-stu-id="bfaf5-143">Auditing</span></span>](auditing-security-events.md)
