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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9df9629e280a2aec6acf93773e09384e763280ca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="callbackbehavior"></a><span data-ttu-id="6dca4-102">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="6dca4-102">CallbackBehavior</span></span>
<span data-ttu-id="6dca4-103">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="6dca4-103">CallbackBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dca4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6dca4-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="6dca4-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6dca4-105">Methods</span></span>  
 <span data-ttu-id="6dca4-106">CallbackBehavior sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="6dca4-106">The CallbackBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="6dca4-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="6dca4-107">Properties</span></span>  
 <span data-ttu-id="6dca4-108">CallbackBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="6dca4-108">The CallbackBehavior class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="6dca4-109">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="6dca4-109">AutomaticSessionShutdown</span></span>  
 <span data-ttu-id="6dca4-110">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="6dca4-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="6dca4-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="6dca4-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6dca4-112">Bir hizmet çift yönlü oturumu kapattığında doğru olduğunda, oturumu otomatik olarak kapatılır.</span><span class="sxs-lookup"><span data-stu-id="6dca4-112">When true, the session is automatically closed when a service closes a duplex session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="6dca4-113">ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="6dca4-113">ConcurrencyMode</span></span>  
 <span data-ttu-id="6dca4-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="6dca4-114">Data type: string</span></span>  
<span data-ttu-id="6dca4-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="6dca4-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6dca4-116">Hizmet bir iş parçacığı, birden çok iş parçacığı veya desteklemeyeceğini aramalar destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6dca4-116">Specifies whether the service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="6dca4-117">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="6dca4-117">IgnoreExtensionDataObject</span></span>  
 <span data-ttu-id="6dca4-118">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="6dca4-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="6dca4-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="6dca4-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6dca4-120">Bilinmeyen seri hale getirme verilerinin gönderilip gönderilmeyeceğini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="6dca4-120">A value that specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="6dca4-121">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="6dca4-121">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="6dca4-122">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="6dca4-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="6dca4-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="6dca4-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6dca4-124">Etkinleştirildiğinde, hakkındaki geri arama özel durumların ayrıntıları hizmete döndürülen hatalara eklenir.</span><span class="sxs-lookup"><span data-stu-id="6dca4-124">When enabled, details about exceptions on the callback are attached to the faults returned to the service.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="6dca4-125">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="6dca4-125">MaxItemsInObjectGraph</span></span>  
 <span data-ttu-id="6dca4-126">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="6dca4-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="6dca4-127">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="6dca4-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6dca4-128">Serileştirilmiş nesne içinde izin verilen öğe maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="6dca4-128">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="6dca4-129">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="6dca4-129">UseSynchronizationContext</span></span>  
 <span data-ttu-id="6dca4-130">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="6dca4-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="6dca4-131">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="6dca4-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6dca4-132">Geçerli eşitleme bağlamı yürütme iş parçacığı seçmek için kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6dca4-132">Specifies whether to use the current synchronization context to choose the thread of execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="6dca4-133">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="6dca4-133">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="6dca4-134">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="6dca4-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="6dca4-135">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="6dca4-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6dca4-136">Sistem veya uygulama SOAP MustUnderstand üstbilgi işlemeyi zorunlu olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6dca4-136">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6dca4-137">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6dca4-137">Requirements</span></span>  
  
|<span data-ttu-id="6dca4-138">MOF</span><span class="sxs-lookup"><span data-stu-id="6dca4-138">MOF</span></span>|<span data-ttu-id="6dca4-139">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="6dca4-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="6dca4-140">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="6dca4-140">Namespace</span></span>|<span data-ttu-id="6dca4-141">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="6dca4-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6dca4-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6dca4-142">See Also</span></span>  
 <xref:System.ServiceModel.CallbackBehaviorAttribute>
