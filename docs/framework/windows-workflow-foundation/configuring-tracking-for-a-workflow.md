---
title: Bir iş akışı için izlemeyi yapılandırma
ms.date: 03/30/2017
ms.assetid: 905adcc9-30a0-4918-acd6-563f86db988a
ms.openlocfilehash: ae6b61bf572da1757920b737b03861c891637f51
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43519707"
---
# <a name="configuring-tracking-for-a-workflow"></a>Bir iş akışı için izlemeyi yapılandırma
Bir iş akışı, üç şekilde yürütebilirsiniz:  
  
-   Barındırılan <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
-   Olarak yürütülen bir <xref:System.Activities.WorkflowApplication>  
  
-   Kullanarak doğrudan yürütüldü <xref:System.Activities.WorkflowInvoker>  
  
 Barındırma seçeneği iş akışı bağlı olarak, bir izleme katılımcı, kod veya yapılandırma dosyası aracılığıyla eklenebilir. Bu konu, izleme için izleme katılımcı ekleyerek nasıl yapılandırıldığını açıklar. bir <xref:System.Activities.WorkflowApplication> ve bir <xref:System.ServiceModel.Activities.WorkflowServiceHost>ve kullanırken izlemeyi etkinleştirme <xref:System.Activities.WorkflowInvoker>.  
  
## <a name="configuring-workflow-application-tracking"></a>İzleme iş akışı uygulamasını yapılandırma  
 Bir iş akışı kullanarak çalıştırabilirsiniz <xref:System.Activities.WorkflowApplication> sınıfı. Bu konuda izleme için nasıl yapılandırıldığını gösterir. bir [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] iş akışı uygulama için izleme katılımcı ekleyerek <xref:System.Activities.WorkflowApplication> iş akışı ana bilgisayarı. Bu durumda, iş akışını bir iş akışı uygulaması çalışır. Şirket içinde barındırılan bir .exe olan bir iş akışı uygulama kodu (yerine bir yapılandırma dosyası kullanarak), yapılandırma dosyası kullanarak <xref:System.Activities.WorkflowApplication> sınıfı. İzleme katılımcı bir uzantısı olarak eklenmiş <xref:System.Activities.WorkflowApplication> örneği. Bu ekleyerek yapılır <xref:System.Activities.Tracking.TrackingParticipant> WorkflowApplication örneği için uzantıları koleksiyonu.  
  
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
  
### <a name="configuring-workflow-service-tracking"></a>Yapılandırma iş akışı hizmeti izleme  
 Bir iş akışı içinde barındırıldığında, bir WCF hizmeti olarak kullanıma sunulabilecek <xref:System.ServiceModel.Activities.WorkflowServiceHost> hizmet ana bilgisayarı. <xref:System.ServiceModel.Activities.WorkflowServiceHost> özel bir .NET ServiceHost uygulama iş akışı tabanlı bir hizmet için geçerlidir. Bu bölümde izleme için yapılandırma açıklanmaktadır bir [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] çalışan iş akışı hizmeti <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Bu bir Web.config dosyası (bir Web barındırılan hizmeti) veya bir App.config dosyası (bir hizmeti bir konsol uygulaması gibi bir tek başına uygulama içinde barındırılan) aracılığıyla bir hizmet davranışını belirterek veya kod için bir izleme özgü davranışı ekleyerek yapılandırılır <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> koleksiyonu hizmet ana bilgisayarı.  
  
 Barındırılan bir iş akışı hizmeti için <xref:System.ServiceModel.WorkflowServiceHost>, ekleyebileceğiniz <xref:System.Activities.Tracking.EtwTrackingParticipant> kullanarak <`behavior`> öğesinde aşağıdaki örnekte gösterildiği gibi bir yapılandırma dosyası.  
  
```xml  
<behaviors>  
   <serviceBehaviors>  
        <behavior>  
          <etwTracking profileName="Sample Tracking Profile" />  
        </behavior>              
   </serviceBehaviors>  
<behaviors>  
```  
  
 Alternatif olarak, bir iş akışı hizmeti için barındırılan <xref:System.ServiceModel.WorkflowServiceHost>, ekleyebileceğiniz <xref:System.Activities.Tracking.EtwTrackingParticipant> kod aracılığıyla davranış uzantısı. Özel İzleme Katılımcı eklemek için yeni bir davranış uzantısı oluşturun ve eklemek <xref:System.ServiceModel.ServiceHost> aşağıdaki örnekte gösterildiği gibi.  
  
