---
title: 4210 - SqlExceptionCaught
ms.date: 03/30/2017
ms.assetid: f0ce8af3-eb4c-48c8-b3d9-dd2f94b5574b
ms.openlocfilehash: 2493014e80e79ac2935c1bcc685147a74e48fb47
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512079"
---
# <a name="4210---sqlexceptioncaught"></a><span data-ttu-id="495fb-102">4210 - SqlExceptionCaught</span><span class="sxs-lookup"><span data-stu-id="495fb-102">4210 - SqlExceptionCaught</span></span>
## <a name="properties"></a><span data-ttu-id="495fb-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="495fb-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="495fb-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="495fb-104">ID</span></span>|<span data-ttu-id="495fb-105">4210</span><span class="sxs-lookup"><span data-stu-id="495fb-105">4210</span></span>|  
|<span data-ttu-id="495fb-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="495fb-106">Keywords</span></span>|<span data-ttu-id="495fb-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="495fb-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="495fb-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="495fb-108">Level</span></span>|<span data-ttu-id="495fb-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="495fb-109">Warning</span></span>|  
|<span data-ttu-id="495fb-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="495fb-110">Channel</span></span>|<span data-ttu-id="495fb-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="495fb-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="495fb-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="495fb-112">Description</span></span>  
 <span data-ttu-id="495fb-113">Bir SQL özel durumu yakalandı gösterir.</span><span class="sxs-lookup"><span data-stu-id="495fb-113">Indicates a SQL exception was caught.</span></span>  
  
## <a name="message"></a><span data-ttu-id="495fb-114">İleti</span><span class="sxs-lookup"><span data-stu-id="495fb-114">Message</span></span>  
 <span data-ttu-id="495fb-115">SQL özel durumu numarası %1 ileti %2 yakalandı.</span><span class="sxs-lookup"><span data-stu-id="495fb-115">Caught SQL Exception number %1 message %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="495fb-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="495fb-116">Details</span></span>  
  
|<span data-ttu-id="495fb-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="495fb-117">Data Item Name</span></span>|<span data-ttu-id="495fb-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="495fb-118">Data Item Type</span></span>|<span data-ttu-id="495fb-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="495fb-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="495fb-120">HataNumarası</span><span class="sxs-lookup"><span data-stu-id="495fb-120">ErrorNumber</span></span>|<span data-ttu-id="495fb-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="495fb-121">xs:string</span></span>|<span data-ttu-id="495fb-122">SQL hata numarası.</span><span class="sxs-lookup"><span data-stu-id="495fb-122">The SQL error number.</span></span>|  
|<span data-ttu-id="495fb-123">ExceptionMessage</span><span class="sxs-lookup"><span data-stu-id="495fb-123">ExceptionMessage</span></span>|<span data-ttu-id="495fb-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="495fb-124">xs:string</span></span>|<span data-ttu-id="495fb-125">SQL özel durum iletisi.</span><span class="sxs-lookup"><span data-stu-id="495fb-125">The message from the SQL exception.</span></span>|  
|<span data-ttu-id="495fb-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="495fb-126">AppDomain</span></span>|<span data-ttu-id="495fb-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="495fb-127">xs:string</span></span>|<span data-ttu-id="495fb-128">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="495fb-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
