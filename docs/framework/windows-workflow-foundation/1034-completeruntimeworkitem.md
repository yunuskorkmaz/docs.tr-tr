---
title: 1034 - CompleteRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 45620011-8b04-4f87-ab5a-65b24145e17d
ms.openlocfilehash: bd49c608a8f6a6caab6975850507a00a2c0edb03
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924559"
---
# <a name="1034---completeruntimeworkitem"></a><span data-ttu-id="2f961-102">1034 - CompleteRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="2f961-102">1034 - CompleteRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="2f961-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="2f961-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2f961-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="2f961-104">ID</span></span>|<span data-ttu-id="2f961-105">1034</span><span class="sxs-lookup"><span data-stu-id="2f961-105">1034</span></span>|  
|<span data-ttu-id="2f961-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="2f961-106">Keywords</span></span>|<span data-ttu-id="2f961-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="2f961-107">WFRuntime</span></span>|  
|<span data-ttu-id="2f961-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="2f961-108">Level</span></span>|<span data-ttu-id="2f961-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="2f961-109">Verbose</span></span>|  
|<span data-ttu-id="2f961-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="2f961-110">Channel</span></span>|<span data-ttu-id="2f961-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="2f961-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2f961-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2f961-112">Description</span></span>  
 <span data-ttu-id="2f961-113">Bir RuntimeWorkItem tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2f961-113">Indicates a RuntimeWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2f961-114">İleti</span><span class="sxs-lookup"><span data-stu-id="2f961-114">Message</span></span>  
 <span data-ttu-id="2f961-115">'%1', DisplayName etkinliği için bir çalışma zamanı iş öğesi tamamlandı: '%2', InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="2f961-115">A runtime work item has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2f961-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="2f961-116">Details</span></span>  
  
|<span data-ttu-id="2f961-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="2f961-117">Data Item Name</span></span>|<span data-ttu-id="2f961-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="2f961-118">Data Item Type</span></span>|<span data-ttu-id="2f961-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2f961-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2f961-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="2f961-120">Activity</span></span>|<span data-ttu-id="2f961-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="2f961-121">xs:string</span></span>|<span data-ttu-id="2f961-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="2f961-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="2f961-123">displayName</span><span class="sxs-lookup"><span data-stu-id="2f961-123">DisplayName</span></span>|<span data-ttu-id="2f961-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="2f961-124">xs:string</span></span>|<span data-ttu-id="2f961-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="2f961-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="2f961-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="2f961-126">InstanceId</span></span>|<span data-ttu-id="2f961-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="2f961-127">xs:string</span></span>|<span data-ttu-id="2f961-128">Etkinlik örneği kimliği.</span><span class="sxs-lookup"><span data-stu-id="2f961-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="2f961-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2f961-129">AppDomain</span></span>|<span data-ttu-id="2f961-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="2f961-130">xs:string</span></span>|<span data-ttu-id="2f961-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="2f961-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
