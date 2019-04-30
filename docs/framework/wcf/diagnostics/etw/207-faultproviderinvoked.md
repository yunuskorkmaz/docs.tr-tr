---
title: 207 - FaultProviderInvoked
ms.date: 03/30/2017
ms.assetid: b730d903-01c2-4deb-85a4-da12f8a21fe4
ms.openlocfilehash: 9f97e74e7685d57b487f456625826ee9cd8e1760
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781920"
---
# <a name="207---faultproviderinvoked"></a><span data-ttu-id="49e31-102">207 - FaultProviderInvoked</span><span class="sxs-lookup"><span data-stu-id="49e31-102">207 - FaultProviderInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="49e31-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="49e31-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="49e31-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="49e31-104">ID</span></span>|<span data-ttu-id="49e31-105">207</span><span class="sxs-lookup"><span data-stu-id="49e31-105">207</span></span>|  
|<span data-ttu-id="49e31-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="49e31-106">Keywords</span></span>|<span data-ttu-id="49e31-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="49e31-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="49e31-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="49e31-108">Level</span></span>|<span data-ttu-id="49e31-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="49e31-109">Information</span></span>|  
|<span data-ttu-id="49e31-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="49e31-110">Channel</span></span>|<span data-ttu-id="49e31-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="49e31-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="49e31-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="49e31-112">Description</span></span>  
 <span data-ttu-id="49e31-113">Bu olay sonra yayılan bir `FaultProvider` çağrılmış.</span><span class="sxs-lookup"><span data-stu-id="49e31-113">This event is emitted after a `FaultProvider` has been invoked.</span></span>  
  
## <a name="message"></a><span data-ttu-id="49e31-114">İleti</span><span class="sxs-lookup"><span data-stu-id="49e31-114">Message</span></span>  
 <span data-ttu-id="49e31-115">Dağıtıcı '%2' türünde bir özel durum ile '%1' türünde bir FaultProvider çağrılır.</span><span class="sxs-lookup"><span data-stu-id="49e31-115">The Dispatcher invoked a FaultProvider of type '%1' with an exception of type '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="49e31-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="49e31-116">Details</span></span>  
  
|<span data-ttu-id="49e31-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="49e31-117">Data Item Name</span></span>|<span data-ttu-id="49e31-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="49e31-118">Data Item Type</span></span>|<span data-ttu-id="49e31-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="49e31-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="49e31-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="49e31-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="49e31-121">Çağrılan türünün CLR FullName `FaultProvider`.</span><span class="sxs-lookup"><span data-stu-id="49e31-121">The CLR FullName of the type of the invoked `FaultProvider`.</span></span>|  
|<span data-ttu-id="49e31-122">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="49e31-122">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="49e31-123">Özel durumun CLR FullName, `FaultProvider` işletilen.</span><span class="sxs-lookup"><span data-stu-id="49e31-123">The CLR FullName of the exception that the `FaultProvider` has operated on.</span></span>|  
|<span data-ttu-id="49e31-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="49e31-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="49e31-125">Bu alan, Web barındırılan hizmetleri, Web hiyerarşideki hizmet benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="49e31-125">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="49e31-126">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı '.</span><span class="sxs-lookup"><span data-stu-id="49e31-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="49e31-127">Örnek: ' Varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="49e31-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="49e31-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="49e31-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="49e31-129">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="49e31-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
