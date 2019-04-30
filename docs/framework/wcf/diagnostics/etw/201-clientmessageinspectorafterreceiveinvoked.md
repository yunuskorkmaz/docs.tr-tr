---
title: 201 - ClientMessageInspectorAfterReceiveInvoked
ms.date: 03/30/2017
ms.assetid: 9ff637f1-cc26-4400-ab9b-546f70e5057d
ms.openlocfilehash: 96ca318c141d49e2ac5594d5ee101658a2aa8f21
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782045"
---
# <a name="201---clientmessageinspectorafterreceiveinvoked"></a><span data-ttu-id="68dd5-102">201 - ClientMessageInspectorAfterReceiveInvoked</span><span class="sxs-lookup"><span data-stu-id="68dd5-102">201 - ClientMessageInspectorAfterReceiveInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="68dd5-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="68dd5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="68dd5-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="68dd5-104">ID</span></span>|<span data-ttu-id="68dd5-105">201</span><span class="sxs-lookup"><span data-stu-id="68dd5-105">201</span></span>|  
|<span data-ttu-id="68dd5-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="68dd5-106">Keywords</span></span>|<span data-ttu-id="68dd5-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="68dd5-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="68dd5-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="68dd5-108">Level</span></span>|<span data-ttu-id="68dd5-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="68dd5-109">Information</span></span>|  
|<span data-ttu-id="68dd5-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="68dd5-110">Channel</span></span>|<span data-ttu-id="68dd5-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="68dd5-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="68dd5-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="68dd5-112">Description</span></span>  
 <span data-ttu-id="68dd5-113">Bu olay, hizmet modeli çağırdığı sonra yayıldığını `AfterReceiveReply` istemci ileti denetçisi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="68dd5-113">This event is emitted after the Service Model has invoked the `AfterReceiveReply` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="68dd5-114">İleti</span><span class="sxs-lookup"><span data-stu-id="68dd5-114">Message</span></span>  
 <span data-ttu-id="68dd5-115">Dağıtıcı 'AfterReceiveReply' üzerinde '%1' türünde bir ClientMessageInspector çağrılır.</span><span class="sxs-lookup"><span data-stu-id="68dd5-115">The Dispatcher invoked 'AfterReceiveReply' on a ClientMessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="68dd5-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="68dd5-116">Details</span></span>  
  
|<span data-ttu-id="68dd5-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="68dd5-117">Data Item Name</span></span>|<span data-ttu-id="68dd5-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="68dd5-118">Data Item Type</span></span>|<span data-ttu-id="68dd5-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="68dd5-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="68dd5-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="68dd5-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="68dd5-121">CLR FullName çağrılan denetçisinin türü.</span><span class="sxs-lookup"><span data-stu-id="68dd5-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="68dd5-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="68dd5-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="68dd5-123">Bu alan, Web barındırılan hizmetleri, Web hiyerarşideki hizmet benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="68dd5-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="68dd5-124">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı '.</span><span class="sxs-lookup"><span data-stu-id="68dd5-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="68dd5-125">Örnek: ' Varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="68dd5-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="68dd5-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="68dd5-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="68dd5-127">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="68dd5-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
