---
title: 401- StopSignPostEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e033d03a-510d-4300-aa65-ef02cb4807f2
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 058cae31c70e2c415e27870af1a0064b84a70b12
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="401--stopsignpostevent"></a><span data-ttu-id="9c7c6-102">401- StopSignPostEvent</span><span class="sxs-lookup"><span data-stu-id="9c7c6-102">401- StopSignPostEvent</span></span>
## <a name="properties"></a><span data-ttu-id="9c7c6-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="9c7c6-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9c7c6-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="9c7c6-104">ID</span></span>|<span data-ttu-id="9c7c6-105">401</span><span class="sxs-lookup"><span data-stu-id="9c7c6-105">401</span></span>|  
|<span data-ttu-id="9c7c6-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="9c7c6-106">Keywords</span></span>|<span data-ttu-id="9c7c6-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="9c7c6-107">Troubleshooting</span></span>|  
|<span data-ttu-id="9c7c6-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="9c7c6-108">Level</span></span>|<span data-ttu-id="9c7c6-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="9c7c6-109">Information</span></span>|  
|<span data-ttu-id="9c7c6-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="9c7c6-110">Channel</span></span>|<span data-ttu-id="9c7c6-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="9c7c6-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9c7c6-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9c7c6-112">Description</span></span>  
 <span data-ttu-id="9c7c6-113">Bu olay, uçtan uca Etkinliğin sonunu işaretler.</span><span class="sxs-lookup"><span data-stu-id="9c7c6-113">This event marks the end of an end-to-end activity.</span></span> <span data-ttu-id="9c7c6-114">Bu etkinliğin adını içerir.</span><span class="sxs-lookup"><span data-stu-id="9c7c6-114">It contains the name of the activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9c7c6-115">İleti</span><span class="sxs-lookup"><span data-stu-id="9c7c6-115">Message</span></span>  
 <span data-ttu-id="9c7c6-116">Etkinlik sınırı.</span><span class="sxs-lookup"><span data-stu-id="9c7c6-116">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9c7c6-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="9c7c6-117">Details</span></span>  
  
|<span data-ttu-id="9c7c6-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="9c7c6-118">Data Item Name</span></span>|<span data-ttu-id="9c7c6-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="9c7c6-119">Data Item Type</span></span>|<span data-ttu-id="9c7c6-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9c7c6-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9c7c6-121">Genişletilmiş verileri</span><span class="sxs-lookup"><span data-stu-id="9c7c6-121">Extended Data</span></span>|`xs:string`|<span data-ttu-id="9c7c6-122">Etkinlik adı.</span><span class="sxs-lookup"><span data-stu-id="9c7c6-122">The name of the activity.</span></span>|  
|<span data-ttu-id="9c7c6-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9c7c6-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="9c7c6-124">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="9c7c6-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
