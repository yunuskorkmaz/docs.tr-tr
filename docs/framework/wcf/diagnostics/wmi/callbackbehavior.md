---
title: CallbackBehavior
ms.date: 03/30/2017
ms.assetid: 42acd302-2b62-4849-a2d1-a03084343ecd
ms.openlocfilehash: cec9005a099247671dbebaacc0b242ca8d7a0144
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96269656"
---
# <a name="callbackbehavior"></a><span data-ttu-id="b7a49-102">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="b7a49-102">CallbackBehavior</span></span>

<span data-ttu-id="b7a49-103">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="b7a49-103">CallbackBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7a49-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="b7a49-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="b7a49-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b7a49-105">Methods</span></span>  

 <span data-ttu-id="b7a49-106">CallbackBehavior sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="b7a49-106">The CallbackBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b7a49-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="b7a49-107">Properties</span></span>  

 <span data-ttu-id="b7a49-108">CallbackBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="b7a49-108">The CallbackBehavior class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="b7a49-109">Automaticsessionkapanıyor</span><span class="sxs-lookup"><span data-stu-id="b7a49-109">AutomaticSessionShutdown</span></span>  

 <span data-ttu-id="b7a49-110">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="b7a49-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="b7a49-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="b7a49-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b7a49-112">Doğru olduğunda, bir hizmet bir çift yönlü oturumu kapattığında oturum otomatik olarak kapatılır.</span><span class="sxs-lookup"><span data-stu-id="b7a49-112">When true, the session is automatically closed when a service closes a duplex session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="b7a49-113">ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="b7a49-113">ConcurrencyMode</span></span>  

 <span data-ttu-id="b7a49-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="b7a49-114">Data type: string</span></span>  
<span data-ttu-id="b7a49-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="b7a49-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b7a49-116">Hizmetin bir iş parçacığını, birden çok iş parçacığını veya yer aldığı çağrıları destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b7a49-116">Specifies whether the service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="b7a49-117">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="b7a49-117">IgnoreExtensionDataObject</span></span>  

 <span data-ttu-id="b7a49-118">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="b7a49-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="b7a49-119">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="b7a49-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b7a49-120">Bilinmeyen serileştirme verilerinin hatta gönderileceğini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="b7a49-120">A value that specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="b7a49-121">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="b7a49-121">IncludeExceptionDetailInFaults</span></span>  

 <span data-ttu-id="b7a49-122">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="b7a49-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="b7a49-123">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="b7a49-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b7a49-124">Etkinleştirildiğinde, geri çağırmada özel durumlar hakkındaki ayrıntılar, hizmete döndürülen hatalara eklenir.</span><span class="sxs-lookup"><span data-stu-id="b7a49-124">When enabled, details about exceptions on the callback are attached to the faults returned to the service.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="b7a49-125">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="b7a49-125">MaxItemsInObjectGraph</span></span>  

 <span data-ttu-id="b7a49-126">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="b7a49-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="b7a49-127">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="b7a49-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b7a49-128">Seri hale getirilen bir nesnede izin verilen en fazla öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="b7a49-128">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="b7a49-129">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="b7a49-129">UseSynchronizationContext</span></span>  

 <span data-ttu-id="b7a49-130">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="b7a49-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="b7a49-131">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="b7a49-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b7a49-132">Yürütmenin iş parçacığını seçmek için geçerli eşitleme kapsamının kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b7a49-132">Specifies whether to use the current synchronization context to choose the thread of execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="b7a49-133">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="b7a49-133">ValidateMustUnderstand</span></span>  

 <span data-ttu-id="b7a49-134">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="b7a49-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="b7a49-135">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="b7a49-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b7a49-136">Sistemin ya da uygulamanın SOAP MustUnderstand üst bilgi işlemeyi zorunlu yapıp uygulamamadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b7a49-136">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7a49-137">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b7a49-137">Requirements</span></span>  
  
|<span data-ttu-id="b7a49-138">MOF</span><span class="sxs-lookup"><span data-stu-id="b7a49-138">MOF</span></span>|<span data-ttu-id="b7a49-139">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b7a49-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b7a49-140">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="b7a49-140">Namespace</span></span>|<span data-ttu-id="b7a49-141">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="b7a49-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b7a49-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7a49-142">See also</span></span>

- <xref:System.ServiceModel.CallbackBehaviorAttribute>
