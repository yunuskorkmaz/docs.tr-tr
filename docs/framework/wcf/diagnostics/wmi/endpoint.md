---
title: Uç Noktası
ms.date: 03/30/2017
ms.assetid: fe63370d-81a1-40f3-97c2-59cb357c78d2
ms.openlocfilehash: 03c401358839671d750985b95b1aada599931aad
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795902"
---
# <a name="endpoint"></a><span data-ttu-id="f0919-102">Uç Noktası</span><span class="sxs-lookup"><span data-stu-id="f0919-102">Endpoint</span></span>
<span data-ttu-id="f0919-103">Uç Noktası</span><span class="sxs-lookup"><span data-stu-id="f0919-103">Endpoint</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0919-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f0919-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="f0919-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f0919-105">Methods</span></span>  
 <span data-ttu-id="f0919-106">Endpoint sınıfı aşağıdaki yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f0919-106">The Endpoint class defines the following method.</span></span>  
  
|<span data-ttu-id="f0919-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f0919-107">Method</span></span>|<span data-ttu-id="f0919-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0919-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f0919-109">GetOperationCounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="f0919-109">GetOperationCounterInstanceName</span></span>](getoperationcounterinstancename.md)|<span data-ttu-id="f0919-110">İşlem performans sayacı örnek adını alır</span><span class="sxs-lookup"><span data-stu-id="f0919-110">Retrieves the operation performance counter instance name</span></span>|  
  
## <a name="properties"></a><span data-ttu-id="f0919-111">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f0919-111">Properties</span></span>  
 <span data-ttu-id="f0919-112">Uç nokta sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="f0919-112">The Endpoint class has the following properties:</span></span>  
  
### <a name="address"></a><span data-ttu-id="f0919-113">Adres</span><span class="sxs-lookup"><span data-stu-id="f0919-113">Address</span></span>  
 <span data-ttu-id="f0919-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="f0919-114">Data type: string</span></span>  
  
 <span data-ttu-id="f0919-115">Erişim türü: Salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="f0919-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0919-116">Uç noktanın adresini içeren bir URI.</span><span class="sxs-lookup"><span data-stu-id="f0919-116">A URI that contains the address of the endpoint.</span></span>  
  
### <a name="addressheaders"></a><span data-ttu-id="f0919-117">AddressHeaders</span><span class="sxs-lookup"><span data-stu-id="f0919-117">AddressHeaders</span></span>  
 <span data-ttu-id="f0919-118">Veri türü: dize dizisi</span><span class="sxs-lookup"><span data-stu-id="f0919-118">Data type: string array</span></span>  
  
 <span data-ttu-id="f0919-119">Erişim türü: Salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="f0919-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0919-120">Bu uç noktaya eklenen adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="f0919-120">The collection of address headers attached to this endpoint.</span></span>  
  
### <a name="addressidentity"></a><span data-ttu-id="f0919-121">Addressıdentity</span><span class="sxs-lookup"><span data-stu-id="f0919-121">AddressIdentity</span></span>  
 <span data-ttu-id="f0919-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="f0919-122">Data type: string</span></span>  
  
 <span data-ttu-id="f0919-123">Erişim türü: Salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="f0919-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0919-124">Uç noktanın kimliği.</span><span class="sxs-lookup"><span data-stu-id="f0919-124">The identity of the endpoint.</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="f0919-125">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="f0919-125">AppDomainId</span></span>  
 <span data-ttu-id="f0919-126">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="f0919-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="f0919-127">Erişim türü: Salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="f0919-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0919-128">Uç noktasını barındıran AppDomain 'in AppDomain kimliği.</span><span class="sxs-lookup"><span data-stu-id="f0919-128">The appdomain id of the appdomain that hosts the endpoint.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="f0919-129">Davranışlar</span><span class="sxs-lookup"><span data-stu-id="f0919-129">Behaviors</span></span>  
 <span data-ttu-id="f0919-130">Veri türü: Davranış dizisi</span><span class="sxs-lookup"><span data-stu-id="f0919-130">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="f0919-131">Erişim türü: Salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="f0919-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0919-132">Bu uç nokta tarafından uygulanan davranışların koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="f0919-132">The collection of behaviors implemented by this endpoint.</span></span>  
  
