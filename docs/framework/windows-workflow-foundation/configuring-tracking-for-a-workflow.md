---
title: İş akışı izlemeyi yapılandırma
ms.date: 03/30/2017
ms.assetid: 905adcc9-30a0-4918-acd6-563f86db988a
ms.openlocfilehash: 70697d82242ab0704dd67129940a6660d300bef9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="configuring-tracking-for-a-workflow"></a>İş akışı izlemeyi yapılandırma
Bir iş akışı üç şekilde çalıştırabilirsiniz:  
  
-   Barındırılan <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
-   Olarak yürütülen bir <xref:System.Activities.WorkflowApplication>  
  
-   Kullanarak doğrudan yürütülebilir. <xref:System.Activities.WorkflowInvoker>  
  
 Barındırma seçeneği iş akışı bağlı olarak, bir izleme katılımcı kodu veya bir yapılandırma dosyası aracılığıyla eklenebilir. Bu konu, bir izleme katılımcı ekleyerek izleme nasıl yapılandırıldığını açıklar bir <xref:System.Activities.WorkflowApplication> ve bir <xref:System.ServiceModel.Activities.WorkflowServiceHost>ve kullanırken izlemeyi etkinleştirme <xref:System.Activities.WorkflowInvoker>.  
  
## <a name="configuring-workflow-application-tracking"></a>İş akışı uygulaması izlemeyi yapılandırma  
 Bir iş akışı kullanarak çalıştırabilirsiniz <xref:System.Activities.WorkflowApplication> sınıfı. Bu konuda izleme için nasıl yapılandırılacağı gösterilmektedir bir [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] izleme Katılımcısı ekleyerek iş akışı uygulaması <xref:System.Activities.WorkflowApplication> iş akışı ana bilgisayarı. Bu durumda, iş akışını bir iş akışı uygulama olarak çalışır. Kendini barındıran .exe olan bir iş akışı uygulama kodlarda (yerine bir yapılandırma dosyası kullanarak), yapılandırma kullanarak dosya <xref:System.Activities.WorkflowApplication> sınıfı. İzleme katılımcı bir Extension olarak eklenen <xref:System.Activities.WorkflowApplication> örneği. Bu ekleyerek yapılır <xref:System.Activities.Tracking.TrackingParticipant> WorkflowApplication örneği için uzantıları koleksiyonuna.  
  
 Bir iş akışı uygulama için eklediğiniz <xref:System.Activities.Tracking.EtwTrackingParticipant> aşağıdaki kodda gösterildiği gibi davranış uzantısı.  
  
```csharp  
LogActivity activity = new LogActivity();  
  
WorkflowApplication instance = new WorkflowApplication(activity);  
EtwTrackingParticipant trackingParticipant =  
    new EtwTrackingParticipant  
{  
  
        TrackingProfile = new TrackingProfile  
           {  
               Name = "SampleTrackingProfile",  
               ActivityDefinitionId = "ProcessOrder",  
               Queries = new WorkflowInstanceQuery  
               {  
                  States = { "*" }  
              }  
          }  
       };  
instance.Extensions.Add(trackingParticipant);  
```  
  
### <a name="configuring-workflow-service-tracking"></a>İzleme iş akışı hizmeti yapılandırma  
 Bir iş akışı olarak kullanıma sunulabilecek bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmeti barındırılan olduğunda <xref:System.ServiceModel.Activities.WorkflowServiceHost> hizmet ana bilgisayarı. <xref:System.ServiceModel.Activities.WorkflowServiceHost> bir iş akışı tabanlı hizmet için özelleştirilmiş bir .NET ServiceHost uygulama işlemidir. Bu bölümde, izleme için yapılandırmak açıklanmaktadır bir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] iş akışı hizmeti çalışır durumda <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Bir Web.config dosyası (bir Web barındırılan hizmeti) veya bir App.config dosyası (bir konsol uygulaması gibi tek başına bir uygulamadaki barındırılan hizmeti) yoluyla bir hizmet davranışı belirterek veya bu kod aracılığıyla bir izleme özgü davranış ekleyerek yapılandırıldığı <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> hizmet ana bilgisayarı koleksiyonu.  
  
 Bir iş akışı hizmeti barındırılan için <xref:System.ServiceModel.WorkflowServiceHost>, ekleyebileceğiniz <xref:System.Activities.Tracking.EtwTrackingParticipant> kullanarak <`behavior`> öğesi aşağıdaki örnekte gösterildiği gibi bir yapılandırma dosyası.  
  
