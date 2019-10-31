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
ms.openlocfilehash: 426a8acf2e9319725cf592db00dc97c8960bca4f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139163"
---
# <a name="pfn_clrdatacreateinstance-function-pointer"></a><span data-ttu-id="3dcd4-102">PFN_CLRDataCreateInstance İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="3dcd4-102">PFN_CLRDataCreateInstance Function Pointer</span></span>
<span data-ttu-id="3dcd4-103">Belirtilen hedef öğe için arabirim nesnesi oluşturan bir işleve işaret eder.</span><span class="sxs-lookup"><span data-stu-id="3dcd4-103">Points to a function that creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dcd4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3dcd4-104">Syntax</span></span>  
  
```cpp  
typedef HRESULT (STDAPICALLTYPE* PFN_CLRDataCreateInstance) (  
    [in]  REFIID           iid,  
    [in]  ICLRDataTarget  *target,  
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3dcd4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3dcd4-105">Parameters</span></span>  
 `iid`  
 <span data-ttu-id="3dcd4-106">'ndaki Oluşturulacak arabirimin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="3dcd4-106">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="3dcd4-107">'ndaki Arabirim nesnesinin oluşturulacağı hedef öğeyi temsil eden, Kullanıcı tarafından uygulanan [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3dcd4-107">[in] A pointer to a user-implemented [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="3dcd4-108">dışı Döndürülen arabirim nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3dcd4-108">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3dcd4-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3dcd4-109">Remarks</span></span>  
 <span data-ttu-id="3dcd4-110">`ICLRDataTarget` nesnesi, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="3dcd4-110">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="3dcd4-111">Uygulama, temsil edilen hedef öğe türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3dcd4-111">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="3dcd4-112">Hedef öğe bir işlem, bellek dökümü, uzak makine vb. olabilir.</span><span class="sxs-lookup"><span data-stu-id="3dcd4-112">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3dcd4-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3dcd4-113">Requirements</span></span>  
 <span data-ttu-id="3dcd4-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3dcd4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3dcd4-115">**Üst bilgi:** ClrData. IDL</span><span class="sxs-lookup"><span data-stu-id="3dcd4-115">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="3dcd4-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3dcd4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3dcd4-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3dcd4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dcd4-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3dcd4-118">See also</span></span>

- [<span data-ttu-id="3dcd4-119">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="3dcd4-119">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
