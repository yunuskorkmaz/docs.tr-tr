---
title: "Güvenlik Duvarı Yönergeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7dc429f-65ac-4faf-974a-77d5fb977fe1
caps.latest.revision: "32"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 38d1f0f6bf9245048f21bbe1cb0aa6a0b8d768dd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="firewall-instructions"></a>Güvenlik Duvarı Yönergeleri
Birkaç bağlantı noktalarını etkinleştirmeniz gerekir ya da Güvenlik Duvarı'nda böylece programları [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] örnekleri işlev görebilir. Birçok örnekleri 8000-8003 aralığında bağlantı noktasını kullanarak iletişim kurmak ve 9000 bağlantı noktası. Güvenlik Duvarı varsayılan olarak açıktır ve bu bağlantı noktalarına erişimi engeller. Örnekler için Güvenlik Duvarı'nı etkinleştirmek için gereksinimler ve güvenlik ortamı bağlı olarak aşağıdaki yordamlardan birini tamamlayın:  
  
-   Seçenek 1: Etkileşimli olarak çalıştırırken örnekleri etkinleştirin. Güvenlik duvarı yapılandırmanızı hiçbir öncelikli değişiklik ve oluşturma ve çalıştırma örnekleri başlatmak için devam edin. Bir örneği çalıştırdığınızda, bir **Windows Güvenlik Uyarısı** iletişim kutusu görüntülenir. Örnek program söz konusu ardından etkileşimli olarak engeli listesine eklenebilir. Bu yordamı kullanarak, örnek yeniden başlatmanız gerekebilir.  
  
-   Seçenek 2: örnek programlar önceden etkinleştirin. Başlat **Windows Güvenlik Duvarı'nı Denetim Masası** uygulamasını ve örnek programları çalıştırmak için plan etkinleştir. Yürütülebilir dosyalar mevcut şekilde programları önce oluşturmanız gerekir. Aşağıdaki yordamda daha ayrıntılı yönergeler bulabilirsiniz.  
  
-   Seçenek 3: önceden bir bağlantı noktası aralığını etkinleştirin. Başlat **Windows Güvenlik Duvarı** **Denetim Masası** uygulaması ve Etkinleştir bağlantı noktası 80, 443, 8000 8003 ve örnekleri tarafından kullanılan 9000. Aşağıdaki yordamda daha ayrıntılı yönergeler bulabilirsiniz. Bu bağlantı noktaları, yalnızca örnekleri kullanmak herhangi bir programı sağladığından bu diğerlerinden daha az güvenli bir seçenektir.  
  
 Hangi yordamın emin değilseniz, ilk seçeneği belirleyin. Başka bir satıcıdan bir güvenlik duvarı çalıştırıyorsanız, benzer değişiklikler yapmanız gerekebilir.  
  
> [!IMPORTANT]
>  Güvenlik duvarı yapılandırmanızı değiştirme güvenlik etkiler. Değişiklikleri yapın ve örnekleri ile işiniz bittiğinde bunları kaldırın kayıt önerilir.  
  
### <a name="to-enable-samples-programs-in-advance"></a>Örnekleri programları önceden etkinleştirmek için  
  
1.  Örnek oluşturun.  
  
2.  Tıklatın **Başlat**, tıklatın **çalıştırmak**ve türü `firewall.cpl`. Bu açılır **Windows Güvenlik Duvarı'nı Denetim Masası** uygulaması.  
  
    > [!NOTE]
    >  Windows Güvenlik Duvarı üzerinden iletişim kurmasına olanak gerektiren örnekleri çalıştırmak için Güvenlik Duvarı ayarlarını değiştirme izniniz olmalıdır. Bazı güvenlik duvarı ayarları kullanılamıyorsa ve bilgisayarınız bir etki alanına bağlıysa, sistem yöneticiniz bu ayarları Grup İlkesi aracılığıyla denetliyor olabilir.  
  
