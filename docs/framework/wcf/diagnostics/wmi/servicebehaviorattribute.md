---
description: 'Daha fazla bilgi edinin: ServiceBehaviorAttribute'
title: ServiceBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 5faa266f-587f-4e03-828d-1c7dd5acfe65
ms.openlocfilehash: 57ffa9103523618db752b3be6d43bb16603d1728
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715580"
---
# <a name="servicebehaviorattribute"></a><span data-ttu-id="ef995-103">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="ef995-103">ServiceBehaviorAttribute</span></span>

<span data-ttu-id="ef995-104">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="ef995-104">ServiceBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef995-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ef995-105">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="ef995-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ef995-106">Methods</span></span>  

 <span data-ttu-id="ef995-107">ServiceBehaviorAttribute sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="ef995-107">The ServiceBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ef995-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ef995-108">Properties</span></span>  

 <span data-ttu-id="ef995-109">ServiceBehaviorAttribute sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="ef995-109">The ServiceBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="ef995-110">Automaticsessionkapanıyor</span><span class="sxs-lookup"><span data-stu-id="ef995-110">AutomaticSessionShutdown</span></span>  

 <span data-ttu-id="ef995-111">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="ef995-111">Data type: boolean</span></span>  
  
 <span data-ttu-id="ef995-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="ef995-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef995-113">Bir istemci bir çıkış oturumunu kapattığında, oturumun otomatik olarak kapatılıp kapatılmayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ef995-113">Indicates whether to automatically close a session when a client closes an output session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="ef995-114">ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="ef995-114">ConcurrencyMode</span></span>  

 <span data-ttu-id="ef995-115">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="ef995-115">Data type: string</span></span>  
<span data-ttu-id="ef995-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="ef995-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef995-117">Bir hizmetin bir iş parçacığını, birden çok iş parçacığını veya yer aldığı çağrıları destekleyip desteklemediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ef995-117">Indicates whether a service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="ef995-118">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="ef995-118">ConfigurationName</span></span>  

 <span data-ttu-id="ef995-119">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="ef995-119">Data type: string</span></span>  
  
 <span data-ttu-id="ef995-120">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="ef995-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef995-121">Hizmet yapılandırmasının adı.</span><span class="sxs-lookup"><span data-stu-id="ef995-121">The name of the service configuration.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="ef995-122">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="ef995-122">IgnoreExtensionDataObject</span></span>  

 <span data-ttu-id="ef995-123">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="ef995-123">Data type: boolean</span></span>  
  
 <span data-ttu-id="ef995-124">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="ef995-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef995-125">Bilinmeyen serileştirme verilerinin hatta gönderileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ef995-125">Specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="ef995-126">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="ef995-126">IncludeExceptionDetailInFaults</span></span>  

 <span data-ttu-id="ef995-127">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="ef995-127">Data type: boolean</span></span>  
  
 <span data-ttu-id="ef995-128">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="ef995-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef995-129">Yönetilen özel durum bilgilerinin, istemcilere hata ayıklama amacıyla döndürülen SOAP hatalarının ayrıntısına eklenip eklenmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ef995-129">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
### <a name="instancecontextmode"></a><span data-ttu-id="ef995-130">InstanceContextMode</span><span class="sxs-lookup"><span data-stu-id="ef995-130">InstanceContextMode</span></span>  

 <span data-ttu-id="ef995-131">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="ef995-131">Data type: string</span></span>  
  
 <span data-ttu-id="ef995-132">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="ef995-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef995-133">Yeni bir hizmet nesnesinin ne zaman oluşturulacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ef995-133">Specifies when a new service object is created.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="ef995-134">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="ef995-134">MaxItemsInObjectGraph</span></span>  

 <span data-ttu-id="ef995-135">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="ef995-135">Data type: sint32</span></span>  
  
 <span data-ttu-id="ef995-136">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="ef995-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef995-137">Seri hale getirilen bir nesnede izin verilen en fazla öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="ef995-137">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="name"></a><span data-ttu-id="ef995-138">Name</span><span class="sxs-lookup"><span data-stu-id="ef995-138">Name</span></span>  

 <span data-ttu-id="ef995-139">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="ef995-139">Data type: string</span></span>  
  
 <span data-ttu-id="ef995-140">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="ef995-140">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef995-141">WSDL içindeki hizmetin Name özniteliği.</span><span class="sxs-lookup"><span data-stu-id="ef995-141">The name attribute of the service in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="ef995-142">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="ef995-142">Namespace</span></span>  

 <span data-ttu-id="ef995-143">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="ef995-143">Data type: string</span></span>  
  
 <span data-ttu-id="ef995-144">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="ef995-144">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef995-145">WSDL 'de hizmetin hedef ad alanı.</span><span class="sxs-lookup"><span data-stu-id="ef995-145">The target namespace of the service in WSDL.</span></span>  
  
