---
title: 211 - ParameterInspectorAfterCallInvoked
ms.date: 03/30/2017
ms.assetid: c0e21297-10b8-4456-a0e1-e019145cd5ac
ms.openlocfilehash: ada3ced31def2bb821b975e09f50ad83f28d56bf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781868"
---
# <a name="211---parameterinspectoraftercallinvoked"></a><span data-ttu-id="be248-102">211 - ParameterInspectorAfterCallInvoked</span><span class="sxs-lookup"><span data-stu-id="be248-102">211 - ParameterInspectorAfterCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="be248-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="be248-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="be248-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="be248-104">ID</span></span>|<span data-ttu-id="be248-105">211</span><span class="sxs-lookup"><span data-stu-id="be248-105">211</span></span>|  
|<span data-ttu-id="be248-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="be248-106">Keywords</span></span>|<span data-ttu-id="be248-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="be248-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="be248-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="be248-108">Level</span></span>|<span data-ttu-id="be248-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="be248-109">Information</span></span>|  
|<span data-ttu-id="be248-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="be248-110">Channel</span></span>|<span data-ttu-id="be248-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="be248-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="be248-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="be248-112">Description</span></span>  
 <span data-ttu-id="be248-113">Bu olay, hizmet modeli çağırdığı sonra yayıldığını `AfterCall` metodunda bir `ParameterInspector`.</span><span class="sxs-lookup"><span data-stu-id="be248-113">This event is emitted after the Service Model has invoked the `AfterCall` method on a `ParameterInspector`.</span></span>  
  
## <a name="message"></a><span data-ttu-id="be248-114">İleti</span><span class="sxs-lookup"><span data-stu-id="be248-114">Message</span></span>  
 <span data-ttu-id="be248-115">Dağıtıcı 'AfterCall' üzerinde '%1' türünde bir ParameterInspector çağrılır.</span><span class="sxs-lookup"><span data-stu-id="be248-115">The Dispatcher invoked 'AfterCall' on a ParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="be248-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="be248-116">Details</span></span>  
  
|<span data-ttu-id="be248-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="be248-117">Data Item Name</span></span>|<span data-ttu-id="be248-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="be248-118">Data Item Type</span></span>|<span data-ttu-id="be248-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="be248-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="be248-120">Tür adı</span><span class="sxs-lookup"><span data-stu-id="be248-120">Type Name</span></span>|`xs:string`|<span data-ttu-id="be248-121">Çağrılan türünün CLR FullName `ParameterInspector`.</span><span class="sxs-lookup"><span data-stu-id="be248-121">The CLR FullName of the type of the invoked `ParameterInspector`.</span></span>|  
|<span data-ttu-id="be248-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="be248-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="be248-123">Bu alan, Web barındırılan hizmetleri, Web hiyerarşideki hizmet benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="be248-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="be248-124">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı '.</span><span class="sxs-lookup"><span data-stu-id="be248-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="be248-125">Örnek: ' Varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="be248-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="be248-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="be248-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="be248-127">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="be248-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
