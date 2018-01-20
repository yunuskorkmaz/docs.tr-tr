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
ms.openlocfilehash: a4d53cd4072ab3f9ff52729f122c0a0ecab400df
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="marshaling-strings"></a><span data-ttu-id="ff405-102">Dizeleri Hazırlama</span><span class="sxs-lookup"><span data-stu-id="ff405-102">Marshaling Strings</span></span>
<span data-ttu-id="ff405-103">Platform çağırma bunları .NET Framework biçimden (Unicode) yönetilmeyen biçimi (ANSI), gerekirse dönüştürme kopyaları dizesi parametreleri.</span><span class="sxs-lookup"><span data-stu-id="ff405-103">Platform invoke copies string parameters, converting them from the .NET Framework format (Unicode) to the unmanaged format (ANSI), if needed.</span></span> <span data-ttu-id="ff405-104">Yönetilen dizeleri değişmez olduğundan, platform çağırma işlevi döndüğünde bunları yönetilmeyen bellekten yönetilen bellek kopyalamaz.</span><span class="sxs-lookup"><span data-stu-id="ff405-104">Because managed strings are immutable, platform invoke does not copy them back from unmanaged memory to managed memory when the function returns.</span></span>  
  
 <span data-ttu-id="ff405-105">Aşağıdaki tabloda dizeleri sıralama seçeneklerini listeler, bunların kullanım açıklar ve karşılık gelen .NET Framework örnek bağlantı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ff405-105">The following table lists marshaling options for strings, describes their usage, and provides a link to the corresponding .NET Framework sample.</span></span>  
  
