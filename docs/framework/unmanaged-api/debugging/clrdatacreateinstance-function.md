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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 73a4a8a2fc737bbf4b49ca859f0549ca7efd54a2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701287"
---
# <a name="clrdatacreateinstance-function"></a><span data-ttu-id="2a8ba-102">CLRDataCreateInstance İşlevi</span><span class="sxs-lookup"><span data-stu-id="2a8ba-102">CLRDataCreateInstance Function</span></span>
<span data-ttu-id="2a8ba-103">Belirtilen hedef öğe için bir arabirimi nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2a8ba-103">Creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a8ba-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2a8ba-104">Syntax</span></span>  
  
```  
HRESULT CLRDataCreateInstance (  
    [in]  REFIID           iid,   
    [in]  ICLRDataTarget  *target,   
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a8ba-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2a8ba-105">Parameters</span></span>  
 `iid`  
 <span data-ttu-id="2a8ba-106">[in] Oluşturulacak arabirimi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="2a8ba-106">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="2a8ba-107">[in] Bir kullanıcı olarak uygulanan bir işaretçiye [Iclrdatatarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) arabirimi nesnesi oluşturulacağı hedef öğeyi temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="2a8ba-107">[in] A pointer to a user-implemented [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="2a8ba-108">[out] Döndürülen arabirim nesnesinin adresine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2a8ba-108">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a8ba-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2a8ba-109">Remarks</span></span>  
 <span data-ttu-id="2a8ba-110">`ICLRDataTarget` Nesne, hata ayıklama uygulamanın yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="2a8ba-110">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="2a8ba-111">Uygulama, temsil ettiği hedef öğesinin türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="2a8ba-111">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="2a8ba-112">Hedef öğe, bir işlem, bellek dökümü, uzak makine vb. olabilir.</span><span class="sxs-lookup"><span data-stu-id="2a8ba-112">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a8ba-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2a8ba-113">Requirements</span></span>  
 <span data-ttu-id="2a8ba-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a8ba-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a8ba-115">**Üst bilgi:** ClrData.idl</span><span class="sxs-lookup"><span data-stu-id="2a8ba-115">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="2a8ba-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a8ba-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a8ba-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a8ba-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a8ba-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a8ba-118">See also</span></span>

- [<span data-ttu-id="2a8ba-119">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="2a8ba-119">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
