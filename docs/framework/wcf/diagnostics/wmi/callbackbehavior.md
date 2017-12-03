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
ms.openlocfilehash: 7c10d9e26f86fa569b1a607c9b755f32ee97792a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="callbackbehavior"></a><span data-ttu-id="1c9a1-102">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="1c9a1-102">CallbackBehavior</span></span>
<span data-ttu-id="1c9a1-103">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="1c9a1-103">CallbackBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c9a1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1c9a1-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="1c9a1-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1c9a1-105">Methods</span></span>  
 <span data-ttu-id="1c9a1-106">CallbackBehavior sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="1c9a1-106">The CallbackBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1c9a1-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="1c9a1-107">Properties</span></span>  
 <span data-ttu-id="1c9a1-108">CallbackBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="1c9a1-108">The CallbackBehavior class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="1c9a1-109">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="1c9a1-109">AutomaticSessionShutdown</span></span>  
 <span data-ttu-id="1c9a1-110">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="1c9a1-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="1c9a1-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="1c9a1-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1c9a1-112">Bir hizmet çift yönlü oturumu kapattığında doğru olduğunda, oturumu otomatik olarak kapatılır.</span><span class="sxs-lookup"><span data-stu-id="1c9a1-112">When true, the session is automatically closed when a service closes a duplex session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="1c9a1-113">ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="1c9a1-113">ConcurrencyMode</span></span>  
 <span data-ttu-id="1c9a1-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="1c9a1-114">Data type: string</span></span>  
<span data-ttu-id="1c9a1-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="1c9a1-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1c9a1-116">Hizmet bir iş parçacığı, birden çok iş parçacığı veya desteklemeyeceğini aramalar destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1c9a1-116">Specifies whether the service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="1c9a1-117">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="1c9a1-117">IgnoreExtensionDataObject</span></span>  
 <span data-ttu-id="1c9a1-118">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="1c9a1-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="1c9a1-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="1c9a1-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1c9a1-120">Bilinmeyen seri hale getirme verilerinin gönderilip gönderilmeyeceğini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="1c9a1-120">A value that specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="1c9a1-121">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="1c9a1-121">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="1c9a1-122">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="1c9a1-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="1c9a1-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="1c9a1-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1c9a1-124">Etkinleştirildiğinde, hakkındaki geri arama özel durumların ayrıntıları hizmete döndürülen hatalara eklenir.</span><span class="sxs-lookup"><span data-stu-id="1c9a1-124">When enabled, details about exceptions on the callback are attached to the faults returned to the service.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="1c9a1-125">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="1c9a1-125">MaxItemsInObjectGraph</span></span>  
 <span data-ttu-id="1c9a1-126">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="1c9a1-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="1c9a1-127">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="1c9a1-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1c9a1-128">Serileştirilmiş nesne içinde izin verilen öğe maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="1c9a1-128">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="1c9a1-129">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="1c9a1-129">UseSynchronizationContext</span></span>  
 <span data-ttu-id="1c9a1-130">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="1c9a1-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="1c9a1-131">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="1c9a1-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1c9a1-132">Geçerli eşitleme bağlamı yürütme iş parçacığı seçmek için kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1c9a1-132">Specifies whether to use the current synchronization context to choose the thread of execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="1c9a1-133">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="1c9a1-133">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="1c9a1-134">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="1c9a1-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="1c9a1-135">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="1c9a1-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1c9a1-136">Sistem veya uygulama SOAP MustUnderstand üstbilgi işlemeyi zorunlu olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1c9a1-136">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c9a1-137">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1c9a1-137">Requirements</span></span>  
  
|<span data-ttu-id="1c9a1-138">MOF</span><span class="sxs-lookup"><span data-stu-id="1c9a1-138">MOF</span></span>|<span data-ttu-id="1c9a1-139">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="1c9a1-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="1c9a1-140">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="1c9a1-140">Namespace</span></span>|<span data-ttu-id="1c9a1-141">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1c9a1-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1c9a1-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1c9a1-142">See Also</span></span>  
 <xref:System.ServiceModel.CallbackBehaviorAttribute>
