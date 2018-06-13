---
title: 201 - ClientMessageInspectorAfterReceiveInvoked
ms.date: 03/30/2017
ms.assetid: 9ff637f1-cc26-4400-ab9b-546f70e5057d
ms.openlocfilehash: 96ca318c141d49e2ac5594d5ee101658a2aa8f21
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459030"
---
# <a name="201---clientmessageinspectorafterreceiveinvoked"></a><span data-ttu-id="f5030-102">201 - ClientMessageInspectorAfterReceiveInvoked</span><span class="sxs-lookup"><span data-stu-id="f5030-102">201 - ClientMessageInspectorAfterReceiveInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="f5030-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f5030-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f5030-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="f5030-104">ID</span></span>|<span data-ttu-id="f5030-105">201</span><span class="sxs-lookup"><span data-stu-id="f5030-105">201</span></span>|  
|<span data-ttu-id="f5030-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="f5030-106">Keywords</span></span>|<span data-ttu-id="f5030-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f5030-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="f5030-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="f5030-108">Level</span></span>|<span data-ttu-id="f5030-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="f5030-109">Information</span></span>|  
|<span data-ttu-id="f5030-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="f5030-110">Channel</span></span>|<span data-ttu-id="f5030-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="f5030-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f5030-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f5030-112">Description</span></span>  
 <span data-ttu-id="f5030-113">Bu olay, hizmet modeli çağrılmış sonra yayınlanır `AfterReceiveReply` istemci ileti denetçisi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f5030-113">This event is emitted after the Service Model has invoked the `AfterReceiveReply` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f5030-114">İleti</span><span class="sxs-lookup"><span data-stu-id="f5030-114">Message</span></span>  
 <span data-ttu-id="f5030-115">Dağıtıcı '%1' türünde bir ClientMessageInspector ' AfterReceiveReply' çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f5030-115">The Dispatcher invoked 'AfterReceiveReply' on a ClientMessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f5030-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f5030-116">Details</span></span>  
  
|<span data-ttu-id="f5030-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="f5030-117">Data Item Name</span></span>|<span data-ttu-id="f5030-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="f5030-118">Data Item Type</span></span>|<span data-ttu-id="f5030-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f5030-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f5030-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="f5030-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="f5030-121">Çağrılan Denetçisi'nin türü CLR tam adı.</span><span class="sxs-lookup"><span data-stu-id="f5030-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="f5030-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="f5030-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="f5030-123">Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f5030-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="f5030-124">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="f5030-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="f5030-125">Örnek: ' varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="f5030-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="f5030-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f5030-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="f5030-127">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="f5030-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
