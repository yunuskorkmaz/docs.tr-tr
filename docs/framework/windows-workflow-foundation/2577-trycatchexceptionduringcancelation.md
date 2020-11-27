---
title: 2577 - TryCatchExceptionDuringCancelation
ms.date: 03/30/2017
ms.assetid: 35ee9f55-227f-4566-bcb4-4c7c75dea85b
ms.openlocfilehash: 33c68984e88eaa5e3028899a7c3066c94a65e8eb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271245"
---
# <a name="2577---trycatchexceptionduringcancelation"></a><span data-ttu-id="b927a-102">2577 - TryCatchExceptionDuringCancelation</span><span class="sxs-lookup"><span data-stu-id="b927a-102">2577 - TryCatchExceptionDuringCancelation</span></span>

## <a name="properties"></a><span data-ttu-id="b927a-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="b927a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b927a-104">ID</span><span class="sxs-lookup"><span data-stu-id="b927a-104">ID</span></span>|<span data-ttu-id="b927a-105">2577</span><span class="sxs-lookup"><span data-stu-id="b927a-105">2577</span></span>|  
|<span data-ttu-id="b927a-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="b927a-106">Keywords</span></span>|<span data-ttu-id="b927a-107">WFActivities</span><span class="sxs-lookup"><span data-stu-id="b927a-107">WFActivities</span></span>|  
|<span data-ttu-id="b927a-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="b927a-108">Level</span></span>|<span data-ttu-id="b927a-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="b927a-109">Warning</span></span>|  
|<span data-ttu-id="b927a-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="b927a-110">Channel</span></span>|<span data-ttu-id="b927a-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="b927a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b927a-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b927a-112">Description</span></span>  

 <span data-ttu-id="b927a-113">TryCatch etkinliğinin bir alt etkinliğinin iptal sırasında özel durum yaptığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b927a-113">Indicates a child activity of the TryCatch activity has thrown an exception during cancelation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b927a-114">İleti</span><span class="sxs-lookup"><span data-stu-id="b927a-114">Message</span></span>  

 <span data-ttu-id="b927a-115">' %1 ' TryCatch etkinliğinin bir alt etkinliği iptal işlemi sırasında özel durum oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="b927a-115">A child activity of the TryCatch activity '%1' has thrown an exception during cancelation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b927a-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b927a-116">Details</span></span>  
  
|<span data-ttu-id="b927a-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="b927a-117">Data Item Name</span></span>|<span data-ttu-id="b927a-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="b927a-118">Data Item Type</span></span>|<span data-ttu-id="b927a-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b927a-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b927a-120">DisplayName</span><span class="sxs-lookup"><span data-stu-id="b927a-120">DisplayName</span></span>|<span data-ttu-id="b927a-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="b927a-121">xs:string</span></span>|<span data-ttu-id="b927a-122">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="b927a-122">The display name of the activity.</span></span>|  
|<span data-ttu-id="b927a-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b927a-123">AppDomain</span></span>|<span data-ttu-id="b927a-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="b927a-124">xs:string</span></span>|<span data-ttu-id="b927a-125">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="b927a-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
