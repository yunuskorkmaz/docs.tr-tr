---
title: 'İlişkilendirilmiş İzlemeleri Görüntülemek ve Sorun Gidermek için Hizmet İzleme Görüntüleyicisini Kullanma '
ms.date: 03/30/2017
ms.assetid: 05d2321c-8acb-49d7-a6cd-8ef2220c6775
ms.openlocfilehash: e1cd1443e96e7195127cb95e7ef1b2c4d6d9c176
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84587761"
---
# <a name="using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting"></a>İlişkilendirilmiş İzlemeleri Görüntülemek ve Sorun Gidermek için Hizmet İzleme Görüntüleyicisini Kullanma 

Bu konu başlığı altında, izleme verilerinin biçimi, nasıl görüntüleneceği ve uygulamanızın sorunlarını gidermek için hizmet Izleme görüntüleyicisini kullanan yaklaşımlar açıklanmaktadır.

## <a name="using-the-service-trace-viewer-tool"></a>Hizmet Izleme Görüntüleyicisi aracını kullanma

Windows Communication Foundation (WCF) hizmet Izleme Görüntüleyicisi Aracı, bir hatanın kök nedenini bulmak için WCF dinleyicileri tarafından üretilen tanılama izlemelerini ilişkilendirmenize yardımcı olur. Araç, WCF hizmetleriyle ilgili sorunları tanılamak, onarmak ve doğrulamak üzere izlemeleri kolayca görüntülemenizi, gruplandırmanızı ve filtrelemenizi sağlayan bir yol sunar. Bu aracı kullanma hakkında daha fazla bilgi için bkz. [hizmet Izleme Görüntüleyicisi Aracı (SvcTraceViewer. exe)](../../service-trace-viewer-tool-svctraceviewer-exe.md).

Bu konu, [hizmet Izleme Görüntüleyicisi Aracı (SvcTraceViewer. exe)](../../service-trace-viewer-tool-svctraceviewer-exe.md)kullanılarak görüntülenirken [Izleme ve mesaj günlüğü](../../samples/tracing-and-message-logging.md) örneği çalıştırılarak oluşturulan izlemelerin ekran görüntülerini içerir. Bu konu, izleme içeriğini, etkinlikleri ve bunların bağıntılarını ve sorun giderirken çok sayıda izlemenin nasıl çözümlendiğini gösterir.

## <a name="viewing-trace-content"></a>Izleme Içeriğini görüntüleme

İzleme olayı aşağıdaki en önemli bilgileri içerir:

- Ayarlandığında etkinlik adı.

- Emisin süresi.

- İzleme düzeyi.

- İzleme kaynağı adı.

- İşlem adı.

- İş parçacığı kimliği.

- Microsoft Docs içindeki bir hedefe işaret eden, izleme ile ilgili daha fazla bilgi alabileceğiniz bir URL olan benzersiz bir izleme tanımlayıcısı.

 Bunların tümü, hizmet Izleme görüntüleyicisinde sağ üst panelde veya bir izleme seçilirken sağ alt panelin biçimlendirilen görünümündeki **temel bilgiler** bölümünde görülebilir.

> [!NOTE]
> İstemci ve hizmet aynı makineli ise, her iki uygulamanın izlemeleri da mevcut olacaktır. Bunlar, **Işlem adı** sütunu kullanılarak filtrelenebilir.

Ayrıca, biçimlendirilen görünüm, izleme için bir açıklama ve kullanılabilir olduğunda ek ayrıntılı bilgiler de sağlar. İkincisi, özel durum türü ve ileti, çağrı yığınları, ileti eylemi, from/to alanları ve diğer özel durum bilgilerini içerebilir.

XML görünümünde, yararlı XML etiketleri şunları içerir:

- `<SubType>`(izleme düzeyi).

- `<TimeCreated>`.

- `<Source>`(izleme kaynağı adı).

- `<Correlation>`(izleme yayırken etkinlik kimliği kümesi).

