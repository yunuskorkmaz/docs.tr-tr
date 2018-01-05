---
title: 1036 - RuntimeTransactionCompletionRequested
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d36b9f44-7c0f-4083-9d3a-9034dd2b98de
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 91fcac0bdfe885051941d100f1a2c131c547f19e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="1036---runtimetransactioncompletionrequested"></a><span data-ttu-id="a6de0-102">1036 - RuntimeTransactionCompletionRequested</span><span class="sxs-lookup"><span data-stu-id="a6de0-102">1036 - RuntimeTransactionCompletionRequested</span></span>
## <a name="properties"></a><span data-ttu-id="a6de0-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a6de0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a6de0-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="a6de0-104">ID</span></span>|<span data-ttu-id="a6de0-105">1036</span><span class="sxs-lookup"><span data-stu-id="a6de0-105">1036</span></span>|  
|<span data-ttu-id="a6de0-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="a6de0-106">Keywords</span></span>|<span data-ttu-id="a6de0-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="a6de0-107">WFRuntime</span></span>|  
|<span data-ttu-id="a6de0-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="a6de0-108">Level</span></span>|<span data-ttu-id="a6de0-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="a6de0-109">Verbose</span></span>|  
|<span data-ttu-id="a6de0-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="a6de0-110">Channel</span></span>|<span data-ttu-id="a6de0-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="a6de0-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a6de0-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a6de0-112">Description</span></span>  
 <span data-ttu-id="a6de0-113">Etkinlik çalışma zamanı işlemin tamamlanmasından zamanlanmış gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6de0-113">Indicates an activity has scheduled the completion of the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a6de0-114">İleti</span><span class="sxs-lookup"><span data-stu-id="a6de0-114">Message</span></span>  
 <span data-ttu-id="a6de0-115">Etkinlik '%1', DisplayName: '%2', örnek kimliği: '%3' çalışma zamanı TRANSACTION zamanlanmış.</span><span class="sxs-lookup"><span data-stu-id="a6de0-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has scheduled completion of the runtime transaction.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a6de0-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="a6de0-116">Details</span></span>  
  
|<span data-ttu-id="a6de0-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="a6de0-117">Data Item Name</span></span>|<span data-ttu-id="a6de0-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="a6de0-118">Data Item Type</span></span>|<span data-ttu-id="a6de0-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a6de0-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a6de0-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="a6de0-120">Activity</span></span>|<span data-ttu-id="a6de0-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="a6de0-121">xs:string</span></span>|<span data-ttu-id="a6de0-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="a6de0-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="a6de0-123">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="a6de0-123">DisplayName</span></span>|<span data-ttu-id="a6de0-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="a6de0-124">xs:string</span></span>|<span data-ttu-id="a6de0-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="a6de0-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="a6de0-126">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="a6de0-126">InstanceId</span></span>|<span data-ttu-id="a6de0-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="a6de0-127">xs:string</span></span>|<span data-ttu-id="a6de0-128">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="a6de0-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="a6de0-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a6de0-129">AppDomain</span></span>|<span data-ttu-id="a6de0-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="a6de0-130">xs:string</span></span>|<span data-ttu-id="a6de0-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="a6de0-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
