---
ms.openlocfilehash: 23987c300ac4fbad401de180b63106cd234f8d27
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496227"
---
### <a name="remove-ssl3-from-the-wcf-transportdefaults"></a><span data-ttu-id="7440e-101">WCF TransportDefaults Ssl3 kaldırma</span><span class="sxs-lookup"><span data-stu-id="7440e-101">Remove Ssl3 from the WCF TransportDefaults</span></span>

#### <a name="details"></a><span data-ttu-id="7440e-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="7440e-102">Details</span></span>

<span data-ttu-id="7440e-103">Aktarım güvenliği ile NetTcp kullanılırken ve bir sertifika kimlik bilgisi türüyle, SSL 3 Protokolü artık güvenli bir bağlantı anlaşması için kullanılan varsayılan bir protokol değildir.</span><span class="sxs-lookup"><span data-stu-id="7440e-103">When using NetTcp with transport security and a credential type of certificate, the SSL 3 protocol is no longer a default protocol used for negotiating a secure connection.</span></span> <span data-ttu-id="7440e-104">Çoğu durumda, TLS 1,0, her zaman NetTcp protokol listesine eklendiğinden, var olan uygulamalara hiçbir etkisi olmaz.</span><span class="sxs-lookup"><span data-stu-id="7440e-104">In most cases there should be no impact to existing apps as TLS 1.0 has always been included in the protocol list for NetTcp.</span></span> <span data-ttu-id="7440e-105">Tüm mevcut istemciler, en az TLS 1.0 kullanarak bir bağlantı anlaşması yapabilmelidir.</span><span class="sxs-lookup"><span data-stu-id="7440e-105">All existing clients should be able to negotiate a connection using at least TLS1.0.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7440e-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="7440e-106">Suggestion</span></span>

<span data-ttu-id="7440e-107">Ssl3 gerekliyse, anlaşmalı protokoller listesine Ssl3 eklemek için aşağıdaki yapılandırma mekanizmalarından birini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7440e-107">If Ssl3 is required, use one of the following configuration mechanisms to add Ssl3 to the list of negotiated protocols.</span></span><ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols></li><li>[<](~/docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)</li><li><span data-ttu-id="7440e-108">[ &lt; CustomBinding] için [sslStreamSecurity &gt; bölümü &lt; &gt; ] ~/FI/Framework/configure-Apps/File-Schema/WCF/sslStreamSecurity.exe)</span><span class="sxs-lookup"><span data-stu-id="7440e-108">[&lt;sslStreamSecurity&gt; section of &lt;customBinding&gt;]~/docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)</span></span></li></ul>

| <span data-ttu-id="7440e-109">Name</span><span class="sxs-lookup"><span data-stu-id="7440e-109">Name</span></span>    | <span data-ttu-id="7440e-110">Değer</span><span class="sxs-lookup"><span data-stu-id="7440e-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7440e-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="7440e-111">Scope</span></span>   |<span data-ttu-id="7440e-112">Edge</span><span class="sxs-lookup"><span data-stu-id="7440e-112">Edge</span></span>|
|<span data-ttu-id="7440e-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="7440e-113">Version</span></span>|<span data-ttu-id="7440e-114">4.6.2</span><span class="sxs-lookup"><span data-stu-id="7440e-114">4.6.2</span></span>|
|<span data-ttu-id="7440e-115">Tür</span><span class="sxs-lookup"><span data-stu-id="7440e-115">Type</span></span>|<span data-ttu-id="7440e-116">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="7440e-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="7440e-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="7440e-117">Affected APIs</span></span>

- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols?displayProperty=nameWithType>
- <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols`
- `P:System.ServiceModel.TcpTransportSecurity.SslProtocols`

-->
