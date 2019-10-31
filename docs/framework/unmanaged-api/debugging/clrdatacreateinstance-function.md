---
title: CLRDataCreateInstance İşlevi
ms.date: 03/30/2017
api_name:
- CLRDataCreateInstance
api_location:
- mscordbi.dll
- mscordacwks.dll
api_type:
- COM
f1_keywords:
- CLRDataCreateInstance
helpviewer_keywords:
- CLRDataCreateInstance function [.NET Framework debugging]
ms.assetid: 440bad90-5a88-45e7-9157-4596801d8d19
topic_type:
- apiref
ms.openlocfilehash: 71836108dbd0ce01a64b4d9ac773c28d385dfd7c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099683"
---
# <a name="clrdatacreateinstance-function"></a><span data-ttu-id="5d77b-102">CLRDataCreateInstance İşlevi</span><span class="sxs-lookup"><span data-stu-id="5d77b-102">CLRDataCreateInstance Function</span></span>
<span data-ttu-id="5d77b-103">Belirtilen hedef öğe için bir arabirim nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5d77b-103">Creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d77b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5d77b-104">Syntax</span></span>  
  
```cpp  
HRESULT CLRDataCreateInstance (  
    [in]  REFIID           iid,   
    [in]  ICLRDataTarget  *target,   
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d77b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5d77b-105">Parameters</span></span>  
 `iid`  
 <span data-ttu-id="5d77b-106">'ndaki Oluşturulacak arabirimin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="5d77b-106">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="5d77b-107">'ndaki Arabirim nesnesinin oluşturulacağı hedef öğeyi temsil eden, Kullanıcı tarafından uygulanan [ICLRDataTarget](iclrdatatarget-interface.md) nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5d77b-107">[in] A pointer to a user-implemented [ICLRDataTarget](iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="5d77b-108">dışı Döndürülen arabirim nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5d77b-108">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d77b-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5d77b-109">Remarks</span></span>  
 <span data-ttu-id="5d77b-110">`ICLRDataTarget` nesnesi, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="5d77b-110">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="5d77b-111">Uygulama, temsil edilen hedef öğe türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="5d77b-111">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="5d77b-112">Hedef öğe bir işlem, bellek dökümü, uzak makine vb. olabilir.</span><span class="sxs-lookup"><span data-stu-id="5d77b-112">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d77b-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5d77b-113">Requirements</span></span>  
 <span data-ttu-id="5d77b-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d77b-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d77b-115">**Üst bilgi:** ClrData. IDL</span><span class="sxs-lookup"><span data-stu-id="5d77b-115">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="5d77b-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5d77b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d77b-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d77b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d77b-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d77b-118">See also</span></span>

- [<span data-ttu-id="5d77b-119">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="5d77b-119">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
