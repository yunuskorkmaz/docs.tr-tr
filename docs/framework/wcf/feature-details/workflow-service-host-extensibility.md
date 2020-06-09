---
title: İş Akışı Hizmeti Ana Bilgisayar Genişletilebilirliği
ms.date: 03/30/2017
ms.assetid: c0e8f7bb-cb13-49ec-852f-b85d7c23972f
ms.openlocfilehash: 4c2edec8c23e27f019b95223c998c72069384c75
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594900"
---
# <a name="workflow-service-host-extensibility"></a>İş Akışı Hizmeti Ana Bilgisayar Genişletilebilirliği
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)], <xref:System.ServiceModel.Activities.WorkflowServiceHost> iş akışı hizmetlerini barındırmak için sınıfını sağlar. Bu sınıf, yönetilen bir uygulamada veya bir Windows hizmetinde bir iş akışı hizmetini kendiliğinden barındırıyorsanız kullanılır. Bu sınıf, Internet Information Services (IIS) veya Windows Işlem etkinleştirme hizmeti (WAS) ile bir iş akışı hizmeti barındırırken de kullanılır. <xref:System.ServiceModel.Activities.WorkflowServiceHost>Sınıfı, Özel uzantılar eklemenize, boşta davranışını değiştirmenize ve hizmet dışı iş akışlarını (ileti alma etkinliği kullanmayan iş akışları) barındırmanıza olanak sağlayan uzantı noktaları sağlar.  
  
## <a name="workflow-service-host-extensions"></a>İş akışı hizmeti konak uzantıları  
 , ' <xref:System.ServiceModel.Activities.WorkflowServiceHost> A <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager> uzantı eklemek için yöntemler sağlayan türünde bir özelliği içerir <xref:System.ServiceModel.Activities.WorkflowServiceHost> . <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager.Add%2A>Her bir iş akışı hizmeti örneği için bir uzantı eklemek için yöntemini kullanın. Belirtilen temsilci, bir iş akışı hizmet örneği oluşturulduğunda veya bir kalıcılık deposundan yüklendiğinde yeni bir uzantı oluşturmak için çağırılır. Yöntemini kullanarak <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager.Add%2A> her bir iş akışı hizmet ana bilgisayarı için bir uzantı ekleyin, uzantının bir örneği tüm iş akışı hizmeti örnekleri için paylaşılır.  
  
## <a name="react-to-unhandled-exceptions"></a>Işlenmeyen özel durumlara tepki verme  
 , <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> Bir iş akışı hizmeti içinde işlenmeyen bir özel durum oluşursa gerçekleştirilecek eylemi belirtmenizi sağlar. <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior.Action%2A>Özelliği değerlerden birini belirtir <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction> :  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Abandon>– İş akışı hizmeti örneğini iptal eder.  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.AbandonAndSuspend>– Son kalıcı duruma geri döner ve iş akışı hizmeti örneğini askıya alır. Bu yalnızca iş akışı en az bir kez tekrarlanmışsa oluşur. İş akışı örneği durdurulmaz.  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Cancel>– Örneği iptal eder.  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Terminate>– Örneği sonlandırır.  
  
 Bu davranış, aşağıdaki örnekte gösterildiği gibi, kodda yapılandırılabilir.  
  
```csharp  
host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.Abandon });  
```  
  
 Ayrıca, aşağıdaki örnekte gösterildiği gibi bir yapılandırma dosyasında da yapılandırılabilir.  
  
```xml
<behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <workflowUnhandledExceptionBehavior action="Abandon" />
        </behavior>  
      </serviceBehaviors>  
</behaviors>
```  
  
## <a name="hosting-non-service-workflows"></a>Hizmet dışı Iş akışlarını barındırma  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>hizmet dışı iş akışlarını veya <xref:System.ServiceModel.Activities.Receive> ileti oluşturma etkinliklerini kullanmayan bir etkinlik ya da iş akışlarıyla başlamayan iş akışlarını barındırmak için kullanılabilir. İş akışı Hizmetleri normalde bir <xref:System.ServiceModel.Activities.Receive> etkinlikle başlar. <xref:System.ServiceModel.Activities.WorkflowServiceHost>Bir iş akışı hizmeti için bir ileti aldığında, zaten çalışmıyorsa (veya kalıcı), yeni bir iş akışı hizmeti örneği oluşturulur. Bir iş akışı alma etkinliğiyle başlamazsa, iletiyi alacak bir etkinlik olmadığından ileti gönderilerek başlatılamaz. Hizmet dışı bir iş akışını barındırmak için, ve ' den bir sınıf türetebilir ve <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> geçersiz kılın <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A> <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A> <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnResolveBookmark%2A> . <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A>Tercih edilen örnek kimliği sağlamak istiyorsanız bunu geçersiz kılın. <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A>Özel bir iş akışı oluşturma bağlamı oluşturmak veya var olan bir örneğini doldurmak için geçersiz kılın <xref:System.ServiceModel.Activities.WorkflowCreationContext> . <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnResolveBookmark%2A>Gelen iletiden yer işaretini el ile ayıklamak için geçersiz kılın. Bu yöntemi geçersiz kılarsınız, <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> Workflowwhostingendpoint 'e gönderilen iletiye yanıt vermek için gövdesini çağırmanız gerekir. Bunu yapmazsanız, bir <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> sınır en sonunda aşılmış olabilir. İki yönlü sözleşmelerde, <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> istemcinin yanıt alma hatası nedeniyle çağırma başarısızlığını tespit edebilirsiniz. Tek yönlü sözleşmelerde, <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> kısıtlama sınırı aşıldıktan sonra çok geç olana kadar çağrı başarısız olma hatası ' nı tanıyamayabiliriz. Daha fazla bilgi için lütfen [Workflowwhostingendpoint özgeçmişi yer işaretine](../../windows-workflow-foundation/samples/workflowhostingendpoint-resume-bookmark.md)bakın. hizmet olmayan bir iş akışının yeni bir örneğini oluşturmak için yeni bir örnek oluşturan bir işlemi tanımlayan bir hizmet sözleşmesi bildirin. Oluşturma işlemi, \<string, object> gerekli herhangi bir iş akışı parametresini iletmek için bir IDictionary almalıdır. Bu sözleşme, türetilmiş sınıf tarafından örtük olarak uygulanır <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> . İş akışını barındırırken, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> çağırarak ve çağırarak konağa türetilmiş sınıfın bir örneğini ekleyin <xref:System.ServiceModel.Activities.WorkflowServiceHost.AddServiceEndpoint%2A> <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> . İş akışının bir örneğini oluşturmak için, <xref:System.ServiceModel.ChannelFactory%601> hizmet sözleşmesi türü ve çağrısı oluşturun <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> . Ardından, hizmet sözleşmeniz tarafından tanımlanan oluşturma işlemini çağırabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Hizmetleri](workflow-services.md)
- [Mesajlaşma Etkinlikleri](messaging-activities.md)
