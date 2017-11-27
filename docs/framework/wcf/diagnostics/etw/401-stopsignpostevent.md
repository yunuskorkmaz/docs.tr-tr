---
title: 401- StopSignPostEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e033d03a-510d-4300-aa65-ef02cb4807f2
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 31cd94e2c988d614babc1e0c203316b41e01f5bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="401--stopsignpostevent"></a><span data-ttu-id="079c0-102">401- StopSignPostEvent</span><span class="sxs-lookup"><span data-stu-id="079c0-102">401- StopSignPostEvent</span></span>
## <a name="properties"></a><span data-ttu-id="079c0-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="079c0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="079c0-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="079c0-104">ID</span></span>|<span data-ttu-id="079c0-105">401</span><span class="sxs-lookup"><span data-stu-id="079c0-105">401</span></span>|  
|<span data-ttu-id="079c0-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="079c0-106">Keywords</span></span>|<span data-ttu-id="079c0-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="079c0-107">Troubleshooting</span></span>|  
|<span data-ttu-id="079c0-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="079c0-108">Level</span></span>|<span data-ttu-id="079c0-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="079c0-109">Information</span></span>|  
|<span data-ttu-id="079c0-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="079c0-110">Channel</span></span>|<span data-ttu-id="079c0-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="079c0-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="079c0-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="079c0-112">Description</span></span>  
 <span data-ttu-id="079c0-113">Bu olay, uçtan uca Etkinliğin sonunu işaretler.</span><span class="sxs-lookup"><span data-stu-id="079c0-113">This event marks the end of an end-to-end activity.</span></span> <span data-ttu-id="079c0-114">Bu etkinliğin adını içerir.</span><span class="sxs-lookup"><span data-stu-id="079c0-114">It contains the name of the activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="079c0-115">İleti</span><span class="sxs-lookup"><span data-stu-id="079c0-115">Message</span></span>  
 <span data-ttu-id="079c0-116">Etkinlik sınırı.</span><span class="sxs-lookup"><span data-stu-id="079c0-116">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="079c0-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="079c0-117">Details</span></span>  
  
|<span data-ttu-id="079c0-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="079c0-118">Data Item Name</span></span>|<span data-ttu-id="079c0-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="079c0-119">Data Item Type</span></span>|<span data-ttu-id="079c0-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="079c0-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="079c0-121">Genişletilmiş verileri</span><span class="sxs-lookup"><span data-stu-id="079c0-121">Extended Data</span></span>|`xs:string`|<span data-ttu-id="079c0-122">Etkinlik adı.</span><span class="sxs-lookup"><span data-stu-id="079c0-122">The name of the activity.</span></span>|  
|<span data-ttu-id="079c0-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="079c0-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="079c0-124">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="079c0-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
