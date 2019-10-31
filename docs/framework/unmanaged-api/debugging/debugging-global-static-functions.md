---
title: Hata Ayıklama Genel Statik İşlevleri
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework debugging]
- debugging global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], debugging
ms.assetid: efc64414-77c3-48d0-881a-8594ed416aad
ms.openlocfilehash: 965724c1e937fa62f05c33b0dcf8a5c8b9e1b029
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124311"
---
# <a name="debugging-global-static-functions"></a><span data-ttu-id="fbf3c-102">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="fbf3c-102">Debugging Global Static Functions</span></span>
<span data-ttu-id="fbf3c-103">Bu bölümde, hata ayıklama API 'sinin kullandığı yönetilmeyen genel statik işlevler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fbf3c-103">This section describes the unmanaged global static functions that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fbf3c-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="fbf3c-104">In This Section</span></span>  
 [<span data-ttu-id="fbf3c-105">_EFN_GetManagedExcepStack İşlevi</span><span class="sxs-lookup"><span data-stu-id="fbf3c-105">_EFN_GetManagedExcepStack Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedexcepstack-function.md)  
 <span data-ttu-id="fbf3c-106">Yönetilen bir özel durum nesne adresi verildiğinde, içinde bulunan yığın izlemenin bir dize sürümünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="fbf3c-106">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
 [<span data-ttu-id="fbf3c-107">_EFN_GetManagedObjectFieldInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="fbf3c-107">_EFN_GetManagedObjectFieldInfo Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectfieldinfo-function.md)  
 <span data-ttu-id="fbf3c-108">Belirtilen nesne işaretçisini ve alan adını kullanarak bir nesnenin başından bir alana ve alanın değerine kadar olan sapmayı alır.</span><span class="sxs-lookup"><span data-stu-id="fbf3c-108">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
 [<span data-ttu-id="fbf3c-109">_EFN_GetManagedObjectName İşlevi</span><span class="sxs-lookup"><span data-stu-id="fbf3c-109">_EFN_GetManagedObjectName Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectname-function.md)  
 <span data-ttu-id="fbf3c-110">Belirtilen yönetilen nesne işaretçisini kullanarak bir türün adını alır.</span><span class="sxs-lookup"><span data-stu-id="fbf3c-110">Gets the name of a type by using the provided managed object pointer.</span></span>  
  
 [<span data-ttu-id="fbf3c-111">_EFN_StackTrace İşlevi</span><span class="sxs-lookup"><span data-stu-id="fbf3c-111">_EFN_StackTrace Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-stacktrace-function.md)  
 <span data-ttu-id="fbf3c-112">Yönetilmeyen ve yönetilen kod arasındaki her geçiş için bir yönetilen yığın izlemenin ve bir dizi `CONTEXT` kaydın metin gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="fbf3c-112">Provides a text representation of a managed stack trace and an array of `CONTEXT` records, one for each transition between unmanaged and managed code.</span></span>  
  
 [<span data-ttu-id="fbf3c-113">CLRDataCreateInstance İşlevi</span><span class="sxs-lookup"><span data-stu-id="fbf3c-113">CLRDataCreateInstance Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatacreateinstance-function.md)  
 <span data-ttu-id="fbf3c-114">Belirtilen hedef işlem için belirtilen arabirim nesnesini oluşturmak için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="fbf3c-114">Called by the common language runtime (CLR) data access services to create the specified interface object for the specified target process.</span></span>  
  
 [<span data-ttu-id="fbf3c-115">PFN_CLRDataCreateInstance İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="fbf3c-115">PFN_CLRDataCreateInstance Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/debugging/pfn-clrdatacreateinstance-function-pointer.md)  
 <span data-ttu-id="fbf3c-116">Belirtilen hedef işlem için belirtilen arabirim nesnesini oluşturmak üzere CLR veri erişim Hizmetleri tarafından çağrılan bir işleve işaret eder.</span><span class="sxs-lookup"><span data-stu-id="fbf3c-116">Points to a function that is called by the CLR data access services to create the specified interface object for the specified target process.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="fbf3c-117">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="fbf3c-117">Related Sections</span></span>  
 [<span data-ttu-id="fbf3c-118">Hata Ayıklama Coclass’ları</span><span class="sxs-lookup"><span data-stu-id="fbf3c-118">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="fbf3c-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fbf3c-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [<span data-ttu-id="fbf3c-120">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="fbf3c-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [<span data-ttu-id="fbf3c-121">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="fbf3c-121">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
