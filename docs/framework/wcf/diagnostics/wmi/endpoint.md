---
title: Uç Noktası
ms.date: 03/30/2017
ms.assetid: fe63370d-81a1-40f3-97c2-59cb357c78d2
ms.openlocfilehash: 4562481e8b0b18c0ea0d9df0af3427ffe6419821
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963611"
---
# <a name="endpoint"></a><span data-ttu-id="b5cbc-102">Uç Noktası</span><span class="sxs-lookup"><span data-stu-id="b5cbc-102">Endpoint</span></span>
<span data-ttu-id="b5cbc-103">Uç Noktası</span><span class="sxs-lookup"><span data-stu-id="b5cbc-103">Endpoint</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5cbc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b5cbc-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="b5cbc-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b5cbc-105">Methods</span></span>  
 <span data-ttu-id="b5cbc-106">Uç nokta sınıfı, aşağıdaki yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b5cbc-106">The Endpoint class defines the following method.</span></span>  
  
|<span data-ttu-id="b5cbc-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b5cbc-107">Method</span></span>|<span data-ttu-id="b5cbc-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b5cbc-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b5cbc-109">GetOperationCounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="b5cbc-109">GetOperationCounterInstanceName</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/getoperationcounterinstancename.md)|<span data-ttu-id="b5cbc-110">İşlemi performans sayacı örneği adını alır.</span><span class="sxs-lookup"><span data-stu-id="b5cbc-110">Retrieves the operation performance counter instance name</span></span>|  
  
## <a name="properties"></a><span data-ttu-id="b5cbc-111">Özellikler</span><span class="sxs-lookup"><span data-stu-id="b5cbc-111">Properties</span></span>  
 <span data-ttu-id="b5cbc-112">Uç nokta sınıfı, aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="b5cbc-112">The Endpoint class has the following properties:</span></span>  
  
### <a name="address"></a><span data-ttu-id="b5cbc-113">Adres</span><span class="sxs-lookup"><span data-stu-id="b5cbc-113">Address</span></span>  
 <span data-ttu-id="b5cbc-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="b5cbc-114">Data type: string</span></span>  
  
 <span data-ttu-id="b5cbc-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="b5cbc-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b5cbc-116">Bitiş noktasının adresini içeren bir URI.</span><span class="sxs-lookup"><span data-stu-id="b5cbc-116">A URI that contains the address of the endpoint.</span></span>  
  
### <a name="addressheaders"></a><span data-ttu-id="b5cbc-117">AddressHeaders</span><span class="sxs-lookup"><span data-stu-id="b5cbc-117">AddressHeaders</span></span>  
 <span data-ttu-id="b5cbc-118">Veri türü: dize dizisi</span><span class="sxs-lookup"><span data-stu-id="b5cbc-118">Data type: string array</span></span>  
  
 <span data-ttu-id="b5cbc-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="b5cbc-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b5cbc-120">Adres üstbilgileri Bu uç noktaya bağlı koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="b5cbc-120">The collection of address headers attached to this endpoint.</span></span>  
  
### <a name="addressidentity"></a><span data-ttu-id="b5cbc-121">AddressIdentity</span><span class="sxs-lookup"><span data-stu-id="b5cbc-121">AddressIdentity</span></span>  
 <span data-ttu-id="b5cbc-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="b5cbc-122">Data type: string</span></span>  
  
 <span data-ttu-id="b5cbc-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="b5cbc-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b5cbc-124">Uç noktanın kimliği.</span><span class="sxs-lookup"><span data-stu-id="b5cbc-124">The identity of the endpoint.</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="b5cbc-125">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="b5cbc-125">AppDomainId</span></span>  
 <span data-ttu-id="b5cbc-126">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="b5cbc-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="b5cbc-127">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="b5cbc-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b5cbc-128">Uç noktayı barındıran appdomain kimliği.</span><span class="sxs-lookup"><span data-stu-id="b5cbc-128">The appdomain id of the appdomain that hosts the endpoint.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="b5cbc-129">Davranışlar</span><span class="sxs-lookup"><span data-stu-id="b5cbc-129">Behaviors</span></span>  
 <span data-ttu-id="b5cbc-130">Veri türü: Davranış dizi</span><span class="sxs-lookup"><span data-stu-id="b5cbc-130">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="b5cbc-131">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="b5cbc-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b5cbc-132">Bu bitiş noktası tarafından uygulanan davranış koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="b5cbc-132">The collection of behaviors implemented by this endpoint.</span></span>  
  
