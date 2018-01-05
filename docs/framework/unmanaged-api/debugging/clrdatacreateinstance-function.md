---
title: "CLRDataCreateInstance İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CLRDataCreateInstance
api_location:
- mscordbi.dll
- mscordacwks.dll
api_type: COM
f1_keywords: CLRDataCreateInstance
helpviewer_keywords: CLRDataCreateInstance function [.NET Framework debugging]
ms.assetid: 440bad90-5a88-45e7-9157-4596801d8d19
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0740e80732e03ac6c1e7cf974d258113a181ea9d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="clrdatacreateinstance-function"></a><span data-ttu-id="04daf-102">CLRDataCreateInstance İşlevi</span><span class="sxs-lookup"><span data-stu-id="04daf-102">CLRDataCreateInstance Function</span></span>
<span data-ttu-id="04daf-103">Belirtilen hedef öğesi için bir arabirimi nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="04daf-103">Creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04daf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="04daf-104">Syntax</span></span>  
  
```  
HRESULT CLRDataCreateInstance (  
    [in]  REFIID           iid,   
    [in]  ICLRDataTarget  *target,   
    [out] void           **iface  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="04daf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="04daf-105">Parameters</span></span>  
 `iid`  
 <span data-ttu-id="04daf-106">[in] Arabirim örneğinin oluşturulması için tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="04daf-106">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="04daf-107">[in] Kullanıcı uygulanan bir işaretçi [Iclrdatatarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) arabirimi nesnesi oluşturulacağı hedef öğeyi temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="04daf-107">[in] A pointer to a user-implemented [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="04daf-108">[out] Döndürülen arabirimi nesnesi adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="04daf-108">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04daf-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="04daf-109">Remarks</span></span>  
 <span data-ttu-id="04daf-110">`ICLRDataTarget` Nesnesi, hata ayıklama uygulama yazıcı tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="04daf-110">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="04daf-111">Uygulama temsil ettiği hedef öğesi türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="04daf-111">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="04daf-112">Hedef öğesi, bir işlem, bellek dökümü, uzak makine vb. olabilir.</span><span class="sxs-lookup"><span data-stu-id="04daf-112">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04daf-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="04daf-113">Requirements</span></span>  
 <span data-ttu-id="04daf-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04daf-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04daf-115">**Başlık:** ClrData.idl</span><span class="sxs-lookup"><span data-stu-id="04daf-115">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="04daf-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04daf-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04daf-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04daf-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04daf-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="04daf-118">See Also</span></span>  
 [<span data-ttu-id="04daf-119">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="04daf-119">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
