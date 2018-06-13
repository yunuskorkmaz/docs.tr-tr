---
title: Hata Ayıklama Genel Statik İşlevleri
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework debugging]
- debugging global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], debugging
ms.assetid: efc64414-77c3-48d0-881a-8594ed416aad
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2403d736d031aab52525fc12b5071e764a8bde1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406457"
---
# <a name="debugging-global-static-functions"></a><span data-ttu-id="dd6a8-102">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="dd6a8-102">Debugging Global Static Functions</span></span>
<span data-ttu-id="dd6a8-103">Bu bölümde, hata ayıklama API'si kullanan yönetilmeyen genel statik işlevler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dd6a8-103">This section describes the unmanaged global static functions that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dd6a8-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="dd6a8-104">In This Section</span></span>  
 [<span data-ttu-id="dd6a8-105">_EFN_GetManagedExcepStack İşlevi</span><span class="sxs-lookup"><span data-stu-id="dd6a8-105">_EFN_GetManagedExcepStack Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedexcepstack-function.md)  
 <span data-ttu-id="dd6a8-106">Yönetilen özel durum nesnesi adresi içinde yer alan yığın izleme dize sürümünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="dd6a8-106">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
 [<span data-ttu-id="dd6a8-107">_EFN_GetManagedObjectFieldInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="dd6a8-107">_EFN_GetManagedObjectFieldInfo Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectfieldinfo-function.md)  
 <span data-ttu-id="dd6a8-108">Uzaklık, bir alan ve alanın değerini, sağlanan nesne işaretçisi ve alan adını kullanarak bir nesne başından alır.</span><span class="sxs-lookup"><span data-stu-id="dd6a8-108">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
 [<span data-ttu-id="dd6a8-109">_EFN_GetManagedObjectName İşlevi</span><span class="sxs-lookup"><span data-stu-id="dd6a8-109">_EFN_GetManagedObjectName Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectname-function.md)  
 <span data-ttu-id="dd6a8-110">Sağlanan yönetilen nesne işaretçisi kullanılarak bir türün adını alır.</span><span class="sxs-lookup"><span data-stu-id="dd6a8-110">Gets the name of a type by using the provided managed object pointer.</span></span>  
  
 [<span data-ttu-id="dd6a8-111">_EFN_StackTrace İşlevi</span><span class="sxs-lookup"><span data-stu-id="dd6a8-111">_EFN_StackTrace Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-stacktrace-function.md)  
 <span data-ttu-id="dd6a8-112">Yönetilen yığın izlemesi metin gösterimini ve bir dizi sağlar `CONTEXT` kaydeder, bir yönetilmeyen ve yönetilen kod arasında her geçiş için.</span><span class="sxs-lookup"><span data-stu-id="dd6a8-112">Provides a text representation of a managed stack trace and an array of `CONTEXT` records, one for each transition between unmanaged and managed code.</span></span>  
  
 [<span data-ttu-id="dd6a8-113">CLRDataCreateInstance İşlevi</span><span class="sxs-lookup"><span data-stu-id="dd6a8-113">CLRDataCreateInstance Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatacreateinstance-function.md)  
 <span data-ttu-id="dd6a8-114">Belirtilen hedef işlem için belirtilen arabirimi nesnesi oluşturmak için ortak dil çalışma zamanı (CLR) veri erişim hizmeti tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="dd6a8-114">Called by the common language runtime (CLR) data access services to create the specified interface object for the specified target process.</span></span>  
  
 [<span data-ttu-id="dd6a8-115">PFN_CLRDataCreateInstance İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="dd6a8-115">PFN_CLRDataCreateInstance Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/debugging/pfn-clrdatacreateinstance-function-pointer.md)  
 <span data-ttu-id="dd6a8-116">Belirtilen hedef işlem için belirtilen arabirimi nesnesi oluşturmak için Sertifika Hizmetleri'ni erişim noktaları tarafından CLR veri adlı bir işlev.</span><span class="sxs-lookup"><span data-stu-id="dd6a8-116">Points to a function that is called by the CLR data access services to create the specified interface object for the specified target process.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="dd6a8-117">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="dd6a8-117">Related Sections</span></span>  
 [<span data-ttu-id="dd6a8-118">Hata Ayıklama Coclass’ları</span><span class="sxs-lookup"><span data-stu-id="dd6a8-118">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="dd6a8-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="dd6a8-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [<span data-ttu-id="dd6a8-120">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="dd6a8-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [<span data-ttu-id="dd6a8-121">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="dd6a8-121">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
