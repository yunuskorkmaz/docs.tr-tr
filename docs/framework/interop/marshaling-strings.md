---
title: "Dizeleri Hazırlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- marshaling, samples
- platform invoke, marshaling data
- data marshaling, strings
- data marshaling, samples
- data marshaling, platform invoke
- marshaling. strings
- marshaling, platform invoke
- sample applications [.NET Framework], marshaling strings
ms.assetid: e21b078b-70fb-4905-be26-c097ab2433ff
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 89dace5ba946f2c6bd1384f23ffcff797e99bdd4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="marshaling-strings"></a><span data-ttu-id="78df7-102">Dizeleri Hazırlama</span><span class="sxs-lookup"><span data-stu-id="78df7-102">Marshaling Strings</span></span>
<span data-ttu-id="78df7-103">Platform çağırma bunları .NET Framework biçimden (Unicode) yönetilmeyen biçimi (ANSI), gerekirse dönüştürme kopyaları dizesi parametreleri.</span><span class="sxs-lookup"><span data-stu-id="78df7-103">Platform invoke copies string parameters, converting them from the .NET Framework format (Unicode) to the unmanaged format (ANSI), if needed.</span></span> <span data-ttu-id="78df7-104">Yönetilen dizeleri değişmez olduğundan, platform çağırma işlevi döndüğünde bunları yönetilmeyen bellekten yönetilen bellek kopyalamaz.</span><span class="sxs-lookup"><span data-stu-id="78df7-104">Because managed strings are immutable, platform invoke does not copy them back from unmanaged memory to managed memory when the function returns.</span></span>  
  
 <span data-ttu-id="78df7-105">Aşağıdaki tabloda dizeleri sıralama seçeneklerini listeler, bunların kullanım açıklar ve karşılık gelen .NET Framework örnek bağlantı sağlar.</span><span class="sxs-lookup"><span data-stu-id="78df7-105">The following table lists marshaling options for strings, describes their usage, and provides a link to the corresponding .NET Framework sample.</span></span>  
  
