---
title: 203 - ClientParameterInspectorAfterCallInvoked
ms.date: 03/30/2017
ms.assetid: b9592212-07e2-43e0-8b00-affd195cf55a
ms.openlocfilehash: 57192b44a0c3babc77fcca13ad4a1433b85bfdd7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781946"
---
# <a name="203---clientparameterinspectoraftercallinvoked"></a><span data-ttu-id="b7a47-102">203 - ClientParameterInspectorAfterCallInvoked</span><span class="sxs-lookup"><span data-stu-id="b7a47-102">203 - ClientParameterInspectorAfterCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="b7a47-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="b7a47-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b7a47-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="b7a47-104">ID</span></span>|<span data-ttu-id="b7a47-105">203</span><span class="sxs-lookup"><span data-stu-id="b7a47-105">203</span></span>|  
|<span data-ttu-id="b7a47-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="b7a47-106">Keywords</span></span>|<span data-ttu-id="b7a47-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b7a47-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="b7a47-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="b7a47-108">Level</span></span>|<span data-ttu-id="b7a47-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="b7a47-109">Information</span></span>|  
|<span data-ttu-id="b7a47-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="b7a47-110">Channel</span></span>|<span data-ttu-id="b7a47-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="b7a47-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b7a47-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b7a47-112">Description</span></span>  
 <span data-ttu-id="b7a47-113">Bu olay, hizmet modeli çağırdığı sonra yayıldığını `AfterCall` istemci parametresi denetçisi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b7a47-113">This event is emitted after the Service Model has invoked the `AfterCall` method on a client parameter inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b7a47-114">İleti</span><span class="sxs-lookup"><span data-stu-id="b7a47-114">Message</span></span>  
 <span data-ttu-id="b7a47-115">Dağıtıcı 'AfterCall' üzerinde '%1' türünde bir ClientParameterInspector çağrılır.</span><span class="sxs-lookup"><span data-stu-id="b7a47-115">The Dispatcher invoked 'AfterCall' on a ClientParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b7a47-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b7a47-116">Details</span></span>  
  
|<span data-ttu-id="b7a47-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="b7a47-117">Data Item Name</span></span>|<span data-ttu-id="b7a47-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="b7a47-118">Data Item Type</span></span>|<span data-ttu-id="b7a47-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b7a47-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b7a47-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="b7a47-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="b7a47-121">CLR FullName çağrılan denetçisinin türü.</span><span class="sxs-lookup"><span data-stu-id="b7a47-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="b7a47-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="b7a47-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="b7a47-123">Bu alan, Web barındırılan hizmetleri, Web hiyerarşideki hizmet benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b7a47-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="b7a47-124">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı '.</span><span class="sxs-lookup"><span data-stu-id="b7a47-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="b7a47-125">Örnek: ' Varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="b7a47-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="b7a47-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b7a47-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="b7a47-127">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="b7a47-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
