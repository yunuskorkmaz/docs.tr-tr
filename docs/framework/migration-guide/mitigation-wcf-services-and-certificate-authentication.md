---
title: 'Azaltma: WCF hizmetleri ve sertifika kimlik doğrulaması'
ms.date: 03/30/2017
ms.assetid: ef19c91a-b9df-4bf0-a28e-eb1e99c4bc95
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fdacf5fc4a5c73fc60df961432089ee65dd0cfaa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59079545"
---
# <a name="mitigation-wcf-services-and-certificate-authentication"></a><span data-ttu-id="56a80-102">Azaltma: WCF hizmetleri ve sertifika kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="56a80-102">Mitigation: WCF Services and Certificate Authentication</span></span>
<span data-ttu-id="56a80-103">.NET Framework 4.6, TLS 1.1 ve TLS 1.2 WCF SSL protokolü varsayılan listeye ekler.</span><span class="sxs-lookup"><span data-stu-id="56a80-103">The .NET Framework 4.6 adds TLS 1.1 and TLS 1.2 to the WCF SSL protocol default list.</span></span> <span data-ttu-id="56a80-104">İstemci ve sunucu makineler sahip .NET Framework 4.6 veya üzeri yüklü olduğunda, TLS 1.2 anlaşması için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="56a80-104">When both client and server machines have  the .NET Framework 4.6 or later installed, TLS 1.2 is used for negotiation.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="56a80-105">Etki</span><span class="sxs-lookup"><span data-stu-id="56a80-105">Impact</span></span>  
 <span data-ttu-id="56a80-106">TLS 1.2 MD5 sertifika kimlik doğrulamasını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="56a80-106">TLS 1.2 does not support MD5 certificate authentication.</span></span> <span data-ttu-id="56a80-107">Bir MD5 karma algoritması kullanan bir SSL sertifikası kullanırsa, sonuç olarak, WCF istemcisini WCF hizmetine bağlanamıyor.</span><span class="sxs-lookup"><span data-stu-id="56a80-107">As a result, if a customer uses an SSL  certificate which uses MD5 for the hash algorithm, the WCF client fails to connect to the WCF service.</span></span> <span data-ttu-id="56a80-108">Daha fazla bilgi için [azaltma: WCF hizmetleri ve sertifika kimlik doğrulaması](../../../docs/framework/migration-guide/mitigation-wcf-services-and-certificate-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="56a80-108">For more information, see [Mitigation: WCF Services and Certificate Authentication](../../../docs/framework/migration-guide/mitigation-wcf-services-and-certificate-authentication.md).</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="56a80-109">Azaltma</span><span class="sxs-lookup"><span data-stu-id="56a80-109">Mitigation</span></span>  
 <span data-ttu-id="56a80-110">Bir WCF istemcisi, aşağıdakilerden birini yaparak bir WCF sunucuya bağlanabilmesi için bu sorunu geçici olarak çalışabilir:</span><span class="sxs-lookup"><span data-stu-id="56a80-110">You can work around this issue so that a WCF client can connect to a WCF server by doing any of the following:</span></span>  
  
-   <span data-ttu-id="56a80-111">MD5 algoritmasını kullanmayı sertifikayı güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="56a80-111">Update the certificate to not use the MD5 algorithm.</span></span> <span data-ttu-id="56a80-112">Önerilen çözüm budur.</span><span class="sxs-lookup"><span data-stu-id="56a80-112">This is the recommended solution.</span></span>  
  
-   <span data-ttu-id="56a80-113">Bağlama dinamik olarak kaynak kodunda yapılandırılmamışsa, TLS 1.1 veya önceki bir sürümünün protokolü kullanmak için uygulama yapılandırma dosyasını güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="56a80-113">If the binding is not dynamically configured in source code, update the application's configuration file to use TLS 1.1 or an earlier version of the protocol.</span></span> <span data-ttu-id="56a80-114">Bu, bir sertifika MD5 karma algoritması ile kullanmaya devam etmek sağlar.</span><span class="sxs-lookup"><span data-stu-id="56a80-114">This allows you to continue to use a certificate with the MD5 hash algorithm.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="56a80-115">Bu geçici çözüm önerilmez, bu yana MD5 karma algoritması bir sertifikayla güvenli olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="56a80-115">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>  
  
     <span data-ttu-id="56a80-116">Şu yapılandırma dosyasını şunu yapar:</span><span class="sxs-lookup"><span data-stu-id="56a80-116">The following configuration file does this:</span></span>  
  
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
  
-   <span data-ttu-id="56a80-117">Kaynak kodunda bağlama dinamik olarak yapılandırılmışsa, güncelleştirme <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> özelliğinin TLS 1.1 kullanmak için (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) veya önceki bir sürümünün kaynak kodundaki protokolü.</span><span class="sxs-lookup"><span data-stu-id="56a80-117">If the binding is dynamically configured in source code, update the <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> property to use TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) or an  earlier version of the protocol in the source code.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="56a80-118">Bu geçici çözüm önerilmez, bu yana MD5 karma algoritması bir sertifikayla güvenli olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="56a80-118">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56a80-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56a80-119">See also</span></span>

- [<span data-ttu-id="56a80-120">Çalışma Zamanı Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="56a80-120">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
