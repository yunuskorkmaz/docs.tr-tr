---
title: ServiceBehaviorAttribute
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5faa266f-587f-4e03-828d-1c7dd5acfe65
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f7401acd5aefcb7a8c02ea6c05a94374e41d9b9d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="servicebehaviorattribute"></a><span data-ttu-id="d7ea2-102">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="d7ea2-102">ServiceBehaviorAttribute</span></span>
<span data-ttu-id="d7ea2-103">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="d7ea2-103">ServiceBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7ea2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d7ea2-104">Syntax</span></span>  
  
```  
class ServiceBehaviorAttribute : Behavior  
{  
  boolean AutomaticSessionShutdown;  
  string ConcurrencyMode;  
  string ConfigurationName;  
  boolean IgnoreExtensionDataObject;  
  boolean IncludeExceptionDetailInFaults;  
  string InstanceContextMode;  
  sint32 MaxItemsInObjectGraph;  
  string Name;  
  string Namespace;  
  boolean ReleaseServiceInstanceOnTransactionComplete;  
  boolean TransactionAutoCompleteOnSessionClose;  
  string TransactionIsolationLevel;  
  datetime TransactionTimeout;  
  boolean UseSynchronizationContext;  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d7ea2-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d7ea2-105">Methods</span></span>  
 <span data-ttu-id="d7ea2-106">ServiceBehaviorAttribute sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="d7ea2-106">The ServiceBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d7ea2-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d7ea2-107">Properties</span></span>  
 <span data-ttu-id="d7ea2-108">ServiceBehaviorAttribute sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="d7ea2-108">The ServiceBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="d7ea2-109">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="d7ea2-109">AutomaticSessionShutdown</span></span>  
 <span data-ttu-id="d7ea2-110">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="d7ea2-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="d7ea2-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d7ea2-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d7ea2-112">Otomatik olarak bir istemci bir çıktı oturumu kapattığı zaman oturumu kapatmaya gösterir.</span><span class="sxs-lookup"><span data-stu-id="d7ea2-112">Indicates whether to automatically close a session when a client closes an output session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="d7ea2-113">ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="d7ea2-113">ConcurrencyMode</span></span>  
 <span data-ttu-id="d7ea2-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="d7ea2-114">Data type: string</span></span>  
<span data-ttu-id="d7ea2-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d7ea2-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d7ea2-116">Bir hizmet bir iş parçacığı, birden çok iş parçacığı veya desteklemeyeceğini aramalar destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7ea2-116">Indicates whether a service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="d7ea2-117">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="d7ea2-117">ConfigurationName</span></span>  
 <span data-ttu-id="d7ea2-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="d7ea2-118">Data type: string</span></span>  
  
 <span data-ttu-id="d7ea2-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d7ea2-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d7ea2-120">Hizmet yapılandırmasının adı.</span><span class="sxs-lookup"><span data-stu-id="d7ea2-120">The name of the service configuration.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="d7ea2-121">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="d7ea2-121">IgnoreExtensionDataObject</span></span>  
 <span data-ttu-id="d7ea2-122">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="d7ea2-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="d7ea2-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d7ea2-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d7ea2-124">Bilinmeyen seri hale getirme verilerinin gönderilip gönderilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7ea2-124">Specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="d7ea2-125">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="d7ea2-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="d7ea2-126">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="d7ea2-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="d7ea2-127">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d7ea2-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d7ea2-128">Hata ayıklama amacıyla istemcilere döndürülen SOAP hatalarının ayrıntılı yönetilen özel durum bilgileri dahil edilip edilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7ea2-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
### <a name="instancecontextmode"></a><span data-ttu-id="d7ea2-129">InstanceContextMode</span><span class="sxs-lookup"><span data-stu-id="d7ea2-129">InstanceContextMode</span></span>  
 <span data-ttu-id="d7ea2-130">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="d7ea2-130">Data type: string</span></span>  
  
 <span data-ttu-id="d7ea2-131">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d7ea2-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d7ea2-132">Yeni bir hizmet nesnesi oluşturulduğunda belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7ea2-132">Specifies when a new service object is created.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="d7ea2-133">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="d7ea2-133">MaxItemsInObjectGraph</span></span>  
 <span data-ttu-id="d7ea2-134">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="d7ea2-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="d7ea2-135">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d7ea2-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d7ea2-136">Serileştirilmiş nesne içinde izin verilen öğe maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="d7ea2-136">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="name"></a><span data-ttu-id="d7ea2-137">Ad</span><span class="sxs-lookup"><span data-stu-id="d7ea2-137">Name</span></span>  
 <span data-ttu-id="d7ea2-138">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="d7ea2-138">Data type: string</span></span>  
  
 <span data-ttu-id="d7ea2-139">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d7ea2-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d7ea2-140">WSDL hizmetinde name özniteliği.</span><span class="sxs-lookup"><span data-stu-id="d7ea2-140">The name attribute of the service in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="d7ea2-141">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="d7ea2-141">Namespace</span></span>  
 <span data-ttu-id="d7ea2-142">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="d7ea2-142">Data type: string</span></span>  
  
 <span data-ttu-id="d7ea2-143">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d7ea2-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d7ea2-144">WSDL hizmetinde hedef ad alanı.</span><span class="sxs-lookup"><span data-stu-id="d7ea2-144">The target namespace of the service in WSDL.</span></span>  
  
### <a name="releaseserviceinstanceontransactioncomplete"></a><span data-ttu-id="d7ea2-145">ReleaseServiceInstanceOnTransactionComplete</span><span class="sxs-lookup"><span data-stu-id="d7ea2-145">ReleaseServiceInstanceOnTransactionComplete</span></span>  
 <span data-ttu-id="d7ea2-146">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="d7ea2-146">Data type: boolean</span></span>  
  
 <span data-ttu-id="d7ea2-147">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d7ea2-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d7ea2-148">Geçerli işlem tamamlandıktan sonra hizmeti nesnesi geri dönüştürüldüğünde olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7ea2-148">Specifies whether the service object is recycled when the current transaction completes.</span></span>  
  
### <a name="transactionautocompleteonsessionclose"></a><span data-ttu-id="d7ea2-149">TransactionAutoCompleteOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="d7ea2-149">TransactionAutoCompleteOnSessionClose</span></span>  
 <span data-ttu-id="d7ea2-150">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="d7ea2-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="d7ea2-151">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d7ea2-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d7ea2-152">Geçerli oturumu kapattığında bekleyen işlem tamamlandı olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7ea2-152">Specifies whether pending transactions are completed when the current session closes.</span></span>  
  
### <a name="transactionisolationlevel"></a><span data-ttu-id="d7ea2-153">TransactionIsolationLevel</span><span class="sxs-lookup"><span data-stu-id="d7ea2-153">TransactionIsolationLevel</span></span>  
 <span data-ttu-id="d7ea2-154">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="d7ea2-154">Data type: string</span></span>  
  
 <span data-ttu-id="d7ea2-155">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d7ea2-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d7ea2-156">İşlem yalıtım düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7ea2-156">Specifies the transaction isolation level.</span></span>  
  
### <a name="transactiontimeout"></a><span data-ttu-id="d7ea2-157">TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="d7ea2-157">TransactionTimeout</span></span>  
 <span data-ttu-id="d7ea2-158">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="d7ea2-158">Data type: datetime</span></span>  
  
 <span data-ttu-id="d7ea2-159">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d7ea2-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d7ea2-160">İçinde bir işlemin tamamlanması gereken süre.</span><span class="sxs-lookup"><span data-stu-id="d7ea2-160">The period within which a transaction must complete.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="d7ea2-161">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="d7ea2-161">UseSynchronizationContext</span></span>  
 <span data-ttu-id="d7ea2-162">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="d7ea2-162">Data type: boolean</span></span>  
  
 <span data-ttu-id="d7ea2-163">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d7ea2-163">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d7ea2-164">Geçerli eşitleme bağlamı iş parçacığı yürütmeyi seçmek için kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7ea2-164">Specifies whether to use the current synchronization context to choose the thread execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="d7ea2-165">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="d7ea2-165">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="d7ea2-166">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="d7ea2-166">Data type: boolean</span></span>  
  
 <span data-ttu-id="d7ea2-167">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d7ea2-167">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d7ea2-168">Sistem veya uygulama SOAP MustUnderstand üstbilgi işlemeyi zorunlu olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7ea2-168">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7ea2-169">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d7ea2-169">Requirements</span></span>  
  
|<span data-ttu-id="d7ea2-170">MOF</span><span class="sxs-lookup"><span data-stu-id="d7ea2-170">MOF</span></span>|<span data-ttu-id="d7ea2-171">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d7ea2-171">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d7ea2-172">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="d7ea2-172">Namespace</span></span>|<span data-ttu-id="d7ea2-173">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d7ea2-173">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d7ea2-174">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d7ea2-174">See Also</span></span>  
 <xref:System.ServiceModel.ServiceBehaviorAttribute>
