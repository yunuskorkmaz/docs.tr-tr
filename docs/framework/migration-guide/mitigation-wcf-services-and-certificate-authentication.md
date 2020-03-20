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
# <a name="mitigation-wcf-services-and-certificate-authentication"></a><span data-ttu-id="3191f-102">Azaltma: WCF Hizmetleri ve Sertifika Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="3191f-102">Mitigation: WCF Services and Certificate Authentication</span></span>

<span data-ttu-id="3191f-103">.NET Framework 4.6, WCF SSL protokolü varsayılan listesine 1,1 TLve TLS 1.2 ekler.</span><span class="sxs-lookup"><span data-stu-id="3191f-103">The .NET Framework 4.6 adds TLS 1.1 and TLS 1.2 to the WCF SSL protocol default list.</span></span> <span data-ttu-id="3191f-104">Hem istemci hem de sunucu makineleri .NET Framework 4.6 veya daha sonra yüklü olduğunda, TLS 1.2 anlaşma için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3191f-104">When both client and server machines have  the .NET Framework 4.6 or later installed, TLS 1.2 is used for negotiation.</span></span>

## <a name="impact"></a><span data-ttu-id="3191f-105">Etki</span><span class="sxs-lookup"><span data-stu-id="3191f-105">Impact</span></span>

<span data-ttu-id="3191f-106">TLS 1.2, MD5 sertifika kimlik doğrulamasını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="3191f-106">TLS 1.2 does not support MD5 certificate authentication.</span></span> <span data-ttu-id="3191f-107">Sonuç olarak, bir müşteri karma algoritması için MD5 kullanan bir SSL sertifikası kullanırsa, WCF istemcisi WCF hizmetine bağlanmayı başaramaz.</span><span class="sxs-lookup"><span data-stu-id="3191f-107">As a result, if a customer uses an SSL  certificate which uses MD5 for the hash algorithm, the WCF client fails to connect to the WCF service.</span></span> <span data-ttu-id="3191f-108">Daha fazla bilgi için [bkz: Azaltma: WCF Hizmetleri ve Sertifika Kimlik Doğrulaması.](mitigation-wcf-services-and-certificate-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="3191f-108">For more information, see [Mitigation: WCF Services and Certificate Authentication](mitigation-wcf-services-and-certificate-authentication.md).</span></span>

## <a name="mitigation"></a><span data-ttu-id="3191f-109">Risk azaltma</span><span class="sxs-lookup"><span data-stu-id="3191f-109">Mitigation</span></span>

<span data-ttu-id="3191f-110">WCF istemcisinin aşağıdakilerden herhangi birini yaparak bir WCF sunucusuna bağlanabilmesi için bu sorunu çözebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3191f-110">You can work around this issue so that a WCF client can connect to a WCF server by doing any of the following:</span></span>

- <span data-ttu-id="3191f-111">MD5 algoritmasını kullanmamak için sertifikayı güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="3191f-111">Update the certificate to not use the MD5 algorithm.</span></span> <span data-ttu-id="3191f-112">Bu önerilen çözümdür.</span><span class="sxs-lookup"><span data-stu-id="3191f-112">This is the recommended solution.</span></span>

- <span data-ttu-id="3191f-113">Bağlama kaynak kodunda dinamik olarak yapılandırılmamışsa, TLS 1.1 veya protokolün önceki bir sürümünü kullanacak şekilde uygulamanın yapılandırma dosyasını güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="3191f-113">If the binding is not dynamically configured in source code, update the application's configuration file to use TLS 1.1 or an earlier version of the protocol.</span></span> <span data-ttu-id="3191f-114">Bu, MD5 karma algoritması ile bir sertifika kullanmaya devam etmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3191f-114">This allows you to continue to use a certificate with the MD5 hash algorithm.</span></span>

  > [!CAUTION]
  > <span data-ttu-id="3191f-115">MD5 karma algoritması olan bir sertifika güvenli olarak kabul edilir, bu geçici çözüm önerilmez.</span><span class="sxs-lookup"><span data-stu-id="3191f-115">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>

  <span data-ttu-id="3191f-116">Aşağıdaki yapılandırma dosyası bunu yapar:</span><span class="sxs-lookup"><span data-stu-id="3191f-116">The following configuration file does this:</span></span>

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

- <span data-ttu-id="3191f-117">Bağlama kaynak kodunda dinamik olarak yapılandırılırsa, <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> tls 1.1<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>() veya kaynak kodundaki protokolün önceki bir sürümünü kullanacak şekilde özelliği güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="3191f-117">If the binding is dynamically configured in source code, update the <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> property to use TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) or an  earlier version of the protocol in the source code.</span></span>

  > [!CAUTION]
  > <span data-ttu-id="3191f-118">MD5 karma algoritması olan bir sertifika güvenli olarak kabul edilir, bu geçici çözüm önerilmez.</span><span class="sxs-lookup"><span data-stu-id="3191f-118">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>

## <a name="see-also"></a><span data-ttu-id="3191f-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3191f-119">See also</span></span>

- [<span data-ttu-id="3191f-120">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="3191f-120">Application compatibility</span></span>](application-compatibility.md)
