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
ms.openlocfilehash: 0a36af5b411673081e74aa243ec8e0f8f876f238
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860478"
---
# <a name="iclrdatatarget2freevirtual-method"></a><span data-ttu-id="cba05-102">ICLRDataTarget2::FreeVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cba05-102">ICLRDataTarget2::FreeVirtual Method</span></span>
<span data-ttu-id="cba05-103">Daha önce hedef işlemin adres alanında ayrılan belleği boşaltmak için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="cba05-103">Called by the common language runtime (CLR) data access services to free memory that was previously allocated in the address space of the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cba05-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cba05-104">Syntax</span></span>  
  
```cpp  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cba05-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cba05-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="cba05-106">'ndaki Boşaltılacak `CLRDATA_ADDRESS` belleğin başlangıç adresini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="cba05-106">[in] A `CLRDATA_ADDRESS` value that specifies the starting address of the memory to be freed.</span></span>  
  
 `size`  
 <span data-ttu-id="cba05-107">'ndaki Boşaltılacak belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="cba05-107">[in] The size, in bytes, of the memory to be freed.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="cba05-108">'ndaki Belleğin boşaltımı kontrol eden bayraklar.</span><span class="sxs-lookup"><span data-stu-id="cba05-108">[in] Flags that control the freeing of memory.</span></span> <span data-ttu-id="cba05-109">Bkz. Win32 `VirtualFree` işlevi.</span><span class="sxs-lookup"><span data-stu-id="cba05-109">See the Win32 `VirtualFree` function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cba05-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cba05-110">Remarks</span></span>  
 <span data-ttu-id="cba05-111">`FreeVirtual` Yöntemi, Win32 `VirtualFree` işlevi için bir mantıksal sarmalayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="cba05-111">The `FreeVirtual` method serves as a logical wrapper for the Win32 `VirtualFree` function.</span></span>  
  
 <span data-ttu-id="cba05-112">Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="cba05-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cba05-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cba05-113">Requirements</span></span>  
 <span data-ttu-id="cba05-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cba05-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cba05-115">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="cba05-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="cba05-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cba05-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cba05-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cba05-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cba05-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cba05-118">See also</span></span>

- [<span data-ttu-id="cba05-119">ICLRDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cba05-119">ICLRDataTarget2 Interface</span></span>](iclrdatatarget2-interface.md)
- [<span data-ttu-id="cba05-120">AllocVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cba05-120">AllocVirtual Method</span></span>](iclrdatatarget2-allocvirtual-method.md)
