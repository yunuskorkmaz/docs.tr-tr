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
# <a name="how-to-audit-windows-communication-foundation-security-events"></a><span data-ttu-id="d3ea0-102">Nasıl yapılır: Windows Communication Foundation Güvenlik Olaylarını Denetleme</span><span class="sxs-lookup"><span data-stu-id="d3ea0-102">How to: Audit Windows Communication Foundation Security Events</span></span>
<span data-ttu-id="d3ea0-103">Windows Communication Foundation (WCF), güvenlik olaylarını Windows Olay Görüntüleyicisi kullanılarak görüntülenebilen Windows olay günlüğüne günlüğe kaydetmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d3ea0-103">Windows Communication Foundation (WCF) allows you to log security events to the Windows event log, which can be viewed using the Windows Event Viewer.</span></span> <span data-ttu-id="d3ea0-104">Bu konu, güvenlik olaylarını günlüğe kaydedecek şekilde bir uygulamanın nasıl ayarlanışsüreceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="d3ea0-104">This topic explains how to set up an application so that it logs security events.</span></span> <span data-ttu-id="d3ea0-105">WCF denetimi hakkında daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)</span><span class="sxs-lookup"><span data-stu-id="d3ea0-105">For more information about WCF auditing, see [Auditing](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).</span></span>  
  
### <a name="to-audit-security-events-in-code"></a><span data-ttu-id="d3ea0-106">Güvenlik olaylarını kodda denetlemek için</span><span class="sxs-lookup"><span data-stu-id="d3ea0-106">To audit security events in code</span></span>  
  
