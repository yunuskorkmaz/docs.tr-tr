---
title: 1018 - StartCancelActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 68b4fa1d-eee6-4a2a-8c16-7e9d89f08ab9
ms.openlocfilehash: 8d7045b0a7f31ecfd5dd90f319192bd202804353
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008869"
---
# <a name="1018---startcancelactivityworkitem"></a><span data-ttu-id="80171-102">1018 - StartCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="80171-102">1018 - StartCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="80171-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="80171-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="80171-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="80171-104">ID</span></span>|<span data-ttu-id="80171-105">1018</span><span class="sxs-lookup"><span data-stu-id="80171-105">1018</span></span>|  
|<span data-ttu-id="80171-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="80171-106">Keywords</span></span>|<span data-ttu-id="80171-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="80171-107">WFRuntime</span></span>|  
|<span data-ttu-id="80171-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="80171-108">Level</span></span>|<span data-ttu-id="80171-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="80171-109">Verbose</span></span>|  
|<span data-ttu-id="80171-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="80171-110">Channel</span></span>|<span data-ttu-id="80171-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="80171-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="80171-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80171-112">Description</span></span>  
 <span data-ttu-id="80171-113">Bir CancelActivityWorkItem yürütme başlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="80171-113">Indicates a CancelActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="80171-114">İleti</span><span class="sxs-lookup"><span data-stu-id="80171-114">Message</span></span>  
 <span data-ttu-id="80171-115">'%1', DisplayName etkinliği için bir CancelActivityWorkItem yürütülmesi başlatılıyor: '%2', InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="80171-115">Starting execution of a CancelActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="80171-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="80171-116">Details</span></span>  
  
|<span data-ttu-id="80171-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="80171-117">Data Item Name</span></span>|<span data-ttu-id="80171-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="80171-118">Data Item Type</span></span>|<span data-ttu-id="80171-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80171-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="80171-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="80171-120">Activity</span></span>|<span data-ttu-id="80171-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="80171-121">xs:string</span></span>|<span data-ttu-id="80171-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="80171-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="80171-123">displayName</span><span class="sxs-lookup"><span data-stu-id="80171-123">DisplayName</span></span>|<span data-ttu-id="80171-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="80171-124">xs:string</span></span>|<span data-ttu-id="80171-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="80171-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="80171-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="80171-126">InstanceId</span></span>|<span data-ttu-id="80171-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="80171-127">xs:string</span></span>|<span data-ttu-id="80171-128">Etkinlik örneği kimliği.</span><span class="sxs-lookup"><span data-stu-id="80171-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="80171-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="80171-129">AppDomain</span></span>|<span data-ttu-id="80171-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="80171-130">xs:string</span></span>|<span data-ttu-id="80171-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="80171-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
