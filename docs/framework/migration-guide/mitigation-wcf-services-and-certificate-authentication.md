---
title: 'Risk azaltma: WCF Hizmetleri ve sertifika kimlik doğrulaması'
description: .NET Framework 4,6 ' deki WCF SSL protokolü varsayılan listesindeki değişikliklerden sertifika kimlik doğrulama sorunlarını nasıl azaltacağınızı öğrenin.
ms.date: 03/30/2017
ms.assetid: ef19c91a-b9df-4bf0-a28e-eb1e99c4bc95
ms.openlocfilehash: b6460e58bb32151003430d6573c4bcf1b514081b
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475378"
---
# <a name="mitigation-wcf-services-and-certificate-authentication"></a><span data-ttu-id="ba9d9-103">Risk azaltma: WCF Hizmetleri ve sertifika kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="ba9d9-103">Mitigation: WCF Services and Certificate Authentication</span></span>

<span data-ttu-id="ba9d9-104">4,6 .NET Framework, WCF SSL protokolü varsayılan listesine TLS 1,1 ve TLS 1,2 ekler.</span><span class="sxs-lookup"><span data-stu-id="ba9d9-104">The .NET Framework 4.6 adds TLS 1.1 and TLS 1.2 to the WCF SSL protocol default list.</span></span> <span data-ttu-id="ba9d9-105">Hem istemci hem de sunucu makinelerinin .NET Framework 4,6 veya üzeri bir sürümü yüklüyse, anlaşma için TLS 1,2 kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ba9d9-105">When both client and server machines have  the .NET Framework 4.6 or later installed, TLS 1.2 is used for negotiation.</span></span>

## <a name="impact"></a><span data-ttu-id="ba9d9-106">Etki</span><span class="sxs-lookup"><span data-stu-id="ba9d9-106">Impact</span></span>

<span data-ttu-id="ba9d9-107">TLS 1,2, MD5 sertifikası kimlik doğrulamasını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="ba9d9-107">TLS 1.2 does not support MD5 certificate authentication.</span></span> <span data-ttu-id="ba9d9-108">Sonuç olarak, bir müşteri karma algoritma için MD5 kullanan bir SSL sertifikası kullanıyorsa, WCF istemcisi WCF hizmetine bağlanamaz.</span><span class="sxs-lookup"><span data-stu-id="ba9d9-108">As a result, if a customer uses an SSL certificate which uses MD5 for the hash algorithm, the WCF client fails to connect to the WCF service.</span></span> <span data-ttu-id="ba9d9-109">Daha fazla bilgi için bkz. [azaltma: WCF Hizmetleri ve sertifika kimlik doğrulaması](mitigation-wcf-services-and-certificate-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="ba9d9-109">For more information, see [Mitigation: WCF Services and Certificate Authentication](mitigation-wcf-services-and-certificate-authentication.md).</span></span>

## <a name="mitigation"></a><span data-ttu-id="ba9d9-110">Risk azaltma</span><span class="sxs-lookup"><span data-stu-id="ba9d9-110">Mitigation</span></span>

<span data-ttu-id="ba9d9-111">Bir WCF istemcisinin aşağıdakilerden birini yaparak bir WCF sunucusuna bağlanabilmesi için bu soruna geçici bir çözüm bulabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ba9d9-111">You can work around this issue so that a WCF client can connect to a WCF server by doing any of the following:</span></span>

- <span data-ttu-id="ba9d9-112">Bu sertifikayı, MD5 algoritmasını kullanacak şekilde güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="ba9d9-112">Update the certificate to not use the MD5 algorithm.</span></span> <span data-ttu-id="ba9d9-113">Önerilen çözüm budur.</span><span class="sxs-lookup"><span data-stu-id="ba9d9-113">This is the recommended solution.</span></span>

- <span data-ttu-id="ba9d9-114">Bağlama kaynak kodunda dinamik olarak yapılandırılmamışsa, uygulamanın yapılandırma dosyasını TLS 1,1 veya protokolün önceki bir sürümünü kullanacak şekilde güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="ba9d9-114">If the binding is not dynamically configured in source code, update the application's configuration file to use TLS 1.1 or an earlier version of the protocol.</span></span> <span data-ttu-id="ba9d9-115">Bu, MD5 karma algoritmasıyla bir sertifika kullanmaya devam etmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba9d9-115">This allows you to continue to use a certificate with the MD5 hash algorithm.</span></span>

  > [!CAUTION]
  > <span data-ttu-id="ba9d9-116">Bu geçici çözüm önerilmez, çünkü MD5 karma algoritması olan bir sertifika güvenli değil olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="ba9d9-116">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>

  <span data-ttu-id="ba9d9-117">Aşağıdaki yapılandırma dosyası bunu yapar:</span><span class="sxs-lookup"><span data-stu-id="ba9d9-117">The following configuration file does this:</span></span>

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

- <span data-ttu-id="ba9d9-118">Bağlama, kaynak kodunda dinamik olarak yapılandırılırsa, <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> özelliği, kaynak KODUNDAKI TLS 1,1 ( <xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType> ) veya protokolün önceki bir sürümünü kullanacak şekilde güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="ba9d9-118">If the binding is dynamically configured in source code, update the <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> property to use TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) or an  earlier version of the protocol in the source code.</span></span>

  > [!CAUTION]
  > <span data-ttu-id="ba9d9-119">Bu geçici çözüm önerilmez, çünkü MD5 karma algoritması olan bir sertifika güvenli değil olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="ba9d9-119">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>

## <a name="see-also"></a><span data-ttu-id="ba9d9-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba9d9-120">See also</span></span>

- [<span data-ttu-id="ba9d9-121">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="ba9d9-121">Application compatibility</span></span>](application-compatibility.md)
