---
title: Hizmet Denetleme Davranışı
ms.date: 03/30/2017
ms.assetid: 59bf0cda-e496-4418-a3a1-2f0f6e85f8ce
ms.openlocfilehash: bfe13146a7f7cdec648a82a34c34077ec5466809
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599938"
---
# <a name="service-auditing-behavior"></a><span data-ttu-id="b4768-102">Hizmet Denetleme Davranışı</span><span class="sxs-lookup"><span data-stu-id="b4768-102">Service Auditing Behavior</span></span>
<span data-ttu-id="b4768-103">Bu örnek, <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> hizmet işlemleri sırasında güvenlik olaylarının denetlenmesini etkinleştirmek için öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b4768-103">This sample demonstrates how to use the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to enable auditing of security events during service operations.</span></span> <span data-ttu-id="b4768-104">Bu örnek, [Başlarken](getting-started-sample.md)' i temel alır.</span><span class="sxs-lookup"><span data-stu-id="b4768-104">This sample is based on the [Getting Started](getting-started-sample.md).</span></span> <span data-ttu-id="b4768-105">Hizmeti ve istemcisi kullanılarak yapılandırıldı [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="b4768-105">The service and client have been configured using the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="b4768-106">`mode`Öğesinin özniteliği [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) olarak ayarlanmıştır `Message` ve `clientCredentialType` olarak ayarlanmıştır `Windows` .</span><span class="sxs-lookup"><span data-stu-id="b4768-106">The `mode` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) has been set to `Message` and `clientCredentialType` has been set to `Windows`.</span></span> <span data-ttu-id="b4768-107">Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="b4768-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b4768-108">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="b4768-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="b4768-109">Hizmet yapılandırma dosyası, `serviceSecurityAudit` denetimi yapılandırmak için öğesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b4768-109">The service configuration file uses the `serviceSecurityAudit` element to configure auditing.</span></span>  
  
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
  
 <span data-ttu-id="b4768-110">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b4768-110">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="b4768-111">İstemcisini kapatmak için konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b4768-111">Press ENTER in the console window to shut down the client.</span></span>  
  
 <span data-ttu-id="b4768-112">Elde edilen denetim günlükleri Olay Görüntüleyicisi çalıştırılarak görülebilir.</span><span class="sxs-lookup"><span data-stu-id="b4768-112">The resulting audit logs can be seen by running the Event Viewer.</span></span> <span data-ttu-id="b4768-113">Varsayılan olarak, Windows XP 'de, Windows Server 2003 ve Windows Vista 'da denetim olayları uygulama günlüğünde görülebilir, bu da denetim olayları güvenlik günlüğünde görülebilir.</span><span class="sxs-lookup"><span data-stu-id="b4768-113">By default, on Windows XP the audit events can be seen in the Application Log while on Windows Server 2003 and Windows Vista, the audit events can be seen in the Security Log.</span></span> <span data-ttu-id="b4768-114">Windows Server 2008 ve Windows 7 ' de, denetim olayları uygulamalar ve hizmetler günlüklerinde görülebilir.</span><span class="sxs-lookup"><span data-stu-id="b4768-114">On Windows Server 2008 and Windows 7, the audit events can be seen in the Applications and Services logs.</span></span> <span data-ttu-id="b4768-115">`auditLogLocation`"Application" veya "Security" özniteliği ayarlanarak denetim olaylarının konumu belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="b4768-115">The location of audit events can be specified by setting the `auditLogLocation` attribute to "Application" or "Security".</span></span> <span data-ttu-id="b4768-116">Daha fazla bilgi için bkz. [nasıl yapılır: güvenlik olaylarını denetleme](../feature-details/how-to-audit-wcf-security-events.md).</span><span class="sxs-lookup"><span data-stu-id="b4768-116">For more information, see [How to: Audit Security Events](../feature-details/how-to-audit-wcf-security-events.md).</span></span> <span data-ttu-id="b4768-117">Olaylar güvenlik günlüğünde yazılmışsa, LocalSecurityPolicy-> nesne erişimini etkinleştir "başarı" ve "başarısızlık" için ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b4768-117">If the events are written in the Security Log the LocalSecurityPolicy-> Enable Object Access should be set for "Success" and "Failure".</span></span>  
  
 <span data-ttu-id="b4768-118">Olay günlüğüne baktığınızda, denetim olaylarının kaynağı "ServiceModel Audit 3.0.0.0" olur.</span><span class="sxs-lookup"><span data-stu-id="b4768-118">When looking at the event log, the source of the audit events is "ServiceModel Audit 3.0.0.0".</span></span> <span data-ttu-id="b4768-119">İleti kimlik doğrulaması denetim kayıtları, hizmet yetkilendirme denetim kayıtları "ServiceAuthorization" kategorisine sahip olsa da "MessageAuthentication" kategorisine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b4768-119">Message authentication audit records have a category of "MessageAuthentication" while service authorization audit records have a category of "ServiceAuthorization".</span></span>  
  
 <span data-ttu-id="b4768-120">İleti kimlik doğrulaması denetim olayları iletinin değiştirilip değiştirilmediğini, iletinin süresi dolmadığını ve istemcinin hizmette kimlik doğrulaması yapıp yapamadığını kapsar.</span><span class="sxs-lookup"><span data-stu-id="b4768-120">Message authentication audit events cover whether the message was tampered with, whether the message has expired, and whether the client can authenticate to the service.</span></span> <span data-ttu-id="b4768-121">Kimlik doğrulamanın, istemcinin kimliğiyle birlikte başarılı mı yoksa başarısız mı olduğunu ve iletinin iletiyle ilişkili eylem ile birlikte gönderildiği bitiş noktasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4768-121">They provide information about whether the authentication succeeded or failed along with the identity of the client, and the endpoint the message was sent to along with the action associated with the message.</span></span>  
  
 <span data-ttu-id="b4768-122">Hizmet yetkilendirme denetim olayları, bir hizmet Yetkilendirme Yöneticisi tarafından yapılan yetkilendirme kararlarını kapsar.</span><span class="sxs-lookup"><span data-stu-id="b4768-122">Service authorization audit events cover the authorization decision made by a service authorization manager.</span></span> <span data-ttu-id="b4768-123">Bunlar, Yetkilendirme başarılı veya başarısız olsun, istemcinin kimliği, iletinin gönderildiği bitiş noktası, iletiyle ilişkili eylem, gelen iletiden oluşturulan yetkilendirme bağlamının tanımlayıcısı ve erişim kararı veren Yetkilendirme Yöneticisi türü hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4768-123">They provide information about whether authorization succeeded or failed along with the identity of the client, the endpoint the message was sent to, the action associated with the message, the identifier of the authorization context that was generated from the incoming message, and the type of the authorization manager that made the access decision.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b4768-124">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="b4768-124">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b4768-125">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="b4768-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="b4768-126">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="b4768-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="b4768-127">Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="b4768-127">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4768-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4768-128">See also</span></span>

- [<span data-ttu-id="b4768-129">Denetim</span><span class="sxs-lookup"><span data-stu-id="b4768-129">Auditing</span></span>](../feature-details/auditing-security-events.md)
- [<span data-ttu-id="b4768-130">Nasıl yapılır: Güvenlik Olaylarını Denetleme</span><span class="sxs-lookup"><span data-stu-id="b4768-130">How to: Audit Security Events</span></span>](../feature-details/how-to-audit-wcf-security-events.md)
