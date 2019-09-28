---
title: İş Akışı için İzlemeyi Yapılandırma
ms.date: 03/30/2017
ms.assetid: 905adcc9-30a0-4918-acd6-563f86db988a
ms.openlocfilehash: 889efc804bb45b384dfde5b4deb520a81d1e5486
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353057"
---
# <a name="configuring-tracking-for-a-workflow"></a>İş Akışı için İzlemeyi Yapılandırma

Bir iş akışı üç şekilde çalıştırılabilir:

- @No__t içinde barındırılan-0

- @No__t olarak yürütüldü-0

- @No__t ile doğrudan yürütülür-0

İş akışı barındırma seçeneğine bağlı olarak, bir izleme katılımcısı kod aracılığıyla veya bir yapılandırma dosyası aracılığıyla eklenebilir. Bu konu, izlemenin bir <xref:System.Activities.WorkflowApplication> ' a ve <xref:System.ServiceModel.Activities.WorkflowServiceHost> ' e bir izleme katılımcısı ekleyerek nasıl yapılandırıldığını ve <xref:System.Activities.WorkflowInvoker> kullanılırken izlemenin nasıl etkinleştirileceğini açıklar.

## <a name="configuring-workflow-application-tracking"></a>Iş akışı uygulama Izlemeyi yapılandırma

Bir iş akışı <xref:System.Activities.WorkflowApplication> sınıfı kullanılarak çalıştırılabilir. Bu konu, <xref:System.Activities.WorkflowApplication> iş akışı konağına izleme katılımcısı ekleyerek izlemenin [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] iş akışı uygulaması için nasıl yapılandırıldığını gösterir. Bu durumda iş akışı, iş akışı uygulaması olarak çalışır. Bir iş akışı uygulamasını, <xref:System.Activities.WorkflowApplication> sınıfını kullanan şirket içinde barındırılan bir. exe dosyası olan kod aracılığıyla (bir yapılandırma dosyası kullanmak yerine) yapılandırırsınız. İzleme katılımcısı <xref:System.Activities.WorkflowApplication> örneğine bir uzantı olarak eklenir. Bu işlem, WorkflowApplication örneği için Uzantılar koleksiyonuna <xref:System.Activities.Tracking.TrackingParticipant> eklenerek yapılır.

Bir iş akışı uygulaması için aşağıdaki kodda gösterildiği gibi <xref:System.Activities.Tracking.EtwTrackingParticipant> davranış uzantısını ekleyebilirsiniz.

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

### <a name="configuring-workflow-service-tracking"></a>Iş akışı hizmeti Izlemeyi yapılandırma

Bir iş akışı, <xref:System.ServiceModel.Activities.WorkflowServiceHost> hizmet konağında barındırıldığında bir WCF hizmeti olarak gösterilebilir. <xref:System.ServiceModel.Activities.WorkflowServiceHost>, iş akışı tabanlı hizmet için özelleşmiş bir .NET ServiceHost uygulamasıdır. Bu bölümde, <xref:System.ServiceModel.Activities.WorkflowServiceHost> ' de çalışan [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] iş akışı hizmeti için izlemenin nasıl yapılandırılacağı açıklanmaktadır. Bir Web. config dosyası (Web 'de barındırılan bir hizmet için) veya bir App. config dosyası aracılığıyla, bir hizmet davranışı belirterek veya ' ye izlemeye özgü bir davranış ekleyerek kod aracılığıyla bir uygulama. config dosyası (konsol uygulaması gibi tek başına bir uygulamada barındırılan bir hizmet için) ile yapılandırılır. hizmet ana bilgisayarı için <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> koleksiyonu.

@No__t-0 ' da barındırılan bir iş akışı hizmeti için, aşağıdaki örnekte gösterildiği gibi, bir yapılandırma dosyasındaki < `behavior` > öğesini kullanarak <xref:System.Activities.Tracking.EtwTrackingParticipant> ekleyebilirsiniz.

```xml
<behaviors>
   <serviceBehaviors>
        <behavior>
          <etwTracking profileName="Sample Tracking Profile" />
        </behavior>
   </serviceBehaviors>
<behaviors>
```

Alternatif olarak, <xref:System.ServiceModel.WorkflowServiceHost> ' da barındırılan bir iş akışı hizmeti için, kod aracılığıyla <xref:System.Activities.Tracking.EtwTrackingParticipant> davranış uzantısını ekleyebilirsiniz. Özel bir izleme katılımcısı eklemek için yeni bir davranış uzantısı oluşturun ve aşağıdaki örnek kodda gösterildiği gibi <xref:System.ServiceModel.ServiceHost> ' a ekleyin.

