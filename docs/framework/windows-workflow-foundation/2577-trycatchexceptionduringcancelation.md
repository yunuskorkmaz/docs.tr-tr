---
title: 2577 - TryCatchExceptionDuringCancelation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35ee9f55-227f-4566-bcb4-4c7c75dea85b
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f1e851a50c9677b2f10ea3478c3599706007d4d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="2577---trycatchexceptionduringcancelation"></a><span data-ttu-id="95dca-102">2577 - TryCatchExceptionDuringCancelation</span><span class="sxs-lookup"><span data-stu-id="95dca-102">2577 - TryCatchExceptionDuringCancelation</span></span>
## <a name="properties"></a><span data-ttu-id="95dca-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="95dca-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="95dca-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="95dca-104">ID</span></span>|<span data-ttu-id="95dca-105">2577</span><span class="sxs-lookup"><span data-stu-id="95dca-105">2577</span></span>|  
|<span data-ttu-id="95dca-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="95dca-106">Keywords</span></span>|<span data-ttu-id="95dca-107">WFActivities</span><span class="sxs-lookup"><span data-stu-id="95dca-107">WFActivities</span></span>|  
|<span data-ttu-id="95dca-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="95dca-108">Level</span></span>|<span data-ttu-id="95dca-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="95dca-109">Warning</span></span>|  
|<span data-ttu-id="95dca-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="95dca-110">Channel</span></span>|<span data-ttu-id="95dca-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="95dca-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="95dca-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="95dca-112">Description</span></span>  
 <span data-ttu-id="95dca-113">Bir alt etkinlik TryCatch etkinliğin iptali sırasında bir özel durum oluşturdu gösterir.</span><span class="sxs-lookup"><span data-stu-id="95dca-113">Indicates a child activity of the TryCatch activity has thrown an exception during cancelation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="95dca-114">İleti</span><span class="sxs-lookup"><span data-stu-id="95dca-114">Message</span></span>  
 <span data-ttu-id="95dca-115">'%1' TryCatch etkinliğin alt etkinlik iptali sırasında bir özel durum oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="95dca-115">A child activity of the TryCatch activity '%1' has thrown an exception during cancelation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="95dca-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="95dca-116">Details</span></span>  
  
|<span data-ttu-id="95dca-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="95dca-117">Data Item Name</span></span>|<span data-ttu-id="95dca-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="95dca-118">Data Item Type</span></span>|<span data-ttu-id="95dca-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="95dca-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="95dca-120">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="95dca-120">DisplayName</span></span>|<span data-ttu-id="95dca-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="95dca-121">xs:string</span></span>|<span data-ttu-id="95dca-122">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="95dca-122">The display name of the activity.</span></span>|  
|<span data-ttu-id="95dca-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="95dca-123">AppDomain</span></span>|<span data-ttu-id="95dca-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="95dca-124">xs:string</span></span>|<span data-ttu-id="95dca-125">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="95dca-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
