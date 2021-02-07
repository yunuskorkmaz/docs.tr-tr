---
description: 'Daha fazla bilgi edinin: MSMQ aktarımı'
title: MSMQ Taşıma
ms.date: 03/30/2017
ms.assetid: 3f29a2fe-24df-4614-b64c-b0c084fb7003
ms.openlocfilehash: af371a6481e7137321f1c32d0183f68e529d13d3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99686355"
---
# <a name="msmq-transport"></a>MSMQ Taşıma

Bu konu, MSMQ taşıması tarafından oluşturulan tüm özel durumları listeler.  
  
## <a name="exception-list"></a>Özel durum listesi  
  
|Kaynak kodu|Kaynak dizesi|  
|-------------------|---------------------|  
|MsmqActiveDirectoryRequiresNativeTransfer|İleti için bağlama doğrulaması başarısız oldu. İstemci ileti gönderemiyor. Bağlama özelliklerindeki bir çakışma bu hataya neden oldu. UseActiveDirectory değeri true olarak ayarlanır ve QueueTransferProtocol yerel olarak ayarlanır. Çakışmayı çözmek için özelliklerden birini düzeltin.|  
|MsmqAuthNoneRequiresProtectionNone|Hizmet için bağlama doğrulaması başarısız oldu. Hizmet uç noktası veya istemcisi başlatılamıyor. Bağlama özelliklerindeki bir çakışma bu hataya neden oldu. MsmqAuthenticationMode, None olarak ayarlanmış ve MsmqProtectionLevel, None olarak ayarlanmadı. Çakışmayı çözmek için özelliklerden birini düzeltin.|  
|MsmqCustomRequiresPerAddDLQ|İleti için bağlama doğrulaması başarısız oldu. İstemci iletiyi gönderemiyor. DeadLetterQueue özel olarak ayarlanmış, ancak CustomDeadLetterQueue belirtilmemiş. CustomDeadLetterQueue özelliğindeki her uygulama için atılacak ileti sırasının URI 'sini belirtin.|  
|MsmqDeserializationError|XML iletisi seri durumdan çıkarılırken bir hatayla karşılaşıldı. İleti alınamıyor ve bırakıldı.|  
|MsmqDLQNotWriteable|İstemci için bağlama doğrulaması başarısız oldu. İstemci bir ileti gönderemiyor. Belirtilen atılacak mektup kuyruğu yok veya yazılamıyor. Kuyruğun kendisine yazmak için uygun yetkilendirmeyle aynı olduğundan emin olun.|  
|Msmqgetprivatecomputerınformationerror|Sürüm denetimi belirtilen hatayla başarısız oldu. MSMQ sürümü algılanamıyor ve sıraya alınan kanaldaki tüm işlemler başarısız olur. MSMQ 'nun yüklü olduğundan ve kullanılabilir olduğundan emin olun.|  
|MsmqNoAssurancesForVolatile|Hizmet için bağlama doğrulaması başarısız oldu. Hizmet uç noktası veya istemcisi başlatılamıyor. ExactlyOnce özelliği true olarak ayarlanır ve dayanıklı özelliği false olarak ayarlanır. Bu özellik desteklenmez. Çakışmayı çözmek için bu özelliklerden birini düzeltin.|  
|MsmqNonTransactionalQueueNeeded|Bağlama ve MSMQ kuyruğu yapılandırması arasında uyuşmazlık algılandı. Hizmet uç noktası başlatılamıyor. ExactlyOnce özelliği yanlış olarak ayarlanır ve iletilerin okunacağı kuyruk bir işlem kuyruğundan oluşturulur. ExactlyOnce özelliğini true olarak ayarlayarak ya da işlemsel olmayan bir bağlama oluşturarak hatayı düzeltin.|  
|MsmqOpenError|Belirtilen sıra açılırken bir hata oluştu. İleti kuyruktan gönderilemiyor veya alınamıyor. MSMQ 'nun yüklü olduğundan ve çalıştığından emin olun. Ayrıca, sıranın gerekli erişim modu ve yetkilendirme ile açılmasını sağlamak için kullanılabilir olduğundan emin olun.|  
|MsmqPathLookupError|Belirtilen sıra yolu adı biçim adına dönüştürülürken bir hata oluştu. Sıraya alınan kanaldaki tüm işlemler başarısız oldu. Kuyruk adresinin geçerli olduğundan emin olun. MSMQ, Active Directory tümleştirme etkin ve erişilebilir hale gelmelidir.|  
|MsmqPerAppDLQRequiresCustom|İstemcideki bağlama doğrulaması başarısız oldu. İstemci ileti gönderemiyor. CustomDeadLetterQueue özelliği ayarlandı, ancak DeadLetterQueue özelliği Custom olarak ayarlanmadı. DeadLetterQueue özelliğini Custom olarak ayarlayın.|  
|MsmqPerAppDLQRequiresExactlyOnce|İstemci için bağlama doğrulaması başarısız oldu. İstemci ileti gönderemiyor. Bağlama özelliklerindeki bir çakışma hataya neden oluyor. Özel atılacak ileti sırasını kullanmak için,, çakışmaya çözüm vermek üzere ExactlyOnce değeri true olarak ayarlanmalıdır.|  
|MsmqPerAppDLQRequiresMsmq4|Bağlama ile MSMQ yapılandırması arasında bir uyumsuzluk algılandı. İstemci ileti gönderemiyor. Özel atılacak mektup sırasını kullanmak için MSMQ 4,0 veya daha yüksek bir sürümü gerekir. MSMQ sürüm 4,0 veya üzeri bir sürümü yoksa, DeadLetterQueue özelliğini System veya None olarak ayarlayın.|  
|MsmqReceiveError|Sıradan bir ileti alınırken hata oluştu. MSMQ 'nun yüklü olduğundan ve çalıştığından emin olun. Kuyruğun alma için kullanılabilir olduğundan emin olun.|  
|Msmqsametransactionbekleniyordu|Bu oturum için bir işlem hatası oluştu. Oturum kanalı hatalı. Oturumdaki iletiler gönderilemiyor veya alınamıyor. Kuyruğa alınmış bir oturum, birden fazla işlemle ilişkilendirilemez. Oturumdaki tüm iletilerin tek bir işlem kullanılarak gönderildiğinden veya alındığından emin olun.|  
|MsmqSendError|Belirtilen sıraya gönderilirken bir hata oluştu. MSMQ 'nun yüklü olduğundan ve çalıştığından emin olun. Yerel bir kuyruğa gönderiyorsanız, sıranın gerekli erişim modu ve yetkilendirmeyle mevcut olduğundan emin olun.|  
|MsmqTimeSpanTooLarge|İleti yaşam süresi çok büyük. İleti gönderilemiyor. İleti yaşam süresi (TTL), Int32 en büyük değerini aşamaz.|  
|MsmqTokenProviderNeededForCertificates|Bir X509SecurityTokenProvider bulunamıyor. İleti gönderilemiyor. Sertifika kimlik doğrulama modu bir X. 509.440 belirteç sağlayıcısı gerektirir. Yüklü sertifika için bir güvenlik belirteci sağlayıcısının kullanılabildiğinden emin olun.|  
|MsmqTransactedDLQExpected|Bağlama ile MSMQ yapılandırması arasında uyuşmazlık oluştu. İletiler gönderilemiyor. Bağlamada belirtilen özel atılacak mektup sırasının bir işlem sırası olması gerekir. Özel atılacak ileti sırası adresinin doğru olduğundan ve kuyruğun bir işlem sırası olduğundan emin olun.|  
|MsmqTransactionalQueueNeeded|Bağlama ile MSMQ kuyruğu yapılandırması arasında uyuşmazlık oluştu. Hizmet uç noktası başlatılamıyor. ExactlyOnce özelliği doğru olarak ayarlanır ve iletilerin okunacağı kuyruk bir işlem kuyruğu değildir. Hatayı düzeltmek için, ExactlyOnce özelliğini false olarak ayarlayın veya bu bağlama için bir işlem kuyruğu oluşturun.|  
|MsmqTransactionCurrentRequired|Oturumda ileti göndermek için kullanılabilir işlem yok. Sıraya alınmış bir oturumda ileti göndermek için bir işlem gerekir. İletiyi oturumda göndermek için bir işlem kapsamı belirtildiğinden emin olun.|  
|MsmqTransactionRequired|İşlem gerekli ancak kullanılamıyor. İletiler gönderilemiyor veya alınamıyor. İleti göndermek veya almak için işlem kapsamının belirtildiğinden emin olun.|  
|MsmqUnsupportedSerializationFormat|Seri kaldırma hatası oluştu. İleti alınamıyor ve bırakıldı. Belirtilen serileştirme biçimi desteklenmiyor.|  
|Msmqyanlışlıkla Gprivatequeuesyntax|URL geçersiz. Kuyruğun URL 'SI ' $ ' karakterini içeremez. Özel bir kuyruğu gidermek için net. MSMQ: gt Machine/Private/SıraAdı içindeki sözdizimini kullanın.|
