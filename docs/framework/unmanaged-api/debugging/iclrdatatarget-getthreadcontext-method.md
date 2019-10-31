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
ms.openlocfilehash: 0d34577f0f785bc851646423b8cd732ab4d1dae0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73113859"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a><span data-ttu-id="8dd70-102">ICLRDataTarget::GetThreadContext Metodu</span><span class="sxs-lookup"><span data-stu-id="8dd70-102">ICLRDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="8dd70-103">Hedef işlemde verilen iş parçacığı için geçerli yürütme bağlamını alır.</span><span class="sxs-lookup"><span data-stu-id="8dd70-103">Gets the current execution context for the given thread in the target process.</span></span> <span data-ttu-id="8dd70-104">Bu yöntem, ortak dil çalışma zamanı veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="8dd70-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dd70-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8dd70-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]   
        BYTE                *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8dd70-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8dd70-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="8dd70-107">'ndaki Hedef işlemdeki bir iş parçacığının işletim sistemi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="8dd70-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="8dd70-108">'ndaki Bağlamın hangi bölümlerinin dönebileceği belirten bayraklar.</span><span class="sxs-lookup"><span data-stu-id="8dd70-108">[in] Flags that specify which parts of the context to return.</span></span> <span data-ttu-id="8dd70-109">Uygulama, en azından bu içeriğin bölümlerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="8dd70-109">The implementation will return at least these parts of the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="8dd70-110">'ndaki Bağlam boyutu.</span><span class="sxs-lookup"><span data-stu-id="8dd70-110">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="8dd70-111">dışı İçeriğin yerleştirileceği bir arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="8dd70-111">[out] Pointer to a buffer in which to place the context.</span></span>  
  
 <span data-ttu-id="8dd70-112">`context` arabelleğindeki verilerin Win32 `CONTEXT` yapısı biçiminde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8dd70-112">The data in the `context` buffer must be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="8dd70-113">Bağlam, işlemciye özgü kayıt verilerini belirtir, bu nedenle Win32 `CONTEXT` yapısının tanımı işlemcinin mimarisine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="8dd70-113">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="8dd70-114">Win32 `CONTEXT` yapısının tanımı için WinNT. h üst bilgi dosyasına bakın.</span><span class="sxs-lookup"><span data-stu-id="8dd70-114">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8dd70-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8dd70-115">Remarks</span></span>  
 <span data-ttu-id="8dd70-116">Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="8dd70-116">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8dd70-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8dd70-117">Requirements</span></span>  
 <span data-ttu-id="8dd70-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8dd70-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8dd70-119">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="8dd70-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="8dd70-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8dd70-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8dd70-121">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8dd70-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dd70-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8dd70-122">See also</span></span>

- [<span data-ttu-id="8dd70-123">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8dd70-123">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
