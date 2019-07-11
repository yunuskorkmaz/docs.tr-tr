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
ms.openlocfilehash: 6d51c445d6f375f805253b9f640ab61ab3dccc58
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738480"
---
# <a name="iclrdatatarget2freevirtual-method"></a><span data-ttu-id="02b87-102">ICLRDataTarget2::FreeVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="02b87-102">ICLRDataTarget2::FreeVirtual Method</span></span>
<span data-ttu-id="02b87-103">Ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri hedef işlemin adres alanında önceden ayrılmış olan belleği boşaltmak için tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="02b87-103">Called by the common language runtime (CLR) data access services to free memory that was previously allocated in the address space of the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02b87-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="02b87-104">Syntax</span></span>  
  
```cpp  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02b87-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="02b87-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="02b87-106">[in] A `CLRDATA_ADDRESS` belleğin boşaltılması için başlangıç adresini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="02b87-106">[in] A `CLRDATA_ADDRESS` value that specifies the starting address of the memory to be freed.</span></span>  
  
 `size`  
 <span data-ttu-id="02b87-107">[in] Serbest bırakılacak belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="02b87-107">[in] The size, in bytes, of the memory to be freed.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="02b87-108">[in] Bellek boşaltma denetleyen bayraklar.</span><span class="sxs-lookup"><span data-stu-id="02b87-108">[in] Flags that control the freeing of memory.</span></span> <span data-ttu-id="02b87-109">Win32 bkz `VirtualFree` işlevi.</span><span class="sxs-lookup"><span data-stu-id="02b87-109">See the Win32 `VirtualFree` function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02b87-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="02b87-110">Remarks</span></span>  
 <span data-ttu-id="02b87-111">`FreeVirtual` Yöntemi Win32 için mantıksal kapsayıcı olarak hizmet veren `VirtualFree` işlevi.</span><span class="sxs-lookup"><span data-stu-id="02b87-111">The `FreeVirtual` method serves as a logical wrapper for the Win32 `VirtualFree` function.</span></span>  
  
 <span data-ttu-id="02b87-112">Bu yöntem, hata ayıklama uygulamanın yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="02b87-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02b87-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="02b87-113">Requirements</span></span>  
 <span data-ttu-id="02b87-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02b87-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02b87-115">**Üst bilgi:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="02b87-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="02b87-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="02b87-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02b87-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02b87-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02b87-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="02b87-118">See also</span></span>

- [<span data-ttu-id="02b87-119">ICLRDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="02b87-119">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [<span data-ttu-id="02b87-120">AllocVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="02b87-120">AllocVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)
