---
title: İzleme Profilleri
ms.date: 03/30/2017
ms.assetid: 22682566-1cd9-4672-9791-fb3523638e18
ms.openlocfilehash: 9217f25ba4499e7ff75020642be387aa79ba27bf
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837629"
---
# <a name="tracking-profiles"></a>İzleme Profilleri

İzleme profilleri, bir iş akışı örneğinin durumu çalışma zamanında değiştiğinde yayınlanan iş akışı olaylarına abone olmak için izleme katılımcısına izin veren izleme sorguları içerir.

## <a name="tracking-profiles"></a>İzleme Profilleri

İzleme profilleri, bir iş akışı örneği için hangi izleme bilgilerinin yayınlandığını belirtmek için kullanılır. Hiçbir profil belirtilmemişse, tüm izleme olayları yayınlanır. Bir profil belirtilmişse, profilde belirtilen izleme olayları yayınlanır. İzleme gereksinimlerinize bağlı olarak, çok genel olan bir profil yazabilirsiniz, bu, bir iş akışındaki küçük bir üst düzey durum değişikliği kümesine abone olabilir. Buna karşılık, daha sonra ayrıntılı bir yürütme akışını yeniden oluşturmak için yeterince zengin olan çok ayrıntılı bir profil oluşturabilirsiniz.

Profiller bildirimi, standart bir .NET Framework yapılandırma dosyası içinde veya kodda belirtilen XML öğeleri olarak kendini takip ediyor. Aşağıdaki örnek bir yapılandırma dosyasındaki bir [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] izleme profilidir. Bu, izleme katılımcısının `Started` abone olmasına ve iş akışı olaylarına `Completed` izin verir.

```xml
<system.serviceModel>
    ...
    <tracking>
      <trackingProfile name="Sample Tracking Profile">
        <workflow activityDefinitionId="*">
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="Started"/>
                <state name="Completed"/>
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
    ...
</system.serviceModel>
```

Aşağıdaki örnek, kod kullanılarak oluşturulan eşdeğer izleme profilini gösterir.

```csharp
TrackingProfile profile = new TrackingProfile()
{
    Name = "CustomTrackingProfile",
    Queries =
    {
        new WorkflowInstanceQuery()
        {
            // Limit workflow instance tracking records for started and
            // completed workflow states.
            States = { WorkflowInstanceStates.Started, WorkflowInstanceStates.Completed },
        }
    }
};
```

İzleme kayıtları, <xref:System.Activities.Tracking.ImplementationVisibility> özniteliği kullanılarak izleme profili içindeki görünürlük modu aracılığıyla filtrelenir. Bileşik etkinlik, uygulamasını oluşturan diğer etkinlikleri içeren en üst düzey bir etkinliktir. Görünürlük modu, uygulamayı oluşturan etkinliklerin izlendiğini belirtmek için bir iş akışı etkinliği içinde bileşik etkinliklerden yayılan izleme kayıtlarını belirtir. Görünürlük modu, izleme profili düzeyinde geçerlidir. Bir iş akışı içindeki bireysel etkinliklerin izleme kayıtlarının filtrelenmesi, izleme profili içindeki sorgular tarafından denetlenir. Daha fazla bilgi için bu belgedeki **profil sorgu türlerini izleme** bölümüne bakın.

İzleme profilindeki `implementationVisibility` özniteliği tarafından belirtilen iki görünürlük modu `RootScope` ve `All`. `RootScope` modunu kullanmak, bileşik etkinliğin bir iş akışının kökü olmadığı durumda bir etkinliğin uygulanmasını oluşturan etkinliklerin izleme kayıtlarını bastırır. Bu, diğer etkinlikleri kullanarak uygulanan bir etkinlik bir iş akışına eklendiğinde ve `implementationVisibility` RootScope olarak ayarlandığında, yalnızca bu bileşik etkinliğin içindeki en üst düzey etkinlik izlendiğine ilişkin anlamına gelir. Bir etkinlik iş akışının köküdür, etkinliğin uygulanması iş akışının kendisidir ve izleme kayıtları, uygulamayı oluşturan etkinlikler için yayınlanır. All modunun kullanılması, tüm izleme kayıtlarının kök etkinlik ve tüm bileşik etkinlikleri için oluşturulmasına izin verir.

