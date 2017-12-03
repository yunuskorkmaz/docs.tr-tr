---
title: "Hizmet Denetleme Davranışı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59bf0cda-e496-4418-a3a1-2f0f6e85f8ce
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f84bff892a35288a75738d9cfa326ffc4119b433
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="service-auditing-behavior"></a><span data-ttu-id="c1e58-102">Hizmet Denetleme Davranışı</span><span class="sxs-lookup"><span data-stu-id="c1e58-102">Service Auditing Behavior</span></span>
<span data-ttu-id="c1e58-103">Bu örnek nasıl kullanılacağı ortaya <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> hizmet işlemleri sırasında güvenlik olaylarının denetimini etkinleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="c1e58-103">This sample demonstrates how to use the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to enable auditing of security events during service operations.</span></span> <span data-ttu-id="c1e58-104">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="c1e58-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="c1e58-105">İstemci ve hizmet kullanılarak yapılandırılmış [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="c1e58-105">The service and client have been configured using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="c1e58-106">`mode` Özniteliği [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) ayarlandığından `Message` ve `clientCredentialType` ayarlandığından `Windows`.</span><span class="sxs-lookup"><span data-stu-id="c1e58-106">The `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) has been set to `Message` and `clientCredentialType` has been set to `Windows`.</span></span> <span data-ttu-id="c1e58-107">Bu örnekte, istemci bir konsol uygulaması (.exe) ve Internet Information Services (IIS) tarafından barındırılan hizmetindeki.</span><span class="sxs-lookup"><span data-stu-id="c1e58-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c1e58-108">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="c1e58-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c1e58-109">Hizmet yapılandırma dosyası kullanan `serviceSecurityAudit` denetimi yapılandırmak amacıyla öğesi.</span><span class="sxs-lookup"><span data-stu-id="c1e58-109">The service configuration file uses the `serviceSecurityAudit` element to configure auditing.</span></span>  
  
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
  
 <span data-ttu-id="c1e58-110">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c1e58-110">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="c1e58-111">Konsol penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c1e58-111">Press ENTER in the console window to shut down the client.</span></span>  
  
 <span data-ttu-id="c1e58-112">Sonuçta elde edilen denetim günlüklerini Olay Görüntüleyicisi'ni çalıştırarak görülebilir.</span><span class="sxs-lookup"><span data-stu-id="c1e58-112">The resulting audit logs can be seen by running the Event Viewer.</span></span> <span data-ttu-id="c1e58-113">Varsayılan olarak, Windows XP Windows Server 2003 ve Windows Vista üzerinde uygulama günlüğünde denetim olaylarını görülebilir denetim olaylarını güvenlik günlüğüne görülebilir.</span><span class="sxs-lookup"><span data-stu-id="c1e58-113">By default, on Windows XP the audit events can be seen in the Application Log while on Windows Server 2003 and Windows Vista, the audit events can be seen in the Security Log.</span></span> <span data-ttu-id="c1e58-114">Windows Server 2008 ve Windows 7 üzerinde denetim olayları uygulamaları ve Hizmetleri günlüklerinde görülebilir.</span><span class="sxs-lookup"><span data-stu-id="c1e58-114">On Windows Server 2008 and Windows 7, the audit events can be seen in the Applications and Services logs.</span></span> <span data-ttu-id="c1e58-115">Denetim olaylarının konumu ayarlayarak belirtilebilir `auditLogLocation` özniteliği için "Uygulama" veya "Güvenlik".</span><span class="sxs-lookup"><span data-stu-id="c1e58-115">The location of audit events can be specified by setting the `auditLogLocation` attribute to "Application" or "Security".</span></span> <span data-ttu-id="c1e58-116">Daha fazla bilgi için bkz: [nasıl yapılır: denetim güvenlik olaylarını](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md).</span><span class="sxs-lookup"><span data-stu-id="c1e58-116">For more information, see [How to: Audit Security Events](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md).</span></span> <span data-ttu-id="c1e58-117">Nesne erişimi etkinleştir "Başarılı" ve "Başarısız" için ayarlanmalıdır LocalSecurityPolicy -> güvenlik günlüğüne yazılan olaylar durumunda.</span><span class="sxs-lookup"><span data-stu-id="c1e58-117">If the events are written in the Security Log the LocalSecurityPolicy-> Enable Object Access should be set for "Success" and "Failure".</span></span>  
  
 <span data-ttu-id="c1e58-118">Olay günlüğü bakarken olaylarını denetle "ServiceModel denetim 3.0.0.0" kaynağıdır.</span><span class="sxs-lookup"><span data-stu-id="c1e58-118">When looking at the event log, the source of the audit events is "ServiceModel Audit 3.0.0.0".</span></span> <span data-ttu-id="c1e58-119">Hizmet yetkilendirme denetim kayıtlarının "ServiceAuthorization" kategorisi bulunurken ileti kimlik doğrulama denetim kayıtlarının "MessageAuthentication" kategorisi vardır.</span><span class="sxs-lookup"><span data-stu-id="c1e58-119">Message authentication audit records have a category of "MessageAuthentication" while service authorization audit records have a category of "ServiceAuthorization".</span></span>  
  
 <span data-ttu-id="c1e58-120">İleti, ileti olup süresi doldu ve istemci hizmete olup doğrulanabilir müdahale olup olmadığını ileti kimlik doğrulama denetim olaylarını kapsar.</span><span class="sxs-lookup"><span data-stu-id="c1e58-120">Message authentication audit events cover whether the message was tampered with, whether the message has expired, and whether the client can authenticate to the service.</span></span> <span data-ttu-id="c1e58-121">Kimlik doğrulaması başarılı oldu veya istemci kimlikle birlikte başarısız hakkında bilgi sağlar ve uç nokta ileti ileti ile ilişkili eylem birlikte gönderildi.</span><span class="sxs-lookup"><span data-stu-id="c1e58-121">They provide information about whether the authentication succeeded or failed along with the identity of the client, and the endpoint the message was sent to along with the action associated with the message.</span></span>  
  
 <span data-ttu-id="c1e58-122">Hizmet yetkilendirme denetim olaylarını hizmet Yetkilendirme Yöneticisi tarafından yapılan yetkilendirme kararı kapsar.</span><span class="sxs-lookup"><span data-stu-id="c1e58-122">Service authorization audit events cover the authorization decision made by a service authorization manager.</span></span> <span data-ttu-id="c1e58-123">Olup Yetkilendirme başarılı hakkında bilgi sağlamak veya istemci kimlikle birlikte başarısız oldu, uç nokta ileti, ileti, gelen oluşturulan yetkilendirme Bağlam tanıtıcısı ile ilişkili eylem gönderildi gelen ileti ve erişim kararı Yetkilendirme Yöneticisi'ni türü.</span><span class="sxs-lookup"><span data-stu-id="c1e58-123">They provide information about whether authorization succeeded or failed along with the identity of the client, the endpoint the message was sent to, the action associated with the message, the identifier of the authorization context that was generated from the incoming message, and the type of the authorization manager that made the access decision.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c1e58-124">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="c1e58-124">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c1e58-125">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c1e58-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="c1e58-126">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c1e58-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="c1e58-127">Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c1e58-127">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1e58-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c1e58-128">See Also</span></span>  
 [<span data-ttu-id="c1e58-129">Denetleme</span><span class="sxs-lookup"><span data-stu-id="c1e58-129">Auditing</span></span>](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 [<span data-ttu-id="c1e58-130">Nasıl yapılır: güvenlik olaylarını denetleme</span><span class="sxs-lookup"><span data-stu-id="c1e58-130">How to: Audit Security Events</span></span>](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)
