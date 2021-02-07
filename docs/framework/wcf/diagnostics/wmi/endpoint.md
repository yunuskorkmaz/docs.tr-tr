---
description: 'Daha fazla bilgi için: uç nokta'
title: Uç Nokta
ms.date: 03/30/2017
ms.assetid: fe63370d-81a1-40f3-97c2-59cb357c78d2
ms.openlocfilehash: 1c28be37d1b1abfe1813e6da8903809affd309e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757468"
---
# <a name="endpoint"></a><span data-ttu-id="2fc98-103">Uç Nokta</span><span class="sxs-lookup"><span data-stu-id="2fc98-103">Endpoint</span></span>

<span data-ttu-id="2fc98-104">Uç Nokta</span><span class="sxs-lookup"><span data-stu-id="2fc98-104">Endpoint</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fc98-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="2fc98-105">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="2fc98-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2fc98-106">Methods</span></span>  

 <span data-ttu-id="2fc98-107">Endpoint sınıfı aşağıdaki yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2fc98-107">The Endpoint class defines the following method.</span></span>  
  
|<span data-ttu-id="2fc98-108">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2fc98-108">Method</span></span>|<span data-ttu-id="2fc98-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2fc98-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2fc98-110">GetOperationCounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="2fc98-110">GetOperationCounterInstanceName</span></span>](getoperationcounterinstancename.md)|<span data-ttu-id="2fc98-111">İşlem performans sayacı örnek adını alır</span><span class="sxs-lookup"><span data-stu-id="2fc98-111">Retrieves the operation performance counter instance name</span></span>|  
  
## <a name="properties"></a><span data-ttu-id="2fc98-112">Özellikler</span><span class="sxs-lookup"><span data-stu-id="2fc98-112">Properties</span></span>  

 <span data-ttu-id="2fc98-113">Uç nokta sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="2fc98-113">The Endpoint class has the following properties:</span></span>  
  
### <a name="address"></a><span data-ttu-id="2fc98-114">Adres</span><span class="sxs-lookup"><span data-stu-id="2fc98-114">Address</span></span>  

 <span data-ttu-id="2fc98-115">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="2fc98-115">Data type: string</span></span>  
  
 <span data-ttu-id="2fc98-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="2fc98-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2fc98-117">Uç noktanın adresini içeren bir URI.</span><span class="sxs-lookup"><span data-stu-id="2fc98-117">A URI that contains the address of the endpoint.</span></span>  
  
### <a name="addressheaders"></a><span data-ttu-id="2fc98-118">AddressHeaders</span><span class="sxs-lookup"><span data-stu-id="2fc98-118">AddressHeaders</span></span>  

 <span data-ttu-id="2fc98-119">Veri türü: dize dizisi</span><span class="sxs-lookup"><span data-stu-id="2fc98-119">Data type: string array</span></span>  
  
 <span data-ttu-id="2fc98-120">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="2fc98-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2fc98-121">Bu uç noktaya eklenen adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="2fc98-121">The collection of address headers attached to this endpoint.</span></span>  
  
### <a name="addressidentity"></a><span data-ttu-id="2fc98-122">Addressıdentity</span><span class="sxs-lookup"><span data-stu-id="2fc98-122">AddressIdentity</span></span>  

 <span data-ttu-id="2fc98-123">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="2fc98-123">Data type: string</span></span>  
  
 <span data-ttu-id="2fc98-124">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="2fc98-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2fc98-125">Uç noktanın kimliği.</span><span class="sxs-lookup"><span data-stu-id="2fc98-125">The identity of the endpoint.</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="2fc98-126">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="2fc98-126">AppDomainId</span></span>  

 <span data-ttu-id="2fc98-127">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="2fc98-127">Data type: sint32</span></span>  
  
 <span data-ttu-id="2fc98-128">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="2fc98-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2fc98-129">Uç noktasını barındıran AppDomain 'in AppDomain kimliği.</span><span class="sxs-lookup"><span data-stu-id="2fc98-129">The appdomain id of the appdomain that hosts the endpoint.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="2fc98-130">Davranışlar</span><span class="sxs-lookup"><span data-stu-id="2fc98-130">Behaviors</span></span>  

 <span data-ttu-id="2fc98-131">Veri türü: davranış dizisi</span><span class="sxs-lookup"><span data-stu-id="2fc98-131">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="2fc98-132">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="2fc98-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2fc98-133">Bu uç nokta tarafından uygulanan davranışların koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="2fc98-133">The collection of behaviors implemented by this endpoint.</span></span>  
  