Örneğin, *MyActivity* , uygulamasında iki etkinlik ( *Activity1* ve *Activity2*) içeren bir bileşik etkinlik olduğunu varsayalım. Bu etkinlik bir iş akışına eklendiğinde ve izleme `implementationVisibility` `RootScope`olarak ayarlanmış bir izleme profiliyle etkinleştirildiğinde, izleme kayıtları yalnızca *MyActivity*için yayılır. Ancak, *Activity1* ve *Activity2*etkinlikleri için hiçbir kayıt yayınlanmadı.

Ancak, izleme profili için `implementationVisibility` özniteliği `All`olarak ayarlanırsa, izleme kayıtları yalnızca *MyActivity*için değil, *Activity1* ve *Activity2*etkinlikleri için de geçerlidir.

`implementationVisibility` bayrağı aşağıdaki izleme kayıt türleri için geçerlidir:

- ActivityStateRecord

- FaultPropagationRecord

- CancelRequestedRecord

- ActivityScheduledRecord

> [!NOTE]
> Etkinlik uygulamasından yayılan CustomTrackingRecords, ImplementationVisibility ayarı tarafından filtrelenmez.

`implementationVisibility` işlevselliği, aşağıdaki gibi koddaki izleme profilinde <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> olarak belirtilir:

```csharp
TrackingProfile sampleTrackingProfile = new TrackingProfile()
{
    Name = "Sample Tracking Profile",
    ImplementationVisibility = ImplementationVisibility.RootScope
};
```

`implementationVisibility` işlevi bir yapılandırma dosyasındaki izleme profilinde aşağıdaki gibi <xref:System.Activities.Tracking.ImplementationVisibility.All> olarak belirtilir:

```xml
<tracking>
      <profiles>
        <trackingProfile name="Shipping Monitoring" implementationVisibility="All">
          <workflow activityDefinitionId="*">
...
         </workflow>
        </trackingProfile>
      </profiles>
</tracking>
```

İzleme profilindeki `ImplementationVisibility` ayarı isteğe bağlıdır. Varsayılan olarak, değeri `RootScope`olarak ayarlanır. Bu özniteliğin değerleri de büyük/küçük harfe duyarlıdır.

### <a name="tracking-profile-query-types"></a>İzleme profili sorgu türleri

İzleme profilleri, belirli izleme kayıtları için iş akışı çalışma zamanını sorgulamanızı sağlayan kayıtları izlemek için bildirim temelli abonelikler olarak yapılandırılır. Farklı <xref:System.Activities.Tracking.TrackingRecord> nesneleri sınıflarına abone olmanızı sağlayan birkaç sorgu türü vardır. İzleme profilleri, yapılandırma veya kod aracılığıyla belirtilebilir. En yaygın sorgu türleri şunlardır:

- <xref:System.Activities.Tracking.WorkflowInstanceQuery>-bunu, daha önce gösterilen `Started` ve `Completed`gibi iş akışı örneği yaşam döngüsü değişikliklerini izlemek için kullanın. <xref:System.Activities.Tracking.WorkflowInstanceQuery> Aşağıdaki abone olmak için kullanılan <xref:System.Activities.Tracking.TrackingRecord> nesneleri:

  - <xref:System.Activities.Tracking.WorkflowInstanceRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>

  Abone olunmasına izin veren durumlar <xref:System.Activities.Tracking.WorkflowInstanceStates> sınıfında belirtilmiştir.

  <xref:System.Activities.Tracking.WorkflowInstanceQuery> kullanılarak `Started` örneği durumu için iş akışı örnek düzeyi izleme kayıtlarına abone olmak için kullanılan yapılandırma veya kod aşağıdaki örnekte gösterilmiştir.

  ```xml
  <workflowInstanceQueries>
      <workflowInstanceQuery>
        <states>
          <state name="Started"/>
        </states>
      </workflowInstanceQuery>
  </workflowInstanceQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new WorkflowInstanceQuery()
          {
              States = { WorkflowInstanceStates.Started}
          }
      }
  };
  ```

- <xref:System.Activities.Tracking.ActivityStateQuery>-bir iş akışı örneği oluşturan etkinliklerin yaşam döngüsü değişikliklerini izlemek için bunu kullanın. Örneğin, bir iş akışı örneği içinde "e-posta gönder" etkinliğinin tamamlandığı her seferinde izlemek isteyebilirsiniz. Bu sorgu, bir <xref:System.Activities.Tracking.TrackingParticipant> <xref:System.Activities.Tracking.ActivityStateRecord> nesnelerine abone olmak için gereklidir. Abone olunacak durumlar <xref:System.Activities.Tracking.ActivityStates>olarak belirtilir.

  `SendEmailActivity` etkinliği için <xref:System.Activities.Tracking.ActivityStateQuery> kullanan etkinlik durumu izleme kayıtlarına abone olmak için kullanılan yapılandırma ve kod aşağıdaki örnekte gösterilmiştir.

  ```xml
  <activityStateQueries>
    <activityStateQuery activityName="SendEmailActivity">
      <states>
        <state name="Closed"/>
      </states>
    </activityStateQuery>
  </activityStateQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new ActivityStateQuery()
          {
              ActivityName = "SendEmailActivity",
              States = { ActivityStates.Closed }
          }
      }
  };
  ```

  > [!NOTE]
  > Birden çok activityStateQuery öğesi aynı ada sahip ise, izleme profilinde yalnızca son öğedeki durumlar kullanılır.

