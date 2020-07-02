---
ms.openlocfilehash: fb9436ec9e525afb497033775e34b6b636ced22d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621442"
---
### <a name="wcf-services-that-use-nettcp-with-ssl-security-and-md5-certificate-authentication"></a><span data-ttu-id="5b21a-101">SSL güvenliği ve MD5 sertifikası kimlik doğrulamasıyla NETTCP kullanan WCF Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="5b21a-101">WCF services that use NETTCP with SSL security and MD5 certificate authentication</span></span>

#### <a name="details"></a><span data-ttu-id="5b21a-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="5b21a-102">Details</span></span>

<span data-ttu-id="5b21a-103">4,6 .NET Framework, WCF SSL varsayılan protokol listesine TLS 1,1 ve TLS 1,2 ekler.</span><span class="sxs-lookup"><span data-stu-id="5b21a-103">The .NET Framework 4.6 adds TLS 1.1 and TLS 1.2 to the WCF SSL default protocol list.</span></span> <span data-ttu-id="5b21a-104">Hem istemci hem de sunucu makinelerinin .NET Framework 4,6 veya üzeri bir sürümü yüklüyse, anlaşma için TLS 1,2 kullanılır. TLS 1,2, MD5 sertifikası kimlik doğrulamasını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="5b21a-104">When both client and server machines have the .NET Framework 4.6 or later installed, TLS 1.2 is used for negotiation.TLS 1.2 does not support MD5 certificate authentication.</span></span> <span data-ttu-id="5b21a-105">Sonuç olarak, bir müşteri MD5 sertifikası kullanıyorsa, WCF istemcisi WCF hizmetine bağlanamaz.</span><span class="sxs-lookup"><span data-stu-id="5b21a-105">As a result, if a customer uses an MD5 certificate, the WCF client will fail to connect to the WCF service.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5b21a-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="5b21a-106">Suggestion</span></span>

<span data-ttu-id="5b21a-107">Bir WCF istemcisinin aşağıdakilerden birini yaparak bir WCF sunucusuna bağlanabilmesi için bu soruna geçici bir çözüm bulabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5b21a-107">You can work around this issue so that a WCF client can connect to a WCF server by doing any of the following:</span></span>

- <span data-ttu-id="5b21a-108">Bu sertifikayı, MD5 algoritmasını kullanacak şekilde güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="5b21a-108">Update the certificate to not use the MD5 algorithm.</span></span> <span data-ttu-id="5b21a-109">Önerilen çözüm budur.</span><span class="sxs-lookup"><span data-stu-id="5b21a-109">This is the recommended solution.</span></span>
- <span data-ttu-id="5b21a-110">Bağlama kaynak kodunda dinamik olarak yapılandırılmamışsa, uygulamanın yapılandırma dosyasını TLS 1,1 veya protokolün önceki bir sürümünü kullanacak şekilde güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="5b21a-110">If the binding is not dynamically configured in source code, update the application's configuration file to use TLS 1.1 or an earlier version of the protocol.</span></span> <span data-ttu-id="5b21a-111">Bu, MD5 karma algoritmasıyla bir sertifika kullanmaya devam etmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b21a-111">This allows you to continue to use a certificate with the MD5 hash algorithm.</span></span>

> [!WARNING]
> <span data-ttu-id="5b21a-112">Bu geçici çözüm önerilmez, çünkü MD5 karma algoritması olan bir sertifika güvenli değil olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="5b21a-112">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>

<span data-ttu-id="5b21a-113">Aşağıdaki yapılandırma dosyası bunu yapar:</span><span class="sxs-lookup"><span data-stu-id="5b21a-113">The following configuration file does this:</span></span>

```xml
<configuration>
  <system.serviceModel>
    <bindings>
      <netTcpBinding>
        <binding>
          <security mode= "None/Transport/Message/TransportWithMessageCredential" >
            <transport clientCredentialType="None/Windows/Certificate"
                       protectionLevel="None/Sign/EncryptAndSign"
                       sslProtocols="Ssl3/Tls1/Tls11">
            </transport>
          </security>
        </binding>
      </netTcpBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```

- <span data-ttu-id="5b21a-114">Bağlama, kaynak kodunda dinamik olarak yapılandırılırsa, <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType> ÖZELLIĞI TLS 1,1 ( <xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType> veya kaynak kodundaki protokolün önceki bir sürümünü) kullanacak şekilde güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="5b21a-114">If the binding is dynamically configured in source code, update the <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType> property to use TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType> or an earlier version of the protocol in the source code.</span></span>

> [!WARNING]
> <span data-ttu-id="5b21a-115">Bu geçici çözüm önerilmez, çünkü MD5 karma algoritması olan bir sertifika güvenli değil olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="5b21a-115">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>

| <span data-ttu-id="5b21a-116">Name</span><span class="sxs-lookup"><span data-stu-id="5b21a-116">Name</span></span>    | <span data-ttu-id="5b21a-117">Değer</span><span class="sxs-lookup"><span data-stu-id="5b21a-117">Value</span></span>   |
|:--------|:--------|
| <span data-ttu-id="5b21a-118">Kapsam</span><span class="sxs-lookup"><span data-stu-id="5b21a-118">Scope</span></span>   | <span data-ttu-id="5b21a-119">İkincil</span><span class="sxs-lookup"><span data-stu-id="5b21a-119">Minor</span></span>   |
| <span data-ttu-id="5b21a-120">Sürüm</span><span class="sxs-lookup"><span data-stu-id="5b21a-120">Version</span></span> | <span data-ttu-id="5b21a-121">4.6</span><span class="sxs-lookup"><span data-stu-id="5b21a-121">4.6</span></span>     |
| <span data-ttu-id="5b21a-122">Tür</span><span class="sxs-lookup"><span data-stu-id="5b21a-122">Type</span></span>    | <span data-ttu-id="5b21a-123">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="5b21a-123">Runtime</span></span> |
