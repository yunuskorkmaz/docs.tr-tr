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
ms.openlocfilehash: 34aae3cd913465bc3167d6c5eee9873d212fa4ac
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420701"
---
# <a name="pfn_clrdatacreateinstance-function-pointer"></a><span data-ttu-id="b5aa2-102">PFN_CLRDataCreateInstance İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="b5aa2-102">PFN_CLRDataCreateInstance Function Pointer</span></span>
<span data-ttu-id="b5aa2-103">Belirtilen hedef öğe için arabirim nesnesi oluşturan bir işleve işaret eder.</span><span class="sxs-lookup"><span data-stu-id="b5aa2-103">Points to a function that creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5aa2-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b5aa2-104">Syntax</span></span>  
  
```cpp  
typedef HRESULT (STDAPICALLTYPE* PFN_CLRDataCreateInstance) (  
    [in]  REFIID           iid,  
    [in]  ICLRDataTarget  *target,  
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5aa2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b5aa2-105">Parameters</span></span>  
 `iid`  
 <span data-ttu-id="b5aa2-106">'ndaki Oluşturulacak arabirimin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="b5aa2-106">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="b5aa2-107">'ndaki Arabirim nesnesinin oluşturulacağı hedef öğeyi temsil eden, Kullanıcı tarafından uygulanan [ICLRDataTarget](iclrdatatarget-interface.md) nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b5aa2-107">[in] A pointer to a user-implemented [ICLRDataTarget](iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="b5aa2-108">dışı Döndürülen arabirim nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b5aa2-108">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5aa2-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b5aa2-109">Remarks</span></span>  
 <span data-ttu-id="b5aa2-110">`ICLRDataTarget`Nesnesi, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b5aa2-110">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="b5aa2-111">Uygulama, temsil edilen hedef öğe türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b5aa2-111">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="b5aa2-112">Hedef öğe bir işlem, bellek dökümü, uzak makine vb. olabilir.</span><span class="sxs-lookup"><span data-stu-id="b5aa2-112">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5aa2-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b5aa2-113">Requirements</span></span>  
 <span data-ttu-id="b5aa2-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5aa2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5aa2-115">**Üst bilgi:** ClrData. IDL</span><span class="sxs-lookup"><span data-stu-id="b5aa2-115">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="b5aa2-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b5aa2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5aa2-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5aa2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5aa2-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5aa2-118">See also</span></span>

- [<span data-ttu-id="b5aa2-119">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="b5aa2-119">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
