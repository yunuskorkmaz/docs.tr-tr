---
title: İşlem sınıfı
ms.date: 03/30/2017
ms.assetid: b19d1496-ef06-4d0c-b2ae-e728ec00cca0
ms.openlocfilehash: 9696a7f026e54afacb5ccbfa8703a2ba617a9f3d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165086"
---
# <a name="operation-class"></a><span data-ttu-id="162f4-102">İşlem sınıfı</span><span class="sxs-lookup"><span data-stu-id="162f4-102">Operation class</span></span>
<span data-ttu-id="162f4-103">Çalışma</span><span class="sxs-lookup"><span data-stu-id="162f4-103">Operation</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="162f4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="162f4-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="162f4-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="162f4-105">Methods</span></span>  
 <span data-ttu-id="162f4-106">İşlem sınıfı herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="162f4-106">The Operation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="162f4-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="162f4-107">Properties</span></span>  
 <span data-ttu-id="162f4-108">İşlem sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="162f4-108">The Operation class has the following properties:</span></span>  
  
### <a name="action"></a><span data-ttu-id="162f4-109">Eylem</span><span class="sxs-lookup"><span data-stu-id="162f4-109">Action</span></span>  
 <span data-ttu-id="162f4-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="162f4-110">Data type: string</span></span>  
  
 <span data-ttu-id="162f4-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="162f4-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="162f4-112">İstek iletisinin WS-Addressing eylem.</span><span class="sxs-lookup"><span data-stu-id="162f4-112">The WS-Addressing action of the request message.</span></span>  
  
### <a name="asyncpattern"></a><span data-ttu-id="162f4-113">AsyncPattern</span><span class="sxs-lookup"><span data-stu-id="162f4-113">AsyncPattern</span></span>  
 <span data-ttu-id="162f4-114">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="162f4-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="162f4-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="162f4-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="162f4-116">Bir işlem kullanarak zaman uyumsuz olarak uygulandığını belirtir bir `Begin`[Aç/Kapat açılı ayraçlar] ve `End`hizmet sözleşmesi [Aç/Kapat açılı ayraçlar] yöntemi çifti.</span><span class="sxs-lookup"><span data-stu-id="162f4-116">Indicates that an operation is implemented asynchronously using a `Begin`[open/close angle brackets] and `End`[open/close angle brackets] method pair in a service contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="162f4-117">Davranışlar</span><span class="sxs-lookup"><span data-stu-id="162f4-117">Behaviors</span></span>  
 <span data-ttu-id="162f4-118">Veri türü: Davranış dizi</span><span class="sxs-lookup"><span data-stu-id="162f4-118">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="162f4-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="162f4-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="162f4-120">Bu işlemle ilişkili davranışlar.</span><span class="sxs-lookup"><span data-stu-id="162f4-120">The behaviors associated with this operation.</span></span>  
  
### <a name="iscallback"></a><span data-ttu-id="162f4-121">IsCallback</span><span class="sxs-lookup"><span data-stu-id="162f4-121">IsCallback</span></span>  
 <span data-ttu-id="162f4-122">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="162f4-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="162f4-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="162f4-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="162f4-124">İşlemi bir geri çağırma işlemi olduğunda true olur.</span><span class="sxs-lookup"><span data-stu-id="162f4-124">True when the operation is a callback operation.</span></span>  
  
### <a name="isinitiating"></a><span data-ttu-id="162f4-125">IsInitiating</span><span class="sxs-lookup"><span data-stu-id="162f4-125">IsInitiating</span></span>  
 <span data-ttu-id="162f4-126">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="162f4-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="162f4-127">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="162f4-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="162f4-128">Yöntemi sunucudaki bir oturum başlatabilirsiniz bir işlem uygulayıp uygulamadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="162f4-128">Indicates whether the method implements an operation that can initiate a session on the server.</span></span>  
  
### <a name="isoneway"></a><span data-ttu-id="162f4-129">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="162f4-129">IsOneWay</span></span>  
 <span data-ttu-id="162f4-130">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="162f4-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="162f4-131">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="162f4-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="162f4-132">Bir işlem bir yanıt iletisi döndürüp döndürmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="162f4-132">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="isterminating"></a><span data-ttu-id="162f4-133">IsTerminating</span><span class="sxs-lookup"><span data-stu-id="162f4-133">IsTerminating</span></span>  
 <span data-ttu-id="162f4-134">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="162f4-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="162f4-135">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="162f4-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="162f4-136">Bir işlem bir yanıt iletisi döndürüp döndürmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="162f4-136">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="methodsignature"></a><span data-ttu-id="162f4-137">MethodSignature</span><span class="sxs-lookup"><span data-stu-id="162f4-137">MethodSignature</span></span>  
 <span data-ttu-id="162f4-138">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="162f4-138">Data type: string</span></span>  
  
 <span data-ttu-id="162f4-139">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="162f4-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="162f4-140">İşlem metodu imzası.</span><span class="sxs-lookup"><span data-stu-id="162f4-140">The method signature of the operation.</span></span>  
  
### <a name="name"></a><span data-ttu-id="162f4-141">Ad</span><span class="sxs-lookup"><span data-stu-id="162f4-141">Name</span></span>  
 <span data-ttu-id="162f4-142">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="162f4-142">Data type: string</span></span>  
  
 <span data-ttu-id="162f4-143">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="162f4-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="162f4-144">İşlemin adı.</span><span class="sxs-lookup"><span data-stu-id="162f4-144">The name of the operation.</span></span>  
  
### <a name="parametertypes"></a><span data-ttu-id="162f4-145">ParameterTypes</span><span class="sxs-lookup"><span data-stu-id="162f4-145">ParameterTypes</span></span>  
 <span data-ttu-id="162f4-146">Veri türü: dize dizisi</span><span class="sxs-lookup"><span data-stu-id="162f4-146">Data type: string array</span></span>  
  
 <span data-ttu-id="162f4-147">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="162f4-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="162f4-148">İşlem parametrelerinin türleri.</span><span class="sxs-lookup"><span data-stu-id="162f4-148">The types of the parameters of the operation.</span></span>  
  
### <a name="replyaction"></a><span data-ttu-id="162f4-149">ReplyAction</span><span class="sxs-lookup"><span data-stu-id="162f4-149">ReplyAction</span></span>  
 <span data-ttu-id="162f4-150">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="162f4-150">Data type: string</span></span>  
  
 <span data-ttu-id="162f4-151">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="162f4-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="162f4-152">İşlem yanıt iletisi için SOAP eylemi değeri.</span><span class="sxs-lookup"><span data-stu-id="162f4-152">The value of the SOAP action for the reply message of the operation.</span></span>  
  
### <a name="returntype"></a><span data-ttu-id="162f4-153">ReturnType</span><span class="sxs-lookup"><span data-stu-id="162f4-153">ReturnType</span></span>  
 <span data-ttu-id="162f4-154">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="162f4-154">Data type: string</span></span>  
  
 <span data-ttu-id="162f4-155">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="162f4-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="162f4-156">İşlemin dönüş türü.</span><span class="sxs-lookup"><span data-stu-id="162f4-156">The return type of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="162f4-157">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="162f4-157">Requirements</span></span>  
  
|<span data-ttu-id="162f4-158">MOF</span><span class="sxs-lookup"><span data-stu-id="162f4-158">MOF</span></span>|<span data-ttu-id="162f4-159">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="162f4-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="162f4-160">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="162f4-160">Namespace</span></span>|<span data-ttu-id="162f4-161">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="162f4-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="162f4-162">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="162f4-162">See also</span></span>

- <xref:System.ServiceModel.Description.OperationDescription>
