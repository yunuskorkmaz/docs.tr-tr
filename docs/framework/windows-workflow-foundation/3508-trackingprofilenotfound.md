---
title: 3508 - TrackingProfileNotFound
ms.date: 03/30/2017
ms.assetid: 4cee3c4a-0490-4c94-aa19-ef7ce7287c02
ms.openlocfilehash: 94c7ce231df241778f7c6ec5fe5998eae364750d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755577"
---
# <a name="3508---trackingprofilenotfound"></a><span data-ttu-id="38abf-102">3508 - TrackingProfileNotFound</span><span class="sxs-lookup"><span data-stu-id="38abf-102">3508 - TrackingProfileNotFound</span></span>
## <a name="properties"></a><span data-ttu-id="38abf-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="38abf-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="38abf-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="38abf-104">ID</span></span>|<span data-ttu-id="38abf-105">3508</span><span class="sxs-lookup"><span data-stu-id="38abf-105">3508</span></span>|  
|<span data-ttu-id="38abf-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="38abf-106">Keywords</span></span>|<span data-ttu-id="38abf-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="38abf-107">WFServices</span></span>|  
|<span data-ttu-id="38abf-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="38abf-108">Level</span></span>|<span data-ttu-id="38abf-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="38abf-109">Verbose</span></span>|  
|<span data-ttu-id="38abf-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="38abf-110">Channel</span></span>|<span data-ttu-id="38abf-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="38abf-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="38abf-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="38abf-112">Description</span></span>  
 <span data-ttu-id="38abf-113">Yapılandırma dosyasında bir TrackingProfile bulunamadı veya ActivityDefinitionId profili eşleşmiyor gösterir.</span><span class="sxs-lookup"><span data-stu-id="38abf-113">Indicates either a TrackingProfile is not found in the config file or the ActivityDefinitionId does not match the profile.</span></span>  
  
## <a name="message"></a><span data-ttu-id="38abf-114">İleti</span><span class="sxs-lookup"><span data-stu-id="38abf-114">Message</span></span>  
 <span data-ttu-id="38abf-115">TrackingProfile ActivityDefinitionId bulunamadı ' %2' için '%1'.</span><span class="sxs-lookup"><span data-stu-id="38abf-115">TrackingProfile '%1' for the ActivityDefinitionId '%2' not found.</span></span> <span data-ttu-id="38abf-116">TrackingProfile yapılandırma dosyasında bulunamadı ya da ActivityDefinitionId eşleşmiyor.</span><span class="sxs-lookup"><span data-stu-id="38abf-116">Either the TrackingProfile is not found in the config file or the ActivityDefinitionId does not match.</span></span>  
  
## <a name="details"></a><span data-ttu-id="38abf-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="38abf-117">Details</span></span>  
  
|<span data-ttu-id="38abf-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="38abf-118">Data Item Name</span></span>|<span data-ttu-id="38abf-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="38abf-119">Data Item Type</span></span>|<span data-ttu-id="38abf-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="38abf-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="38abf-121">trackingProfile</span><span class="sxs-lookup"><span data-stu-id="38abf-121">TrackingProfile</span></span>|<span data-ttu-id="38abf-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="38abf-122">xs:string</span></span>|<span data-ttu-id="38abf-123">İzleme profilinin adı.</span><span class="sxs-lookup"><span data-stu-id="38abf-123">The name of the tracking profile.</span></span>|  
|<span data-ttu-id="38abf-124">activityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="38abf-124">ActivityDefinitionId</span></span>|<span data-ttu-id="38abf-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="38abf-125">xs:string</span></span>|<span data-ttu-id="38abf-126">Etkinlik tanımı kimliği.</span><span class="sxs-lookup"><span data-stu-id="38abf-126">The activity definition id.</span></span>|  
|<span data-ttu-id="38abf-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="38abf-127">AppDomain</span></span>|<span data-ttu-id="38abf-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="38abf-128">xs:string</span></span>|<span data-ttu-id="38abf-129">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="38abf-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