- `<Execution>`(işlem ve iş parçacığı kimliği).

- `<Computer>`.

- `<ExtendedData>`, `<Action>` `<MessageID>` ve `<ActivityId>` bir ileti gönderilirken ileti üstbilgisinde ayarlanır.

"Bir kanaldan ileti gönderildi" izlemesini incelerseniz, aşağıdaki içeriği görebilirsiniz.

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

## <a name="servicemodel-e2e-tracing"></a>ServiceModel E2E Izleme

`System.ServiceModel`İzleme kaynağı off dışında bir ile ayarlandığında `switchValue` ve `ActivityTracing` WCF, WCF işleme için etkinlikler ve aktarımlar oluşturur.

Etkinlik, bu işleme birimiyle ilgili tüm izlemeleri gruplandıran mantıksal bir işleme birimidir. Örneğin, her istek için bir etkinlik tanımlayabilirsiniz. Aktarımlar, uç noktalar içindeki etkinlikler arasında bir causal ilişkisi oluşturur. Etkinlik KIMLIĞINI yayma, etkinlikleri uç noktalar arasında ilişkilendirmenizi sağlar. Bu, `propagateActivity` = `true` her uç noktada yapılandırma ayarı yaparak yapılabilir. Etkinlikler, aktarımlar ve yayma, hata bağıntısını gerçekleştirmenize olanak tanır. Bu şekilde, bir hatanın kök nedenini daha hızlı bulabilirsiniz.

İstemcide, her nesne modeli çağrısı için bir WCF etkinliği oluşturulur (örneğin, ChannelFactory, Ekle, Böl vb.) İşlem çağrılarının her biri bir "Işlem eylemi" etkinliğinde işlenir.

Aşağıdaki ekran görüntüsünde, [izleme ve Ileti günlüğe kaydetme](../../samples/tracing-and-message-logging.md) örneğinden ayıklanan sol panel, istemci işleminde oluşturulan etkinliklerin listesini, oluşturma zamanına göre sıralanmış olarak görüntüler. Aşağıda, etkinliklerin kronolojik bir listesi verilmiştir:

- Kanal fabrikası (ClientBase) oluşturulmuş.

- Kanal fabrikası açıldı.

- Ekleme eylemi işlendi.

- Güvenli oturumu ayarlayın (Bu ilk istekte meydana geldı) ve üç güvenlik altyapısı yanıt iletisini işledi: RST, RSTR, SCT (Işlem iletisi 1, 2, 3).

- Çıkarma, çarpma ve bölme istekleri işlendi.

- Kanal fabrikası kapatıldı ve bunu yapmak güvenli oturumu kapattı ve güvenlik iletisi yanıtı Iptali 'ni işledi.

 WsHttpBinding nedeniyle güvenlik altyapısı iletileri görüyoruz.

> [!NOTE]
> WCF 'de, bir aktarım aracılığıyla istek iletisini içeren ilgili Işlem eylemi etkinliğiyle ilişkilendirmeden önce, ilk olarak ayrı bir etkinlikte (Işlem iletisi) işlenen yanıt iletilerini gösteririz. Bu durum, altyapı iletileri ve zaman uyumsuz istekler için gerçekleşir ve iletiyi incelebilmemiz, ActivityId üst bilgisini okuduğumuz ve bu kimlik ile ilişkilendirmek üzere var olan Işlem eylemi etkinliğini tanımmız gerekir. Zaman uyumlu istekler için, yanıtı engelliyoruz ve bu nedenle yanıtın hangi Işlem eylemiyle ilişkili olduğunu biliyoruz.

Aşağıdaki görüntüde, oluşturma zamanı (sol panel) ve iç içe geçmiş etkinlikleri ve izlemeleri (sağ üst panel) tarafından listelenen WCF istemci etkinlikleri gösterilmektedir:

![Oluşturulma zamanına göre listelenen WCF istemci etkinliklerini gösteren ekran görüntüsü.](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/wcf-client-activities-creation-time.gif)

