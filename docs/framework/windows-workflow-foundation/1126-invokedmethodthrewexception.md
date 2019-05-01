---
title: 1126 - InvokedMethodThrewException
ms.date: 03/30/2017
ms.assetid: 0d3cff1a-97e6-4b6c-be18-108c6881bfc0
ms.openlocfilehash: 714a98a300426d80c3b494d701ae1bd53a49592f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924013"
---
# <a name="1126---invokedmethodthrewexception"></a><span data-ttu-id="f4cd9-102">1126 - InvokedMethodThrewException</span><span class="sxs-lookup"><span data-stu-id="f4cd9-102">1126 - InvokedMethodThrewException</span></span>
## <a name="properties"></a><span data-ttu-id="f4cd9-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f4cd9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f4cd9-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="f4cd9-104">ID</span></span>|<span data-ttu-id="f4cd9-105">1126</span><span class="sxs-lookup"><span data-stu-id="f4cd9-105">1126</span></span>|  
|<span data-ttu-id="f4cd9-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="f4cd9-106">Keywords</span></span>|<span data-ttu-id="f4cd9-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="f4cd9-107">WFRuntime</span></span>|  
|<span data-ttu-id="f4cd9-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="f4cd9-108">Level</span></span>|<span data-ttu-id="f4cd9-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="f4cd9-109">Information</span></span>|  
|<span data-ttu-id="f4cd9-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="f4cd9-110">Channel</span></span>|<span data-ttu-id="f4cd9-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="f4cd9-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f4cd9-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f4cd9-112">Description</span></span>  
 <span data-ttu-id="f4cd9-113">InvokeMethod etkinlik tarafından çağrılan yöntemi tarafından bir özel durum oluştu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4cd9-113">Indicates an exception was thrown by the method called by the InvokeMethod activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f4cd9-114">İleti</span><span class="sxs-lookup"><span data-stu-id="f4cd9-114">Message</span></span>  
 <span data-ttu-id="f4cd9-115">Etkinlik tarafından '%1' adlı bir yöntemde özel durum oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="f4cd9-115">An exception was thrown in the method called by the activity '%1'.</span></span> <span data-ttu-id="f4cd9-116">%2</span><span class="sxs-lookup"><span data-stu-id="f4cd9-116">%2</span></span>  
  
## <a name="details"></a><span data-ttu-id="f4cd9-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f4cd9-117">Details</span></span>  
  
|<span data-ttu-id="f4cd9-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="f4cd9-118">Data Item Name</span></span>|<span data-ttu-id="f4cd9-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="f4cd9-119">Data Item Type</span></span>|<span data-ttu-id="f4cd9-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f4cd9-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f4cd9-121">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="f4cd9-121">InvokeMethod</span></span>|<span data-ttu-id="f4cd9-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="f4cd9-122">xs:string</span></span>|<span data-ttu-id="f4cd9-123">InvokeMethod etkinliği görünen adı.</span><span class="sxs-lookup"><span data-stu-id="f4cd9-123">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="f4cd9-124">Özel Durum</span><span class="sxs-lookup"><span data-stu-id="f4cd9-124">Exception</span></span>|<span data-ttu-id="f4cd9-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="f4cd9-125">xs:string</span></span>|<span data-ttu-id="f4cd9-126">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="f4cd9-126">The exception details for the exception</span></span>|  
|<span data-ttu-id="f4cd9-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f4cd9-127">AppDomain</span></span>|<span data-ttu-id="f4cd9-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="f4cd9-128">xs:string</span></span>|<span data-ttu-id="f4cd9-129">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="f4cd9-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
