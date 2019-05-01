---
title: 1013 - CompleteExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 31fc57b3-ef2f-48f0-a5de-b4e2c5c9ded7
ms.openlocfilehash: c1ff62bb4143bb798ea7adb7c3fee539ef68bc37
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925196"
---
# <a name="1013---completeexecuteactivityworkitem"></a><span data-ttu-id="d859b-102">1013 - CompleteExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="d859b-102">1013 - CompleteExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="d859b-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d859b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d859b-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="d859b-104">ID</span></span>|<span data-ttu-id="d859b-105">1013</span><span class="sxs-lookup"><span data-stu-id="d859b-105">1013</span></span>|  
|<span data-ttu-id="d859b-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="d859b-106">Keywords</span></span>|<span data-ttu-id="d859b-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="d859b-107">WFRuntime</span></span>|  
|<span data-ttu-id="d859b-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="d859b-108">Level</span></span>|<span data-ttu-id="d859b-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="d859b-109">Verbose</span></span>|  
|<span data-ttu-id="d859b-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="d859b-110">Channel</span></span>|<span data-ttu-id="d859b-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="d859b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d859b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d859b-112">Description</span></span>  
 <span data-ttu-id="d859b-113">Bir ExecuteActivityWorkItem tamamlandığını gösterir</span><span class="sxs-lookup"><span data-stu-id="d859b-113">Indicates an ExecuteActivityWorkItem has completed</span></span>  
  
## <a name="message"></a><span data-ttu-id="d859b-114">İleti</span><span class="sxs-lookup"><span data-stu-id="d859b-114">Message</span></span>  
 <span data-ttu-id="d859b-115">'%1', DisplayName etkinliği için bir ExecuteActivityWorkItem tamamlandı: '%2', InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="d859b-115">An ExecuteActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d859b-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="d859b-116">Details</span></span>  
  
|<span data-ttu-id="d859b-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="d859b-117">Data Item Name</span></span>|<span data-ttu-id="d859b-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="d859b-118">Data Item Type</span></span>|<span data-ttu-id="d859b-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d859b-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d859b-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="d859b-120">Activity</span></span>|<span data-ttu-id="d859b-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="d859b-121">xs:string</span></span>|<span data-ttu-id="d859b-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="d859b-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="d859b-123">displayName</span><span class="sxs-lookup"><span data-stu-id="d859b-123">DisplayName</span></span>|<span data-ttu-id="d859b-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="d859b-124">xs:string</span></span>|<span data-ttu-id="d859b-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="d859b-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="d859b-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="d859b-126">InstanceId</span></span>|<span data-ttu-id="d859b-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="d859b-127">xs:string</span></span>|<span data-ttu-id="d859b-128">Etkinlik örneği kimliği.</span><span class="sxs-lookup"><span data-stu-id="d859b-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="d859b-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d859b-129">AppDomain</span></span>|<span data-ttu-id="d859b-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="d859b-130">xs:string</span></span>|<span data-ttu-id="d859b-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="d859b-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
