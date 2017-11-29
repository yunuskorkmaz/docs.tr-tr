---
title: 402 - StartSignpostEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e5be126-765d-4ac9-88e7-008e9ef4f0e5
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c0cd786f78336be50ad2ef5447f74b92b2abbdc7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="402---startsignpostevent"></a><span data-ttu-id="c1c99-102">402 - StartSignpostEvent</span><span class="sxs-lookup"><span data-stu-id="c1c99-102">402 - StartSignpostEvent</span></span>
## <a name="properties"></a><span data-ttu-id="c1c99-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="c1c99-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c1c99-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="c1c99-104">ID</span></span>|<span data-ttu-id="c1c99-105">402</span><span class="sxs-lookup"><span data-stu-id="c1c99-105">402</span></span>|  
|<span data-ttu-id="c1c99-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="c1c99-106">Keywords</span></span>|<span data-ttu-id="c1c99-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="c1c99-107">Troubleshooting</span></span>|  
|<span data-ttu-id="c1c99-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="c1c99-108">Level</span></span>|<span data-ttu-id="c1c99-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="c1c99-109">Information</span></span>|  
|<span data-ttu-id="c1c99-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="c1c99-110">Channel</span></span>|<span data-ttu-id="c1c99-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="c1c99-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c1c99-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c1c99-112">Description</span></span>  
 <span data-ttu-id="c1c99-113">Bu olay bir uçtan uca etkinlik başlangıcını işaretler.</span><span class="sxs-lookup"><span data-stu-id="c1c99-113">This event marks the beginning of an end-to-end activity.</span></span> <span data-ttu-id="c1c99-114">Bu etkinliğin adını içerir.</span><span class="sxs-lookup"><span data-stu-id="c1c99-114">It contains the name of the activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c1c99-115">İleti</span><span class="sxs-lookup"><span data-stu-id="c1c99-115">Message</span></span>  
 <span data-ttu-id="c1c99-116">Etkinlik sınırı.</span><span class="sxs-lookup"><span data-stu-id="c1c99-116">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c1c99-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="c1c99-117">Details</span></span>  
  
|<span data-ttu-id="c1c99-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="c1c99-118">Data Item Name</span></span>|<span data-ttu-id="c1c99-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="c1c99-119">Data Item Type</span></span>|<span data-ttu-id="c1c99-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c1c99-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c1c99-121">Genişletilmiş verileri</span><span class="sxs-lookup"><span data-stu-id="c1c99-121">Extended Data</span></span>|`xs:string`|<span data-ttu-id="c1c99-122">Etkinlik adı.</span><span class="sxs-lookup"><span data-stu-id="c1c99-122">The name of the activity.</span></span>|  
|<span data-ttu-id="c1c99-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c1c99-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="c1c99-124">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="c1c99-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
