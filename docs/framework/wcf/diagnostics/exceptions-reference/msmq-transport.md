---
title: MSMQ Taşıma
ms.date: 03/30/2017
ms.assetid: 3f29a2fe-24df-4614-b64c-b0c084fb7003
ms.openlocfilehash: a2e5384808b82f48bd1d4856bf893130da8c5f1b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61959425"
---
# <a name="msmq-transport"></a>MSMQ Taşıma
Bu konu, MSMQ taşıma tarafından oluşturulan tüm özel durumları listeler.  
  
## <a name="exception-list"></a>Özel durum listesi  
  
|Kaynak kodu|Kaynak dizesi|  
|-------------------|---------------------|  
|MsmqActiveDirectoryRequiresNativeTransfer|İleti için bağlama doğrulaması başarısız oldu. İstemci iletileri gönderemiyor. Bir çakışma bağlama özelliklerinde bu hataya neden oldu. İse true ve QueueTransferProtocol doğal olarak ayarlanır. Çakışmayı çözmek için özelliklerinden düzeltin.|  
|MsmqAuthNoneRequiresProtectionNone|Hizmet için bağlama doğrulaması başarısız oldu. Hizmet uç noktası veya istemci başlatılamıyor. Bir çakışma bağlama özelliklerinde bu hataya neden oldu. MsmqAuthenticationMode hiçbiri olarak ayarlandı ve MsmqProtectionLevel None olarak ayarlı değil. Çakışmayı gidermek için özelliklerinden düzeltin.|  
|MsmqCustomRequiresPerAddDLQ|İleti için bağlama doğrulaması başarısız oldu. İstemci, ileti gönderemezsiniz. DeadLetterQueue özel olarak ayarlanmış, ancak CustomDeadLetterQueue belirtilmemiş. Her uygulama için geçerliliğini yitirmiş kuyruk URI'sini CustomDeadLetterQueue özelliğini belirtin.|  
|MsmqDeserializationError|XML iletisi seri durumdan çıkarılırken bir hata ile karşılaşıldı. İleti alınamaz ve bırakılır.|  
|MsmqDLQNotWriteable|İstemcisi için bağlama doğrulaması başarısız oldu. İstemci, bir ileti gönderemezsiniz. Belirtilen eski ileti sırası yok veya yazılamaz. Sıranın yazma için uygun yetkilere sahip olduğundan emin olun.|  
|MsmqGetPrivateComputerInformationError|Sürüm denetimi, belirtilen hata nedeniyle başarısız oldu. Sıraya alınan kanalı tüm işlemleri başarısız olur, MSMQ sürümü algılanamıyor. MSMQ'ın yüklenmiş ve kullanılabilir olduğundan emin olun.|  
|MsmqNoAssurancesForVolatile|Hizmet için bağlama doğrulaması başarısız oldu. Hizmet uç noktası veya istemci başlatılamıyor. Özelliği true olarak ve dayanıklı özelliğinin ayarlanır. ExactlyOnce yanlış olarak ayarlanır. Bu işlem desteklenmez. Çakışmayı çözmek için bu özelliklerden birini düzeltin.|  
|MsmqNonTransactionalQueueNeeded|MSMQ sırası yapılandırması ve bağlama arasında bir uyumsuzluk algılandı. Hizmet uç noktası başlatılamıyor. ExactlyOnce özelliği false olarak ayarlanır ve gelen iletileri okumak için bir işlem kuyruğu kuyruğudur. Doğru veya işlem olmayan bir bağlama oluşturun ExactlyOnce özelliğini ayarlayarak hatasını düzeltin.|  
|MsmqOpenError|Belirtilen sıra açılırken bir hata oluştu. İleti gönderildi veya kuyruktan alınan. MSMQ yüklü ve çalışıyor olduğundan emin olun. Ayrıca kuyruk gerekli erişim modu ve yetkilendirme ile açmak kullanılabilir olduğundan emin olun.|  
|MsmqPathLookupError|Belirtilen sıra yolu adı biçim adına dönüştürülürken bir hata oluştu. Sıraya alınan kanal üzerindeki tüm işlemler başarısız oldu. Kuyruk adresi geçerli olduğundan emin olun. MSMQ Active Directory Tümleştirmesi ile etkinleştirildi yüklü olmalıdır ve erişimi kullanılabilir.|  
|MsmqPerAppDLQRequiresCustom|İstemci üzerinde bağlama doğrulaması başarısız oldu. İstemci iletileri gönderemiyor. CustomDeadLetterQueue özelliği ayarlanmış ancak özel olarak DeadLetterQueue özelliği ayarlı değil. DeadLetterQueue özelliği Custom ölerek ayarlayın.|  
|MsmqPerAppDLQRequiresExactlyOnce|İstemcisi için bağlama doğrulaması başarısız oldu. İstemci iletileri gönderemiyor. Bir çakışma Bağlama özelliklerindeki hataya neden oluyor. Özel eski ileti sırası kullanmak için ExactlyOnce çakışmayı gidermek için true olarak ayarlanmalıdır.|  
|MsmqPerAppDLQRequiresMsmq4|MSMQ Yapılandırma ve bağlama arasında bir uyumsuzluk algılandı. İstemci iletileri gönderemiyor. Özel eski ileti sırası kullanmak için MSMQ sürüm 4.0 veya üstü olmalıdır. MSMQ sürüm 4.0 veya üstü yoksa DeadLetterQueue özelliği sistem veya None olarak ayarlanmış.|  
|MsmqReceiveError|Kuyruktan bir ileti alınırken bir hata oluştu. MSMQ yüklü ve çalışıyor olduğundan emin olun. Kuyruğa almak kullanılabilir olduğundan emin olun.|  
|MsmqSameTransactionExpected|Bu oturum için bir işlem hatası oluştu. Oturum kanalı hatalı. Oturumdaki iletileri gönderilen veya alınan. Sıraya alınan bir oturum ile birden fazla işlem ilişkilendirilemiyor. Oturum içindeki tüm iletileri gönderilir veya tek bir işlem kullanılarak alınan emin olun.|  
|MsmqSendError|Belirtilen sıraya gönderilirken bir hata oluştu. MSMQ yüklü ve çalışıyor olduğundan emin olun. Yerel bir kuyruğa gönderiyorsanız, yetkilendirme ve gerekli erişim modu ile sıranın var emin olun.|  
|MsmqTimeSpanTooLarge|İleti yaşam süresi çok büyük. İleti gönderilemiyor. İleti yaşam süresi (TTL) Int32 maksimum değeri aşamaz.|  
|MsmqTokenProviderNeededForCertificates|Bir X509SecurityTokenProvider öğesi bulunamıyor. İleti gönderilemiyor. Sertifika kimlik doğrulaması modunu X.509 belirteç sağlayıcısı gerektirir. Bir güvenlik belirteci sağlayıcı için yüklü sertifikayı kullanılabilir olduğundan emin olun.|  
|MsmqTransactedDLQExpected|MSMQ Yapılandırma bağlama arasında bir uyuşmazlığı oluştu. İleti gönderilemiyor. İletim sırası bağlamasında belirtilen özel eski ileti sırası olması gerekir. Özel eski ileti sırası adresin doğru olduğundan ve sıranın işlem sırası olduğundan emin olun.|  
|MsmqTransactionalQueueNeeded|Bağlama ve MSMQ sırası yapılandırması arasında bir uyuşmazlık oluştu. Hizmet uç noktası başlatılamıyor. Özelliği true ve kuyruk iletileri okumak için ayarlanmış ExactlyOnce işlem sırası değildir. İçin hatayı düzeltmek için ExactlyOnce özelliğini false olarak ayarlayın veya bu bağlama için bir işlem kuyruğu oluşturun.|  
|MsmqTransactionCurrentRequired|Hiçbir işlem oturumda ileti göndermek kullanılabilir. Sıraya alınan bir oturumda ileti göndermek için bir işlem gerektirir. İşlem kapsamı oturumda ileti göndermek için belirtildiğinden emin olun.|  
|MsmqTransactionRequired|Bir işlem gerekiyor ancak yok. İletileri gönderilen veya alınan. İşlem kapsamı ileti göndermek veya almak için belirtildiğinden emin olun.|  
|MsmqUnsupportedSerializationFormat|Seri durumundan çıkarma hatası oluştu. İleti alınamaz ve bırakılır. Belirtilen serileştirme biçimi desteklenmiyor.|  
|MsmqWrongPrivateQueueSyntax|URL geçersiz. Kuyruk URL'si, '$' karakterini içeremez. Söz dizimi içinde.MSMQ://machine/private/queueName özel sıra ele almak için kullanın.|
