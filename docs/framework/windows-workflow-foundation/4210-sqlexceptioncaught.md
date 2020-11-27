---
title: 4210 - SqlExceptionCaught
ms.date: 03/30/2017
ms.assetid: f0ce8af3-eb4c-48c8-b3d9-dd2f94b5574b
ms.openlocfilehash: 1dab44e3fb97d74a2146f5bf992225222bc93d50
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280383"
---
# <a name="4210---sqlexceptioncaught"></a><span data-ttu-id="b1c35-102">4210 - SqlExceptionCaught</span><span class="sxs-lookup"><span data-stu-id="b1c35-102">4210 - SqlExceptionCaught</span></span>

## <a name="properties"></a><span data-ttu-id="b1c35-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="b1c35-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b1c35-104">ID</span><span class="sxs-lookup"><span data-stu-id="b1c35-104">ID</span></span>|<span data-ttu-id="b1c35-105">4210</span><span class="sxs-lookup"><span data-stu-id="b1c35-105">4210</span></span>|  
|<span data-ttu-id="b1c35-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="b1c35-106">Keywords</span></span>|<span data-ttu-id="b1c35-107">Wfınstancestore</span><span class="sxs-lookup"><span data-stu-id="b1c35-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="b1c35-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="b1c35-108">Level</span></span>|<span data-ttu-id="b1c35-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="b1c35-109">Warning</span></span>|  
|<span data-ttu-id="b1c35-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="b1c35-110">Channel</span></span>|<span data-ttu-id="b1c35-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="b1c35-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b1c35-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1c35-112">Description</span></span>  

 <span data-ttu-id="b1c35-113">Bir SQL özel durumunun yakalandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b1c35-113">Indicates a SQL exception was caught.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b1c35-114">İleti</span><span class="sxs-lookup"><span data-stu-id="b1c35-114">Message</span></span>  

 <span data-ttu-id="b1c35-115">Yakalanan SQL özel durum numarası %1 ileti %2.</span><span class="sxs-lookup"><span data-stu-id="b1c35-115">Caught SQL Exception number %1 message %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b1c35-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b1c35-116">Details</span></span>  
  
|<span data-ttu-id="b1c35-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="b1c35-117">Data Item Name</span></span>|<span data-ttu-id="b1c35-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="b1c35-118">Data Item Type</span></span>|<span data-ttu-id="b1c35-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1c35-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b1c35-120">ErrorNumber</span><span class="sxs-lookup"><span data-stu-id="b1c35-120">ErrorNumber</span></span>|<span data-ttu-id="b1c35-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="b1c35-121">xs:string</span></span>|<span data-ttu-id="b1c35-122">SQL hata numarası.</span><span class="sxs-lookup"><span data-stu-id="b1c35-122">The SQL error number.</span></span>|  
|<span data-ttu-id="b1c35-123">ExceptionMessage</span><span class="sxs-lookup"><span data-stu-id="b1c35-123">ExceptionMessage</span></span>|<span data-ttu-id="b1c35-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="b1c35-124">xs:string</span></span>|<span data-ttu-id="b1c35-125">SQL özel durumunun iletisi.</span><span class="sxs-lookup"><span data-stu-id="b1c35-125">The message from the SQL exception.</span></span>|  
|<span data-ttu-id="b1c35-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b1c35-126">AppDomain</span></span>|<span data-ttu-id="b1c35-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="b1c35-127">xs:string</span></span>|<span data-ttu-id="b1c35-128">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="b1c35-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
