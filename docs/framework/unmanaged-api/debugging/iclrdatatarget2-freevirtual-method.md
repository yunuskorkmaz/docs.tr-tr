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
ms.openlocfilehash: b30bd3e97af8d222f629c5b4f9f318a9b6379e78
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59181408"
---
# <a name="iclrdatatarget2freevirtual-method"></a><span data-ttu-id="9bb10-102">ICLRDataTarget2::FreeVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9bb10-102">ICLRDataTarget2::FreeVirtual Method</span></span>
<span data-ttu-id="9bb10-103">Ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri hedef işlemin adres alanında önceden ayrılmış olan belleği boşaltmak için tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="9bb10-103">Called by the common language runtime (CLR) data access services to free memory that was previously allocated in the address space of the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bb10-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9bb10-104">Syntax</span></span>  
  
```  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9bb10-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9bb10-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="9bb10-106">[in] A `CLRDATA_ADDRESS` belleğin boşaltılması için başlangıç adresini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="9bb10-106">[in] A `CLRDATA_ADDRESS` value that specifies the starting address of the memory to be freed.</span></span>  
  
 `size`  
 <span data-ttu-id="9bb10-107">[in] Serbest bırakılacak belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="9bb10-107">[in] The size, in bytes, of the memory to be freed.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="9bb10-108">[in] Bellek boşaltma denetleyen bayraklar.</span><span class="sxs-lookup"><span data-stu-id="9bb10-108">[in] Flags that control the freeing of memory.</span></span> <span data-ttu-id="9bb10-109">Win32 bkz `VirtualFree` işlevi.</span><span class="sxs-lookup"><span data-stu-id="9bb10-109">See the Win32 `VirtualFree` function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9bb10-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9bb10-110">Remarks</span></span>  
 <span data-ttu-id="9bb10-111">`FreeVirtual` Yöntemi Win32 için mantıksal kapsayıcı olarak hizmet veren `VirtualFree` işlevi.</span><span class="sxs-lookup"><span data-stu-id="9bb10-111">The `FreeVirtual` method serves as a logical wrapper for the Win32 `VirtualFree` function.</span></span>  
  
 <span data-ttu-id="9bb10-112">Bu yöntem, hata ayıklama uygulamanın yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="9bb10-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bb10-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9bb10-113">Requirements</span></span>  
 <span data-ttu-id="9bb10-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bb10-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bb10-115">**Üst bilgi:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="9bb10-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="9bb10-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9bb10-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9bb10-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bb10-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bb10-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9bb10-118">See also</span></span>

- [<span data-ttu-id="9bb10-119">ICLRDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9bb10-119">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [<span data-ttu-id="9bb10-120">AllocVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9bb10-120">AllocVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)
