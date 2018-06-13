---
title: 'Azaltma: WCF hizmetleri ve sertifika kimlik doğrulaması'
ms.date: 03/30/2017
ms.assetid: ef19c91a-b9df-4bf0-a28e-eb1e99c4bc95
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4f05dfab89fa5f811769687c467b2186745ecd5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33388943"
---
# <a name="mitigation-wcf-services-and-certificate-authentication"></a>Azaltma: WCF hizmetleri ve sertifika kimlik doğrulaması
.NET Framework 4.6 TLS 1.1 ve TLS 1.2 WCF SSL protokolü varsayılan listesine ekler. İstemci ve sunucu makinelerini .NET Framework 4.6 veya sonrası yüklü olduğunda, TLS 1.2 anlaşması için kullanılır.  
  
## <a name="impact"></a>Etki  
 TLS 1.2 MD5 sertifika kimlik doğrulamasını desteklemez. Bir müşteri MD5 karma algoritması kullanan bir SSL sertifikası kullanıyorsa, sonuç olarak, WCF istemcisini WCF hizmetine bağlanamıyor. Daha fazla bilgi için bkz: [azaltma: WCF hizmetleri ve sertifika kimlik doğrulaması](../../../docs/framework/migration-guide/mitigation-wcf-services-and-certificate-authentication.md).  
  
## <a name="mitigation"></a>Azaltma  
 Bir WCF istemcisi aşağıdakilerden birini yaparak bir WCF sunucuya bağlanabilmesi bu soruna geçici çözüm bulabilirsiniz:  
  
-   MD5 algoritması kullanmamayı sertifikayı güncelleştirin. Bu önerilen bir yöntemdir.  
  
-   Bağlama kaynak kodunu dinamik olarak yapılandırılmamışsa, TLS 1.1 veya protokolü önceki bir sürümünü kullanmak için uygulamanın yapılandırma dosyasını güncelleştirin. Bu, bir sertifika ile MD5 karma algoritması kullanmaya devam etmek sağlar.  
  
    > [!CAUTION]
    >  Bu geçici çözüm önerilmez, bu yana MD5 karma algoritmasını bir sertifikayla güvenli olarak değerlendirilir.  
  
     Aşağıdaki yapılandırma dosyası bu yapar:  
  
    ```xml  
    <configuration>  
        <system.serviceModel>  
            <bindings>  
                <netTcpBinding>  
                    <binding>  
                        <security mode= "None|Transport|Message|TransportWithMessageCredential" >  
                            <transport clientCredentialType="None|Windows|Certificate"  
                                                protectionLevel="None|Sign|EncryptAndSign"  
                                                sslProtocols="Ssl3|Tls1|Tls11">  
                            </transport>  
                        </security>  
                    </binding>  
                </netTcpBinding>  
            </bindings>  
        </system.ServiceModel>  
    </configuration>  
    ```  
  
-   Bağlama kaynak kodunu dinamik olarak yapılandırılmışsa, güncelleştirme <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> TLS 1.1 kullanmak için özelliği (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) veya kaynak kodu protokolünde önceki bir sürümü.  
  
    > [!CAUTION]
    >  Bu geçici çözüm önerilmez, bu yana MD5 karma algoritmasını bir sertifikayla güvenli olarak değerlendirilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Değişiklikleri](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
