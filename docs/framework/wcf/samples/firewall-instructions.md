---
title: Güvenlik Duvarı Yönergeleri
ms.date: 03/30/2017
ms.assetid: a7dc429f-65ac-4faf-974a-77d5fb977fe1
ms.openlocfilehash: f1b576b4e413fa3bae70ef1eb8f8ed768e28e309
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051942"
---
# <a name="firewall-instructions"></a>Güvenlik Duvarı Yönergeleri
Windows Communication Foundation (WCF) örnekleri çalışması birkaç Güvenlik Duvarı'nda Program veya bağlantı noktalarını etkinleştirmeniz gerekir. Birçok örnekleri 8000-8003 aralığındaki bağlantı noktaları kullanılarak iletişim kurmak ve 9000 bağlantı noktası. Güvenlik Duvarı varsayılan olarak açıktır ve bu bağlantı noktalarına erişimi engeller. Örnekler için güvenlik duvarını etkinleştirmek için gereksinimler ve güvenlik ortamı bağlı olarak aşağıdaki yordamlardan birini tamamlayın:  
  
- 1. seçenek: Etkileşimli olarak çalışırken örnekleri sağlar. Güvenlik duvarı yapılandırmanızı hiçbir öncelikli değişiklik yaparak oluşturmaya ve örnekleri çalıştırmaya başlamak için devam edin. Bir örneği çalıştırdığınızda bir **Windows Güvenlik Uyarısı** iletişim kutusu görüntülenir. Söz konusu örnek program ardından etkileşimli bir engeli listesine eklenebilir. Bu yordamı kullanarak, ardından örnek yeniden başlatmanız gerekebilir.  
  
- 2. seçenek: Örnek programları önceden etkinleştirin. Başlangıç **Windows Güvenlik Duvarı'nı Denetim Masası'ndaki** uygulaması ve örnek çalıştırmak için plan programları etkinleştirin. Yürütülebilir dosyalar için program önce oluşturmanız gerekir. Aşağıdaki yordamda ayrıntılı yönergeleri bulabilirsiniz.  
  
- Seçenek 3: Önceden bir bağlantı noktası aralığını etkinleştirin. Başlangıç **Windows Güvenlik Duvarı** **Denetim Masası** uygulaması ve etkinleştirme bağlantı noktası 80, 443, 8000 8003 ve örnekleri tarafından kullanılan 9000. Aşağıdaki yordamda ayrıntılı yönergeleri bulabilirsiniz. Bu bağlantı noktaları, yalnızca örnekleri kullanmak tüm programı izin verdiğinden bu diğerlerine göre daha az güvenli bir seçenektir.  
  
 Hangi yordamın emin değilseniz, ilk seçenek seçin. Başka bir satıcıdan bir güvenlik duvarı çalıştırıyorsanız, benzer değişiklikler yapmanız gerekebilir.  
  
> [!IMPORTANT]
>  Güvenlik duvarı yapılandırmanızı değiştirmeden güvenlik etkiler. Kaydettiğiniz değişiklikleri yapın ve örnekler ile çalışmayı bitirseniz bile bunları kaldırmanız önerilir.  
  
### <a name="to-enable-samples-programs-in-advance"></a>Önceden örnekleri programları etkinleştirmek için  
  
1. Örneği derleyin.  
  
2. Tıklayın **Başlat**, tıklayın **çalıştırma**ve türü `firewall.cpl`. Bu açılır **Windows Güvenlik Duvarı'nı Denetim Masası'ndaki** uygulaması.  
  
    > [!NOTE]
    >  Windows Güvenlik Duvarı üzerinden iletişim gerektirir örnekleri çalıştırmak için Güvenlik Duvarı ayarlarını değiştirme izniniz olmalıdır. Bazı güvenlik duvarı ayarları ve bilgisayarınız bir etki alanına bağlıysa, sistem yöneticiniz bu ayarları Grup İlkesi aracılığıyla denetleme.  
  
