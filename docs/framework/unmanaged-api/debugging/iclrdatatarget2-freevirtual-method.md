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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59181408"
---
# <a name="iclrdatatarget2freevirtual-method"></a><span data-ttu-id="6b584-102">ICLRDataTarget2::FreeVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6b584-102">ICLRDataTarget2::FreeVirtual Method</span></span>
<span data-ttu-id="6b584-103">Ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri hedef işlemin adres alanında önceden ayrılmış olan belleği boşaltmak için tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="6b584-103">Called by the common language runtime (CLR) data access services to free memory that was previously allocated in the address space of the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b584-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6b584-104">Syntax</span></span>  
  
```  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b584-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6b584-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="6b584-106">[in] A `CLRDATA_ADDRESS` belleğin boşaltılması için başlangıç adresini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="6b584-106">[in] A `CLRDATA_ADDRESS` value that specifies the starting address of the memory to be freed.</span></span>  
  
 `size`  
 <span data-ttu-id="6b584-107">[in] Serbest bırakılacak belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="6b584-107">[in] The size, in bytes, of the memory to be freed.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="6b584-108">[in] Bellek boşaltma denetleyen bayraklar.</span><span class="sxs-lookup"><span data-stu-id="6b584-108">[in] Flags that control the freeing of memory.</span></span> <span data-ttu-id="6b584-109">Win32 bkz `VirtualFree` işlevi.</span><span class="sxs-lookup"><span data-stu-id="6b584-109">See the Win32 `VirtualFree` function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b584-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6b584-110">Remarks</span></span>  
 <span data-ttu-id="6b584-111">`FreeVirtual` Yöntemi Win32 için mantıksal kapsayıcı olarak hizmet veren `VirtualFree` işlevi.</span><span class="sxs-lookup"><span data-stu-id="6b584-111">The `FreeVirtual` method serves as a logical wrapper for the Win32 `VirtualFree` function.</span></span>  
  
 <span data-ttu-id="6b584-112">Bu yöntem, hata ayıklama uygulamanın yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="6b584-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b584-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6b584-113">Requirements</span></span>  
 <span data-ttu-id="6b584-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b584-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b584-115">**Üst bilgi:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="6b584-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="6b584-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b584-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="6b584-117">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="6b584-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6b584-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b584-118">See also</span></span>

- [<span data-ttu-id="6b584-119">ICLRDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6b584-119">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [<span data-ttu-id="6b584-120">AllocVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6b584-120">AllocVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)
