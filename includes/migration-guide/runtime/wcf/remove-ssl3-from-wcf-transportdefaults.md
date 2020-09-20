---
ms.openlocfilehash: a5f4047d70276a90c9d72918a2559fd795feb26e
ms.sourcegitcommit: 261e0c98a111357692b3b63c596edf0cacf72991
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2020
ms.locfileid: "90770812"
---
### <a name="remove-ssl3-from-the-wcf-transportdefaults"></a><span data-ttu-id="4393a-101">WCF TransportDefaults Ssl3 kaldırma</span><span class="sxs-lookup"><span data-stu-id="4393a-101">Remove Ssl3 from the WCF TransportDefaults</span></span>

#### <a name="details"></a><span data-ttu-id="4393a-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="4393a-102">Details</span></span>

<span data-ttu-id="4393a-103">Aktarım güvenliği ile NetTcp kullanılırken ve bir sertifika kimlik bilgisi türüyle, SSL 3 Protokolü artık güvenli bir bağlantı anlaşması için kullanılan varsayılan bir protokol değildir.</span><span class="sxs-lookup"><span data-stu-id="4393a-103">When using NetTcp with transport security and a credential type of certificate, the SSL 3 protocol is no longer a default protocol used for negotiating a secure connection.</span></span> <span data-ttu-id="4393a-104">Çoğu durumda, TLS 1,0, her zaman NetTcp protokol listesine eklendiğinden, var olan uygulamalara hiçbir etkisi olmaz.</span><span class="sxs-lookup"><span data-stu-id="4393a-104">In most cases there should be no impact to existing apps as TLS 1.0 has always been included in the protocol list for NetTcp.</span></span> <span data-ttu-id="4393a-105">Tüm mevcut istemciler, en az TLS 1.0 kullanarak bir bağlantı anlaşması yapabilmelidir.</span><span class="sxs-lookup"><span data-stu-id="4393a-105">All existing clients should be able to negotiate a connection using at least TLS1.0.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4393a-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="4393a-106">Suggestion</span></span>

<span data-ttu-id="4393a-107">Ssl3 gerekliyse, anlaşmalı protokoller listesine Ssl3 eklemek için aşağıdaki yapılandırma mekanizmalarından birini kullanın.</span><span class="sxs-lookup"><span data-stu-id="4393a-107">If Ssl3 is required, use one of the following configuration mechanisms to add Ssl3 to the list of negotiated protocols.</span></span>

- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols>
- <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols>
- [<span data-ttu-id="4393a-108">\<transport> durumunu \<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="4393a-108">\<transport> of \<netTcpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)
- [\<sslStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)

| <span data-ttu-id="4393a-109">Name</span><span class="sxs-lookup"><span data-stu-id="4393a-109">Name</span></span>    | <span data-ttu-id="4393a-110">Değer</span><span class="sxs-lookup"><span data-stu-id="4393a-110">Value</span></span>   |
|:--------|:--------|
| <span data-ttu-id="4393a-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="4393a-111">Scope</span></span>   | <span data-ttu-id="4393a-112">Edge</span><span class="sxs-lookup"><span data-stu-id="4393a-112">Edge</span></span>    |
| <span data-ttu-id="4393a-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="4393a-113">Version</span></span> | <span data-ttu-id="4393a-114">4.6.2</span><span class="sxs-lookup"><span data-stu-id="4393a-114">4.6.2</span></span>   |
| <span data-ttu-id="4393a-115">Tür</span><span class="sxs-lookup"><span data-stu-id="4393a-115">Type</span></span>    | <span data-ttu-id="4393a-116">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="4393a-116">Runtime</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="4393a-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="4393a-117">Affected APIs</span></span>

- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols?displayProperty=nameWithType>
- <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols`
- `P:System.ServiceModel.TcpTransportSecurity.SslProtocols`

-->
