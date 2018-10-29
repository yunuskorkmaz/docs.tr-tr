---
title: Binding2
ms.date: 03/30/2017
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
ms.openlocfilehash: 84e304f3dedcbd785d6238e6cb5eb142c288b995
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50198895"
---
# <a name="binding"></a><span data-ttu-id="a2b15-102">Bağlama</span><span class="sxs-lookup"><span data-stu-id="a2b15-102">Binding</span></span>
<span data-ttu-id="a2b15-103">WMI bağlama</span><span class="sxs-lookup"><span data-stu-id="a2b15-103">wmi Binding</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2b15-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a2b15-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="a2b15-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a2b15-105">Methods</span></span>  
 <span data-ttu-id="a2b15-106">Bağlama sınıfı herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="a2b15-106">The Binding class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a2b15-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a2b15-107">Properties</span></span>  
 <span data-ttu-id="a2b15-108">Bağlama sınıfı aşağıdaki özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a2b15-108">The Binding class has the following properties.</span></span>  
  
### <a name="bindingelements"></a><span data-ttu-id="a2b15-109">BindingElements</span><span class="sxs-lookup"><span data-stu-id="a2b15-109">BindingElements</span></span>  
 <span data-ttu-id="a2b15-110">Veri türü: BindingElement dizi</span><span class="sxs-lookup"><span data-stu-id="a2b15-110">Data type: BindingElement array</span></span>  
  
 <span data-ttu-id="a2b15-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a2b15-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a2b15-112">Bağlama tarafından uygulanan bağlama öğeleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="a2b15-112">The collection of binding elements implemented by the binding.</span></span>  
  
### <a name="closetimeout"></a><span data-ttu-id="a2b15-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="a2b15-113">CloseTimeout</span></span>  
 <span data-ttu-id="a2b15-114">Veri türü: tarih/saat</span><span class="sxs-lookup"><span data-stu-id="a2b15-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="a2b15-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a2b15-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a2b15-116">Bir kapatma işlemi tamamlamak sağlanan zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="a2b15-116">The interval of time provided for a close operation to complete.</span></span>  
  
### <a name="name"></a><span data-ttu-id="a2b15-117">Ad</span><span class="sxs-lookup"><span data-stu-id="a2b15-117">Name</span></span>  
 <span data-ttu-id="a2b15-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="a2b15-118">Data type: string</span></span>  
  
 <span data-ttu-id="a2b15-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a2b15-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a2b15-120">Bağlama adı.</span><span class="sxs-lookup"><span data-stu-id="a2b15-120">The name of the binding.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="a2b15-121">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="a2b15-121">Namespace</span></span>  
 <span data-ttu-id="a2b15-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="a2b15-122">Data type: string</span></span>  
  
 <span data-ttu-id="a2b15-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a2b15-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a2b15-124">XML ad alanı bağlama.</span><span class="sxs-lookup"><span data-stu-id="a2b15-124">The XML namespace of the binding.</span></span>  
  
### <a name="opentimeout"></a><span data-ttu-id="a2b15-125">opentimeout =</span><span class="sxs-lookup"><span data-stu-id="a2b15-125">OpenTimeout</span></span>  
 <span data-ttu-id="a2b15-126">Veri türü: tarih/saat</span><span class="sxs-lookup"><span data-stu-id="a2b15-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="a2b15-127">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a2b15-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a2b15-128">Sağlanan bir açık bir işlemin tamamlanması zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="a2b15-128">The interval of time provided for an open operation to complete.</span></span>  
  
### <a name="receivetimeout"></a><span data-ttu-id="a2b15-129">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="a2b15-129">ReceiveTimeout</span></span>  
 <span data-ttu-id="a2b15-130">Veri türü: tarih/saat</span><span class="sxs-lookup"><span data-stu-id="a2b15-130">Data type: datetime</span></span>  
  
 <span data-ttu-id="a2b15-131">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a2b15-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a2b15-132">Tamamlamak alma işlemi için belirtilen zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="a2b15-132">The interval of time provided for a receive operation to complete.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="a2b15-133">Düzen</span><span class="sxs-lookup"><span data-stu-id="a2b15-133">Scheme</span></span>  
 <span data-ttu-id="a2b15-134">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="a2b15-134">Data type: string</span></span>  
  
 <span data-ttu-id="a2b15-135">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a2b15-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a2b15-136">Bağlama tarafından oluşturulan kanal ve dinleyici fabrikası tarafından kullanılan URI aktarma düzenini.</span><span class="sxs-lookup"><span data-stu-id="a2b15-136">The URI transport scheme that is used by the channel and listener factories that are built by the binding.</span></span>  
  
### <a name="sendtimeout"></a><span data-ttu-id="a2b15-137">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="a2b15-137">SendTimeout</span></span>  
 <span data-ttu-id="a2b15-138">Veri türü: tarih/saat</span><span class="sxs-lookup"><span data-stu-id="a2b15-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="a2b15-139">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a2b15-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a2b15-140">Tamamlamak için bir gönderme işlemi belirtilen zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="a2b15-140">The interval of time provided for a send operation to complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2b15-141">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a2b15-141">Requirements</span></span>  
  
|<span data-ttu-id="a2b15-142">MOF</span><span class="sxs-lookup"><span data-stu-id="a2b15-142">MOF</span></span>|<span data-ttu-id="a2b15-143">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="a2b15-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a2b15-144">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="a2b15-144">Namespace</span></span>|<span data-ttu-id="a2b15-145">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a2b15-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a2b15-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a2b15-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>
