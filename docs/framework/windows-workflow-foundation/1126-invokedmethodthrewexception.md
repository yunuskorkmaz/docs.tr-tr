---
title: 1126 - InvokedMethodThrewException
ms.date: 03/30/2017
ms.assetid: 0d3cff1a-97e6-4b6c-be18-108c6881bfc0
ms.openlocfilehash: 7caaebe42f49a62fec61ba17a4d3fe3a538e2ab4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262846"
---
# <a name="1126---invokedmethodthrewexception"></a><span data-ttu-id="2a77f-102">1126 - InvokedMethodThrewException</span><span class="sxs-lookup"><span data-stu-id="2a77f-102">1126 - InvokedMethodThrewException</span></span>

## <a name="properties"></a><span data-ttu-id="2a77f-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="2a77f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2a77f-104">ID</span><span class="sxs-lookup"><span data-stu-id="2a77f-104">ID</span></span>|<span data-ttu-id="2a77f-105">1126</span><span class="sxs-lookup"><span data-stu-id="2a77f-105">1126</span></span>|  
|<span data-ttu-id="2a77f-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="2a77f-106">Keywords</span></span>|<span data-ttu-id="2a77f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="2a77f-107">WFRuntime</span></span>|  
|<span data-ttu-id="2a77f-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="2a77f-108">Level</span></span>|<span data-ttu-id="2a77f-109">Bilgi</span><span class="sxs-lookup"><span data-stu-id="2a77f-109">Information</span></span>|  
|<span data-ttu-id="2a77f-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="2a77f-110">Channel</span></span>|<span data-ttu-id="2a77f-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="2a77f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2a77f-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a77f-112">Description</span></span>  

 <span data-ttu-id="2a77f-113">InvokeMethod etkinliği tarafından çağrılan yöntem tarafından bir özel durumun oluşturulduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="2a77f-113">Indicates an exception was thrown by the method called by the InvokeMethod activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2a77f-114">İleti</span><span class="sxs-lookup"><span data-stu-id="2a77f-114">Message</span></span>  

 <span data-ttu-id="2a77f-115">' %1 ' etkinliğinin çağırdığı yöntemde bir özel durum oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="2a77f-115">An exception was thrown in the method called by the activity '%1'.</span></span> <span data-ttu-id="2a77f-116">%2</span><span class="sxs-lookup"><span data-stu-id="2a77f-116">%2</span></span>  
  
## <a name="details"></a><span data-ttu-id="2a77f-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="2a77f-117">Details</span></span>  
  
|<span data-ttu-id="2a77f-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="2a77f-118">Data Item Name</span></span>|<span data-ttu-id="2a77f-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="2a77f-119">Data Item Type</span></span>|<span data-ttu-id="2a77f-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a77f-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2a77f-121">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="2a77f-121">InvokeMethod</span></span>|<span data-ttu-id="2a77f-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="2a77f-122">xs:string</span></span>|<span data-ttu-id="2a77f-123">InvokeMethod etkinliğinin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="2a77f-123">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="2a77f-124">Özel durum</span><span class="sxs-lookup"><span data-stu-id="2a77f-124">Exception</span></span>|<span data-ttu-id="2a77f-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="2a77f-125">xs:string</span></span>|<span data-ttu-id="2a77f-126">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="2a77f-126">The exception details for the exception</span></span>|  
|<span data-ttu-id="2a77f-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2a77f-127">AppDomain</span></span>|<span data-ttu-id="2a77f-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="2a77f-128">xs:string</span></span>|<span data-ttu-id="2a77f-129">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="2a77f-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