```xml  
<behaviors>  
   <serviceBehaviors>  
        <behavior>  
          <etwTracking profileName="Sample Tracking Profile" />  
        </behavior>              
   </serviceBehaviors>  
<behaviors>  
```  
  
 Alternatif olarak, bir iş akışı hizmeti için barındırılan <xref:System.ServiceModel.WorkflowServiceHost>, ekleyebileceğiniz <xref:System.Activities.Tracking.EtwTrackingParticipant> kodlarda davranış uzantısı. Özel İzleme Katılımcı eklemek için yeni bir davranış uzantısı oluşturun ve ekleyin <xref:System.ServiceModel.ServiceHost> aşağıdaki örnek kodda gösterildiği gibi.  
  
> [!NOTE]
>  Özel İzleme katılımcı ekler özel davranış öğesi oluşturmayı gösteren örnek kod görüntülemek istiyorsanız, başvurmak [izleme](../../../docs/framework/windows-workflow-foundation/samples/tracking.md) örnekleri.  
  
```  
ServiceHost svcHost = new ServiceHost(typeof(WorkflowService), new   
                                 Uri("http://localhost:8001/Sample"));  
EtwTrackingBehavior trackingBehavior =   
    new EtwTrackingBehavior  
    {  
        ProfileName = "Sample Tracking Profile"  
    };  
svcHost.Description.Behaviors.Add(trackingBehavior);  
svcHost.Open();  
```  
  
 İzleme katılımcı iş akışı hizmeti ana bilgisayarı için davranış bir uzantısı olarak eklenir.  
  
 Bu örnek kod, bir izleme profili yapılandırma dosyasından okunur gösterilmektedir.  
  
```  
TrackingProfile GetProfile(string profileName, string displayName)  
        {  
            TrackingProfile trackingProfile = null;  
            TrackingSection trackingSection = (TrackingSection)WebConfigurationManager.GetSection("system.serviceModel/tracking");  
            if (trackingSection == null)   
            {  
                return null;  
            }  
  
            if (profileName == null)   
            {  
                profileName = "";  
            }  
  
            //Find the profile with the specified profile name in the list of profile found in config  
            var match = from p in new List<TrackingProfile>(trackingSection.TrackingProfiles)  
                        where (p.Name == profileName) && ((p.ActivityDefinitionId == displayName) || (p.ActivityDefinitionId == "*"))  
                        select p;  
  
            if (match.Count() == 0)  
            {  
                //return an empty profile  
                trackingProfile = new TrackingProfile()  
                {  
                    ActivityDefinitionId = displayName  
                };  
  
            }  
            else  
            {  
                trackingProfile = match.First();  
            }  
  
            return trackingProfile;  
```  
  
 Bu örnek kod, bir iş akışı ana bilgisayarı için izleme profili eklemek gösterilmiştir.  
  
```  
WorkflowServiceHost workflowServiceHost = serviceHostBase as WorkflowServiceHost;  
if (null != workflowServiceHost)  
{  
              string workflowDisplayName = workflowServiceHost.Activity.DisplayName;  
               TrackingProfile trackingProfile = GetProfile(this.profileName, workflowDisplayName);  
                workflowServiceHost.WorkflowExtensions.Add(()  => new EtwTrackingParticipant  {  
               TrackingProfile = trackingProfile  
                        });  
 }  
```  
  
