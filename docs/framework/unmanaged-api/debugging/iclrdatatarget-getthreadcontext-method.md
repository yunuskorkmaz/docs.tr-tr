---
title: ICLRDataTarget::GetThreadContext Metodu
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetThreadContext
helpviewer_keywords:
- ICLRDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: b9d8c3b5-3a2e-4225-95d4-dd052c4532c3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1492c6d72d68a95a79925d7789a710b5b5ed14b1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738710"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a><span data-ttu-id="3d02d-102">ICLRDataTarget::GetThreadContext Metodu</span><span class="sxs-lookup"><span data-stu-id="3d02d-102">ICLRDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="3d02d-103">Hedef işlemde verilen iş parçacığı için geçerli yürütme bağlamı alır.</span><span class="sxs-lookup"><span data-stu-id="3d02d-103">Gets the current execution context for the given thread in the target process.</span></span> <span data-ttu-id="3d02d-104">Bu yöntem, ortak dil çalışma zamanı veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="3d02d-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d02d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3d02d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]   
        BYTE                *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d02d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3d02d-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="3d02d-107">[in] Bir iş parçacığı hedef işlem, işletim sistemi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="3d02d-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="3d02d-108">[in] Hangi parçalarının dönmek bağlamının belirten bayraklar.</span><span class="sxs-lookup"><span data-stu-id="3d02d-108">[in] Flags that specify which parts of the context to return.</span></span> <span data-ttu-id="3d02d-109">Uygulama bağlamı en az bu bölümlerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="3d02d-109">The implementation will return at least these parts of the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="3d02d-110">[in] İçerik boyutu.</span><span class="sxs-lookup"><span data-stu-id="3d02d-110">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="3d02d-111">[out] Bağlam yerleştirileceği bir arabellek için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3d02d-111">[out] Pointer to a buffer in which to place the context.</span></span>  
  
 <span data-ttu-id="3d02d-112">Verileri `context` arabellek Win32 biçiminde olmalıdır `CONTEXT` yapısı.</span><span class="sxs-lookup"><span data-stu-id="3d02d-112">The data in the `context` buffer must be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="3d02d-113">Bağlam nedenle işlemciye özel kayıt veri belirtir Win32 tanımını `CONTEXT` yapısı işlemci mimarisine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3d02d-113">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="3d02d-114">Win32 tanımını WinNT.h üstbilgi dosyasına `CONTEXT` yapısı.</span><span class="sxs-lookup"><span data-stu-id="3d02d-114">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d02d-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3d02d-115">Remarks</span></span>  
 <span data-ttu-id="3d02d-116">Bu yöntem, hata ayıklama uygulamanın yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="3d02d-116">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d02d-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3d02d-117">Requirements</span></span>  
 <span data-ttu-id="3d02d-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d02d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d02d-119">**Üst bilgi:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="3d02d-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="3d02d-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d02d-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d02d-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d02d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d02d-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d02d-122">See also</span></span>

- [<span data-ttu-id="3d02d-123">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3d02d-123">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
