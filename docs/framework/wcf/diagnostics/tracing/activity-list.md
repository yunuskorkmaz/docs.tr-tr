---
title: Etkinlik Listesi
ms.date: 03/30/2017
ms.assetid: 5540e185-ce8e-4db3-83b0-2b9f5bf71829
ms.openlocfilehash: f96aab037e86b05096df7ffc82a0be3f6cce1ad2
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809764"
---
# <a name="activity-list"></a>Etkinlik Listesi
Bu konu, Windows Communication Foundation (WCF) tarafından tanımlanan tüm etkinlikleri listeler.  
  
> [!NOTE]
>  Etkinlikler de program aracılığıyla ve grup kullanıcı izlemeleri tanımlayabilirsiniz. Daha fazla bilgi için bkz: [kullanıcı kodu izleri yayma](../../../../../docs/framework/wcf/diagnostics/tracing/emitting-user-code-traces.md).  
  
## <a name="servicemodel-activities"></a>ServiceModel etkinlikleri  
 Aşağıdaki tabloda önemli kullanım senaryoları için tüm etkinlikleri listeler.  
  
|Etiketle|Etkinlik Adı|Etkinlik Türü|Açıklama|  
|-----------|-------------------|-------------------|-----------------|  
|BİR, M|Ortam etkinliği|(Bu ServiceModel tarafından denetlenmeyen) yok|Etkinlik Kimliğine ServiceModel kodu (istemci tarafı veya sunucu tarafı) yapılan her çağrı önce TLS ayarlanır.<br /><br /> Örnek: açık WCF istemcisi veya serviceHost.open burada adlı bir etkinlik olarak adlandırılır.|  
|B|Oluştur<br /><br /> ChannelFactory. ContractType: '[türü]'.|Oluştur||  
|C|Open<br /><br /> [ClientBase&#124;ChannelFactory]. ContractType: '[türü]'.|Open||  
|I|Kapat [ClientBase&#124;ChannelFactory]. ContractType: '[türü]'.|Close||  
|M|ServiceHost oluşturun. ServiceType: '[türü]'.|Oluştur||  
|N|ServiceHost'ni açın. ServiceType: '[türü]'.|Open||  
|Z|ServiceHost kapatın. ServiceType: '[türü]'.|Close||  
|O|'[Address]' dinler.|ListenAt|Bu ve sonraki etkinliği aktarım özgüdür. ListenAt etkinlik olduğu anda kanal dinleyicisi dinler adresine eşleyen içeriğini temsil eder. Sıranın bir adresine eşleyen olduğundan MSMQ söz konusu olduğunda, sıra kalır. MSMQ durumunda MSMQ iletileri için bağlantı yönelimli aktarmaları durumunda gelen bağlantılar için bu etkinliği dinler. Bu etkinlik ServiceHost.Open() sırasında oluşturulur ve oluşturma ve atma dinleyicisi, yanı sıra tüm ReceiveBytes etkinlikler için dışarı aktarma ile ilgili izlemeleri içerir.|  
|P|Bayt [address] bağlantıda alırsınız. MSMQ iletisi alırsınız.|ReceiveBytes|Bu etkinlikte sonunda bir WCF iletisi alırsınız veriler işlenir. Gelen bayt bağlantı yönelimli taşıma veya http söz konusu olduğunda beklendi. Bağlantı oluşturulduğunda oluşturulan TCP/adlandırılmış kanal için bu etkinlik ömrü bağlantı ömrü aynıdır. Http için bir ileti isteğini ömrü olduğundan ve ileti gönderildiğinde oluşturulur. Bu etkinlik oluşturma ve uygulanabilirse bağlantı atma ilgili izlemeleri içerir, aynı zamanda tüm ileti (nesne) işleme etkinlikler için dışarı aktarır.<br /><br /> MSMQ söz konusu olduğunda, bunu burada MSMQ iletisi alınır etkinliktir.|  
|Q|İşlem iletisi [sayı]. (Not, [sayı], 1 ile başlayan artan bir değer olur.)|ProcessMessage|Gelen ileti işleme. Bir WCF ileti nesnesi oluşturmak için tüm verileri (bayt, MSMQ iletisi) alındığında bu etkinliği başlatır. Bu etkinlik izlemeleri üstbilgi işlemeyi ile ilgilidir.<br /><br /> Dağıtılması bir ileti biçimlendirilmiş sonra ServiceHost ProcessAction etkinlik için karşılık gelen etkinlik kimliği bakan geçiş yapıldı|  
|D, S|İşlem bir eylem '[eylem]'.|ProcessAction|Üzerinde kullanıcı kodu için ileti gönderilirken için güvenlik/aktarım/RM yığını aracılığıyla iletisi, işlem ve ters sırada gönderme.<br /><br /> "Etkinlik yayma"; aracılığıyla ileti üstbilgisinde gönderilirse sunucu üzerinde bu etkinlik yayılan etkinlik kimliği kullanır. Aksi takdirde, yeni bir GUID oluşturulur.<br /><br /> Yanıt iletisi istek/yanıt sözleşmeleri için de bu etkinlikte işlenir.|  
|T|'[IContract.Operation]' yürütün.|ExecuteUserCode|Gönderme hizmeti tarafında sonra kullanıcı kodu yürütün. Bu etkinliği kullanıcı tarafından sağlanan kod ServiceHost kodundan ayırmak için bir sınır sağlar.|  
  
## <a name="security-activities"></a>Güvenlik etkinlikleri  
 Aşağıdaki tabloda güvenlik ile ilgili tüm etkinlikleri listeler.  
  
|Etkinlik Adı|Etkinlik Türü|Açıklama|  
|-------------------|-------------------|-----------------|  
|Kurulum güvenli oturum|SetupSecurity|Yalnızca istemci tarafında bulunmaktadır. İçeren tüm RST * / SCT alış verişleri kimlik doğrulaması ve güvenlik bağlamını ayarlanması için. Varsa `propagateActivity` = `true`, bu etkinlik hizmetin karşılık gelen işlemi eylem RST ile birleştirilmiş\*/SCT etkinlikler.|  
|Güvenli Oturumu Kapat|SetupSecurity|İstemci tarafında bulunmaktadır. Güvenli oturum kapatma iptal ileti değişimi içerir. Varsa `propagateActivity` = `true`, bu etkinlik hizmetinden işlem eylem "İptal" ile birleştirilir.|  
  
 Aşağıdaki tabloda, COM + ilgili tüm etkinlikleri listelenmektedir.  
  
|Etkinlik Adı|Etkinlik Türü|Açıklama|  
|-------------------|-------------------|-----------------|  
|COM + örneği oluşturma|TransferToCOMPlus|Her COM + 1 etkinliği örneği, WCF koddan çağırma|  
|COM + yürütme \<işlemi >|TransferToCOMPlus|Her COM + 1 etkinliği örneği, WCF koddan çağırma|  
  
## <a name="wmi-activities"></a>WMI etkinlikleri  
 Aşağıdaki tabloda WMI ile ilgili tüm etkinlikleri listeler.  
  
|Etkinlik Adı|Etkinlik Türü|Açıklama|  
|-------------------|-------------------|-----------------|  
|WMI Al|WMIGetObject|Kullanıcı verileri WMI'dan alıyor.|  
|WMI put|WmiPutInstance|Kullanıcı verileri WMI ile güncelleştiriliyor.|
