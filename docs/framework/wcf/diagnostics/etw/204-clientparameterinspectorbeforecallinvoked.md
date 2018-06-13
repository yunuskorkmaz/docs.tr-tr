---
title: 204 - ClientParameterInspectorBeforeCallInvoked
ms.date: 03/30/2017
ms.assetid: 8253555a-9002-4565-8ede-33d7a33a895f
ms.openlocfilehash: eb060cfa79b75452deae67705126a24b7ca9ffef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458591"
---
# <a name="204---clientparameterinspectorbeforecallinvoked"></a><span data-ttu-id="47a50-102">204 - ClientParameterInspectorBeforeCallInvoked</span><span class="sxs-lookup"><span data-stu-id="47a50-102">204 - ClientParameterInspectorBeforeCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="47a50-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="47a50-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="47a50-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="47a50-104">ID</span></span>|<span data-ttu-id="47a50-105">204</span><span class="sxs-lookup"><span data-stu-id="47a50-105">204</span></span>|  
|<span data-ttu-id="47a50-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="47a50-106">Keywords</span></span>|<span data-ttu-id="47a50-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="47a50-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="47a50-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="47a50-108">Level</span></span>|<span data-ttu-id="47a50-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="47a50-109">Information</span></span>|  
|<span data-ttu-id="47a50-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="47a50-110">Channel</span></span>|<span data-ttu-id="47a50-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="47a50-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="47a50-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="47a50-112">Description</span></span>  
 <span data-ttu-id="47a50-113">Bu olay, hizmet modeli çağrılmış sonra yayınlanır `BeforeCall` istemci parametre denetçisi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="47a50-113">This event is emitted after the Service Model has invoked the `BeforeCall` method on a client parameter inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="47a50-114">İleti</span><span class="sxs-lookup"><span data-stu-id="47a50-114">Message</span></span>  
 <span data-ttu-id="47a50-115">Dağıtıcı '%1' türünde bir ClientParameterInspector ' BeforeCall' çağrılır.</span><span class="sxs-lookup"><span data-stu-id="47a50-115">The Dispatcher invoked 'BeforeCall' on a ClientParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="47a50-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="47a50-116">Details</span></span>  
  
|<span data-ttu-id="47a50-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="47a50-117">Data Item Name</span></span>|<span data-ttu-id="47a50-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="47a50-118">Data Item Type</span></span>|<span data-ttu-id="47a50-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="47a50-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="47a50-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="47a50-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="47a50-121">Çağrılan Denetçisi'nin türü CLR tam adı.</span><span class="sxs-lookup"><span data-stu-id="47a50-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="47a50-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="47a50-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="47a50-123">Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="47a50-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="47a50-124">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="47a50-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="47a50-125">Örnek: ' varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="47a50-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="47a50-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="47a50-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="47a50-127">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="47a50-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
