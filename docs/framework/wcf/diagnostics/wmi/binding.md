---
description: 'Daha fazla bilgi edinin: bağlama'
title: Binding2
ms.date: 03/30/2017
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
ms.openlocfilehash: 36887a9296bfafd0790105e7f4d513efc3009bf8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757793"
---
# <a name="binding"></a><span data-ttu-id="38a47-103">Bağlama</span><span class="sxs-lookup"><span data-stu-id="38a47-103">Binding</span></span>

<span data-ttu-id="38a47-104">WMI bağlama</span><span class="sxs-lookup"><span data-stu-id="38a47-104">wmi Binding</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38a47-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="38a47-105">Syntax</span></span>  
  
```csharp
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
  
## <a name="methods"></a><span data-ttu-id="38a47-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="38a47-106">Methods</span></span>  

 <span data-ttu-id="38a47-107">Bağlama sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="38a47-107">The Binding class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="38a47-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="38a47-108">Properties</span></span>  

 <span data-ttu-id="38a47-109">Bağlama sınıfı aşağıdaki özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="38a47-109">The Binding class has the following properties.</span></span>  
  
### <a name="bindingelements"></a><span data-ttu-id="38a47-110">BindingElements</span><span class="sxs-lookup"><span data-stu-id="38a47-110">BindingElements</span></span>  

 <span data-ttu-id="38a47-111">Veri türü: BindingElement dizisi</span><span class="sxs-lookup"><span data-stu-id="38a47-111">Data type: BindingElement array</span></span>  
  
 <span data-ttu-id="38a47-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="38a47-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="38a47-113">Bağlama tarafından uygulanan bağlama öğelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="38a47-113">The collection of binding elements implemented by the binding.</span></span>  
  
### <a name="closetimeout"></a><span data-ttu-id="38a47-114">CloseTimeout</span><span class="sxs-lookup"><span data-stu-id="38a47-114">CloseTimeout</span></span>  

 <span data-ttu-id="38a47-115">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="38a47-115">Data type: datetime</span></span>  
  
 <span data-ttu-id="38a47-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="38a47-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="38a47-117">Bir kapatma işleminin tamamlanabilmesi için girilen zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="38a47-117">The interval of time provided for a close operation to complete.</span></span>  
  
### <a name="name"></a><span data-ttu-id="38a47-118">Name</span><span class="sxs-lookup"><span data-stu-id="38a47-118">Name</span></span>  

 <span data-ttu-id="38a47-119">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="38a47-119">Data type: string</span></span>  
  
 <span data-ttu-id="38a47-120">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="38a47-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="38a47-121">Bağlamanın adı.</span><span class="sxs-lookup"><span data-stu-id="38a47-121">The name of the binding.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="38a47-122">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="38a47-122">Namespace</span></span>  

 <span data-ttu-id="38a47-123">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="38a47-123">Data type: string</span></span>  
  
 <span data-ttu-id="38a47-124">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="38a47-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="38a47-125">Bağlamanın XML ad alanı.</span><span class="sxs-lookup"><span data-stu-id="38a47-125">The XML namespace of the binding.</span></span>  
  
### <a name="opentimeout"></a><span data-ttu-id="38a47-126">OpenTimeout</span><span class="sxs-lookup"><span data-stu-id="38a47-126">OpenTimeout</span></span>  

 <span data-ttu-id="38a47-127">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="38a47-127">Data type: datetime</span></span>  
  
 <span data-ttu-id="38a47-128">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="38a47-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="38a47-129">Bir açık işlemin tamamlanabilmesi için girilen zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="38a47-129">The interval of time provided for an open operation to complete.</span></span>  
  
### <a name="receivetimeout"></a><span data-ttu-id="38a47-130">ReceiveTimeout</span><span class="sxs-lookup"><span data-stu-id="38a47-130">ReceiveTimeout</span></span>  

 <span data-ttu-id="38a47-131">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="38a47-131">Data type: datetime</span></span>  
  
 <span data-ttu-id="38a47-132">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="38a47-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="38a47-133">Alma işleminin tamamlanabilmesi için girilen zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="38a47-133">The interval of time provided for a receive operation to complete.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="38a47-134">Düzen</span><span class="sxs-lookup"><span data-stu-id="38a47-134">Scheme</span></span>  

 <span data-ttu-id="38a47-135">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="38a47-135">Data type: string</span></span>  
  
 <span data-ttu-id="38a47-136">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="38a47-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="38a47-137">Bağlama tarafından oluşturulan kanal ve dinleyici fabrikaları tarafından kullanılan URI taşıma düzeni.</span><span class="sxs-lookup"><span data-stu-id="38a47-137">The URI transport scheme that is used by the channel and listener factories that are built by the binding.</span></span>  
  
### <a name="sendtimeout"></a><span data-ttu-id="38a47-138">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="38a47-138">SendTimeout</span></span>  

 <span data-ttu-id="38a47-139">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="38a47-139">Data type: datetime</span></span>  
  
 <span data-ttu-id="38a47-140">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="38a47-140">Access type: Read-only</span></span>  
  
 <span data-ttu-id="38a47-141">Gönderme işleminin tamamlanabilmesi için girilen zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="38a47-141">The interval of time provided for a send operation to complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38a47-142">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="38a47-142">Requirements</span></span>  
  
|<span data-ttu-id="38a47-143">MOF</span><span class="sxs-lookup"><span data-stu-id="38a47-143">MOF</span></span>|<span data-ttu-id="38a47-144">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="38a47-144">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="38a47-145">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="38a47-145">Namespace</span></span>|<span data-ttu-id="38a47-146">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="38a47-146">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="38a47-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38a47-147">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
