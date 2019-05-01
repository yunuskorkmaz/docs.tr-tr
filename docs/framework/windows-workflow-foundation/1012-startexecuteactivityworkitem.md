---
title: 1012 - StartExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 29e9b1c6-c5d7-4b58-b59d-a06a923d3c80
ms.openlocfilehash: d6b330bc454c39584e5027f757fd9d9d3434d941
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924585"
---
# <a name="1012---startexecuteactivityworkitem"></a><span data-ttu-id="a4024-102">1012 - StartExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="a4024-102">1012 - StartExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="a4024-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a4024-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a4024-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="a4024-104">ID</span></span>|<span data-ttu-id="a4024-105">1012</span><span class="sxs-lookup"><span data-stu-id="a4024-105">1012</span></span>|  
|<span data-ttu-id="a4024-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="a4024-106">Keywords</span></span>|<span data-ttu-id="a4024-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="a4024-107">WFRuntime</span></span>|  
|<span data-ttu-id="a4024-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="a4024-108">Level</span></span>|<span data-ttu-id="a4024-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="a4024-109">Verbose</span></span>|  
|<span data-ttu-id="a4024-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="a4024-110">Channel</span></span>|<span data-ttu-id="a4024-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="a4024-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a4024-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4024-112">Description</span></span>  
 <span data-ttu-id="a4024-113">Bir ExecuteActivityWorkItem yürütme başlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a4024-113">Indicates an ExecuteActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a4024-114">İleti</span><span class="sxs-lookup"><span data-stu-id="a4024-114">Message</span></span>  
 <span data-ttu-id="a4024-115">'%1', DisplayName etkinliği için bir ExecuteActivityWorkItem yürütülmesi başlatılıyor: '%2', InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="a4024-115">Starting execution of an ExecuteActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a4024-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="a4024-116">Details</span></span>  
  
|<span data-ttu-id="a4024-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="a4024-117">Data Item Name</span></span>|<span data-ttu-id="a4024-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="a4024-118">Data Item Type</span></span>|<span data-ttu-id="a4024-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4024-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a4024-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="a4024-120">Activity</span></span>|<span data-ttu-id="a4024-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="a4024-121">xs:string</span></span>|<span data-ttu-id="a4024-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="a4024-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="a4024-123">displayName</span><span class="sxs-lookup"><span data-stu-id="a4024-123">DisplayName</span></span>|<span data-ttu-id="a4024-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="a4024-124">xs:string</span></span>|<span data-ttu-id="a4024-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="a4024-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="a4024-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="a4024-126">InstanceId</span></span>|<span data-ttu-id="a4024-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="a4024-127">xs:string</span></span>|<span data-ttu-id="a4024-128">Etkinlik örneği kimliği.</span><span class="sxs-lookup"><span data-stu-id="a4024-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="a4024-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a4024-129">AppDomain</span></span>|<span data-ttu-id="a4024-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="a4024-130">xs:string</span></span>|<span data-ttu-id="a4024-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="a4024-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
