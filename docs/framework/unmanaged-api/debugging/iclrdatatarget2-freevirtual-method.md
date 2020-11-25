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
ms.openlocfilehash: 1fb701a40abe2dc6e51443837c07ee5ba05ddfbe
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723655"
---
# <a name="iclrdatatarget2freevirtual-method"></a><span data-ttu-id="83f4b-102">ICLRDataTarget2::FreeVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="83f4b-102">ICLRDataTarget2::FreeVirtual Method</span></span>

<span data-ttu-id="83f4b-103">Daha önce hedef işlemin adres alanında ayrılan belleği boşaltmak için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="83f4b-103">Called by the common language runtime (CLR) data access services to free memory that was previously allocated in the address space of the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83f4b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="83f4b-104">Syntax</span></span>  
  
```cpp  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83f4b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="83f4b-105">Parameters</span></span>  

 `addr`  
 <span data-ttu-id="83f4b-106">'ndaki `CLRDATA_ADDRESS` Boşaltılacak belleğin başlangıç adresini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="83f4b-106">[in] A `CLRDATA_ADDRESS` value that specifies the starting address of the memory to be freed.</span></span>  
  
 `size`  
 <span data-ttu-id="83f4b-107">'ndaki Boşaltılacak belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="83f4b-107">[in] The size, in bytes, of the memory to be freed.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="83f4b-108">'ndaki Belleğin boşaltımı kontrol eden bayraklar.</span><span class="sxs-lookup"><span data-stu-id="83f4b-108">[in] Flags that control the freeing of memory.</span></span> <span data-ttu-id="83f4b-109">Bkz. Win32 `VirtualFree` işlevi.</span><span class="sxs-lookup"><span data-stu-id="83f4b-109">See the Win32 `VirtualFree` function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83f4b-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="83f4b-110">Remarks</span></span>  

 <span data-ttu-id="83f4b-111">`FreeVirtual`Yöntemi, Win32 işlevi için bir mantıksal sarmalayıcı görevi görür `VirtualFree` .</span><span class="sxs-lookup"><span data-stu-id="83f4b-111">The `FreeVirtual` method serves as a logical wrapper for the Win32 `VirtualFree` function.</span></span>  
  
 <span data-ttu-id="83f4b-112">Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="83f4b-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83f4b-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="83f4b-113">Requirements</span></span>  

 <span data-ttu-id="83f4b-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83f4b-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83f4b-115">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="83f4b-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="83f4b-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="83f4b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83f4b-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83f4b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83f4b-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83f4b-118">See also</span></span>

- [<span data-ttu-id="83f4b-119">ICLRDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="83f4b-119">ICLRDataTarget2 Interface</span></span>](iclrdatatarget2-interface.md)
- [<span data-ttu-id="83f4b-120">AllocVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="83f4b-120">AllocVirtual Method</span></span>](iclrdatatarget2-allocvirtual-method.md)