- <xref:System.Activities.Tracking.ActivityScheduledQuery>-bu sorgu, bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemenize olanak sağlar. Sorgu, bir <xref:System.Activities.Tracking.TrackingParticipant> <xref:System.Activities.Tracking.ActivityScheduledRecord> nesnelerine abone olmak için gereklidir.

  <xref:System.Activities.Tracking.ActivityScheduledQuery> kullanılarak zamanlanmakta olan `SendEmailActivity` alt etkinliği ile ilgili kayıtlara abone olmak için kullanılan yapılandırma ve kod aşağıdaki örnekte gösterilmiştir.

  ```xml
  <activityScheduledQueries>
    <activityScheduledQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />
  </activityScheduledQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new ActivityScheduledQuery()
          {
              ActivityName = "ProcessNotificationsActivity",
              ChildActivityName = "SendEmailActivity"
          }
      }
  };
  ```

- <xref:System.Activities.Tracking.FaultPropagationQuery> bir etkinlik içinde oluşan hataların işlenmesini izlemek için bunu kullanın. Sorgu, bir <xref:System.Activities.Tracking.TrackingParticipant> <xref:System.Activities.Tracking.FaultPropagationRecord> nesnelerine abone olmak için gereklidir.

  <xref:System.Activities.Tracking.FaultPropagationQuery> kullanılarak oluşan hata yayılmaya ilişkin kayıtlara abone olmak için kullanılan yapılandırma ve kod aşağıdaki örnekte gösterilmiştir.

  ```xml
  <faultPropagationQueries>
    <faultPropagationQuery faultSourceActivityName="SendEmailActivity" faultHandlerActivityName="NotificationsFaultHandler" />
  </faultPropagationQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new FaultPropagationQuery()
          {
              FaultSourceActivityName = "SendEmailActivity",
              FaultHandlerActivityName = "NotificationsFaultHandler"
          }
      }
  };
  ```

- <xref:System.Activities.Tracking.CancelRequestedQuery>-üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere bunu kullanın. Sorgu, bir <xref:System.Activities.Tracking.TrackingParticipant> <xref:System.Activities.Tracking.CancelRequestedRecord> nesnelerine abone olmak için gereklidir.

  <xref:System.Activities.Tracking.CancelRequestedQuery> kullanılarak etkinlik iptalle ilgili kayıtlara abone olmak için kullanılan yapılandırma ve kod aşağıdaki örnekte gösterilmiştir.

  ```xml
  <cancelRequestedQueries>
    <cancelRequestedQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />
  </cancelRequestedQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new CancelRequestedQuery()
          {
              ActivityName = "ProcessNotificationsActivity",
              ChildActivityName = "SendEmailActivity"
          }
      }
  };
  ```

- <xref:System.Activities.Tracking.CustomTrackingQuery>-bunu, kod etkinliklerinizde tanımladığınız olayları izlemek için kullanın. Sorgu, bir <xref:System.Activities.Tracking.TrackingParticipant> <xref:System.Activities.Tracking.CustomTrackingRecord> nesnelerine abone olmak için gereklidir.

  <xref:System.Activities.Tracking.CustomTrackingQuery> kullanarak özel izleme kayıtlarıyla ilgili kayıtlara abone olmak için kullanılan yapılandırma ve kod aşağıdaki örnekte gösterilmiştir.

  ```xml
  <customTrackingQueries>
    <customTrackingQuery name="EmailAddress" activityName="SendEmailActivity" />
  </customTrackingQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new CustomTrackingQuery()
          {
              Name = "EmailAddress",
              ActivityName = "SendEmailActivity"
          }
      }
  };
  ```

