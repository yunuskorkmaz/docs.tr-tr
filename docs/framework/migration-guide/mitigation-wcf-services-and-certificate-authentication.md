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
# <a name="mitigation-wcf-services-and-certificate-authentication"></a><span data-ttu-id="4000a-102">Azaltma: WCF hizmetleri ve sertifika kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="4000a-102">Mitigation: WCF Services and Certificate Authentication</span></span>
<span data-ttu-id="4000a-103">.NET Framework 4.6 TLS 1.1 ve TLS 1.2 WCF SSL protokolü varsayılan listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="4000a-103">The .NET Framework 4.6 adds TLS 1.1 and TLS 1.2 to the WCF SSL protocol default list.</span></span> <span data-ttu-id="4000a-104">İstemci ve sunucu makinelerini .NET Framework 4.6 veya sonrası yüklü olduğunda, TLS 1.2 anlaşması için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4000a-104">When both client and server machines have  the .NET Framework 4.6 or later installed, TLS 1.2 is used for negotiation.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="4000a-105">Etki</span><span class="sxs-lookup"><span data-stu-id="4000a-105">Impact</span></span>  
 <span data-ttu-id="4000a-106">TLS 1.2 MD5 sertifika kimlik doğrulamasını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="4000a-106">TLS 1.2 does not support MD5 certificate authentication.</span></span> <span data-ttu-id="4000a-107">Bir müşteri MD5 karma algoritması kullanan bir SSL sertifikası kullanıyorsa, sonuç olarak, WCF istemcisini WCF hizmetine bağlanamıyor.</span><span class="sxs-lookup"><span data-stu-id="4000a-107">As a result, if a customer uses an SSL  certificate which uses MD5 for the hash algorithm, the WCF client fails to connect to the WCF service.</span></span> <span data-ttu-id="4000a-108">Daha fazla bilgi için bkz: [azaltma: WCF hizmetleri ve sertifika kimlik doğrulaması](../../../docs/framework/migration-guide/mitigation-wcf-services-and-certificate-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="4000a-108">For more information, see [Mitigation: WCF Services and Certificate Authentication](../../../docs/framework/migration-guide/mitigation-wcf-services-and-certificate-authentication.md).</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="4000a-109">Azaltma</span><span class="sxs-lookup"><span data-stu-id="4000a-109">Mitigation</span></span>  
 <span data-ttu-id="4000a-110">Bir WCF istemcisi aşağıdakilerden birini yaparak bir WCF sunucuya bağlanabilmesi bu soruna geçici çözüm bulabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4000a-110">You can work around this issue so that a WCF client can connect to a WCF server by doing any of the following:</span></span>  
  
-   <span data-ttu-id="4000a-111">MD5 algoritması kullanmamayı sertifikayı güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="4000a-111">Update the certificate to not use the MD5 algorithm.</span></span> <span data-ttu-id="4000a-112">Bu önerilen bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="4000a-112">This is the recommended solution.</span></span>  
  
-   <span data-ttu-id="4000a-113">Bağlama kaynak kodunu dinamik olarak yapılandırılmamışsa, TLS 1.1 veya protokolü önceki bir sürümünü kullanmak için uygulamanın yapılandırma dosyasını güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="4000a-113">If the binding is not dynamically configured in source code, update the application's configuration file to use TLS 1.1 or an earlier version of the protocol.</span></span> <span data-ttu-id="4000a-114">Bu, bir sertifika ile MD5 karma algoritması kullanmaya devam etmek sağlar.</span><span class="sxs-lookup"><span data-stu-id="4000a-114">This allows you to continue to use a certificate with the MD5 hash algorithm.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="4000a-115">Bu geçici çözüm önerilmez, bu yana MD5 karma algoritmasını bir sertifikayla güvenli olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="4000a-115">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>  
  
     <span data-ttu-id="4000a-116">Aşağıdaki yapılandırma dosyası bu yapar:</span><span class="sxs-lookup"><span data-stu-id="4000a-116">The following configuration file does this:</span></span>  
  
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
  
-   <span data-ttu-id="4000a-117">Bağlama kaynak kodunu dinamik olarak yapılandırılmışsa, güncelleştirme <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> TLS 1.1 kullanmak için özelliği (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) veya kaynak kodu protokolünde önceki bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="4000a-117">If the binding is dynamically configured in source code, update the <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> property to use TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) or an  earlier version of the protocol in the source code.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="4000a-118">Bu geçici çözüm önerilmez, bu yana MD5 karma algoritmasını bir sertifikayla güvenli olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="4000a-118">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4000a-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4000a-119">See Also</span></span>  
 [<span data-ttu-id="4000a-120">Çalışma Zamanı Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="4000a-120">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
