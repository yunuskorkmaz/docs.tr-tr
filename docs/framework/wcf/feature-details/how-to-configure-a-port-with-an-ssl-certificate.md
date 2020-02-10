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
ms.openlocfilehash: 99a08c9714e8f8cef0c1c96ac7f890d163324b44
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095027"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a>Nasıl Yapılır: SSL Sertifikası ile Bir Bağlantı Noktasını Yapılandırma

Aktarım güvenliği kullanan <xref:System.ServiceModel.WSHttpBinding> sınıfıyla şirket içinde barındırılan bir Windows Communication Foundation (WCF) hizmeti oluştururken, bir X. 509.440 sertifikası ile bir bağlantı noktası da yapılandırmanız gerekir. Kendi kendine barındırılan bir hizmet oluşturmadıysanız, hizmetinizi Internet Information Services (IIS) üzerinde barındırabilirsiniz. Daha fazla bilgi için bkz. [http aktarım güvenliği](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
 Bir bağlantı noktasını yapılandırmak için, kullandığınız araç makinenizde çalışan işletim sistemine bağlıdır.  
  
 Windows Server 2003 çalıştırıyorsanız, HttpCfg. exe aracını kullanın. Windows Server 2003 ' de bu araç yüklüdür. Daha fazla bilgi için bkz. [Httpcfg Overview](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10)). [Windows Destek Araçları belgeleri](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10)) , Httpcfg. exe aracının sözdizimini açıklar.  
  
 Windows Vista çalıştırıyorsanız, zaten yüklü olan Netsh. exe aracını kullanın. 
  
> [!NOTE]
> Bilgisayarda depolanan sertifikaların değiştirilmesi için yönetici ayrıcalıkları gerekir.  
  
## <a name="determine-how-ports-are-configured"></a>Bağlantı noktalarının nasıl yapılandırıldığını belirleme  
  
1. Windows Server 2003 veya Windows XP 'de, aşağıdaki örnekte gösterildiği gibi, **sorgu** ve **SSL** anahtarlarını kullanarak geçerli bağlantı noktası yapılandırmasını görüntülemek için Httpcfg. exe aracını kullanın.  
  
    ```console
    httpcfg query ssl  
    ```  
  
2. Windows Vista 'da, aşağıdaki örnekte gösterildiği gibi geçerli bağlantı noktası yapılandırmasını görüntülemek için Netsh. exe aracını kullanın.  
  
    ```console  
    netsh http show sslcert  
    ```  
  
## <a name="get-a-certificates-thumbprint"></a>Bir sertifikanın parmak izini al  
  
1. İstemci kimlik doğrulamasının amaçlanan amacını içeren bir X. 509.440 sertifikası bulmak için Sertifikalar MMC ek bileşenini kullanın. Daha fazla bilgi için bkz. [nasıl yapılır: MMC ek bileşeni Ile sertifikaları görüntüleme](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
2. Sertifikanın parmak izine erişin. Daha fazla bilgi için bkz. [Nasıl yapılır: Bir Sertifikanın Parmak İzini Alma](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
3. Sertifikanın parmak izini Not Defteri gibi bir metin düzenleyicisine kopyalayın.  
  
4. Onaltılık karakterler arasındaki tüm boşlukları kaldırın. Bunu gerçekleştirmenin bir yolu metin düzenleyicisinin Bul ve Değiştir özelliğini kullanmaktır ve her bir boşluğu null karakterle değiştirir.  
  
## <a name="bind-an-ssl-certificate-to-a-port-number"></a>Bir bağlantı noktası numarasına SSL sertifikası bağlama  
  
1. Windows Server 2003 veya Windows XP 'de, sertifikayı bir bağlantı noktası numarasına bağlamak için Güvenli Yuva Katmanı (SSL) deposundaki "küme" modunda HttpCfg. exe aracını kullanın. Araç, aşağıdaki örnekte gösterildiği gibi sertifikayı tanımlamak için parmak izini kullanır.  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    - **-I** anahtarı `IP`:`port` sözdizimine sahiptir ve aracı sertifikayı bilgisayarın 8012 numaralı bağlantı noktasına ayarlamaya yönlendirir. İsteğe bağlı olarak, sayının önündeki dört sıfırda bilgisayarın gerçek IP adresi ile değiştirilebilir.  
  
    - **-H** anahtarı, sertifikanın parmak izini belirtir.  
  
2. Windows Vista 'da, aşağıdaki örnekte gösterildiği gibi Netsh. exe aracını kullanın.  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}   
    ```  
  
    - **Sunucunuzda certhash** parametresi, sertifikanın parmak izini belirtir.  
  
    - **Ipport** PARAMETRESI, IP adresini ve bağlantı noktasını ve yalnızca ' i r. exe aracının **-ı** anahtarı gibi işlevleri belirtir.  
  
    - **AppID** parametresi, sahip olan uygulamayı tanımlamak için KULLANıLABILEN bir GUID 'dir.  
  
## <a name="bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a>Bir bağlantı noktası numarasına SSL sertifikası bağlama ve istemci sertifikalarını destekleme  
  
1. Windows Server 2003 veya Windows XP 'de, aktarım katmanında X. 509.440 sertifikalarıyla kimlik doğrulayan istemcileri desteklemek için, önceki yordamı izleyin, ancak aşağıdaki örnekte gösterildiği gibi, HttpCfg. exe ' ye ek bir komut satırı parametresi geçirin.  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     **-F** anahtarının, 1 ile 7 arasında bir sayı olduğu `n` söz dizimi vardır. 2 değeri, yukarıdaki örnekte gösterildiği gibi, aktarım katmanında istemci sertifikalarına izin vermez. 3 değeri, istemci sertifikalarını sağlar ve bu sertifikaları bir Windows hesabıyla eşleştirir. Diğer değerlerin davranışı için bkz. HttpCfg. exe yardımı.  
  
2. Windows Vista 'da, aktarım katmanında X. 509.440 sertifikalarıyla kimlik doğrulayan istemcileri desteklemek için, aşağıdaki örnekte gösterildiği gibi önceki yordamı, ek bir parametre ile izleyin.  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
## <a name="delete-an-ssl-certificate-from-a-port-number"></a>Bir bağlantı noktası numarasından SSL sertifikası silme  
  
1. Bilgisayardaki tüm bağlamaların bağlantı noktalarını ve parmak izlerini görmek için HttpCfg. exe veya Netsh. exe aracını kullanın. Bilgileri diske yazdırmak için aşağıdaki örnekte gösterildiği gibi ">" yeniden yönlendirme karakterini kullanın.  
  
    ```console  
    httpcfg query ssl>myMachinePorts.txt  
    ```
  
2. Windows Server 2003 veya Windows XP 'de, **Delete** ve **SSL** anahtar sözcükleriyle Httpcfg. exe aracını kullanın. Parmak izini belirtmek için `IP`:`port` Number ve **-h** anahtarını belirtmek için **-ı** anahtarını kullanın.  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. Windows Vista 'da, aşağıdaki örnekte gösterildiği gibi Netsh. exe aracını kullanın.  
  
    ```console  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod, aktarım güvenliği için ayarlanan <xref:System.ServiceModel.WSHttpBinding> sınıfı kullanılarak şirket içinde barındırılan bir hizmetin nasıl oluşturulacağını gösterir. Bir uygulama oluştururken, adreste bağlantı noktası numarasını belirtin.  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [HTTP Aktarım Güvenliği](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
