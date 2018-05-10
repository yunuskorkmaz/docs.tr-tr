---
title: İleti Akışı Genel Bakış
ms.date: 03/30/2017
ms.assetid: fb0899e1-84cc-4d90-b45b-dc5a50063943
ms.openlocfilehash: aea0ca4c5a8574f6039cd055561ce7da0099841b
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="message-flow-overview"></a>İleti Akışı Genel Bakış
Birbirine bağlı hizmetleri içeren dağıtılmış bir sistemde hizmetleri arasında nedensel ilişkilerini belirlemek gereklidir. Kök neden analizi ve izleme, sorun giderme sistem durumu gibi kritik senaryoları desteklemek için bir istek akışının bir parçası olan çeşitli bileşenleri anlamak önemlidir. Aşağıdaki özellikler sayesinde destek eklediğimiz izlemeleri bağıntı .NET Framework 4'te çeşitli hizmetler arasında etkinleştirmek için:  
  
-   Çözümleme izleme: yüksek performans ve olay izleme için Windows (ETW) kullanarak düşük ayrıntı izleme özelliği.  
  
-   WCF/WF Hizmetleri için uçtan uca etkinlik modeli: tarafından oluşturulan izlemeleri bağıntı bu özelliği destekleyen <xref:System.ServiceModel> ve <xref:System.Workflow.ComponentModel> ad alanları.  
  
-   WF izleme ETW: Bu özellik iş akışının geçerli durumuna ve ilerleme görünürlük sağlamak için WF Hizmetleri tarafından oluşturulan izleme kayıtları kullanır.  
  
 Bir izleme veya kayıt izleme günlüğe hataları, kod hataları veya hatalı oluşturulmuş iletileri bulmak için kullanılabilir. Olayın ileti üstbilgisinde bağıntı düğümün ActivityID özelliği hataya neden olan etkinliğini belirlemek için kullanılabilir. Etkinlik Kimliği tarafından ileti akışı izlemeyi etkinleştirmek için bkz: [ileti akışı izlemeyi yapılandırma](../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md). Bu konu, Başlarken öğreticisinde oluşturulan projesinde ileti akışı izlemeyi etkinleştirmek gösterilmiştir.  
  
### <a name="to-enable-message-flow-tracing-in-the-getting-started-tutorial"></a>Başlarken Öğreticisi ileti akışı izlemeyi etkinleştirmek için  
  
1.  Olay Görüntüleyicisi'ni tıklatarak açın **Başlat**, **çalıştırmak**ve girerek `eventvwr.exe`.  
  
2.  Çözümleme izleme etkinleştirmediyseniz genişletin **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**, **uygulama sunucusu-uygulamalar** . Seçin **Görünüm**, **Göster Analitik ve hata ayıklama günlüklerini**. Sağ **analitik** seçip **günlüğü etkinleştir**. Böylece izlemeleri görüntülenebilmesi için Olay Görüntüleyicisi'ni kapatmayın.  
  
3.  Oluşturulan örnek açmak [başlangıç Öğreticisi](../../../../docs/framework/wcf/getting-started-tutorial.md) içinde [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]. Çalıştırmalısınız Not [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] yönetici olarak böylece hizmet oluşturulabilir. Yüklü WCF örnekleri varsa açabilirsiniz [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), öğreticide oluşturulan projeyi içerir.  
  
4.  Sağ **hizmet** proje ve seçin **Ekle**, **yeni öğe**. Seçin **uygulama yapılandırma dosyası** tıklatıp **Tamam**.  
  
5.  Önceki adımda oluşturulan App.Config dosyasına aşağıdaki kodu ekleyin.  
  
    ```xml  
    <system.serviceModel>  
      <diagnostics>  
        <endToEndTracing propagateActivity="true" messageFlowTracing="true"/>  
      </diagnostics>  
    </system.serviceModel>  
    ```  
  
6.  Sunucu uygulaması, CTRL + F5'e basarak hata ayıklama olmadan yürütün. İstemci projesine sağ tıklayarak yürütme **istemci** proje ve seçerek **hata ayıklama**, **Başlat yeni örnek**.  
  
7.  İstemciden sunucuya olayları izlemek için aşağıdaki istemci projesine uygulama yapılandırma dosyasında ekleyin.  
  
    ```xml  
    <diagnostics>  
      <endToEndTracing propagateActivity="true" messageFlowTracing="true"/>  
    </diagnostics>  
    ```  
  
8.  İstemcisindeki program.cs içinde aşağıdaki Using deyimini ekleyin.  
  
    ```  
    using System.Diagnostics;  
    ```  
  
9. İstemci projesindeki program.cs dosyasını ana yönteminde olay günlüğü'nde dağıtılmasını izleme GUID'i ayarlayın.  
  
    ```  
    Guid guid = Guid.NewGuid();  
    Trace.CorrelationManager.ActivityId = guid;  
    ```  
  
10. Yenileyin ve incelemek **analitik** günlük.  Olay Kimliği 220 sahip bir olay arayın.  Olay seçin ve tıklayın **ayrıntıları** önizleme bölmesinde sekmesi. Bu olay çağırma etkinliğinin bağıntı kimliği içerir.  
  
    ```xml  
    <Correlation ActivityID="{A066CCF1-8AB3-459B-B62F-F79F957A5036}" />  
    ```  
  
    > [!NOTE]
    >  Tüm olayları ActivityID içinde aynı GUID'ye sahip bir istekle ilişkili. Bu, belirli bir hizmeti belirli bir istemciden gelen iletileri ilişkilendirmek için kullanılabilir. İstemci başka bir hizmet olarak adlandırılan, aynı istemci tarafından ActivityID tanımlanamadı.  
  
11. Bazı durumlarda, ActivityID adresinden özgün GUID yeni ActivityID olarak değiştirebilirsiniz. Bu durumda, bir aktarım olayını yayınlanır. Bu olay kimliği 499 olduğu ve olay üstbilgisinde aşağıdaki veri içerir.  
  
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
    >  Aktarım olayını ActivityID GUID RelatedActivityID belirtilen olarak belirtilen Guid'den etkin ActivityID değişiklik kaydeder. Aktarım olayını yayılan sonra tüm olayları yeni bir GUID ActivityID içerir.
