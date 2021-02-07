---
description: 'Daha fazla bilgi edinin: CallbackBehavior'
title: CallbackBehavior
ms.date: 03/30/2017
ms.assetid: 42acd302-2b62-4849-a2d1-a03084343ecd
ms.openlocfilehash: fa9e403324afe818e247d1f751cce0ce7d5a6fb6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757767"
---
# <a name="callbackbehavior"></a><span data-ttu-id="54a0b-103">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="54a0b-103">CallbackBehavior</span></span>

<span data-ttu-id="54a0b-104">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="54a0b-104">CallbackBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54a0b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="54a0b-105">Syntax</span></span>  
  
```csharp
class CallbackBehavior : Behavior  
{  
  boolean AutomaticSessionShutdown;  
  string ConcurrencyMode;  
  boolean IgnoreExtensionDataObject;  
  boolean IncludeExceptionDetailInFaults;  
  boolean MaxItemsInObjectGraph;  
  boolean UseSynchronizationContext;  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="54a0b-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="54a0b-106">Methods</span></span>  

 <span data-ttu-id="54a0b-107">CallbackBehavior sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="54a0b-107">The CallbackBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="54a0b-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="54a0b-108">Properties</span></span>  

 <span data-ttu-id="54a0b-109">CallbackBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="54a0b-109">The CallbackBehavior class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="54a0b-110">Automaticsessionkapanıyor</span><span class="sxs-lookup"><span data-stu-id="54a0b-110">AutomaticSessionShutdown</span></span>  

 <span data-ttu-id="54a0b-111">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="54a0b-111">Data type: boolean</span></span>  
  
 <span data-ttu-id="54a0b-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="54a0b-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="54a0b-113">Doğru olduğunda, bir hizmet bir çift yönlü oturumu kapattığında oturum otomatik olarak kapatılır.</span><span class="sxs-lookup"><span data-stu-id="54a0b-113">When true, the session is automatically closed when a service closes a duplex session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="54a0b-114">ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="54a0b-114">ConcurrencyMode</span></span>  

 <span data-ttu-id="54a0b-115">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="54a0b-115">Data type: string</span></span>  
<span data-ttu-id="54a0b-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="54a0b-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="54a0b-117">Hizmetin bir iş parçacığını, birden çok iş parçacığını veya yer aldığı çağrıları destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="54a0b-117">Specifies whether the service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="54a0b-118">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="54a0b-118">IgnoreExtensionDataObject</span></span>  

 <span data-ttu-id="54a0b-119">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="54a0b-119">Data type: boolean</span></span>  
  
 <span data-ttu-id="54a0b-120">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="54a0b-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="54a0b-121">Bilinmeyen serileştirme verilerinin hatta gönderileceğini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="54a0b-121">A value that specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="54a0b-122">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="54a0b-122">IncludeExceptionDetailInFaults</span></span>  

 <span data-ttu-id="54a0b-123">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="54a0b-123">Data type: boolean</span></span>  
  
 <span data-ttu-id="54a0b-124">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="54a0b-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="54a0b-125">Etkinleştirildiğinde, geri çağırmada özel durumlar hakkındaki ayrıntılar, hizmete döndürülen hatalara eklenir.</span><span class="sxs-lookup"><span data-stu-id="54a0b-125">When enabled, details about exceptions on the callback are attached to the faults returned to the service.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="54a0b-126">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="54a0b-126">MaxItemsInObjectGraph</span></span>  

 <span data-ttu-id="54a0b-127">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="54a0b-127">Data type: boolean</span></span>  
  
 <span data-ttu-id="54a0b-128">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="54a0b-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="54a0b-129">Seri hale getirilen bir nesnede izin verilen en fazla öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="54a0b-129">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="54a0b-130">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="54a0b-130">UseSynchronizationContext</span></span>  

 <span data-ttu-id="54a0b-131">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="54a0b-131">Data type: boolean</span></span>  
  
 <span data-ttu-id="54a0b-132">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="54a0b-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="54a0b-133">Yürütmenin iş parçacığını seçmek için geçerli eşitleme kapsamının kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="54a0b-133">Specifies whether to use the current synchronization context to choose the thread of execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="54a0b-134">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="54a0b-134">ValidateMustUnderstand</span></span>  

 <span data-ttu-id="54a0b-135">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="54a0b-135">Data type: boolean</span></span>  
  
 <span data-ttu-id="54a0b-136">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="54a0b-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="54a0b-137">Sistemin ya da uygulamanın SOAP MustUnderstand üst bilgi işlemeyi zorunlu yapıp uygulamamadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="54a0b-137">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54a0b-138">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="54a0b-138">Requirements</span></span>  
  
|<span data-ttu-id="54a0b-139">MOF</span><span class="sxs-lookup"><span data-stu-id="54a0b-139">MOF</span></span>|<span data-ttu-id="54a0b-140">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="54a0b-140">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="54a0b-141">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="54a0b-141">Namespace</span></span>|<span data-ttu-id="54a0b-142">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="54a0b-142">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="54a0b-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54a0b-143">See also</span></span>

- <xref:System.ServiceModel.CallbackBehaviorAttribute>
