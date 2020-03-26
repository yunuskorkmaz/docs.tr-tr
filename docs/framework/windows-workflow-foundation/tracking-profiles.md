---
title: İzleme Profilleri
ms.date: 03/30/2017
ms.assetid: 22682566-1cd9-4672-9791-fb3523638e18
ms.openlocfilehash: 609c3f0c728e71d1bbf5335aae0b18d6f99a7181
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249044"
---
# <a name="tracking-profiles"></a>İzleme Profilleri

İzleme profilleri, bir izleme katılımcısının çalışma zamanında iş akışı örneği durumu değiştiğinde yayılan iş akışı olaylarına abone olmasını sağlayan izleme sorguları içerir.

## <a name="tracking-profiles"></a>İzleme Profilleri

İzleme profilleri, iş akışı örneği için hangi izleme bilgilerinin yayıldığıbelirtilmek için kullanılır. Profil belirtilmemişse, tüm izleme olayları yayılır. Bir profil belirtilirse, profilde belirtilen izleme olayları yayılır. İzleme gereksinimlerinize bağlı olarak, çok genel bir profil yazabilirsiniz ve bu profil, iş akışındaki küçük bir üst düzey durum değişikliğine abone dir. Tersine, ortaya çıkan olaylar daha sonra ayrıntılı bir yürütme akışını yeniden oluşturmak için yeterince zengin olan çok ayrıntılı bir profil oluşturabilirsiniz.

İzleme profilleri, standart bir .NET Framework yapılandırma dosyasında veya kodda belirtilen XML öğeleri olarak kendini gösterir. Aşağıdaki örnek, bir [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] izleme katılımcısının iş akışı olaylarına abone `Started` `Completed` olmasını sağlayan bir yapılandırma dosyasındaki izleme profilidir.

