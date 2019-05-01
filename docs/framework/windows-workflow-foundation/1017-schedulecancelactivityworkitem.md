---
title: 1017 - ScheduleCancelActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 864546ab-d65c-4989-8fcb-537ba03a3cdd
ms.openlocfilehash: 186b012cdd554ec7dd0d195b460619cca04eddcb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924494"
---
# <a name="1017---schedulecancelactivityworkitem"></a><span data-ttu-id="21118-102">1017 - ScheduleCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="21118-102">1017 - ScheduleCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="21118-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="21118-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="21118-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="21118-104">ID</span></span>|<span data-ttu-id="21118-105">1017</span><span class="sxs-lookup"><span data-stu-id="21118-105">1017</span></span>|  
|<span data-ttu-id="21118-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="21118-106">Keywords</span></span>|<span data-ttu-id="21118-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="21118-107">WFRuntime</span></span>|  
|<span data-ttu-id="21118-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="21118-108">Level</span></span>|<span data-ttu-id="21118-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="21118-109">Verbose</span></span>|  
|<span data-ttu-id="21118-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="21118-110">Channel</span></span>|<span data-ttu-id="21118-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="21118-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="21118-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21118-112">Description</span></span>  
 <span data-ttu-id="21118-113">Bir CancelActivityWorkItem zamanlandı gösterir.</span><span class="sxs-lookup"><span data-stu-id="21118-113">Indicates a CancelActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="21118-114">İleti</span><span class="sxs-lookup"><span data-stu-id="21118-114">Message</span></span>  
 <span data-ttu-id="21118-115">'%1', DisplayName etkinliği için bir CancelActivityWorkItem zamanlandı: '%2', InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="21118-115">A CancelActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="21118-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="21118-116">Details</span></span>  
  
|<span data-ttu-id="21118-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="21118-117">Data Item Name</span></span>|<span data-ttu-id="21118-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="21118-118">Data Item Type</span></span>|<span data-ttu-id="21118-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21118-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="21118-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="21118-120">Activity</span></span>|<span data-ttu-id="21118-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="21118-121">xs:string</span></span>|<span data-ttu-id="21118-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="21118-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="21118-123">displayName</span><span class="sxs-lookup"><span data-stu-id="21118-123">DisplayName</span></span>|<span data-ttu-id="21118-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="21118-124">xs:string</span></span>|<span data-ttu-id="21118-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="21118-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="21118-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="21118-126">InstanceId</span></span>|<span data-ttu-id="21118-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="21118-127">xs:string</span></span>|<span data-ttu-id="21118-128">Etkinlik örneği kimliği.</span><span class="sxs-lookup"><span data-stu-id="21118-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="21118-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="21118-129">AppDomain</span></span>|<span data-ttu-id="21118-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="21118-130">xs:string</span></span>|<span data-ttu-id="21118-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="21118-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
