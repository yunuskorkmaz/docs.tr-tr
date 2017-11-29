---
title: "İşlem sınıfı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b19d1496-ef06-4d0c-b2ae-e728ec00cca0
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 739f8309e7a01eeecf921b50fcde24417fbbc515
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="operation-class"></a><span data-ttu-id="3b794-102">İşlem sınıfı</span><span class="sxs-lookup"><span data-stu-id="3b794-102">Operation class</span></span>
<span data-ttu-id="3b794-103">Çalışma</span><span class="sxs-lookup"><span data-stu-id="3b794-103">Operation</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b794-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3b794-104">Syntax</span></span>  
  
```  
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
  
## <a name="methods"></a><span data-ttu-id="3b794-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="3b794-105">Methods</span></span>  
 <span data-ttu-id="3b794-106">İşlem sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="3b794-106">The Operation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3b794-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="3b794-107">Properties</span></span>  
 <span data-ttu-id="3b794-108">İşlem sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="3b794-108">The Operation class has the following properties:</span></span>  
  
### <a name="action"></a><span data-ttu-id="3b794-109">Eylem</span><span class="sxs-lookup"><span data-stu-id="3b794-109">Action</span></span>  
 <span data-ttu-id="3b794-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="3b794-110">Data type: string</span></span>  
  
 <span data-ttu-id="3b794-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="3b794-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3b794-112">İstek iletisinin WS adresleme eylem.</span><span class="sxs-lookup"><span data-stu-id="3b794-112">The WS-Addressing action of the request message.</span></span>  
  
### <a name="asyncpattern"></a><span data-ttu-id="3b794-113">Başlatıcıda</span><span class="sxs-lookup"><span data-stu-id="3b794-113">AsyncPattern</span></span>  
 <span data-ttu-id="3b794-114">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="3b794-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="3b794-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="3b794-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3b794-116">Zaman uyumsuz olarak kullanarak, bir işlem yapılmayacağını gösterir bir `Begin`[Aç/Kapat köşeli] ve `End`[Aç/Kapat açılı ayraçları] yöntem çiftinin bir hizmet sözleşmesinde.</span><span class="sxs-lookup"><span data-stu-id="3b794-116">Indicates that an operation is implemented asynchronously using a `Begin`[open/close angle brackets] and `End`[open/close angle brackets] method pair in a service contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="3b794-117">Davranışlar</span><span class="sxs-lookup"><span data-stu-id="3b794-117">Behaviors</span></span>  
 <span data-ttu-id="3b794-118">Veri türü: davranış dizisi</span><span class="sxs-lookup"><span data-stu-id="3b794-118">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="3b794-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="3b794-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3b794-120">Bu işlemle ilişkili davranışlar.</span><span class="sxs-lookup"><span data-stu-id="3b794-120">The behaviors associated with this operation.</span></span>  
  
### <a name="iscallback"></a><span data-ttu-id="3b794-121">IsCallback</span><span class="sxs-lookup"><span data-stu-id="3b794-121">IsCallback</span></span>  
 <span data-ttu-id="3b794-122">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="3b794-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="3b794-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="3b794-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3b794-124">İşlemi bir geri çağırma işlemi olduğunda true olur.</span><span class="sxs-lookup"><span data-stu-id="3b794-124">True when the operation is a callback operation.</span></span>  
  
### <a name="isinitiating"></a><span data-ttu-id="3b794-125">IsInitiating</span><span class="sxs-lookup"><span data-stu-id="3b794-125">IsInitiating</span></span>  
 <span data-ttu-id="3b794-126">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="3b794-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="3b794-127">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="3b794-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3b794-128">Yöntemi sunucudaki bir oturum başlatabilirsiniz bir işlem uygulayan olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3b794-128">Indicates whether the method implements an operation that can initiate a session on the server.</span></span>  
  
### <a name="isoneway"></a><span data-ttu-id="3b794-129">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="3b794-129">IsOneWay</span></span>  
 <span data-ttu-id="3b794-130">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="3b794-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="3b794-131">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="3b794-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3b794-132">Bir işlem bir yanıt iletisi döndürüp döndürmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3b794-132">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="isterminating"></a><span data-ttu-id="3b794-133">IsTerminating</span><span class="sxs-lookup"><span data-stu-id="3b794-133">IsTerminating</span></span>  
 <span data-ttu-id="3b794-134">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="3b794-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="3b794-135">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="3b794-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3b794-136">Bir işlem bir yanıt iletisi döndürüp döndürmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3b794-136">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="methodsignature"></a><span data-ttu-id="3b794-137">MethodSignature</span><span class="sxs-lookup"><span data-stu-id="3b794-137">MethodSignature</span></span>  
 <span data-ttu-id="3b794-138">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="3b794-138">Data type: string</span></span>  
  
 <span data-ttu-id="3b794-139">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="3b794-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3b794-140">İşlemi yöntemi imzası.</span><span class="sxs-lookup"><span data-stu-id="3b794-140">The method signature of the operation.</span></span>  
  
### <a name="name"></a><span data-ttu-id="3b794-141">Ad</span><span class="sxs-lookup"><span data-stu-id="3b794-141">Name</span></span>  
 <span data-ttu-id="3b794-142">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="3b794-142">Data type: string</span></span>  
  
 <span data-ttu-id="3b794-143">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="3b794-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3b794-144">İşlemin adı.</span><span class="sxs-lookup"><span data-stu-id="3b794-144">The name of the operation.</span></span>  
  
### <a name="parametertypes"></a><span data-ttu-id="3b794-145">ParameterTypes</span><span class="sxs-lookup"><span data-stu-id="3b794-145">ParameterTypes</span></span>  
 <span data-ttu-id="3b794-146">Veri türü: dize dizisi</span><span class="sxs-lookup"><span data-stu-id="3b794-146">Data type: string array</span></span>  
  
 <span data-ttu-id="3b794-147">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="3b794-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3b794-148">İşlemin parametre türleri.</span><span class="sxs-lookup"><span data-stu-id="3b794-148">The types of the parameters of the operation.</span></span>  
  
### <a name="replyaction"></a><span data-ttu-id="3b794-149">ReplyAction</span><span class="sxs-lookup"><span data-stu-id="3b794-149">ReplyAction</span></span>  
 <span data-ttu-id="3b794-150">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="3b794-150">Data type: string</span></span>  
  
 <span data-ttu-id="3b794-151">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="3b794-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3b794-152">İşlem yanıt iletisi için SOAP eylemi değeri.</span><span class="sxs-lookup"><span data-stu-id="3b794-152">The value of the SOAP action for the reply message of the operation.</span></span>  
  
### <a name="returntype"></a><span data-ttu-id="3b794-153">ReturnType</span><span class="sxs-lookup"><span data-stu-id="3b794-153">ReturnType</span></span>  
 <span data-ttu-id="3b794-154">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="3b794-154">Data type: string</span></span>  
  
 <span data-ttu-id="3b794-155">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="3b794-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3b794-156">İşlemin dönüş türü.</span><span class="sxs-lookup"><span data-stu-id="3b794-156">The return type of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b794-157">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3b794-157">Requirements</span></span>  
  
|<span data-ttu-id="3b794-158">MOF</span><span class="sxs-lookup"><span data-stu-id="3b794-158">MOF</span></span>|<span data-ttu-id="3b794-159">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="3b794-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="3b794-160">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="3b794-160">Namespace</span></span>|<span data-ttu-id="3b794-161">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3b794-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3b794-162">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3b794-162">See Also</span></span>  
 <xref:System.ServiceModel.Description.OperationDescription>
