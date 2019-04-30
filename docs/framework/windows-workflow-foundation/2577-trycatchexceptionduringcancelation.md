---
title: 2577 - TryCatchExceptionDuringCancelation
ms.date: 03/30/2017
ms.assetid: 35ee9f55-227f-4566-bcb4-4c7c75dea85b
ms.openlocfilehash: c272dd91249dfc90e6f4c38a7339919a5a6446e5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755629"
---
# <a name="2577---trycatchexceptionduringcancelation"></a><span data-ttu-id="feeb0-102">2577 - TryCatchExceptionDuringCancelation</span><span class="sxs-lookup"><span data-stu-id="feeb0-102">2577 - TryCatchExceptionDuringCancelation</span></span>
## <a name="properties"></a><span data-ttu-id="feeb0-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="feeb0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="feeb0-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="feeb0-104">ID</span></span>|<span data-ttu-id="feeb0-105">2577</span><span class="sxs-lookup"><span data-stu-id="feeb0-105">2577</span></span>|  
|<span data-ttu-id="feeb0-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="feeb0-106">Keywords</span></span>|<span data-ttu-id="feeb0-107">WFActivities</span><span class="sxs-lookup"><span data-stu-id="feeb0-107">WFActivities</span></span>|  
|<span data-ttu-id="feeb0-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="feeb0-108">Level</span></span>|<span data-ttu-id="feeb0-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="feeb0-109">Warning</span></span>|  
|<span data-ttu-id="feeb0-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="feeb0-110">Channel</span></span>|<span data-ttu-id="feeb0-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="feeb0-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="feeb0-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="feeb0-112">Description</span></span>  
 <span data-ttu-id="feeb0-113">TryCatch etkinlik bir alt etkinlik iptal etme sırasında bir özel durum gösterir.</span><span class="sxs-lookup"><span data-stu-id="feeb0-113">Indicates a child activity of the TryCatch activity has thrown an exception during cancelation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="feeb0-114">İleti</span><span class="sxs-lookup"><span data-stu-id="feeb0-114">Message</span></span>  
 <span data-ttu-id="feeb0-115">TryCatch etkinlik '%1' bir alt etkinlik iptal etme sırasında bir özel durum oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="feeb0-115">A child activity of the TryCatch activity '%1' has thrown an exception during cancelation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="feeb0-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="feeb0-116">Details</span></span>  
  
|<span data-ttu-id="feeb0-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="feeb0-117">Data Item Name</span></span>|<span data-ttu-id="feeb0-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="feeb0-118">Data Item Type</span></span>|<span data-ttu-id="feeb0-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="feeb0-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="feeb0-120">displayName</span><span class="sxs-lookup"><span data-stu-id="feeb0-120">DisplayName</span></span>|<span data-ttu-id="feeb0-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="feeb0-121">xs:string</span></span>|<span data-ttu-id="feeb0-122">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="feeb0-122">The display name of the activity.</span></span>|  
|<span data-ttu-id="feeb0-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="feeb0-123">AppDomain</span></span>|<span data-ttu-id="feeb0-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="feeb0-124">xs:string</span></span>|<span data-ttu-id="feeb0-125">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="feeb0-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
