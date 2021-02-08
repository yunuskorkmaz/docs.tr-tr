---
description: 'Hakkında daha fazla bilgi edinin: hizmet denetleme davranışı'
title: Hizmet Denetleme Davranışı
ms.date: 03/30/2017
ms.assetid: 59bf0cda-e496-4418-a3a1-2f0f6e85f8ce
ms.openlocfilehash: 101f737d790d7e5ec0fdefc3a60695cb3c432c28
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793135"
---
# <a name="service-auditing-behavior"></a><span data-ttu-id="e3ad1-103">Hizmet Denetleme Davranışı</span><span class="sxs-lookup"><span data-stu-id="e3ad1-103">Service Auditing Behavior</span></span>

<span data-ttu-id="e3ad1-104">Bu örnek, <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> hizmet işlemleri sırasında güvenlik olaylarının denetlenmesini etkinleştirmek için öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e3ad1-104">This sample demonstrates how to use the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to enable auditing of security events during service operations.</span></span> <span data-ttu-id="e3ad1-105">Bu örnek, [Başlarken](getting-started-sample.md)' i temel alır.</span><span class="sxs-lookup"><span data-stu-id="e3ad1-105">This sample is based on the [Getting Started](getting-started-sample.md).</span></span> <span data-ttu-id="e3ad1-106">Hizmeti ve istemcisi kullanılarak yapılandırıldı [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="e3ad1-106">The service and client have been configured using the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="e3ad1-107">`mode`Öğesinin özniteliği [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) olarak ayarlanmıştır `Message` ve `clientCredentialType` olarak ayarlanmıştır `Windows` .</span><span class="sxs-lookup"><span data-stu-id="e3ad1-107">The `mode` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) has been set to `Message` and `clientCredentialType` has been set to `Windows`.</span></span> <span data-ttu-id="e3ad1-108">Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="e3ad1-108">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e3ad1-109">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="e3ad1-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e3ad1-110">Hizmet yapılandırma dosyası, `serviceSecurityAudit` denetimi yapılandırmak için öğesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e3ad1-110">The service configuration file uses the `serviceSecurityAudit` element to configure auditing.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      ...  
<!-- serviceSecurityAudit allows specification of audit location   
     and whether to audit success, failure or both. This service   
     logs success and failure of messageAuthentication   
     to the default location -->  
     <serviceSecurityAudit auditLogLocation ="Default" messageAuthenticationAuditLevel = "SuccessOrFailure" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="e3ad1-111">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e3ad1-111">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="e3ad1-112">İstemcisini kapatmak için konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e3ad1-112">Press ENTER in the console window to shut down the client.</span></span>  
  
 <span data-ttu-id="e3ad1-113">Elde edilen denetim günlükleri Olay Görüntüleyicisi çalıştırılarak görülebilir.</span><span class="sxs-lookup"><span data-stu-id="e3ad1-113">The resulting audit logs can be seen by running the Event Viewer.</span></span> <span data-ttu-id="e3ad1-114">Varsayılan olarak, Windows XP 'de, Windows Server 2003 ve Windows Vista 'da denetim olayları uygulama günlüğünde görülebilir, bu da denetim olayları güvenlik günlüğünde görülebilir.</span><span class="sxs-lookup"><span data-stu-id="e3ad1-114">By default, on Windows XP the audit events can be seen in the Application Log while on Windows Server 2003 and Windows Vista, the audit events can be seen in the Security Log.</span></span> <span data-ttu-id="e3ad1-115">Windows Server 2008 ve Windows 7 ' de, denetim olayları uygulamalar ve hizmetler günlüklerinde görülebilir.</span><span class="sxs-lookup"><span data-stu-id="e3ad1-115">On Windows Server 2008 and Windows 7, the audit events can be seen in the Applications and Services logs.</span></span> <span data-ttu-id="e3ad1-116">`auditLogLocation`"Application" veya "Security" özniteliği ayarlanarak denetim olaylarının konumu belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="e3ad1-116">The location of audit events can be specified by setting the `auditLogLocation` attribute to "Application" or "Security".</span></span> <span data-ttu-id="e3ad1-117">Daha fazla bilgi için bkz. [nasıl yapılır: güvenlik olaylarını denetleme](../feature-details/how-to-audit-wcf-security-events.md).</span><span class="sxs-lookup"><span data-stu-id="e3ad1-117">For more information, see [How to: Audit Security Events](../feature-details/how-to-audit-wcf-security-events.md).</span></span> <span data-ttu-id="e3ad1-118">Olaylar güvenlik günlüğünde yazılmışsa, LocalSecurityPolicy-> nesne erişimini etkinleştir "başarı" ve "başarısızlık" için ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e3ad1-118">If the events are written in the Security Log the LocalSecurityPolicy-> Enable Object Access should be set for "Success" and "Failure".</span></span>  
  
 <span data-ttu-id="e3ad1-119">Olay günlüğüne baktığınızda, denetim olaylarının kaynağı "ServiceModel Audit 3.0.0.0" olur.</span><span class="sxs-lookup"><span data-stu-id="e3ad1-119">When looking at the event log, the source of the audit events is "ServiceModel Audit 3.0.0.0".</span></span> <span data-ttu-id="e3ad1-120">İleti kimlik doğrulaması denetim kayıtları, hizmet yetkilendirme denetim kayıtları "ServiceAuthorization" kategorisine sahip olsa da "MessageAuthentication" kategorisine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e3ad1-120">Message authentication audit records have a category of "MessageAuthentication" while service authorization audit records have a category of "ServiceAuthorization".</span></span>  
  
 <span data-ttu-id="e3ad1-121">İleti kimlik doğrulaması denetim olayları iletinin değiştirilip değiştirilmediğini, iletinin süresi dolmadığını ve istemcinin hizmette kimlik doğrulaması yapıp yapamadığını kapsar.</span><span class="sxs-lookup"><span data-stu-id="e3ad1-121">Message authentication audit events cover whether the message was tampered with, whether the message has expired, and whether the client can authenticate to the service.</span></span> <span data-ttu-id="e3ad1-122">Kimlik doğrulamanın, istemcinin kimliğiyle birlikte başarılı mı yoksa başarısız mı olduğunu ve iletinin iletiyle ilişkili eylem ile birlikte gönderildiği bitiş noktasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e3ad1-122">They provide information about whether the authentication succeeded or failed along with the identity of the client, and the endpoint the message was sent to along with the action associated with the message.</span></span>  
  
 <span data-ttu-id="e3ad1-123">Hizmet yetkilendirme denetim olayları, bir hizmet Yetkilendirme Yöneticisi tarafından yapılan yetkilendirme kararlarını kapsar.</span><span class="sxs-lookup"><span data-stu-id="e3ad1-123">Service authorization audit events cover the authorization decision made by a service authorization manager.</span></span> <span data-ttu-id="e3ad1-124">Bunlar, Yetkilendirme başarılı veya başarısız olsun, istemcinin kimliği, iletinin gönderildiği bitiş noktası, iletiyle ilişkili eylem, gelen iletiden oluşturulan yetkilendirme bağlamının tanımlayıcısı ve erişim kararı veren Yetkilendirme Yöneticisi türü hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e3ad1-124">They provide information about whether authorization succeeded or failed along with the identity of the client, the endpoint the message was sent to, the action associated with the message, the identifier of the authorization context that was generated from the incoming message, and the type of the authorization manager that made the access decision.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e3ad1-125">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="e3ad1-125">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e3ad1-126">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="e3ad1-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="e3ad1-127">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="e3ad1-127">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="e3ad1-128">Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="e3ad1-128">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3ad1-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e3ad1-129">See also</span></span>

- [<span data-ttu-id="e3ad1-130">Denetim</span><span class="sxs-lookup"><span data-stu-id="e3ad1-130">Auditing</span></span>](../feature-details/auditing-security-events.md)
- [<span data-ttu-id="e3ad1-131">Nasıl yapılır: Güvenlik Olaylarını Denetleme</span><span class="sxs-lookup"><span data-stu-id="e3ad1-131">How to: Audit Security Events</span></span>](../feature-details/how-to-audit-wcf-security-events.md)