3.  Bir program Windows Güvenlik Duvarı aracılığıyla izin vermek için aşağıdaki işletim belirli adımları tamamlayın:  
  
    -   Windows 7 veya Windows Server 2008 r2 üzerinde tıklatın **bir programı veya özelliği Windows Güvenlik Duvarı aracılığıyla izin**. Tıklatın **Ayarları Değiştir**, izin **başka bir Program...** .  
  
    -   Üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)] veya [!INCLUDE[lserver](../../../../includes/lserver-md.md)], tıklatın **bir program Windows Güvenlik Duvarı aracılığıyla izin**.  
  
4.  Üzerinde **özel durumları** sekmesini tıklatın, **Program Ekle**.  
  
5.  Tıklatın **Gözat** düğmesini tıklatın ve çalıştırmayı düşündüğünüz örnek yürütülebilir dosya seçin.  
  
6.  Yürütülebilir dosyalar çalıştırmayı planladığınız tüm örnekleri ekleyene kadar 4 ve 5. adımları yineleyin.  
  
7.  Tıklatın **Tamam** güvenlik duvarı uygulamasını kapatın.  
  
### <a name="to-enable-a-port-range-in-advance"></a>Bir bağlantı noktası aralığı önceden etkinleştirmek için  
  
1.  Tıklatın **Başlat**, tıklatın **çalıştırmak**ve türü `firewall.cpl`. Bu açılır **Windows Güvenlik Duvarı'nı Denetim Masası** uygulaması.  
  
2.  Windows 7 veya Windows Server 2008 R2, aşağıdaki adımları izleyin.  
  
    1.  Tıklatın **Gelişmiş ayarları** Windows Güvenlik Duvarı penceresinin sol sütunda.  
  
    2.  Tıklatın **gelen kuralları** sol sütunda.  
  
    3.  Tıklatın **yeni kurallar** sağ sütundaki.  
  
    4.  Seçin **bağlantı noktası** tıklatıp **sonraki**.  
  
    5.  Seçin **TCP** ve girin `8000, 8001, 8002, 8003, 9000, 80, 443` içinde **belirli yerel bağlantı noktaları** alan.  
  
    6.  
              **İleri**'ye tıklayın.  
  
    7.  Seçin **bağlantıya izin**, tıklatıp **sonraki** .  
  
    8.  Seçin **etki alanı** ve **özel**, tıklatıp **sonraki**.  
  
    9. Bu kural adı `WCF-WF 4.0 Samples`, tıklatıp **son**.  
  
    10. Tıklatın **giden kuralları** ve h c adımlarını yineleyin.  
  
3.  Üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)] veya [!INCLUDE[lserver](../../../../includes/lserver-md.md)], şu adımları izleyin.  
  
    1.  Tıklatın **bir program Windows Güvenlik Duvarı aracılığıyla izin**.  
  
    2.  Üzerinde **özel durumları** sekmesini tıklatın, **bağlantı noktası Ekle**.  
  
    3.  Bir ad girin, 8000 de bağlantı noktası numarası girin ve seçin **TCP** seçeneği.  
  
    4.  Tıklatın **Kapsamı Değiştir** düğmesi, select **Ağ Bağlantılarım** (alt ağ) tek seçenek ve tıklatın **Tamam**.  
  
    5.  İçin bağlantı noktalarını 8001, d b adımları yineleyin 8002, 8003, 9000, 80 ve 443.  
  
4.  Tıklatın **Tamam** güvenlik duvarı uygulamasını kapatın.  
  
> [!NOTE]
>  Örneklerle çalışma bittiğinde tüm güvenlik duvarı özel durumları kaldırın. Bunu yapmak için açık **Windows Güvenlik Duvarı'nı Denetim Masası** uygulaması ve tüm programları kaldırın veya bağlantı noktası, önceki yordamları tarafından eklenen girdileri.
