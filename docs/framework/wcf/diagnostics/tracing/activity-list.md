---
title: Etkinlik Listesi
ms.date: 03/30/2017
ms.assetid: 5540e185-ce8e-4db3-83b0-2b9f5bf71829
ms.openlocfilehash: f96aab037e86b05096df7ffc82a0be3f6cce1ad2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61998042"
---
# <a name="activity-list"></a>Etkinlik Listesi
Bu konuda, Windows Communication Foundation (WCF) tarafından tanımlanan tüm etkinlikleri listelenir.  
  
> [!NOTE]
>  Etkinlikler de program aracılığıyla ve grup kullanıcı izlemelere tanımlayabilirsiniz. Daha fazla bilgi için [kullanıcı kodu izlemeleri yayma](../../../../../docs/framework/wcf/diagnostics/tracing/emitting-user-code-traces.md).  
  
## <a name="servicemodel-activities"></a>ServiceModel etkinlikleri  
 Aşağıdaki tabloda ana kullanım senaryoları için tüm etkinlikleri listeler.  
  
|Etiketle|Etkinlik Adı|Etkinlik Türü|Açıklama|  
|-----------|-------------------|-------------------|-----------------|  
|M|Ortam etkinliği|(Bu ServiceModel tarafından denetlenen) yok|Etkinlik Kimliği (istemci tarafı veya sunucu tarafı) ServiceModel koddaki çağrıları önce TLS'ye ayarlanır.<br /><br /> Örnek: Açık WCF istemcisi veya serviceHost.open burada adlı bir etkinlik olarak adlandırılır.|  
|B|Oluştur<br /><br /> ChannelFactory. ContractType: '[Type]'.|Oluştur||  
|C|Open<br /><br /> [ClientBase&#124;ChannelFactory]. ContractType: '[Type]'.|Open||  
|I|Kapat [ClientBase&#124;ChannelFactory]. ContractType: '[Type]'.|Close||  
|M|ServiceHost oluşturun. ServiceType: '[Type]'.|Oluştur||  
|N|ServiceHost açın. ServiceType: '[Type]'.|Open||  
|Z|ServiceHost kapatma. ServiceType: '[Type]'.|Close||  
|O|'[Address]' dinleyin.|ListenAt|Bu ve sonraki etkinliğin aktarım özgüdür. ListenAt etkinlik, burada, kanal dinleyicisi dinler adresine eşleyen içeriğini temsil eder. Sıranın bir adrese eşlendiğinden MSMQ söz konusu olduğunda, kendisini kuyruğudur. Bu etkinlik, gelen bağlantıları taşımaları bağlantıya dayalı'MSMQ söz konusu olduğunda MSMQ iletileri için söz konusu olduğunda dinler. Bu etkinlik sırasında ServiceHost.Open() oluşturulur ve oluşturma ve disposing dinleyici, aynı zamanda tüm ReceiveBytes etkinlikler için dışarı aktarma ile ilgili izlemeleri içerir.|  
|P|Bayt [address] bağlantısı alırsınız. MSMQ iletisi alırsınız.|ReceiveBytes|Bu etkinlik, sonunda bir WCF ileti alacak veriler işlenir. Gelen bayt sayısı, aktarım bağlantı odaklı veya http söz konusu olduğunda beklendi. Bağlantı oluşturulduğunda oluşturulan TCP/adlandırılmış kanal için bu etkinlik ömrünü bağlantı ömrünü aynıdır. Http için bu ileti isteği ömrünü ve ileti gönderildiğinde oluşturulur. Bu etkinlik oluşturma ve uygunsa bağlantısı kesilirken ilgili izlemeleri içerir, aynı zamanda tüm ileti (nesne) işleme etkinlikler için dışarı aktarır.<br /><br /> MSMQ söz konusu olduğunda, MSMQ iletisinin nerede alınır etkinliğidir.|  
|Q|İşlem iletisi [sayı]. (Not [sayı], 1 ile başlayan bir düz olarak artan değerdir.)|ProcessMessage|Gelen ileti işler. Bu etkinlik bir WCF ileti nesnesi oluşturmak için alınan tüm veri (bayt, MSMQ iletisinin) başlar. Bu etkinlik içinde izlemeleri üst bilgisi işleme ile ilgilidir.<br /><br /> Tekrarlanarak gönderilen bir iletinin oluşturulduğunda ServiceHost ProcessAction etkinlik için karşılık gelen etkinlik kimliği bakan geçiş|  
|D, S|'[Action]' eylemini işleyin.|ProcessAction|Üzerinde kullanıcı kodu için ileti gönderme için Aktarım/güvenlik/RM yığını aracılığıyla iletisi, işlem ve ters sırada gönderme.<br /><br /> "Etkinlik yayma"; aracılığıyla ileti üstbilgisinde gönderirse sunucuda bu etkinlik yayılan etkinlik kimliği kullanır. Aksi takdirde, yeni bir GUID oluşturulur.<br /><br /> İstek/yanıt sözleşmeleri yanıt iletisi Ayrıca, etkinlik olarak işlenir.|  
|T|'[IContract.Operation]' yürütün.|ExecuteUserCode|Gönderme hizmeti tarafındaki sonra kullanıcı bir kod yürütün. Bu etkinlik, kullanıcı tarafından sağlanan kod ServiceHost koddan ayırmak için bir sınır sağlar.|  
  
## <a name="security-activities"></a>Güvenlik etkinlikleri  
 Aşağıdaki tabloda, güvenlikle ilgili tüm etkinlikleri listeler.  
  
|Etkinlik Adı|Etkinlik Türü|Açıklama|  
|-------------------|-------------------|-----------------|  
|Kurulum güvenli oturum|SetupSecurity|Yalnızca istemci tarafında var. İçeren tüm k * / kimlik doğrulama ve güvenlik bağlamını ayarlamak için SCT birbiriyle değiştirir. Varsa `propagateActivity` = `true`, bu etkinlik, hizmetin karşılık gelen işlem eylem lk ile birleştirilmiş\*/SCT etkinlikler.|  
|Güvenli Oturumu Kapat|SetupSecurity|İstemci tarafında var. Güvenli oturum kapatma iptal ileti alışverişi içerir. Varsa `propagateActivity` = `true`, bu etkinlik hizmetten işlem eylem "İptal" ile birleştirilir.|  
  
 Aşağıdaki tabloda, COM + ilgili tüm etkinlikleri listelenmektedir.  
  
|Etkinlik Adı|Etkinlik Türü|Açıklama|  
|-------------------|-------------------|-----------------|  
|COM + örneği oluşturma|TransferToCOMPlus|Her COM + 1 etkinlik örneği, WCF koddan çağırma|  
|COM + yürütme \<işlem >|TransferToCOMPlus|Her COM + 1 etkinlik örneği, WCF koddan çağırma|  
  
## <a name="wmi-activities"></a>WMI etkinlikleri  
 Aşağıdaki tabloda, WMI ile ilgili tüm etkinlikleri listeler.  
  
|Etkinlik Adı|Etkinlik Türü|Açıklama|  
|-------------------|-------------------|-----------------|  
|WMI Al|WMIGetObject|Kullanıcı, WMI'dan veri alıyor.|  
|WMI put|WmiPutInstance|Kullanıcı verileri ile WMI güncelleştiriyor.|
