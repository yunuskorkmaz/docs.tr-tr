---
ms.openlocfilehash: 57f68c10d5d1edc9b8deaca2f4fe7edda2dd69b0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620669"
---
### <a name="systemservicemodelwebwebservicehost-object-no-longer-adds-a-default-endpoint"></a><span data-ttu-id="7ebe2-101">System. ServiceModel. Web. WebServiceHost nesnesi artık varsayılan bir uç nokta eklemektedir</span><span class="sxs-lookup"><span data-stu-id="7ebe2-101">System.ServiceModel.Web.WebServiceHost object no longer adds a default endpoint</span></span>

#### <a name="details"></a><span data-ttu-id="7ebe2-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="7ebe2-102">Details</span></span>

<span data-ttu-id="7ebe2-103"><xref:System.ServiceModel.Web.WebServiceHost>Uygulama kodu tarafından açık bir uç nokta eklendiyse nesne artık varsayılan bir uç nokta eklemektedir.</span><span class="sxs-lookup"><span data-stu-id="7ebe2-103">The <xref:System.ServiceModel.Web.WebServiceHost> object no longer adds a default endpoint if an explicit endpoint has been added by application code.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7ebe2-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="7ebe2-104">Suggestion</span></span>

<span data-ttu-id="7ebe2-105">Kullanıcıların varsayılan bir uç noktaya bağlanabilmesi ve diğer açık uç noktaların öğesine eklenmiş olması beklendiğinde <xref:System.ServiceModel.Web.WebServiceHost?displayProperty=fullName> , varsayılan bitiş noktaları da açıkça eklenmelidir (kullanılarak <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints?displayProperty=fullName> ).</span><span class="sxs-lookup"><span data-stu-id="7ebe2-105">If users will expect to be able to connect to a default endpoint and other explicit endpoints have been added to the <xref:System.ServiceModel.Web.WebServiceHost?displayProperty=fullName>, default endpoints should also be added explicitly (using <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints?displayProperty=fullName>).</span></span>

| <span data-ttu-id="7ebe2-106">Name</span><span class="sxs-lookup"><span data-stu-id="7ebe2-106">Name</span></span>    | <span data-ttu-id="7ebe2-107">Değer</span><span class="sxs-lookup"><span data-stu-id="7ebe2-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7ebe2-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="7ebe2-108">Scope</span></span>   |<span data-ttu-id="7ebe2-109">İkincil</span><span class="sxs-lookup"><span data-stu-id="7ebe2-109">Minor</span></span>|
|<span data-ttu-id="7ebe2-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="7ebe2-110">Version</span></span>|<span data-ttu-id="7ebe2-111">4,5</span><span class="sxs-lookup"><span data-stu-id="7ebe2-111">4.5</span></span>|
|<span data-ttu-id="7ebe2-112">Tür</span><span class="sxs-lookup"><span data-stu-id="7ebe2-112">Type</span></span>|<span data-ttu-id="7ebe2-113">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="7ebe2-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7ebe2-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="7ebe2-114">Affected APIs</span></span>

-<xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.String)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.String,System.Uri)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.ServiceModel.Description.ServiceEndpoint)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.String)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.Uri)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.String,System.Uri)?displayProperty=nameWithType></li><li><xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)?displayProperty=nameWithType></li></ul>|
