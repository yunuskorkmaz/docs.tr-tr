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
ms.openlocfilehash: 112063d5cd550f438541b2d775eaa49124d9cc02
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="1036---runtimetransactioncompletionrequested"></a><span data-ttu-id="ee1c6-102">1036 - RuntimeTransactionCompletionRequested</span><span class="sxs-lookup"><span data-stu-id="ee1c6-102">1036 - RuntimeTransactionCompletionRequested</span></span>
## <a name="properties"></a><span data-ttu-id="ee1c6-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ee1c6-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ee1c6-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="ee1c6-104">ID</span></span>|<span data-ttu-id="ee1c6-105">1036</span><span class="sxs-lookup"><span data-stu-id="ee1c6-105">1036</span></span>|  
|<span data-ttu-id="ee1c6-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="ee1c6-106">Keywords</span></span>|<span data-ttu-id="ee1c6-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="ee1c6-107">WFRuntime</span></span>|  
|<span data-ttu-id="ee1c6-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="ee1c6-108">Level</span></span>|<span data-ttu-id="ee1c6-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="ee1c6-109">Verbose</span></span>|  
|<span data-ttu-id="ee1c6-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="ee1c6-110">Channel</span></span>|<span data-ttu-id="ee1c6-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="ee1c6-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ee1c6-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ee1c6-112">Description</span></span>  
 <span data-ttu-id="ee1c6-113">Etkinlik çalışma zamanı işlemin tamamlanmasından zamanlanmış gösterir.</span><span class="sxs-lookup"><span data-stu-id="ee1c6-113">Indicates an activity has scheduled the completion of the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ee1c6-114">İleti</span><span class="sxs-lookup"><span data-stu-id="ee1c6-114">Message</span></span>  
 <span data-ttu-id="ee1c6-115">Etkinlik '%1', DisplayName: '%2', örnek kimliği: '%3' çalışma zamanı TRANSACTION zamanlanmış.</span><span class="sxs-lookup"><span data-stu-id="ee1c6-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has scheduled completion of the runtime transaction.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ee1c6-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="ee1c6-116">Details</span></span>  
  
|<span data-ttu-id="ee1c6-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="ee1c6-117">Data Item Name</span></span>|<span data-ttu-id="ee1c6-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="ee1c6-118">Data Item Type</span></span>|<span data-ttu-id="ee1c6-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ee1c6-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ee1c6-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="ee1c6-120">Activity</span></span>|<span data-ttu-id="ee1c6-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="ee1c6-121">xs:string</span></span>|<span data-ttu-id="ee1c6-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="ee1c6-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="ee1c6-123">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="ee1c6-123">DisplayName</span></span>|<span data-ttu-id="ee1c6-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="ee1c6-124">xs:string</span></span>|<span data-ttu-id="ee1c6-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="ee1c6-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="ee1c6-126">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="ee1c6-126">InstanceId</span></span>|<span data-ttu-id="ee1c6-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="ee1c6-127">xs:string</span></span>|<span data-ttu-id="ee1c6-128">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="ee1c6-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="ee1c6-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ee1c6-129">AppDomain</span></span>|<span data-ttu-id="ee1c6-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="ee1c6-130">xs:string</span></span>|<span data-ttu-id="ee1c6-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="ee1c6-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
