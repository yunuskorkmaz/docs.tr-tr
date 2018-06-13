---
title: 212 - ParameterInspectorBeforeCallInvoked
ms.date: 03/30/2017
ms.assetid: 063fc8d2-ceac-4c18-8368-de84f2c78035
ms.openlocfilehash: 02d4a4ed1e96983e132a1943dd39f9f885e5596a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458812"
---
# <a name="212---parameterinspectorbeforecallinvoked"></a><span data-ttu-id="fa3e4-102">212 - ParameterInspectorBeforeCallInvoked</span><span class="sxs-lookup"><span data-stu-id="fa3e4-102">212 - ParameterInspectorBeforeCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="fa3e4-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="fa3e4-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fa3e4-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="fa3e4-104">ID</span></span>|<span data-ttu-id="fa3e4-105">212</span><span class="sxs-lookup"><span data-stu-id="fa3e4-105">212</span></span>|  
|<span data-ttu-id="fa3e4-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="fa3e4-106">Keywords</span></span>|<span data-ttu-id="fa3e4-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="fa3e4-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="fa3e4-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="fa3e4-108">Level</span></span>|<span data-ttu-id="fa3e4-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="fa3e4-109">Information</span></span>|  
|<span data-ttu-id="fa3e4-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="fa3e4-110">Channel</span></span>|<span data-ttu-id="fa3e4-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="fa3e4-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="fa3e4-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa3e4-112">Description</span></span>  
 <span data-ttu-id="fa3e4-113">Bu olay, hizmet modeli çağrılmış sonra yayınlanır `BeforeCall` yöntemi bir `ParameterInspector`.</span><span class="sxs-lookup"><span data-stu-id="fa3e4-113">This event is emitted after the Service Model has invoked the `BeforeCall` method on a `ParameterInspector`.</span></span>  
  
## <a name="message"></a><span data-ttu-id="fa3e4-114">İleti</span><span class="sxs-lookup"><span data-stu-id="fa3e4-114">Message</span></span>  
 <span data-ttu-id="fa3e4-115">Dağıtıcı '%1' türünde bir ParameterInspector ' BeforeCall' çağrılır.</span><span class="sxs-lookup"><span data-stu-id="fa3e4-115">The Dispatcher invoked 'BeforeCall' on a ParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="fa3e4-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="fa3e4-116">Details</span></span>  
  
|<span data-ttu-id="fa3e4-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="fa3e4-117">Data Item Name</span></span>|<span data-ttu-id="fa3e4-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="fa3e4-118">Data Item Type</span></span>|<span data-ttu-id="fa3e4-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa3e4-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="fa3e4-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="fa3e4-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="fa3e4-121">Çağrılan Denetçisi'nin türü CLR tam adı.</span><span class="sxs-lookup"><span data-stu-id="fa3e4-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="fa3e4-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="fa3e4-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="fa3e4-123">Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fa3e4-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="fa3e4-124">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="fa3e4-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="fa3e4-125">Örnek: ' varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="fa3e4-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="fa3e4-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="fa3e4-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="fa3e4-127">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="fa3e4-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
