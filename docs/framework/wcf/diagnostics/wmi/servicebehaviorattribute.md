---
title: ServiceBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 5faa266f-587f-4e03-828d-1c7dd5acfe65
ms.openlocfilehash: c2915c636aec26cfb1f58d12da49151915c52c05
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50182963"
---
# <a name="servicebehaviorattribute"></a><span data-ttu-id="2203e-102">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="2203e-102">ServiceBehaviorAttribute</span></span>
<span data-ttu-id="2203e-103">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="2203e-103">ServiceBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2203e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2203e-104">Syntax</span></span>  
  
```csharp
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
  
## <a name="methods"></a><span data-ttu-id="2203e-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2203e-105">Methods</span></span>  
 <span data-ttu-id="2203e-106">ServiceBehaviorAttribute sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="2203e-106">The ServiceBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="2203e-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="2203e-107">Properties</span></span>  
 <span data-ttu-id="2203e-108">ServiceBehaviorAttribute sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="2203e-108">The ServiceBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="2203e-109">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="2203e-109">AutomaticSessionShutdown</span></span>  
 <span data-ttu-id="2203e-110">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="2203e-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="2203e-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="2203e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2203e-112">Otomatik olarak bir istemci bir çıkış oturumu kapattığı zaman oturumu kapatmak görüntülenip görüntülenmeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="2203e-112">Indicates whether to automatically close a session when a client closes an output session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="2203e-113">ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="2203e-113">ConcurrencyMode</span></span>  
 <span data-ttu-id="2203e-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="2203e-114">Data type: string</span></span>  
<span data-ttu-id="2203e-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="2203e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2203e-116">Bir hizmet tek bir iş parçacığı, birden çok iş parçacığı veya yeniden girilen çağrıları destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2203e-116">Indicates whether a service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="2203e-117">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="2203e-117">ConfigurationName</span></span>  
 <span data-ttu-id="2203e-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="2203e-118">Data type: string</span></span>  
  
 <span data-ttu-id="2203e-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="2203e-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2203e-120">Hizmet yapılandırmasının adı.</span><span class="sxs-lookup"><span data-stu-id="2203e-120">The name of the service configuration.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="2203e-121">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="2203e-121">IgnoreExtensionDataObject</span></span>  
 <span data-ttu-id="2203e-122">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="2203e-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="2203e-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="2203e-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2203e-124">Bilinmeyen serileştirme verilerinin gönderilip gönderilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2203e-124">Specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="2203e-125">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="2203e-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="2203e-126">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="2203e-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="2203e-127">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="2203e-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2203e-128">Hata ayıklama amacıyla, istemcilere dönen SOAP hatalarının ayrıntılarındaki yönetilen özel durum bilgilerinin dahil edilip edilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2203e-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
### <a name="instancecontextmode"></a><span data-ttu-id="2203e-129">InstanceContextMode</span><span class="sxs-lookup"><span data-stu-id="2203e-129">InstanceContextMode</span></span>  
 <span data-ttu-id="2203e-130">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="2203e-130">Data type: string</span></span>  
  
 <span data-ttu-id="2203e-131">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="2203e-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2203e-132">Yeni bir hizmet nesnesi oluşturulduğunda belirtir.</span><span class="sxs-lookup"><span data-stu-id="2203e-132">Specifies when a new service object is created.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="2203e-133">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="2203e-133">MaxItemsInObjectGraph</span></span>  
 <span data-ttu-id="2203e-134">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="2203e-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="2203e-135">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="2203e-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2203e-136">Serileştirilmiş nesne içinde izin verilen öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="2203e-136">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="name"></a><span data-ttu-id="2203e-137">Ad</span><span class="sxs-lookup"><span data-stu-id="2203e-137">Name</span></span>  
 <span data-ttu-id="2203e-138">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="2203e-138">Data type: string</span></span>  
  
 <span data-ttu-id="2203e-139">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="2203e-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2203e-140">WSDL hizmetinde öğesinin ad özniteliği.</span><span class="sxs-lookup"><span data-stu-id="2203e-140">The name attribute of the service in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="2203e-141">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="2203e-141">Namespace</span></span>  
 <span data-ttu-id="2203e-142">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="2203e-142">Data type: string</span></span>  
  
 <span data-ttu-id="2203e-143">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="2203e-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2203e-144">WSDL hizmetinde hedef ad alanı.</span><span class="sxs-lookup"><span data-stu-id="2203e-144">The target namespace of the service in WSDL.</span></span>  
  
### <a name="releaseserviceinstanceontransactioncomplete"></a><span data-ttu-id="2203e-145">ReleaseServiceInstanceOnTransactionComplete</span><span class="sxs-lookup"><span data-stu-id="2203e-145">ReleaseServiceInstanceOnTransactionComplete</span></span>  
 <span data-ttu-id="2203e-146">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="2203e-146">Data type: boolean</span></span>  
  
 <span data-ttu-id="2203e-147">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="2203e-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2203e-148">Geçerli işlem tamamlandıktan sonra hizmet nesnesi geri olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2203e-148">Specifies whether the service object is recycled when the current transaction completes.</span></span>  
  
### <a name="transactionautocompleteonsessionclose"></a><span data-ttu-id="2203e-149">TransactionAutoCompleteOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="2203e-149">TransactionAutoCompleteOnSessionClose</span></span>  
 <span data-ttu-id="2203e-150">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="2203e-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="2203e-151">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="2203e-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2203e-152">Geçerli oturumu kapattığında bekleyen işlem tamamlanıp tamamlanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2203e-152">Specifies whether pending transactions are completed when the current session closes.</span></span>  
  
### <a name="transactionisolationlevel"></a><span data-ttu-id="2203e-153">TransactionIsolationLevel</span><span class="sxs-lookup"><span data-stu-id="2203e-153">TransactionIsolationLevel</span></span>  
 <span data-ttu-id="2203e-154">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="2203e-154">Data type: string</span></span>  
  
 <span data-ttu-id="2203e-155">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="2203e-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2203e-156">İşlem yalıtım düzeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="2203e-156">Specifies the transaction isolation level.</span></span>  
  
### <a name="transactiontimeout"></a><span data-ttu-id="2203e-157">TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="2203e-157">TransactionTimeout</span></span>  
 <span data-ttu-id="2203e-158">Veri türü: tarih/saat</span><span class="sxs-lookup"><span data-stu-id="2203e-158">Data type: datetime</span></span>  
  
 <span data-ttu-id="2203e-159">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="2203e-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2203e-160">İçinde bir işlemin tamamlanması gereken süre.</span><span class="sxs-lookup"><span data-stu-id="2203e-160">The period within which a transaction must complete.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="2203e-161">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="2203e-161">UseSynchronizationContext</span></span>  
 <span data-ttu-id="2203e-162">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="2203e-162">Data type: boolean</span></span>  
  
 <span data-ttu-id="2203e-163">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="2203e-163">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2203e-164">Geçerli eşitleme kapsamının iş parçacığı yürütmeyi seçmek için kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2203e-164">Specifies whether to use the current synchronization context to choose the thread execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="2203e-165">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="2203e-165">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="2203e-166">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="2203e-166">Data type: boolean</span></span>  
  
 <span data-ttu-id="2203e-167">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="2203e-167">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2203e-168">Sistem veya uygulama SOAP MustUnderstand üst bilgi işleme uygulayıp uygulamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2203e-168">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2203e-169">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2203e-169">Requirements</span></span>  
  
|<span data-ttu-id="2203e-170">MOF</span><span class="sxs-lookup"><span data-stu-id="2203e-170">MOF</span></span>|<span data-ttu-id="2203e-171">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="2203e-171">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="2203e-172">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="2203e-172">Namespace</span></span>|<span data-ttu-id="2203e-173">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2203e-173">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2203e-174">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2203e-174">See Also</span></span>  
 <xref:System.ServiceModel.ServiceBehaviorAttribute>
