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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 492a3cb4b11706bfabc42976fb1adfad24a2279a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="operation-class"></a><span data-ttu-id="adf88-102">İşlem sınıfı</span><span class="sxs-lookup"><span data-stu-id="adf88-102">Operation class</span></span>
<span data-ttu-id="adf88-103">Çalışma</span><span class="sxs-lookup"><span data-stu-id="adf88-103">Operation</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adf88-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="adf88-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="adf88-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="adf88-105">Methods</span></span>  
 <span data-ttu-id="adf88-106">İşlem sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="adf88-106">The Operation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="adf88-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="adf88-107">Properties</span></span>  
 <span data-ttu-id="adf88-108">İşlem sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="adf88-108">The Operation class has the following properties:</span></span>  
  
### <a name="action"></a><span data-ttu-id="adf88-109">Eylem</span><span class="sxs-lookup"><span data-stu-id="adf88-109">Action</span></span>  
 <span data-ttu-id="adf88-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="adf88-110">Data type: string</span></span>  
  
 <span data-ttu-id="adf88-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="adf88-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="adf88-112">İstek iletisinin WS adresleme eylem.</span><span class="sxs-lookup"><span data-stu-id="adf88-112">The WS-Addressing action of the request message.</span></span>  
  
### <a name="asyncpattern"></a><span data-ttu-id="adf88-113">Başlatıcıda</span><span class="sxs-lookup"><span data-stu-id="adf88-113">AsyncPattern</span></span>  
 <span data-ttu-id="adf88-114">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="adf88-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="adf88-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="adf88-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="adf88-116">Zaman uyumsuz olarak kullanarak, bir işlem yapılmayacağını gösterir bir `Begin`[Aç/Kapat köşeli] ve `End`[Aç/Kapat açılı ayraçları] yöntem çiftinin bir hizmet sözleşmesinde.</span><span class="sxs-lookup"><span data-stu-id="adf88-116">Indicates that an operation is implemented asynchronously using a `Begin`[open/close angle brackets] and `End`[open/close angle brackets] method pair in a service contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="adf88-117">Davranışlar</span><span class="sxs-lookup"><span data-stu-id="adf88-117">Behaviors</span></span>  
 <span data-ttu-id="adf88-118">Veri türü: davranış dizisi</span><span class="sxs-lookup"><span data-stu-id="adf88-118">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="adf88-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="adf88-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="adf88-120">Bu işlemle ilişkili davranışlar.</span><span class="sxs-lookup"><span data-stu-id="adf88-120">The behaviors associated with this operation.</span></span>  
  
### <a name="iscallback"></a><span data-ttu-id="adf88-121">IsCallback</span><span class="sxs-lookup"><span data-stu-id="adf88-121">IsCallback</span></span>  
 <span data-ttu-id="adf88-122">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="adf88-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="adf88-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="adf88-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="adf88-124">İşlemi bir geri çağırma işlemi olduğunda true olur.</span><span class="sxs-lookup"><span data-stu-id="adf88-124">True when the operation is a callback operation.</span></span>  
  
### <a name="isinitiating"></a><span data-ttu-id="adf88-125">IsInitiating</span><span class="sxs-lookup"><span data-stu-id="adf88-125">IsInitiating</span></span>  
 <span data-ttu-id="adf88-126">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="adf88-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="adf88-127">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="adf88-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="adf88-128">Yöntemi sunucudaki bir oturum başlatabilirsiniz bir işlem uygulayan olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="adf88-128">Indicates whether the method implements an operation that can initiate a session on the server.</span></span>  
  
### <a name="isoneway"></a><span data-ttu-id="adf88-129">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="adf88-129">IsOneWay</span></span>  
 <span data-ttu-id="adf88-130">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="adf88-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="adf88-131">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="adf88-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="adf88-132">Bir işlem bir yanıt iletisi döndürüp döndürmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="adf88-132">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="isterminating"></a><span data-ttu-id="adf88-133">IsTerminating</span><span class="sxs-lookup"><span data-stu-id="adf88-133">IsTerminating</span></span>  
 <span data-ttu-id="adf88-134">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="adf88-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="adf88-135">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="adf88-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="adf88-136">Bir işlem bir yanıt iletisi döndürüp döndürmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="adf88-136">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="methodsignature"></a><span data-ttu-id="adf88-137">MethodSignature</span><span class="sxs-lookup"><span data-stu-id="adf88-137">MethodSignature</span></span>  
 <span data-ttu-id="adf88-138">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="adf88-138">Data type: string</span></span>  
  
 <span data-ttu-id="adf88-139">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="adf88-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="adf88-140">İşlemi yöntemi imzası.</span><span class="sxs-lookup"><span data-stu-id="adf88-140">The method signature of the operation.</span></span>  
  
### <a name="name"></a><span data-ttu-id="adf88-141">Ad</span><span class="sxs-lookup"><span data-stu-id="adf88-141">Name</span></span>  
 <span data-ttu-id="adf88-142">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="adf88-142">Data type: string</span></span>  
  
 <span data-ttu-id="adf88-143">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="adf88-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="adf88-144">İşlemin adı.</span><span class="sxs-lookup"><span data-stu-id="adf88-144">The name of the operation.</span></span>  
  
### <a name="parametertypes"></a><span data-ttu-id="adf88-145">ParameterTypes</span><span class="sxs-lookup"><span data-stu-id="adf88-145">ParameterTypes</span></span>  
 <span data-ttu-id="adf88-146">Veri türü: dize dizisi</span><span class="sxs-lookup"><span data-stu-id="adf88-146">Data type: string array</span></span>  
  
 <span data-ttu-id="adf88-147">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="adf88-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="adf88-148">İşlemin parametre türleri.</span><span class="sxs-lookup"><span data-stu-id="adf88-148">The types of the parameters of the operation.</span></span>  
  
### <a name="replyaction"></a><span data-ttu-id="adf88-149">ReplyAction</span><span class="sxs-lookup"><span data-stu-id="adf88-149">ReplyAction</span></span>  
 <span data-ttu-id="adf88-150">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="adf88-150">Data type: string</span></span>  
  
 <span data-ttu-id="adf88-151">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="adf88-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="adf88-152">İşlem yanıt iletisi için SOAP eylemi değeri.</span><span class="sxs-lookup"><span data-stu-id="adf88-152">The value of the SOAP action for the reply message of the operation.</span></span>  
  
### <a name="returntype"></a><span data-ttu-id="adf88-153">ReturnType</span><span class="sxs-lookup"><span data-stu-id="adf88-153">ReturnType</span></span>  
 <span data-ttu-id="adf88-154">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="adf88-154">Data type: string</span></span>  
  
 <span data-ttu-id="adf88-155">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="adf88-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="adf88-156">İşlemin dönüş türü.</span><span class="sxs-lookup"><span data-stu-id="adf88-156">The return type of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="adf88-157">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="adf88-157">Requirements</span></span>  
  
|<span data-ttu-id="adf88-158">MOF</span><span class="sxs-lookup"><span data-stu-id="adf88-158">MOF</span></span>|<span data-ttu-id="adf88-159">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="adf88-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="adf88-160">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="adf88-160">Namespace</span></span>|<span data-ttu-id="adf88-161">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="adf88-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="adf88-162">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="adf88-162">See Also</span></span>  
 <xref:System.ServiceModel.Description.OperationDescription>
