---
title: ServiceBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 5faa266f-587f-4e03-828d-1c7dd5acfe65
ms.openlocfilehash: e3716d42d479bcbdfd900b4fd2e335576a71574b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96295606"
---
# <a name="servicebehaviorattribute"></a><span data-ttu-id="6f50d-102">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="6f50d-102">ServiceBehaviorAttribute</span></span>

<span data-ttu-id="6f50d-103">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="6f50d-103">ServiceBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f50d-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="6f50d-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="6f50d-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6f50d-105">Methods</span></span>  

 <span data-ttu-id="6f50d-106">ServiceBehaviorAttribute sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="6f50d-106">The ServiceBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="6f50d-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="6f50d-107">Properties</span></span>  

 <span data-ttu-id="6f50d-108">ServiceBehaviorAttribute sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="6f50d-108">The ServiceBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="6f50d-109">Automaticsessionkapanıyor</span><span class="sxs-lookup"><span data-stu-id="6f50d-109">AutomaticSessionShutdown</span></span>  

 <span data-ttu-id="6f50d-110">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="6f50d-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="6f50d-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="6f50d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6f50d-112">Bir istemci bir çıkış oturumunu kapattığında, oturumun otomatik olarak kapatılıp kapatılmayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f50d-112">Indicates whether to automatically close a session when a client closes an output session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="6f50d-113">ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="6f50d-113">ConcurrencyMode</span></span>  

 <span data-ttu-id="6f50d-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="6f50d-114">Data type: string</span></span>  
<span data-ttu-id="6f50d-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="6f50d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6f50d-116">Bir hizmetin bir iş parçacığını, birden çok iş parçacığını veya yer aldığı çağrıları destekleyip desteklemediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f50d-116">Indicates whether a service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="6f50d-117">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="6f50d-117">ConfigurationName</span></span>  

 <span data-ttu-id="6f50d-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="6f50d-118">Data type: string</span></span>  
  
 <span data-ttu-id="6f50d-119">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="6f50d-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6f50d-120">Hizmet yapılandırmasının adı.</span><span class="sxs-lookup"><span data-stu-id="6f50d-120">The name of the service configuration.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="6f50d-121">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="6f50d-121">IgnoreExtensionDataObject</span></span>  

 <span data-ttu-id="6f50d-122">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="6f50d-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="6f50d-123">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="6f50d-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6f50d-124">Bilinmeyen serileştirme verilerinin hatta gönderileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f50d-124">Specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="6f50d-125">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="6f50d-125">IncludeExceptionDetailInFaults</span></span>  

 <span data-ttu-id="6f50d-126">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="6f50d-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="6f50d-127">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="6f50d-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6f50d-128">Yönetilen özel durum bilgilerinin, istemcilere hata ayıklama amacıyla döndürülen SOAP hatalarının ayrıntısına eklenip eklenmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f50d-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
### <a name="instancecontextmode"></a><span data-ttu-id="6f50d-129">InstanceContextMode</span><span class="sxs-lookup"><span data-stu-id="6f50d-129">InstanceContextMode</span></span>  

 <span data-ttu-id="6f50d-130">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="6f50d-130">Data type: string</span></span>  
  
 <span data-ttu-id="6f50d-131">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="6f50d-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6f50d-132">Yeni bir hizmet nesnesinin ne zaman oluşturulacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f50d-132">Specifies when a new service object is created.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="6f50d-133">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="6f50d-133">MaxItemsInObjectGraph</span></span>  

 <span data-ttu-id="6f50d-134">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="6f50d-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="6f50d-135">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="6f50d-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6f50d-136">Seri hale getirilen bir nesnede izin verilen en fazla öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="6f50d-136">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="name"></a><span data-ttu-id="6f50d-137">Adı</span><span class="sxs-lookup"><span data-stu-id="6f50d-137">Name</span></span>  

 <span data-ttu-id="6f50d-138">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="6f50d-138">Data type: string</span></span>  
  
 <span data-ttu-id="6f50d-139">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="6f50d-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6f50d-140">WSDL içindeki hizmetin Name özniteliği.</span><span class="sxs-lookup"><span data-stu-id="6f50d-140">The name attribute of the service in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="6f50d-141">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="6f50d-141">Namespace</span></span>  

 <span data-ttu-id="6f50d-142">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="6f50d-142">Data type: string</span></span>  
  
 <span data-ttu-id="6f50d-143">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="6f50d-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6f50d-144">WSDL 'de hizmetin hedef ad alanı.</span><span class="sxs-lookup"><span data-stu-id="6f50d-144">The target namespace of the service in WSDL.</span></span>  
  
