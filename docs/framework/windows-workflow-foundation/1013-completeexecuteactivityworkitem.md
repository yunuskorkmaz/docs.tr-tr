---
title: 1013 - CompleteExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 31fc57b3-ef2f-48f0-a5de-b4e2c5c9ded7
ms.openlocfilehash: c1ff62bb4143bb798ea7adb7c3fee539ef68bc37
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509580"
---
# <a name="1013---completeexecuteactivityworkitem"></a><span data-ttu-id="4230f-102">1013 - CompleteExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="4230f-102">1013 - CompleteExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="4230f-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="4230f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4230f-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="4230f-104">ID</span></span>|<span data-ttu-id="4230f-105">1013</span><span class="sxs-lookup"><span data-stu-id="4230f-105">1013</span></span>|  
|<span data-ttu-id="4230f-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="4230f-106">Keywords</span></span>|<span data-ttu-id="4230f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="4230f-107">WFRuntime</span></span>|  
|<span data-ttu-id="4230f-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="4230f-108">Level</span></span>|<span data-ttu-id="4230f-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="4230f-109">Verbose</span></span>|  
|<span data-ttu-id="4230f-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="4230f-110">Channel</span></span>|<span data-ttu-id="4230f-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="4230f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4230f-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4230f-112">Description</span></span>  
 <span data-ttu-id="4230f-113">Bir ExecuteActivityWorkItem tamamlandığını gösterir</span><span class="sxs-lookup"><span data-stu-id="4230f-113">Indicates an ExecuteActivityWorkItem has completed</span></span>  
  
## <a name="message"></a><span data-ttu-id="4230f-114">İleti</span><span class="sxs-lookup"><span data-stu-id="4230f-114">Message</span></span>  
 <span data-ttu-id="4230f-115">'%1', DisplayName etkinliği için bir ExecuteActivityWorkItem tamamlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="4230f-115">An ExecuteActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4230f-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="4230f-116">Details</span></span>  
  
|<span data-ttu-id="4230f-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="4230f-117">Data Item Name</span></span>|<span data-ttu-id="4230f-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="4230f-118">Data Item Type</span></span>|<span data-ttu-id="4230f-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4230f-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4230f-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="4230f-120">Activity</span></span>|<span data-ttu-id="4230f-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="4230f-121">xs:string</span></span>|<span data-ttu-id="4230f-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="4230f-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="4230f-123">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="4230f-123">DisplayName</span></span>|<span data-ttu-id="4230f-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="4230f-124">xs:string</span></span>|<span data-ttu-id="4230f-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="4230f-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="4230f-126">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="4230f-126">InstanceId</span></span>|<span data-ttu-id="4230f-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="4230f-127">xs:string</span></span>|<span data-ttu-id="4230f-128">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="4230f-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="4230f-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4230f-129">AppDomain</span></span>|<span data-ttu-id="4230f-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="4230f-130">xs:string</span></span>|<span data-ttu-id="4230f-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="4230f-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
