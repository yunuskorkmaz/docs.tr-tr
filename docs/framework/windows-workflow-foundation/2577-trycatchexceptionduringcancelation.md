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
ms.openlocfilehash: 11781bcab37a5034f3bbfadf2c50cbc1c6d378a2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="2577---trycatchexceptionduringcancelation"></a><span data-ttu-id="07e35-102">2577 - TryCatchExceptionDuringCancelation</span><span class="sxs-lookup"><span data-stu-id="07e35-102">2577 - TryCatchExceptionDuringCancelation</span></span>
## <a name="properties"></a><span data-ttu-id="07e35-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="07e35-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="07e35-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="07e35-104">ID</span></span>|<span data-ttu-id="07e35-105">2577</span><span class="sxs-lookup"><span data-stu-id="07e35-105">2577</span></span>|  
|<span data-ttu-id="07e35-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="07e35-106">Keywords</span></span>|<span data-ttu-id="07e35-107">WFActivities</span><span class="sxs-lookup"><span data-stu-id="07e35-107">WFActivities</span></span>|  
|<span data-ttu-id="07e35-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="07e35-108">Level</span></span>|<span data-ttu-id="07e35-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="07e35-109">Warning</span></span>|  
|<span data-ttu-id="07e35-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="07e35-110">Channel</span></span>|<span data-ttu-id="07e35-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="07e35-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="07e35-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07e35-112">Description</span></span>  
 <span data-ttu-id="07e35-113">Bir alt etkinlik TryCatch etkinliğin iptali sırasında bir özel durum oluşturdu gösterir.</span><span class="sxs-lookup"><span data-stu-id="07e35-113">Indicates a child activity of the TryCatch activity has thrown an exception during cancelation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="07e35-114">İleti</span><span class="sxs-lookup"><span data-stu-id="07e35-114">Message</span></span>  
 <span data-ttu-id="07e35-115">'%1' TryCatch etkinliğin alt etkinlik iptali sırasında bir özel durum oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="07e35-115">A child activity of the TryCatch activity '%1' has thrown an exception during cancelation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="07e35-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="07e35-116">Details</span></span>  
  
|<span data-ttu-id="07e35-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="07e35-117">Data Item Name</span></span>|<span data-ttu-id="07e35-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="07e35-118">Data Item Type</span></span>|<span data-ttu-id="07e35-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07e35-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="07e35-120">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="07e35-120">DisplayName</span></span>|<span data-ttu-id="07e35-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="07e35-121">xs:string</span></span>|<span data-ttu-id="07e35-122">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="07e35-122">The display name of the activity.</span></span>|  
|<span data-ttu-id="07e35-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="07e35-123">AppDomain</span></span>|<span data-ttu-id="07e35-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="07e35-124">xs:string</span></span>|<span data-ttu-id="07e35-125">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="07e35-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
