---
description: 'Daha fazla bilgi edinin: Işlem sınıfı'
title: İşlem sınıfı
ms.date: 03/30/2017
ms.assetid: b19d1496-ef06-4d0c-b2ae-e728ec00cca0
ms.openlocfilehash: 035c02bc05b7a64c5d15538001dbdcf2ec0b135b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803080"
---
# <a name="operation-class"></a><span data-ttu-id="7116e-103">İşlem sınıfı</span><span class="sxs-lookup"><span data-stu-id="7116e-103">Operation class</span></span>

<span data-ttu-id="7116e-104">İşlem</span><span class="sxs-lookup"><span data-stu-id="7116e-104">Operation</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7116e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7116e-105">Syntax</span></span>  
  
```csharp
class Operation  
{  
  string Action;  
  boolean AsyncPattern;  
  Behavior Behaviors[];  
  boolean IsCallback;  
  boolean IsInitiating;  
  boolean IsOneWay;  
  boolean IsTerminating;  
  string MethodSignature;  
  string Name;  
  string ParameterTypes[];  
  string ReplyAction;  
  string ReturnType;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="7116e-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7116e-106">Methods</span></span>  

 <span data-ttu-id="7116e-107">Işlem sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="7116e-107">The Operation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7116e-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="7116e-108">Properties</span></span>  

 <span data-ttu-id="7116e-109">Işlem sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="7116e-109">The Operation class has the following properties:</span></span>  
  
### <a name="action"></a><span data-ttu-id="7116e-110">Eylem</span><span class="sxs-lookup"><span data-stu-id="7116e-110">Action</span></span>  

 <span data-ttu-id="7116e-111">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="7116e-111">Data type: string</span></span>  
  
 <span data-ttu-id="7116e-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="7116e-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7116e-113">İstek iletisinin WS-Addressing eylemi.</span><span class="sxs-lookup"><span data-stu-id="7116e-113">The WS-Addressing action of the request message.</span></span>  
  
### <a name="asyncpattern"></a><span data-ttu-id="7116e-114">Metodundaki AsyncPattern</span><span class="sxs-lookup"><span data-stu-id="7116e-114">AsyncPattern</span></span>  

 <span data-ttu-id="7116e-115">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="7116e-115">Data type: boolean</span></span>  
  
 <span data-ttu-id="7116e-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="7116e-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7116e-117">Bir işlemin zaman uyumsuz `Begin` olarak bir hizmet sözleşmesindeki [açık/kapalı açılı ayraçlar] ve `End` [açık/kapalı açılı ayraçlar] Yöntem çifti kullanılarak uygulandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7116e-117">Indicates that an operation is implemented asynchronously using a `Begin`[open/close angle brackets] and `End`[open/close angle brackets] method pair in a service contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="7116e-118">Davranışlar</span><span class="sxs-lookup"><span data-stu-id="7116e-118">Behaviors</span></span>  

 <span data-ttu-id="7116e-119">Veri türü: davranış dizisi</span><span class="sxs-lookup"><span data-stu-id="7116e-119">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="7116e-120">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="7116e-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7116e-121">Bu işlemle ilişkilendirilen davranışlar.</span><span class="sxs-lookup"><span data-stu-id="7116e-121">The behaviors associated with this operation.</span></span>  
  
### <a name="iscallback"></a><span data-ttu-id="7116e-122">IsCallback</span><span class="sxs-lookup"><span data-stu-id="7116e-122">IsCallback</span></span>  

 <span data-ttu-id="7116e-123">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="7116e-123">Data type: boolean</span></span>  
  
 <span data-ttu-id="7116e-124">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="7116e-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7116e-125">İşlem bir geri çağırma işlemi olduğunda true.</span><span class="sxs-lookup"><span data-stu-id="7116e-125">True when the operation is a callback operation.</span></span>  
  
### <a name="isinitiating"></a><span data-ttu-id="7116e-126">IsInitiating</span><span class="sxs-lookup"><span data-stu-id="7116e-126">IsInitiating</span></span>  

 <span data-ttu-id="7116e-127">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="7116e-127">Data type: boolean</span></span>  
  
 <span data-ttu-id="7116e-128">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="7116e-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7116e-129">Yöntemin sunucuda oturum başlatabilen bir işlem uygulayıp uygulamadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7116e-129">Indicates whether the method implements an operation that can initiate a session on the server.</span></span>  
  
### <a name="isoneway"></a><span data-ttu-id="7116e-130">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="7116e-130">IsOneWay</span></span>  

 <span data-ttu-id="7116e-131">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="7116e-131">Data type: boolean</span></span>  
  
 <span data-ttu-id="7116e-132">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="7116e-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7116e-133">Bir işlemin yanıt iletisi döndürüp döndürmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7116e-133">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="isterminating"></a><span data-ttu-id="7116e-134">IsTerminating</span><span class="sxs-lookup"><span data-stu-id="7116e-134">IsTerminating</span></span>  

 <span data-ttu-id="7116e-135">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="7116e-135">Data type: boolean</span></span>  
  
 <span data-ttu-id="7116e-136">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="7116e-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7116e-137">Bir işlemin yanıt iletisi döndürüp döndürmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7116e-137">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="methodsignature"></a><span data-ttu-id="7116e-138">MethodSignature</span><span class="sxs-lookup"><span data-stu-id="7116e-138">MethodSignature</span></span>  

 <span data-ttu-id="7116e-139">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="7116e-139">Data type: string</span></span>  
  
 <span data-ttu-id="7116e-140">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="7116e-140">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7116e-141">İşlemin Yöntem imzası.</span><span class="sxs-lookup"><span data-stu-id="7116e-141">The method signature of the operation.</span></span>  
  
### <a name="name"></a><span data-ttu-id="7116e-142">Name</span><span class="sxs-lookup"><span data-stu-id="7116e-142">Name</span></span>  

 <span data-ttu-id="7116e-143">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="7116e-143">Data type: string</span></span>  
  
 <span data-ttu-id="7116e-144">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="7116e-144">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7116e-145">İşlemin adı.</span><span class="sxs-lookup"><span data-stu-id="7116e-145">The name of the operation.</span></span>  
  
### <a name="parametertypes"></a><span data-ttu-id="7116e-146">ParameterTypes</span><span class="sxs-lookup"><span data-stu-id="7116e-146">ParameterTypes</span></span>  

 <span data-ttu-id="7116e-147">Veri türü: dize dizisi</span><span class="sxs-lookup"><span data-stu-id="7116e-147">Data type: string array</span></span>  
  
 <span data-ttu-id="7116e-148">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="7116e-148">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7116e-149">İşlemin parametrelerinin türleri.</span><span class="sxs-lookup"><span data-stu-id="7116e-149">The types of the parameters of the operation.</span></span>  
  
### <a name="replyaction"></a><span data-ttu-id="7116e-150">ReplyAction</span><span class="sxs-lookup"><span data-stu-id="7116e-150">ReplyAction</span></span>  

 <span data-ttu-id="7116e-151">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="7116e-151">Data type: string</span></span>  
  
 <span data-ttu-id="7116e-152">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="7116e-152">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7116e-153">İşlemin yanıt iletisi için SOAP eyleminin değeri.</span><span class="sxs-lookup"><span data-stu-id="7116e-153">The value of the SOAP action for the reply message of the operation.</span></span>  
  
### <a name="returntype"></a><span data-ttu-id="7116e-154">'Indaki</span><span class="sxs-lookup"><span data-stu-id="7116e-154">ReturnType</span></span>  

 <span data-ttu-id="7116e-155">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="7116e-155">Data type: string</span></span>  
  
 <span data-ttu-id="7116e-156">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="7116e-156">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7116e-157">İşlemin dönüş türü.</span><span class="sxs-lookup"><span data-stu-id="7116e-157">The return type of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7116e-158">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7116e-158">Requirements</span></span>  
  
|<span data-ttu-id="7116e-159">MOF</span><span class="sxs-lookup"><span data-stu-id="7116e-159">MOF</span></span>|<span data-ttu-id="7116e-160">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7116e-160">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="7116e-161">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="7116e-161">Namespace</span></span>|<span data-ttu-id="7116e-162">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="7116e-162">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7116e-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7116e-163">See also</span></span>

- <xref:System.ServiceModel.Description.OperationDescription>
