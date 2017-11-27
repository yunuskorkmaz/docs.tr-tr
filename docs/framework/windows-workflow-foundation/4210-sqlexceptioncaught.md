---
title: 4210 - SqlExceptionCaught
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0ce8af3-eb4c-48c8-b3d9-dd2f94b5574b
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a3fb3c780b80172db8770e717f517b97608fcb7c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="4210---sqlexceptioncaught"></a><span data-ttu-id="d3709-102">4210 - SqlExceptionCaught</span><span class="sxs-lookup"><span data-stu-id="d3709-102">4210 - SqlExceptionCaught</span></span>
## <a name="properties"></a><span data-ttu-id="d3709-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d3709-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d3709-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="d3709-104">ID</span></span>|<span data-ttu-id="d3709-105">4210</span><span class="sxs-lookup"><span data-stu-id="d3709-105">4210</span></span>|  
|<span data-ttu-id="d3709-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="d3709-106">Keywords</span></span>|<span data-ttu-id="d3709-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="d3709-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="d3709-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="d3709-108">Level</span></span>|<span data-ttu-id="d3709-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="d3709-109">Warning</span></span>|  
|<span data-ttu-id="d3709-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="d3709-110">Channel</span></span>|<span data-ttu-id="d3709-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="d3709-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d3709-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3709-112">Description</span></span>  
 <span data-ttu-id="d3709-113">Bir SQL özel durumu yakalandı gösterir.</span><span class="sxs-lookup"><span data-stu-id="d3709-113">Indicates a SQL exception was caught.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d3709-114">İleti</span><span class="sxs-lookup"><span data-stu-id="d3709-114">Message</span></span>  
 <span data-ttu-id="d3709-115">SQL özel durumu numarası %1 ileti %2 yakalandı.</span><span class="sxs-lookup"><span data-stu-id="d3709-115">Caught SQL Exception number %1 message %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d3709-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="d3709-116">Details</span></span>  
  
|<span data-ttu-id="d3709-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="d3709-117">Data Item Name</span></span>|<span data-ttu-id="d3709-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="d3709-118">Data Item Type</span></span>|<span data-ttu-id="d3709-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3709-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d3709-120">HataNumarası</span><span class="sxs-lookup"><span data-stu-id="d3709-120">ErrorNumber</span></span>|<span data-ttu-id="d3709-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="d3709-121">xs:string</span></span>|<span data-ttu-id="d3709-122">SQL hata numarası.</span><span class="sxs-lookup"><span data-stu-id="d3709-122">The SQL error number.</span></span>|  
|<span data-ttu-id="d3709-123">ExceptionMessage</span><span class="sxs-lookup"><span data-stu-id="d3709-123">ExceptionMessage</span></span>|<span data-ttu-id="d3709-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="d3709-124">xs:string</span></span>|<span data-ttu-id="d3709-125">SQL özel durum iletisi.</span><span class="sxs-lookup"><span data-stu-id="d3709-125">The message from the SQL exception.</span></span>|  
|<span data-ttu-id="d3709-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d3709-126">AppDomain</span></span>|<span data-ttu-id="d3709-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="d3709-127">xs:string</span></span>|<span data-ttu-id="d3709-128">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="d3709-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
