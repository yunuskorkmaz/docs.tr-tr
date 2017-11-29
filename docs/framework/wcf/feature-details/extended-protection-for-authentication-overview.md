---
title: "Kimlik Doğrulama için Genişletilmiş Koruma Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d2ceffe-a7bf-4bd9-a5a2-9406423bd7f8
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: d8dadf09434778bc32bb75c5eff5ff4cb0494373
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="extended-protection-for-authentication-overview"></a>Kimlik Doğrulama için Genişletilmiş Koruma Genel Bakış
Kimlik doğrulaması için genişletilmiş koruma, bir saldırganın istemci kimlik bilgilerini yakalar ve bunları bir sunucuya iletir man-in--middle (MITM) saldırılarına karşı korunmasına yardımcı olur.  
  
 Üç katılımcılar bir senaryoyu düşünün: bir istemci, sunucu ve saldırgan. Sunucunun URL'sine sahip `https://server`, saldırgan URL sahipken `https://attacker`. Saldırgan, sunucunun değilmiş gibi saldırgan erişme içine istemci püf noktaları. Saldırgan sonra sunucuya istek gönderir. Saldırgan güvenli bir kaynağa erişmeye çalıştığında, sunucunun bir WWW-Authenticate üstbilgisi olan saldırgan yanıtlar. İstemcide WWW-Authenticate üstbilgisi gönderir şekilde saldırgan kimlik doğrulama bilgileri yok. İstemci yetkilendirme üst bilgisi bir saldırgana gönderir ve saldırgan sunucu üstbilgi gönderir ve istemci kimlik bilgileri kullanılarak güvenli kaynaklara erişim alır.  
  
 Şu anda bir istemci uygulaması kendisini Kerberos, Özet veya HTTPS kullanarak NTLM kullanarak sunucuya doğruladığında bir aktarım düzeyi güvenlik (TLS) kanalı ilk kurulur ve kimlik doğrulaması bu kanalı kullanılarak gerçekleştirilir. Ancak, Güvenli Yuva Katmanı (SSL) tarafından oluşturulan oturum anahtarı ile kimlik doğrulaması sırasında oluşturulan oturum anahtarı arasındaki hiçbir bağlama yok. Bu nedenle, önceki senaryoda, iletişimin (örneğin, bir HTTPS kanalı), TLS üzerinden yer alıyorsa vardır oluşturulan iki SSL kanalı: bir istemci ve saldırgan ve başka bir saldırgan ve sunucu arasında arasında. İstemcinin kimlik bilgileri istemciden sunucuya ilk saldırgan ile istemci arasında SSL kanalı üzerinden ve sonra saldırgan ve sunucu arasında kanal üzerinden gönderilir. İstemcinin kimlik bilgilerini sunucu ulaştığınızda, sunucu üzerinde bu kimlik bilgilerini gönderilen kanal saldırgan ve istemci ile kaynaklanan algılama olmadan kimlik bilgilerini doğrular.  
  
 , TLS güvenli bir dış kanal hem de istemci kimlik doğrulaması iç kanal ve bir kanal bağlama belirteci (CBT) sunucusuna iletmek için çözümüdür. CBT TLS güvenlikli dış kanal bir özelliktir ve istemci kimlik doğrulaması iç kanalı üzerinden bir konuşma dış kanalına bağlamak için kullanılır.  
  
 Önceki senaryoda, istemci saldırgan TLS kanalı CBT sunucuya gönderilen yetkilendirme bilgilerle birleştirilir. CBT algılayan bir sunucu, istemci saldırgan kanala saldırgan sunuculu kanala bağlı CBT karşılık gelen istemci kimlik doğrulaması bilgilerini bulunan CBT karşılaştırır. Bir CBT bir kanalın hedefe belirli olduğundan istemci-saldırgan CBT saldırgan-sunucu CBT eşleşmiyor. Bu sunucunun MITM saldırı algılama ve kimlik doğrulama isteği reddeder sağlar.  
  
 İstemci tarafı herhangi bir yapılandırma ayarı gerektirmez. İstemci CBT sunucuya geçirmek için güncelleştirilmiş sonra bunu her zaman yapar. Sunucu da güncelleştirildiyse yok sayın veya CBT kullanmak üzere yapılandırılabilir. Bunu güncelleştirilmemiş varsa, onu yoksayar.  
  
 Sunucunun aşağıdaki koruma düzeylerini sahip olabilir:  
  
-   Yok. Bir kanal bağlama doğrulama yapılmaz. Güncellenmedi tüm sunucuların davranış budur.  
  
-   Kısmi. Güncelleştirilen tüm istemcilerin sunucuya kanal bağlama bilgileri sağlamanız gerekir. Güncellenmedi istemciler Bunu yapmak gerekmez. Uygulama uyumluluğu için izin veren bir ara seçenek budur.  
  
-   Tam. Tüm istemcilerin, kanal bağlama bilgileri sağlamanız gerekir. Sunucunun bunu yapmayın istemcilerinden gelen kimlik doğrulama istekleri reddeder.  
  
 Daha fazla bilgi için Win7 CBT/genişletilmiş koruma örneğe bakın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Server App Fabric için güvenlik modeli](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
