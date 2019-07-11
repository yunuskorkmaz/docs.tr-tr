---
title: PFN_CLRDataCreateInstance İşlev İşaretçisi
ms.date: 03/30/2017
api_name:
- PFN_CLRDataCreateInstance
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- PFN_CLRDataCreateInstance
helpviewer_keywords:
- PFN_CLRDataCreateInstance function pointer [.NET Framework debugging]
ms.assetid: 5c66ac57-d751-4de5-af9f-26ceb949af8b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 81fcc99a739d5e673d1d01d5efb801ba4930bdee
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752553"
---
# <a name="pfnclrdatacreateinstance-function-pointer"></a><span data-ttu-id="6eeeb-102">PFN_CLRDataCreateInstance İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="6eeeb-102">PFN_CLRDataCreateInstance Function Pointer</span></span>
<span data-ttu-id="6eeeb-103">Belirtilen hedef öğe için bir arabirimi nesne oluşturan bir işlev işaret eder.</span><span class="sxs-lookup"><span data-stu-id="6eeeb-103">Points to a function that creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6eeeb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6eeeb-104">Syntax</span></span>  
  
```cpp  
typedef HRESULT (STDAPICALLTYPE* PFN_CLRDataCreateInstance) (  
    [in]  REFIID           iid,  
    [in]  ICLRDataTarget  *target,  
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6eeeb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6eeeb-105">Parameters</span></span>  
 `iid`  
 <span data-ttu-id="6eeeb-106">[in] Oluşturulacak arabirimi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="6eeeb-106">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="6eeeb-107">[in] Bir kullanıcı olarak uygulanan bir işaretçiye [Iclrdatatarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) arabirimi nesnesi oluşturulacağı hedef öğeyi temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="6eeeb-107">[in] A pointer to a user-implemented [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="6eeeb-108">[out] Döndürülen arabirim nesnesinin adresine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6eeeb-108">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6eeeb-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6eeeb-109">Remarks</span></span>  
 <span data-ttu-id="6eeeb-110">`ICLRDataTarget` Nesne, hata ayıklama uygulamanın yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="6eeeb-110">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="6eeeb-111">Uygulama, temsil ettiği hedef öğesinin türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="6eeeb-111">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="6eeeb-112">Hedef öğe, bir işlem, bellek dökümü, uzak makine vb. olabilir.</span><span class="sxs-lookup"><span data-stu-id="6eeeb-112">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6eeeb-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6eeeb-113">Requirements</span></span>  
 <span data-ttu-id="6eeeb-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6eeeb-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6eeeb-115">**Üst bilgi:** ClrData.idl</span><span class="sxs-lookup"><span data-stu-id="6eeeb-115">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="6eeeb-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6eeeb-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6eeeb-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6eeeb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6eeeb-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6eeeb-118">See also</span></span>

- [<span data-ttu-id="6eeeb-119">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="6eeeb-119">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
