---
title: 'Nasıl yapılır: Windows Communication Foundation Güvenlik Olaylarını Denetleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], auditing events
ms.assetid: e71e9587-3336-46a2-9a9e-d72a1743ecec
author: BrucePerlerMS
ms.openlocfilehash: 1efd651751e0f81b5125b64f81f7d2087d002d8d
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47196287"
---
# <a name="how-to-audit-windows-communication-foundation-security-events"></a><span data-ttu-id="e0cb4-102">Nasıl yapılır: Windows Communication Foundation Güvenlik Olaylarını Denetleme</span><span class="sxs-lookup"><span data-stu-id="e0cb4-102">How to: Audit Windows Communication Foundation Security Events</span></span>
<span data-ttu-id="e0cb4-103">Windows Communication Foundation (WCF), güvenlik olaylarını Windows olay, Windows Olay Görüntüleyicisi'ni kullanarak görüntüleyebileceğiniz, günlüğüne olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="e0cb4-103">Windows Communication Foundation (WCF) allows you to log security events to the Windows event log, which can be viewed using the Windows Event Viewer.</span></span> <span data-ttu-id="e0cb4-104">Bu konu başlığı altında güvenlik olayları kaydeder, böylece uygulama ayarlama açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e0cb4-104">This topic explains how to set up an application so that it logs security events.</span></span> <span data-ttu-id="e0cb4-105">WCF denetimi hakkında daha fazla bilgi için bkz. [denetim](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).</span><span class="sxs-lookup"><span data-stu-id="e0cb4-105">For more information about WCF auditing, see [Auditing](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).</span></span>  
  
### <a name="to-audit-security-events-in-code"></a><span data-ttu-id="e0cb4-106">Kod içindeki güvenlik olaylarını denetleme</span><span class="sxs-lookup"><span data-stu-id="e0cb4-106">To audit security events in code</span></span>  
  
