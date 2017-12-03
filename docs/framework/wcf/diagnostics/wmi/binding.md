---
title: Binding2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b9e44d161e1229db9145f4ed7e337396bbd98c68
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="binding"></a><span data-ttu-id="80953-102">Bağlama</span><span class="sxs-lookup"><span data-stu-id="80953-102">Binding</span></span>
<span data-ttu-id="80953-103">WMI bağlama</span><span class="sxs-lookup"><span data-stu-id="80953-103">wmi Binding</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80953-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80953-104">Syntax</span></span>  
  
```  
class Binding  
{  
  BindingElement BindingElements[];  
  datetime CloseTimeout;  
  string Name;  
  string Namespace;  
  datetime OpenTimeout;  
  datetime ReceiveTimeout;  
  string Scheme;  
  datetime SendTimeout;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="80953-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="80953-105">Methods</span></span>  
 <span data-ttu-id="80953-106">Bağlama sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="80953-106">The Binding class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="80953-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="80953-107">Properties</span></span>  
 <span data-ttu-id="80953-108">Bağlama sınıfı aşağıdaki özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="80953-108">The Binding class has the following properties.</span></span>  
  
### <a name="bindingelements"></a><span data-ttu-id="80953-109">BindingElements</span><span class="sxs-lookup"><span data-stu-id="80953-109">BindingElements</span></span>  
 <span data-ttu-id="80953-110">Veri türü: BindingElement dizisi</span><span class="sxs-lookup"><span data-stu-id="80953-110">Data type: BindingElement array</span></span>  
  
 <span data-ttu-id="80953-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="80953-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80953-112">Bağlama tarafından uygulanan bağlama öğeleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="80953-112">The collection of binding elements implemented by the binding.</span></span>  
  
### <a name="closetimeout"></a><span data-ttu-id="80953-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="80953-113">CloseTimeout</span></span>  
 <span data-ttu-id="80953-114">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="80953-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="80953-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="80953-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80953-116">Bir kapatma işlemi tamamlamak sağlanan zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="80953-116">The interval of time provided for a close operation to complete.</span></span>  
  
### <a name="name"></a><span data-ttu-id="80953-117">Ad</span><span class="sxs-lookup"><span data-stu-id="80953-117">Name</span></span>  
 <span data-ttu-id="80953-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="80953-118">Data type: string</span></span>  
  
 <span data-ttu-id="80953-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="80953-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80953-120">Bağlama adı.</span><span class="sxs-lookup"><span data-stu-id="80953-120">The name of the binding.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="80953-121">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="80953-121">Namespace</span></span>  
 <span data-ttu-id="80953-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="80953-122">Data type: string</span></span>  
  
 <span data-ttu-id="80953-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="80953-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80953-124">XML ad alanı bağlama.</span><span class="sxs-lookup"><span data-stu-id="80953-124">The XML namespace of the binding.</span></span>  
  
### <a name="opentimeout"></a><span data-ttu-id="80953-125">openTimeout</span><span class="sxs-lookup"><span data-stu-id="80953-125">OpenTimeout</span></span>  
 <span data-ttu-id="80953-126">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="80953-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="80953-127">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="80953-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80953-128">Bir açık işleminin tamamlanması için sağlanan zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="80953-128">The interval of time provided for an open operation to complete.</span></span>  
  
### <a name="receivetimeout"></a><span data-ttu-id="80953-129">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="80953-129">ReceiveTimeout</span></span>  
 <span data-ttu-id="80953-130">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="80953-130">Data type: datetime</span></span>  
  
 <span data-ttu-id="80953-131">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="80953-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80953-132">Bir alma işleminin tamamlanması için sağlanan zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="80953-132">The interval of time provided for a receive operation to complete.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="80953-133">Düzen</span><span class="sxs-lookup"><span data-stu-id="80953-133">Scheme</span></span>  
 <span data-ttu-id="80953-134">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="80953-134">Data type: string</span></span>  
  
 <span data-ttu-id="80953-135">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="80953-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80953-136">Bağlama tarafından oluşturulan kanal ve dinleyici üreteçleri tarafından kullanılan URI aktarma düzenini.</span><span class="sxs-lookup"><span data-stu-id="80953-136">The URI transport scheme that is used by the channel and listener factories that are built by the binding.</span></span>  
  
### <a name="sendtimeout"></a><span data-ttu-id="80953-137">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="80953-137">SendTimeout</span></span>  
 <span data-ttu-id="80953-138">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="80953-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="80953-139">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="80953-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80953-140">Bir gönderme işleminin tamamlanması için sağlanan zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="80953-140">The interval of time provided for a send operation to complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80953-141">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="80953-141">Requirements</span></span>  
  
|<span data-ttu-id="80953-142">MOF</span><span class="sxs-lookup"><span data-stu-id="80953-142">MOF</span></span>|<span data-ttu-id="80953-143">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="80953-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="80953-144">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="80953-144">Namespace</span></span>|<span data-ttu-id="80953-145">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="80953-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="80953-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="80953-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>
