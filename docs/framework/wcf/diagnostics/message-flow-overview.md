---
title: İleti Akışı Genel Bakış
ms.date: 03/30/2017
ms.assetid: fb0899e1-84cc-4d90-b45b-dc5a50063943
ms.openlocfilehash: 0bfbd1523f1d5db4a94cf3af03a03779af14655d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795968"
---
# <a name="message-flow-overview"></a>İleti Akışı Genel Bakış
Birbirine bağlı hizmetler içeren dağıtılmış bir sistemde, hizmetler arasında causal ilişkilerinin belirlenmesi gerekir. Durum izleme, sorun giderme ve kök neden analizi gibi kritik senaryoları desteklemek için bir istek akışının parçası olan çeşitli bileşenleri anlamak önemlidir. .NET Framework 4 ' te çeşitli hizmetler arasındaki izlemelerin bağıntısını etkinleştirmek için aşağıdaki özellikler aracılığıyla destek ekledik:

- Analitik izleme: Windows için olay Izleme (ETW) kullanan yüksek performanslı ve düşük ayrıntı düzeyi izleme özelliği.

- WCF/WF hizmetleri için uçtan uca etkinlik modeli: Bu özellik, <xref:System.ServiceModel> ve <xref:System.Workflow.ComponentModel> ad alanları tarafından oluşturulan izlemelerin bağıntısını destekler.

- WF için ETW izleme: Bu özellik, iş akışının geçerli durumuna ve ilerlemesini görünürlük sağlamak için WF hizmetleri tarafından oluşturulan izleme kayıtlarını kullanır.

 İzleme veya izleme kaydında günlüğe kaydedilen hatalar, kod kusurlarını veya hatalı biçimlendirilmiş iletileri bulmak için kullanılabilir. Olayın ileti üstbilgisindeki bağıntı düğümünün ActivityId özelliği, hatalı etkinliği belirlemede kullanılabilir. İleti akışı izlemeyi etkinlik KIMLIĞINE göre etkinleştirmek için bkz. [Ileti akışı Izlemeyi yapılandırma](./etw/configuring-message-flow-tracing.md). Bu konuda, başlangıç öğreticisinde oluşturulan projede ileti akışı izlemenin nasıl etkinleştirileceği gösterilmektedir.

### <a name="to-enable-message-flow-tracing-in-the-getting-started-tutorial"></a>Başlangıç öğreticisinde ileti akışı izlemeyi etkinleştirmek için

1. **Başlat**, **çalıştır**ve girerek `eventvwr.exe`Olay Görüntüleyicisi açın.

2. Analitik izlemeyi etkinleştirmediyseniz, **uygulamalar ve hizmetler günlükleri**, **Microsoft**, **Windows**, **uygulama sunucusu-uygulamalar**' ı genişletin. **Görünüm**, **analitik ve hata ayıklama günlüklerini göster**' i seçin. **Analitik** öğesine sağ tıklayın ve **günlüğü etkinleştir**' i seçin. İzlemelerin görüntülenebilmesi için Olay Görüntüleyicisi açık bırakın.

3. Visual Studio 2012 ' de başlangıç [öğreticisinde](../getting-started-tutorial.md) oluşturulan örneği açın. Hizmetin oluşturulabilmesi için Visual Studio 2012 ' i yönetici olarak çalıştırmanız gerektiğini unutmayın. WCF örnekleri yüklüyse, öğreticide oluşturulan tamamlanmış projeyi içeren [Başlarken](../samples/getting-started-sample.md)' i açabilirsiniz.

4. **Hizmet** projesine sağ tıklayın ve **Ekle**, **Yeni öğe**' yi seçin. **Uygulama yapılandırma dosyası** ' nı seçin ve **Tamam**' ı tıklatın.

5. Önceki adımda oluşturulan app. config dosyasına aşağıdaki kodu ekleyin.

    ```xml
    <system.serviceModel>
      <diagnostics>
        <endToEndTracing propagateActivity="true" messageFlowTracing="true"/>
      </diagnostics>
    </system.serviceModel>
    ```

6. CTRL + F5 tuşlarına basarak sunucu uygulamasını hata ayıklamadan yürütün. **İstemci projesine** sağ tıklayıp **Hata Ayıkla**, **Yeni örnek Başlat**' ı seçerek istemci projesini yürütün.

7. İstemciden sunucuya olayları izlemek için, aşağıdakileri Istemci projesindeki uygulama yapılandırma dosyasına ekleyin.

    ```xml
    <diagnostics>
      <endToEndTracing propagateActivity="true" messageFlowTracing="true"/>
    </diagnostics>
    ```

8. İstemcide Program.cs ' de, aşağıdaki using ifadesini ekleyin.

    ```csharp
    using System.Diagnostics;
    ```

9. İstemci projesindeki program.cs dosyasındaki Main yönteminde, Izleme GUID 'sini olay günlüğüne yayılacağı şekilde ayarlayın.

    ```csharp
    Guid guid = Guid.NewGuid();
    Trace.CorrelationManager.ActivityId = guid;
    ```

10. **Analitik** günlüğü yenileyin ve inceleyin.  Olay KIMLIĞI 220 olan bir olay arayın.  Olayı seçin ve Önizleme bölmesindeki **Ayrıntılar** sekmesine tıklayın. Bu olay çağıran etkinliğin bağıntı KIMLIĞINI içerir.

    ```xml
    <Correlation ActivityID="{A066CCF1-8AB3-459B-B62F-F79F957A5036}" />
    ```

    > [!NOTE]
    > ActivityID içindeki aynı GUID 'ye sahip tüm olaylar bir istekle ilgilidir. Bu, belirli bir istemciden gelen iletileri belirli bir hizmete ilişkilendirmek için kullanılabilir. İstemci başka bir hizmet olarak adlandırılrsa, aynı istemci ActivityId ile tanımlanabilir.

11. Bazı durumlarda, ActivityId özgün GUID 'den yeni bir ActivityId 'ye değişebilir. Bu durumda, bir aktarım olayı yayınlanır. Bu olay KIMLIĞI 499 ' dir ve olay üst bilgide aşağıdaki verileri içerir.

    ```xml
    <Event xmlns="http://schemas.microsoft.com/win/2004/08/events/event">
        <System>
            <Provider Name="Microsoft-Windows-Application Server-Applications" Guid="{c651f5f6-1c0d-492e-8ae1-b4efd7c9d503}" />
            <EventID>499</EventID>
            ...
            <Correlation ActivityID="{A066CCF1-8AB3-459B-B62F-F79F957A5036}" RelatedActivityID="{85FC0930-9C49-42DA-804B-A7368104BD1B}" />
            ...
       </System>
    </Event>
    ```

    > [!NOTE]
    > Aktarım olayı, etkin ActivityId 'nin değişikliğini ActivityId olarak belirtilen GUID 'den relatedActivityId olarak belirtilen GUID 'ye kaydeder. Aktarım olayı oluşturulduktan sonra, tüm olaylar ActivityId olarak yeni GUID 'YI içerir.
