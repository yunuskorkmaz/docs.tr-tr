---
title: Binding2
ms.date: 03/30/2017
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
ms.openlocfilehash: a040cc6e12833d2c737eb14c591300e5873ddce7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61964087"
---
# <a name="binding"></a><span data-ttu-id="966f3-102">Bağlama</span><span class="sxs-lookup"><span data-stu-id="966f3-102">Binding</span></span>
<span data-ttu-id="966f3-103">WMI bağlama</span><span class="sxs-lookup"><span data-stu-id="966f3-103">wmi Binding</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="966f3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="966f3-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="966f3-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="966f3-105">Methods</span></span>  
 <span data-ttu-id="966f3-106">Bağlama sınıfı herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="966f3-106">The Binding class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="966f3-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="966f3-107">Properties</span></span>  
 <span data-ttu-id="966f3-108">Bağlama sınıfı aşağıdaki özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="966f3-108">The Binding class has the following properties.</span></span>  
  
### <a name="bindingelements"></a><span data-ttu-id="966f3-109">BindingElements</span><span class="sxs-lookup"><span data-stu-id="966f3-109">BindingElements</span></span>  
 <span data-ttu-id="966f3-110">Veri türü: BindingElement dizi</span><span class="sxs-lookup"><span data-stu-id="966f3-110">Data type: BindingElement array</span></span>  
  
 <span data-ttu-id="966f3-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="966f3-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="966f3-112">Bağlama tarafından uygulanan bağlama öğeleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="966f3-112">The collection of binding elements implemented by the binding.</span></span>  
  
### <a name="closetimeout"></a><span data-ttu-id="966f3-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="966f3-113">CloseTimeout</span></span>  
 <span data-ttu-id="966f3-114">Veri türü: tarih/saat</span><span class="sxs-lookup"><span data-stu-id="966f3-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="966f3-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="966f3-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="966f3-116">Bir kapatma işlemi tamamlamak sağlanan zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="966f3-116">The interval of time provided for a close operation to complete.</span></span>  
  
### <a name="name"></a><span data-ttu-id="966f3-117">Ad</span><span class="sxs-lookup"><span data-stu-id="966f3-117">Name</span></span>  
 <span data-ttu-id="966f3-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="966f3-118">Data type: string</span></span>  
  
 <span data-ttu-id="966f3-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="966f3-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="966f3-120">Bağlama adı.</span><span class="sxs-lookup"><span data-stu-id="966f3-120">The name of the binding.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="966f3-121">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="966f3-121">Namespace</span></span>  
 <span data-ttu-id="966f3-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="966f3-122">Data type: string</span></span>  
  
 <span data-ttu-id="966f3-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="966f3-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="966f3-124">XML ad alanı bağlama.</span><span class="sxs-lookup"><span data-stu-id="966f3-124">The XML namespace of the binding.</span></span>  
  
### <a name="opentimeout"></a><span data-ttu-id="966f3-125">opentimeout =</span><span class="sxs-lookup"><span data-stu-id="966f3-125">OpenTimeout</span></span>  
 <span data-ttu-id="966f3-126">Veri türü: tarih/saat</span><span class="sxs-lookup"><span data-stu-id="966f3-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="966f3-127">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="966f3-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="966f3-128">Sağlanan bir açık bir işlemin tamamlanması zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="966f3-128">The interval of time provided for an open operation to complete.</span></span>  
  
### <a name="receivetimeout"></a><span data-ttu-id="966f3-129">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="966f3-129">ReceiveTimeout</span></span>  
 <span data-ttu-id="966f3-130">Veri türü: tarih/saat</span><span class="sxs-lookup"><span data-stu-id="966f3-130">Data type: datetime</span></span>  
  
 <span data-ttu-id="966f3-131">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="966f3-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="966f3-132">Tamamlamak alma işlemi için belirtilen zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="966f3-132">The interval of time provided for a receive operation to complete.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="966f3-133">Düzen</span><span class="sxs-lookup"><span data-stu-id="966f3-133">Scheme</span></span>  
 <span data-ttu-id="966f3-134">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="966f3-134">Data type: string</span></span>  
  
 <span data-ttu-id="966f3-135">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="966f3-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="966f3-136">Bağlama tarafından oluşturulan kanal ve dinleyici fabrikası tarafından kullanılan URI aktarma düzenini.</span><span class="sxs-lookup"><span data-stu-id="966f3-136">The URI transport scheme that is used by the channel and listener factories that are built by the binding.</span></span>  
  
### <a name="sendtimeout"></a><span data-ttu-id="966f3-137">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="966f3-137">SendTimeout</span></span>  
 <span data-ttu-id="966f3-138">Veri türü: tarih/saat</span><span class="sxs-lookup"><span data-stu-id="966f3-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="966f3-139">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="966f3-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="966f3-140">Tamamlamak için bir gönderme işlemi belirtilen zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="966f3-140">The interval of time provided for a send operation to complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="966f3-141">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="966f3-141">Requirements</span></span>  
  
|<span data-ttu-id="966f3-142">MOF</span><span class="sxs-lookup"><span data-stu-id="966f3-142">MOF</span></span>|<span data-ttu-id="966f3-143">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="966f3-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="966f3-144">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="966f3-144">Namespace</span></span>|<span data-ttu-id="966f3-145">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="966f3-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="966f3-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="966f3-146">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
