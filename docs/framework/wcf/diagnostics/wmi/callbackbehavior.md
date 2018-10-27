---
title: CallbackBehavior
ms.date: 03/30/2017
ms.assetid: 42acd302-2b62-4849-a2d1-a03084343ecd
ms.openlocfilehash: 38a38a71db2927d187ccdd93e5e364b0d4955373
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452618"
---
# <a name="callbackbehavior"></a><span data-ttu-id="d14f4-102">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="d14f4-102">CallbackBehavior</span></span>
<span data-ttu-id="d14f4-103">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="d14f4-103">CallbackBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d14f4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d14f4-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="d14f4-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d14f4-105">Methods</span></span>  
 <span data-ttu-id="d14f4-106">CallbackBehavior sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="d14f4-106">The CallbackBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d14f4-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d14f4-107">Properties</span></span>  
 <span data-ttu-id="d14f4-108">CallbackBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="d14f4-108">The CallbackBehavior class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="d14f4-109">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="d14f4-109">AutomaticSessionShutdown</span></span>  
 <span data-ttu-id="d14f4-110">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="d14f4-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="d14f4-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d14f4-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d14f4-112">Bir hizmeti bir çift yönlü oturumu kapattığında true olduğunda, oturumu otomatik olarak kapatılır.</span><span class="sxs-lookup"><span data-stu-id="d14f4-112">When true, the session is automatically closed when a service closes a duplex session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="d14f4-113">ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="d14f4-113">ConcurrencyMode</span></span>  
 <span data-ttu-id="d14f4-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="d14f4-114">Data type: string</span></span>  
<span data-ttu-id="d14f4-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d14f4-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d14f4-116">Hizmet bir iş parçacığı, birden çok iş parçacığı veya yeniden girilen çağrıları destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d14f4-116">Specifies whether the service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="d14f4-117">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="d14f4-117">IgnoreExtensionDataObject</span></span>  
 <span data-ttu-id="d14f4-118">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="d14f4-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="d14f4-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d14f4-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d14f4-120">Bilinmeyen serileştirme verilerinin gönderilip gönderilmeyeceğini belirten bir değeri.</span><span class="sxs-lookup"><span data-stu-id="d14f4-120">A value that specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="d14f4-121">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="d14f4-121">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="d14f4-122">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="d14f4-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="d14f4-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d14f4-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d14f4-124">Etkin olduğunda, geri çağırma özel durumları hakkında ayrıntıları hizmete döndürülen hatalara eklenir.</span><span class="sxs-lookup"><span data-stu-id="d14f4-124">When enabled, details about exceptions on the callback are attached to the faults returned to the service.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="d14f4-125">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="d14f4-125">MaxItemsInObjectGraph</span></span>  
 <span data-ttu-id="d14f4-126">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="d14f4-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="d14f4-127">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d14f4-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d14f4-128">Serileştirilmiş nesne içinde izin verilen öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="d14f4-128">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="d14f4-129">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="d14f4-129">UseSynchronizationContext</span></span>  
 <span data-ttu-id="d14f4-130">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="d14f4-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="d14f4-131">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d14f4-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d14f4-132">Geçerli eşitleme bağlamı yürütme iş parçacığı seçmek için kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d14f4-132">Specifies whether to use the current synchronization context to choose the thread of execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="d14f4-133">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="d14f4-133">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="d14f4-134">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="d14f4-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="d14f4-135">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d14f4-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d14f4-136">Sistem veya uygulama SOAP MustUnderstand üst bilgi işleme uygulayıp uygulamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d14f4-136">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d14f4-137">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d14f4-137">Requirements</span></span>  
  
|<span data-ttu-id="d14f4-138">MOF</span><span class="sxs-lookup"><span data-stu-id="d14f4-138">MOF</span></span>|<span data-ttu-id="d14f4-139">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d14f4-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d14f4-140">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="d14f4-140">Namespace</span></span>|<span data-ttu-id="d14f4-141">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d14f4-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d14f4-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d14f4-142">See Also</span></span>  
 <xref:System.ServiceModel.CallbackBehaviorAttribute>
