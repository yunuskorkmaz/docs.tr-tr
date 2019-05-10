---
title: İleti Akışı Genel Bakış
ms.date: 03/30/2017
ms.assetid: fb0899e1-84cc-4d90-b45b-dc5a50063943
ms.openlocfilehash: 009dd05ab299b92ee5f5cafd1c2131a2e6eb0132
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650250"
---
# <a name="message-flow-overview"></a>İleti Akışı Genel Bakış
Birbirine bağlı hizmetleri içeren dağıtılmış bir sistemde hizmetler arasında nedensel ilişkilerini belirlemek gereklidir. Kök neden analizi ve izleme, sorun giderme durumu gibi önemli senaryoları desteklemek için bir istek akışının bir parçası olan çeşitli bileşenleri anlamak önemlidir. İzlemeler, .NET Framework 4'te çeşitli hizmetler arasındaki bağıntıyı etkinleştirmek için aşağıdaki özellikler sayesinde desteği ekledik:

- Çözümleme izleme: Yüksek performanslı ve düşük ayrıntı izleme özelliği için olay izleme Windows (ETW) kullanarak.

- WCF/WF Hizmetleri için model uçtan uca etkinlik: Bu özellik, izlemeleri tarafından oluşturulan bağıntısı destekler <xref:System.ServiceModel> ve <xref:System.Workflow.ComponentModel> ad alanları.

- ETW İzleme WF için: Bu özellik, iş akışının geçerli durumunu ve ilerlemesini görünürlük sağlamak için WF Hizmetleri tarafından oluşturulan izleme kayıtları kullanır.

 Bir izleme veya kayıt izleme hatanın günlüğe kaydedilip kaydedilmediğine kod kusurlarını veya yanlış biçimlendirilmiş iletiler bulmak için kullanılabilir. Olay iletisi üst bilgisindeki bağıntı düğümün ActivityID özelliği hataya neden olan etkinliğini belirlemek için kullanılabilir. Etkinlik Kimliğine göre ileti akışı izlemeyi etkinleştirmek için bkz: [ileti akışı izlemeyi yapılandırma](../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md). Bu konu, ileti akışı izlemeyi kullanmaya başlama öğreticisinde oluşturulan projedeki etkinleştirme gösterir.

### <a name="to-enable-message-flow-tracing-in-the-getting-started-tutorial"></a>Başlarken öğreticide ileti akışı izlemeyi etkinleştirmek için

1. Olay Görüntüleyicisi'ni tıklatarak açın **Başlat**, **çalıştırma**, girerek `eventvwr.exe`.

2. Çözümleme izleme etkinleştirmediyseniz genişletin **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**, **uygulama sunucu uygulamaları** . Seçin **görünümü**, **Göster Analitik ve hata ayıklama günlüklerini**. Sağ **analitik** seçip **günlüğü etkinleştir**. Olay Görüntüleyicisi, böylece izlemeleri görüntülenebilir açık bırakın.

3. Oluşturulan örnek açın [başlangıç Öğreticisi](../../../../docs/framework/wcf/getting-started-tutorial.md) Visual Studio 2012. Böylece hizmet oluşturulabilmesi için yönetici olarak Visual Studio 2012 çalıştırmanız gerektiğini unutmayın. Yüklü WCF örnekleri varsa açabileceğiniz [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), öğreticide oluşturulan projeyi içerir.

4. Sağ **hizmet** seçin ve proje **Ekle**, **yeni öğe**. Seçin **uygulama yapılandırma dosyası** tıklatıp **Tamam**.

5. Önceki adımda oluşturulan App.Config dosyasına aşağıdaki kodu ekleyin.

    ```xml
    <system.serviceModel>
      <diagnostics>
        <endToEndTracing propagateActivity="true" messageFlowTracing="true"/>
      </diagnostics>
    </system.serviceModel>
    ```

6. CTRL + F5 tuşlarına basarak hata ayıklama olmadan sunucu uygulamasını çalıştırın. İstemci projesi sağ tıklayarak yürütme **istemci** proje ve seçerek **hata ayıklama**, **yeni örnek Başlat**.

7. İstemciden sunucuya olayları izlemek için istemci projesindeki uygulama yapılandırma dosyasına aşağıdakileri ekleyin.

    ```xml
    <diagnostics>
      <endToEndTracing propagateActivity="true" messageFlowTracing="true"/>
    </diagnostics>
    ```

8. İstemci program.cs'ye aşağıdaki Using deyimini ekleyin.

    ```csharp
    using System.Diagnostics;
    ```

9. İstemci projesindeki program.cs dosyasının ana yöntemde olay günlüğünde dağıtılmasını izleme GUID'i ayarlayın.

    ```csharp
    Guid guid = Guid.NewGuid();
    Trace.CorrelationManager.ActivityId = guid;
    ```

10. Yenileyin ve incelemek **analitik** günlük.  Olay Kimliği 220 sahip bir olay olup olmadığına bakın.  Olay seçin ve tıklayın **ayrıntıları** önizleme bölmesinde sekmesi. Bu olay arama etkinliği için bağıntı Kimliğini içerir.

    ```xml
    <Correlation ActivityID="{A066CCF1-8AB3-459B-B62F-F79F957A5036}" />
    ```

    > [!NOTE]
    >  Tüm olaylar aynı GUID etkinlik kimliği ile bir istekle ilişkili. Bu, belirli bir istemci bir kuyruktan belirli bir hizmete ilişkilendirmek için kullanılabilir. İstemci başka bir hizmet çağrılır, aynı istemci tarafından ActivityID tanımlanamadı.

11. Bazı durumlarda, etkinlik kimliği için yeni bir etkinlik kimliği özgün GUID'ini değiştirebilirsiniz. Bu durumda, bir aktarım olayını yayınlanır. Bu olay kimliği 499 ve olay başlığı aşağıdaki verileri içerir.

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
    >  Aktarım olayını, etkin RelatedActivityID ActivityID GUID olarak belirtilen olarak belirtilen GUID etkinlik değişikliği kaydeder. Aktarım olayını yayılan sonra tüm olayları yeni bir GUID etkinlik kimliği içerir.
