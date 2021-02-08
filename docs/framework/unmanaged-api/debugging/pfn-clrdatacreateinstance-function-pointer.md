---
description: 'Hakkında daha fazla bilgi edinin: PFN_CLRDataCreateInstance Işlev Işaretçisi'
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
ms.openlocfilehash: fc048f840084eff0270944d3190ccbb153bf22d8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800636"
---
# <a name="pfn_clrdatacreateinstance-function-pointer"></a><span data-ttu-id="6a82e-103">PFN_CLRDataCreateInstance İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="6a82e-103">PFN_CLRDataCreateInstance Function Pointer</span></span>

<span data-ttu-id="6a82e-104">Belirtilen hedef öğe için arabirim nesnesi oluşturan bir işleve işaret eder.</span><span class="sxs-lookup"><span data-stu-id="6a82e-104">Points to a function that creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a82e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a82e-105">Syntax</span></span>  
  
```cpp  
typedef HRESULT (STDAPICALLTYPE* PFN_CLRDataCreateInstance) (  
    [in]  REFIID           iid,  
    [in]  ICLRDataTarget  *target,  
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a82e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6a82e-106">Parameters</span></span>  

 `iid`  
 <span data-ttu-id="6a82e-107">'ndaki Oluşturulacak arabirimin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="6a82e-107">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="6a82e-108">'ndaki Arabirim nesnesinin oluşturulacağı hedef öğeyi temsil eden, Kullanıcı tarafından uygulanan [ICLRDataTarget](iclrdatatarget-interface.md) nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6a82e-108">[in] A pointer to a user-implemented [ICLRDataTarget](iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="6a82e-109">dışı Döndürülen arabirim nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6a82e-109">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a82e-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6a82e-110">Remarks</span></span>  

 <span data-ttu-id="6a82e-111">`ICLRDataTarget`Nesnesi, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="6a82e-111">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="6a82e-112">Uygulama, temsil edilen hedef öğe türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="6a82e-112">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="6a82e-113">Hedef öğe bir işlem, bellek dökümü, uzak makine vb. olabilir.</span><span class="sxs-lookup"><span data-stu-id="6a82e-113">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a82e-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6a82e-114">Requirements</span></span>  

 <span data-ttu-id="6a82e-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a82e-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a82e-116">**Üst bilgi:** ClrData. IDL</span><span class="sxs-lookup"><span data-stu-id="6a82e-116">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="6a82e-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6a82e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a82e-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a82e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a82e-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a82e-119">See also</span></span>

- [<span data-ttu-id="6a82e-120">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="6a82e-120">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
