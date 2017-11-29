---
title: "Hata Ayıklama Genel Statik İşlevleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- global static functions [.NET Framework debugging]
- debugging global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], debugging
ms.assetid: efc64414-77c3-48d0-881a-8594ed416aad
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ad5d3ef689a251ea4b154afc5d1bfb387388ddb3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="debugging-global-static-functions"></a><span data-ttu-id="21dff-102">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="21dff-102">Debugging Global Static Functions</span></span>
<span data-ttu-id="21dff-103">Bu bölümde, hata ayıklama API'si kullanan yönetilmeyen genel statik işlevler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="21dff-103">This section describes the unmanaged global static functions that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="21dff-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="21dff-104">In This Section</span></span>  
 [<span data-ttu-id="21dff-105">_EFN_GetManagedExcepStack işlevi</span><span class="sxs-lookup"><span data-stu-id="21dff-105">_EFN_GetManagedExcepStack Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedexcepstack-function.md)  
 <span data-ttu-id="21dff-106">Yönetilen özel durum nesnesi adresi içinde yer alan yığın izleme dize sürümünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="21dff-106">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
 [<span data-ttu-id="21dff-107">_Efn_getmanagedobjectfieldınfo işlevi</span><span class="sxs-lookup"><span data-stu-id="21dff-107">_EFN_GetManagedObjectFieldInfo Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectfieldinfo-function.md)  
 <span data-ttu-id="21dff-108">Uzaklık, bir alan ve alanın değerini, sağlanan nesne işaretçisi ve alan adını kullanarak bir nesne başından alır.</span><span class="sxs-lookup"><span data-stu-id="21dff-108">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
 [<span data-ttu-id="21dff-109">_EFN_GetManagedObjectName işlevi</span><span class="sxs-lookup"><span data-stu-id="21dff-109">_EFN_GetManagedObjectName Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectname-function.md)  
 <span data-ttu-id="21dff-110">Sağlanan yönetilen nesne işaretçisi kullanılarak bir türün adını alır.</span><span class="sxs-lookup"><span data-stu-id="21dff-110">Gets the name of a type by using the provided managed object pointer.</span></span>  
  
 [<span data-ttu-id="21dff-111">_EFN_StackTrace işlevi</span><span class="sxs-lookup"><span data-stu-id="21dff-111">_EFN_StackTrace Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-stacktrace-function.md)  
 <span data-ttu-id="21dff-112">Yönetilen yığın izlemesi metin gösterimini ve bir dizi sağlar `CONTEXT` kaydeder, bir yönetilmeyen ve yönetilen kod arasında her geçiş için.</span><span class="sxs-lookup"><span data-stu-id="21dff-112">Provides a text representation of a managed stack trace and an array of `CONTEXT` records, one for each transition between unmanaged and managed code.</span></span>  
  
 [<span data-ttu-id="21dff-113">Clrdatacreateınstance işlevi</span><span class="sxs-lookup"><span data-stu-id="21dff-113">CLRDataCreateInstance Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatacreateinstance-function.md)  
 <span data-ttu-id="21dff-114">Belirtilen hedef işlem için belirtilen arabirimi nesnesi oluşturmak için ortak dil çalışma zamanı (CLR) veri erişim hizmeti tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="21dff-114">Called by the common language runtime (CLR) data access services to create the specified interface object for the specified target process.</span></span>  
  
 [<span data-ttu-id="21dff-115">Pfn_clrdatacreateınstance işlev işaretçisi</span><span class="sxs-lookup"><span data-stu-id="21dff-115">PFN_CLRDataCreateInstance Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/debugging/pfn-clrdatacreateinstance-function-pointer.md)  
 <span data-ttu-id="21dff-116">Belirtilen hedef işlem için belirtilen arabirimi nesnesi oluşturmak için Sertifika Hizmetleri'ni erişim noktaları tarafından CLR veri adlı bir işlev.</span><span class="sxs-lookup"><span data-stu-id="21dff-116">Points to a function that is called by the CLR data access services to create the specified interface object for the specified target process.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="21dff-117">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="21dff-117">Related Sections</span></span>  
 [<span data-ttu-id="21dff-118">Hata ayıklama coclass'ları</span><span class="sxs-lookup"><span data-stu-id="21dff-118">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="21dff-119">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="21dff-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [<span data-ttu-id="21dff-120">Hata ayıklama numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="21dff-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [<span data-ttu-id="21dff-121">Hata ayıklama yapıları</span><span class="sxs-lookup"><span data-stu-id="21dff-121">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
