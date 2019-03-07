---
title: ICLRDataTarget2::FreeVirtual Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2.FreeVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2::FreeVirtual
helpviewer_keywords:
- ICLRDataTarget::FreeVirtual method [.NET Framework debugging]
- FreeVirtual method [.NET Framework debugging]
ms.assetid: 26fb69f8-1467-4711-bd24-cb117c63938f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d8d2f6a716c65596c781015bad0dea52705611a0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487175"
---
# <a name="iclrdatatarget2freevirtual-method"></a><span data-ttu-id="b2738-102">ICLRDataTarget2::FreeVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2738-102">ICLRDataTarget2::FreeVirtual Method</span></span>
<span data-ttu-id="b2738-103">Ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri hedef işlemin adres alanında önceden ayrılmış olan belleği boşaltmak için tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="b2738-103">Called by the common language runtime (CLR) data access services to free memory that was previously allocated in the address space of the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2738-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b2738-104">Syntax</span></span>  
  
```  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2738-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b2738-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="b2738-106">[in] A `CLRDATA_ADDRESS` belleğin boşaltılması için başlangıç adresini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="b2738-106">[in] A `CLRDATA_ADDRESS` value that specifies the starting address of the memory to be freed.</span></span>  
  
 `size`  
 <span data-ttu-id="b2738-107">[in] Serbest bırakılacak belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="b2738-107">[in] The size, in bytes, of the memory to be freed.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="b2738-108">[in] Bellek boşaltma denetleyen bayraklar.</span><span class="sxs-lookup"><span data-stu-id="b2738-108">[in] Flags that control the freeing of memory.</span></span> <span data-ttu-id="b2738-109">Win32 bkz `VirtualFree` işlevi.</span><span class="sxs-lookup"><span data-stu-id="b2738-109">See the Win32 `VirtualFree` function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2738-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b2738-110">Remarks</span></span>  
 <span data-ttu-id="b2738-111">`FreeVirtual` Yöntemi Win32 için mantıksal kapsayıcı olarak hizmet veren `VirtualFree` işlevi.</span><span class="sxs-lookup"><span data-stu-id="b2738-111">The `FreeVirtual` method serves as a logical wrapper for the Win32 `VirtualFree` function.</span></span>  
  
 <span data-ttu-id="b2738-112">Bu yöntem, hata ayıklama uygulamanın yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b2738-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2738-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b2738-113">Requirements</span></span>  
 <span data-ttu-id="b2738-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2738-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2738-115">**Üst bilgi:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="b2738-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="b2738-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2738-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2738-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2738-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2738-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2738-118">See also</span></span>
- [<span data-ttu-id="b2738-119">ICLRDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b2738-119">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [<span data-ttu-id="b2738-120">AllocVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2738-120">AllocVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)