Sol panelde bir etkinlik seçtiğimiz zaman, sağ üst panelde iç içe geçmiş etkinlikleri ve izlemeleri görebiliriz. Bu nedenle, seçilen üst etkinliğe bağlı olarak, sol taraftaki etkinliklerin listesinin azaltılmış hiyerarşik görünümüdür. Seçilen Işlem eylemi ekleme ilk istek yaptığı için, bu etkinlik, Ekle eyleminin gerçek işleme için güvenli oturum ayarlama etkinliğini (aktarım, geri aktarma) ve izlemeleri içerir.

Sol panelde Işlem eylemi ekleme etkinliği ' ne çift tıkladığımızda, ekleme ile ilgili istemci WCF etkinliklerinin grafik bir gösterimini görebiliriz. Soldaki ilk etkinlik, varsayılan etkinlik olan kök etkinliğidir (0000). WCF, çevresel etkinlikten dışarı aktarır. Tanımlı değilse, WCF/0000 'yi aktarır. Burada, ikinci etkinlik, Işlem eylemi Ekle, 0 ' dan dışarı aktarır. Daha sonra güvenli oturum ayarla ' yı görüyoruz.

Aşağıdaki görüntüde, WCF istemci etkinliklerinin grafik görünümü, özellikle çevresel etkinlik (burada 0), Işlem eylemi ve güvenli oturum ayarlama gösterilmektedir:

![Izleme görüntüleyicisinde çevresel etkinlik ve Işlem eylemini gösteren grafik.](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/wcf-activities-graph-ambient-process.gif)

Sağ üst panelde, Işlem eylemi ekleme etkinliği ile ilgili tüm izlemeleri görebiliriz. Özellikle, istek iletisini ("bir kanal üzerinden bir ileti gönderdi") gönderdik ve aynı etkinlikte yanıtı ("bir kanal üzerinden bir ileti alındı") aldınız. Bu, aşağıdaki grafikte gösterilmiştir. Netlik açısından, güvenli oturum ayarla etkinliği grafikte daraltılır.

Aşağıdaki görüntüde Işlem eylemi etkinliğinin izlemelerinin bir listesi gösterilmektedir. İsteği gönderir ve aynı etkinlikte yanıtı alırsınız.

![Işlem eylemi etkinliğinin izlemelerinin listesini gösteren Izleme görüntüleyicisinin ekran görüntüsü](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/process-action-traces.gif)

Burada, istemci izlemelerini yalnızca açıklık için yükledik, ancak hizmet izlemeleri (gönderilen istek iletisi ve yanıt iletisi gönderildi) aynı etkinlikte araç içinde yükleniyorsa ve `propagateActivity` `true.` daha sonra bu şekilde ayarlandıysa, daha sonraki bir çizimde gösterilmiştir.

Hizmette, etkinlik modeli aşağıdaki şekilde WCF kavramlarıyla eşlenir:

1. Bir ServiceHost oluşturacağız ve Açarsınız (örneğin, güvenlik durumunda, ana bilgisayarla ilgili birkaç etkinlik oluşturabilir).

2. ServiceHost 'daki her dinleyici için bir dinleme etkinliği oluşturacağız (açık ServiceHost içindeki ve olmayan aktarımlarla).

3. Dinleyici, istemci tarafından başlatılan bir iletişim isteği algıladığında, istemciden gönderilen tüm baytların işlendiği bir "alma bayt" etkinliğine aktarır. Bu etkinlikte, istemci-hizmet etkileşimi sırasında gerçekleşen bağlantı hatalarını görebiliriz.

4. Bir iletiye karşılık gelen her bir bayt kümesi için, bu baytları WCF Ileti nesnesini oluşturduğumuz "Işlem Iletisi" etkinliğinde işletik. Bu etkinlikte, hatalı bir zarfa veya hatalı biçimlendirilmiş iletiyle ilgili hatalar görüyoruz.

