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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2a4bc0d9ab45fe8e2f025c651fce137d6a4255bc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="2577---trycatchexceptionduringcancelation"></a><span data-ttu-id="eccad-102">2577 - TryCatchExceptionDuringCancelation</span><span class="sxs-lookup"><span data-stu-id="eccad-102">2577 - TryCatchExceptionDuringCancelation</span></span>
## <a name="properties"></a><span data-ttu-id="eccad-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="eccad-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="eccad-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="eccad-104">ID</span></span>|<span data-ttu-id="eccad-105">2577</span><span class="sxs-lookup"><span data-stu-id="eccad-105">2577</span></span>|  
|<span data-ttu-id="eccad-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="eccad-106">Keywords</span></span>|<span data-ttu-id="eccad-107">WFActivities</span><span class="sxs-lookup"><span data-stu-id="eccad-107">WFActivities</span></span>|  
|<span data-ttu-id="eccad-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="eccad-108">Level</span></span>|<span data-ttu-id="eccad-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="eccad-109">Warning</span></span>|  
|<span data-ttu-id="eccad-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="eccad-110">Channel</span></span>|<span data-ttu-id="eccad-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="eccad-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="eccad-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eccad-112">Description</span></span>  
 <span data-ttu-id="eccad-113">Bir alt etkinlik TryCatch etkinliğin iptali sırasında bir özel durum oluşturdu gösterir.</span><span class="sxs-lookup"><span data-stu-id="eccad-113">Indicates a child activity of the TryCatch activity has thrown an exception during cancelation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="eccad-114">İleti</span><span class="sxs-lookup"><span data-stu-id="eccad-114">Message</span></span>  
 <span data-ttu-id="eccad-115">'%1' TryCatch etkinliğin alt etkinlik iptali sırasında bir özel durum oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="eccad-115">A child activity of the TryCatch activity '%1' has thrown an exception during cancelation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="eccad-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="eccad-116">Details</span></span>  
  
|<span data-ttu-id="eccad-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="eccad-117">Data Item Name</span></span>|<span data-ttu-id="eccad-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="eccad-118">Data Item Type</span></span>|<span data-ttu-id="eccad-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eccad-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="eccad-120">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="eccad-120">DisplayName</span></span>|<span data-ttu-id="eccad-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="eccad-121">xs:string</span></span>|<span data-ttu-id="eccad-122">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="eccad-122">The display name of the activity.</span></span>|  
|<span data-ttu-id="eccad-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="eccad-123">AppDomain</span></span>|<span data-ttu-id="eccad-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="eccad-124">xs:string</span></span>|<span data-ttu-id="eccad-125">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="eccad-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