```xml
<system.serviceModel>
    ...
    <tracking>
     <profiles>
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

Aşağıdaki örnekte, kod kullanılarak oluşturulan eşdeğer izleme profili gösterilmektedir.

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

İzleme kayıtları öznitelik kullanılarak <xref:System.Activities.Tracking.ImplementationVisibility> izleme profili içindeki görünürlük modundan filtrelenir. Bileşik etkinlik, uygulanmasını oluşturan diğer etkinlikleri içeren üst düzey bir etkinliktir. Görünürlük modu, uygulamayı oluşturan etkinliklerin izlendiğini belirtmek için, bir iş akışı etkinliği içindeki bileşik etkinliklerden yayılan izleme kayıtlarını belirtir. Görünürlük modu izleme profili düzeyinde geçerlidir. İş akışı içindeki tek tek etkinliklere ait izleme kayıtlarının filtrelemi, izleme profilindeki sorgular tarafından denetlenir. Daha fazla bilgi için bu belgedeki **İzleme Profili Sorgu Türleri** bölümüne bakın.

İzleme profilindeki öznitelik tarafından `implementationVisibility` belirtilen iki görünürlük `RootScope` `All`modu ve . `RootScope` Modu kullanmak, bileşik bir etkinliğin iş akışının kökü olmadığı durumlarda bir etkinliğin uygulanmasını oluşturan etkinliklerin izleme kayıtlarını bastırır. Bu, diğer etkinlikler kullanılarak uygulanan bir etkinlik iş akışına ve RootScope `implementationVisibility` kümesine eklendiğinde, yalnızca bu bileşik etkinlik içindeki üst düzey etkinliğin izlendiğinde anlamına gelir. Bir etkinlik iş akışının köküise, etkinliğin uygulanması iş akışının kendisidir ve izleme kayıtları uygulamayı oluşturan etkinlikler için yayılır. Tüm modu kullanmak, tüm izleme kayıtlarının kök etkinliği ve tüm bileşik etkinlikleri için yayımlansına izin verir.

Örneğin, *MyActivity'in,* uygulaması *etkinlik1* ve *Etkinlik2*olmak üzere iki etkinlik içeren bileşik bir etkinlik olduğunu varsayalım. Bu etkinlik bir iş akışına eklendiğinde ve izleme `implementationVisibility` ayarlanmış `RootScope`bir izleme profili ile etkinleştirildiğinde, izleme kayıtları yalnızca *MyActivity*için yayılır. Ancak, etkinlikler *Etkinlik1* ve *Etkinlik2*için hiçbir kayıt yayımlanır.

`implementationVisibility` Ancak, izleme profili için öznitelik ayarlanırsa `All`, o zaman izleme kayıtları *MyActivity*için değil, aynı zamanda etkinlikler *Etkinlik1* ve *Etkinlik2*için yayılan .

Bayrak `implementationVisibility` aşağıdaki izleme kayıt türleri için geçerlidir:

- ActivityStateRecord

- Fay YayılımıKayıt

- Cancelrequestedrecord

- Activityscheduledrecord

> [!NOTE]
> Etkinlik uygulamasından yayılan CustomTrackingRecords uygulamaGörünürlük ayarı tarafından filtreuygulanmaz.

İşlevsellik `implementationVisibility` <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> koddaki izleme profilinde aşağıdaki gibi belirtilir:

```csharp
TrackingProfile sampleTrackingProfile = new TrackingProfile()
{
    Name = "Sample Tracking Profile",
    ImplementationVisibility = ImplementationVisibility.RootScope
};
```

`implementationVisibility` İşlevsellik, <xref:System.Activities.Tracking.ImplementationVisibility.All> yapılandırma dosyasındaki izleme profilinde aşağıdaki gibi belirtilir:

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

İzleme `ImplementationVisibility` profilindeki ayar isteğe bağlıdır. Varsayılan olarak, değeri `RootScope`. Bu öznitelik için değerler de büyük/küçük harf duyarlıdır.

### <a name="tracking-profile-query-types"></a>İzleme Profili Sorgu Türleri

İzleme profilleri, belirli izleme kayıtları için iş akışı çalışma zamanını sorgulamanıza olanak tanıyan kayıtları izlemek için bildirimsel abonelikler olarak yapılandırılır. Farklı <xref:System.Activities.Tracking.TrackingRecord> nesne sınıflarına abone olsanız birkaç sorgu türü vardır. İzleme profilleri yapılandırmada veya kod aracılığıyla belirtilebilir. En yaygın sorgu türleri şunlardır:

- <xref:System.Activities.Tracking.WorkflowInstanceQuery>- Daha önce gösterildiği `Started` gibi iş akışı örneği yaşam döngüsü `Completed`değişiklikleri izlemek için bunu kullanın ve. <xref:System.Activities.Tracking.WorkflowInstanceQuery> Aşağıdaki abone olmak için kullanılan <xref:System.Activities.Tracking.TrackingRecord> nesneleri:

  - <xref:System.Activities.Tracking.WorkflowInstanceRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>

  Abone olunabilecek durumlar <xref:System.Activities.Tracking.WorkflowInstanceStates> sınıfta belirtilir.

  İş akışı örnek düzeyi izleme kayıtlarına abone olmak için `Started` <xref:System.Activities.Tracking.WorkflowInstanceQuery> kullanılan yapılandırma veya kod aşağıdaki örnekte gösterilmiştir.

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

- <xref:System.Activities.Tracking.ActivityStateQuery>- İş akışı örneğini oluşturan etkinliklerin yaşam döngüsü değişikliklerini izlemek için bunu kullanın. Örneğin, "E-Posta Gönder" etkinliği bir iş akışı örneği içinde her tamamlandığında izlemek isteyebilirsiniz. Bu sorgu, nesnelerin <xref:System.Activities.Tracking.TrackingParticipant> abone <xref:System.Activities.Tracking.ActivityStateRecord> olmak için gereklidir. Abone olunacak kullanılabilir durumlar <xref:System.Activities.Tracking.ActivityStates>.

  Etkinlik için kullanılan etkinlik durumu izleme kayıtlarını <xref:System.Activities.Tracking.ActivityStateQuery> abone `SendEmailActivity` etmek için kullanılan yapılandırma ve kod aşağıdaki örnekte gösterilmiştir.

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
  > Birden çok etkinlikStateQuery öğesi aynı ada sahipse, izleme profilinde yalnızca son öğedeki durumlar kullanılır.

- <xref:System.Activities.Tracking.ActivityScheduledQuery>- Bu sorgu, bir üst etkinlik tarafından yürütülmesi için zamanlanmış bir etkinliği izlemenize olanak sağlar. Sorgu, nesnelerin <xref:System.Activities.Tracking.TrackingParticipant> abone olması <xref:System.Activities.Tracking.ActivityScheduledRecord> için gereklidir.

  Zamanlanan `SendEmailActivity` <xref:System.Activities.Tracking.ActivityScheduledQuery> alt etkinlikle ilgili kayıtlara abone olmak için kullanılan yapılandırma ve kod aşağıdaki örnekte gösterilmiştir.

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

- <xref:System.Activities.Tracking.FaultPropagationQuery>- Bir etkinlik içinde oluşan hataların işlenmesini izlemek için bunu kullanın. Sorgu, nesnelerin <xref:System.Activities.Tracking.TrackingParticipant> abone olması <xref:System.Activities.Tracking.FaultPropagationRecord> için gereklidir.

  Hata yayılımı kullanılarak <xref:System.Activities.Tracking.FaultPropagationQuery> ilgili kayıtlara abone olmak için kullanılan yapılandırma ve kod aşağıdaki örnekte gösterilmiştir.

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

- <xref:System.Activities.Tracking.CancelRequestedQuery>- Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek için bunu kullanın. Sorgu, nesnelerin <xref:System.Activities.Tracking.TrackingParticipant> abone olması <xref:System.Activities.Tracking.CancelRequestedRecord> için gereklidir.

  Etkinlik iptali ile <xref:System.Activities.Tracking.CancelRequestedQuery> ilgili kayıtlara abone olmak için kullanılan yapılandırma ve kod aşağıdaki örnekte gösterilmiştir.

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

- <xref:System.Activities.Tracking.CustomTrackingQuery>- Kod etkinliklerinizde tanımladığınız olayları izlemek için bunu kullanın. Sorgu, nesnelerin <xref:System.Activities.Tracking.TrackingParticipant> abone olması <xref:System.Activities.Tracking.CustomTrackingRecord> için gereklidir.

  Özel izleme kayıtları kullanılarak <xref:System.Activities.Tracking.CustomTrackingQuery> ilgili kayıtlara abone olmak için kullanılan yapılandırma ve kod aşağıdaki örnekte gösterilmiştir.

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

- <xref:System.Activities.Tracking.BookmarkResumptionQuery>- İş akışı örneği içinde yer imi devamını izlemek için bunu kullanın. Bu sorgu, nesnelerin <xref:System.Activities.Tracking.TrackingParticipant> abone <xref:System.Activities.Tracking.BookmarkResumptionRecord> olmak için gereklidir.

  Yer imi devamı ile <xref:System.Activities.Tracking.BookmarkResumptionQuery> ilgili kayıtlara abone olmak için kullanılan yapılandırma ve kod aşağıdaki örnekte gösterilmiştir.

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

Ek açıklamalar, izleme kayıtlarını oluşturma süresinden sonra yapılandırılabilen bir değerle rasgele etiketlemenize olanak sağlar. Örneğin, birkaç iş akışında birkaç izleme kaydının "Mail Server" == "Mail Server1" ile etiketletilmesi isteyebilirsiniz. Bu, izleme kayıtlarını daha sonra sorgularken bu etikete sahip tüm kayıtları bulmayı kolaylaştırır.

Bunu gerçekleştirmek için, aşağıdaki örnekte gösterildiği gibi bir izleme sorgusuna bir ek açıklama eklenir.

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

### <a name="how-to-create-a-tracking-profile"></a>İzleme Profili Nasıl Oluşturulur?

İzleme sorgusu öğeleri, Bir XML yapılandırma dosyası veya [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] kodu kullanarak bir izleme profili oluşturmak için kullanılır. Burada, yapılandırma dosyası kullanılarak oluşturulan izleme profiline bir örnek verilmiştir.

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
> İş Akışı hizmet ana bilgisayarını kullanan bir WF için izleme profili genellikle bir yapılandırma dosyası kullanılarak oluşturulur. İzleme profilini ve izleme sorgusu API'sını kullanarak kodlu bir izleme profili oluşturmak da mümkündür.

XML yapılandırma dosyası olarak yapılandırılan bir profil, davranış uzantısı kullanılarak izleme katılımcısına uygulanır. Bu, daha sonraki bölümde açıklandığı gibi bir İş AkışıServiceHost eklenir Bir [İş Akışı için İzleme Yapılandırma.](configuring-tracking-for-a-workflow.md)

Ana bilgisayar tarafından yayılan izleme kayıtlarının ayrıntılılığı, izleme profiliiçindeki yapılandırma ayarları yla belirlenir. Bir izleme katılımcısı, izleme profiline sorgular ekleyerek kayıtları izlemeye abone dir. Tüm izleme kayıtlarına abone olmak için, izleme profilinin her\*sorgudaki ad alanlarında " " kullanarak tüm izleme sorgularını belirtmesi gerekir.

İzleme profillerinin yaygın örneklerinden bazıları aşağıda verilmiştir.

- İş akışı örneği kayıtlarını ve hatalarını elde etmek için bir izleme profili.

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
- [Windows Server App Kumaş İzleme](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))
- [Uygulama Kumaşı ile Uygulamaların İzlenmesi](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))