### <a name="releaseserviceinstanceontransactioncomplete"></a><span data-ttu-id="ef995-146">ReleaseServiceInstanceOnTransactionComplete</span><span class="sxs-lookup"><span data-stu-id="ef995-146">ReleaseServiceInstanceOnTransactionComplete</span></span>  

 <span data-ttu-id="ef995-147">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="ef995-147">Data type: boolean</span></span>  
  
 <span data-ttu-id="ef995-148">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="ef995-148">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef995-149">Geçerli işlem tamamlandığında hizmet nesnesinin geri dönüştürülüp dönüştürülmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ef995-149">Specifies whether the service object is recycled when the current transaction completes.</span></span>  
  
### <a name="transactionautocompleteonsessionclose"></a><span data-ttu-id="ef995-150">TransactionAutoCompleteOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="ef995-150">TransactionAutoCompleteOnSessionClose</span></span>  

 <span data-ttu-id="ef995-151">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="ef995-151">Data type: boolean</span></span>  
  
 <span data-ttu-id="ef995-152">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="ef995-152">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef995-153">Geçerli oturum kapandığında bekleyen işlemlerin tamamlanıp tamamlanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ef995-153">Specifies whether pending transactions are completed when the current session closes.</span></span>  
  
### <a name="transactionisolationlevel"></a><span data-ttu-id="ef995-154">TransactionIsolationLevel</span><span class="sxs-lookup"><span data-stu-id="ef995-154">TransactionIsolationLevel</span></span>  

 <span data-ttu-id="ef995-155">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="ef995-155">Data type: string</span></span>  
  
 <span data-ttu-id="ef995-156">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="ef995-156">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef995-157">İşlem yalıtım düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ef995-157">Specifies the transaction isolation level.</span></span>  
  
### <a name="transactiontimeout"></a><span data-ttu-id="ef995-158">Işlem zaman aşımı</span><span class="sxs-lookup"><span data-stu-id="ef995-158">TransactionTimeout</span></span>  

 <span data-ttu-id="ef995-159">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="ef995-159">Data type: datetime</span></span>  
  
 <span data-ttu-id="ef995-160">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="ef995-160">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef995-161">Bir işlemin tamamlaması gereken dönem.</span><span class="sxs-lookup"><span data-stu-id="ef995-161">The period within which a transaction must complete.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="ef995-162">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="ef995-162">UseSynchronizationContext</span></span>  

 <span data-ttu-id="ef995-163">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="ef995-163">Data type: boolean</span></span>  
  
 <span data-ttu-id="ef995-164">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="ef995-164">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef995-165">İş parçacığı yürütmeyi seçmek için geçerli eşitleme kapsamının kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ef995-165">Specifies whether to use the current synchronization context to choose the thread execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="ef995-166">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="ef995-166">ValidateMustUnderstand</span></span>  

 <span data-ttu-id="ef995-167">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="ef995-167">Data type: boolean</span></span>  
  
 <span data-ttu-id="ef995-168">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="ef995-168">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef995-169">Sistemin ya da uygulamanın SOAP MustUnderstand üst bilgi işlemeyi zorunlu yapıp uygulamamadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ef995-169">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef995-170">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ef995-170">Requirements</span></span>  
  
|<span data-ttu-id="ef995-171">MOF</span><span class="sxs-lookup"><span data-stu-id="ef995-171">MOF</span></span>|<span data-ttu-id="ef995-172">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ef995-172">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ef995-173">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="ef995-173">Namespace</span></span>|<span data-ttu-id="ef995-174">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="ef995-174">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ef995-175">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef995-175">See also</span></span>

- <xref:System.ServiceModel.ServiceBehaviorAttribute>
