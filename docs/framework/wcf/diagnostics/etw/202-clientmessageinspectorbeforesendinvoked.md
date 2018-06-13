---
title: 202 - ClientMessageInspectorBeforeSendInvoked
ms.date: 03/30/2017
ms.assetid: 0b02ca82-8a55-45e3-b2e2-ddfe28a7269c
ms.openlocfilehash: 98de1d7e8e5e87ec7fbd783092f7fbc212fec65d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459361"
---
# <a name="202---clientmessageinspectorbeforesendinvoked"></a><span data-ttu-id="bf90d-102">202 - ClientMessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="bf90d-102">202 - ClientMessageInspectorBeforeSendInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="bf90d-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="bf90d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bf90d-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="bf90d-104">ID</span></span>|<span data-ttu-id="bf90d-105">202</span><span class="sxs-lookup"><span data-stu-id="bf90d-105">202</span></span>|  
|<span data-ttu-id="bf90d-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="bf90d-106">Keywords</span></span>|<span data-ttu-id="bf90d-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="bf90d-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="bf90d-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="bf90d-108">Level</span></span>|<span data-ttu-id="bf90d-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="bf90d-109">Information</span></span>|  
|<span data-ttu-id="bf90d-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="bf90d-110">Channel</span></span>|<span data-ttu-id="bf90d-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="bf90d-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="bf90d-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bf90d-112">Description</span></span>  
 <span data-ttu-id="bf90d-113">Bu olay, hizmet modeli çağrılmış sonra yayınlanır `BeforeSendRequest` istemci ileti denetçisi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bf90d-113">This event is emitted after the Service Model has invoked the `BeforeSendRequest` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="bf90d-114">İleti</span><span class="sxs-lookup"><span data-stu-id="bf90d-114">Message</span></span>  
 <span data-ttu-id="bf90d-115">Dağıtıcı '%1' türünde bir ClientMessageInspector ' BeforeSendRequest' çağrılır.</span><span class="sxs-lookup"><span data-stu-id="bf90d-115">The Dispatcher invoked 'BeforeSendRequest' on a ClientMessageInspector of type  '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="bf90d-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="bf90d-116">Details</span></span>  
  
|<span data-ttu-id="bf90d-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="bf90d-117">Data Item Name</span></span>|<span data-ttu-id="bf90d-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="bf90d-118">Data Item Type</span></span>|<span data-ttu-id="bf90d-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bf90d-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="bf90d-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="bf90d-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="bf90d-121">Çağrılan Denetçisi'nin türü CLR tam adı.</span><span class="sxs-lookup"><span data-stu-id="bf90d-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="bf90d-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="bf90d-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="bf90d-123">Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bf90d-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="bf90d-124">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="bf90d-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="bf90d-125">Örnek: ' varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="bf90d-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="bf90d-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="bf90d-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="bf90d-127">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="bf90d-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
