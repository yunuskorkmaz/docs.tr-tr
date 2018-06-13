---
title: 1018 - StartCancelActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 68b4fa1d-eee6-4a2a-8c16-7e9d89f08ab9
ms.openlocfilehash: 8d7045b0a7f31ecfd5dd90f319192bd202804353
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510659"
---
# <a name="1018---startcancelactivityworkitem"></a><span data-ttu-id="43cad-102">1018 - StartCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="43cad-102">1018 - StartCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="43cad-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="43cad-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="43cad-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="43cad-104">ID</span></span>|<span data-ttu-id="43cad-105">1018</span><span class="sxs-lookup"><span data-stu-id="43cad-105">1018</span></span>|  
|<span data-ttu-id="43cad-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="43cad-106">Keywords</span></span>|<span data-ttu-id="43cad-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="43cad-107">WFRuntime</span></span>|  
|<span data-ttu-id="43cad-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="43cad-108">Level</span></span>|<span data-ttu-id="43cad-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="43cad-109">Verbose</span></span>|  
|<span data-ttu-id="43cad-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="43cad-110">Channel</span></span>|<span data-ttu-id="43cad-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="43cad-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="43cad-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43cad-112">Description</span></span>  
 <span data-ttu-id="43cad-113">Bir CancelActivityWorkItem yürütme başlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="43cad-113">Indicates a CancelActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="43cad-114">İleti</span><span class="sxs-lookup"><span data-stu-id="43cad-114">Message</span></span>  
 <span data-ttu-id="43cad-115">'%1', DisplayName etkinliğinin CancelActivityWorkItem yürütülmesi başlatılıyor: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="43cad-115">Starting execution of a CancelActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="43cad-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="43cad-116">Details</span></span>  
  
|<span data-ttu-id="43cad-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="43cad-117">Data Item Name</span></span>|<span data-ttu-id="43cad-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="43cad-118">Data Item Type</span></span>|<span data-ttu-id="43cad-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43cad-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="43cad-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="43cad-120">Activity</span></span>|<span data-ttu-id="43cad-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="43cad-121">xs:string</span></span>|<span data-ttu-id="43cad-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="43cad-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="43cad-123">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="43cad-123">DisplayName</span></span>|<span data-ttu-id="43cad-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="43cad-124">xs:string</span></span>|<span data-ttu-id="43cad-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="43cad-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="43cad-126">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="43cad-126">InstanceId</span></span>|<span data-ttu-id="43cad-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="43cad-127">xs:string</span></span>|<span data-ttu-id="43cad-128">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="43cad-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="43cad-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="43cad-129">AppDomain</span></span>|<span data-ttu-id="43cad-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="43cad-130">xs:string</span></span>|<span data-ttu-id="43cad-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="43cad-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