5. İleti oluşturulduktan sonra bir Işlem eylemi etkinliğine aktarıyoruz. `propagateActivity` `true` Hem istemci hem de hizmette olarak ayarlandıysa, bu etkinlik istemcide tanımlananla aynı kimliğe sahiptir ve daha önce açıklanmıştır. Bu aşamada, istekle ilişkili tüm izlemeler, yanıt iletisi işleme dahil olmak üzere aynı etkinlik içinde olduğundan, uç noktalar genelinde doğrudan bağıntı üzerinden faydalanabilir.

6. İşlem dışı eylem için, WCF 'de yayıldıklarından Kullanıcı kodunda oluşturulan izlemeleri yalıtmak üzere bir "Kullanıcı kodu Yürüt" etkinliği oluşturacağız. Yukarıdaki örnekte, "hizmet yanıtı gönderme" izlemesi, varsa istemci tarafından yayılan etkinlikte "Kullanıcı kodunu Yürüt" etkinliği içinde dağıtılır.

Aşağıdaki çizimde, soldaki ilk etkinlik, varsayılan etkinlik olan kök etkinliğidir (0000). Sonraki üç etkinlik ServiceHost 'u açmak için kullanılır. 5. sütundaki etkinlik, dinleyiciye ve kalan etkinliklerin (6-8), bayt işlemeden Kullanıcı kodu etkinleştirmesine kadar bir iletinin WCF işlemesini tanımlıyor.

Aşağıdaki görüntüde, WCF hizmeti etkinliklerinin grafik görünümü gösterilmektedir:

![WCF hizmeti etkinliklerinin listesini gösteren Izleme görüntüleyicisinin ekran görüntüsü](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/wcf-service-activities.gif)

Aşağıdaki ekran görüntüsünde hem istemci hem de hizmetin etkinlikleri gösterilmektedir ve işlemler arasında etkinlik Ekle (turuncu) Işlem eylemi vurgulanmıştır. Oklar, istemci ve hizmet tarafından gönderilen ve alınan istek ve yanıt iletilerini birbirleriyle ilişkilidir. Işlem izlemeleri eylemi, grafikteki işlemler arasında ayrılır, ancak sağ üst panelde aynı etkinliğin bir parçası olarak gösterilir. Bu panelde, gönderilen iletiler için istemci izlemelerini ve alınan ve işlenen iletiler için hizmet izlemelerini görebiliriz.

Aşağıdaki resimlerde hem WCF istemcisinin hem de hizmet etkinliklerinin grafik görünümü gösterilmektedir

![Hem WCF istemcisi hem de hizmet etkinliklerini gösteren Izleme görüntüleyicisinden grafik.](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/wcf-client-service-activities.gif)

Aşağıdaki hata senaryosunda, hizmette ve istemcide hata ve uyarı izlemeleri ilgili. İlk olarak, hizmette Kullanıcı kodunda bir özel durum oluşturulur (özel durum için bir uyarı izlemesi içeren en yüksek yeşil etkinlik "hizmetin Kullanıcı kodunda bu isteği işleyemez."). Yanıt istemciye gönderildiğinde, hata iletisini göstermek için bir uyarı izlemesi yeniden oluşturulur (sol pembe etkinlik). İstemci daha sonra, hizmet bağlantısını iptal eden WCF istemcisini (sol tarafta sarı etkinlik) kapatır. Hizmet bir hata (sağ tarafta en uzun pembe etkinlik) oluşturur.

![Izleme görüntüleyicisini kullanma](media/wcfc-e2etrace9s.gif "wcfc_e2etrace9s")

Hizmet ve istemci genelinde hata bağıntısı