> [!NOTE]
>  Profilleri izleme ile ilgili daha fazla bilgi için başvurmak [izleme profilleri](http://go.microsoft.com/fwlink/?LinkId=201310).  
  
### <a name="configuring-tracking-using-workflowinvoker"></a>WorkflowInvoker kullanarak izlemeyi yapılandırma  
 İzleme kullanılarak yürütülen iş akışı için yapılandırmak için <xref:System.Activities.WorkflowInvoker>, bir Extension olarak İzleme Sağlayıcısı Ekle bir <xref:System.Activities.WorkflowInvoker> örneği. Aşağıdaki kod örneğinde arasındadır [özel izleme](../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) örnek.  
  
```  
WorkflowInvoker invoker = new WorkflowInvoker(BuildSampleWorkflow());  
invoker.Extensions.Add(customTrackingParticipant);  
invoker.Invoke();  
```  
  
### <a name="viewing-tracking-records-in-event-viewer"></a>Olay Görüntüleyicisi'nde kayıtları izleme görüntüleme  
 WF yürütme - analitik günlüğünü ve hata ayıklama günlüğünü izlerken görüntülemek için özellikle ilgisini çeken iki Olay Görüntüleyicisi günlükleri vardır. Her ikisi de Microsoft altında bulunan&#124;Windows&#124;uygulama uygulamalarının düğümü.  Bu bölümde günlüklere tek bir uygulama olayları yerine tüm sistem üzerinde bir etkisi olaylarını içerir.  
  
 Hata ayıklama izleme olayları için hata ayıklama günlüğüne yazılır. Olay Görüntüleyicisi'nde WF hata ayıklama izleme olaylarını toplamak için hata ayıklama günlüğünü etkinleştirin.  
  
1.  Olay Görüntüleyicisi'ni açmak için **Başlat**ve ardından **çalıştırın.** Çalıştır iletişim kutusuna `eventvwr`.  
  
2.  Olay Görüntüleyicisi'ni iletişim kutusunda genişletin **uygulama ve hizmet günlükleri** düğümü.  
  
3.  Genişletme **Microsoft**, **Windows**, ve **uygulama uygulamalarının** düğümleri.  
  
4.  Sağ **hata ayıklama** düğümü altında **uygulama uygulamalarının** düğümü ve seçin **günlüğü etkinleştir**.  
  
5.  İzleme olayları oluşturmak için izleme etkinleştirilmiş uygulamanız yürütün.  
  
6.  Sağ **hata ayıklama** düğümü ve select **yenileyin.** Olayları izleme Orta bölmede görünür olmalıdır.  
  
 WF 4 izleme kayıtları ETW (Windows için olay izleme) oturumuna Yazar izleme katılımcı sağlar. ETW İzleme katılımcı kayıtları izleme için abone olmak için izleme profili ile yapılandırılır.  İzleme etkinleştirildiğinde, kayıtları izleme hataları için ETW gösterilen. ETW olayları (100 113 aralığını arasında) izleme ETW İzleme katılımcı tarafından gösterilen izleme olaylarını karşılık gelen yazılır analitik günlük.  
  
 İzleme kayıtları görüntülemek için aşağıdaki adımları izleyin.  
  
1.  Olay Görüntüleyicisi'ni açmak için **Başlat**ve ardından **çalıştırın.** Çalıştır iletişim kutusuna `eventvwr`.  
  
2.  Olay Görüntüleyicisi'ni iletişim kutusunda genişletin **uygulama ve hizmet günlükleri** düğümü.  
  
3.  Genişletme **Microsoft**, **Windows**, ve **uygulama uygulamalarının** düğümleri.  
  
4.  Sağ **analitik** düğümü altında **uygulama uygulamalarının** düğümü ve Seç **günlüğü etkinleştir**.  
  
5.  İzleme kayıtları oluşturmak için izleme etkinleştirilmiş uygulamanız yürütün.  
  
6.  Sağ **analitik** düğümü ve select **yenileyin.** Kayıtları İzleme Orta bölmede görünür olmalıdır.  
  
 Aşağıdaki resimde, Olay Görüntüleyicisi'nde izleme olayları gösterir.  
  
 ![Olay Görüntüleyicisi'ni gösteren kayıtları izleme](../../../docs/framework/windows-workflow-foundation/media/trackingeventviewer.PNG "TrackingEventViewer")  
  
### <a name="registering-an-application-specific-provider-id"></a>Bir uygulamaya özgü sağlayıcı kimliği kaydediliyor  
 Olayları belirli uygulama günlüğüne yazılması gerekiyorsa, yeni bir sağlayıcı bildirimi kaydetmek için şu adımları izleyin.  
  
1.  Uygulama yapılandırma dosyasında sağlayıcı kimliği bildirin.  
  
    ```xml  
    <system.serviceModel>  
        <diagnostics etwProviderId="2720e974-9fe9-477a-bb60-81fe3bf91eec"/>  
    </system.serviceModel>  
    ```  
  
2.  %Windir%\Microsoft.NET\Framework bildirim dosyasını kopyalamak\\< en son sürümünü [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]> \Microsoft.Windows.ApplicationServer.Applications.man geçici bir konuma ve ona yeniden adlandırın Microsoft.Windows.ApplicationServer.Applications_Provider1.man  
  
3.  Bildirim dosyasında GUID için yeni bir GUID değiştirin.  
  
    ```xml  
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}"  
    ```  
  
4.  Varsayılan sağlayıcıyı kaldırmak istemiyorsanız sağlayıcı adını değiştirin.  
  
    ```xml  
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}"  
    ```  
  
5.  Önceki adımda sağlayıcı adı değişirse, bildirim dosyasındaki kanal adlarını yeni sağlayıcı adı değiştirin.  
  
    ```xml  
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Admin" chid="ADMIN_CHANNEL" symbol="ADMIN_CHANNEL" type="Admin" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ADMIN_CHANNEL.message)" />  
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Operational" chid="OPERATIONAL_CHANNEL" symbol="OPERATIONAL_CHANNEL" type="Operational" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.OPERATIONAL_CHANNEL.message)" />  
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" />  
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Debug" chid="DEBUG_CHANNEL" symbol="DEBUG_CHANNEL" type="Debug" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.DEBUG_CHANNEL.message)" />  
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Perf" chid="PERF_CHANNEL" symbol="PERF_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.PERF_CHANNEL.message)" />  
    ```  
  
6.  Kaynak DLL'si, aşağıdaki adımları izleyerek oluşturun.  
  
    1.  Windows SDK yükleyin. İleti Derleyicisi Windows SDK'sı içerir ([mc.exe](http://go.microsoft.com/fwlink/?LinkId=184606)) ve kaynak derleyicisi ([rc.exe](http://go.microsoft.com/fwlink/?LinkId=184605)).  
  
    2.  Bir Windows SDK komut istemi mc.exe yeni bildirim dosyasını çalıştırın.  
  
        ```  
        mc.exe Microsoft.Windows.ApplicationServer.Applications_Provider1.man  
        ```  
  
    3.  Önceki adımda oluşturulan kaynak dosyada RC.exe çalıştırın.  
  
        ```  
        rc.exe  Microsoft.Windows.ApplicationServer.Applications_Provider1.rc  
        ```  
  
    4.  NewProviderReg.cs adlı bir boş cs dosyası oluşturun.  
  
    5.  Bir kaynak DLL'si C# Derleyici kullanarak oluşturun.  
  
        ```  
        csc /target:library /win32res:Microsoft.Windows.ApplicationServer.Applications_Provider1.res NewProviderReg.cs /out:Microsoft.Windows.ApplicationServer.Applications_Provider1.dll  
        ```  
  
    6.  Kaynak ve ileti dl namel bildirim dosyasında değişiklik `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` yeni dll adı.  
  
        ```xml  
        <provider name="Microsoft-Windows-Application Server-Applications_Provider1" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" symbol="Microsoft_Windows_ApplicationServer_ApplicationEvents" resourceFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll" messageFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll">  
        ```  
  
    7.  Kullanım [wevtutil](http://go.microsoft.com/fwlink/?LinkId=184608) bildirim kaydetmek için.  
  
        ```  
        wevtutil im Microsoft.Windows.ApplicationServer.Applications_Provider1.man  
        ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Server App Fabric izleme](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [App Fabric ile uygulamaları izleme](http://go.microsoft.com/fwlink/?LinkId=201275)
