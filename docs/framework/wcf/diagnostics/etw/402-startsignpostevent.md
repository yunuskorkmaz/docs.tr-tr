---
title: 402 - StartSignpostEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e5be126-765d-4ac9-88e7-008e9ef4f0e5
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2ade357acdebc6222e59bf5b15725a1edc97dc43
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="402---startsignpostevent"></a><span data-ttu-id="eb207-102">402 - StartSignpostEvent</span><span class="sxs-lookup"><span data-stu-id="eb207-102">402 - StartSignpostEvent</span></span>
## <a name="properties"></a><span data-ttu-id="eb207-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="eb207-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="eb207-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="eb207-104">ID</span></span>|<span data-ttu-id="eb207-105">402</span><span class="sxs-lookup"><span data-stu-id="eb207-105">402</span></span>|  
|<span data-ttu-id="eb207-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="eb207-106">Keywords</span></span>|<span data-ttu-id="eb207-107">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="eb207-107">Troubleshooting</span></span>|  
|<span data-ttu-id="eb207-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="eb207-108">Level</span></span>|<span data-ttu-id="eb207-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="eb207-109">Information</span></span>|  
|<span data-ttu-id="eb207-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="eb207-110">Channel</span></span>|<span data-ttu-id="eb207-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="eb207-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="eb207-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eb207-112">Description</span></span>  
 <span data-ttu-id="eb207-113">Bu olay bir uçtan uca etkinlik başlangıcını işaretler.</span><span class="sxs-lookup"><span data-stu-id="eb207-113">This event marks the beginning of an end-to-end activity.</span></span> <span data-ttu-id="eb207-114">Bu etkinliğin adını içerir.</span><span class="sxs-lookup"><span data-stu-id="eb207-114">It contains the name of the activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="eb207-115">İleti</span><span class="sxs-lookup"><span data-stu-id="eb207-115">Message</span></span>  
 <span data-ttu-id="eb207-116">Etkinlik sınırı.</span><span class="sxs-lookup"><span data-stu-id="eb207-116">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="eb207-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="eb207-117">Details</span></span>  
  
|<span data-ttu-id="eb207-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="eb207-118">Data Item Name</span></span>|<span data-ttu-id="eb207-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="eb207-119">Data Item Type</span></span>|<span data-ttu-id="eb207-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eb207-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="eb207-121">Genişletilmiş verileri</span><span class="sxs-lookup"><span data-stu-id="eb207-121">Extended Data</span></span>|`xs:string`|<span data-ttu-id="eb207-122">Etkinlik adı.</span><span class="sxs-lookup"><span data-stu-id="eb207-122">The name of the activity.</span></span>|  
|<span data-ttu-id="eb207-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="eb207-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="eb207-124">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="eb207-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
