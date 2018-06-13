---
title: 2577 - TryCatchExceptionDuringCancelation
ms.date: 03/30/2017
ms.assetid: 35ee9f55-227f-4566-bcb4-4c7c75dea85b
ms.openlocfilehash: c272dd91249dfc90e6f4c38a7339919a5a6446e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510737"
---
# <a name="2577---trycatchexceptionduringcancelation"></a><span data-ttu-id="e58b2-102">2577 - TryCatchExceptionDuringCancelation</span><span class="sxs-lookup"><span data-stu-id="e58b2-102">2577 - TryCatchExceptionDuringCancelation</span></span>
## <a name="properties"></a><span data-ttu-id="e58b2-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e58b2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e58b2-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="e58b2-104">ID</span></span>|<span data-ttu-id="e58b2-105">2577</span><span class="sxs-lookup"><span data-stu-id="e58b2-105">2577</span></span>|  
|<span data-ttu-id="e58b2-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="e58b2-106">Keywords</span></span>|<span data-ttu-id="e58b2-107">WFActivities</span><span class="sxs-lookup"><span data-stu-id="e58b2-107">WFActivities</span></span>|  
|<span data-ttu-id="e58b2-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="e58b2-108">Level</span></span>|<span data-ttu-id="e58b2-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="e58b2-109">Warning</span></span>|  
|<span data-ttu-id="e58b2-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="e58b2-110">Channel</span></span>|<span data-ttu-id="e58b2-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="e58b2-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e58b2-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e58b2-112">Description</span></span>  
 <span data-ttu-id="e58b2-113">Bir alt etkinlik TryCatch etkinliğin iptali sırasında bir özel durum oluşturdu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e58b2-113">Indicates a child activity of the TryCatch activity has thrown an exception during cancelation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e58b2-114">İleti</span><span class="sxs-lookup"><span data-stu-id="e58b2-114">Message</span></span>  
 <span data-ttu-id="e58b2-115">'%1' TryCatch etkinliğin alt etkinlik iptali sırasında bir özel durum oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="e58b2-115">A child activity of the TryCatch activity '%1' has thrown an exception during cancelation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e58b2-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e58b2-116">Details</span></span>  
  
|<span data-ttu-id="e58b2-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="e58b2-117">Data Item Name</span></span>|<span data-ttu-id="e58b2-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="e58b2-118">Data Item Type</span></span>|<span data-ttu-id="e58b2-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e58b2-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e58b2-120">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="e58b2-120">DisplayName</span></span>|<span data-ttu-id="e58b2-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="e58b2-121">xs:string</span></span>|<span data-ttu-id="e58b2-122">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="e58b2-122">The display name of the activity.</span></span>|  
|<span data-ttu-id="e58b2-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e58b2-123">AppDomain</span></span>|<span data-ttu-id="e58b2-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="e58b2-124">xs:string</span></span>|<span data-ttu-id="e58b2-125">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="e58b2-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
