---
title: 1017 - ScheduleCancelActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 864546ab-d65c-4989-8fcb-537ba03a3cdd
ms.openlocfilehash: 186b012cdd554ec7dd0d195b460619cca04eddcb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510178"
---
# <a name="1017---schedulecancelactivityworkitem"></a><span data-ttu-id="42654-102">1017 - ScheduleCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="42654-102">1017 - ScheduleCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="42654-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="42654-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="42654-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="42654-104">ID</span></span>|<span data-ttu-id="42654-105">1017</span><span class="sxs-lookup"><span data-stu-id="42654-105">1017</span></span>|  
|<span data-ttu-id="42654-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="42654-106">Keywords</span></span>|<span data-ttu-id="42654-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="42654-107">WFRuntime</span></span>|  
|<span data-ttu-id="42654-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="42654-108">Level</span></span>|<span data-ttu-id="42654-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="42654-109">Verbose</span></span>|  
|<span data-ttu-id="42654-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="42654-110">Channel</span></span>|<span data-ttu-id="42654-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="42654-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="42654-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="42654-112">Description</span></span>  
 <span data-ttu-id="42654-113">Bir CancelActivityWorkItem zamanlanmış gösterir.</span><span class="sxs-lookup"><span data-stu-id="42654-113">Indicates a CancelActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="42654-114">İleti</span><span class="sxs-lookup"><span data-stu-id="42654-114">Message</span></span>  
 <span data-ttu-id="42654-115">'%1', DisplayName etkinliği için bir CancelActivityWorkItem zamanlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="42654-115">A CancelActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="42654-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="42654-116">Details</span></span>  
  
|<span data-ttu-id="42654-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="42654-117">Data Item Name</span></span>|<span data-ttu-id="42654-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="42654-118">Data Item Type</span></span>|<span data-ttu-id="42654-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="42654-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="42654-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="42654-120">Activity</span></span>|<span data-ttu-id="42654-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="42654-121">xs:string</span></span>|<span data-ttu-id="42654-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="42654-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="42654-123">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="42654-123">DisplayName</span></span>|<span data-ttu-id="42654-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="42654-124">xs:string</span></span>|<span data-ttu-id="42654-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="42654-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="42654-126">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="42654-126">InstanceId</span></span>|<span data-ttu-id="42654-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="42654-127">xs:string</span></span>|<span data-ttu-id="42654-128">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="42654-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="42654-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="42654-129">AppDomain</span></span>|<span data-ttu-id="42654-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="42654-130">xs:string</span></span>|<span data-ttu-id="42654-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="42654-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
