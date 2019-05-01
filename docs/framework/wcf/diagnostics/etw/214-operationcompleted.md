---
title: 214 - OperationCompleted
ms.date: 03/30/2017
ms.assetid: a6287eef-023f-4816-813c-1802c82366df
ms.openlocfilehash: da1021b674b555b683f8f745f5a2a0073c9567e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61968005"
---
# <a name="214---operationcompleted"></a><span data-ttu-id="4f42c-102">214 - OperationCompleted</span><span class="sxs-lookup"><span data-stu-id="4f42c-102">214 - OperationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="4f42c-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="4f42c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4f42c-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="4f42c-104">ID</span></span>|<span data-ttu-id="4f42c-105">214</span><span class="sxs-lookup"><span data-stu-id="4f42c-105">214</span></span>|  
|<span data-ttu-id="4f42c-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="4f42c-106">Keywords</span></span>|<span data-ttu-id="4f42c-107">EndToEndMonitoring, sorun giderme, ServiceModel ögesi</span><span class="sxs-lookup"><span data-stu-id="4f42c-107">HealthMonitoring, EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="4f42c-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="4f42c-108">Level</span></span>|<span data-ttu-id="4f42c-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="4f42c-109">Information</span></span>|  
|<span data-ttu-id="4f42c-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="4f42c-110">Channel</span></span>|<span data-ttu-id="4f42c-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="4f42c-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4f42c-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4f42c-112">Description</span></span>  
 <span data-ttu-id="4f42c-113">Bu olay yayılan olduğunda hizmet modelinin varsayılan `OperationInvoker` bir yönteme bir çağrı o yöntemi bir özel durum tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="4f42c-113">This event is emitted when the Service Model's default `OperationInvoker` has completed a call to a method without that method throwing an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4f42c-114">İleti</span><span class="sxs-lookup"><span data-stu-id="4f42c-114">Message</span></span>  
 <span data-ttu-id="4f42c-115">'%1' yöntemine çağrı bir OperationInvoker tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="4f42c-115">An OperationInvoker completed the call to the '%1' method.</span></span> <span data-ttu-id="4f42c-116">Yöntem çağrısı süresi '%2' ms idi.</span><span class="sxs-lookup"><span data-stu-id="4f42c-116">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4f42c-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="4f42c-117">Details</span></span>  
  
|<span data-ttu-id="4f42c-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="4f42c-118">Data Item Name</span></span>|<span data-ttu-id="4f42c-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="4f42c-119">Data Item Type</span></span>|<span data-ttu-id="4f42c-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4f42c-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4f42c-121">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="4f42c-121">Method Name</span></span>|`xs:string`|<span data-ttu-id="4f42c-122">CLR adı tarafından çağrılan yöntemin `OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="4f42c-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="4f42c-123">Süresi</span><span class="sxs-lookup"><span data-stu-id="4f42c-123">Duration</span></span>|`xs:long`|<span data-ttu-id="4f42c-124">Geçen milisaniye cinsinden zaman `OperationInvoker` yöntemini çağırmak için.</span><span class="sxs-lookup"><span data-stu-id="4f42c-124">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="4f42c-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="4f42c-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="4f42c-126">Bu alan, Web barındırılan hizmetleri, Web hiyerarşideki hizmet benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4f42c-126">For web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="4f42c-127">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı '.</span><span class="sxs-lookup"><span data-stu-id="4f42c-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="4f42c-128">Örnek: ' Varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="4f42c-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="4f42c-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4f42c-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="4f42c-130">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="4f42c-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
