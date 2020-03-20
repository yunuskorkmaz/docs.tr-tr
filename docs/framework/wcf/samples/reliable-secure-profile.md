---
title: Güvenilir Güvenlik Profili
ms.date: 03/30/2017
ms.assetid: 921edc41-e91b-40f9-bde9-b6148b633e61
ms.openlocfilehash: 9ddd0d78396bba6712650620e6b46c62f13337e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144220"
---
# <a name="reliable-secure-profile"></a>Güvenilir Güvenlik Profili

Bu örnek, WCF ve [Güvenilir Güvenli Profil (RSP)](http://www.ws-i.org/Profiles/ReliableSecureProfile-1.0.html)nasıl oluşturulabildiğini göstermektedir. Bu örnek, RSP belirtimine dayalı bir Güvenilir Güvenli Bağlama oluşturmak için Güvenilir İleti ve isteğe bağlı olarak güvenli bir kanal la birlikte oluşturulabilen bir [Bağlantı](http://docs.oasis-open.org/ws-rx/wsmc/200702/wsmc-1.0-spec-cs-01.pdf) Yap kanalının uygulanmasını göstermektedir.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ReliableSecureProfile`  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek, güvenilir bir eşzamanlı iki yönlü ileti değişimi senaryosu gösterir. Hizmetin çift yönlü bir sözleşmesi vardır ve istemci çift yönlü geri arama sözleşmesini uygular. İstemci, ayrı bir bağlantıda yanıt bekleniyor bir hizmet için bir istek başlatır. İstek iletisi güvenilir bir şekilde gönderilir. İstemci sonunda bir dinleme bitiş noktası açmak istemiyor. Böylece, bu 'Bağlantı Yap' isteğinin arka kanalında yanıtı geri göndermek için hizmet için 'Bağlantı Yap' istekleri ile hizmet anketler. Bu örnek, istemci bir dinleme bitiş noktası (ve bir güvenlik duvarı özel durum oluşturma) açığa olmadan HTTP üzerinden güvenli güvenilir çift yönlü iletişim nasıl gösterin.  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. **ReliableSecureProfile** çözümlerini açın.  
  
2. **Çözüm Gezgini'nde** **Hizmet** projesine sağ tıklayın, **Hata Ayıklama'yı**seçin , bağlam menüsünden **yeni örneği başlat'** ı seçin. Bu, servis ana bilgisayarını başlatır.  
  
3. **Çözüm Gezgini'nde** **İstemci** projesini sağ tıklatın, **Hata Ayıklama'yı**seçin , bağlam menüsünden **yeni örnek başlat'** ı seçin. Bu müşteriyi başlatıyor.  
  
4. İstemci konsol penceresinde ki istemi herhangi bir dize yazın ve ENTER'u tıklatın. Bu, giriş dizesini hizmete gönderir ve bu dizedeki bir karmayı hesaplar.  
  
5. Servis, sonucu istemci konsol penceresinde görüntülemek için çift yönlü geri arama sözleşmesi işlemini geri aradığında sonucu istemci pencerelerinde görüntüleyin. Verileri işleme uzun süren bir işlem simüle etmek için hizmet kasıtlı bir gecikme vardır.  
  
6. HTTP trafiğinin izlenmesi (Network Monitor, Fiddler vb. gibi çevrimiçi ağ izleme araçlarından herhangi biri tarafından) müşteri ile Hizmet arasında Güvenilir Güvenli Profil tarafından belirlenen bir iletişim dizisinin kurulduğunu ve istemcinin nasıl 'Bağlantı Yap' istekleriyle hizmeti yoklar. Hizmet işlenmiş yanıtı geri göndermeye hazır olduğunda, sonuçları geri göndermek için son 'Bağlantı Yap' isteğinin arka kanalını kullanır.  
  
7. Hizmeti kapatmak için servis konsolu penceresinde ENTER tuşuna basın. İstemciyi kapatmak için istemci konsol penceresinde ENTER tuşuna basın.
