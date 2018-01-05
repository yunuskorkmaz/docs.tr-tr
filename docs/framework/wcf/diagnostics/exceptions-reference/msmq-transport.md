---
title: "MSMQ Taşıma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f29a2fe-24df-4614-b64c-b0c084fb7003
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3c8f1283a27488c56a866973270409c22efc1fb1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="msmq-transport"></a>MSMQ Taşıma
Bu konu MSMQ aktarım tarafından oluşturulan tüm özel durumları listeler.  
  
## <a name="exception-list"></a>Özel durum listesi  
  
|Kaynak kodu|Kaynak dizesi|  
|-------------------|---------------------|  
|MsmqActiveDirectoryRequiresNativeTransfer|İleti için bağlama doğrulanamadı. İstemci iletileri gönderemiyor. Bağlama özelliklerindeki bir çakışma bu hataya neden oldu. İse true ve QueueTransferProtocol doğal olarak ayarlayın. Çakışmayı çözmek için özelliklerden birini düzeltin.|  
|MsmqAuthNoneRequiresProtectionNone|Hizmeti için bağlama doğrulanamadı. Hizmet uç noktası ya da istemci başlatılamıyor. Bağlama özelliklerindeki bir çakışma bu hataya neden oldu. MsmqAuthenticationMode hiçbiri olarak ayarlanır ve MsmqProtectionLevel None olarak ayarlı değil. Çakışmayı gidermek için özelliklerden birini düzeltin.|  
|MsmqCustomRequiresPerAddDLQ|İleti için bağlama doğrulanamadı. İstemci ileti gönderilemiyor. DeadLetterQueue özel olarak ayarlanmış, ancak CustomDeadLetterQueue belirtilmemiş. Sahipsiz sıra her uygulama için URI CustomDeadLetterQueue özelliğinde belirtin.|  
|MsmqDeserializationError|XML iletisini kaldırılırken bir hata oluştu. İleti alınamaz ve bırakılır.|  
|MsmqDLQNotWriteable|İstemci için bağlama doğrulanamadı. İstemci bir ileti gönderilemiyor. Belirtilen sahipsiz sıra yok veya yazılamaz. Yazma için uygun yetkilere sahip sıranın var olduğundan emin olun.|  
|MsmqGetPrivateComputerInformationError|Sürüm denetimi belirtilen hatasıyla başarısız oldu. Sıraya alınan kanalı olmayan tüm işlemleri başarısız olur MSMQ sürümü algılanamıyor. MSMQ yüklü olduğundan ve kullanılabilir olduğundan emin olun.|  
|MsmqNoAssurancesForVolatile|Hizmeti için bağlama doğrulanamadı. Hizmet uç noktası ya da istemci başlatılamıyor. Özelliği true ve sağlam özelliği için ayarlanmış ExactlyOnce false olarak ayarlanır. Bu işlem desteklenmiyor. Çakışmayı çözmek için bu özelliklerden birini düzeltin.|  
|MsmqNonTransactionalQueueNeeded|Bağlama ve MSMQ sıra yapılandırması arasında uyumsuzluk algılandı. Hizmet uç noktası başlatılamıyor. ExactlyOnce özelliği false olarak ayarlandığında ve kuyruğa alınan iletileri okumak için bir işlem sırası. Doğru veya işlemsel olmayan bir bağlama oluşturun ExactlyOnce özelliği ayarlanarak hatayı düzeltin.|  
|MsmqOpenError|Belirtilen sıra açılırken bir hata oluştu. İleti gönderilen veya alınan sıradan. MSMQ yüklü olduğundan ve çalıştığından emin olun. Ayrıca sıranın gerekli erişim modu ve yetkilendirme açmak kullanılabilir olduğundan emin olun.|  
|MsmqPathLookupError|Belirtilen sıra yol adı biçim adına dönüştürürken bir hata oluştu. Sıraya alınan kanalındaki tüm işlemleri başarısız oldu. Sıra adres geçerli olduğundan emin olun. MSMQ Active Directory Tümleştirme ile etkinleştirilmiş yüklü olmalıdır ve erişimi kullanılabilir.|  
|MsmqPerAppDLQRequiresCustom|İstemci üzerinde bağlama doğrulaması başarısız oldu. İstemci iletileri gönderemiyor. CustomDeadLetterQueue özelliği ayarlanmış ancak DeadLetterQueue özelliği özel olarak ayarlanmadı. DeadLetterQueue özelliğini özel olarak ayarlayın.|  
|MsmqPerAppDLQRequiresExactlyOnce|İstemci için bağlama doğrulanamadı. İstemci iletileri gönderemiyor. Bağlama özelliklerindeki bir çakışma bu hataya neden oluyor. Özel sahipsiz sırayı kullanmak için ExactlyOnce çakışmayı gidermek için true olarak ayarlanmalıdır.|  
|MsmqPerAppDLQRequiresMsmq4|Bağlama ve MSMQ Yapılandırma arasında uyumsuzluk algılandı. İstemci iletileri gönderemiyor. Özel sahipsiz sırayı kullanmak için MSMQ sürüm 4.0 veya üstü olmalıdır. MSMQ sürüm 4.0 veya üstü yoksa DeadLetterQueue özelliği sistem veya None olarak ayarlanmış.|  
|MsmqReceiveError|Kuyruktan bir ileti alınırken bir hata oluştu. MSMQ yüklü olduğundan ve çalıştığından emin olun. Sıraya almak kullanılabilir olduğundan emin olun.|  
|MsmqSameTransactionExpected|Bu oturum için bir işlem hatası oluştu. Oturum kanalı hata döndürdü. Oturumdaki iletilerin gönderilen veya alınan. Sıraya alınan bir oturum ile birden fazla işlem ilişkilendirilemiyor. Oturumdaki tüm iletilerin gönderilen veya tek bir işlem kullanılarak alınan emin olun.|  
|MsmqSendError|Belirtilen sıraya gönderilirken bir hata oluştu. MSMQ yüklü olduğundan ve çalıştığından emin olun. Yerel bir sıra gönderiyorsanız, gerekli erişim modu ve yetkilendirme sıranın mevcut emin olun.|  
|MsmqTimeSpanTooLarge|İleti yaşam süresi çok büyük. İleti gönderilemiyor. İletinin yaşam süresi (TTL) Int32 en büyük değeri aşamaz.|  
|MsmqTokenProviderNeededForCertificates|Bir X509SecurityTokenProvider öğesi bulunamıyor. İleti gönderilemiyor. Sertifika kimlik doğrulama modu, bir X.509 belirteç sağlayıcısı gerektirir. Bir güvenlik belirteci sağlayıcısı için yüklü sertifikayı kullanılabilir olduğundan emin olun.|  
|MsmqTransactedDLQExpected|Bağlama ve MSMQ Yapılandırması arasında bir uyuşmazlığı oluştu. İleti gönderilemiyor. Bağlamada belirtilen özel sahipsiz sırayı iletim sırası olması gerekir. Özel sahipsiz sırayı adresinin doğru olduğundan ve bir işlem sırası olduğundan emin olun.|  
|MsmqTransactionalQueueNeeded|Bağlama ve MSMQ sıra yapılandırması arasında bir uyuşmazlık oluştu. Hizmet uç noktası başlatılamıyor. Özelliği true ve sıraya alınan iletileri okumak için olarak ayarlanmış ExactlyOnce işlemsel bir sıra değil. Hatayı düzeltmek için ExactlyOnce özelliğini false olarak ayarlayın veya bu bağlama için bir işlem sırası oluşturun.|  
|MsmqTransactionCurrentRequired|Hiçbir işlem oturumda ileti göndermek kullanılabilir. Sıraya alınan bir oturumda ileti göndermek için bir işlem gerekiyor. Bir işlem kapsamı oturumda ileti göndermek için belirtildiğinden emin olun.|  
|MsmqTransactionRequired|Bir işlem gerekiyor ancak yok. İletiler gönderilen veya alınan. İşlem kapsamı ileti göndermek veya almak için belirtildiğinden emin olun.|  
|MsmqUnsupportedSerializationFormat|Seri durumundan çıkarma hatası oluştu. İleti alınamaz ve bırakılır. Belirtilen seri hale getirme biçimi desteklenmiyor.|  
|MsmqWrongPrivateQueueSyntax|URL geçersiz. Sıra için URL '$' karakterini içeremez. Özel bir sıra adreslemek için.MSMQ://machine/private/queueName sözdizimini kullanın.|
