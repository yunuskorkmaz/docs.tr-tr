---
title: İş Akışı için İzlemeyi Yapılandırma
ms.date: 03/30/2017
ms.assetid: 905adcc9-30a0-4918-acd6-563f86db988a
ms.openlocfilehash: 5ec94d6b8e58012d0c5c8ca8593c3cef81cd9ec3
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80248218"
---
# <a name="configuring-tracking-for-a-workflow"></a>İş Akışı için İzlemeyi Yapılandırma

İş akışı üç şekilde yürütülebilir:

- Barındırılan<xref:System.ServiceModel.Activities.WorkflowServiceHost>

- Bir olarak yürütülür<xref:System.Activities.WorkflowApplication>

- Doğrudan kullanılarak yürütülür<xref:System.Activities.WorkflowInvoker>

İş akışı barındırma seçeneğine bağlı olarak, bir izleme katılımcısı kod veya yapılandırma dosyası aracılığıyla eklenebilir. Bu konu, bir izleme katılımcısı ve bir <xref:System.Activities.WorkflowApplication> <xref:System.ServiceModel.Activities.WorkflowServiceHost>,'ye ekleyerek izlemenin nasıl <xref:System.Activities.WorkflowInvoker>yapılandırıldığı ve kullanırken izlemeyi nasıl etkinleştireceklerini açıklar.

## <a name="configuring-workflow-application-tracking"></a>İş Akışı Uygulama Takibini Yapılandırma

İş akışı <xref:System.Activities.WorkflowApplication> sınıfı kullanarak çalıştırılabilir. Bu konu, iş akışı ana [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] bilgisayara bir izleme katılımcısı <xref:System.Activities.WorkflowApplication> ekleyerek bir iş akışı uygulaması için izlemenin nasıl yapılandırıldığı gösteriş gösterir. Bu durumda, iş akışı bir iş akışı uygulaması olarak çalışır. İş akışı <xref:System.Activities.WorkflowApplication> uygulamasını, sınıfı kullanarak kendi kendine barındırılan bir .exe dosyası olan kod (yapılandırma dosyası kullanmak yerine) aracılığıyla yapılandırAbilirsiniz. İzleme <xref:System.Activities.WorkflowApplication> katılımcısı, örneğin uzantısı olarak eklenir. Bu, İş Akışı <xref:System.Activities.Tracking.TrackingParticipant> Uygulaması örneği için uzantılar koleksiyonuna eklenerek yapılır.

İş akışı uygulaması için, davranış <xref:System.Activities.Tracking.EtwTrackingParticipant> uzantısını aşağıdaki kodda gösterildiği gibi ekleyebilirsiniz.

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

### <a name="configuring-workflow-service-tracking"></a>İş Akışı Hizmeti Takibini Yapılandırma

İş <xref:System.ServiceModel.Activities.WorkflowServiceHost> akışı, hizmet ana bilgisayarda barındırıldığında WCF hizmeti olarak ortaya çıkabilir. <xref:System.ServiceModel.Activities.WorkflowServiceHost>iş akışı tabanlı bir hizmet için özel bir .NET ServiceHost uygulamasıdır. Bu bölümde, 'de [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <xref:System.ServiceModel.Activities.WorkflowServiceHost>çalışan bir iş akışı hizmeti için izlemenin nasıl yapılandırılabildiğini açıklamaktadır. Bir hizmet davranışı belirterek veya hizmet barındırıcı için <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> koleksiyona izlemeye özgü bir davranış ekleyerek Web.config dosyası (Web barındırılan bir hizmet için) veya App.config dosyası (konsol uygulaması gibi tek başına bir uygulamada barındırılan bir hizmet için) aracılığıyla yapılandırılır.

Barındırılan bir iş <xref:System.ServiceModel.WorkflowServiceHost>akışı hizmeti <xref:System.Activities.Tracking.EtwTrackingParticipant> için, `behavior` aşağıdaki örnekte gösterildiği gibi, yapılandırma dosyasında <> öğesini kullanarak ekleyebilirsiniz.

```xml
<behaviors>
   <serviceBehaviors>
        <behavior>
          <etwTracking profileName="Sample Tracking Profile" />
        </behavior>
   </serviceBehaviors>
</behaviors>
```

Alternatif olarak, barındırılan bir <xref:System.ServiceModel.WorkflowServiceHost>iş akışı <xref:System.Activities.Tracking.EtwTrackingParticipant> hizmeti için, davranış uzantısını kod aracılığıyla ekleyebilirsiniz. Özel bir izleme katılımcısı eklemek için yeni bir <xref:System.ServiceModel.ServiceHost> davranış uzantısı oluşturun ve aşağıdaki örnek kodda gösterildiği gibi ekleyin.