> [!NOTE]
> Özel bir izleme katılımcısı ekleyen özel bir davranış öğesinin nasıl oluşturulacağını gösteren örnek kodu görüntülemek istiyorsanız [izleme](./samples/tracking.md) örneklerine bakın.

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

İzleme katılımcısı, iş akışı hizmet ana bilgisayarına davranışın uzantısı olarak eklenir.

Aşağıdaki örnek kod, yapılandırma dosyasından bir izleme profilinin nasıl okunacağını gösterir.

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

Bu örnek kod, bir iş akışı konağına izleme profilinin nasıl ekleneceğini gösterir.

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
> İzleme profilleri hakkında daha fazla bilgi için bkz. [Izleme profilleri](https://go.microsoft.com/fwlink/?LinkId=201310).

### <a name="configuring-tracking-using-workflowinvoker"></a>Workflowwınvoker kullanarak izlemeyi yapılandırma

@No__t-0 kullanılarak yürütülen bir iş akışına yönelik izlemeyi yapılandırmak için, izleme sağlayıcısını bir <xref:System.Activities.WorkflowInvoker> örneğine uzantı olarak ekleyin. Aşağıdaki kod örneği, [özel izleme](./samples/custom-tracking.md) örneğinden yapılır.

```csharp
WorkflowInvoker invoker = new WorkflowInvoker(BuildSampleWorkflow());
invoker.Extensions.Add(customTrackingParticipant);
invoker.Invoke();
```

### <a name="viewing-tracking-records-in-event-viewer"></a>Olay Görüntüleyicisi izleme kayıtlarını görüntüleme

WF yürütmesi izlenirken, analiz günlüğü ve hata ayıklama günlüğünde görüntülemek için belirli bir ilgi çekici iki Olay Görüntüleyicisi günlüğü vardır. Her ikisi de Microsoft&#124;Windows&#124;uygulama sunucusu-uygulamalar düğümü altında bulunur. Bu bölümün içindeki günlüklerde, tüm sistem üzerinde bir etkisi olan olaylar yerine tek bir uygulamanın olayları bulunur.

Hata ayıklama izleme olayları hata ayıklama günlüğüne yazılır. Olay Görüntüleyicisi WF hata ayıklama izleme olaylarını toplamak için, hata ayıklama günlüğünü etkinleştirin.

1. Olay Görüntüleyicisi açmak için **Başlat**' a ve ardından Çalıştır ' a tıklayın **.** Çalıştır iletişim kutusunda `eventvwr` yazın.

2. Olay Görüntüleyicisi iletişim kutusunda, **uygulamalar ve hizmetler günlükleri** düğümünü genişletin.

3. **Microsoft**, **Windows**ve **uygulama sunucusu-uygulamalar** düğümlerini genişletin.

4. **Uygulama sunucusu-uygulamalar** düğümünün altındaki **hata ayıklama** düğümüne sağ tıklayın ve **günlüğü etkinleştir**' i seçin.

5. İzleme olaylarını oluşturmak için izleme özellikli uygulamanızı yürütün.

6. **Hata ayıklama** düğümüne sağ tıklayın ve Yenile ' yi seçin **.** İzleme olayları, Orta bölmede görünür olmalıdır.

WF 4, izleme kayıtlarını ETW (Windows için olay Izleme) oturumuna yazan bir izleme katılımcısı sağlar. ETW izleme katılımcısı, kayıtları izlemeye abone olmak için bir izleme profili ile yapılandırılır. İzleme etkinleştirildiğinde, hata izleme kayıtları ETW 'ye dağıtılır. ETW izleme katılımcısı tarafından yayılan izleme olaylarına karşılık gelen ETW izleme olayları (100-113 aralığı arasında) analitik günlüğe yazılır.

İzleme kayıtlarını görüntülemek için aşağıdaki adımları izleyin.

1. Olay Görüntüleyicisi açmak için **Başlat**' a ve ardından Çalıştır ' a tıklayın **.** Çalıştır iletişim kutusunda `eventvwr` yazın.

2. Olay Görüntüleyicisi iletişim kutusunda, **uygulamalar ve hizmetler günlükleri** düğümünü genişletin.

3. **Microsoft**, **Windows**ve **uygulama sunucusu-uygulamalar** düğümlerini genişletin.

4. **Uygulama sunucusu-uygulamalar** düğümünün altındaki **analitik** düğüme sağ tıklayın ve **günlüğü etkinleştir**' i seçin.

5. İzleme etkin uygulamanızı, izleme kayıtları oluşturmak için yürütün.

6. **Analitik** düğümüne sağ tıklayın ve Yenile ' yi seçin **.** İzleme kayıtları, Orta bölmede görünür olmalıdır.

Aşağıdaki görüntüde olay görüntüleyicisinde izleme olayları gösterilmektedir:

![İzleme kayıtlarını gösteren Olay Görüntüleyicisi ekran görüntüsü.](./media/configuring-tracking-for-a-workflow/tracking-event-viewer.png)

### <a name="registering-an-application-specific-provider-id"></a>Uygulamaya özgü bir sağlayıcı KIMLIĞINI kaydetme

Olayların belirli bir uygulama günlüğüne yazılması gerekiyorsa, yeni sağlayıcı bildirimini kaydetmek için aşağıdaki adımları izleyin.

1. Uygulama yapılandırma dosyasında sağlayıcı KIMLIĞINI bildirin.

    ```xml
    <system.serviceModel>
        <diagnostics etwProviderId="2720e974-9fe9-477a-bb60-81fe3bf91eec"/>
    </system.serviceModel>
    ```

2. Bildirim dosyasını%windir%\Microsoft.NET\Framework @ no__t-0 @ no__t-1En son sürümü olan [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] > \Microsoft.Windows.ApplicationServer.Applications.man geçici bir konuma kopyalayın ve şu şekilde yeniden adlandırın Microsoft. Windows. ApplicationServer. Applications_Provider1. Man

3. Bildirim dosyasındaki GUID 'yi yeni GUID ile değiştirin.

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}"
    ```

4. Varsayılan Sağlayıcıyı kaldırmak istemiyorsanız sağlayıcı adını değiştirin.

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}"
    ```