Bu izlemeleri oluşturmak için kullanılan örnek, wsHttpBinding kullanan bir dizi zaman uyumlu istekdir. Bu grafikten güvenlik içermeyen senaryolar veya zaman uyumsuz isteklerle ilgili sapmalar vardır; burada Işlem eylemi etkinliği, zaman uyumsuz çağrıyı oluşturan başlangıç ve bitiş işlemlerini kapsar ve bir geri çağırma etkinliğine yapılan aktarımları gösterir. Ek senaryolar hakkında daha fazla bilgi için bkz. [uçtan uca Izleme senaryoları](end-to-end-tracing-scenarios.md).

## <a name="troubleshooting-using-the-service-trace-viewer"></a>Hizmet Izleme görüntüleyicisini kullanarak sorun giderme

İzleme dosyalarını hizmet Izleme Görüntüleyicisi aracında yüklediğinizde, uygulamanızdaki bir sorunun nedenini izlemek için sol panelde herhangi bir kırmızı veya sarı etkinlik seçebilirsiniz. 000 etkinlik genellikle kullanıcıya kabarcıklu işlenmemiş özel durumlara sahiptir.

Aşağıdaki görüntüde, bir sorunun kökünü bulmak için kırmızı veya sarı bir etkinliğin nasıl görüntüleneceği gösterilmektedir.
![Bir sorunun kökünü bulmak için kırmızı veya sarı etkinliklerin ekran görüntüsü.](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/service-trace-viewer.gif)

Sağ üst bölmede, sol tarafta seçtiğiniz etkinliğin izlemelerini inceleyebilirsiniz. Daha sonra bu panelde kırmızı veya sarı izlemeleri inceleyebilir ve bunların nasıl bağıntılı olduğunu görebilirsiniz. Yukarıdaki grafikte, aynı Işlem eylemi etkinliğinde istemci ve hizmet için uyarı izlemelerinin her ikisini de görüyoruz.

Bu izlemeler, hatanın temel nedenini sağlamıyorsa, sol panelde seçili etkinliğe çift tıklayarak grafiği kullanabilirsiniz (burada Işlem eylemi). İlgili etkinlikleri içeren grafik daha sonra görüntülenir. Ardından ilgili etkinlikleri genişleterek ilgili etkinlikleri genişletebilirsiniz ("+" işaretlerine tıklayarak) ve ilgili etkinlikteki ilk yayınlanan izlemeyi kırmızı veya sarı olarak bulabilirsiniz. Sorunun kök nedenini izlemediğiniz sürece, yalnızca kırmızı veya sarı bir şekilde ilgilenmeden önce gerçekleşen etkinlikleri genişlettikten sonra, uç noktalar arasında ilgili etkinliklere veya ileti akışlarına yönelik aktarımları takip edin.

![Izleme görüntüleyicisini kullanma](media/wcfc-e2etrace9s.gif "wcfc_e2etrace9s")

Sorunun kök nedenini izlemek için etkinlikleri genişletme

ServiceModel `ActivityTracing` kapalıysa ancak ServiceModel izleme açık ise, 0000 etkinliğinde bulunan ServiceModel izlemelerini görebilirsiniz. Ancak, bu izlemelerin bağıntısını anlamak için daha fazla çaba gerektirir.

Ileti günlüğe kaydetme etkinse, hatadan etkilenen iletiyi görmek için Ileti sekmesini kullanabilirsiniz. Kırmızı veya sarı renkte bir iletiye çift tıklayarak ilgili etkinliklerin grafik görünümünü görebilirsiniz. Bu etkinlikler, bir hatanın gerçekleştiği istekle en yakından ilgili olan etkinliklerdir.

![İleti günlüğü etkin olan Izleme görüntüleyicisinin ekran görüntüsü.](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/message-logging-enabled.gif)

Sorun gidermeye başlamak için Ayrıca kırmızı veya sarı bir ileti izlemesi seçebilir ve temel nedeni izlemek için çift tıklayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Uçtan Uca İzleme Senaryoları](end-to-end-tracing-scenarios.md)
- [Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)](../../service-trace-viewer-tool-svctraceviewer-exe.md)
- [İzleme](index.md)
