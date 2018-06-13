---
title: 211 - ParameterInspectorAfterCallInvoked
ms.date: 03/30/2017
ms.assetid: c0e21297-10b8-4456-a0e1-e019145cd5ac
ms.openlocfilehash: ada3ced31def2bb821b975e09f50ad83f28d56bf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459723"
---
# <a name="211---parameterinspectoraftercallinvoked"></a><span data-ttu-id="3d836-102">211 - ParameterInspectorAfterCallInvoked</span><span class="sxs-lookup"><span data-stu-id="3d836-102">211 - ParameterInspectorAfterCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="3d836-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="3d836-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3d836-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="3d836-104">ID</span></span>|<span data-ttu-id="3d836-105">211</span><span class="sxs-lookup"><span data-stu-id="3d836-105">211</span></span>|  
|<span data-ttu-id="3d836-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="3d836-106">Keywords</span></span>|<span data-ttu-id="3d836-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3d836-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="3d836-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="3d836-108">Level</span></span>|<span data-ttu-id="3d836-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="3d836-109">Information</span></span>|  
|<span data-ttu-id="3d836-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="3d836-110">Channel</span></span>|<span data-ttu-id="3d836-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="3d836-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3d836-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3d836-112">Description</span></span>  
 <span data-ttu-id="3d836-113">Bu olay, hizmet modeli çağrılmış sonra yayınlanır `AfterCall` yöntemi bir `ParameterInspector`.</span><span class="sxs-lookup"><span data-stu-id="3d836-113">This event is emitted after the Service Model has invoked the `AfterCall` method on a `ParameterInspector`.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3d836-114">İleti</span><span class="sxs-lookup"><span data-stu-id="3d836-114">Message</span></span>  
 <span data-ttu-id="3d836-115">Dağıtıcı '%1' türünde bir ParameterInspector ' AfterCall' çağrılır.</span><span class="sxs-lookup"><span data-stu-id="3d836-115">The Dispatcher invoked 'AfterCall' on a ParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3d836-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="3d836-116">Details</span></span>  
  
|<span data-ttu-id="3d836-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="3d836-117">Data Item Name</span></span>|<span data-ttu-id="3d836-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="3d836-118">Data Item Type</span></span>|<span data-ttu-id="3d836-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3d836-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3d836-120">Tür adı</span><span class="sxs-lookup"><span data-stu-id="3d836-120">Type Name</span></span>|`xs:string`|<span data-ttu-id="3d836-121">Çağrılan türünün CLR FullName `ParameterInspector`.</span><span class="sxs-lookup"><span data-stu-id="3d836-121">The CLR FullName of the type of the invoked `ParameterInspector`.</span></span>|  
|<span data-ttu-id="3d836-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="3d836-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="3d836-123">Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3d836-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="3d836-124">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="3d836-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="3d836-125">Örnek: ' varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="3d836-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="3d836-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3d836-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="3d836-127">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="3d836-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
