---
title: Uç Nokta
ms.date: 03/30/2017
ms.assetid: fe63370d-81a1-40f3-97c2-59cb357c78d2
ms.openlocfilehash: ceb4e4b41502b00d7bb21f1ecbd8249fccf1ce3b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96288820"
---
# <a name="endpoint"></a><span data-ttu-id="a3be3-102">Uç Nokta</span><span class="sxs-lookup"><span data-stu-id="a3be3-102">Endpoint</span></span>

<span data-ttu-id="a3be3-103">Uç Nokta</span><span class="sxs-lookup"><span data-stu-id="a3be3-103">Endpoint</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3be3-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="a3be3-104">Syntax</span></span>  
  
```csharp
class Endpoint  
{  
  string Address;  
  string AddressHeaders[];  
  string AddressIdentity;  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  Binding Binding;  
  string ContractName;  
  string CounterInstanceName;  
  string ListenUri;  
  string Name;  
  sint32 ProcessId;  
  Contract ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a3be3-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a3be3-105">Methods</span></span>  

 <span data-ttu-id="a3be3-106">Endpoint sınıfı aşağıdaki yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a3be3-106">The Endpoint class defines the following method.</span></span>  
  
|<span data-ttu-id="a3be3-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a3be3-107">Method</span></span>|<span data-ttu-id="a3be3-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a3be3-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a3be3-109">GetOperationCounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="a3be3-109">GetOperationCounterInstanceName</span></span>](getoperationcounterinstancename.md)|<span data-ttu-id="a3be3-110">İşlem performans sayacı örnek adını alır</span><span class="sxs-lookup"><span data-stu-id="a3be3-110">Retrieves the operation performance counter instance name</span></span>|  
  
## <a name="properties"></a><span data-ttu-id="a3be3-111">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a3be3-111">Properties</span></span>  

 <span data-ttu-id="a3be3-112">Uç nokta sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="a3be3-112">The Endpoint class has the following properties:</span></span>  
  
### <a name="address"></a><span data-ttu-id="a3be3-113">Adres</span><span class="sxs-lookup"><span data-stu-id="a3be3-113">Address</span></span>  

 <span data-ttu-id="a3be3-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="a3be3-114">Data type: string</span></span>  
  
 <span data-ttu-id="a3be3-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="a3be3-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a3be3-116">Uç noktanın adresini içeren bir URI.</span><span class="sxs-lookup"><span data-stu-id="a3be3-116">A URI that contains the address of the endpoint.</span></span>  
  
### <a name="addressheaders"></a><span data-ttu-id="a3be3-117">AddressHeaders</span><span class="sxs-lookup"><span data-stu-id="a3be3-117">AddressHeaders</span></span>  

 <span data-ttu-id="a3be3-118">Veri türü: dize dizisi</span><span class="sxs-lookup"><span data-stu-id="a3be3-118">Data type: string array</span></span>  
  
 <span data-ttu-id="a3be3-119">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="a3be3-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a3be3-120">Bu uç noktaya eklenen adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="a3be3-120">The collection of address headers attached to this endpoint.</span></span>  
  
### <a name="addressidentity"></a><span data-ttu-id="a3be3-121">Addressıdentity</span><span class="sxs-lookup"><span data-stu-id="a3be3-121">AddressIdentity</span></span>  

 <span data-ttu-id="a3be3-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="a3be3-122">Data type: string</span></span>  
  
 <span data-ttu-id="a3be3-123">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="a3be3-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a3be3-124">Uç noktanın kimliği.</span><span class="sxs-lookup"><span data-stu-id="a3be3-124">The identity of the endpoint.</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="a3be3-125">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="a3be3-125">AppDomainId</span></span>  

 <span data-ttu-id="a3be3-126">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="a3be3-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="a3be3-127">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="a3be3-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a3be3-128">Uç noktasını barındıran AppDomain 'in AppDomain kimliği.</span><span class="sxs-lookup"><span data-stu-id="a3be3-128">The appdomain id of the appdomain that hosts the endpoint.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="a3be3-129">Davranışlar</span><span class="sxs-lookup"><span data-stu-id="a3be3-129">Behaviors</span></span>  

 <span data-ttu-id="a3be3-130">Veri türü: davranış dizisi</span><span class="sxs-lookup"><span data-stu-id="a3be3-130">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="a3be3-131">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="a3be3-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a3be3-132">Bu uç nokta tarafından uygulanan davranışların koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="a3be3-132">The collection of behaviors implemented by this endpoint.</span></span>  
  
### <a name="binding"></a><span data-ttu-id="a3be3-133">Bağlama</span><span class="sxs-lookup"><span data-stu-id="a3be3-133">Binding</span></span>  

 <span data-ttu-id="a3be3-134">Veri türü: bağlama</span><span class="sxs-lookup"><span data-stu-id="a3be3-134">Data type: Binding</span></span>  
  
 <span data-ttu-id="a3be3-135">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="a3be3-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a3be3-136">Bu uç nokta tarafından kullanılan bağlama.</span><span class="sxs-lookup"><span data-stu-id="a3be3-136">The binding used by this endpoint.</span></span>  
  
### <a name="contractname"></a><span data-ttu-id="a3be3-137">ContractName</span><span class="sxs-lookup"><span data-stu-id="a3be3-137">ContractName</span></span>  

 <span data-ttu-id="a3be3-138">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="a3be3-138">Data type: string</span></span>  
  
 <span data-ttu-id="a3be3-139">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="a3be3-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a3be3-140">Bu uç noktanın hangi sözleşmeyi açığa çıkardığınızı belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="a3be3-140">A string that specifies which contract this endpoint is exposing.</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="a3be3-141">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="a3be3-141">CounterInstanceName</span></span>  

 <span data-ttu-id="a3be3-142">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="a3be3-142">Data type: string</span></span>  
  
 <span data-ttu-id="a3be3-143">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="a3be3-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a3be3-144">Uç noktanın performans sayaçları örneğinin adı.</span><span class="sxs-lookup"><span data-stu-id="a3be3-144">The name of the instance of performance counters of the endpoint.</span></span>  
  
### <a name="listenuri"></a><span data-ttu-id="a3be3-145">Öğesini</span><span class="sxs-lookup"><span data-stu-id="a3be3-145">ListenUri</span></span>  

 <span data-ttu-id="a3be3-146">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="a3be3-146">Data type: string</span></span>  
  
 <span data-ttu-id="a3be3-147">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="a3be3-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a3be3-148">Uç noktanın dinlediği URI.</span><span class="sxs-lookup"><span data-stu-id="a3be3-148">The Uri the endpoint listens on.</span></span>  
  
### <a name="name"></a><span data-ttu-id="a3be3-149">Adı</span><span class="sxs-lookup"><span data-stu-id="a3be3-149">Name</span></span>  

 <span data-ttu-id="a3be3-150">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="a3be3-150">Data type: string</span></span>  
  
 <span data-ttu-id="a3be3-151">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="a3be3-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a3be3-152">Bu uç noktanın benzersiz adı.</span><span class="sxs-lookup"><span data-stu-id="a3be3-152">The unique name of this endpoint.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="a3be3-153">Işlem</span><span class="sxs-lookup"><span data-stu-id="a3be3-153">ProcessId</span></span>  

 <span data-ttu-id="a3be3-154">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="a3be3-154">Data type: sint32</span></span>  
  
 <span data-ttu-id="a3be3-155">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="a3be3-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a3be3-156">Uç noktasını barındıran işlemin işlem kimliği.</span><span class="sxs-lookup"><span data-stu-id="a3be3-156">The process Id of the process that hosts the endpoint.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="a3be3-157">ref</span><span class="sxs-lookup"><span data-stu-id="a3be3-157">ref</span></span>  

 <span data-ttu-id="a3be3-158">Veri türü: sözleşme</span><span class="sxs-lookup"><span data-stu-id="a3be3-158">Data type: Contract</span></span>  
  
 <span data-ttu-id="a3be3-159">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="a3be3-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a3be3-160">Bu uç noktanın sunduğu sözleşme.</span><span class="sxs-lookup"><span data-stu-id="a3be3-160">The contract this endpoint is exposing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3be3-161">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a3be3-161">Requirements</span></span>  
  
|<span data-ttu-id="a3be3-162">MOF</span><span class="sxs-lookup"><span data-stu-id="a3be3-162">MOF</span></span>|<span data-ttu-id="a3be3-163">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a3be3-163">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a3be3-164">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="a3be3-164">Namespace</span></span>|<span data-ttu-id="a3be3-165">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="a3be3-165">Defined in root\ServiceModel</span></span>|
