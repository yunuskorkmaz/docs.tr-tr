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
ms.openlocfilehash: b5f6a830cbe601443f03cd91a356c7e49450e7f3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793723"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a><span data-ttu-id="db099-102">ICLRDataTarget::GetThreadContext Metodu</span><span class="sxs-lookup"><span data-stu-id="db099-102">ICLRDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="db099-103">Hedef işlemde verilen iş parçacığı için geçerli yürütme bağlamını alır.</span><span class="sxs-lookup"><span data-stu-id="db099-103">Gets the current execution context for the given thread in the target process.</span></span> <span data-ttu-id="db099-104">Bu yöntem, ortak dil çalışma zamanı veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="db099-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db099-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="db099-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]   
        BYTE                *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db099-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="db099-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="db099-107">'ndaki Hedef işlemdeki bir iş parçacığının işletim sistemi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="db099-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="db099-108">'ndaki Bağlamın hangi bölümlerinin dönebileceği belirten bayraklar.</span><span class="sxs-lookup"><span data-stu-id="db099-108">[in] Flags that specify which parts of the context to return.</span></span> <span data-ttu-id="db099-109">Uygulama, en azından bu içeriğin bölümlerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="db099-109">The implementation will return at least these parts of the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="db099-110">'ndaki Bağlam boyutu.</span><span class="sxs-lookup"><span data-stu-id="db099-110">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="db099-111">dışı İçeriğin yerleştirileceği bir arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="db099-111">[out] Pointer to a buffer in which to place the context.</span></span>  
  
 <span data-ttu-id="db099-112">`context` arabelleğindeki verilerin Win32 `CONTEXT` yapısı biçiminde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="db099-112">The data in the `context` buffer must be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="db099-113">Bağlam, işlemciye özgü kayıt verilerini belirtir, bu nedenle Win32 `CONTEXT` yapısının tanımı işlemcinin mimarisine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="db099-113">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="db099-114">Win32 `CONTEXT` yapısının tanımı için WinNT. h üst bilgi dosyasına bakın.</span><span class="sxs-lookup"><span data-stu-id="db099-114">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db099-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="db099-115">Remarks</span></span>  
 <span data-ttu-id="db099-116">Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="db099-116">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db099-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="db099-117">Requirements</span></span>  
 <span data-ttu-id="db099-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db099-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db099-119">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="db099-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="db099-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="db099-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db099-121">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db099-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db099-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db099-122">See also</span></span>

- [<span data-ttu-id="db099-123">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="db099-123">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
