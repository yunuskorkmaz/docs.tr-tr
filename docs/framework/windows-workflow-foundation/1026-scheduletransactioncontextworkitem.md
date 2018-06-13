---
title: 1026 - ScheduleTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 0d5f86ba-ec21-4129-a726-5432e425384c
ms.openlocfilehash: 6d0b43208f86c52e8863d4415a64466b0531832c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510289"
---
# <a name="1026---scheduletransactioncontextworkitem"></a><span data-ttu-id="4e5e9-102">1026 - ScheduleTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="4e5e9-102">1026 - ScheduleTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="4e5e9-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="4e5e9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4e5e9-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="4e5e9-104">ID</span></span>|<span data-ttu-id="4e5e9-105">1026</span><span class="sxs-lookup"><span data-stu-id="4e5e9-105">1026</span></span>|  
|<span data-ttu-id="4e5e9-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="4e5e9-106">Keywords</span></span>|<span data-ttu-id="4e5e9-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="4e5e9-107">WFRuntime</span></span>|  
|<span data-ttu-id="4e5e9-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="4e5e9-108">Level</span></span>|<span data-ttu-id="4e5e9-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="4e5e9-109">Verbose</span></span>|  
|<span data-ttu-id="4e5e9-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="4e5e9-110">Channel</span></span>|<span data-ttu-id="4e5e9-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="4e5e9-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4e5e9-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4e5e9-112">Description</span></span>  
 <span data-ttu-id="4e5e9-113">Bir TransactionContextWorkItem zamanlanmış gösterir.</span><span class="sxs-lookup"><span data-stu-id="4e5e9-113">Indicates a TransactionContextWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4e5e9-114">İleti</span><span class="sxs-lookup"><span data-stu-id="4e5e9-114">Message</span></span>  
 <span data-ttu-id="4e5e9-115">'%1', DisplayName etkinliği için bir TransactionContextWorkItem zamanlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="4e5e9-115">A TransactionContextWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4e5e9-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="4e5e9-116">Details</span></span>  
  
|<span data-ttu-id="4e5e9-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="4e5e9-117">Data Item Name</span></span>|<span data-ttu-id="4e5e9-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="4e5e9-118">Data Item Type</span></span>|<span data-ttu-id="4e5e9-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4e5e9-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4e5e9-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="4e5e9-120">Activity</span></span>|<span data-ttu-id="4e5e9-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="4e5e9-121">xs:string</span></span>|<span data-ttu-id="4e5e9-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="4e5e9-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="4e5e9-123">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="4e5e9-123">DisplayName</span></span>|<span data-ttu-id="4e5e9-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="4e5e9-124">xs:string</span></span>|<span data-ttu-id="4e5e9-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="4e5e9-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="4e5e9-126">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="4e5e9-126">InstanceId</span></span>|<span data-ttu-id="4e5e9-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="4e5e9-127">xs:string</span></span>|<span data-ttu-id="4e5e9-128">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="4e5e9-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="4e5e9-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4e5e9-129">AppDomain</span></span>|<span data-ttu-id="4e5e9-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="4e5e9-130">xs:string</span></span>|<span data-ttu-id="4e5e9-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="4e5e9-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