|<span data-ttu-id="78df7-106">Dize</span><span class="sxs-lookup"><span data-stu-id="78df7-106">String</span></span>|<span data-ttu-id="78df7-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="78df7-107">Description</span></span>|<span data-ttu-id="78df7-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="78df7-108">Sample</span></span>|  
|------------|-----------------|------------|  
|<span data-ttu-id="78df7-109">Değer tarafından.</span><span class="sxs-lookup"><span data-stu-id="78df7-109">By value.</span></span>|<span data-ttu-id="78df7-110">Dizeleri parametreleri olduğu gibi geçirir.</span><span class="sxs-lookup"><span data-stu-id="78df7-110">Passes strings as In parameters.</span></span>|[<span data-ttu-id="78df7-111">MsgBox</span><span class="sxs-lookup"><span data-stu-id="78df7-111">MsgBox</span></span>](../../../docs/framework/interop/msgbox-sample.md)|  
|<span data-ttu-id="78df7-112">Sonuç olarak.</span><span class="sxs-lookup"><span data-stu-id="78df7-112">As result.</span></span>|<span data-ttu-id="78df7-113">Yönetilmeyen kod dizelerden döndürür.</span><span class="sxs-lookup"><span data-stu-id="78df7-113">Returns strings from unmanaged code.</span></span>|[<span data-ttu-id="78df7-114">Dizeler</span><span class="sxs-lookup"><span data-stu-id="78df7-114">Strings</span></span>](http://msdn.microsoft.com/en-us/be9e82a3-dc95-4aaa-9396-61b66e467e02)|  
|<span data-ttu-id="78df7-115">Başvuruya göre.</span><span class="sxs-lookup"><span data-stu-id="78df7-115">By reference.</span></span>|<span data-ttu-id="78df7-116">Dizeleri olarak giriş/çıkış kullanarak parametrelerini geçirir <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="78df7-116">Passes strings as In/Out parameters using <xref:System.Text.StringBuilder>.</span></span>|[<span data-ttu-id="78df7-117">Arabellekler</span><span class="sxs-lookup"><span data-stu-id="78df7-117">Buffers</span></span>](http://msdn.microsoft.com/en-us/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5)|  
|<span data-ttu-id="78df7-118">Değere göre bir yapısında.</span><span class="sxs-lookup"><span data-stu-id="78df7-118">In a structure by value.</span></span>|<span data-ttu-id="78df7-119">Dizeleri bir giriş parametresi bir yapısında geçirir.</span><span class="sxs-lookup"><span data-stu-id="78df7-119">Passes strings in a structure that is an In parameter.</span></span>|[<span data-ttu-id="78df7-120">Yapılar</span><span class="sxs-lookup"><span data-stu-id="78df7-120">Structs</span></span>](http://msdn.microsoft.com/en-us/96a62265-dcf9-4608-bc0a-1f762ab9f48e)|  
|<span data-ttu-id="78df7-121">Başvuruya göre bir yapı **(char\*)**.</span><span class="sxs-lookup"><span data-stu-id="78df7-121">In a structure by reference **(char\*)**.</span></span>|<span data-ttu-id="78df7-122">Dizeleri giriş/çıkış parametresi bir yapısında geçirir.</span><span class="sxs-lookup"><span data-stu-id="78df7-122">Passes strings in a structure that is an In/Out parameter.</span></span> <span data-ttu-id="78df7-123">Yönetilmeyen işlev karakter arabellek için bir işaretçi bekler ve arabellek boyutu yapısı bir üyesidir.</span><span class="sxs-lookup"><span data-stu-id="78df7-123">The unmanaged function expects a pointer to a character buffer and the buffer size is a member of the structure.</span></span>|[<span data-ttu-id="78df7-124">Dizeler</span><span class="sxs-lookup"><span data-stu-id="78df7-124">Strings</span></span>](http://msdn.microsoft.com/en-us/be9e82a3-dc95-4aaa-9396-61b66e467e02)|  
|<span data-ttu-id="78df7-125">Başvuruya göre bir yapı **(char[])**.</span><span class="sxs-lookup"><span data-stu-id="78df7-125">In a structure by reference **(char[])**.</span></span>|<span data-ttu-id="78df7-126">Dizeleri giriş/çıkış parametresi bir yapısında geçirir.</span><span class="sxs-lookup"><span data-stu-id="78df7-126">Passes strings in a structure that is an In/Out parameter.</span></span> <span data-ttu-id="78df7-127">Yönetilmeyen işlevi bir katıştırılmış karakter arabellek bekliyor.</span><span class="sxs-lookup"><span data-stu-id="78df7-127">The unmanaged function expects an embedded character buffer.</span></span>|[<span data-ttu-id="78df7-128">Osınfo</span><span class="sxs-lookup"><span data-stu-id="78df7-128">OSInfo</span></span>](http://msdn.microsoft.com/en-us/69d89067-507b-41fe-859d-30bf3ff29455)|  
|<span data-ttu-id="78df7-129">Değere göre bir sınıftaki **(char\*)**.</span><span class="sxs-lookup"><span data-stu-id="78df7-129">In a class by value **(char\*)**.</span></span>|<span data-ttu-id="78df7-130">Dizeler (bir sınıf bir giriş/çıkış parametresine olan) bir sınıfta geçirir.</span><span class="sxs-lookup"><span data-stu-id="78df7-130">Passes strings in a class (a class is an In/Out parameter).</span></span> <span data-ttu-id="78df7-131">Yönetilmeyen işlev karakter arabellek için bir işaretçi bekliyor.</span><span class="sxs-lookup"><span data-stu-id="78df7-131">The unmanaged function expects a pointer to a character buffer.</span></span>|[<span data-ttu-id="78df7-132">OpenFileDlg</span><span class="sxs-lookup"><span data-stu-id="78df7-132">OpenFileDlg</span></span>](http://msdn.microsoft.com/en-us/b7dea792-cb92-4baf-ac7b-6a24803e6c75)|  
|<span data-ttu-id="78df7-133">Değere göre bir sınıftaki **(char[])**.</span><span class="sxs-lookup"><span data-stu-id="78df7-133">In a class by value **(char[])**.</span></span>|<span data-ttu-id="78df7-134">Dizeler (bir sınıf bir giriş/çıkış parametresine olan) bir sınıfta geçirir.</span><span class="sxs-lookup"><span data-stu-id="78df7-134">Passes strings in a class (a class is an In/Out parameter).</span></span> <span data-ttu-id="78df7-135">Yönetilmeyen işlevi bir katıştırılmış karakter arabellek bekliyor.</span><span class="sxs-lookup"><span data-stu-id="78df7-135">The unmanaged function expects an embedded character buffer.</span></span>|[<span data-ttu-id="78df7-136">Osınfo</span><span class="sxs-lookup"><span data-stu-id="78df7-136">OSInfo</span></span>](http://msdn.microsoft.com/en-us/69d89067-507b-41fe-859d-30bf3ff29455)|  
|<span data-ttu-id="78df7-137">Değere göre bir dizeler dizisi.</span><span class="sxs-lookup"><span data-stu-id="78df7-137">As an array of strings by value.</span></span>|<span data-ttu-id="78df7-138">Değeri tarafından geçirilen bir dizeler dizisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="78df7-138">Creates an array of strings that is passed by value.</span></span>|[<span data-ttu-id="78df7-139">Diziler</span><span class="sxs-lookup"><span data-stu-id="78df7-139">Arrays</span></span>](../../../docs/framework/interop/marshaling-different-types-of-arrays.md)|  
|<span data-ttu-id="78df7-140">Değere göre dizelerini içeren yapıları dizisi.</span><span class="sxs-lookup"><span data-stu-id="78df7-140">As an array of structures that contain strings by value.</span></span>|<span data-ttu-id="78df7-141">Yapıları dizisi oluşturan dizeler içeriyor ve dizi değere göre geçirilir.</span><span class="sxs-lookup"><span data-stu-id="78df7-141">Creates an array of structures that contain strings and the array is passed by value.</span></span>|[<span data-ttu-id="78df7-142">Diziler</span><span class="sxs-lookup"><span data-stu-id="78df7-142">Arrays</span></span>](../../../docs/framework/interop/marshaling-different-types-of-arrays.md)|  
  
## <a name="see-also"></a><span data-ttu-id="78df7-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="78df7-143">See Also</span></span>  
 [<span data-ttu-id="78df7-144">Platform Çağırma ile Veri Hazırlama</span><span class="sxs-lookup"><span data-stu-id="78df7-144">Marshaling Data with Platform Invoke</span></span>](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)  
 [<span data-ttu-id="78df7-145">Platform çağırma veri türleri</span><span class="sxs-lookup"><span data-stu-id="78df7-145">Platform Invoke Data Types</span></span>](http://msdn.microsoft.com/en-us/16014d9f-d6bd-481e-83f0-df11377c550f)  
 [<span data-ttu-id="78df7-146">Sınıflar, Yapılar ve Birleşimleri Hazırlama</span><span class="sxs-lookup"><span data-stu-id="78df7-146">Marshaling Classes, Structures, and Unions</span></span>](../../../docs/framework/interop/marshaling-classes-structures-and-unions.md)  
 [<span data-ttu-id="78df7-147">Türlerin dizileri sıralama</span><span class="sxs-lookup"><span data-stu-id="78df7-147">Marshaling Arrays of Types</span></span>](http://msdn.microsoft.com/en-us/049b1c1b-228f-4445-88ec-91bc7fd4b1e8)  
 [<span data-ttu-id="78df7-148">Çeşitli hazırlama örnekleri</span><span class="sxs-lookup"><span data-stu-id="78df7-148">Miscellaneous Marshaling Samples</span></span>](http://msdn.microsoft.com/en-us/a915c948-54e9-4d0f-a525-95a77fd8ed70)
