---
title: 1033 - StartRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 172b5346-9f3b-46ae-bc06-39872022376a
ms.openlocfilehash: c7192ed7c5fb43fe6f65b47b8cebde3cf4aed32c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924247"
---
# <a name="1033---startruntimeworkitem"></a><span data-ttu-id="ec852-102">1033 - StartRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="ec852-102">1033 - StartRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="ec852-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ec852-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ec852-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="ec852-104">ID</span></span>|<span data-ttu-id="ec852-105">1033</span><span class="sxs-lookup"><span data-stu-id="ec852-105">1033</span></span>|  
|<span data-ttu-id="ec852-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="ec852-106">Keywords</span></span>|<span data-ttu-id="ec852-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="ec852-107">WFRuntime</span></span>|  
|<span data-ttu-id="ec852-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="ec852-108">Level</span></span>|<span data-ttu-id="ec852-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="ec852-109">Verbose</span></span>|  
|<span data-ttu-id="ec852-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="ec852-110">Channel</span></span>|<span data-ttu-id="ec852-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="ec852-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ec852-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ec852-112">Description</span></span>  
 <span data-ttu-id="ec852-113">Bir RuntimeWorkItem yürütme başlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec852-113">Indicates a RuntimeWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ec852-114">İleti</span><span class="sxs-lookup"><span data-stu-id="ec852-114">Message</span></span>  
 <span data-ttu-id="ec852-115">'%1', DisplayName etkinliği için bir çalışma zamanı iş öğesinin yürütme başlatılıyor: '%2', InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="ec852-115">Starting execution of a runtime work item for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ec852-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="ec852-116">Details</span></span>  
  
|<span data-ttu-id="ec852-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="ec852-117">Data Item Name</span></span>|<span data-ttu-id="ec852-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="ec852-118">Data Item Type</span></span>|<span data-ttu-id="ec852-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ec852-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ec852-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="ec852-120">Activity</span></span>|<span data-ttu-id="ec852-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="ec852-121">xs:string</span></span>|<span data-ttu-id="ec852-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="ec852-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="ec852-123">displayName</span><span class="sxs-lookup"><span data-stu-id="ec852-123">DisplayName</span></span>|<span data-ttu-id="ec852-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="ec852-124">xs:string</span></span>|<span data-ttu-id="ec852-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="ec852-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="ec852-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="ec852-126">InstanceId</span></span>|<span data-ttu-id="ec852-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="ec852-127">xs:string</span></span>|<span data-ttu-id="ec852-128">Etkinlik örneği kimliği.</span><span class="sxs-lookup"><span data-stu-id="ec852-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="ec852-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ec852-129">AppDomain</span></span>|<span data-ttu-id="ec852-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="ec852-130">xs:string</span></span>|<span data-ttu-id="ec852-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="ec852-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