> [!NOTE]
>  Özel İzleme katılımcı ekleyen bir özel davranış öğesi oluşturmak nasıl gösteren örnek kodunu görüntülemek istiyorsanız, başvurmak [izleme](../../../docs/framework/windows-workflow-foundation/samples/tracking.md) örnekleri.  
  
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
  
 İzleme katılımcı için iş akışı hizmeti konağı davranışı için bir genişletme olarak eklenir.  
  
 Bu örnek kod, bir izleme profili yapılandırma dosyasından okuma işlemi gösterilmektedir.  
  
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
  
 Bu örnek kod, bir iş akışı ana bilgisayarı için bir izleme profili ekleme işlemi gösterilmektedir.  
  
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
>  İzleme profilleri ile ilgili daha fazla bilgi için [izleme profilleri](https://go.microsoft.com/fwlink/?LinkId=201310).  
  
### <a name="configuring-tracking-using-workflowinvoker"></a>Workflowınvoker kullanarak izlemeyi yapılandırma  
 İzleme kullanarak çalıştırılan bir iş akışı için yapılandırmak için <xref:System.Activities.WorkflowInvoker>, izleme sağlayıcısı için bir genişletme olarak ekleme bir <xref:System.Activities.WorkflowInvoker> örneği. Aşağıdaki kod örneği dandır [özel izleme](../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) örnek.  
  
```  
WorkflowInvoker invoker = new WorkflowInvoker(BuildSampleWorkflow());  
invoker.Extensions.Add(customTrackingParticipant);  
invoker.Invoke();  
```  
  
### <a name="viewing-tracking-records-in-event-viewer"></a>Olay Görüntüleyicisi'nde kayıtları izleme görüntüleme  
 Analitik günlüğünü ve hata ayıklama günlüğünü WF yürütme - izleme zaman görüntülemek için belirli ilgilenilen iki Olay Görüntüleyicisi günlükleri vardır. Hem de Microsoft altında bulunan&#124;Windows&#124;uygulama uygulamalarının düğümü.  Bu bölümde günlüklere tek bir uygulama olayları yerine tüm sistem üzerinde bir etkisi olan olayları içerir.  
  
 Hata ayıklama izleme olayları hata ayıklama günlüğüne yazılır. Olay Görüntüleyicisi'nde WF hata ayıklama izleme olaylarını toplamak için hata ayıklama günlüğünü etkinleştirin.  
  
1.  Olay Görüntüleyicisi'ni açmak için **Başlat**ve ardından **çalıştırın.** Çalıştır iletişim kutusuna `eventvwr`.  
  
2.  Olay Görüntüleyicisi'ni iletişim kutusunda Genişlet **uygulama ve hizmet günlükleri** düğümü.  
  
3.  Genişletin **Microsoft**, **Windows**, ve **uygulama uygulamalarının** düğümleri.  
  
4.  Sağ **hata ayıklama** düğümü altında **uygulama uygulamalarının** düğüm ve select **günlüğü etkinleştir**.  
  
5.  İzlemenin etkin uygulamanızı izleme olayları oluşturmak üzere yürütün.  
  
6.  Sağ **hata ayıklama** düğümünü seçip alt **yenileyin.** Olayları izleme Orta bölmede görünür olmalıdır.  
  
 WF 4, izleme kayıtları bir ETW (olay izleme için Windows) oturumu Yazar izleme katılımcı sağlar. ETW İzleme katılımcı abone izleme kayıtları için bir izleme profili ile yapılandırılır.  İzleme etkin olduğunda, hataları kayıtları izleme için ETW gönderilir. ETW olayları (100 113 aralığını arasında) izleme ETW İzleme katılımcı tarafından yayılan izleme olaylarını karşılık gelen yazılmış analitik günlüğü için.  
  
 İzleme kayıtları görüntülemek için aşağıdaki adımları izleyin.  
  
1.  Olay Görüntüleyicisi'ni açmak için **Başlat**ve ardından **çalıştırın.** Çalıştır iletişim kutusuna `eventvwr`.  
  
2.  Olay Görüntüleyicisi'ni iletişim kutusunda Genişlet **uygulama ve hizmet günlükleri** düğümü.  
  
3.  Genişletin **Microsoft**, **Windows**, ve **uygulama uygulamalarının** düğümleri.  
  
4.  Sağ **analitik** düğümünde **uygulama uygulamalarının** düğüm ve Seç **günlüğü etkinleştir**.  
  
5.  İzleme etkinleştirilmiş uygulamanızı izleme kayıtları oluşturmak için yürütün.  
  
6.  Sağ **analitik** düğümünü seçip alt **yenileyin.** Kayıtları İzleme Orta bölmede görünür olmalıdır.  
  
 Aşağıdaki görüntüde, Olay Görüntüleyicisi'nde izleme olayları gösterir.  
  
 ![Kayıtları İzleme Olay Görüntüleyicisi'ni gösteren](../../../docs/framework/windows-workflow-foundation/media/trackingeventviewer.PNG "TrackingEventViewer")  
  
### <a name="registering-an-application-specific-provider-id"></a>Bir uygulamaya özgü sağlayıcı kimliği kaydediliyor  
 Olayları bir belirli uygulama günlüğüne yazılması gerekirse, yeni sağlayıcı bildirimi kaydetmek için şu adımları izleyin.  
  
1.  Sağlayıcı Kimliği uygulama yapılandırma dosyasında bildirin.  
  
    ```xml  
    <system.serviceModel>  
        <diagnostics etwProviderId="2720e974-9fe9-477a-bb60-81fe3bf91eec"/>  
    </system.serviceModel>  
    ```  
  
2.  Bildirim dosyası %windir%\Microsoft.NET\Framework kopyalayın\\< en son sürümünü [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]> \Microsoft.Windows.ApplicationServer.Applications.man geçici bir konuma ve yeniden adlandırın Microsoft.Windows.ApplicationServer.Applications_Provider1.man  
  
3.  Bildirim dosyasında GUID, yeni bir GUID ile değiştirin.  
  
    ```xml  
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}"  
    ```  
  
4.  Varsayılan sağlayıcıyı kaldırmak istemiyorsanız sağlayıcı adını değiştirin.  
  
    ```xml  
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}"  
    ```  
  
5.  Sağlayıcı adı önceki adımda değiştirdiyseniz, bildirim dosyasında kanal adları yeni sağlayıcı ad ile değiştirin.  
  
    ```xml  
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Admin" chid="ADMIN_CHANNEL" symbol="ADMIN_CHANNEL" type="Admin" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ADMIN_CHANNEL.message)" />  
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Operational" chid="OPERATIONAL_CHANNEL" symbol="OPERATIONAL_CHANNEL" type="Operational" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.OPERATIONAL_CHANNEL.message)" />  
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" />  
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Debug" chid="DEBUG_CHANNEL" symbol="DEBUG_CHANNEL" type="Debug" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.DEBUG_CHANNEL.message)" />  
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Perf" chid="PERF_CHANNEL" symbol="PERF_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.PERF_CHANNEL.message)" />  
    ```  
  
6.  Aşağıdaki adımları izleyerek kaynak DLL'si oluşturur.  
  
    1.  Windows SDK'sını yükleyin. Windows SDK'sı ileti derleyicisi içerir ([mc.exe](https://go.microsoft.com/fwlink/?LinkId=184606)) ve kaynak derleyicisi ([rc.exe](https://go.microsoft.com/fwlink/?LinkId=184605)).  
  
    2.  Windows SDK Komut İstemi'nde mc.exe yeni bildirim dosyasını çalıştırın.  
  
        ```  
        mc.exe Microsoft.Windows.ApplicationServer.Applications_Provider1.man  
        ```  
  
    3.  Önceki adımda oluşturulan kaynak dosyada RC.exe çalıştırın.  
  
        ```  
        rc.exe  Microsoft.Windows.ApplicationServer.Applications_Provider1.rc  
        ```  
  
    4.  NewProviderReg.cs adlı bir boş cs dosyası oluşturun.  
  
    5.  Bir kaynak DLL'si C# derleyicisi kullanarak oluşturun.  
  
        ```  
        csc /target:library /win32res:Microsoft.Windows.ApplicationServer.Applications_Provider1.res NewProviderReg.cs /out:Microsoft.Windows.ApplicationServer.Applications_Provider1.dll  
        ```  
  
    6.  Kaynak ve ileti dl namel bildirim dosyasında değişiklik `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` yeni dll adı.  
  
        ```xml  
        <provider name="Microsoft-Windows-Application Server-Applications_Provider1" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" symbol="Microsoft_Windows_ApplicationServer_ApplicationEvents" resourceFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll" messageFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll">  
        ```  
  
    7.  Kullanım [wevtutil](https://go.microsoft.com/fwlink/?LinkId=184608) bildirim kaydedilecek.  
  
        ```  
        wevtutil im Microsoft.Windows.ApplicationServer.Applications_Provider1.man  
        ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Server App Fabric izleme](https://go.microsoft.com/fwlink/?LinkId=201273)  
 [App Fabric ile uygulamaları izleme](https://go.microsoft.com/fwlink/?LinkId=201275)
