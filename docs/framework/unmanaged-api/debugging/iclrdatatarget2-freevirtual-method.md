---
description: 'Daha fazla bilgi edinin: ICLRDataTarget2:: FreeVirtual Yöntemi'
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
ms.openlocfilehash: ef4048f421fcdc7d284663036f8cc9f2614f4e13
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729256"
---
# <a name="iclrdatatarget2freevirtual-method"></a><span data-ttu-id="93e87-103">ICLRDataTarget2::FreeVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="93e87-103">ICLRDataTarget2::FreeVirtual Method</span></span>

<span data-ttu-id="93e87-104">Daha önce hedef işlemin adres alanında ayrılan belleği boşaltmak için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="93e87-104">Called by the common language runtime (CLR) data access services to free memory that was previously allocated in the address space of the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93e87-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="93e87-105">Syntax</span></span>  
  
```cpp  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93e87-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="93e87-106">Parameters</span></span>  

 `addr`  
 <span data-ttu-id="93e87-107">'ndaki `CLRDATA_ADDRESS` Boşaltılacak belleğin başlangıç adresini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="93e87-107">[in] A `CLRDATA_ADDRESS` value that specifies the starting address of the memory to be freed.</span></span>  
  
 `size`  
 <span data-ttu-id="93e87-108">'ndaki Boşaltılacak belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="93e87-108">[in] The size, in bytes, of the memory to be freed.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="93e87-109">'ndaki Belleğin boşaltımı kontrol eden bayraklar.</span><span class="sxs-lookup"><span data-stu-id="93e87-109">[in] Flags that control the freeing of memory.</span></span> <span data-ttu-id="93e87-110">Bkz. Win32 `VirtualFree` işlevi.</span><span class="sxs-lookup"><span data-stu-id="93e87-110">See the Win32 `VirtualFree` function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93e87-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="93e87-111">Remarks</span></span>  

 <span data-ttu-id="93e87-112">`FreeVirtual`Yöntemi, Win32 işlevi için bir mantıksal sarmalayıcı görevi görür `VirtualFree` .</span><span class="sxs-lookup"><span data-stu-id="93e87-112">The `FreeVirtual` method serves as a logical wrapper for the Win32 `VirtualFree` function.</span></span>  
  
 <span data-ttu-id="93e87-113">Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="93e87-113">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93e87-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="93e87-114">Requirements</span></span>  

 <span data-ttu-id="93e87-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93e87-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93e87-116">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="93e87-116">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="93e87-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="93e87-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93e87-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93e87-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93e87-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93e87-119">See also</span></span>

- [<span data-ttu-id="93e87-120">ICLRDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="93e87-120">ICLRDataTarget2 Interface</span></span>](iclrdatatarget2-interface.md)
- [<span data-ttu-id="93e87-121">AllocVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="93e87-121">AllocVirtual Method</span></span>](iclrdatatarget2-allocvirtual-method.md)