1. <span data-ttu-id="d3ea0-107">Denetim günlüğü konumunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="d3ea0-107">Specify the audit log location.</span></span> <span data-ttu-id="d3ea0-108">Bunu yapmak için, <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> sınıfın <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> özelliğini aşağıdaki <xref:System.ServiceModel.AuditLogLocation> kodda gösterildiği gibi numaralandırma değerlerinden birine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d3ea0-108">To do this, set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> property of the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> class to one of the <xref:System.ServiceModel.AuditLogLocation> enumeration values, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#2)]
     [!code-vb[AuditingSecurityEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#2)]  
  
     <span data-ttu-id="d3ea0-109">Numaralandırmanın <xref:System.ServiceModel.AuditLogLocation> üç değeri `Application`vardır: `Security`, `Default`, veya .</span><span class="sxs-lookup"><span data-stu-id="d3ea0-109">The <xref:System.ServiceModel.AuditLogLocation> enumeration has three values: `Application`, `Security`, or `Default`.</span></span> <span data-ttu-id="d3ea0-110">Değer, Olay Görüntüleyicisi'nde görünen günlüklerden birini, Güvenlik günlüğü veya Uygulama günlüğünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="d3ea0-110">The value specifies one of the logs visible in the Event Viewer, either the Security log or the Application log.</span></span> <span data-ttu-id="d3ea0-111">`Default` Değeri kullanırsanız, gerçek günlük uygulamanın çalıştığı işletim sistemine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="d3ea0-111">If you use the `Default` value, the actual log will depend on the operating system the application is running on.</span></span> <span data-ttu-id="d3ea0-112">Denetim etkinleştirilmişse ve günlük konumu belirtilmemişse, varsayılan değer Güvenlik günlüğüne yazmayı destekleyen platformlar için `Security` günlükolur; aksi takdirde, `Application` günlük yazacaktır.</span><span class="sxs-lookup"><span data-stu-id="d3ea0-112">If auditing is enabled and the log location is not specified, the default is the `Security` log for platforms that support writing to the Security log; otherwise, it will write to the `Application` log.</span></span> <span data-ttu-id="d3ea0-113">Yalnızca Windows Server 2003 ve Windows Vista varsayılan olarak Güvenlik günlüğüne yazmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="d3ea0-113">Only Windows Server 2003 and Windows Vista support writing to the Security log by default.</span></span>  
  
2. <span data-ttu-id="d3ea0-114">Denetlemek için etkinlik türlerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d3ea0-114">Set up the types of events to audit.</span></span> <span data-ttu-id="d3ea0-115">Hizmet düzeyi etkinlikleri veya ileti düzeyinde yetkilendirme olaylarını aynı anda denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3ea0-115">You can simultaneously audit service-level events or message-level authorization events.</span></span> <span data-ttu-id="d3ea0-116">Bunu yapmak için, <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> aşağıdaki <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> kodda gösterildiği <xref:System.ServiceModel.AuditLevel> gibi özelliği veya özelliği numaralandırma değerlerinden birine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d3ea0-116">To do this, set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> property or the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> property to one of the <xref:System.ServiceModel.AuditLevel> enumeration values, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#3)]
     [!code-vb[AuditingSecurityEvents#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#3)]  
  
3. <span data-ttu-id="d3ea0-117">Günlük denetimi olaylarıyla ilgili hataları bastırıp bastırmayyacağınızı veya uygulamada hataları ortaya çıkartıp göstermeyeceğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="d3ea0-117">Specify whether to suppress or expose failures to the application regarding log audit events.</span></span> <span data-ttu-id="d3ea0-118">Aşağıdaki <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> kodda `true` gösterildiği `false`gibi özelliği aşağıdaki koddan biri veya</span><span class="sxs-lookup"><span data-stu-id="d3ea0-118">Set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> property to either `true` or `false`, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#4)]
     [!code-vb[AuditingSecurityEvents#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#4)]  
  
     <span data-ttu-id="d3ea0-119">Varsayılan `SuppressAuditFailure` `true`özellik, böylece denetim başarısızlığı uygulamayı etkilemez.</span><span class="sxs-lookup"><span data-stu-id="d3ea0-119">The default `SuppressAuditFailure` property is `true`, so that the failure to audit does not affect the application.</span></span> <span data-ttu-id="d3ea0-120">Aksi takdirde, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d3ea0-120">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="d3ea0-121">Başarılı bir denetim için ayrıntılı bir izleme yazılır.</span><span class="sxs-lookup"><span data-stu-id="d3ea0-121">For any successful audit, a verbose trace is written.</span></span> <span data-ttu-id="d3ea0-122">Herhangi bir denetim hatası için izleme Hata düzeyinde yazılır.</span><span class="sxs-lookup"><span data-stu-id="d3ea0-122">For any failure to audit, the trace is written at the Error level.</span></span>  
  
4. <span data-ttu-id="d3ea0-123">Bir <xref:System.ServiceModel.ServiceHost>' <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> nin açıklamasında bulunan davranışlar koleksiyonundan varolan ları silin.</span><span class="sxs-lookup"><span data-stu-id="d3ea0-123">Delete the existing <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> from the collection of behaviors found in the description of a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="d3ea0-124">Davranış koleksiyonuna, özellikten <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> <xref:System.ServiceModel.ServiceHostBase.Description%2A> erişilen özellik tarafından erişilir.</span><span class="sxs-lookup"><span data-stu-id="d3ea0-124">The behavior collection is accessed by the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> property, which in turn is accessed from the <xref:System.ServiceModel.ServiceHostBase.Description%2A> property.</span></span> <span data-ttu-id="d3ea0-125">Ardından, aşağıdaki <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> kodda gösterildiği gibi, yeniyi aynı koleksiyona ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d3ea0-125">Then add the new <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to the same collection, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#5)]
     [!code-vb[AuditingSecurityEvents#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#5)]  
  
### <a name="to-set-up-auditing-in-configuration"></a><span data-ttu-id="d3ea0-126">Yapılandırmada denetim kurmak için</span><span class="sxs-lookup"><span data-stu-id="d3ea0-126">To set up auditing in configuration</span></span>  
  
1. <span data-ttu-id="d3ea0-127">Yapılandırmada denetim ayarlamak için, web.config dosyasının [ \<>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) bölümüne davranış [ \<>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d3ea0-127">To set up auditing in configuration, add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) section of the web.config file.</span></span> <span data-ttu-id="d3ea0-128">Ardından bir [ \<serviceSecurityAudit>](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) öğesi ekleyin ve aşağıdaki örnekte gösterildiği gibi çeşitli öznitelikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d3ea0-128">Then add a [\<serviceSecurityAudit>](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) element and set the various attributes, as shown in the following example.</span></span>  
  
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
  
2. <span data-ttu-id="d3ea0-129">Aşağıdaki örnekte gösterildiği gibi hizmetin davranışını belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d3ea0-129">You must specify the behavior for the service, as shown in the following example.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="d3ea0-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="d3ea0-130">Example</span></span>  
 <span data-ttu-id="d3ea0-131">Aşağıdaki kod sınıfın bir örneğini <xref:System.ServiceModel.ServiceHost> oluşturur ve <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> davranış koleksiyonuna yeni bir yeni ekler.</span><span class="sxs-lookup"><span data-stu-id="d3ea0-131">The following code creates an instance of the <xref:System.ServiceModel.ServiceHost> class and adds a new <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to its collection of behaviors.</span></span>  
  
 [!code-csharp[AuditingSecurityEvents#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#1)]
 [!code-vb[AuditingSecurityEvents#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#1)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="d3ea0-132">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="d3ea0-132">.NET Framework Security</span></span>  
 <span data-ttu-id="d3ea0-133"><xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> Özelliği `true`ayarlamak, güvenlik denetimleri oluşturmadaki tüm hataları bastırır `false`(ayarlanmışsa, bir özel durum atılır).</span><span class="sxs-lookup"><span data-stu-id="d3ea0-133">Setting the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> property to `true`, suppresses any failure to generate security audits (if set to `false`, an exception is thrown).</span></span> <span data-ttu-id="d3ea0-134">Ancak, aşağıdaki Windows **Yerel Güvenlik Ayarı** özelliğini etkinleştiriseniz, denetim olayları nın oluşturulmasında başarısız olmak Windows'un hemen kapanmasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="d3ea0-134">However, if you enable the following Windows **Local Security Setting** property, a failure to generate audit events will cause Windows to shut down immediately:</span></span>  
  
 <span data-ttu-id="d3ea0-135">**Denetim: Güvenlik denetimleri günlüğe alınamıyorsa sistemi hemen kapat**</span><span class="sxs-lookup"><span data-stu-id="d3ea0-135">**Audit: Shut down system immediately if unable to log security audits**</span></span>  
  
 <span data-ttu-id="d3ea0-136">Özelliği ayarlamak için **Yerel Güvenlik Ayarları** iletişim kutusunu açın.</span><span class="sxs-lookup"><span data-stu-id="d3ea0-136">To set the property, open the **Local Security Settings** dialog box.</span></span> <span data-ttu-id="d3ea0-137">**Güvenlik Ayarları**altında, **Yerel İlkeler'i**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="d3ea0-137">Under **Security Settings**, click **Local Policies**.</span></span> <span data-ttu-id="d3ea0-138">Ardından **Güvenlik Seçenekleri'ni**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="d3ea0-138">Then click **Security Options**.</span></span>  
  
 <span data-ttu-id="d3ea0-139">Özellik ayarlanırsa <xref:System.ServiceModel.AuditLogLocation.Security> ve **Denetim Nesnesi Erişimi** **Yerel Güvenlik İlkesi'nde**ayarlanmazsa, denetim olayları Güvenlik günlüğüne yazılmaz. <xref:System.ServiceModel.AuditLogLocation></span><span class="sxs-lookup"><span data-stu-id="d3ea0-139">If the <xref:System.ServiceModel.AuditLogLocation> property is set to <xref:System.ServiceModel.AuditLogLocation.Security> and **Audit Object Access** is not set in the **Local Security Policy**, audit events will not be written to the Security log.</span></span> <span data-ttu-id="d3ea0-140">Hata döndürülmediğini, ancak denetim girişlerinin Güvenlik günlüğüne yazıldığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d3ea0-140">Note that no failure is returned, but audit entries are not written to the Security log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3ea0-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3ea0-141">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A>
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- <xref:System.ServiceModel.AuditLogLocation>
- [<span data-ttu-id="d3ea0-142">Denetim</span><span class="sxs-lookup"><span data-stu-id="d3ea0-142">Auditing</span></span>](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
