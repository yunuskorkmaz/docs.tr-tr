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
# <a name="mitigation-wcf-services-and-certificate-authentication"></a><span data-ttu-id="ccc27-102">Mayı WCF Hizmetleri ve sertifika kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="ccc27-102">Mitigation: WCF Services and Certificate Authentication</span></span>

<span data-ttu-id="ccc27-103">4,6 .NET Framework, WCF SSL protokolü varsayılan listesine TLS 1,1 ve TLS 1,2 ekler.</span><span class="sxs-lookup"><span data-stu-id="ccc27-103">The .NET Framework 4.6 adds TLS 1.1 and TLS 1.2 to the WCF SSL protocol default list.</span></span> <span data-ttu-id="ccc27-104">Hem istemci hem de sunucu makinelerinin .NET Framework 4,6 veya üzeri bir sürümü yüklüyse, anlaşma için TLS 1,2 kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ccc27-104">When both client and server machines have  the .NET Framework 4.6 or later installed, TLS 1.2 is used for negotiation.</span></span>

## <a name="impact"></a><span data-ttu-id="ccc27-105">Etki</span><span class="sxs-lookup"><span data-stu-id="ccc27-105">Impact</span></span>

<span data-ttu-id="ccc27-106">TLS 1,2, MD5 sertifikası kimlik doğrulamasını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="ccc27-106">TLS 1.2 does not support MD5 certificate authentication.</span></span> <span data-ttu-id="ccc27-107">Sonuç olarak, bir müşteri karma algoritma için MD5 kullanan bir SSL sertifikası kullanıyorsa, WCF istemcisi WCF hizmetine bağlanamaz.</span><span class="sxs-lookup"><span data-stu-id="ccc27-107">As a result, if a customer uses an SSL  certificate which uses MD5 for the hash algorithm, the WCF client fails to connect to the WCF service.</span></span> <span data-ttu-id="ccc27-108">Daha fazla bilgi için bkz [. azaltma: WCF Hizmetleri ve sertifika kimlik](mitigation-wcf-services-and-certificate-authentication.md)doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="ccc27-108">For more information, see [Mitigation: WCF Services and Certificate Authentication](mitigation-wcf-services-and-certificate-authentication.md).</span></span>

## <a name="mitigation"></a><span data-ttu-id="ccc27-109">Azaltma</span><span class="sxs-lookup"><span data-stu-id="ccc27-109">Mitigation</span></span>

<span data-ttu-id="ccc27-110">Bir WCF istemcisinin aşağıdakilerden birini yaparak bir WCF sunucusuna bağlanabilmesi için bu soruna geçici bir çözüm bulabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ccc27-110">You can work around this issue so that a WCF client can connect to a WCF server by doing any of the following:</span></span>

- <span data-ttu-id="ccc27-111">Bu sertifikayı, MD5 algoritmasını kullanacak şekilde güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="ccc27-111">Update the certificate to not use the MD5 algorithm.</span></span> <span data-ttu-id="ccc27-112">Önerilen çözüm budur.</span><span class="sxs-lookup"><span data-stu-id="ccc27-112">This is the recommended solution.</span></span>

- <span data-ttu-id="ccc27-113">Bağlama kaynak kodunda dinamik olarak yapılandırılmamışsa, uygulamanın yapılandırma dosyasını TLS 1,1 veya protokolün önceki bir sürümünü kullanacak şekilde güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="ccc27-113">If the binding is not dynamically configured in source code, update the application's configuration file to use TLS 1.1 or an earlier version of the protocol.</span></span> <span data-ttu-id="ccc27-114">Bu, MD5 karma algoritmasıyla bir sertifika kullanmaya devam etmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ccc27-114">This allows you to continue to use a certificate with the MD5 hash algorithm.</span></span>

  > [!CAUTION]
  > <span data-ttu-id="ccc27-115">Bu geçici çözüm önerilmez, çünkü MD5 karma algoritması olan bir sertifika güvenli değil olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="ccc27-115">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>

  <span data-ttu-id="ccc27-116">Aşağıdaki yapılandırma dosyası bunu yapar:</span><span class="sxs-lookup"><span data-stu-id="ccc27-116">The following configuration file does this:</span></span>

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

- <span data-ttu-id="ccc27-117">Bağlama, kaynak kodunda dinamik olarak yapılandırılırsa, <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> özelliği, kaynak kodundaki TLS 1,1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) veya protokolün önceki bir sürümünü kullanacak şekilde güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="ccc27-117">If the binding is dynamically configured in source code, update the <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> property to use TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) or an  earlier version of the protocol in the source code.</span></span>

  > [!CAUTION]
  > <span data-ttu-id="ccc27-118">Bu geçici çözüm önerilmez, çünkü MD5 karma algoritması olan bir sertifika güvenli değil olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="ccc27-118">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>

## <a name="see-also"></a><span data-ttu-id="ccc27-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ccc27-119">See also</span></span>

- [<span data-ttu-id="ccc27-120">Çalışma Zamanı Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="ccc27-120">Runtime Changes</span></span>](runtime-changes-in-the-net-framework-4-6.md)
