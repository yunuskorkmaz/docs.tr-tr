---
title: 1034 - CompleteRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 45620011-8b04-4f87-ab5a-65b24145e17d
ms.openlocfilehash: bd49c608a8f6a6caab6975850507a00a2c0edb03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509710"
---
# <a name="1034---completeruntimeworkitem"></a><span data-ttu-id="75285-102">1034 - CompleteRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="75285-102">1034 - CompleteRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="75285-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="75285-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="75285-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="75285-104">ID</span></span>|<span data-ttu-id="75285-105">1034</span><span class="sxs-lookup"><span data-stu-id="75285-105">1034</span></span>|  
|<span data-ttu-id="75285-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="75285-106">Keywords</span></span>|<span data-ttu-id="75285-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="75285-107">WFRuntime</span></span>|  
|<span data-ttu-id="75285-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="75285-108">Level</span></span>|<span data-ttu-id="75285-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="75285-109">Verbose</span></span>|  
|<span data-ttu-id="75285-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="75285-110">Channel</span></span>|<span data-ttu-id="75285-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="75285-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="75285-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75285-112">Description</span></span>  
 <span data-ttu-id="75285-113">Bir RuntimeWorkItem tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="75285-113">Indicates a RuntimeWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="75285-114">İleti</span><span class="sxs-lookup"><span data-stu-id="75285-114">Message</span></span>  
 <span data-ttu-id="75285-115">Bir çalışma zamanı iş öğesi etkinliği için '%1', DisplayName tamamlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="75285-115">A runtime work item has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="75285-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="75285-116">Details</span></span>  
  
|<span data-ttu-id="75285-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="75285-117">Data Item Name</span></span>|<span data-ttu-id="75285-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="75285-118">Data Item Type</span></span>|<span data-ttu-id="75285-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75285-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="75285-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="75285-120">Activity</span></span>|<span data-ttu-id="75285-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="75285-121">xs:string</span></span>|<span data-ttu-id="75285-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="75285-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="75285-123">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="75285-123">DisplayName</span></span>|<span data-ttu-id="75285-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="75285-124">xs:string</span></span>|<span data-ttu-id="75285-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="75285-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="75285-126">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="75285-126">InstanceId</span></span>|<span data-ttu-id="75285-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="75285-127">xs:string</span></span>|<span data-ttu-id="75285-128">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="75285-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="75285-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="75285-129">AppDomain</span></span>|<span data-ttu-id="75285-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="75285-130">xs:string</span></span>|<span data-ttu-id="75285-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="75285-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