### <a name="binding"></a><span data-ttu-id="b5cbc-133">Bağlama</span><span class="sxs-lookup"><span data-stu-id="b5cbc-133">Binding</span></span>  
 <span data-ttu-id="b5cbc-134">Veri türü: Bağlama</span><span class="sxs-lookup"><span data-stu-id="b5cbc-134">Data type: Binding</span></span>  
  
 <span data-ttu-id="b5cbc-135">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="b5cbc-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b5cbc-136">Bu uç nokta tarafından kullanılan bağlama.</span><span class="sxs-lookup"><span data-stu-id="b5cbc-136">The binding used by this endpoint.</span></span>  
  
### <a name="contractname"></a><span data-ttu-id="b5cbc-137">ContractName</span><span class="sxs-lookup"><span data-stu-id="b5cbc-137">ContractName</span></span>  
 <span data-ttu-id="b5cbc-138">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="b5cbc-138">Data type: string</span></span>  
  
 <span data-ttu-id="b5cbc-139">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="b5cbc-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b5cbc-140">Hangi anlaşmanın belirten bir dize bu koncový bod vystavuje.</span><span class="sxs-lookup"><span data-stu-id="b5cbc-140">A string that specifies which contract this endpoint is exposing.</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="b5cbc-141">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="b5cbc-141">CounterInstanceName</span></span>  
 <span data-ttu-id="b5cbc-142">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="b5cbc-142">Data type: string</span></span>  
  
 <span data-ttu-id="b5cbc-143">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="b5cbc-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b5cbc-144">Uç nokta performans sayaçları örneğinin adı.</span><span class="sxs-lookup"><span data-stu-id="b5cbc-144">The name of the instance of performance counters of the endpoint.</span></span>  
  
### <a name="listenuri"></a><span data-ttu-id="b5cbc-145">ListenUri</span><span class="sxs-lookup"><span data-stu-id="b5cbc-145">ListenUri</span></span>  
 <span data-ttu-id="b5cbc-146">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="b5cbc-146">Data type: string</span></span>  
  
 <span data-ttu-id="b5cbc-147">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="b5cbc-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b5cbc-148">Uç nokta URI'si dinler.</span><span class="sxs-lookup"><span data-stu-id="b5cbc-148">The Uri the endpoint listens on.</span></span>  
  
### <a name="name"></a><span data-ttu-id="b5cbc-149">Ad</span><span class="sxs-lookup"><span data-stu-id="b5cbc-149">Name</span></span>  
 <span data-ttu-id="b5cbc-150">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="b5cbc-150">Data type: string</span></span>  
  
 <span data-ttu-id="b5cbc-151">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="b5cbc-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b5cbc-152">Bu uç nokta benzersiz adı.</span><span class="sxs-lookup"><span data-stu-id="b5cbc-152">The unique name of this endpoint.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="b5cbc-153">İşlem kimliği</span><span class="sxs-lookup"><span data-stu-id="b5cbc-153">ProcessId</span></span>  
 <span data-ttu-id="b5cbc-154">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="b5cbc-154">Data type: sint32</span></span>  
  
 <span data-ttu-id="b5cbc-155">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="b5cbc-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b5cbc-156">İşlem uç noktasını barındıran işlem kimliği.</span><span class="sxs-lookup"><span data-stu-id="b5cbc-156">The process Id of the process that hosts the endpoint.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="b5cbc-157">ref</span><span class="sxs-lookup"><span data-stu-id="b5cbc-157">ref</span></span>  
 <span data-ttu-id="b5cbc-158">Veri türü: Sözleşme</span><span class="sxs-lookup"><span data-stu-id="b5cbc-158">Data type: Contract</span></span>  
  
 <span data-ttu-id="b5cbc-159">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="b5cbc-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b5cbc-160">Bu uç noktanın sözleşme.</span><span class="sxs-lookup"><span data-stu-id="b5cbc-160">The contract this endpoint is exposing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5cbc-161">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b5cbc-161">Requirements</span></span>  
  
|<span data-ttu-id="b5cbc-162">MOF</span><span class="sxs-lookup"><span data-stu-id="b5cbc-162">MOF</span></span>|<span data-ttu-id="b5cbc-163">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b5cbc-163">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b5cbc-164">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="b5cbc-164">Namespace</span></span>|<span data-ttu-id="b5cbc-165">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b5cbc-165">Defined in root\ServiceModel</span></span>|
