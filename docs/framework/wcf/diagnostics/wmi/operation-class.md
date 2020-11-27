---
title: İşlem sınıfı
ms.date: 03/30/2017
ms.assetid: b19d1496-ef06-4d0c-b2ae-e728ec00cca0
ms.openlocfilehash: 6b47d933dc84813532398830c92c95210208a709
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96269164"
---
# <a name="operation-class"></a><span data-ttu-id="3d803-102">İşlem sınıfı</span><span class="sxs-lookup"><span data-stu-id="3d803-102">Operation class</span></span>

<span data-ttu-id="3d803-103">İşlem</span><span class="sxs-lookup"><span data-stu-id="3d803-103">Operation</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d803-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="3d803-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="3d803-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="3d803-105">Methods</span></span>  

 <span data-ttu-id="3d803-106">Işlem sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="3d803-106">The Operation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3d803-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="3d803-107">Properties</span></span>  

 <span data-ttu-id="3d803-108">Işlem sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="3d803-108">The Operation class has the following properties:</span></span>  
  
### <a name="action"></a><span data-ttu-id="3d803-109">Eylem</span><span class="sxs-lookup"><span data-stu-id="3d803-109">Action</span></span>  

 <span data-ttu-id="3d803-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="3d803-110">Data type: string</span></span>  
  
 <span data-ttu-id="3d803-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="3d803-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3d803-112">İstek iletisinin WS-Addressing eylemi.</span><span class="sxs-lookup"><span data-stu-id="3d803-112">The WS-Addressing action of the request message.</span></span>  
  
### <a name="asyncpattern"></a><span data-ttu-id="3d803-113">Metodundaki AsyncPattern</span><span class="sxs-lookup"><span data-stu-id="3d803-113">AsyncPattern</span></span>  

 <span data-ttu-id="3d803-114">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="3d803-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="3d803-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="3d803-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3d803-116">Bir işlemin zaman uyumsuz `Begin` olarak bir hizmet sözleşmesindeki [açık/kapalı açılı ayraçlar] ve `End` [açık/kapalı açılı ayraçlar] Yöntem çifti kullanılarak uygulandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3d803-116">Indicates that an operation is implemented asynchronously using a `Begin`[open/close angle brackets] and `End`[open/close angle brackets] method pair in a service contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="3d803-117">Davranışlar</span><span class="sxs-lookup"><span data-stu-id="3d803-117">Behaviors</span></span>  

 <span data-ttu-id="3d803-118">Veri türü: davranış dizisi</span><span class="sxs-lookup"><span data-stu-id="3d803-118">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="3d803-119">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="3d803-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3d803-120">Bu işlemle ilişkilendirilen davranışlar.</span><span class="sxs-lookup"><span data-stu-id="3d803-120">The behaviors associated with this operation.</span></span>  
  
### <a name="iscallback"></a><span data-ttu-id="3d803-121">IsCallback</span><span class="sxs-lookup"><span data-stu-id="3d803-121">IsCallback</span></span>  

 <span data-ttu-id="3d803-122">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="3d803-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="3d803-123">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="3d803-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3d803-124">İşlem bir geri çağırma işlemi olduğunda true.</span><span class="sxs-lookup"><span data-stu-id="3d803-124">True when the operation is a callback operation.</span></span>  
  
### <a name="isinitiating"></a><span data-ttu-id="3d803-125">IsInitiating</span><span class="sxs-lookup"><span data-stu-id="3d803-125">IsInitiating</span></span>  

 <span data-ttu-id="3d803-126">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="3d803-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="3d803-127">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="3d803-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3d803-128">Yöntemin sunucuda oturum başlatabilen bir işlem uygulayıp uygulamadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3d803-128">Indicates whether the method implements an operation that can initiate a session on the server.</span></span>  
  
### <a name="isoneway"></a><span data-ttu-id="3d803-129">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="3d803-129">IsOneWay</span></span>  

 <span data-ttu-id="3d803-130">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="3d803-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="3d803-131">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="3d803-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3d803-132">Bir işlemin yanıt iletisi döndürüp döndürmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3d803-132">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="isterminating"></a><span data-ttu-id="3d803-133">IsTerminating</span><span class="sxs-lookup"><span data-stu-id="3d803-133">IsTerminating</span></span>  

 <span data-ttu-id="3d803-134">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="3d803-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="3d803-135">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="3d803-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3d803-136">Bir işlemin yanıt iletisi döndürüp döndürmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3d803-136">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="methodsignature"></a><span data-ttu-id="3d803-137">MethodSignature</span><span class="sxs-lookup"><span data-stu-id="3d803-137">MethodSignature</span></span>  

 <span data-ttu-id="3d803-138">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="3d803-138">Data type: string</span></span>  
  
 <span data-ttu-id="3d803-139">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="3d803-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3d803-140">İşlemin Yöntem imzası.</span><span class="sxs-lookup"><span data-stu-id="3d803-140">The method signature of the operation.</span></span>  
  
### <a name="name"></a><span data-ttu-id="3d803-141">Adı</span><span class="sxs-lookup"><span data-stu-id="3d803-141">Name</span></span>  

 <span data-ttu-id="3d803-142">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="3d803-142">Data type: string</span></span>  
  
 <span data-ttu-id="3d803-143">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="3d803-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3d803-144">İşlemin adı.</span><span class="sxs-lookup"><span data-stu-id="3d803-144">The name of the operation.</span></span>  
  
### <a name="parametertypes"></a><span data-ttu-id="3d803-145">ParameterTypes</span><span class="sxs-lookup"><span data-stu-id="3d803-145">ParameterTypes</span></span>  

 <span data-ttu-id="3d803-146">Veri türü: dize dizisi</span><span class="sxs-lookup"><span data-stu-id="3d803-146">Data type: string array</span></span>  
  
 <span data-ttu-id="3d803-147">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="3d803-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3d803-148">İşlemin parametrelerinin türleri.</span><span class="sxs-lookup"><span data-stu-id="3d803-148">The types of the parameters of the operation.</span></span>  
  
### <a name="replyaction"></a><span data-ttu-id="3d803-149">ReplyAction</span><span class="sxs-lookup"><span data-stu-id="3d803-149">ReplyAction</span></span>  

 <span data-ttu-id="3d803-150">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="3d803-150">Data type: string</span></span>  
  
 <span data-ttu-id="3d803-151">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="3d803-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3d803-152">İşlemin yanıt iletisi için SOAP eyleminin değeri.</span><span class="sxs-lookup"><span data-stu-id="3d803-152">The value of the SOAP action for the reply message of the operation.</span></span>  
  
### <a name="returntype"></a><span data-ttu-id="3d803-153">'Indaki</span><span class="sxs-lookup"><span data-stu-id="3d803-153">ReturnType</span></span>  

 <span data-ttu-id="3d803-154">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="3d803-154">Data type: string</span></span>  
  
 <span data-ttu-id="3d803-155">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="3d803-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3d803-156">İşlemin dönüş türü.</span><span class="sxs-lookup"><span data-stu-id="3d803-156">The return type of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d803-157">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3d803-157">Requirements</span></span>  
  
|<span data-ttu-id="3d803-158">MOF</span><span class="sxs-lookup"><span data-stu-id="3d803-158">MOF</span></span>|<span data-ttu-id="3d803-159">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3d803-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="3d803-160">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="3d803-160">Namespace</span></span>|<span data-ttu-id="3d803-161">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="3d803-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3d803-162">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d803-162">See also</span></span>

- <xref:System.ServiceModel.Description.OperationDescription>
