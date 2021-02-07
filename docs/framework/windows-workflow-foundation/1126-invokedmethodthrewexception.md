---
description: 'Şu konuda daha fazla bilgi edinin: 1126-ınvokedmethodthrewexception'
title: 1126 - InvokedMethodThrewException
ms.date: 03/30/2017
ms.assetid: 0d3cff1a-97e6-4b6c-be18-108c6881bfc0
ms.openlocfilehash: 35c4311a4ab7750cc54a5c9ffb379f34b1cb12aa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667362"
---
# <a name="1126---invokedmethodthrewexception"></a><span data-ttu-id="06a0f-103">1126 - InvokedMethodThrewException</span><span class="sxs-lookup"><span data-stu-id="06a0f-103">1126 - InvokedMethodThrewException</span></span>

## <a name="properties"></a><span data-ttu-id="06a0f-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="06a0f-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="06a0f-105">ID</span><span class="sxs-lookup"><span data-stu-id="06a0f-105">ID</span></span>|<span data-ttu-id="06a0f-106">1126</span><span class="sxs-lookup"><span data-stu-id="06a0f-106">1126</span></span>|  
|<span data-ttu-id="06a0f-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="06a0f-107">Keywords</span></span>|<span data-ttu-id="06a0f-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="06a0f-108">WFRuntime</span></span>|  
|<span data-ttu-id="06a0f-109">Level</span><span class="sxs-lookup"><span data-stu-id="06a0f-109">Level</span></span>|<span data-ttu-id="06a0f-110">Bilgi</span><span class="sxs-lookup"><span data-stu-id="06a0f-110">Information</span></span>|  
|<span data-ttu-id="06a0f-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="06a0f-111">Channel</span></span>|<span data-ttu-id="06a0f-112">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="06a0f-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="06a0f-113">Description</span><span class="sxs-lookup"><span data-stu-id="06a0f-113">Description</span></span>  

 <span data-ttu-id="06a0f-114">InvokeMethod etkinliği tarafından çağrılan yöntem tarafından bir özel durumun oluşturulduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="06a0f-114">Indicates an exception was thrown by the method called by the InvokeMethod activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="06a0f-115">İleti</span><span class="sxs-lookup"><span data-stu-id="06a0f-115">Message</span></span>  

 <span data-ttu-id="06a0f-116">' %1 ' etkinliğinin çağırdığı yöntemde bir özel durum oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="06a0f-116">An exception was thrown in the method called by the activity '%1'.</span></span> <span data-ttu-id="06a0f-117">%2</span><span class="sxs-lookup"><span data-stu-id="06a0f-117">%2</span></span>  
  
## <a name="details"></a><span data-ttu-id="06a0f-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="06a0f-118">Details</span></span>  
  
|<span data-ttu-id="06a0f-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="06a0f-119">Data Item Name</span></span>|<span data-ttu-id="06a0f-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="06a0f-120">Data Item Type</span></span>|<span data-ttu-id="06a0f-121">Description</span><span class="sxs-lookup"><span data-stu-id="06a0f-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="06a0f-122">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="06a0f-122">InvokeMethod</span></span>|<span data-ttu-id="06a0f-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="06a0f-123">xs:string</span></span>|<span data-ttu-id="06a0f-124">InvokeMethod etkinliğinin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="06a0f-124">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="06a0f-125">Özel durum</span><span class="sxs-lookup"><span data-stu-id="06a0f-125">Exception</span></span>|<span data-ttu-id="06a0f-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="06a0f-126">xs:string</span></span>|<span data-ttu-id="06a0f-127">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="06a0f-127">The exception details for the exception</span></span>|  
|<span data-ttu-id="06a0f-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="06a0f-128">AppDomain</span></span>|<span data-ttu-id="06a0f-129">xs: String</span><span class="sxs-lookup"><span data-stu-id="06a0f-129">xs:string</span></span>|<span data-ttu-id="06a0f-130">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="06a0f-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
