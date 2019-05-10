---
title: 'Azaltma: WCF hizmetleri ve sertifika kimlik doğrulaması'
ms.date: 03/30/2017
ms.assetid: ef19c91a-b9df-4bf0-a28e-eb1e99c4bc95
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5f94cabb482a237395854fcdc91df476c567069c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64599503"
---
# <a name="mitigation-wcf-services-and-certificate-authentication"></a>Azaltma: WCF hizmetleri ve sertifika kimlik doğrulaması
.NET Framework 4.6, TLS 1.1 ve TLS 1.2 WCF SSL protokolü varsayılan listeye ekler. İstemci ve sunucu makineler sahip .NET Framework 4.6 veya üzeri yüklü olduğunda, TLS 1.2 anlaşması için kullanılır.  
  
## <a name="impact"></a>Etki  
 TLS 1.2 MD5 sertifika kimlik doğrulamasını desteklemez. Bir MD5 karma algoritması kullanan bir SSL sertifikası kullanırsa, sonuç olarak, WCF istemcisini WCF hizmetine bağlanamıyor. Daha fazla bilgi için [azaltma: WCF hizmetleri ve sertifika kimlik doğrulaması](../../../docs/framework/migration-guide/mitigation-wcf-services-and-certificate-authentication.md).  
  
## <a name="mitigation"></a>Azaltma  
 Bir WCF istemcisi, aşağıdakilerden birini yaparak bir WCF sunucuya bağlanabilmesi için bu sorunu geçici olarak çalışabilir:  
  
- MD5 algoritmasını kullanmayı sertifikayı güncelleştirin. Önerilen çözüm budur.  
  
- Bağlama dinamik olarak kaynak kodunda yapılandırılmamışsa, TLS 1.1 veya önceki bir sürümünün protokolü kullanmak için uygulama yapılandırma dosyasını güncelleştirin. Bu, bir sertifika MD5 karma algoritması ile kullanmaya devam etmek sağlar.  
  
    > [!CAUTION]
    >  Bu geçici çözüm önerilmez, bu yana MD5 karma algoritması bir sertifikayla güvenli olarak kabul edilir.  
  
     Şu yapılandırma dosyasını şunu yapar:  
  
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
  
- Kaynak kodunda bağlama dinamik olarak yapılandırılmışsa, güncelleştirme <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> özelliğinin TLS 1.1 kullanmak için (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) veya önceki bir sürümünün kaynak kodundaki protokolü.  
  
    > [!CAUTION]
    >  Bu geçici çözüm önerilmez, bu yana MD5 karma algoritması bir sertifikayla güvenli olarak kabul edilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Değişiklikleri](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