5. Önceki adımda sağlayıcı adını değiştirdiyseniz, bildirim dosyasındaki kanal adlarını yeni sağlayıcı adıyla değiştirin.

    ```xml
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Admin" chid="ADMIN_CHANNEL" symbol="ADMIN_CHANNEL" type="Admin" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ADMIN_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Operational" chid="OPERATIONAL_CHANNEL" symbol="OPERATIONAL_CHANNEL" type="Operational" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.OPERATIONAL_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Debug" chid="DEBUG_CHANNEL" symbol="DEBUG_CHANNEL" type="Debug" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.DEBUG_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Perf" chid="PERF_CHANNEL" symbol="PERF_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.PERF_CHANNEL.message)" />
    ```

6. Aşağıdaki adımları izleyerek kaynak DLL 'sini oluşturun.

    1. Windows SDK 'i yükler. Windows SDK, ileti derleyicisini ([mc. exe](https://go.microsoft.com/fwlink/?LinkId=184606)) ve kaynak derleyicisini ([rc. exe](https://go.microsoft.com/fwlink/?LinkId=184605)) içerir.

    2. Windows SDK komut isteminde, yeni bildirim dosyasında Mc. exe ' yi çalıştırın.

        ```console
        mc.exe Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

    3. Önceki adımda oluşturulan kaynak dosyasında RC. exe ' yi çalıştırın.

        ```console
        rc.exe  Microsoft.Windows.ApplicationServer.Applications_Provider1.rc
        ```

    4. NewProviderReg.cs adlı boş bir cs dosyası oluşturun.

    5. C# Derleyiciyi kullanarak bir kaynak dll 'si oluşturun.

        ```console
        csc /target:library /win32res:Microsoft.Windows.ApplicationServer.Applications_Provider1.res NewProviderReg.cs /out:Microsoft.Windows.ApplicationServer.Applications_Provider1.dll
        ```

    6. Bildirim dosyasındaki kaynak ve ileti DLL adını `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` ' dan yeni dll adına değiştirin.

        ```xml
        <provider name="Microsoft-Windows-Application Server-Applications_Provider1" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" symbol="Microsoft_Windows_ApplicationServer_ApplicationEvents" resourceFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll" messageFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll">
        ```

    7. Bildirimi kaydetmek için [wevtutil](https://go.microsoft.com/fwlink/?LinkId=184608) kullanın.

        ```console
        wevtutil im Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Server App Fabric Izleme](https://go.microsoft.com/fwlink/?LinkId=201273)
- [App Fabric ile uygulamaları izleme](https://go.microsoft.com/fwlink/?LinkId=201275)
