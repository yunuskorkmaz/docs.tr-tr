---
title: Binding2
ms.date: 03/30/2017
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
ms.openlocfilehash: b72bd3903b7139c4adf2a8bd0ced6c34e7285640
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274302"
---
# <a name="binding"></a><span data-ttu-id="daf39-102">Bağlama</span><span class="sxs-lookup"><span data-stu-id="daf39-102">Binding</span></span>

<span data-ttu-id="daf39-103">WMI bağlama</span><span class="sxs-lookup"><span data-stu-id="daf39-103">wmi Binding</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="daf39-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="daf39-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="daf39-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="daf39-105">Methods</span></span>  

 <span data-ttu-id="daf39-106">Bağlama sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="daf39-106">The Binding class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="daf39-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="daf39-107">Properties</span></span>  

 <span data-ttu-id="daf39-108">Bağlama sınıfı aşağıdaki özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="daf39-108">The Binding class has the following properties.</span></span>  
  
### <a name="bindingelements"></a><span data-ttu-id="daf39-109">BindingElements</span><span class="sxs-lookup"><span data-stu-id="daf39-109">BindingElements</span></span>  

 <span data-ttu-id="daf39-110">Veri türü: BindingElement dizisi</span><span class="sxs-lookup"><span data-stu-id="daf39-110">Data type: BindingElement array</span></span>  
  
 <span data-ttu-id="daf39-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="daf39-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="daf39-112">Bağlama tarafından uygulanan bağlama öğelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="daf39-112">The collection of binding elements implemented by the binding.</span></span>  
  
### <a name="closetimeout"></a><span data-ttu-id="daf39-113">CloseTimeout</span><span class="sxs-lookup"><span data-stu-id="daf39-113">CloseTimeout</span></span>  

 <span data-ttu-id="daf39-114">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="daf39-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="daf39-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="daf39-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="daf39-116">Bir kapatma işleminin tamamlanabilmesi için girilen zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="daf39-116">The interval of time provided for a close operation to complete.</span></span>  
  
### <a name="name"></a><span data-ttu-id="daf39-117">Adı</span><span class="sxs-lookup"><span data-stu-id="daf39-117">Name</span></span>  

 <span data-ttu-id="daf39-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="daf39-118">Data type: string</span></span>  
  
 <span data-ttu-id="daf39-119">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="daf39-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="daf39-120">Bağlamanın adı.</span><span class="sxs-lookup"><span data-stu-id="daf39-120">The name of the binding.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="daf39-121">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="daf39-121">Namespace</span></span>  

 <span data-ttu-id="daf39-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="daf39-122">Data type: string</span></span>  
  
 <span data-ttu-id="daf39-123">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="daf39-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="daf39-124">Bağlamanın XML ad alanı.</span><span class="sxs-lookup"><span data-stu-id="daf39-124">The XML namespace of the binding.</span></span>  
  
### <a name="opentimeout"></a><span data-ttu-id="daf39-125">OpenTimeout</span><span class="sxs-lookup"><span data-stu-id="daf39-125">OpenTimeout</span></span>  

 <span data-ttu-id="daf39-126">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="daf39-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="daf39-127">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="daf39-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="daf39-128">Bir açık işlemin tamamlanabilmesi için girilen zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="daf39-128">The interval of time provided for an open operation to complete.</span></span>  
  
### <a name="receivetimeout"></a><span data-ttu-id="daf39-129">ReceiveTimeout</span><span class="sxs-lookup"><span data-stu-id="daf39-129">ReceiveTimeout</span></span>  

 <span data-ttu-id="daf39-130">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="daf39-130">Data type: datetime</span></span>  
  
 <span data-ttu-id="daf39-131">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="daf39-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="daf39-132">Alma işleminin tamamlanabilmesi için girilen zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="daf39-132">The interval of time provided for a receive operation to complete.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="daf39-133">Düzen</span><span class="sxs-lookup"><span data-stu-id="daf39-133">Scheme</span></span>  

 <span data-ttu-id="daf39-134">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="daf39-134">Data type: string</span></span>  
  
 <span data-ttu-id="daf39-135">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="daf39-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="daf39-136">Bağlama tarafından oluşturulan kanal ve dinleyici fabrikaları tarafından kullanılan URI taşıma düzeni.</span><span class="sxs-lookup"><span data-stu-id="daf39-136">The URI transport scheme that is used by the channel and listener factories that are built by the binding.</span></span>  
  
### <a name="sendtimeout"></a><span data-ttu-id="daf39-137">Binding üstündeki SendTimeout</span><span class="sxs-lookup"><span data-stu-id="daf39-137">SendTimeout</span></span>  

 <span data-ttu-id="daf39-138">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="daf39-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="daf39-139">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="daf39-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="daf39-140">Gönderme işleminin tamamlanabilmesi için girilen zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="daf39-140">The interval of time provided for a send operation to complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="daf39-141">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="daf39-141">Requirements</span></span>  
  
|<span data-ttu-id="daf39-142">MOF</span><span class="sxs-lookup"><span data-stu-id="daf39-142">MOF</span></span>|<span data-ttu-id="daf39-143">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="daf39-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="daf39-144">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="daf39-144">Namespace</span></span>|<span data-ttu-id="daf39-145">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="daf39-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="daf39-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="daf39-146">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
