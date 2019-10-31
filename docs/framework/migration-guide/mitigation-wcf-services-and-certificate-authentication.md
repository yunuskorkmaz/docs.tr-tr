---
title: 'Risk azaltma: WCF Hizmetleri ve sertifika kimlik doğrulaması'
ms.date: 03/30/2017
ms.assetid: ef19c91a-b9df-4bf0-a28e-eb1e99c4bc95
ms.openlocfilehash: cc8afaf0592a26f7bab15ab94b04ba4a9bfac930
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126126"
---
# <a name="mitigation-wcf-services-and-certificate-authentication"></a>Risk azaltma: WCF Hizmetleri ve sertifika kimlik doğrulaması

4,6 .NET Framework, WCF SSL protokolü varsayılan listesine TLS 1,1 ve TLS 1,2 ekler. Hem istemci hem de sunucu makinelerinin .NET Framework 4,6 veya üzeri bir sürümü yüklüyse, anlaşma için TLS 1,2 kullanılır.

## <a name="impact"></a>Etki

TLS 1,2, MD5 sertifikası kimlik doğrulamasını desteklemez. Sonuç olarak, bir müşteri karma algoritma için MD5 kullanan bir SSL sertifikası kullanıyorsa, WCF istemcisi WCF hizmetine bağlanamaz. Daha fazla bilgi için bkz. [azaltma: WCF Hizmetleri ve sertifika kimlik doğrulaması](mitigation-wcf-services-and-certificate-authentication.md).

## <a name="mitigation"></a>Azaltma

Bir WCF istemcisinin aşağıdakilerden birini yaparak bir WCF sunucusuna bağlanabilmesi için bu soruna geçici bir çözüm bulabilirsiniz:

- Bu sertifikayı, MD5 algoritmasını kullanacak şekilde güncelleştirin. Önerilen çözüm budur.

- Bağlama kaynak kodunda dinamik olarak yapılandırılmamışsa, uygulamanın yapılandırma dosyasını TLS 1,1 veya protokolün önceki bir sürümünü kullanacak şekilde güncelleştirin. Bu, MD5 karma algoritmasıyla bir sertifika kullanmaya devam etmenizi sağlar.

  > [!CAUTION]
  > Bu geçici çözüm önerilmez, çünkü MD5 karma algoritması olan bir sertifika güvenli değil olarak kabul edilir.

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

- Bağlama, kaynak kodunda dinamik olarak yapılandırılırsa, <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> özelliğini, kaynak koddaki TLS 1,1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) veya protokolün önceki bir sürümünü kullanacak şekilde güncelleştirin.

  > [!CAUTION]
  > Bu geçici çözüm önerilmez, çünkü MD5 karma algoritması olan bir sertifika güvenli değil olarak kabul edilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Değişiklikleri](runtime-changes-in-the-net-framework-4-6.md)