### <a name="releaseserviceinstanceontransactioncomplete"></a><span data-ttu-id="6f50d-145">ReleaseServiceInstanceOnTransactionComplete</span><span class="sxs-lookup"><span data-stu-id="6f50d-145">ReleaseServiceInstanceOnTransactionComplete</span></span>  

 <span data-ttu-id="6f50d-146">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="6f50d-146">Data type: boolean</span></span>  
  
 <span data-ttu-id="6f50d-147">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="6f50d-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6f50d-148">Geçerli işlem tamamlandığında hizmet nesnesinin geri dönüştürülüp dönüştürülmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f50d-148">Specifies whether the service object is recycled when the current transaction completes.</span></span>  
  
### <a name="transactionautocompleteonsessionclose"></a><span data-ttu-id="6f50d-149">TransactionAutoCompleteOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="6f50d-149">TransactionAutoCompleteOnSessionClose</span></span>  

 <span data-ttu-id="6f50d-150">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="6f50d-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="6f50d-151">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="6f50d-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6f50d-152">Geçerli oturum kapandığında bekleyen işlemlerin tamamlanıp tamamlanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f50d-152">Specifies whether pending transactions are completed when the current session closes.</span></span>  
  
### <a name="transactionisolationlevel"></a><span data-ttu-id="6f50d-153">TransactionIsolationLevel</span><span class="sxs-lookup"><span data-stu-id="6f50d-153">TransactionIsolationLevel</span></span>  

 <span data-ttu-id="6f50d-154">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="6f50d-154">Data type: string</span></span>  
  
 <span data-ttu-id="6f50d-155">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="6f50d-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6f50d-156">İşlem yalıtım düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f50d-156">Specifies the transaction isolation level.</span></span>  
  
### <a name="transactiontimeout"></a><span data-ttu-id="6f50d-157">Işlem zaman aşımı</span><span class="sxs-lookup"><span data-stu-id="6f50d-157">TransactionTimeout</span></span>  

 <span data-ttu-id="6f50d-158">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="6f50d-158">Data type: datetime</span></span>  
  
 <span data-ttu-id="6f50d-159">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="6f50d-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6f50d-160">Bir işlemin tamamlaması gereken dönem.</span><span class="sxs-lookup"><span data-stu-id="6f50d-160">The period within which a transaction must complete.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="6f50d-161">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="6f50d-161">UseSynchronizationContext</span></span>  

 <span data-ttu-id="6f50d-162">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="6f50d-162">Data type: boolean</span></span>  
  
 <span data-ttu-id="6f50d-163">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="6f50d-163">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6f50d-164">İş parçacığı yürütmeyi seçmek için geçerli eşitleme kapsamının kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f50d-164">Specifies whether to use the current synchronization context to choose the thread execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="6f50d-165">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="6f50d-165">ValidateMustUnderstand</span></span>  

 <span data-ttu-id="6f50d-166">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="6f50d-166">Data type: boolean</span></span>  
  
 <span data-ttu-id="6f50d-167">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="6f50d-167">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6f50d-168">Sistemin ya da uygulamanın SOAP MustUnderstand üst bilgi işlemeyi zorunlu yapıp uygulamamadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f50d-168">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f50d-169">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6f50d-169">Requirements</span></span>  
  
|<span data-ttu-id="6f50d-170">MOF</span><span class="sxs-lookup"><span data-stu-id="6f50d-170">MOF</span></span>|<span data-ttu-id="6f50d-171">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6f50d-171">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="6f50d-172">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="6f50d-172">Namespace</span></span>|<span data-ttu-id="6f50d-173">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="6f50d-173">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6f50d-174">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f50d-174">See also</span></span>

- <xref:System.ServiceModel.ServiceBehaviorAttribute>
