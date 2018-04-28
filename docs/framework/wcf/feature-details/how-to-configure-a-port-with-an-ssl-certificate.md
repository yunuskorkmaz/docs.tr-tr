---
title: 'Nasıl Yapılır: SSL Sertifikası ile Bir Bağlantı Noktasını Yapılandırma'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SSL
- WCF, security mode
- WCF, security
ms.assetid: b8abcc8e-a5f5-4317-aca5-01e3c40ab24d
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bbf3d4b9888d07a89d1b6a8225a7f7415e8c67cc
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a>Nasıl Yapılır: SSL Sertifikası ile Bir Bağlantı Noktasını Yapılandırma
Kendini barındıran oluştururken [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmeti ile <xref:System.ServiceModel.WSHttpBinding> bu kullanımları taşıma güvenliği sınıfı, bir bağlantı noktası bir X.509 sertifikası ile yapılandırmanız da gerekir. Kendini barındıran hizmet oluşturuyorsanız değil, hizmetiniz Internet Information Services (IIS) üzerinde barındırabilir. Daha fazla bilgi için bkz: [HTTP taşıma güvenliği](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
 Bir bağlantı noktasını yapılandırmak için kullandığınız araç, makinede çalışan işletim sistemine bağlıdır.  
  
 Çalıştırıyorsanız, [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] veya [!INCLUDE[wxp](../../../../includes/wxp-md.md)], HttpCfg.exe aracını kullanın. İle [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] bu aracı yüklenir. İle [!INCLUDE[wxp](../../../../includes/wxp-md.md)], aracı indirebilirsiniz [Windows XP Service Pack 2 Destek Araçları](http://go.microsoft.com/fwlink/?LinkId=88606). Daha fazla bilgi için bkz: [Httpcfg genel bakış](http://go.microsoft.com/fwlink/?LinkId=88605). [Windows Destek Araçları belgeleri](http://go.microsoft.com/fwlink/?LinkId=94840) Httpcfg.exe araç söz dizimi açıklanmıştır.  
  
 Çalıştırıyorsanız, [!INCLUDE[wv](../../../../includes/wv-md.md)], zaten yüklüyse Netsh.exe aracını kullanın.  
  
 Bu konuda, birkaç yordamları gerçekleştirmek açıklar:  
  
-   Bir bilgisayarın geçerli bağlantı noktası yapılandırmasını belirleme.  
  
-   Bir sertifikanın parmak izi (aşağıdaki iki yordamdan için gerekli) alma.  
  
-   Bir SSL sertifikası bir bağlantı noktası yapılandırmasını bağlama.  
  
-   Bir bağlantı noktası yapılandırması için bir SSL sertifikası bağlama ve istemci sertifikalarını destekleyen.  
  
-   Bir SSL sertifikası bir bağlantı noktası numarasından siliniyor.  
  
 Bilgisayarda depolanan sertifikalar değiştirme yönetici ayrıcalıkları gerektirir.  
  
### <a name="to-determine-how-ports-are-configured"></a>Bağlantı noktaları nasıl yapılandırılır belirlemek için  
  
1.  İçinde [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] veya [!INCLUDE[wxp](../../../../includes/wxp-md.md)], HttpCfg.exe geçerli bağlantı noktası yapılandırmasını görüntülemek için aracını kullanarak **sorgu** ve **ssl** , aşağıdaki örnekte gösterildiği gibi geçer.  
  
    ```  
    httpcfg query ssl  
    ```  
  
2.  İçinde [!INCLUDE[wv](../../../../includes/wv-md.md)], aşağıdaki örnekte gösterildiği gibi geçerli bağlantı noktası yapılandırmasını görüntülemek için Netsh.exe aracını kullanın.  
  
    ```  
    netsh http show sslcert  
    ```  
  
### <a name="to-get-a-certificates-thumbprint"></a>Bir sertifikanın parmak izi almak için  
  
1.  İstemci kimlik doğrulaması amacı olan bir X.509 sertifikası bulmak için sertifikalar MMC ek bileşenini kullanın. Daha fazla bilgi için bkz: [nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüleme](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
2.  Sertifikanın parmak izi erişin. Daha fazla bilgi için bkz: [nasıl yapılır: bir sertifikanın parmak izini alma](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
3.  Sertifikanın parmak izini Not Defteri gibi bir metin düzenleyicisine kopyalayın.  
  
4.  Onaltılık karakterler arasındaki tüm boşlukları kaldırın. Bunu gerçekleştirmek için bir metin Düzenleyicisi'nin Bul ve Değiştir özelliğini kullanın ve her alan bir null karakter ile değiştirmek için yoludur.  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number"></a>Bir SSL sertifikası bir bağlantı noktası numarası bağlamak için  
  
1.  İçinde [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] veya [!INCLUDE[wxp](../../../../includes/wxp-md.md)], sertifikayı bir bağlantı noktası numarası bağlamak için Güvenli Yuva Katmanı (SSL) deposunda "Ayarla" modunda HttpCfg.exe aracını kullanın. Aracı parmak izi sertifika tanımlamak için aşağıdaki örnekte gösterildiği gibi kullanır.  
  
    ```  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    -   **-İ** anahtar sahip sözdizimi `IP`:`port` ve bilgisayarın 8012 bağlantı noktasına sertifika ayarlamak için aracı bildirir. İsteğe bağlı olarak, numarasını koyun dört sıfır bilgisayarın gerçek IP adresine göre değiştirilebilir.  
  
    -   **-H** anahtar sertifikanın parmak izi belirtir.  
  
2.  İçinde [!INCLUDE[wv](../../../../includes/wv-md.md)], aşağıdaki örnekte gösterildiği gibi Netsh.exe aracını kullanın.  
  
    ```  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}   
    ```  
  
    -   **Certhash** parametresi, sertifikanın parmak izi belirtir.  
  
    -   **İpport** parametresi, IP adresi ve bağlantı noktasını belirtir ve işlevleri olduğu gibi **-i** açıklanan Httpcfg.exe Aracı'nın anahtarı.  
  
    -   **AppID** parametredir sahibi olan uygulama tanımlamak için kullanılan bir GUID.  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a>Bir bağlantı noktası numarası için bir SSL sertifikası bağlama ve istemci sertifikalarını desteklemek için  
  
1.  İçinde [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] veya [!INCLUDE[wxp](../../../../includes/wxp-md.md)], aktarım katmanında X.509 sertifikaları, kimlik doğrulaması, yukarıdaki yordamı izleyin, ancak bir ek komut satırı parametresi HttpCfg.exe için aşağıdaki örnekte gösterildiği gibi geçirmek istemcileri desteklemek için.  
  
    ```  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     **-F** anahtar sahip sözdizimi `n` n, 1 ile 7 arasında bir sayı. 2 ' değeri önceki örnekte gösterildiği gibi aktarım katmanında istemci sertifikalarını etkinleştirir. 3 değerini istemci sertifikalarını sağlar ve bu sertifikaları bir Windows hesabı eşler. Diğer değerlerin davranışını HttpCfg.exe yardımına bakın.  
  
2.  İçinde [!INCLUDE[wv](../../../../includes/wv-md.md)], aktarım katmanında X.509 sertifikaları, kimlik doğrulaması, yukarıdaki yordamı izleyin istemcileri destekler, ancak aşağıdaki örnekte gösterildiği gibi ek bir parametre.  
  
    ```  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
### <a name="to-delete-an-ssl-certificate-from-a-port-number"></a>Bir SSL sertifikası bir bağlantı noktası numarasından silmek için  
  
1.  Bağlantı noktalarını ve tüm bağlamaları parmak izlerini bilgisayarda görmek için HttpCfg.exe veya Netsh.exe aracını kullanın. Disk bilgilerini yazdırmak için yeniden yönlendirme karakteri kullanın ">" aşağıdaki örnekte gösterildiği gibi.  
  
    ```  
    httpcfg query ssl>myMachinePorts.txt  
    ```  
  
2.  İçinde [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] veya [!INCLUDE[wxp](../../../../includes/wxp-md.md)], HttpCfg.exe aracıyla kullanın **silmek** ve **ssl** anahtar sözcükler. Kullanım **-i** belirlemek için anahtarı `IP`:`port` numarası ve **-h** parmak izini belirlemek için anahtarı.  
  
    ```  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3.  İçinde [!INCLUDE[wv](../../../../includes/wv-md.md)], aşağıdaki örnekte gösterildiği gibi Netsh.exe aracını kullanın.  
  
    ```  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kodu kullanarak kendini barındıran hizmet oluşturma gösterilmektedir <xref:System.ServiceModel.WSHttpBinding> sınıf taşıma güvenliği olarak ayarlanmış. Bir uygulama oluştururken, bağlantı noktası numarasını adresi belirtin.  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [HTTP Aktarım Güvenliği](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
