---
title: 'Nasıl Yapılır: SSL Sertifikası ile Bir Bağlantı Noktasını Yapılandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SSL
- WCF, security mode
- WCF, security
ms.assetid: b8abcc8e-a5f5-4317-aca5-01e3c40ab24d
ms.openlocfilehash: 0a2ac22bfb5f84235d34a554df8cc1ad43ddc489
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2018
ms.locfileid: "49308447"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a>Nasıl Yapılır: SSL Sertifikası ile Bir Bağlantı Noktasını Yapılandırma
Şirket içinde barındırılan Windows Communication Foundation (WCF) hizmet ile oluşturulurken <xref:System.ServiceModel.WSHttpBinding> sınıfı bu kullanımları aktarım güvenliği, ayrıca bir X.509 sertifikası ile bir bağlantı noktası yapılandırmanız gerekir. Şirket içinde barındırılan bir hizmet oluşturmuyorsanız, hizmetinizi Internet Information Services (IIS) üzerinde barındırabilirsiniz. Daha fazla bilgi için [HTTP aktarım güvenliği](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
 Bir bağlantı noktasını yapılandırmak için kullandığınız araç makinenizde çalışan işletim sistemine bağlıdır.  
  
 Çalıştırıyorsanız [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] veya [!INCLUDE[wxp](../../../../includes/wxp-md.md)], HttpCfg.exe aracını kullanın. İle [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] bu aracı yüklenir. İle [!INCLUDE[wxp](../../../../includes/wxp-md.md)], aracı indirebileceğiniz [Windows XP Service Pack 2 Destek Araçları](https://go.microsoft.com/fwlink/?LinkId=88606). Daha fazla bilgi için [Httpcfg genel bakış](https://go.microsoft.com/fwlink/?LinkId=88605). [Windows Destek Araçları belgeleri](https://go.microsoft.com/fwlink/?LinkId=94840) Httpcfg.exe aracın sözdizimi açıklar.  
  
 Çalıştırıyorsanız [!INCLUDE[wv](../../../../includes/wv-md.md)], zaten yüklü Netsh.exe aracını kullanın.  
  
 Bu konuda çeşitli yordamları nasıl yapılacağını anlatmaktadır:  
  
-   Bir bilgisayarın geçerli bağlantı noktası yapılandırmasını belirleniyor.  
  
-   Bir sertifikanın parmak izi (aşağıdaki iki yordamdan için gerekli) alma.  
  
-   Bir bağlantı noktası yapılandırması için bir SSL sertifikası bağlama.  
  
-   Bir bağlantı noktası yapılandırması ve istemci sertifikalarını destekleyen bir SSL sertifikası bağlama.  
  
-   Bir bağlantı noktası numarasından bir SSL sertifikası siliniyor.  
  
 Bilgisayarda depolanan sertifikaları değiştirme yönetici ayrıcalıklarını gerektirdiğini unutmayın.  
  
### <a name="to-determine-how-ports-are-configured"></a>Bağlantı noktalarını nasıl yapılandırılacağını belirlemek için  
  
1.  İçinde [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] veya [!INCLUDE[wxp](../../../../includes/wxp-md.md)], HttpCfg.exe geçerli bağlantı noktası yapılandırmasını görüntülemek için aracını kullanarak **sorgu** ve **ssl** geçer, aşağıdaki örnekte gösterildiği gibi.  
  
    ```  
    httpcfg query ssl  
    ```  
  
2.  İçinde [!INCLUDE[wv](../../../../includes/wv-md.md)], aşağıdaki örnekte gösterildiği gibi geçerli bir bağlantı noktası yapılandırmasını görüntülemek için Netsh.exe aracını kullanın.  
  
    ```  
    netsh http show sslcert  
    ```  
  
### <a name="to-get-a-certificates-thumbprint"></a>Bir sertifikanın parmak izi almak için  
  
1.  İstemci kimlik doğrulaması amacı olan bir X.509 sertifikası bulunamıyor sertifikalar MMC ek bileşenini kullanın. Daha fazla bilgi için [nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüleme](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
2.  Sertifikanın parmak izi erişin. Daha fazla bilgi için [nasıl yapılır: bir sertifikanın parmak izini alma](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
3.  Sertifikanın parmak izini Not Defteri gibi bir metin düzenleyicisine kopyalayın.  
  
4.  Onaltılık karakterler arasındaki tüm boşlukları kaldırın. Bunu gerçekleştirmek için bir metin Düzenleyicisi'nin Bul ve Değiştir özelliğini kullanın ve her alanı null karakteri ile değiştirmek için yoludur.  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number"></a>Bir bağlantı noktası numarası için bir SSL sertifikası bağlamak için  
  
1.  İçinde [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] veya [!INCLUDE[wxp](../../../../includes/wxp-md.md)], sertifikayı bir bağlantı noktası numarasını bağlamak için "Ayarla" modunda Güvenli Yuva Katmanı (SSL) deposunda HttpCfg.exe Aracı'nı kullanın. Aracı parmak izi sertifika tanımlamak için aşağıdaki örnekte gösterildiği gibi kullanır.  
  
    ```  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    -   **-İ** anahtar söz dizimi olan `IP`:`port` ve bilgisayarın 8012 bağlantı için sertifika ayarlamak için araç bildirir. İsteğe bağlı olarak, sayı önünde dört sıfırları bilgisayarın gerçek IP adresine göre değiştirilebilir.  
  
    -   **-H** anahtar sertifikanın parmak izini belirtir.  
  
2.  İçinde [!INCLUDE[wv](../../../../includes/wv-md.md)], aşağıdaki örnekte gösterildiği gibi Netsh.exe aracını kullanın.  
  
    ```  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}   
    ```  
  
    -   **Certhash** parametresi, sertifikanın parmak izini belirtir.  
  
    -   **İpport** parametresi, IP adresi ve bağlantı noktasını belirtir ve işlevleri olduğu gibi **-i** açıklanan Httpcfg.exe Aracı'nın anahtarı.  
  
    -   **AppID** parametredir sahip olan uygulamayı tanımlamak için kullanılan bir GUID.  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a>Bir bağlantı noktası numarası için bir SSL sertifikası bağlama ve istemci sertifikalarını desteklemek için  
  
1.  İçinde [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] veya [!INCLUDE[wxp](../../../../includes/wxp-md.md)], aktarım katmanında X.509 sertifikalarıyla kimlik doğrulaması için yukarıdaki yordamı izleyin ancak aşağıdaki örnekte gösterildiği gibi bir ek komut satırı parametresi HttpCfg.exe için geçmesi istemcileri desteklemek için.  
  
    ```  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     **-F** anahtar söz dizimi olan `n` burada n, 1 ile 7 arasında bir sayı. Değeri 2 ' nin, istemci sertifikaları aktarım katmanında önceki örnekte gösterilen şekilde etkinleştirir. 3 değeri, istemci sertifikaları sağlar ve bu sertifikaları için bir Windows hesabı eşler. Diğer değerleri davranışı için HttpCfg.exe yardımına bakın.  
  
2.  İçinde [!INCLUDE[wv](../../../../includes/wv-md.md)], yukarıdaki yordamı izleyin, aktarım katmanında X.509 sertifikalarıyla kimlik doğrulaması istemcileri destekler, ancak aşağıdaki örnekte gösterildiği gibi ek bir parametre.  
  
    ```  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
### <a name="to-delete-an-ssl-certificate-from-a-port-number"></a>Bir bağlantı noktası numarasından bir SSL sertifikası silinemedi  
  
1.  Bilgisayarda tüm bağlamaları parmak izleriyle ve bağlantı noktalarını görmek için HttpCfg.exe veya Netsh.exe aracını kullanın. Disk bilgileri yazdırmak için yeniden yönlendirme karakter kullanın ">" aşağıdaki örnekte gösterildiği gibi.  
  
    ```  
    httpcfg query ssl>myMachinePorts.txt  
    ```  
  
2.  İçinde [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] veya [!INCLUDE[wxp](../../../../includes/wxp-md.md)], HttpCfg.exe aracını **Sil** ve **ssl** anahtar sözcükleri. Kullanım **-i** belirlemek için anahtarı `IP`:`port` numarası ve **-h** parmak izini belirlemek için anahtarı.  
  
    ```  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3.  İçinde [!INCLUDE[wv](../../../../includes/wv-md.md)], aşağıdaki örnekte gösterildiği gibi Netsh.exe aracını kullanın.  
  
    ```  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kodu kullanarak bir şirket içinde barındırılan hizmeti oluşturulacağını gösterir <xref:System.ServiceModel.WSHttpBinding> aktarım güvenliği kümesine sınıfı. Bir uygulama oluştururken, adres, bağlantı noktası numarasını belirtin.  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
* [HTTP Aktarım Güvenliği](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
