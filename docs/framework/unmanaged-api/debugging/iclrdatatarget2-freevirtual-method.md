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
ms.openlocfilehash: 7eda9bfff6de6b386c16ad0a188931d9d3adcb93
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793666"
---
# <a name="iclrdatatarget2freevirtual-method"></a><span data-ttu-id="0dd06-102">ICLRDataTarget2::FreeVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0dd06-102">ICLRDataTarget2::FreeVirtual Method</span></span>
<span data-ttu-id="0dd06-103">Daha önce hedef işlemin adres alanında ayrılan belleği boşaltmak için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="0dd06-103">Called by the common language runtime (CLR) data access services to free memory that was previously allocated in the address space of the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dd06-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0dd06-104">Syntax</span></span>  
  
```cpp  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0dd06-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0dd06-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="0dd06-106">'ndaki Boşaltılacak belleğin başlangıç adresini belirten bir `CLRDATA_ADDRESS` değeri.</span><span class="sxs-lookup"><span data-stu-id="0dd06-106">[in] A `CLRDATA_ADDRESS` value that specifies the starting address of the memory to be freed.</span></span>  
  
 `size`  
 <span data-ttu-id="0dd06-107">'ndaki Boşaltılacak belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="0dd06-107">[in] The size, in bytes, of the memory to be freed.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="0dd06-108">'ndaki Belleğin boşaltımı kontrol eden bayraklar.</span><span class="sxs-lookup"><span data-stu-id="0dd06-108">[in] Flags that control the freeing of memory.</span></span> <span data-ttu-id="0dd06-109">Bkz. Win32 `VirtualFree` işlevi.</span><span class="sxs-lookup"><span data-stu-id="0dd06-109">See the Win32 `VirtualFree` function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0dd06-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0dd06-110">Remarks</span></span>  
 <span data-ttu-id="0dd06-111">`FreeVirtual` yöntemi, Win32 `VirtualFree` işlevi için bir mantıksal sarmalayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="0dd06-111">The `FreeVirtual` method serves as a logical wrapper for the Win32 `VirtualFree` function.</span></span>  
  
 <span data-ttu-id="0dd06-112">Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="0dd06-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0dd06-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0dd06-113">Requirements</span></span>  
 <span data-ttu-id="0dd06-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0dd06-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0dd06-115">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="0dd06-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="0dd06-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0dd06-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0dd06-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0dd06-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dd06-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0dd06-118">See also</span></span>

- [<span data-ttu-id="0dd06-119">ICLRDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0dd06-119">ICLRDataTarget2 Interface</span></span>](iclrdatatarget2-interface.md)
- [<span data-ttu-id="0dd06-120">AllocVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0dd06-120">AllocVirtual Method</span></span>](iclrdatatarget2-allocvirtual-method.md)