- <xref:System.Activities.Tracking.BookmarkResumptionQuery>-bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için bunu kullanın. Bu sorgu, bir <xref:System.Activities.Tracking.TrackingParticipant> <xref:System.Activities.Tracking.BookmarkResumptionRecord> nesnelerine abone olmak için gereklidir.

  <xref:System.Activities.Tracking.BookmarkResumptionQuery> kullanılarak yer işareti sürdürme ilgili kayıtlara abone olmak için kullanılan yapılandırma ve kod aşağıdaki örnekte gösterilmiştir.

  ```xml
  <bookmarkResumptionQueries>
    <bookmarkResumptionQuery name="SentEmailBookmark" />
  </bookmarkResumptionQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new BookmarkResumptionQuery()
          {
              Name = "sentEmailBookmark"
          }
      }
  };
  ```

### <a name="annotations"></a>Ek Açıklamalar

Ek açıklamalar, derleme zamanından sonra yapılandırılabilecek bir değer ile izleme kayıtlarını rastgele etiketlemenize olanak tanır. Örneğin, "posta sunucusu" = = "mail Sunucu1" ile etiketlenecek birkaç iş akışı arasında birkaç izleme kaydının olmasını isteyebilirsiniz. Bu, izleme kayıtlarını daha sonra sorgularken bu etikete sahip tüm kayıtları bulmayı kolaylaştırır.

Bunu gerçekleştirmek için aşağıdaki örnekte gösterildiği gibi bir izleme sorgusuna ek açıklama eklenir.

```xml
<activityStateQuery activityName="SendEmailActivity">
  <states>
    <state name="Closed"/>
  </states>
  <annotations>
    <annotation name="MailServer" value="Mail Server1"/>
  </annotations>
</activityStateQuery>
```

### <a name="how-to-create-a-tracking-profile"></a>Izleme profili oluşturma

İzleme sorgusu öğeleri, bir XML yapılandırma dosyası veya [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]kodu kullanarak bir izleme profili oluşturmak için kullanılır. Bir yapılandırma dosyası kullanılarak oluşturulan izleme profiline bir örnek aşağıda verilmiştir.

```xml
<system.serviceModel>
  <tracking>
    <profiles>
      <trackingProfile name="Sample Tracking Profile ">
        <workflow activityDefinitionId="*">
          <!--Specify the tracking profile query elements to subscribe for tracking records-->
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>
```

> [!WARNING]
> Iş akışı hizmet ana bilgisayarını kullanan bir WF için, izleme profili genellikle bir yapılandırma dosyası kullanılarak oluşturulur. İzleme profilini ve izleme sorgusu API 'sini kullanarak kodla bir izleme profili oluşturmak da mümkündür.

XML yapılandırma dosyası olarak yapılandırılmış bir profil, bir davranış uzantısı kullanılarak bir izleme katılımcısına uygulanır. Bu, [bir Iş akışı Için Izlemeyi yapılandırırken](configuring-tracking-for-a-workflow.md)sonraki bölümde açıklandığı şekilde bir WorkflowServiceHost 'a eklenir.

Konak tarafından yayılan izleme kayıtlarının ayrıntı düzeyi, izleme profili içindeki yapılandırma ayarları tarafından belirlenir. İzleme katılımcısı bir izleme profiline sorgular ekleyerek kayıtları izlemeye abone olur. Tüm izleme kayıtlarına abone olmak için, izleme profilinin her sorgu içindeki ad alanlarında "\*" kullanarak tüm izleme sorgularını belirtmesi gerekir.

Aşağıda, izleme profillerinin bazı yaygın örnekleri verilmiştir.

- İş akışı örneği kayıtlarını ve hatalarını almak için bir izleme profili.

  ```xml
  <trackingProfile name="Instance and Fault Records">
    <workflow activityDefinitionId="*">
      <workflowInstanceQueries>
        <workflowInstanceQuery>
          <states>
            <state name="*" />
          </states>
        </workflowInstanceQuery>
      </workflowInstanceQueries>
      <activityStateQueries>
        <activityStateQuery activityName="*">
          <states>
            <state name="Faulted"/>
          </states>
        </activityStateQuery>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
  ```

- Tüm özel izleme kayıtlarını elde etmek için bir izleme profili.

  ```xml
  <trackingProfile name="Instance_And_Custom_Records">
    <workflow activityDefinitionId="*">
      <customTrackingQueries>
        <customTrackingQuery name="*" activityName="*" />
      </customTrackingQueries>
    </workflow>
  </trackingProfile>
  ```

## <a name="see-also"></a>Ayrıca bkz.

- [SQL İzleme](./samples/sql-tracking.md)
- [Windows Server App Fabric Izleme](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))
- [App Fabric ile uygulamaları izleme](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))
