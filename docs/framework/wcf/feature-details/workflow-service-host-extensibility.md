---
title: İş Akışı Hizmeti Ana Bilgisayar Genişletilebilirliği
ms.date: 03/30/2017
ms.assetid: c0e8f7bb-cb13-49ec-852f-b85d7c23972f
ms.openlocfilehash: eb35b9211bc55ee66f5bb5600ef86f40d4145191
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464001"
---
# <a name="workflow-service-host-extensibility"></a>İş Akışı Hizmeti Ana Bilgisayar Genişletilebilirliği
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]iş <xref:System.ServiceModel.Activities.WorkflowServiceHost> akışı hizmetlerini barındırma için sınıf sağlar. Bu sınıf, yönetilen bir uygulamada veya Windows hizmetinde kendi kendine barındıran bir iş akışı hizmetinde kullanılır. Bu sınıf, Internet Information Services (IIS) veya Windows Process Etkinleştirme Hizmeti (WAS) ile bir iş akışı hizmeti barındırırken de kullanılır. Sınıf, <xref:System.ServiceModel.Activities.WorkflowServiceHost> özel uzantılar eklemenize, boşta kalan davranışı değiştirmenize ve hizmet dışı iş akışlarını (ileti etkinliklerini kullanmayan iş akışları) barındırmanıza olanak tanıyan uzantı noktaları sağlar.  
  
## <a name="workflow-service-host-extensions"></a>İş Akışı Hizmeti Ana Bilgisayar Uzantıları  
 Bu <xref:System.ServiceModel.Activities.WorkflowServiceHost> tür <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> bir <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager> özellik <xref:System.ServiceModel.Activities.WorkflowServiceHost>içerir. Her <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager.Add%2A> iş akışı hizmeti örneği için bir uzantı eklemek için yöntemi kullanın. Bir iş akışı hizmeti örneği oluşturulduğunda veya kalıcılık deposundan yüklendiğinde, belirtilen temsilci yeni bir uzantı oluşturmak için çağrılır. Her <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager.Add%2A> iş akışı hizmeti ana bilgisayarı için bir uzantı eklemek için yöntemi kullanın, uzantının bir örneği tüm iş akışı hizmeti örnekleri için paylaşılır.  
  
## <a name="react-to-unhandled-exceptions"></a>İşlenmemiş Özel Durumlara Tepki Verme  
 İşlenmemiş <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> bir özel durum bir iş akışı hizmeti içinde oluşursa yapılacak eylemi belirtmenizi sağlar. Özellik <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior.Action%2A> <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction> değerlerden birini belirtir:  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Abandon>– İş akışı hizmeti örneğini iptal eder.  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.AbandonAndSuspend>– Son kalıcı duruma geri döner ve iş akışı hizmeti örneğini askıya alar. Bu yalnızca iş akışı zaten en az bir kez kalıcı olduoluşur. Değilse iş akışı örneği iptal edilir.  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Cancel>– Örneği iptal eder.  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Terminate>– Örneği sona erdirir.  
  
 Bu davranış, aşağıdaki örnekte gösterildiği gibi kod olarak yapılandırılabilir.  
  
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
  
## <a name="hosting-non-service-workflows"></a>Hizmet Dışı İş Akışlarını Barındırma  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>hizmet dışı iş akışlarını veya bir <xref:System.ServiceModel.Activities.Receive> etkinlikle başlamayan iş akışlarını veya ileti etkinliklerini kullanmayan iş akışlarını barındırmak için kullanılabilir. İş akışı hizmetleri normalde <xref:System.ServiceModel.Activities.Receive> bir etkinlikle başlar. İş <xref:System.ServiceModel.Activities.WorkflowServiceHost> akışı hizmeti için bir ileti aldığında, zaten çalışmıyorsa (veya kalıcıysa) yeni bir iş akışı hizmeti örneği oluşturulur. İş akışı Bir Al etkinliğiyle başlamıyorsa, iletiyi alacak etkinliği olmadığından ileti gönderilerek başlatılamaz. Hizmet dışı bir iş akışını barındırmak için, bir <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A> <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A>sınıf <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnResolveBookmark%2A>türetin <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> ve geçersiz kılmak , ve . Tercih <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A> edilen bir örnek kimliği sağlamak istiyorsanız geçersiz kılın. Özel <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A> bir iş akışı oluşturma bağlamı oluşturmak veya varolan <xref:System.ServiceModel.Activities.WorkflowCreationContext>bir örneğini doldurmak için geçersiz kılma. Gelen <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnResolveBookmark%2A> iletideki yer imi'ni el ile ayıklamak için geçersiz kılın. Bu yöntemi geçersiz kılarsanız, <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> WorkflowHostingEndpoint'e gönderilen iletiyi yanıtlamak için gövdesinde çağrıda bulunan gerekir. Bunu yapmazsanız, bir <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> sınır sonunda aşılabilir. Çift yönlü sözleşmelerde, istemcinin yanıt alamaması <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> nedeniyle çağrıda başarısız olduğunuzu algılayabilirsiniz. Tek yönlü sözleşmelerde, <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> gaz sınırı aşıldıktan sonra çok geç olana kadar aramama hatasını fark etmeyebilirsiniz. Daha fazla bilgi için, hizmet dışı iş akışının yeni bir örneğini oluşturmak için [lütfen WorkflowHostingEndpoint Özgeçmiş Kitap İşaretine](../../../../docs/framework/windows-workflow-foundation/samples/workflowhostingendpoint-resume-bookmark.md)bakın, yeni bir örnek oluşturan bir işlem tanımlayan bir hizmet sözleşmesi bildirin. Oluşturma işlemi gerekli iş\<akışı parametrelerini geçmek için bir IDictionary dize, nesne> almalıdır. Bu sözleşme örtülü olarak <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>türetilmiş sınıf tarafından uygulanır. İş akışını barındırırken, arayarak <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>ve arayarak <xref:System.ServiceModel.Activities.WorkflowServiceHost.AddServiceEndpoint%2A> <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>ana bilgisayara türetilmiş sınıfın bir örneğini ekleyin. İş akışının bir örneğini oluşturmak <xref:System.ServiceModel.ChannelFactory%601> için, hizmet sözleşmesi <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A>türünden bir örnek oluşturun ve arayın. Daha sonra hizmet sözleşmenizde tanımlanan oluşturma işlemini arayabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Mesajlaşma Etkinlikleri](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
