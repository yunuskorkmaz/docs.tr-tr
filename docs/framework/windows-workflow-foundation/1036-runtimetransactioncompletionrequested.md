---
description: 'Hakkında daha fazla bilgi edinin: 1036-RuntimeTransactionCompletionRequested'
title: 1036 - RuntimeTransactionCompletionRequested
ms.date: 03/30/2017
ms.assetid: d36b9f44-7c0f-4083-9d3a-9034dd2b98de
ms.openlocfilehash: e07400902d5c3e08732385ab30e1be0d72d3e997
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667895"
---
# <a name="1036---runtimetransactioncompletionrequested"></a><span data-ttu-id="34567-103">1036 - RuntimeTransactionCompletionRequested</span><span class="sxs-lookup"><span data-stu-id="34567-103">1036 - RuntimeTransactionCompletionRequested</span></span>

## <a name="properties"></a><span data-ttu-id="34567-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="34567-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="34567-105">ID</span><span class="sxs-lookup"><span data-stu-id="34567-105">ID</span></span>|<span data-ttu-id="34567-106">1036</span><span class="sxs-lookup"><span data-stu-id="34567-106">1036</span></span>|  
|<span data-ttu-id="34567-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="34567-107">Keywords</span></span>|<span data-ttu-id="34567-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="34567-108">WFRuntime</span></span>|  
|<span data-ttu-id="34567-109">Level</span><span class="sxs-lookup"><span data-stu-id="34567-109">Level</span></span>|<span data-ttu-id="34567-110">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="34567-110">Verbose</span></span>|  
|<span data-ttu-id="34567-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="34567-111">Channel</span></span>|<span data-ttu-id="34567-112">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="34567-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="34567-113">Description</span><span class="sxs-lookup"><span data-stu-id="34567-113">Description</span></span>  

 <span data-ttu-id="34567-114">Bir etkinliğin çalışma zamanı işleminin tamamlandığını zamanladığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="34567-114">Indicates an activity has scheduled the completion of the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="34567-115">İleti</span><span class="sxs-lookup"><span data-stu-id="34567-115">Message</span></span>  

 <span data-ttu-id="34567-116">DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' Activity 'si çalışma zamanı işleminin tamamlanmasını zamanladı.</span><span class="sxs-lookup"><span data-stu-id="34567-116">Activity '%1', DisplayName: '%2', InstanceId: '%3' has scheduled completion of the runtime transaction.</span></span>  
  
## <a name="details"></a><span data-ttu-id="34567-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="34567-117">Details</span></span>  
  
|<span data-ttu-id="34567-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="34567-118">Data Item Name</span></span>|<span data-ttu-id="34567-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="34567-119">Data Item Type</span></span>|<span data-ttu-id="34567-120">Description</span><span class="sxs-lookup"><span data-stu-id="34567-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="34567-121">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="34567-121">Activity</span></span>|<span data-ttu-id="34567-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="34567-122">xs:string</span></span>|<span data-ttu-id="34567-123">Etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="34567-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="34567-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="34567-124">DisplayName</span></span>|<span data-ttu-id="34567-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="34567-125">xs:string</span></span>|<span data-ttu-id="34567-126">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="34567-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="34567-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="34567-127">InstanceId</span></span>|<span data-ttu-id="34567-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="34567-128">xs:string</span></span>|<span data-ttu-id="34567-129">Etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="34567-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="34567-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="34567-130">AppDomain</span></span>|<span data-ttu-id="34567-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="34567-131">xs:string</span></span>|<span data-ttu-id="34567-132">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="34567-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