> [!NOTE]
> Özel bir izleme katılımcısı ekleyen özel bir davranış öğesinin nasıl oluşturulabildiğini gösteren örnek kodu görüntülemek istiyorsanız, [İzleme](./samples/tracking.md) örneklerine bakın.

```csharp
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

İzleme katılımcısı, davranışın bir uzantısı olarak iş akışı hizmet ana bilgisayara eklenir.

Aşağıdaki örnek kod, yapılandırma dosyasından izleme profilinin nasıl okunduğunu gösterir.

```csharp
TrackingProfile GetProfile(string profileName, string displayName)
        {
            TrackingProfile trackingProfile = null;
            TrackingSection trackingSection = (TrackingSection)WebConfigurationManager.GetSection("system.serviceModel/tracking");
            if (trackingSection == null)
            {
                return null;
            }

            profileName ??= "";

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

Bu örnek kod, iş akışı ana bilgisayara izleme profilinin nasıl ekleyeceğini gösterir.

```csharp
WorkflowServiceHost workflowServiceHost = serviceHostBase as WorkflowServiceHost;
if (null != workflowServiceHost)
{
    string workflowDisplayName = workflowServiceHost.Activity.DisplayName;
    TrackingProfile trackingProfile = GetProfile(this.profileName, workflowDisplayName);
    workflowServiceHost.WorkflowExtensions.Add(()  => new EtwTrackingParticipant {
        TrackingProfile = trackingProfile
    });
 }
```

> [!NOTE]
> İzleme profilleri hakkında daha fazla bilgi için [İzleme Profilleri'ne](tracking-profiles.md)bakın.

### <a name="configuring-tracking-using-workflowinvoker"></a>WorkflowInvoker kullanarak izlemeyi yapılandırma

Kullanılarak <xref:System.Activities.WorkflowInvoker>yürütülen bir iş akışı için izlemeyi yapılandırmak için, <xref:System.Activities.WorkflowInvoker> izleme sağlayıcısını bir örneğin uzantısı olarak ekleyin. Aşağıdaki kod örneği [Özel İzleme](./samples/custom-tracking.md) örneğindendir.

```csharp
WorkflowInvoker invoker = new WorkflowInvoker(BuildSampleWorkflow());
invoker.Extensions.Add(customTrackingParticipant);
invoker.Invoke();
```

### <a name="viewing-tracking-records-in-event-viewer"></a>Olay Görüntüleyici'de izleme kayıtlarını görüntüleme

WF yürütülmesini takip ederken görüntülemek için özel ilgi çekici iki Olay Görüntüleyen günlüğü vardır - Analytic günlüğü ve Hata Ayıklama günlüğü. Her ikisi de Microsoft&#124;Windows&#124;Application Server-Applications düğümü altında bulunmaktadır. Bu bölümdeki günlükler, tüm sistemi etkileyen olaylar yerine tek bir uygulamadan gelen olayları içerir.

Hata ayıklama izleme olayları Hata Ayıklama Günlüğü'ne yazılır. Olay Görüntüleyicisi'nde WF hata ayıklama olayları toplamak için Hata Ayıklama Günlüğü'ne olanak sağlar.

1. Olay Görüntüleyicisi'ni açmak için **Başlat'ı**ve ardından **Çalıştır'ı tıklatın.** Çalıştır iletişim kutusunda, `eventvwr`'.

2. Olay Görüntüleyicisi iletişim kutusunda, **Uygulamalar ve Hizmetler Günlükleri** düğümlerini genişletin.

3. **Microsoft,** **Windows**ve **Application Server-Applications** düğümlerini genişletin.

4. **Application Server-Applications** düğümünün altındaki **Hata Ayıklama** düğümüne sağ tıklayın ve **Günlük'u etkinleştir'i**seçin.

5. İzleme olayları oluşturmak için izleme etkinleştirilmiş uygulamanızı yürütün.

6. **Hata Ayıklama** düğümüne sağ tıklayın ve **Yenile'yi seçin.** Olayları izleme, orta bölmede görünür olmalıdır.

WF 4, izleme kayıtlarını bir ETW (Windows için Olay İzleme) oturumuna yazan bir izleme katılımcısı sağlar. ETW izleme katılımcısı, kayıtları izlemeye abone olmak için bir izleme profili ile yapılandırılır. İzleme etkinleştirildiğinde, hataları izleme kayıtları ETW'ye yayılır. ETW izleme katılımcısı tarafından yayılan izleme olaylarına karşılık gelen ETW izleme olayları (100-113 aralığı arasında) Analytic Log'a yazılır.

İzleme kayıtlarını görüntülemek için aşağıdaki adımları izleyin.

1. Olay Görüntüleyicisi'ni açmak için **Başlat'ı**ve ardından **Çalıştır'ı tıklatın.** Çalıştır iletişim kutusunda, `eventvwr`'.

2. Olay Görüntüleyicisi iletişim kutusunda, **Uygulamalar ve Hizmetler Günlükleri** düğümlerini genişletin.

3. **Microsoft,** **Windows**ve **Application Server-Applications** düğümlerini genişletin.

4. **Application Server-Applications** düğümünün altındaki **Analitik** düğüme sağ tıklayın ve **Günlük'u Etkinleştir'i**seçin.

5. İzleme kayıtları oluşturmak için izlemeyi etkinleştiren uygulamanızı yürütün.

6. **Analitik** düğüme sağ tıklayın ve **Yenile'yi seçin.** İzleme kayıtları orta bölmede görünür olmalıdır.

Aşağıdaki resim, olay görüntüleyicideki olayları izleme gösterir:

![İzleme kayıtlarını gösteren Olay Görüntüleyicisi'nin ekran görüntüsü.](./media/configuring-tracking-for-a-workflow/tracking-event-viewer.png)

### <a name="registering-an-application-specific-provider-id"></a>Uygulamaya özel bir sağlayıcı kimliğini kaydetme

Olayların belirli bir uygulama günlüğüne yazılması gerekiyorsa, yeni sağlayıcı bildirimini kaydetmek için aşağıdaki adımları izleyin.

1. Uygulama yapılandırma dosyasında sağlayıcı kimliğini bildirin.

    ```xml
    <system.serviceModel>
        <diagnostics etwProviderId="2720e974-9fe9-477a-bb60-81fe3bf91eec"/>
    </system.serviceModel>
    ```

2. Manifesto dosyasını\\\< [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] %windir%\Microsoft.NET\Framework>\Microsoft.Windows.ApplicationServer.Applications.man'ın son sürümünden geçici bir konuma kopyalayın ve Microsoft.Windows.ApplicationServer.Applications_Provider1.man olarak yeniden adlandırın

3. Bildirim dosyasındaki GUID'i yeni GUID olarak değiştirin.

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" />
    ```

4. Varsayılan sağlayıcıyı kaldırmak istemiyorsanız sağlayıcı adını değiştirin.

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" />
    ```

5. Önceki adımda sağlayıcı adını değiştirdiyseniz, bildirim dosyasındaki kanal adlarını yeni sağlayıcı adı ile değiştirin.

    ```xml
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Admin" chid="ADMIN_CHANNEL" symbol="ADMIN_CHANNEL" type="Admin" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ADMIN_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Operational" chid="OPERATIONAL_CHANNEL" symbol="OPERATIONAL_CHANNEL" type="Operational" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.OPERATIONAL_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Debug" chid="DEBUG_CHANNEL" symbol="DEBUG_CHANNEL" type="Debug" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.DEBUG_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Perf" chid="PERF_CHANNEL" symbol="PERF_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.PERF_CHANNEL.message)" />
    ```

6. Bu adımları izleyerek kaynak DLL oluşturun.

    1. Windows SDK'yı yükleyin. Windows SDK ileti derleyicisi ([mc.exe](/windows/win32/wes/message-compiler--mc-exe-)) ve kaynak derleyicisi[(rc.exe)](/windows/win32/menurc/using-rc-the-rc-command-line-)içerir.

    2. Windows SDK komut isteminde, mc.exe'yi yeni bildirim dosyasında çalıştırın.

        ```console
        mc.exe Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

    3. Önceki adımda oluşturulan kaynak dosyasında rc.exe çalıştırın.

        ```console
        rc.exe  Microsoft.Windows.ApplicationServer.Applications_Provider1.rc
        ```

    4. NewProviderReg.cs adlı boş bir cs dosyası oluşturun.

    5. C# derleyicisini kullanarak bir kaynak DLL oluşturun.

        ```console
        csc /target:library /win32res:Microsoft.Windows.ApplicationServer.Applications_Provider1.res NewProviderReg.cs /out:Microsoft.Windows.ApplicationServer.Applications_Provider1.dll
        ```

    6. Bildirim dosyasındaki `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` kaynak ve ileti dll adını yeni dll adına değiştirin.

        ```xml
        <provider name="Microsoft-Windows-Application Server-Applications_Provider1" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" symbol="Microsoft_Windows_ApplicationServer_ApplicationEvents" resourceFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll" messageFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll" />
        ```

    7. Bildirimi kaydetmek için [wevtutil](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732848(v=ws.10)) kullanın.

        ```console
        wevtutil im Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Server App Kumaş İzleme](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))
- [Uygulama Kumaşı ile Uygulamaların İzlenmesi](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))
