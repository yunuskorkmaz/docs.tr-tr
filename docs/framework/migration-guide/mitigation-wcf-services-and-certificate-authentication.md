---
title: 'Azaltma: WCF Hizmetleri ve Sertifika Kimlik Doğrulaması'
ms.date: 03/30/2017
ms.assetid: ef19c91a-b9df-4bf0-a28e-eb1e99c4bc95
ms.openlocfilehash: 8c8493efa2c3223809ad87e01e3faddaea859ca8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457799"
---
# <a name="mitigation-wcf-services-and-certificate-authentication"></a>Azaltma: WCF Hizmetleri ve Sertifika Kimlik Doğrulaması

.NET Framework 4.6, WCF SSL protokolü varsayılan listesine 1,1 TLve TLS 1.2 ekler. Hem istemci hem de sunucu makineleri .NET Framework 4.6 veya daha sonra yüklü olduğunda, TLS 1.2 anlaşma için kullanılır.

## <a name="impact"></a>Etki

TLS 1.2, MD5 sertifika kimlik doğrulamasını desteklemez. Sonuç olarak, bir müşteri karma algoritması için MD5 kullanan bir SSL sertifikası kullanırsa, WCF istemcisi WCF hizmetine bağlanmayı başaramaz. Daha fazla bilgi için [bkz: Azaltma: WCF Hizmetleri ve Sertifika Kimlik Doğrulaması.](mitigation-wcf-services-and-certificate-authentication.md)

## <a name="mitigation"></a>Risk azaltma

WCF istemcisinin aşağıdakilerden herhangi birini yaparak bir WCF sunucusuna bağlanabilmesi için bu sorunu çözebilirsiniz:

- MD5 algoritmasını kullanmamak için sertifikayı güncelleştirin. Bu önerilen çözümdür.

- Bağlama kaynak kodunda dinamik olarak yapılandırılmamışsa, TLS 1.1 veya protokolün önceki bir sürümünü kullanacak şekilde uygulamanın yapılandırma dosyasını güncelleştirin. Bu, MD5 karma algoritması ile bir sertifika kullanmaya devam etmenizi sağlar.

  > [!CAUTION]
  > MD5 karma algoritması olan bir sertifika güvenli olarak kabul edilir, bu geçici çözüm önerilmez.

  Aşağıdaki yapılandırma dosyası bunu yapar:

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
      </system.serviceModel>
  </configuration>
  ```

- Bağlama kaynak kodunda dinamik olarak yapılandırılırsa, <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> tls 1.1<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>() veya kaynak kodundaki protokolün önceki bir sürümünü kullanacak şekilde özelliği güncelleştirin.

  > [!CAUTION]
  > MD5 karma algoritması olan bir sertifika güvenli olarak kabul edilir, bu geçici çözüm önerilmez.

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)
