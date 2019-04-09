---
title: CallbackBehavior
ms.date: 03/30/2017
ms.assetid: 42acd302-2b62-4849-a2d1-a03084343ecd
ms.openlocfilehash: 9d8f4335c304d164daafeb0ad4de5b4e3bba4590
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115043"
---
# <a name="callbackbehavior"></a><span data-ttu-id="d728b-102">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="d728b-102">CallbackBehavior</span></span>
<span data-ttu-id="d728b-103">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="d728b-103">CallbackBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d728b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d728b-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="d728b-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d728b-105">Methods</span></span>  
 <span data-ttu-id="d728b-106">CallbackBehavior sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="d728b-106">The CallbackBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d728b-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d728b-107">Properties</span></span>  
 <span data-ttu-id="d728b-108">CallbackBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="d728b-108">The CallbackBehavior class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="d728b-109">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="d728b-109">AutomaticSessionShutdown</span></span>  
 <span data-ttu-id="d728b-110">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="d728b-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="d728b-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d728b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d728b-112">Bir hizmeti bir çift yönlü oturumu kapattığında true olduğunda, oturumu otomatik olarak kapatılır.</span><span class="sxs-lookup"><span data-stu-id="d728b-112">When true, the session is automatically closed when a service closes a duplex session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="d728b-113">ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="d728b-113">ConcurrencyMode</span></span>  
 <span data-ttu-id="d728b-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="d728b-114">Data type: string</span></span>  
<span data-ttu-id="d728b-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d728b-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d728b-116">Hizmet bir iş parçacığı, birden çok iş parçacığı veya yeniden girilen çağrıları destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d728b-116">Specifies whether the service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="d728b-117">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="d728b-117">IgnoreExtensionDataObject</span></span>  
 <span data-ttu-id="d728b-118">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="d728b-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="d728b-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d728b-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d728b-120">Bilinmeyen serileştirme verilerinin gönderilip gönderilmeyeceğini belirten bir değeri.</span><span class="sxs-lookup"><span data-stu-id="d728b-120">A value that specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="d728b-121">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="d728b-121">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="d728b-122">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="d728b-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="d728b-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d728b-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d728b-124">Etkin olduğunda, geri çağırma özel durumları hakkında ayrıntıları hizmete döndürülen hatalara eklenir.</span><span class="sxs-lookup"><span data-stu-id="d728b-124">When enabled, details about exceptions on the callback are attached to the faults returned to the service.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="d728b-125">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="d728b-125">MaxItemsInObjectGraph</span></span>  
 <span data-ttu-id="d728b-126">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="d728b-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="d728b-127">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d728b-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d728b-128">Serileştirilmiş nesne içinde izin verilen öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="d728b-128">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="d728b-129">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="d728b-129">UseSynchronizationContext</span></span>  
 <span data-ttu-id="d728b-130">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="d728b-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="d728b-131">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d728b-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d728b-132">Geçerli eşitleme bağlamı yürütme iş parçacığı seçmek için kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d728b-132">Specifies whether to use the current synchronization context to choose the thread of execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="d728b-133">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="d728b-133">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="d728b-134">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="d728b-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="d728b-135">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d728b-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d728b-136">Sistem veya uygulama SOAP MustUnderstand üst bilgi işleme uygulayıp uygulamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d728b-136">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d728b-137">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d728b-137">Requirements</span></span>  
  
|<span data-ttu-id="d728b-138">MOF</span><span class="sxs-lookup"><span data-stu-id="d728b-138">MOF</span></span>|<span data-ttu-id="d728b-139">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d728b-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d728b-140">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="d728b-140">Namespace</span></span>|<span data-ttu-id="d728b-141">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d728b-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d728b-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d728b-142">See also</span></span>

- <xref:System.ServiceModel.CallbackBehaviorAttribute>