### <a name="binding"></a><span data-ttu-id="f0919-133">Bağlama</span><span class="sxs-lookup"><span data-stu-id="f0919-133">Binding</span></span>  
 <span data-ttu-id="f0919-134">Veri türü: Bağlama</span><span class="sxs-lookup"><span data-stu-id="f0919-134">Data type: Binding</span></span>  
  
 <span data-ttu-id="f0919-135">Erişim türü: Salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="f0919-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0919-136">Bu uç nokta tarafından kullanılan bağlama.</span><span class="sxs-lookup"><span data-stu-id="f0919-136">The binding used by this endpoint.</span></span>  
  
### <a name="contractname"></a><span data-ttu-id="f0919-137">ContractName</span><span class="sxs-lookup"><span data-stu-id="f0919-137">ContractName</span></span>  
 <span data-ttu-id="f0919-138">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="f0919-138">Data type: string</span></span>  
  
 <span data-ttu-id="f0919-139">Erişim türü: Salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="f0919-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0919-140">Bu uç noktanın hangi sözleşmeyi açığa çıkardığınızı belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="f0919-140">A string that specifies which contract this endpoint is exposing.</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="f0919-141">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="f0919-141">CounterInstanceName</span></span>  
 <span data-ttu-id="f0919-142">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="f0919-142">Data type: string</span></span>  
  
 <span data-ttu-id="f0919-143">Erişim türü: Salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="f0919-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0919-144">Uç noktanın performans sayaçları örneğinin adı.</span><span class="sxs-lookup"><span data-stu-id="f0919-144">The name of the instance of performance counters of the endpoint.</span></span>  
  
### <a name="listenuri"></a><span data-ttu-id="f0919-145">Öğesini</span><span class="sxs-lookup"><span data-stu-id="f0919-145">ListenUri</span></span>  
 <span data-ttu-id="f0919-146">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="f0919-146">Data type: string</span></span>  
  
 <span data-ttu-id="f0919-147">Erişim türü: Salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="f0919-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0919-148">Uç noktanın dinlediği URI.</span><span class="sxs-lookup"><span data-stu-id="f0919-148">The Uri the endpoint listens on.</span></span>  
  
### <a name="name"></a><span data-ttu-id="f0919-149">Ad</span><span class="sxs-lookup"><span data-stu-id="f0919-149">Name</span></span>  
 <span data-ttu-id="f0919-150">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="f0919-150">Data type: string</span></span>  
  
 <span data-ttu-id="f0919-151">Erişim türü: Salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="f0919-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0919-152">Bu uç noktanın benzersiz adı.</span><span class="sxs-lookup"><span data-stu-id="f0919-152">The unique name of this endpoint.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="f0919-153">İşlem kimliği</span><span class="sxs-lookup"><span data-stu-id="f0919-153">ProcessId</span></span>  
 <span data-ttu-id="f0919-154">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="f0919-154">Data type: sint32</span></span>  
  
 <span data-ttu-id="f0919-155">Erişim türü: Salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="f0919-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0919-156">Uç noktasını barındıran işlemin işlem kimliği.</span><span class="sxs-lookup"><span data-stu-id="f0919-156">The process Id of the process that hosts the endpoint.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="f0919-157">ref</span><span class="sxs-lookup"><span data-stu-id="f0919-157">ref</span></span>  
 <span data-ttu-id="f0919-158">Veri türü: Sözleşme</span><span class="sxs-lookup"><span data-stu-id="f0919-158">Data type: Contract</span></span>  
  
 <span data-ttu-id="f0919-159">Erişim türü: Salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="f0919-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0919-160">Bu uç noktanın sunduğu sözleşme.</span><span class="sxs-lookup"><span data-stu-id="f0919-160">The contract this endpoint is exposing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0919-161">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f0919-161">Requirements</span></span>  
  
|<span data-ttu-id="f0919-162">MOF</span><span class="sxs-lookup"><span data-stu-id="f0919-162">MOF</span></span>|<span data-ttu-id="f0919-163">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f0919-163">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f0919-164">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="f0919-164">Namespace</span></span>|<span data-ttu-id="f0919-165">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="f0919-165">Defined in root\ServiceModel</span></span>|
