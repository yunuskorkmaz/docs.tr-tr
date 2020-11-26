---
title: 1012 - StartExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 29e9b1c6-c5d7-4b58-b59d-a06a923d3c80
ms.openlocfilehash: b9cfceb12d56f93c0f9726849e34f4333f1399ac
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239646"
---
# <a name="1012---startexecuteactivityworkitem"></a><span data-ttu-id="64d59-102">1012 - StartExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="64d59-102">1012 - StartExecuteActivityWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="64d59-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="64d59-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="64d59-104">ID</span><span class="sxs-lookup"><span data-stu-id="64d59-104">ID</span></span>|<span data-ttu-id="64d59-105">1012</span><span class="sxs-lookup"><span data-stu-id="64d59-105">1012</span></span>|  
|<span data-ttu-id="64d59-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="64d59-106">Keywords</span></span>|<span data-ttu-id="64d59-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="64d59-107">WFRuntime</span></span>|  
|<span data-ttu-id="64d59-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="64d59-108">Level</span></span>|<span data-ttu-id="64d59-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="64d59-109">Verbose</span></span>|  
|<span data-ttu-id="64d59-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="64d59-110">Channel</span></span>|<span data-ttu-id="64d59-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="64d59-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="64d59-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="64d59-112">Description</span></span>  

 <span data-ttu-id="64d59-113">Bir ExecuteActivityWorkItem 'ın yürütmeyi başlatdığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="64d59-113">Indicates an ExecuteActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="64d59-114">İleti</span><span class="sxs-lookup"><span data-stu-id="64d59-114">Message</span></span>  

 <span data-ttu-id="64d59-115">DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' Activity 'si için bir ExecuteActivityWorkItem 'ın yürütülmesi başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="64d59-115">Starting execution of an ExecuteActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="64d59-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="64d59-116">Details</span></span>  
  
|<span data-ttu-id="64d59-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="64d59-117">Data Item Name</span></span>|<span data-ttu-id="64d59-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="64d59-118">Data Item Type</span></span>|<span data-ttu-id="64d59-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="64d59-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="64d59-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="64d59-120">Activity</span></span>|<span data-ttu-id="64d59-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="64d59-121">xs:string</span></span>|<span data-ttu-id="64d59-122">Etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="64d59-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="64d59-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="64d59-123">DisplayName</span></span>|<span data-ttu-id="64d59-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="64d59-124">xs:string</span></span>|<span data-ttu-id="64d59-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="64d59-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="64d59-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="64d59-126">InstanceId</span></span>|<span data-ttu-id="64d59-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="64d59-127">xs:string</span></span>|<span data-ttu-id="64d59-128">Etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="64d59-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="64d59-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="64d59-129">AppDomain</span></span>|<span data-ttu-id="64d59-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="64d59-130">xs:string</span></span>|<span data-ttu-id="64d59-131">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="64d59-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
