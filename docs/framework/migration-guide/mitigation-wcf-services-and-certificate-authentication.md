---
title: Mayı WCF Hizmetleri ve sertifika kimlik doğrulaması
ms.date: 03/30/2017
ms.assetid: ef19c91a-b9df-4bf0-a28e-eb1e99c4bc95
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0fcb4de714c8a0f1f2c61f3a12815a5a0a3ddc83
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70789814"
---
# <a name="mitigation-wcf-services-and-certificate-authentication"></a>Mayı WCF Hizmetleri ve sertifika kimlik doğrulaması

4,6 .NET Framework, WCF SSL protokolü varsayılan listesine TLS 1,1 ve TLS 1,2 ekler. Hem istemci hem de sunucu makinelerinin .NET Framework 4,6 veya üzeri bir sürümü yüklüyse, anlaşma için TLS 1,2 kullanılır.

## <a name="impact"></a>Etki

TLS 1,2, MD5 sertifikası kimlik doğrulamasını desteklemez. Sonuç olarak, bir müşteri karma algoritma için MD5 kullanan bir SSL sertifikası kullanıyorsa, WCF istemcisi WCF hizmetine bağlanamaz. Daha fazla bilgi için bkz [. azaltma: WCF Hizmetleri ve sertifika kimlik](mitigation-wcf-services-and-certificate-authentication.md)doğrulaması.

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
      </system.ServiceModel>
  </configuration>
  ```

- Bağlama, kaynak kodunda dinamik olarak yapılandırılırsa, <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> özelliği, kaynak kodundaki TLS 1,1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) veya protokolün önceki bir sürümünü kullanacak şekilde güncelleştirin.

  > [!CAUTION]
  > Bu geçici çözüm önerilmez, çünkü MD5 karma algoritması olan bir sertifika güvenli değil olarak kabul edilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Değişiklikleri](runtime-changes-in-the-net-framework-4-6.md)
