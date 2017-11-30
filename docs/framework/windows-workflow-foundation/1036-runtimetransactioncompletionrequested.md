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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4f497d777221a98b38603b2ced29342651b1020b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="1036---runtimetransactioncompletionrequested"></a><span data-ttu-id="af9a5-102">1036 - RuntimeTransactionCompletionRequested</span><span class="sxs-lookup"><span data-stu-id="af9a5-102">1036 - RuntimeTransactionCompletionRequested</span></span>
## <a name="properties"></a><span data-ttu-id="af9a5-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="af9a5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="af9a5-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="af9a5-104">ID</span></span>|<span data-ttu-id="af9a5-105">1036</span><span class="sxs-lookup"><span data-stu-id="af9a5-105">1036</span></span>|  
|<span data-ttu-id="af9a5-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="af9a5-106">Keywords</span></span>|<span data-ttu-id="af9a5-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="af9a5-107">WFRuntime</span></span>|  
|<span data-ttu-id="af9a5-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="af9a5-108">Level</span></span>|<span data-ttu-id="af9a5-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="af9a5-109">Verbose</span></span>|  
|<span data-ttu-id="af9a5-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="af9a5-110">Channel</span></span>|<span data-ttu-id="af9a5-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="af9a5-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="af9a5-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="af9a5-112">Description</span></span>  
 <span data-ttu-id="af9a5-113">Etkinlik çalışma zamanı işlemin tamamlanmasından zamanlanmış gösterir.</span><span class="sxs-lookup"><span data-stu-id="af9a5-113">Indicates an activity has scheduled the completion of the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="af9a5-114">İleti</span><span class="sxs-lookup"><span data-stu-id="af9a5-114">Message</span></span>  
 <span data-ttu-id="af9a5-115">Etkinlik '%1', DisplayName: '%2', örnek kimliği: '%3' çalışma zamanı TRANSACTION zamanlanmış.</span><span class="sxs-lookup"><span data-stu-id="af9a5-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has scheduled completion of the runtime transaction.</span></span>  
  
## <a name="details"></a><span data-ttu-id="af9a5-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="af9a5-116">Details</span></span>  
  
|<span data-ttu-id="af9a5-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="af9a5-117">Data Item Name</span></span>|<span data-ttu-id="af9a5-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="af9a5-118">Data Item Type</span></span>|<span data-ttu-id="af9a5-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="af9a5-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="af9a5-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="af9a5-120">Activity</span></span>|<span data-ttu-id="af9a5-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="af9a5-121">xs:string</span></span>|<span data-ttu-id="af9a5-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="af9a5-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="af9a5-123">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="af9a5-123">DisplayName</span></span>|<span data-ttu-id="af9a5-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="af9a5-124">xs:string</span></span>|<span data-ttu-id="af9a5-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="af9a5-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="af9a5-126">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="af9a5-126">InstanceId</span></span>|<span data-ttu-id="af9a5-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="af9a5-127">xs:string</span></span>|<span data-ttu-id="af9a5-128">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="af9a5-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="af9a5-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="af9a5-129">AppDomain</span></span>|<span data-ttu-id="af9a5-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="af9a5-130">xs:string</span></span>|<span data-ttu-id="af9a5-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="af9a5-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
