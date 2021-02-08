---
description: 'Hakkında daha fazla bilgi edinin: 2577-TryCatch Exceptionduringiptal'
title: 2577 - TryCatchExceptionDuringCancelation
ms.date: 03/30/2017
ms.assetid: 35ee9f55-227f-4566-bcb4-4c7c75dea85b
ms.openlocfilehash: e02e7722dadfe38b9fc1fbb92e809ae8f80cbd2f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778106"
---
# <a name="2577---trycatchexceptionduringcancelation"></a><span data-ttu-id="e5d85-103">2577 - TryCatchExceptionDuringCancelation</span><span class="sxs-lookup"><span data-stu-id="e5d85-103">2577 - TryCatchExceptionDuringCancelation</span></span>

## <a name="properties"></a><span data-ttu-id="e5d85-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e5d85-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e5d85-105">ID</span><span class="sxs-lookup"><span data-stu-id="e5d85-105">ID</span></span>|<span data-ttu-id="e5d85-106">2577</span><span class="sxs-lookup"><span data-stu-id="e5d85-106">2577</span></span>|  
|<span data-ttu-id="e5d85-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="e5d85-107">Keywords</span></span>|<span data-ttu-id="e5d85-108">WFActivities</span><span class="sxs-lookup"><span data-stu-id="e5d85-108">WFActivities</span></span>|  
|<span data-ttu-id="e5d85-109">Level</span><span class="sxs-lookup"><span data-stu-id="e5d85-109">Level</span></span>|<span data-ttu-id="e5d85-110">Uyarı</span><span class="sxs-lookup"><span data-stu-id="e5d85-110">Warning</span></span>|  
|<span data-ttu-id="e5d85-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="e5d85-111">Channel</span></span>|<span data-ttu-id="e5d85-112">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="e5d85-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e5d85-113">Description</span><span class="sxs-lookup"><span data-stu-id="e5d85-113">Description</span></span>  

 <span data-ttu-id="e5d85-114">TryCatch etkinliğinin bir alt etkinliğinin iptal sırasında özel durum yaptığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e5d85-114">Indicates a child activity of the TryCatch activity has thrown an exception during cancelation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e5d85-115">İleti</span><span class="sxs-lookup"><span data-stu-id="e5d85-115">Message</span></span>  

 <span data-ttu-id="e5d85-116">' %1 ' TryCatch etkinliğinin bir alt etkinliği iptal işlemi sırasında özel durum oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="e5d85-116">A child activity of the TryCatch activity '%1' has thrown an exception during cancelation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e5d85-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e5d85-117">Details</span></span>  
  
|<span data-ttu-id="e5d85-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="e5d85-118">Data Item Name</span></span>|<span data-ttu-id="e5d85-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="e5d85-119">Data Item Type</span></span>|<span data-ttu-id="e5d85-120">Description</span><span class="sxs-lookup"><span data-stu-id="e5d85-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e5d85-121">DisplayName</span><span class="sxs-lookup"><span data-stu-id="e5d85-121">DisplayName</span></span>|<span data-ttu-id="e5d85-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="e5d85-122">xs:string</span></span>|<span data-ttu-id="e5d85-123">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="e5d85-123">The display name of the activity.</span></span>|  
|<span data-ttu-id="e5d85-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e5d85-124">AppDomain</span></span>|<span data-ttu-id="e5d85-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="e5d85-125">xs:string</span></span>|<span data-ttu-id="e5d85-126">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="e5d85-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
