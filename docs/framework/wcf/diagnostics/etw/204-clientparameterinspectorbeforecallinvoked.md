---
title: 204 - ClientParameterInspectorBeforeCallInvoked
ms.date: 03/30/2017
ms.assetid: 8253555a-9002-4565-8ede-33d7a33a895f
ms.openlocfilehash: a7db8c9fa87518c59969f3089ff033fa8c912577
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275794"
---
# <a name="204---clientparameterinspectorbeforecallinvoked"></a><span data-ttu-id="25961-102">204 - ClientParameterInspectorBeforeCallInvoked</span><span class="sxs-lookup"><span data-stu-id="25961-102">204 - ClientParameterInspectorBeforeCallInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="25961-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="25961-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="25961-104">ID</span><span class="sxs-lookup"><span data-stu-id="25961-104">ID</span></span>|<span data-ttu-id="25961-105">204</span><span class="sxs-lookup"><span data-stu-id="25961-105">204</span></span>|  
|<span data-ttu-id="25961-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="25961-106">Keywords</span></span>|<span data-ttu-id="25961-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="25961-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="25961-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="25961-108">Level</span></span>|<span data-ttu-id="25961-109">Bilgi</span><span class="sxs-lookup"><span data-stu-id="25961-109">Information</span></span>|  
|<span data-ttu-id="25961-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="25961-110">Channel</span></span>|<span data-ttu-id="25961-111">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="25961-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="25961-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="25961-112">Description</span></span>  

 <span data-ttu-id="25961-113">Bu olay, hizmet modeli `BeforeCall` bir istemci parametresi denetçisinde yöntemi çağırdıktan sonra yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="25961-113">This event is emitted after the Service Model has invoked the `BeforeCall` method on a client parameter inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="25961-114">İleti</span><span class="sxs-lookup"><span data-stu-id="25961-114">Message</span></span>  

 <span data-ttu-id="25961-115">Dağıtıcı, ' %1 ' türünde bir Clientparameterınspector üzerinde ' Befohatırla ' çağırdı.</span><span class="sxs-lookup"><span data-stu-id="25961-115">The Dispatcher invoked 'BeforeCall' on a ClientParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="25961-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="25961-116">Details</span></span>  
  
|<span data-ttu-id="25961-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="25961-117">Data Item Name</span></span>|<span data-ttu-id="25961-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="25961-118">Data Item Type</span></span>|<span data-ttu-id="25961-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="25961-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="25961-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="25961-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="25961-121">Çağrılan Inspector türünün CLR FullName değeri.</span><span class="sxs-lookup"><span data-stu-id="25961-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="25961-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="25961-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="25961-123">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="25961-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="25961-124">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="25961-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="25961-125">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="25961-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="25961-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="25961-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="25961-127">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="25961-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
