---
title: İş Akışı Hizmeti Konak Genişletilebilirliği
ms.date: 03/30/2017
ms.assetid: c0e8f7bb-cb13-49ec-852f-b85d7c23972f
ms.openlocfilehash: 68e7c81d63e6358d90f801cc4480409314821858
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54649875"
---
# <a name="workflow-service-host-extensibility"></a>İş Akışı Hizmeti Konak Genişletilebilirliği
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] sağlar <xref:System.ServiceModel.Activities.WorkflowServiceHost> iş akışı hizmetlerini barındırma için sınıf. Bu sınıf, kendi kendine yönetilen bir uygulamada bir iş akışı hizmeti veya bir Windows hizmet barındırıyorsanız kullanılır. Bu sınıf, Internet Information Services (IIS) veya Windows İşlem Etkinleştirme Hizmeti (WAS) ile bir iş akışı hizmeti barındırma olduğunda da kullanılır. <xref:System.ServiceModel.Activities.WorkflowServiceHost> Sınıfı özel uzantıları eklemeyi uzantı noktaları boşta davranışı değiştirmek ve ana bilgisayar, hizmet olmayan iş akışları (Mesajlaşma etkinlikleri kullanmayın iş akışları) sağlar.  
  
## <a name="workflow-service-host-extensions"></a>İş akışı hizmeti konak uzantıları  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost> İçeren bir <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> türünün özelliği <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager> uzantısı eklemek için yöntemler sağlar <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Kullanım <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager.Add%2A> her iş akışı hizmet örneği için bir uzantı ekleme yöntemi. Belirtilen temsilci, bir iş akışı hizmet örneği oluşturulduğunda veya sürdürme deposundan yüklendi, yeni bir uzantı oluşturma için çağrılır. Kullanım <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager.Add%2A> her iş akışı hizmeti konağı için bir uzantı ekleme yöntemi bir uzantı örneği için tüm iş akışı hizmet örneklerine paylaşılır.  
  
## <a name="react-to-unhandled-exceptions"></a>İşlenmeyen özel durumlar için react  
 <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> Bir iş akışı hizmeti içinde işlenmeyen bir özel durum oluşursa yapılacak eylem belirtmenize olanak sağlar. <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior.Action%2A> Özellik birini belirtir <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction> değerleri:  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Abandon> – İş akışı hizmet örneği durdurur.  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.AbandonAndSuspend> – Geri son kalıcı duruma alır ve iş akışı hizmet örneği askıya alır. Bu yalnızca, iş akışının zaten en az bir kez kalıcı yapılmadı oluşur. Aksi durumda iş akışı örneği iptal edildi.  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Cancel> – Örneği iptal eder.  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Terminate> – Örneği sonlandırır.  
  
 Bu davranış, aşağıdaki örnekte gösterildiği gibi kodda yapılandırılabilir.  
  
```csharp  
host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.Abandon });  
```  
  
 Ayrıca bir yapılandırma dosyasında aşağıdaki örnekte gösterilen şekilde yapılandırılabilir.  
  
```xml
<behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <workflowUnhandledExceptionBehavior action="Abandon" />        
        </behavior>  
      </serviceBehaviors>  
```  
  
## <a name="hosting-non-service-workflows"></a>Hizmet olmayan iş akışları barındırma  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost> Hizmet olmayan iş akışları veya ya da ile başlamayan iş akışlarını barındırmak için kullanılan bir <xref:System.ServiceModel.Activities.Receive> etkinlik veya ileti etkinlikleri kullanan değil iş akışları. İş akışı Hizmetleri ile normalde başlayan bir <xref:System.ServiceModel.Activities.Receive> etkinlik. Zaman <xref:System.ServiceModel.Activities.WorkflowServiceHost> bir iş akışı hizmeti için bir ileti alır, zaten yürütülmekte olmadığını (veya kalıcı) yeni bir iş akışı hizmeti örneği oluşturulur. Bir iş akışı Al etkinliği ile başlamıyorsa iletisi için hiçbir etkinlik olmadığı için bir ileti göndererek başlatılamıyor. Bir hizmet olmayan iş akışı barındırma için öğesinden bir sınıf türetin <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> ve geçersiz kılma <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A>, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A>, ve <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnResolveBookmark%2A>. Geçersiz kılma <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A> bir tercih edilen örneği kimliği sağlamak istiyorsanız Geçersiz kılma <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A> bir özel iş akışı oluşturma bağlamı oluşturur veya mevcut bir örneğini doldurmak için <xref:System.ServiceModel.Activities.WorkflowCreationContext>. Geçersiz kılma <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnResolveBookmark%2A> el ile gelen ileti yer işareti ayıklamak için. Bu yöntemi geçersiz kılarsanız, çağırmalıdır <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> gövdesinde WorkflowHostingEndpoint için gönderilen ileti yanıt koyabilir. Bunu yapmak, bir <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> sonunda sayıyı aştı. Çift yönlü sözleşmeler çağırmak için hata algılayabilir olabilir <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> bir yanıt almak için istemci hatası nedeniyle. Tek yönlü sözleşmeler çağırmak başarısız, hata algılamayabilir <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> sonra çok geç olana kadar <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> kısıtlama sınırı aşıldı. Daha fazla bilgi için lütfen bkz [WorkflowHostingEndpoint sürdürme yer işareti](../../../../docs/framework/windows-workflow-foundation/samples/workflowhostingendpoint-resume-bookmark.md)hizmet olmayan iş akışı yeni bir örneğini oluşturmak için yeni bir örneğini oluşturan bir işlemi tanımlayan bir hizmet sözleşmesini bildirin. Idictionary'ye oluşturma işlemi gerçekleştirmesi gereken\<dize, Nesne > herhangi geçirmek için iş akışı parametreleri gereklidir. Bu sözleşme örtük olarak tarafından uygulanan <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>-türetilmiş sınıf. İş akışı barındırma, bir örneğini ekleme <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>-türetilmiş sınıf konağa çağırarak <xref:System.ServiceModel.Activities.WorkflowServiceHost.AddServiceEndpoint%2A> ve çağrı <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. İş akışı örneği oluşturmak için bir <xref:System.ServiceModel.ChannelFactory%601> hizmet sözleşme türü ve çağrı <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A>. Ardından, hizmet sözleşmesi içerisinde tanımlanan oluşturma işlemi çağırabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Mesajlaşma Etkinlikleri](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
