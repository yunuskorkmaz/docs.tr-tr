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
ms.openlocfilehash: 90d5424e12bb770dc3da85e1b2738206f4777c0c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185101"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a>Nasıl Yapılır: SSL Sertifikası ile Bir Bağlantı Noktasını Yapılandırma

Aktarım güvenliğini kullanan <xref:System.ServiceModel.WSHttpBinding> sınıfla birlikte kendi kendine barındırılan bir Windows Communication Foundation (WCF) hizmeti oluştururken, X.509 sertifikasına sahip bir bağlantı noktasını da yapılandırmanız gerekir. Kendi kendine barındırılan bir hizmet oluşturmuyorsanız, hizmetinizi Internet Bilgi Hizmetleri'nde (IIS) barındırabilirsiniz. Daha fazla bilgi için [HTTP Transport Security'ye](../../../../docs/framework/wcf/feature-details/http-transport-security.md)bakın.  
  
 Bir bağlantı noktasını yapılandırmak için, kullandığınız araç makinenizde çalışan işletim sistemine bağlıdır.  
  
 Windows Server 2003 çalıştırıyorsanız, HttpCfg.exe aracını kullanın. Windows Server 2003'te bu araç yüklenir. Daha fazla bilgi için [Bkz. Httpcfg Genel Bakış.](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10)) [Windows Destek Araçları belgeleri,](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10)) Httpcfg.exe aracının sözdizimini açıklar.  
  
 Windows Vista'yı çalıştırıyorsanız, zaten yüklü olan Netsh.exe aracını kullanın.
  
> [!NOTE]
> Bilgisayarda depolanan sertifikaları değiştirmek için yönetim ayrıcalıkları gerekiyor.  
  
## <a name="determine-how-ports-are-configured"></a>Bağlantı noktalarının nasıl yapılandırıldırıldığını belirleme  
  
1. Windows Server 2003 veya Windows XP'de, aşağıdaki örnekte gösterildiği gibi **sorgu** ve **ssl** anahtarlarını kullanarak geçerli bağlantı noktası yapılandırmasını görüntülemek için HttpCfg.exe aracını kullanın.  
  
    ```console
    httpcfg query ssl  
    ```  
  
2. Windows Vista'da, aşağıdaki örnekte gösterildiği gibi geçerli bağlantı noktası yapılandırmasını görüntülemek için Netsh.exe aracını kullanın.  
  
    ```console  
    netsh http show sslcert  
    ```  
  
## <a name="get-a-certificates-thumbprint"></a>Sertifikanın parmak izini alma  
  
1. İstemci kimlik doğrulaması amacı olan bir X.509 sertifikası bulmak için MMC sertifikalarını kullanın. Daha fazla bilgi için [bkz: MMC Snap-in ile Sertifikaları Görüntüleme](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
2. Sertifikanın parmak izine erişin. Daha fazla bilgi için bkz. [Nasıl yapılır: Bir Sertifikanın Parmak İzini Alma](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
3. Sertifikanın parmak izini Not Defteri gibi bir metin düzenleyicisine kopyalayın.  
  
4. Hexadecimal karakterler arasındaki tüm boşlukları kaldırın. Bunu başarmanın bir yolu, metin düzenleyicisinin bul-değiştir özelliğini kullanmak ve her alanı boş bir karakterle değiştirmektir.  
  
## <a name="bind-an-ssl-certificate-to-a-port-number"></a>SSL sertifikasını bağlantı noktası numarasına bağlama  
  
1. Windows Server 2003 veya Windows XP'de, sertifikayı bir bağlantı noktası numarasına bağlamak için Güvenli Soketler Katmanı'ndaki (SSL) "set" modundaki HttpCfg.exe aracını kullanın. Araç, aşağıdaki örnekte gösterildiği gibi sertifikayı tanımlamak için parmak izini kullanır.  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    - **-i** anahtarında `IP`sözdizimi`port` vardır: ve sertifikayı bilgisayarın 8012 portuna ayarlaması için araca talimat verir. İsteğe bağlı olarak, numaradan önce gelen dört sıfır bilgisayarın gerçek IP adresiyle de değiştirilebilir.  
  
    - **-h** anahtarı sertifikanın parmak izini belirtir.  
  
2. Windows Vista'da, aşağıdaki örnekte gösterildiği gibi Netsh.exe aracını kullanın.  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}
    ```  
  
    - **Certhash** parametresi sertifikanın parmak izini belirtir.  
  
    - **ipport** parametresi IP adresini ve bağlantı noktasını belirtir ve açıklanan Httpcfg.exe aracının **-i** anahtarı gibi işlevler.  
  
    - **Appid** parametresi, sahibi olan uygulamayı tanımlamak için kullanılabilecek bir GUID'dir.  
  
## <a name="bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a>SSL sertifikasını bağlantı noktası numarasına bağlama ve istemci sertifikalarını destekleme  
  
1. Windows Server 2003 veya Windows XP'de, aktarım katmanında X.509 sertifikalarıyla kimlik doğrulayan istemcileri desteklemek için, önceki yordamı izleyin, ancak aşağıdaki örnekte gösterildiği gibi httpCfg.exe'ye ek bir komut satırı parametresini geçirin.  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     **-f** anahtarı, n'nin `n` 1 ile 7 arasında bir sayı olduğu yerin sözdizimini vardır. Önceki örnekte gösterildiği gibi 2 değeri, aktarım katmanında istemci sertifikaları sağlar. 3 değeri istemci sertifikaları sağlar ve bu sertifikaları bir Windows hesabıyla eşler. Diğer değerlerin davranışı için HttpCfg.exe Yardım'a bakın.  
  
2. Windows Vista'da, aktarım katmanında X.509 sertifikalarıyla kimlik doğrulayan istemcileri desteklemek için, aşağıdaki örnekte gösterildiği gibi önceki yordamı izleyin, ancak ek bir parametreyle birlikte.  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
## <a name="delete-an-ssl-certificate-from-a-port-number"></a>Bir SSL sertifikasını bağlantı noktası numarasından silme  
  
1. Bilgisayardaki tüm bağlamaların bağlantı noktalarını ve parmak izlerini görmek için HttpCfg.exe veya Netsh.exe aracını kullanın. Bilgileri diske yazdırmak için aşağıdaki örnekte gösterildiği gibi ">" yeniden yönlendirme karakterini kullanın.  
  
    ```console  
    httpcfg query ssl>myMachinePorts.txt  
    ```
  
2. Windows Server 2003 veya Windows XP'de, **delete** ve **ssl** anahtar kelimeleriyle birlikte HttpCfg.exe aracını kullanın. **-i** anahtarını kullanarak `IP`:`port` sayıyı ve **-h** anahtarını işaret etmek için parmak izini belirtin.  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. Windows Vista'da, aşağıdaki örnekte gösterildiği gibi Netsh.exe aracını kullanın.  
  
    ```console  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod, güvenliği taşımak için sınıf kümesini kullanarak kendi kendine barındırılan bir hizmetin <xref:System.ServiceModel.WSHttpBinding> nasıl oluşturulurulur gösterir. Bir uygulama oluştururken, adresteki bağlantı noktası numarasını belirtin.  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [HTTP Aktarım Güvenliği](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
