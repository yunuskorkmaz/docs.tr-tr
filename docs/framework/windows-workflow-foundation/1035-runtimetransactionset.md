---
title: 1035 - RuntimeTransactionSet
ms.date: 03/30/2017
ms.assetid: 03b37de9-778c-4beb-b0e3-de73ece6088e
ms.openlocfilehash: 198e11dd94b0ad5cdc1e01c3611280754ca081d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510040"
---
# <a name="1035---runtimetransactionset"></a><span data-ttu-id="bf1fa-102">1035 - RuntimeTransactionSet</span><span class="sxs-lookup"><span data-stu-id="bf1fa-102">1035 - RuntimeTransactionSet</span></span>
## <a name="properties"></a><span data-ttu-id="bf1fa-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="bf1fa-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bf1fa-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="bf1fa-104">ID</span></span>|<span data-ttu-id="bf1fa-105">1035</span><span class="sxs-lookup"><span data-stu-id="bf1fa-105">1035</span></span>|  
|<span data-ttu-id="bf1fa-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="bf1fa-106">Keywords</span></span>|<span data-ttu-id="bf1fa-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="bf1fa-107">WFRuntime</span></span>|  
|<span data-ttu-id="bf1fa-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="bf1fa-108">Level</span></span>|<span data-ttu-id="bf1fa-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="bf1fa-109">Verbose</span></span>|  
|<span data-ttu-id="bf1fa-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="bf1fa-110">Channel</span></span>|<span data-ttu-id="bf1fa-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="bf1fa-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="bf1fa-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bf1fa-112">Description</span></span>  
 <span data-ttu-id="bf1fa-113">Etkinlik çalışma zamanı işlem ayarlanmış gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf1fa-113">Indicates an activity has set the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="bf1fa-114">İleti</span><span class="sxs-lookup"><span data-stu-id="bf1fa-114">Message</span></span>  
 <span data-ttu-id="bf1fa-115">Çalışma zamanı işlem '%1', DisplayName etkinliği tarafından ayarlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="bf1fa-115">The runtime transaction has been set by Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="bf1fa-116">Etkinlik '%4', DisplayName yalıtılmış yürütme: '%5', örnek kimliği: '%6'.</span><span class="sxs-lookup"><span data-stu-id="bf1fa-116">Execution isolated to Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="bf1fa-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="bf1fa-117">Details</span></span>  
  
|<span data-ttu-id="bf1fa-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="bf1fa-118">Data Item Name</span></span>|<span data-ttu-id="bf1fa-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="bf1fa-119">Data Item Type</span></span>|<span data-ttu-id="bf1fa-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bf1fa-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="bf1fa-121">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="bf1fa-121">Activity</span></span>|<span data-ttu-id="bf1fa-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="bf1fa-122">xs:string</span></span>|<span data-ttu-id="bf1fa-123">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="bf1fa-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="bf1fa-124">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="bf1fa-124">DisplayName</span></span>|<span data-ttu-id="bf1fa-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="bf1fa-125">xs:string</span></span>|<span data-ttu-id="bf1fa-126">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="bf1fa-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="bf1fa-127">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="bf1fa-127">InstanceId</span></span>|<span data-ttu-id="bf1fa-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="bf1fa-128">xs:string</span></span>|<span data-ttu-id="bf1fa-129">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="bf1fa-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="bf1fa-130">IsolatedActivity</span><span class="sxs-lookup"><span data-stu-id="bf1fa-130">IsolatedActivity</span></span>|<span data-ttu-id="bf1fa-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="bf1fa-131">xs:string</span></span>|<span data-ttu-id="bf1fa-132">İşlem için yalıtılmış etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="bf1fa-132">The type name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="bf1fa-133">IsolatedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="bf1fa-133">IsolatedActivityDisplayName</span></span>|<span data-ttu-id="bf1fa-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="bf1fa-134">xs:string</span></span>|<span data-ttu-id="bf1fa-135">İşlem için yalıtılmış etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="bf1fa-135">The display name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="bf1fa-136">IsolatedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="bf1fa-136">IsolatedActivityInstanceId</span></span>|<span data-ttu-id="bf1fa-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="bf1fa-137">xs:string</span></span>|<span data-ttu-id="bf1fa-138">İşlem için yalıtılmış etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="bf1fa-138">The instance id of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="bf1fa-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="bf1fa-139">AppDomain</span></span>|<span data-ttu-id="bf1fa-140">xs: String</span><span class="sxs-lookup"><span data-stu-id="bf1fa-140">xs:string</span></span>|<span data-ttu-id="bf1fa-141">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="bf1fa-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
