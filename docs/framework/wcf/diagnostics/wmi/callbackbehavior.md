---
title: CallbackBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42acd302-2b62-4849-a2d1-a03084343ecd
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5387e197cdf26a393ba23fd5696eb095dfd17a70
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="callbackbehavior"></a><span data-ttu-id="185f8-102">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="185f8-102">CallbackBehavior</span></span>
<span data-ttu-id="185f8-103">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="185f8-103">CallbackBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="185f8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="185f8-104">Syntax</span></span>  
  
```  
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
  
## <a name="methods"></a><span data-ttu-id="185f8-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="185f8-105">Methods</span></span>  
 <span data-ttu-id="185f8-106">CallbackBehavior sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="185f8-106">The CallbackBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="185f8-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="185f8-107">Properties</span></span>  
 <span data-ttu-id="185f8-108">CallbackBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="185f8-108">The CallbackBehavior class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="185f8-109">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="185f8-109">AutomaticSessionShutdown</span></span>  
 <span data-ttu-id="185f8-110">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="185f8-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="185f8-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="185f8-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="185f8-112">Bir hizmet çift yönlü oturumu kapattığında doğru olduğunda, oturumu otomatik olarak kapatılır.</span><span class="sxs-lookup"><span data-stu-id="185f8-112">When true, the session is automatically closed when a service closes a duplex session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="185f8-113">ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="185f8-113">ConcurrencyMode</span></span>  
 <span data-ttu-id="185f8-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="185f8-114">Data type: string</span></span>  
<span data-ttu-id="185f8-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="185f8-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="185f8-116">Hizmet bir iş parçacığı, birden çok iş parçacığı veya desteklemeyeceğini aramalar destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="185f8-116">Specifies whether the service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="185f8-117">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="185f8-117">IgnoreExtensionDataObject</span></span>  
 <span data-ttu-id="185f8-118">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="185f8-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="185f8-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="185f8-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="185f8-120">Bilinmeyen seri hale getirme verilerinin gönderilip gönderilmeyeceğini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="185f8-120">A value that specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="185f8-121">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="185f8-121">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="185f8-122">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="185f8-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="185f8-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="185f8-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="185f8-124">Etkinleştirildiğinde, hakkındaki geri arama özel durumların ayrıntıları hizmete döndürülen hatalara eklenir.</span><span class="sxs-lookup"><span data-stu-id="185f8-124">When enabled, details about exceptions on the callback are attached to the faults returned to the service.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="185f8-125">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="185f8-125">MaxItemsInObjectGraph</span></span>  
 <span data-ttu-id="185f8-126">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="185f8-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="185f8-127">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="185f8-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="185f8-128">Serileştirilmiş nesne içinde izin verilen öğe maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="185f8-128">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="185f8-129">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="185f8-129">UseSynchronizationContext</span></span>  
 <span data-ttu-id="185f8-130">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="185f8-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="185f8-131">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="185f8-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="185f8-132">Geçerli eşitleme bağlamı yürütme iş parçacığı seçmek için kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="185f8-132">Specifies whether to use the current synchronization context to choose the thread of execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="185f8-133">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="185f8-133">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="185f8-134">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="185f8-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="185f8-135">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="185f8-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="185f8-136">Sistem veya uygulama SOAP MustUnderstand üstbilgi işlemeyi zorunlu olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="185f8-136">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="185f8-137">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="185f8-137">Requirements</span></span>  
  
|<span data-ttu-id="185f8-138">MOF</span><span class="sxs-lookup"><span data-stu-id="185f8-138">MOF</span></span>|<span data-ttu-id="185f8-139">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="185f8-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="185f8-140">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="185f8-140">Namespace</span></span>|<span data-ttu-id="185f8-141">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="185f8-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="185f8-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="185f8-142">See Also</span></span>  
 <xref:System.ServiceModel.CallbackBehaviorAttribute>
