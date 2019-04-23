---
title: 'İlişkilendirilmiş İzlemeleri Görüntülemek ve Sorun Gidermek için Hizmet İzleme Görüntüleyicisini Kullanma '
ms.date: 03/30/2017
ms.assetid: 05d2321c-8acb-49d7-a6cd-8ef2220c6775
ms.openlocfilehash: dd5fe08054b3a10c1663a7dd7dab5f9de5327cbb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59329056"
---
# <a name="using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting"></a>İlişkilendirilmiş İzlemeleri Görüntülemek ve Sorun Gidermek için Hizmet İzleme Görüntüleyicisini Kullanma 
Bu konuda izleme verilerinin biçimini tanımlar ve uygulamanızda sorun giderme için hizmet izleme görüntüleyicisini kullanma yaklaşımları görüntüleme.  
  
## <a name="using-the-service-trace-viewer-tool"></a>Hizmet izleme görüntüleyicisini kullanma  
 Windows Communication Foundation (WCF) hizmet izleme Görüntüleyicisi aracı bir hata nedenini bulmak için WCF dinleyicileri tarafından üretilen tanılama izlemeleri ilişkilendirmenize yardımcı olur. Aracı kolayca görünümünde, Grup ve izlemeler filtre, böylece tanılayabilir, onarma ve WCF hizmetleri ile ilgili sorunlar doğrulamak için bir yol sağlar. Bu aracı kullanma hakkında daha fazla bilgi için bkz. [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).  
  
 Bu konuda çalıştırılarak oluşturulan izlemeleri ekran görüntüleri içeren [izleme ve ileti günlüğe kaydetme](../../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) kullanarak görüntülendiğinde, örnek [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Bu konuda izleme içerik, etkinlikler ve bunların bağıntı anlama ve sorun giderme sırasında izlemeleri çok sayıda analiz etme gösterilir.  
  
## <a name="viewing-trace-content"></a>İzleme içeriği görüntüleme  
 İzleme olayı, aşağıdaki en önemli bilgileri içerir:  
  
-   Etkinlik adı olarak ayarlandığında.  
  
-   Arabellek zaman.  
  
-   İzleme düzeyi.  
  
-   İzleme kaynak adı.  
  
-   İşlem adı.  
  
-   İş parçacığı kimliği.  
  
-   Microsoft Docs izlemeye ilgili daha fazla bilgi edinmek, bir hedefe işaret eden bir URL bir izleme benzersiz tanımlayıcısı.  
  
 Tüm bunların üst sağ panelde hizmet izleme görüntüleyicisini ya da görülebilir **temel bilgileri** biçimlendirilmiş görünümünde bir izleme seçerken sağ bölmenin bölümü.  
  
> [!NOTE]
>  İstemciyi ve hizmeti aynı makinede ise, iki uygulama izlemelerini mevcut olacaktır. Bunları kullanarak filtrelenebilir **işlem adı** sütun.  
  
 Ayrıca, biçimlendirilmiş görünümü, ayrıca izleme ve kullanılabilir olduğunda ek ayrıntılı bilgi için bir açıklama sağlar. İkinci özel durum türünü ve iletisini, çağrı yığınlarını, ileti eylemi / için alanları ve diğer özel durum bilgileri içerebilir.  
  
 XML Görünümü'nde yararlı xml etiketleri şunlardır:  
  
-   `<SubType>` (izleme düzeyi).  
  
-   `<TimeCreated>`.  
  
-   `<Source>` (izleme kaynak adı).  
  
-   `<Correlation>` (izleme gösterilirken etkinlik kimliği ayarlanır).  
  
-   `<Execution>` (kimlik) işlem ve iş parçacığı.  
  
-   `<Computer>`.  
  
-   `<ExtendedData>`, dahil olmak üzere `<Action>`, `<MessageID>` ve `<ActivityId>` ileti üstbilgisinde bir ileti gönderirken ayarlayın.  
  
 "Gönderilen bir kanal üzerinden ileti" izleme incelerseniz, aşağıdaki içeriği görebilirsiniz.  
  
```xml  
<E2ETraceEvent xmlns="http://schemas.microsoft.com/2004/06/E2ETraceEvent">  
   <System xmlns="http://schemas.microsoft.com/2004/06/windows/eventlog/system">  
      <EventID>262163</EventID>  
      <Type>3</Type>  
      <SubType Name="Information">0</SubType>  
      <Level>8</Level>  
      <TimeCreated SystemTime="2006-08-04T18:45:30.8491051Z" />  
      <Source Name="System.ServiceModel" />  
       <Correlation ActivityID="{27c6331d-8998-43aa-a382-03239013a6bd}"/>  
       <Execution ProcessName="client" ProcessID="1808" ThreadID="1" />  
       <Channel />  
       <Computer>TEST1</Computer>  
   </System>  
   <ApplicationData>  
       <TraceData>  
          <DataItem>  
             <TraceRecord xmlns="http://schemas.microsoft.com/2004/10/E2ETraceEvent/TraceRecord" Severity="Information">  
                 <TraceIdentifier>http://msdn.microsoft.com/library/System.ServiceModel.Channels.MessageSent.aspx</TraceIdentifier>  
                 <Description>Sent a message over a channel.</Description>  
                 <AppDomain>client.exe</AppDomain>  
                 <Source>System.ServiceModel.Channels.ClientFramingDuplexSessionChannel/35191196</Source>  
                <ExtendedData xmlns="http://schemas.microsoft.com/2006/08/ServiceModel/MessageTransmitTraceRecord">  
  
                  <MessageProperties>  
                     <AllowOutputBatching>False</AllowOutputBatching>  
                  </MessageProperties>  
                  <MessageHeaders>  
                     <Action d4p1:mustUnderstand="1" xmlns:d4p1="http://www.w3.org/2003/05/soap-envelope" xmlns="http://www.w3.org/2005/08/addressing">http://Microsoft.ServiceModel.Samples/ICalculator/Multiply</Action>  
                     <MessageID xmlns="http://www.w3.org/2005/08/addressing">urn:uuid:7c6670d8-4c9c-496e-b6a0-2ceb6db35338</MessageID>  
                     <ActivityId CorrelationId="b02e2189-0816-4387-980c-dd8e306440f5" xmlns="http://schemas.microsoft.com/2004/09/ServiceModel/Diagnostics">27c6331d-8998-43aa-a382-03239013a6bd</ActivityId>  
                     <ReplyTo xmlns="http://www.w3.org/2005/08/addressing">  
                        <Address>http://www.w3.org/2005/08/addressing/anonymous</Address>  
                    </ReplyTo>  
                    <To d4p1:mustUnderstand="1" xmlns:d4p1="http://www.w3.org/2003/05/soap-envelope" xmlns="http://www.w3.org/2005/08/addressing">net.tcp://localhost/servicemodelsamples/service</To>  
                  </MessageHeaders>  
                  <RemoteAddress>net.tcp://localhost/servicemodelsamples/service</RemoteAddress>  
                </ExtendedData>  
            </TraceRecord>  
          </DataItem>  
       </TraceData>  
   </ApplicationData>  
</E2ETraceEvent>  
```  
  
## <a name="servicemodel-e2e-tracing"></a>ServiceModel E2E izleme  
 Zaman `System.ServiceModel` izleme kaynağı ile ayarlanmış bir `switchValue` dışındaki kapalı, ve `ActivityTracing`, WCF, etkinlikler ve aktarımları için WCF işlemi oluşturur.  
  
 Grupları, işleme birimine tüm izlemeleri ilgili işleme bir mantıksal birim bir etkinliktir. Örneğin, her istek için bir etkinlik tanımlayabilirsiniz. Aktarımları uç noktaları içindeki etkinlikleri arasındaki nedensel bir ilişki oluşturun. Etkinlik Kimliği yayma, uç noktalar genelinde etkinliklerini ilişkilendirmek sağlar. Bu ayarlayarak yapılabilir `propagateActivity` = `true` her uç noktasında yapılandırması. Etkinlikler, aktarımları ve yayma hata bağıntı gerçekleştirmenize olanak sağlar. Bu şekilde, bir hatanın kök nedenini daha hızlı bir şekilde bulabilirsiniz.  
  
 İstemcide, bir WCF etkinlik (örneğin, açık ChannelFactory, Ekle, bölme ve benzeri.) her nesne modeli çağrısı için oluşturulur. Her işlem çağrıları, bir "İşlem Action" etkinlik içinde işlenir.  
  
 Aşağıdaki ekran görüntüsünde, ayıklanan gelen [izleme ve ileti günlüğe kaydetme](../../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) örnek sol panelde, oluşturma zamanı tarafından sıralanan istemci işleminde, oluşturulan etkinlikleri listesini görüntüler. Etkinlikleri kronolojik bir listesi verilmiştir:  
  
-   Kanal fabrikası (ClientBase) oluşturulur.  
  
-   Kanal fabrikası açıldı.  
  
-   Eylem Ekle işlendi.  
  
-   Güvenli oturum (ilk isteğe bu OLUŞTU) ve işlenen üç güvenlik altyapısı yanıt iletilerini ayarlayın: K, RSTR, SCT (işlem iletisi 1, 2, 3).  
  
-   Çıkarma birden çok kez işlenen ve bölme ister.  
  
-   Kapalı kanal fabrikası ve bunun yapılması ve güvenli oturum kapalı güvenlik ileti yanıtı iptal işlenir.  
  
 WsHttpBinding nedeniyle güvenlik altyapısı iletileri görüyoruz.  
  
> [!NOTE]
>  WCF'de, başlangıçta ayrı bir etkinlik (işlem iletisi) işlenmekte olan yanıt iletilerini göstereceğiz önce aktarım aracılığıyla istek iletisi içeren karşılık gelen işlem eylem etkinliği için biz bunları ilişkilendirin. Bu altyapı ileti ve zaman uyumsuz istekler gerçekleşir ve biz gerekir ileti incelemek, ActivityID üstbilgi okuyun ve tanımlamak için ilişkilendirmek için bu kimliğe sahip mevcut işlem eylem etkinliği Bunun nedeni. Zaman uyumlu istekleri için yanıt engelliyor ve bu nedenle yanıt ilişkili işlem eylemi bildirin.  
  
WCF istemci etkinlikler oluşturma zamanı (sol paneli) ve iç içe geçmiş etkinlikleri ve izlemeleri (üst, sağ, paneli) göre listelenen aşağıdaki resimde gösterilmektedir:

 ![WCF istemcisi oluşturma zamanı tarafından listelenen etkinlikleri gösteren ekran görüntüsü.](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/wcf-client-activities-creation-time.gif)  
  
 Sol bölmede bulunan bir etkinlik seçtiğimizde, iç içe geçmiş etkinlikleri ve izlemelerle üst Sağdaki panelde görebiliriz. Bu nedenle, bir azaltılmış budur etkinliklerinin listesini hiyerarşik görünümü sol tarafta seçili üst aktivitesini temel alarak. Seçili işlem Eylem Ekle yapılan ilk istek olduğundan, bu etkinlik, güvenli oturum yedekleme kümesi etkinliği (aktarımı geri aktarmak için) içeren ve işlenmesini ekleme eylemi için izler.  
  
 İşlem Eylem Ekle etkinliği sol bölmede çift tıkladıktan, eklenecek ilgili istemci WCF etkinlikleri grafik gösterimi görebiliriz. İlk soldaki Kök etkinlik (0000), varsayılan etkinlik olduğu etkinliğidir. WCF dışında ortam etkinlik aktarır. Bu tanımlı değil, WCF dışında 0000 aktarır. Burada, ikinci etkinlik işlem eylem eklemek, dışında 0 aktarır. Daha sonra Kurulum güvenli oturum bakın.  

 Aşağıdaki görüntüde, etkinlikleri, özel ortam etkinlik (burada 0), bir WCF istemcisi graf görünümünü gösterilmektedir eyleminin devam ve güvenli oturum ayarlayın:   

 ![İzleme görüntüleyicisinde ortam etkinliği ve işlem eylemini gösteren grafik.](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/wcf-activities-graph-ambient-process.gif)   
  
 Üst Sağdaki panelde, işlem Eylem Ekle etkinliği ilgili tüm izlemeleri görebiliriz. Özellikle, biz istek iletisi ("gönderilen bir kanal üzerinden ileti") gönderdiğiniz ve aynı etkinlik ("alınan bir kanal üzerinden ileti") yanıt alındı. Bu, aşağıdaki grafikte gösterilir. Anlaşılsın diye, güvenli oturum etkinliği kurma grafikte daraltılmıştır.  
  
 Aşağıdaki görüntüde, izlemeler işlem eylem etkinliği için bir listesini gösterir. Biz isteği göndermek ve aynı etkinliğin yanıtı alırsınız.
 
 ![Ekran görüntüsü, izleme işlemi eylem etkinliği izlemelerini listesini gösteren Görüntüleyicisi](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/process-action-traces.gif)  
  
 Burada yalnızca açıklık için istemci izlemelerini yüklediğimiz, ancak hizmet izlemeleri (istek iletisi alındı ve gönderilen yanıt iletisi) aynı etkinliğin Ayrıca aracı yüklü olmaları durumunda görünür ve `propagateActivity` ayarlandı `true.` bunu bir sonraki çizimde gösterilmektedir.  
  
 Hizmette etkinlik modeli WCF kavramlara şu şekilde eşlenir:  
  
1. Biz, oluşturmak ve bir ServiceHost (Bu konakla ilgili birkaç etkinlik örneği için söz konusu olduğunda güvenlik oluşturabilir) açın.  
  
2. Dinleme, etkinlik ServiceHost içinde her dinleyici için (ile aktarımları açık ServiceHost içine ve dışına) oluştururuz.  
  
3. Dinleyici istemci tarafından başlatılan iletişim istek algıladığında istemci tarafından gönderilen tüm baytlar işlenme "Bayt alma" etkinlik için aktarır. Bu etkinlik, istemci-hizmet etkileşim sırasında gerçekleşen bağlantı hataları görebiliriz.  
  
4. İletiye karşılık gelen her kümesi alınan bayt için Biz bu bayt "İşlemi iletisi" etkinliğinde, WCF ileti nesnesi oluştururuz burada işleyin. Bu etkinlik, hatalı bir zarf veya hatalı bir ileti ile ilgili hataları görüyoruz.  
  
5. İleti oluşturulduğunda, biz bir işlem eylem etkinliği aktarın. Varsa `propagateActivity` ayarlanır `true` hem istemci hem de hizmet üzerinde bu etkinlik istemcide tanımlanan ve daha önce açıklanan aynı kimliğe sahip. İstekle ilişkili tüm izlemeleri WCF'de yayılan yanıt ileti işleme dahil olmak üzere bu etkinliğe olduğundan bu aşamadan biz doğrudan bağıntı uç noktalar genelinde fayda başlayın.  
  
6. İşlem dışı eylem için kullanıcı kodunda WCF'de yayılan gördüğünüzden yayılan izlemeleri yalıtmak için bir "Kullanıcı kodu yürütme" etkinlik oluştururuz. Önceki örnekte, "Hizmet Ekle yanıt gönderir" izleme "Yürütme kullanıcı kodu" etkinlik değil istemci tarafından yayılan etkinlik varsa yayılır.  
  
 Aşağıdaki çizimde, ilk soldaki Kök etkinlik (0000), varsayılan etkinlik olduğu etkinliğidir. Sonraki üç ServiceHost açmak için etkinliklerdir. Dinleyici etkinliktir sütunda 5 ve kalan etkinlikleri (6-8), kullanıcı kodu etkinleştirmesi için işleme bayt gelen iletiyi WCF işlenmesini açıklayın.  

 Aşağıdaki resimde, bir WCF Hizmeti etkinlikleri graf görünümünü gösterir:   

 ![Ekran görüntüsü, izleme WCF Hizmeti etkinliklerin listesini gösteren Görüntüleyicisi](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/wcf-service-activities.gif)  

 Aşağıdaki ekran görüntüsünde hem istemci hem de hizmet etkinlikleri gösterir ve eylem işlem Ekle etkinliği (turuncu) süreçler arasında vurgular. Oklar, istemci ile hizmet tarafından gönderilen ve alınan istek ve yanıt iletilerinin ilgilidir. İşlem eyleminin izlemeleri graftaki işlemler arasında ayrılmış, ancak aynı etkinliğin sağ panelde bir parçası olarak gösterilir. Bu panelde alınan ve işlenen iletiler için hizmet izlemeleri ardından gönderilen iletiler için istemci izlemelerini görebiliriz.  
  
 Aşağıdaki görüntülerin her iki WCF hizmet ve istemci etkinliğini graf görünümünü gösterir  
 
 ![İzleme görüntüleyicisini her iki WCF hizmet ve istemci etkinliğini gösteren grafik.](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/wcf-client-service-activities.gif)   
  
 Aşağıdaki hata senaryosunda, hata ve uyarı izlemeleri hizmet ve istemci ilgilidir. Bir özel durum kullanıcı kodunda (bir uyarı içeren en sağdaki yeşil etkinliği izleme için özel "hizmeti, kullanıcı kodunda bu isteği işleyemiyor.") hizmeti ilk durum. İstemciye bir yanıt gönderildiğinde, bir uyarı izleme hata iletisi (sol pembe etkinliği) belirtmek için tekrar yayılır. İstemci, hizmete bağlantıyı durdurur, WCF istemcisi (sol tarafındaki sarı etkinliği), ardından kapatır. Hizmet bir hata (sağdaki uzun pembe etkinliği) oluşturur.  
  
 ![İzleme görüntüleyicisini kullanma](../../../../../docs/framework/wcf/diagnostics/tracing/media/wcfc-e2etrace9s.gif "wcfc_e2etrace9s")  
Hizmet ve istemci hatası bağıntı  
  
 Bu izlemeler üretmek için kullanılan örnek wsHttpBinding kullanarak zaman uyumlu istekleri dizisidir. Güvenlik olmadan veya zaman uyumsuz istekler, burada işlem eylem etkinliği zaman uyumsuz çağrı oluşturan başlangıç ve bitiş işlemleri kapsayan ve bir geri çağırma etkinliği aktarmalarıyla gösterir senaryoları için bu grafik sapmalar vardır. Ek senaryoları hakkında daha fazla bilgi için bkz. [uçtan uca izleme senaryoları](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).  
  
## <a name="troubleshooting-using-the-service-trace-viewer"></a>Hizmet izleme görüntüleyicisini kullanarak sorun giderme  
 Hizmet izleme Görüntüleyicisi aracı izleme dosyalarının yüklediğinizde, uygulamanızdaki bir sorunun nedenini aşağı izlemek için sol bölmenin üzerindeki tüm kırmızı veya sarı etkinlikleri seçebilirsiniz. 000 etkinlik genellikle en fazla kullanıcı Kabarcık özel durum işlenmemiş.  
  
  Aşağıdaki resimde, bir sorun kökünde bulunacak kırmızı veya sarı bir etkinliği seçip işlemi gösterilmektedir.   
 ![Bir sorunun kök bulmak için kırmızı veya sarı etkinliklerin ekran görüntüsü.](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/service-trace-viewer.gif)  

 Üst Sağdaki panelde, sol tarafta seçili etkinlik izlemelerini inceleyebilirsiniz. Panelin kırmızı veya sarı izlemelerinde inceleyin ve nasıl bağıntılı bakın. Yukarıdaki grafikte hem istemci hem de aynı işlemi eylem etkinliğindeki hizmet için uyarı izlemeleri görüyoruz.  
  
 Bu izlemeler, hatanın kök nedeni ile belirtmezseniz, seçili etkinlik (burada işlem eylem) Sol paneldeki çift tıklayarak grafiği kullanabilir. Grafik ile ilgili etkinlikler görüntülenir. Ardından, ("+" işareti tıklayarak) ilgili etkinlikleri genişletebilirsiniz ilk yayılan izleme kırmızı veya sarı ilgili bir aktivite içinde bulunamadı. Yalnızca kırmızı veya sarı izleme sorunun kök nedenini izlemek kadar aktarımları ilgili etkinlikler veya ileti akışları için uç noktalar genelinde aşağıdaki ilgi önce gerçekleşen etkinlikler genişletme tutun.  
  
 ![İzleme görüntüleyicisini kullanma](../../../../../docs/framework/wcf/diagnostics/tracing/media/wcfc-e2etrace9s.gif "wcfc_e2etrace9s")  
Sorunun kök nedenini izlemek için etkinlikleri genişletme  
  
 Varsa ServiceModel `ActivityTracing` kapalı ancak ServiceModel izleme açıktır, 0000 etkinliğinde yayılan ServiceModel izlemeleri görebilirsiniz. Ancak, bu izleme, bağıntı anlamak için daha fazla çaba gerektirir.  
  
 İleti günlüğe kaydetme etkinleştirilmişse, bu hatayı ileti etkilenir görmek için iletisi sekmesini kullanabilirsiniz. Kırmızı veya sarı bir ileti çift tıklayarak, ilgili etkinlikler graf görünümünü görebilirsiniz. Bu etkinlikler en yakın isteği ile ilgili bir hata gerçekleştiği olanlardır.  
  
 ![Ekran görüntüsü, izleme Görüntüleyici ile etkin ileti günlüğe kaydetme.](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/message-logging-enabled.gif)  

Sorun gidermeye başlamak için kırmızı veya sarı ileti izleme seçin ve çift kökenini izlemek için tıklatın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uçtan Uca İzleme Senaryoları](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)
- [Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
- [İzleme](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