|<span data-ttu-id="ff405-106">Dize</span><span class="sxs-lookup"><span data-stu-id="ff405-106">String</span></span>|<span data-ttu-id="ff405-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ff405-107">Description</span></span>|<span data-ttu-id="ff405-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="ff405-108">Sample</span></span>|  
|------------|-----------------|------------|  
|<span data-ttu-id="ff405-109">Değer tarafından.</span><span class="sxs-lookup"><span data-stu-id="ff405-109">By value.</span></span>|<span data-ttu-id="ff405-110">Dizeleri parametreleri olduğu gibi geçirir.</span><span class="sxs-lookup"><span data-stu-id="ff405-110">Passes strings as In parameters.</span></span>|[<span data-ttu-id="ff405-111">MsgBox</span><span class="sxs-lookup"><span data-stu-id="ff405-111">MsgBox</span></span>](../../../docs/framework/interop/msgbox-sample.md)|  
|<span data-ttu-id="ff405-112">Sonuç olarak.</span><span class="sxs-lookup"><span data-stu-id="ff405-112">As result.</span></span>|<span data-ttu-id="ff405-113">Yönetilmeyen kod dizelerden döndürür.</span><span class="sxs-lookup"><span data-stu-id="ff405-113">Returns strings from unmanaged code.</span></span>|[<span data-ttu-id="ff405-114">Dizeler</span><span class="sxs-lookup"><span data-stu-id="ff405-114">Strings</span></span>](http://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02)|  
|<span data-ttu-id="ff405-115">Başvuruya göre.</span><span class="sxs-lookup"><span data-stu-id="ff405-115">By reference.</span></span>|<span data-ttu-id="ff405-116">Dizeleri olarak giriş/çıkış kullanarak parametrelerini geçirir <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="ff405-116">Passes strings as In/Out parameters using <xref:System.Text.StringBuilder>.</span></span>|[<span data-ttu-id="ff405-117">Arabellekler</span><span class="sxs-lookup"><span data-stu-id="ff405-117">Buffers</span></span>](http://msdn.microsoft.com/library/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5)|  
|<span data-ttu-id="ff405-118">Değere göre bir yapısında.</span><span class="sxs-lookup"><span data-stu-id="ff405-118">In a structure by value.</span></span>|<span data-ttu-id="ff405-119">Dizeleri bir giriş parametresi bir yapısında geçirir.</span><span class="sxs-lookup"><span data-stu-id="ff405-119">Passes strings in a structure that is an In parameter.</span></span>|[<span data-ttu-id="ff405-120">Yapılar</span><span class="sxs-lookup"><span data-stu-id="ff405-120">Structs</span></span>](http://msdn.microsoft.com/library/96a62265-dcf9-4608-bc0a-1f762ab9f48e)|  
|<span data-ttu-id="ff405-121">Başvuruya göre bir yapı **(char\*)**.</span><span class="sxs-lookup"><span data-stu-id="ff405-121">In a structure by reference **(char\*)**.</span></span>|<span data-ttu-id="ff405-122">Dizeleri giriş/çıkış parametresi bir yapısında geçirir.</span><span class="sxs-lookup"><span data-stu-id="ff405-122">Passes strings in a structure that is an In/Out parameter.</span></span> <span data-ttu-id="ff405-123">Yönetilmeyen işlev karakter arabellek için bir işaretçi bekler ve arabellek boyutu yapısı bir üyesidir.</span><span class="sxs-lookup"><span data-stu-id="ff405-123">The unmanaged function expects a pointer to a character buffer and the buffer size is a member of the structure.</span></span>|[<span data-ttu-id="ff405-124">Dizeler</span><span class="sxs-lookup"><span data-stu-id="ff405-124">Strings</span></span>](http://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02)|  
|<span data-ttu-id="ff405-125">Başvuruya göre bir yapı **(char[])**.</span><span class="sxs-lookup"><span data-stu-id="ff405-125">In a structure by reference **(char[])**.</span></span>|<span data-ttu-id="ff405-126">Dizeleri giriş/çıkış parametresi bir yapısında geçirir.</span><span class="sxs-lookup"><span data-stu-id="ff405-126">Passes strings in a structure that is an In/Out parameter.</span></span> <span data-ttu-id="ff405-127">Yönetilmeyen işlevi bir katıştırılmış karakter arabellek bekliyor.</span><span class="sxs-lookup"><span data-stu-id="ff405-127">The unmanaged function expects an embedded character buffer.</span></span>|[<span data-ttu-id="ff405-128">OSInfo</span><span class="sxs-lookup"><span data-stu-id="ff405-128">OSInfo</span></span>](http://msdn.microsoft.com/library/69d89067-507b-41fe-859d-30bf3ff29455)|  
|<span data-ttu-id="ff405-129">Değere göre bir sınıftaki **(char\*)**.</span><span class="sxs-lookup"><span data-stu-id="ff405-129">In a class by value **(char\*)**.</span></span>|<span data-ttu-id="ff405-130">Dizeler (bir sınıf bir giriş/çıkış parametresine olan) bir sınıfta geçirir.</span><span class="sxs-lookup"><span data-stu-id="ff405-130">Passes strings in a class (a class is an In/Out parameter).</span></span> <span data-ttu-id="ff405-131">Yönetilmeyen işlev karakter arabellek için bir işaretçi bekliyor.</span><span class="sxs-lookup"><span data-stu-id="ff405-131">The unmanaged function expects a pointer to a character buffer.</span></span>|[<span data-ttu-id="ff405-132">OpenFileDlg</span><span class="sxs-lookup"><span data-stu-id="ff405-132">OpenFileDlg</span></span>](http://msdn.microsoft.com/library/b7dea792-cb92-4baf-ac7b-6a24803e6c75)|  
|<span data-ttu-id="ff405-133">Değere göre bir sınıftaki **(char[])**.</span><span class="sxs-lookup"><span data-stu-id="ff405-133">In a class by value **(char[])**.</span></span>|<span data-ttu-id="ff405-134">Dizeler (bir sınıf bir giriş/çıkış parametresine olan) bir sınıfta geçirir.</span><span class="sxs-lookup"><span data-stu-id="ff405-134">Passes strings in a class (a class is an In/Out parameter).</span></span> <span data-ttu-id="ff405-135">Yönetilmeyen işlevi bir katıştırılmış karakter arabellek bekliyor.</span><span class="sxs-lookup"><span data-stu-id="ff405-135">The unmanaged function expects an embedded character buffer.</span></span>|[<span data-ttu-id="ff405-136">OSInfo</span><span class="sxs-lookup"><span data-stu-id="ff405-136">OSInfo</span></span>](http://msdn.microsoft.com/library/69d89067-507b-41fe-859d-30bf3ff29455)|  
|<span data-ttu-id="ff405-137">Değere göre bir dizeler dizisi.</span><span class="sxs-lookup"><span data-stu-id="ff405-137">As an array of strings by value.</span></span>|<span data-ttu-id="ff405-138">Değeri tarafından geçirilen bir dizeler dizisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ff405-138">Creates an array of strings that is passed by value.</span></span>|[<span data-ttu-id="ff405-139">Diziler</span><span class="sxs-lookup"><span data-stu-id="ff405-139">Arrays</span></span>](../../../docs/framework/interop/marshaling-different-types-of-arrays.md)|  
|<span data-ttu-id="ff405-140">Değere göre dizelerini içeren yapıları dizisi.</span><span class="sxs-lookup"><span data-stu-id="ff405-140">As an array of structures that contain strings by value.</span></span>|<span data-ttu-id="ff405-141">Yapıları dizisi oluşturan dizeler içeriyor ve dizi değere göre geçirilir.</span><span class="sxs-lookup"><span data-stu-id="ff405-141">Creates an array of structures that contain strings and the array is passed by value.</span></span>|[<span data-ttu-id="ff405-142">Diziler</span><span class="sxs-lookup"><span data-stu-id="ff405-142">Arrays</span></span>](../../../docs/framework/interop/marshaling-different-types-of-arrays.md)|  
  
## <a name="see-also"></a><span data-ttu-id="ff405-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ff405-143">See Also</span></span>  
 [<span data-ttu-id="ff405-144">Platform Çağırma ile Veri Hazırlama</span><span class="sxs-lookup"><span data-stu-id="ff405-144">Marshaling Data with Platform Invoke</span></span>](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)  
 [<span data-ttu-id="ff405-145">Platform çağırma veri türleri</span><span class="sxs-lookup"><span data-stu-id="ff405-145">Platform Invoke Data Types</span></span>](http://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f)  
 [<span data-ttu-id="ff405-146">Sınıflar, Yapılar ve Birleşimleri Hazırlama</span><span class="sxs-lookup"><span data-stu-id="ff405-146">Marshaling Classes, Structures, and Unions</span></span>](../../../docs/framework/interop/marshaling-classes-structures-and-unions.md)  
 [<span data-ttu-id="ff405-147">Türlerin dizileri sıralama</span><span class="sxs-lookup"><span data-stu-id="ff405-147">Marshaling Arrays of Types</span></span>](http://msdn.microsoft.com/library/049b1c1b-228f-4445-88ec-91bc7fd4b1e8)  
 [<span data-ttu-id="ff405-148">Çeşitli hazırlama örnekleri</span><span class="sxs-lookup"><span data-stu-id="ff405-148">Miscellaneous Marshaling Samples</span></span>](http://msdn.microsoft.com/library/a915c948-54e9-4d0f-a525-95a77fd8ed70)