1.  <span data-ttu-id="e0cb4-107">Denetim günlüğü konumu belirtin.</span><span class="sxs-lookup"><span data-stu-id="e0cb4-107">Specify the audit log location.</span></span> <span data-ttu-id="e0cb4-108">Bunu yapmak için ayarlanmış <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> özelliği <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> sınıfı birine <xref:System.ServiceModel.AuditLogLocation> numaralandırma değerlerinin, aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="e0cb4-108">To do this, set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> property of the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> class to one of the <xref:System.ServiceModel.AuditLogLocation> enumeration values, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#2)]
     [!code-vb[AuditingSecurityEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#2)]  
  
     <span data-ttu-id="e0cb4-109"><xref:System.ServiceModel.AuditLogLocation> Numaralandırması üç değer vardır: `Application`, `Security`, veya `Default`.</span><span class="sxs-lookup"><span data-stu-id="e0cb4-109">The <xref:System.ServiceModel.AuditLogLocation> enumeration has three values: `Application`, `Security`, or `Default`.</span></span> <span data-ttu-id="e0cb4-110">Değer günlükleri Olay Görüntüleyicisi'nde görünür birini ya da güvenlik günlüğü veya Uygulama günlüğünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="e0cb4-110">The value specifies one of the logs visible in the Event Viewer, either the Security log or the Application log.</span></span> <span data-ttu-id="e0cb4-111">Kullanırsanız `Default` değeri, gerçek günlük bağımlı üzerinde uygulamayı çalıştırdığınız işletim sistemi.</span><span class="sxs-lookup"><span data-stu-id="e0cb4-111">If you use the `Default` value, the actual log will depend on the operating system the application is running on.</span></span> <span data-ttu-id="e0cb4-112">Etkin denetim ve günlük konumu belirtilmezse, varsayılan değer `Security` günlük yazma desteği sunan platformlar için güvenlik günlüğü için; Aksi takdirde, Yazar `Application` günlük.</span><span class="sxs-lookup"><span data-stu-id="e0cb4-112">If auditing is enabled and the log location is not specified, the default is the `Security` log for platforms that support writing to the Security log; otherwise, it will write to the `Application` log.</span></span> <span data-ttu-id="e0cb4-113">Yalnızca [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wv](../../../../includes/wv-md.md)] varsayılan olarak güvenlik günlüğüne yazma desteği.</span><span class="sxs-lookup"><span data-stu-id="e0cb4-113">Only [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] and [!INCLUDE[wv](../../../../includes/wv-md.md)] support writing to the Security log by default.</span></span>  
  
2.  <span data-ttu-id="e0cb4-114">Denetlenecek olay türlerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e0cb4-114">Set up the types of events to audit.</span></span> <span data-ttu-id="e0cb4-115">Aynı anda hizmet düzeyi olayları veya ileti düzeyinde yetkilendirme olayları da denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0cb4-115">You can simultaneously audit service-level events or message-level authorization events.</span></span> <span data-ttu-id="e0cb4-116">Bunu yapmak için ayarlanmış <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> özelliği veya <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> özelliğini birine <xref:System.ServiceModel.AuditLevel> numaralandırma değerlerinin, aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="e0cb4-116">To do this, set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> property or the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> property to one of the <xref:System.ServiceModel.AuditLevel> enumeration values, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#3)]
     [!code-vb[AuditingSecurityEvents#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#3)]  
  
3.  <span data-ttu-id="e0cb4-117">Uygulama günlüğü denetim olaylarını ile ilgili hataları kullanıma sunmak bu seçeneği belirtin.</span><span class="sxs-lookup"><span data-stu-id="e0cb4-117">Specify whether to suppress or expose failures to the application regarding log audit events.</span></span> <span data-ttu-id="e0cb4-118">Ayarlama <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> ya da özellik `true` veya `false`aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="e0cb4-118">Set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> property to either `true` or `false`, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#4)]
     [!code-vb[AuditingSecurityEvents#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#4)]  
  
     <span data-ttu-id="e0cb4-119">Varsayılan `SuppressAuditFailure` özelliği `true`, böylece denetleme hatası uygulamayı etkilemez.</span><span class="sxs-lookup"><span data-stu-id="e0cb4-119">The default `SuppressAuditFailure` property is `true`, so that the failure to audit does not affect the application.</span></span> <span data-ttu-id="e0cb4-120">Aksi takdirde, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e0cb4-120">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="e0cb4-121">Başarılı bir denetim için bir ayrıntılı izleme yazılır.</span><span class="sxs-lookup"><span data-stu-id="e0cb4-121">For any successful audit, a verbose trace is written.</span></span> <span data-ttu-id="e0cb4-122">Denetim herhangi bir hata için izleme hata düzeyinde yazılır.</span><span class="sxs-lookup"><span data-stu-id="e0cb4-122">For any failure to audit, the trace is written at the Error level.</span></span>  
  
4.  <span data-ttu-id="e0cb4-123">Var olanı Sil <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> davranışları açıklamada bulunan koleksiyonundan bir <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="e0cb4-123">Delete the existing <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> from the collection of behaviors found in the description of a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="e0cb4-124">Davranış koleksiyon tarafından erişilen <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> karşılık gelen erişilen özelliği <xref:System.ServiceModel.ServiceHostBase.Description%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="e0cb4-124">The behavior collection is accessed by the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> property, which in turn is accessed from the <xref:System.ServiceModel.ServiceHostBase.Description%2A> property.</span></span> <span data-ttu-id="e0cb4-125">Ardından yeni ekleyin <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> aşağıdaki kodda gösterildiği gibi aynı koleksiyonuna.</span><span class="sxs-lookup"><span data-stu-id="e0cb4-125">Then add the new <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to the same collection, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#5)]
     [!code-vb[AuditingSecurityEvents#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#5)]  
  
### <a name="to-set-up-auditing-in-configuration"></a><span data-ttu-id="e0cb4-126">Yapılandırmada denetimini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="e0cb4-126">To set up auditing in configuration</span></span>  
  
1.  <span data-ttu-id="e0cb4-127">Yapılandırmada denetimini ayarlamak için eklemek bir [ \<davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) öğesine [ \<davranışları >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) web.config dosyasının bölümü.</span><span class="sxs-lookup"><span data-stu-id="e0cb4-127">To set up auditing in configuration, add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) section of the web.config file.</span></span> <span data-ttu-id="e0cb4-128">Ardından Ekle bir [ \<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) öğesi ve çeşitli öznitelikler, aşağıdaki örnekte gösterildiği gibi kümesi.</span><span class="sxs-lookup"><span data-stu-id="e0cb4-128">Then add a [\<serviceSecurityAudit>](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) element and set the various attributes, as shown in the following example.</span></span>  
  
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
  
2.  <span data-ttu-id="e0cb4-129">Aşağıdaki örnekte gösterildiği gibi hizmet davranışı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0cb4-129">You must specify the behavior for the service, as shown in the following example.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="e0cb4-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="e0cb4-130">Example</span></span>  
 <span data-ttu-id="e0cb4-131">Aşağıdaki kod örneği oluşturur <xref:System.ServiceModel.ServiceHost> sınıfı ve yeni bir ekler <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> davranışları kendi koleksiyonuna.</span><span class="sxs-lookup"><span data-stu-id="e0cb4-131">The following code creates an instance of the <xref:System.ServiceModel.ServiceHost> class and adds a new <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to its collection of behaviors.</span></span>  
  
 [!code-csharp[AuditingSecurityEvents#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#1)]
 [!code-vb[AuditingSecurityEvents#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#1)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="e0cb4-132">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="e0cb4-132">.NET Framework Security</span></span>  
 <span data-ttu-id="e0cb4-133">Ayarı <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> özelliğini `true`, güvenlik denetimleri üretmek için herhangi bir hata bastırır (varsa kümesine `false`, bir özel durum).</span><span class="sxs-lookup"><span data-stu-id="e0cb4-133">Setting the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> property to `true`, suppresses any failure to generate security audits (if set to `false`, an exception is thrown).</span></span> <span data-ttu-id="e0cb4-134">Ancak, aşağıdaki Windows etkinleştirirseniz **yerel güvenlik ayarları** özelliği, denetim olayları oluşturmak için bir hata neden hemen kapatmak Windows:</span><span class="sxs-lookup"><span data-stu-id="e0cb4-134">However, if you enable the following Windows **Local Security Setting** property, a failure to generate audit events will cause Windows to shut down immediately:</span></span>  
  
 <span data-ttu-id="e0cb4-135">**Güvenlik günlüğü için denetimleri denetim: sistemi hemen kapat**</span><span class="sxs-lookup"><span data-stu-id="e0cb4-135">**Audit: Shut down system immediately if unable to log security audits**</span></span>  
  
 <span data-ttu-id="e0cb4-136">Özellik ayarlamak için açık **yerel güvenlik ayarları** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="e0cb4-136">To set the property, open the **Local Security Settings** dialog box.</span></span> <span data-ttu-id="e0cb4-137">Altında **güvenlik ayarları**, tıklayın **yerel ilkeler**.</span><span class="sxs-lookup"><span data-stu-id="e0cb4-137">Under **Security Settings**, click **Local Policies**.</span></span> <span data-ttu-id="e0cb4-138">Ardından **güvenlik seçenekleri**.</span><span class="sxs-lookup"><span data-stu-id="e0cb4-138">Then click **Security Options**.</span></span>  
  
 <span data-ttu-id="e0cb4-139">Varsa <xref:System.ServiceModel.AuditLogLocation> özelliği <xref:System.ServiceModel.AuditLogLocation.Security> ve **Nesne erişimini denetle** ayarlanmadı **yerel güvenlik ilkesi**, denetim olayları güvenlik günlüğüne değil yazılır.</span><span class="sxs-lookup"><span data-stu-id="e0cb4-139">If the <xref:System.ServiceModel.AuditLogLocation> property is set to <xref:System.ServiceModel.AuditLogLocation.Security> and **Audit Object Access** is not set in the **Local Security Policy**, audit events will not be written to the Security log.</span></span> <span data-ttu-id="e0cb4-140">Hiçbir hata döndürdü, ancak denetim girişleri güvenlik günlüğüne yazılmaz unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e0cb4-140">Note that no failure is returned, but audit entries are not written to the Security log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0cb4-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e0cb4-141">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>  
 <xref:System.ServiceModel.AuditLogLocation>  
 [<span data-ttu-id="e0cb4-142">Denetim</span><span class="sxs-lookup"><span data-stu-id="e0cb4-142">Auditing</span></span>](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