3. Bir program Windows Güvenlik Duvarı üzerinden izin vermek için aşağıdaki işletim belirli adımlardan birini tamamlayın:  
  
    - Windows 7 veya Windows Server 2008 r2 üzerinde tıklayın **bir programı veya özelliği Windows Güvenlik Duvarı üzerinden izin**. Tıklayın **ayarlarını değiştir**, izin **başka bir Program...** .  
  
    - Üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)] veya [!INCLUDE[lserver](../../../../includes/lserver-md.md)], tıklayın **bir programın Windows Güvenlik Duvarı üzerinden izin**.  
  
4. Üzerinde **özel durumları** sekmesinde **Program Ekle**.  
  
5. Tıklayın **Gözat** düğmesine tıklayın ve çalıştırmayı planladığınız örnek yürütülebilir dosyayı seçin.  
  
6. Yürütülebilir dosyalar çalıştırmayı planladığınız tüm örnekleri ekleyene kadar 4 ve 5. adımları tekrarlayın.  
  
7. Tıklayın **Tamam** güvenlik duvarı uygulamasını kapatın.  
  
### <a name="to-enable-a-port-range-in-advance"></a>Önceden bir bağlantı noktası aralığı etkinleştirmek için  
  
1. Tıklayın **Başlat**, tıklayın **çalıştırma**ve türü `firewall.cpl`. Bu açılır **Windows Güvenlik Duvarı'nı Denetim Masası'ndaki** uygulaması.  
  
2. Windows 7 veya Windows Server 2008 R2, aşağıdaki adımları izleyin.  
  
    1. Tıklayın **Gelişmiş ayarlar** Windows Güvenlik Duvarı'nı pencerenin sol sütunda.  
  
    2. Tıklayın **gelen kuralları** sol sütunda.  
  
    3. Tıklayın **yeni kurallar** sağ sütunda.  
  
    4. Seçin **bağlantı noktası** tıklatıp **sonraki**.  
  
    5. Seçin **TCP** girin `8000, 8001, 8002, 8003, 9000, 80, 443` içinde **belirli yerel bağlantı noktaları** alan.  
  
    6. **İleri**'ye tıklayın.  
  
    7. Seçin **bağlantıya izin**, tıklatıp **sonraki** .  
  
    8. Seçin **etki alanı** ve **özel**, tıklatıp **sonraki**.  
  
    9. Bu kural ad `WCF-WF 4.0 Samples`, tıklatıp **son**.  
  
    10. Tıklayın **giden kuralları** ve h c adımlarını yineleyin.  
  
3. Üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)] veya [!INCLUDE[lserver](../../../../includes/lserver-md.md)], şu adımları izleyin.  
  
    1. Tıklayın **bir programın Windows Güvenlik Duvarı üzerinden izin**.  
  
    2. Üzerinde **özel durumları** sekmesinde **bağlantı noktası Ekle**.  
  
    3. Bir ad girin, 8000 bağlantı noktası numarasını girin ve seçin **TCP** seçeneği.  
  
    4. Tıklayın **kapsamını Değiştir** düğmesini seçme **Ağ Bağlantılarım** (alt ağ) yalnızca seçeneğin seçeneğine tıklayıp **Tamam**.  
  
    5. Bağlantı noktaları için 8001, b ve d adımları yineleyin 8002, 8003, 9000, 80 ve 443.  
  
4. Tıklayın **Tamam** güvenlik duvarı uygulamasını kapatın.  
  
> [!NOTE]
>  Örnekleri ile işiniz bittiğinde, tüm güvenlik duvarı özel durumları kaldırın. Bunu yapmak için açık **Windows Güvenlik Duvarı'nı Denetim Masası'ndaki** uygulaması ve tüm programları kaldırın veya bağlantı noktası, önceki yordamlarda tarafından eklenen girdileri.
