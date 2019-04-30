---
title: 202 - ClientMessageInspectorBeforeSendInvoked
ms.date: 03/30/2017
ms.assetid: 0b02ca82-8a55-45e3-b2e2-ddfe28a7269c
ms.openlocfilehash: 98de1d7e8e5e87ec7fbd783092f7fbc212fec65d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781998"
---
# <a name="202---clientmessageinspectorbeforesendinvoked"></a><span data-ttu-id="e75d9-102">202 - ClientMessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="e75d9-102">202 - ClientMessageInspectorBeforeSendInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="e75d9-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e75d9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e75d9-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="e75d9-104">ID</span></span>|<span data-ttu-id="e75d9-105">202</span><span class="sxs-lookup"><span data-stu-id="e75d9-105">202</span></span>|  
|<span data-ttu-id="e75d9-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="e75d9-106">Keywords</span></span>|<span data-ttu-id="e75d9-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e75d9-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="e75d9-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="e75d9-108">Level</span></span>|<span data-ttu-id="e75d9-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="e75d9-109">Information</span></span>|  
|<span data-ttu-id="e75d9-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="e75d9-110">Channel</span></span>|<span data-ttu-id="e75d9-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="e75d9-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e75d9-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e75d9-112">Description</span></span>  
 <span data-ttu-id="e75d9-113">Bu olay, hizmet modeli çağırdığı sonra yayıldığını `BeforeSendRequest` istemci ileti denetçisi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e75d9-113">This event is emitted after the Service Model has invoked the `BeforeSendRequest` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e75d9-114">İleti</span><span class="sxs-lookup"><span data-stu-id="e75d9-114">Message</span></span>  
 <span data-ttu-id="e75d9-115">Dağıtıcı 'BeforeSendRequest' üzerinde '%1' türünde bir ClientMessageInspector çağrılır.</span><span class="sxs-lookup"><span data-stu-id="e75d9-115">The Dispatcher invoked 'BeforeSendRequest' on a ClientMessageInspector of type  '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e75d9-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e75d9-116">Details</span></span>  
  
|<span data-ttu-id="e75d9-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="e75d9-117">Data Item Name</span></span>|<span data-ttu-id="e75d9-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="e75d9-118">Data Item Type</span></span>|<span data-ttu-id="e75d9-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e75d9-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e75d9-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="e75d9-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="e75d9-121">CLR FullName çağrılan denetçisinin türü.</span><span class="sxs-lookup"><span data-stu-id="e75d9-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="e75d9-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="e75d9-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="e75d9-123">Bu alan, Web barındırılan hizmetleri, Web hiyerarşideki hizmet benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e75d9-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="e75d9-124">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı '.</span><span class="sxs-lookup"><span data-stu-id="e75d9-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="e75d9-125">Örnek: ' Varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="e75d9-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="e75d9-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e75d9-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="e75d9-127">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="e75d9-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
