---
ms.openlocfilehash: 0c3876d30a80501a89f3a37ce24e2f71122c1b44
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497746"
---
### <a name="systemservicemodelwebwebservicehost-object-no-longer-adds-a-default-endpoint"></a><span data-ttu-id="a458e-101">System. ServiceModel. Web. WebServiceHost nesnesi artık varsayılan bir uç nokta eklemektedir</span><span class="sxs-lookup"><span data-stu-id="a458e-101">System.ServiceModel.Web.WebServiceHost object no longer adds a default endpoint</span></span>

#### <a name="details"></a><span data-ttu-id="a458e-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="a458e-102">Details</span></span>

<span data-ttu-id="a458e-103"><xref:System.ServiceModel.Web.WebServiceHost>Uygulama kodu tarafından açık bir uç nokta eklendiyse nesne artık varsayılan bir uç nokta eklemektedir.</span><span class="sxs-lookup"><span data-stu-id="a458e-103">The <xref:System.ServiceModel.Web.WebServiceHost> object no longer adds a default endpoint if an explicit endpoint has been added by application code.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a458e-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="a458e-104">Suggestion</span></span>

<span data-ttu-id="a458e-105">Kullanıcıların varsayılan bir uç noktaya bağlanabilmesi ve diğer açık uç noktaların öğesine eklenmiş olması beklendiğinde <xref:System.ServiceModel.Web.WebServiceHost?displayProperty=fullName> , varsayılan bitiş noktaları da açıkça eklenmelidir (kullanılarak <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints?displayProperty=fullName> ).</span><span class="sxs-lookup"><span data-stu-id="a458e-105">If users will expect to be able to connect to a default endpoint and other explicit endpoints have been added to the <xref:System.ServiceModel.Web.WebServiceHost?displayProperty=fullName>, default endpoints should also be added explicitly (using <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints?displayProperty=fullName>).</span></span>

| <span data-ttu-id="a458e-106">Name</span><span class="sxs-lookup"><span data-stu-id="a458e-106">Name</span></span>    | <span data-ttu-id="a458e-107">Değer</span><span class="sxs-lookup"><span data-stu-id="a458e-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a458e-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="a458e-108">Scope</span></span>   |<span data-ttu-id="a458e-109">İkincil</span><span class="sxs-lookup"><span data-stu-id="a458e-109">Minor</span></span>|
|<span data-ttu-id="a458e-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="a458e-110">Version</span></span>|<span data-ttu-id="a458e-111">4,5</span><span class="sxs-lookup"><span data-stu-id="a458e-111">4.5</span></span>|
|<span data-ttu-id="a458e-112">Tür</span><span class="sxs-lookup"><span data-stu-id="a458e-112">Type</span></span>|<span data-ttu-id="a458e-113">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="a458e-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="a458e-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="a458e-114">Affected APIs</span></span>

- <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.String)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.String,System.Uri)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.ServiceModel.Description.ServiceEndpoint)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.String)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.Uri)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.String,System.Uri)?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.String)`
- `M:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri)`
- `M:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.String,System.Uri)`
- `M:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)`
- `M:System.ServiceModel.ServiceHost.AddServiceEndpoint(System.Type,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)`
- `M:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.ServiceModel.Description.ServiceEndpoint)`
- `M:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.String)`
- `M:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.Uri)`
- `M:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.String,System.Uri)`
- `M:System.ServiceModel.ServiceHostBase.AddServiceEndpoint(System.String,System.ServiceModel.Channels.Binding,System.Uri,System.Uri)`

-->
