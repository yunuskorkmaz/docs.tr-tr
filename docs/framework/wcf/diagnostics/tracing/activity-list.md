---
title: Etkinlik Listesi
ms.date: 03/30/2017
ms.assetid: 5540e185-ce8e-4db3-83b0-2b9f5bf71829
ms.openlocfilehash: 8d43cc878d54efbd4908f92c3405bef2c7956f94
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602173"
---
# <a name="activity-list"></a>Etkinlik Listesi
Bu konu, Windows Communication Foundation (WCF) tarafından tanımlanan tüm etkinlikleri listeler.  
  
> [!NOTE]
> Ayrıca, Kullanıcı izlemelerini gruplamak için etkinlik programlama yoluyla da tanımlayabilirsiniz. Daha fazla bilgi için bkz. [Kullanıcı kodu Izlemelerini yayma](emitting-user-code-traces.md).  
  
## <a name="servicemodel-activities"></a>ServiceModel etkinlikleri  
 Aşağıdaki tabloda, önemli kullanım senaryoları için tüm etkinlikler listelenmektedir.  
  
|Etiket|Etkinlik Adı|Etkinlik Türü|Açıklama|  
|-----------|-------------------|-------------------|-----------------|  
|A, D|Çevresel etkinlik|Yok (ServiceModel tarafından denetlenmiyor)|KIMLIĞI, ServiceModel koduna (istemci tarafı veya sunucu tarafı) yapılan herhangi bir çağrının önüne TLS olarak ayarlanmış olan etkinlik.<br /><br /> Örnek: WCF istemcisi veya serviceHost üzerinde Open çağrısı yapılacak bir etkinlik. Open çağırılır.|  
|B|Oluştur<br /><br /> Endpoint. ContractType: ' [Type] '.|Oluştur||  
|C|Open<br /><br /> [ClientBase&#124;ChannelFactory]. ContractType: ' [Type] '.|Open||  
|I|[ClientBase&#124;ChannelFactory] öğesini kapatın. ContractType: ' [Type] '.|Kapat||  
|M|ServiceHost oluşturun. ServiceType: ' [Type] '.|Oluştur||  
|N|ServiceHost öğesini açın. ServiceType: ' [Type] '.|Open||  
|Z|ServiceHost 'u kapatın. ServiceType: ' [Type] '.|Kapat||  
|O|' [Address] ' konumunda dinleyin.|ListenAt|Bu ve sonraki etkinlik, aktarıma özeldir. ListenAt etkinliği, kanal dinleyicisinin dinlediği adresle eşleşen içeriği temsil eder. MSMQ söz konusu olduğunda, kuyruk tek bir adresle eşlendiğinden sıranın kendisi bu değildir. Bu etkinlik, MSMQ durumunda MSMQ iletileri için bağlantı yönelimli aktarımlara karşı gelen bağlantıları dinler. Bu etkinlik ServiceHost. Open () sırasında oluşturulur ve dinleyiciyi oluşturma ve atma ile ilgili izlemeleri ve tüm ReceiveBytes etkinliklerine aktarmayı içerir.|  
|P|' [Address] ' bağlantısında bayt alın. MSMQ iletisi alın.|ReceiveBytes|Bu etkinlikte, sonunda bir WCF iletisi alacak veriler işlenir. Gelen baytlar, bağlantıya dayalı taşıma veya http olması durumunda bekletilir. TCP/adlandırılmış kanal için, bu etkinliğin ömrü bağlantı oluşturulduğu sırada oluşturulduğu gibi bağlantının kullanım süresidir. Http için bir ileti isteğinin kullanım ömrü ve ileti gönderildiğinde oluşturulur. Bu etkinlik, varsa bağlantıyı oluşturma ve atma ile ilgili izlemeleri içerir ve tüm ileti (nesne) işleme etkinliklerine aktarır.<br /><br /> MSMQ söz konusu olduğunda, MSMQ iletisinin alındığı etkinliktir.|  
|Q|İşlem iletisi [sayı]. (Yani, [Number], 1 ile başlayan tek bir artış değeridir.)|ProcessMessage|Gelen bir iletiyi işleyin. Bu etkinlik, bir WCF ileti nesnesi oluşturmak için tüm veriler (bayt, MSMQ iletisi) alındığında başlar. Bu etkinliğin içindeki izlemeler üst bilgi işlemeyle ilgilenir.<br /><br /> Dağıtılabilir bir ileti biçimlendirilmişse, ServiceHost ProcessAction etkinliği ilgili etkinlik KIMLIĞI arandıktan sonra öğesine geçiş yapar.|  
|D, S|' [Action] ' eylemini işleyin.|ProcessAction|İletiyi alma sırasında kullanıcı koduna ve gönderme sırasında ters sırada göndermek için taşıma/güvenlik/RM yığını aracılığıyla iletiyi işleyin.<br /><br /> Sunucuda, bu etkinlik "etkinlik yayma" yoluyla ileti üstbilgisinde gönderildiyse yayılan etkinlik KIMLIĞINI kullanır; Aksi takdirde, yeni bir GUID oluşturulur.<br /><br /> İstek/yanıt sözleşmeleri için yanıt iletisi de bu etkinlikte işlenir.|  
|T|' [Icondikkatini. Operation] ' yürütün.|ExecuteUserCode|Hizmet tarafında gönderdikten sonra Kullanıcı kodunu yürütün. Bu etkinlik, Kullanıcı tarafından sağlanan koddan ServiceHost kodunu belirtmek için bir sınır sağlar.|  
  
## <a name="security-activities"></a>Güvenlik etkinlikleri  
 Aşağıdaki tabloda güvenlik ile ilgili tüm etkinlikler listelenmektedir.  
  
|Etkinlik Adı|Etkinlik Türü|Açıklama|  
|-------------------|-------------------|-----------------|  
|Güvenli oturum ayarla|SetupSecurity|Yalnızca istemci tarafında bulunur. Kimlik doğrulaması için tüm RST */SCT değişimlerinin yanı sıra güvenlik bağlamını ayarlamaya da sahiptir. `propagateActivity` = `true` Bu etkinlik, hizmetin karşılık gelen işlem eylemi RST \* /SCT etkinlikleriyle birleştirilir.|  
|Güvenli oturumu Kapat|SetupSecurity|İstemci tarafında bulunur. Güvenli oturumu kapatmak için Iptal iletisi değişimini içerir. `propagateActivity` = `true` Bu etkinlik, hizmetten "iptal" işlem eylemiyle birleştirilir.|  
  
 Aşağıdaki tabloda, COM+ ile ilgili tüm etkinlikler listelenmektedir.  
  
|Etkinlik Adı|Etkinlik Türü|Açıklama|  
|-------------------|-------------------|-----------------|  
|COM+ örneği oluştur|TransferToCOMPlus|WCF kodundan gelen her COM+ çağrısı için 1 etkinlik örneği|  
|COM+ yürütme\<operation>|TransferToCOMPlus|WCF kodundan gelen her COM+ çağrısı için 1 etkinlik örneği|  
  
## <a name="wmi-activities"></a>WMI etkinlikleri  
 Aşağıdaki tabloda WMI ile ilgili tüm etkinlikler listelenmektedir.  
  
|Etkinlik Adı|Etkinlik Türü|Açıklama|  
|-------------------|-------------------|-----------------|  
|WMI Get|Wgetobject|Kullanıcı WMI 'dan veri alıyor.|  
|WMI put|Wmiputınstance|Kullanıcı WMI ile verileri güncelleştiriyor.|