### <a name="binding"></a><span data-ttu-id="2fc98-134">Bağlama</span><span class="sxs-lookup"><span data-stu-id="2fc98-134">Binding</span></span>  

 <span data-ttu-id="2fc98-135">Veri türü: bağlama</span><span class="sxs-lookup"><span data-stu-id="2fc98-135">Data type: Binding</span></span>  
  
 <span data-ttu-id="2fc98-136">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="2fc98-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2fc98-137">Bu uç nokta tarafından kullanılan bağlama.</span><span class="sxs-lookup"><span data-stu-id="2fc98-137">The binding used by this endpoint.</span></span>  
  
### <a name="contractname"></a><span data-ttu-id="2fc98-138">ContractName</span><span class="sxs-lookup"><span data-stu-id="2fc98-138">ContractName</span></span>  

 <span data-ttu-id="2fc98-139">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="2fc98-139">Data type: string</span></span>  
  
 <span data-ttu-id="2fc98-140">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="2fc98-140">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2fc98-141">Bu uç noktanın hangi sözleşmeyi açığa çıkardığınızı belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="2fc98-141">A string that specifies which contract this endpoint is exposing.</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="2fc98-142">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="2fc98-142">CounterInstanceName</span></span>  

 <span data-ttu-id="2fc98-143">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="2fc98-143">Data type: string</span></span>  
  
 <span data-ttu-id="2fc98-144">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="2fc98-144">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2fc98-145">Uç noktanın performans sayaçları örneğinin adı.</span><span class="sxs-lookup"><span data-stu-id="2fc98-145">The name of the instance of performance counters of the endpoint.</span></span>  
  
### <a name="listenuri"></a><span data-ttu-id="2fc98-146">Öğesini</span><span class="sxs-lookup"><span data-stu-id="2fc98-146">ListenUri</span></span>  

 <span data-ttu-id="2fc98-147">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="2fc98-147">Data type: string</span></span>  
  
 <span data-ttu-id="2fc98-148">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="2fc98-148">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2fc98-149">Uç noktanın dinlediği URI.</span><span class="sxs-lookup"><span data-stu-id="2fc98-149">The Uri the endpoint listens on.</span></span>  
  
### <a name="name"></a><span data-ttu-id="2fc98-150">Name</span><span class="sxs-lookup"><span data-stu-id="2fc98-150">Name</span></span>  

 <span data-ttu-id="2fc98-151">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="2fc98-151">Data type: string</span></span>  
  
 <span data-ttu-id="2fc98-152">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="2fc98-152">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2fc98-153">Bu uç noktanın benzersiz adı.</span><span class="sxs-lookup"><span data-stu-id="2fc98-153">The unique name of this endpoint.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="2fc98-154">Işlem</span><span class="sxs-lookup"><span data-stu-id="2fc98-154">ProcessId</span></span>  

 <span data-ttu-id="2fc98-155">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="2fc98-155">Data type: sint32</span></span>  
  
 <span data-ttu-id="2fc98-156">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="2fc98-156">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2fc98-157">Uç noktasını barındıran işlemin işlem kimliği.</span><span class="sxs-lookup"><span data-stu-id="2fc98-157">The process Id of the process that hosts the endpoint.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="2fc98-158">ref</span><span class="sxs-lookup"><span data-stu-id="2fc98-158">ref</span></span>  

 <span data-ttu-id="2fc98-159">Veri türü: sözleşme</span><span class="sxs-lookup"><span data-stu-id="2fc98-159">Data type: Contract</span></span>  
  
 <span data-ttu-id="2fc98-160">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="2fc98-160">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2fc98-161">Bu uç noktanın sunduğu sözleşme.</span><span class="sxs-lookup"><span data-stu-id="2fc98-161">The contract this endpoint is exposing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fc98-162">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2fc98-162">Requirements</span></span>  
  
|<span data-ttu-id="2fc98-163">MOF</span><span class="sxs-lookup"><span data-stu-id="2fc98-163">MOF</span></span>|<span data-ttu-id="2fc98-164">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2fc98-164">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="2fc98-165">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="2fc98-165">Namespace</span></span>|<span data-ttu-id="2fc98-166">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="2fc98-166">Defined in root\ServiceModel</span></span>|
