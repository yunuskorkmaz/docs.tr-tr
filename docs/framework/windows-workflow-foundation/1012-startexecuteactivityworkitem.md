---
title: 1012 - StartExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 29e9b1c6-c5d7-4b58-b59d-a06a923d3c80
ms.openlocfilehash: d6b330bc454c39584e5027f757fd9d9d3434d941
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510386"
---
# <a name="1012---startexecuteactivityworkitem"></a><span data-ttu-id="26e68-102">1012 - StartExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="26e68-102">1012 - StartExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="26e68-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="26e68-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="26e68-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="26e68-104">ID</span></span>|<span data-ttu-id="26e68-105">1012</span><span class="sxs-lookup"><span data-stu-id="26e68-105">1012</span></span>|  
|<span data-ttu-id="26e68-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="26e68-106">Keywords</span></span>|<span data-ttu-id="26e68-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="26e68-107">WFRuntime</span></span>|  
|<span data-ttu-id="26e68-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="26e68-108">Level</span></span>|<span data-ttu-id="26e68-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="26e68-109">Verbose</span></span>|  
|<span data-ttu-id="26e68-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="26e68-110">Channel</span></span>|<span data-ttu-id="26e68-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="26e68-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="26e68-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="26e68-112">Description</span></span>  
 <span data-ttu-id="26e68-113">Bir ExecuteActivityWorkItem yürütme başlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="26e68-113">Indicates an ExecuteActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="26e68-114">İleti</span><span class="sxs-lookup"><span data-stu-id="26e68-114">Message</span></span>  
 <span data-ttu-id="26e68-115">'%1', DisplayName etkinliği için bir ExecuteActivityWorkItem yürütülmesi başlatılıyor: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="26e68-115">Starting execution of an ExecuteActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="26e68-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="26e68-116">Details</span></span>  
  
|<span data-ttu-id="26e68-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="26e68-117">Data Item Name</span></span>|<span data-ttu-id="26e68-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="26e68-118">Data Item Type</span></span>|<span data-ttu-id="26e68-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="26e68-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="26e68-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="26e68-120">Activity</span></span>|<span data-ttu-id="26e68-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="26e68-121">xs:string</span></span>|<span data-ttu-id="26e68-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="26e68-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="26e68-123">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="26e68-123">DisplayName</span></span>|<span data-ttu-id="26e68-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="26e68-124">xs:string</span></span>|<span data-ttu-id="26e68-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="26e68-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="26e68-126">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="26e68-126">InstanceId</span></span>|<span data-ttu-id="26e68-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="26e68-127">xs:string</span></span>|<span data-ttu-id="26e68-128">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="26e68-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="26e68-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="26e68-129">AppDomain</span></span>|<span data-ttu-id="26e68-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="26e68-130">xs:string</span></span>|<span data-ttu-id="26e68-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="26e68-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
