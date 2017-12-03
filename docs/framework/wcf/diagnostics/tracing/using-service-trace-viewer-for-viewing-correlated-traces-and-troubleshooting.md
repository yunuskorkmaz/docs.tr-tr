---
title: "İlişkilendirilmiş İzlemeleri Görüntülemek ve Sorun Gidermek için Hizmet İzleme Görüntüleyicisini Kullanma "
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 05d2321c-8acb-49d7-a6cd-8ef2220c6775
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 048ef839db0656340827a5928056a3c063f5aa3c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting"></a>İlişkilendirilmiş İzlemeleri Görüntülemek ve Sorun Gidermek için Hizmet İzleme Görüntüleyicisini Kullanma 
Bu konu, izleme verilerinin biçimi açıklar ve uygulamanızda sorun giderme için hizmet izleme görüntüleyicisini kullanma yaklaşımlar görüntüleme.  
  
## <a name="using-the-service-trace-viewer-tool"></a>Hizmet izleme Görüntüleyicisi Aracı'nı kullanma  
 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Hizmet izleme Görüntüleyicisi aracı tarafından üretilen tanılama izlemeleri ilişkilendirmenize yardımcı olan [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] kök bulmak için dinleyicileri neden bir hata oluştu. Aracı kolayca görüntülemek, grup için bir yöntem sunar ve filtre izlemeleri tanılamak böylece onarın ve sorunları doğrulayın [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Hizmetleri. Bu aracı kullanmayla ilgili daha fazla bilgi için bkz: [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).  
  
 Bu konuda çalıştırarak oluşturulan izlemeleri ekran görüntüleri içeren [izleme ve ileti günlüğe kaydetme](../../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) kullanarak görüntülendiğinde örnek [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Bu konuda izleme içerik, etkinlikler ve bunların bağıntı anlama ve sorunlarını giderirken izlemeleri çok sayıda analiz etme gösterilir.  
  
## <a name="viewing-trace-content"></a>Görüntüleme izleme içeriği  
 İzleme olayı aşağıdaki en önemli bilgileri içerir:  
  
-   Etkinlik adı olarak ayarlandığında.  
  
-   Çıkması süre.  
  
-   İzleme düzeyi.  
  
-   İzleme kaynağı adı.  
  
-   İşlem adı.  
  
-   İş parçacığı kimliği.  
  
-   Microsoft Docs izleme ile ilgili daha fazla bilgi edinmek, bir hedefe işaret eden bir URL bir benzersiz izleme tanımlayıcısı.  
  
 Bunların tümü üst sağ bölmede hizmet izleme Görüntüleyicisi'nde veya içinde görülebilir **temel bilgileri** izleme seçerken sağ alt paneli biçimlendirilmiş görünümünü bölümünde.  
  
> [!NOTE]
>  İstemci ve hizmet aynı makinede varsa, her iki uygulama izlemelerini mevcut olacaktır. Bunlar kullanarak filtrelenebilir **işlem adı** sütun.  
  
 Ayrıca, biçimlendirilmiş görünümü de ek ayrıntılı bilgi kullanılabilir olduğunda ve izleme için bir açıklama sağlar. İkinci özel durum türünü ve ileti, çağrı yığınları ileti eylemi başlangıç/bitiş alanları ve diğer özel durum bilgileri içerebilir.  
  
 XML Görünümü'nde yararlı xml etiketleri şunları içerir:  
  
-   \<Alt > (izleme düzeyi).  
  
-   \<TimeCreated >.  
  
-   \<Kaynak > (izleme kaynak adı).  
  
-   \<Bağıntı > (Etkinlik Kimliği yayma izleme ayarlanır).  
  
-   \<Yürütme > (işlem ve iş parçacığı kimliği).  
  
-   \<Bilgisayar >.  
  
-   \<ExtendedData > gibi \<eylem >, \<MessageID > ve \<ActivityID > ileti üstbilgisinde bir ileti gönderirken ayarlayın.  
  
 "Gönderilen bir ileti bir kanal üzerinden" izleme incelerseniz, aşağıdaki içeriği görebilirsiniz.  
  
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
 Zaman `System.ServiceModel` izleme kaynağı olarak ayarlanmış olan bir `switchValue` dışında kapalı ve `ActivityTracing`, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] etkinlikleri oluşturur ve için aktarımı [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] işleme.  
  
 Bir etkinlik bir mantıksal gruplar bu işleme birimine tüm izlemeleri ilgili işleme birimidir. Örneğin, her istek için bir etkinlik tanımlayabilirsiniz. Aktarımları uç noktaları'nda etkinlikler arasında nedensel bir ilişki oluşturun. Etkinlik Kimliği yayma uç noktalar arasında etkinliklerini ilişkilendirmek etkinleştirir. Bu ayar yapılabilir `propagateActivity` = `true` her uç noktada yapılandırma. Etkinlikler, aktarımları ve yayma hata bağıntı işlemleri yapmanıza olanak verir. Bu şekilde, bir hata kök nedenini daha hızlı bir şekilde bulabilirsiniz.  
  
 İstemci üzerindeki bir [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] etkinlik (örneğin, açık ChannelFactory, Ekle, bölme ve benzeri) her nesne modeli çağrısı için oluşturuldu Her işlem çağrıları "İşlem eylem" etkinliğinde işlenir.  
  
 Aşağıdaki ekran görüntüsünde ayıklanan [izleme ve ileti günlüğe kaydetme](../../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) örnek sol panelde oluşturulma tarihine göre sıralanmış istemci işleminde, oluşturulan etkinliklerin listesini görüntüler. Etkinliklerin kronolojik listesi aşağıdadır:  
  
-   Kanal fabrikası (ClientBase) oluşturulur.  
  
-   Kanal fabrikası açıldı.  
  
-   Ekleme eylemi işlendi.  
  
-   Güvenli oturum (ilk istek üzerine bu OLUŞTU) ayarlayabilir ve üç güvenlik altyapı yanıt iletilerini işlenen: RST, RSTR, SCT (işlem iletisi 1, 2, 3).  
  
-   Çıkarma Çarp işlenir ve bölme ister.  
  
-   Kanal fabrikası kapatılır ve bunun yapılması ve güvenli oturum kapatıldığında güvenlik ileti yanıtı iptal işlenebilir.  
  
 Biz, wsHttpBinding nedeniyle güvenlik altyapı iletilere bakın.  
  
> [!NOTE]
>  İçinde [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)], başlangıçta ayrı bir etkinlik (işlem iletisi) işlenmekte olan yanıt iletilerini gösteriyoruz istek iletisi, bir aktarımı içerir karşılık gelen işlemi eylem etkinliğine biz bunları ilişkilendirmek önce. Bu altyapı iletileri ve zaman uyumsuz istekler için olur ve biz gerekir ileti inceleyin, ActivityID üstbilgi okuyun ve kendisine ilişkilendirmek için bu kimliğe sahip mevcut işlem eylem etkinliğin tanımlamak due için olabilir. Zaman uyumlu istekleri için yanıt için engelleme ve bu nedenle yanıt ilişkili işlem eylemi biliyor.  
  
 ![İzleme Görüntüleyicisi'ni kullanarak](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace4.gif "e2eTrace4")  
WCF istemcisi etkinliklerini oluşturma zamanı (sol paneli) ve iç içe etkinlik ve izlemeleri (üst sağ panelde) tarafından listelenen  
  
 Bir etkinlik sol panelde seçtiğinizde iç içe etkinlik ve izlemelere üst Sağdaki panelde görebiliriz. Bu nedenle, bu bir sınırlı olduğu etkinliklerin listesini hiyerarşik görünümünü solda, seçilen üst aktivitesini temel alarak. Seçili işlem Eylem Ekle yapılan ilk istek olduğu için bu etkinliği güvenli oturum yukarı ayarlamak etkinlik (aktarımı için Aktarım geri) içerir ve işlenmesini ekleme eylemi için izler.  
  
 Biz çift işlem eylemi sol panelinde Ekle etkinliği tıklatın, istemci grafik gösterimi görebiliriz [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] ilgili etkinlikleri Ekle. Sol taraftaki ilk etkinlik kök (0000), varsayılan etkinlik olduğu etkinliktir. [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]ortam etkinlik dışı aktarımları. Bu tanımlanmazsa [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] aktarımları 0000 dışında. Burada, ikinci etkinlik işlem eylem eklemek, 0 dışında aktarır. Daha sonra Kurulum güvenli oturum bakın.  
  
 ![İzleme Görüntüleyicisi'ni kullanarak](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace5.gif "e2eTrace5")  
Grafik görünümü WCF istemci etkinliklerin: ortam etkinlik (burada 0), işlem eylem ve güvenli oturum yukarı ayarlayın  
  
 Üst sağ paneldeki işlem Eylem Ekle etkinliği ile ilgili tüm izlemeleri görebiliriz. Özellikle, biz istek iletisi ("gönderilen bir ileti bir kanal üzerinden") gönderdiğiniz ve aynı etkinlik içindeki ("alınan bir kanal üzerinden ileti") yanıt aldı. Bu aşağıdaki grafikte gösterilir. Daha anlaşılır olması için güvenli oturum etkinlik ayarlama grafikte daraltılmıştır.  
  
 ![İzleme Görüntüleyicisi'ni kullanarak](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace6.gif "e2eTrace6")  
İşlem eylem etkinlik izlemelerini listesi: isteği göndermek ve aynı etkinlik içindeki yanıtı alırsınız.  
  
 Burada, biz yalnızca daha anlaşılır olması için istemci izlemelerini yük, ancak hizmet izlemeleri (istek iletisi aldı ve yanıt iletisi gönderilen) görünür aynı etkinlik içindeki Ayrıca aracı yüklü olup olmadığını ve `propagateActivity` ayarlandı `true.` bu bir sonraki örnekte gösterilir.  
  
 Etkinlik modeli eşlendiği service üzerinde [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] şekilde Kavramları:  
  
1.  Biz oluşturmak ve bir ServiceHost (Bu ana bilgisayar ile ilgili çeşitli etkinlikler örneği için söz konusu olduğunda güvenlik oluşturabilir) açın.  
  
2.  Dinleme adresindeki etkinlik her dinleyicisinde ServiceHost için (ile aktarımları ve açık ServiceHost dışındaki) oluşturuyoruz.  
  
3.  Dinleyici istemci tarafından başlatılan bir iletişim isteği algıladığında istemci tarafından gönderilen tüm bayt işlenme bir "Bayt alma" etkinliğe aktarır. Bu etkinlikte istemci-hizmet etkileşim sırasında oluşmuş bağlantı hatalarını görebiliriz.  
  
4.  Bir iletisine karşılık gelen her kümesi alınan bayt için Biz bu bayt "İşlemi iletisi" etkinliğinde burada oluşturuyoruz işlem [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] ileti nesnesi. Bu etkinlikte hatalı zarf veya hatalı bir ileti ile ilgili hatalar bakın.  
  
5.  İleti biçimlendirilmiş sonra size bir işlem eylem etkinliğe aktarın. Varsa `propagateActivity` ayarlanır `true` hem istemci hem de hizmet üzerinde bu etkinlik istemcisinde tanımlı ve daha önce açıklanan aynı kimliğe sahip. İçindeki tüm izlemeleri yayılan çünkü bu aşamadan şu uç noktalar arasında doğrudan bağıntı yararlanmak Başlat [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] isteği ile ilgili yanıt ileti işleme dahil olmak üzere bu aynı etkinlik içindeki şunlardır.  
  
6.  İşlem dışı eylem için kullanıcı kodu içinde gösterilen olanları ile yayılan izlemeleri ayırmak için bir "kullanıcı kodu yürütme" etkinliği oluşturuyoruz [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]. Önceki örnekte, "Hizmet Ekle yanıt gönderir" izleme "Yürütme kullanıcı kodu" etkinliğinde değil istemci tarafından yayıldığı etkinliğinde varsa yayınlanır.  
  
 Aşağıdaki çizimde, soldaki ilk etkinlik kök (0000), varsayılan etkinlik olduğu etkinliktir. Sonraki üç ServiceHost açmak için etkinliklerdir. Dinleyici etkinliktir sütununda 5 ve bir iletiden kullanıcı kodu etkinleştirme işleme bayt WCF işlenmesini kalan etkinlikleri (6-8) tanımlayın.  
  
 ![İzleme Görüntüleyicisi'ni kullanarak](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace7.gif "e2eTrace7")  
WCF hizmet etkinlikler listesi  
  
 Aşağıdaki ekran görüntüsünde hem istemci hem de hizmet etkinliklerini gösterir ve etkinlik işlem Eylem Ekle (turuncu) işlemleri arasında vurgular. Oklar, istemci ve hizmet tarafından gönderilen ve alınan istek ve yanıt iletileri ilgilidir. İşlem eylem izlerini grafikte işlemler arasında ayrılmış, ancak aynı etkinlik sağ üst köşede panelinde bir parçası olarak gösterilen. Bu panelinde alınan ve işlenen iletiler için hizmet izlemeleri ve ardından gönderilen iletiler için istemci izlemelerini görebiliriz.  
  
 ![İzleme Görüntüleyicisi'ni kullanarak](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace8.gif "e2eTrace8")  
Her iki WCF hizmet ve istemci etkinlik grafik görünümü  
  
 Aşağıdaki hata senaryoda hata ve uyarı izlemeleri hizmet ve istemci ilişkilendirilir. Bir özel durum, büyük bir ilk (bir uyarı içeren en sağdaki yeşil Etkinlik izleme için özel durum "hizmeti kullanıcı kodu bu isteği işleyemiyor.") hizmeti kullanıcı kodu durum oluşturulur. Yanıt istemciye gönderildiğinde, bir uyarı izleme hata iletisi (sol pembe etkinliği) belirtmek için yeniden yayınlanır. İstemci hizmetine bağlantıyı durdurur, WCF istemcisi (sol alt tarafında sarı etkinliği), ardından kapatır. Hizmet bir hata (sağdaki uzun pembe etkinliği) oluşturur.  
  
 ![İzleme Görüntüleyicisi'ni kullanarak](../../../../../docs/framework/wcf/diagnostics/tracing/media/wcfc-e2etrace9s.gif "wcfc_e2etrace9s")  
Hizmet ve istemci arasında hata bağıntı  
  
 Bu izlemeler oluşturmak için kullanılan örnek wsHttpBinding kullanarak eş zamanlı istekleri dizisidir. Bu grafik senaryoları güvenlik olmadan veya burada işlem eylem etkinlik zaman uyumsuz çağrı oluşturan başlangıç ve bitiş işlemleri kapsar ve aktarımları için bir geri çağırma etkinliği gösterir zaman uyumsuz istekler için sapmaları vardır. İlave Senaryolar hakkında daha fazla bilgi için bkz: [uçtan uca izleme senaryoları](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).  
  
## <a name="troubleshooting-using-the-service-trace-viewer"></a>Hizmet izleme Görüntüleyicisi'ni kullanarak sorun giderme  
 Hizmet izleme Görüntüleyicisi aracı izleme dosyalarının yüklediğinizde, herhangi bir kırmızı veya sarı etkinliği, uygulamanızdaki bir sorunun nedenini aşağı izlemek için Sol paneldeki seçebilirsiniz. 000 etkinlik genellikle kadar kullanıcı Kabarcık özel durum işlenmemiş.  
  
 ![İzleme Görüntüleyicisi'ni kullanarak](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace10.gif "e2eTrace10")  
Bir sorun kökünü kırmızı veya sarı etkinlik seçme  
  
 Üst Sağdaki panelde, soldaki bölmede seçili etkinlik izlemelerini inceleyebilirsiniz. Ardından, o panelinde kırmızı veya sarı izlemeleri inceleyin ve nasıl bağıntılı bakın. Yukarıdaki grafikte hem istemci hem de aynı işlemi eylem etkinliğinde hizmet için uyarı izlemeleri bakın.  
  
 Bu izlemeler hatanın temel nedenlerinden biri ile belirtmezseniz, (burada işlem eylem) Sol paneldeki seçili etkinliği çift tıklatarak grafiği kullanabilir. Grafik ilgili etkinlikler ile sonra görüntülenir. ("+" İşareti tıklatarak) sonra ilgili etkinlikler genişletebilirsiniz kırmızı veya sarı ilgili bir aktivite olarak ilk verilmiş izleme bulunamadı. Yalnızca kırmızı veya sarı izleme sorunun kök nedeni izlemek kadar aktarımları ilgili etkinlikler veya ileti akışları için uç noktalar arasında aşağıdaki ilgi önce oldu etkinlikleri genişletme tutun.  
  
 ![İzleme Görüntüleyicisi'ni kullanarak](../../../../../docs/framework/wcf/diagnostics/tracing/media/wcfc-e2etrace9s.gif "wcfc_e2etrace9s")  
Bir sorunun kök nedenini izlemek için etkinlikler genişletme  
  
 Varsa ServiceModel `ActivityTracing` kapalı ancak ServiceModel izleme açıktır, 0000 etkinliğinde yayılan ServiceModel izlemeleri görebilirsiniz. Ancak, bu izlemeleri bağıntı anlamak için daha fazla çaba gerektirir.  
  
 İleti günlüğe kaydetme etkinleştirildiğinde ileti hata tarafından etkilenen görmek için ileti sekmesini kullanabilirsiniz. Kırmızı veya sarı bir ileti çift tıklatarak, ilgili etkinlikler grafik görünümünü görebilirsiniz. Bu etkinlikler en yakından isteği ile ilgili bir hata yapıldığı olanlardır.  
  
 ![İzleme Görüntüleyicisi'ni kullanarak](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace11.gif "e2eTrace11")  
Sorun giderme başlatmak için ayrıca bir kırmızı veya sarı ileti izleme seçin ve çift kök nedeni izlemek için tıklatın  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uçtan uca izleme senaryoları](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 [Hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)  
 [İzleme](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
