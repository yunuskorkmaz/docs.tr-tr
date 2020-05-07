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
ms.openlocfilehash: 5c0fb023dd355f3a9c1ed846913f86b354592ed5
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860613"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a><span data-ttu-id="5ffab-102">ICLRDataTarget::GetThreadContext Metodu</span><span class="sxs-lookup"><span data-stu-id="5ffab-102">ICLRDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="5ffab-103">Hedef işlemde verilen iş parçacığı için geçerli yürütme bağlamını alır.</span><span class="sxs-lookup"><span data-stu-id="5ffab-103">Gets the current execution context for the given thread in the target process.</span></span> <span data-ttu-id="5ffab-104">Bu yöntem, ortak dil çalışma zamanı veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5ffab-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ffab-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ffab-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]
        BYTE                *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ffab-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5ffab-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="5ffab-107">'ndaki Hedef işlemdeki bir iş parçacığının işletim sistemi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="5ffab-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="5ffab-108">'ndaki Bağlamın hangi bölümlerinin dönebileceği belirten bayraklar.</span><span class="sxs-lookup"><span data-stu-id="5ffab-108">[in] Flags that specify which parts of the context to return.</span></span> <span data-ttu-id="5ffab-109">Uygulama, en azından bu içeriğin bölümlerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="5ffab-109">The implementation will return at least these parts of the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="5ffab-110">'ndaki Bağlam boyutu.</span><span class="sxs-lookup"><span data-stu-id="5ffab-110">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="5ffab-111">dışı İçeriğin yerleştirileceği bir arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="5ffab-111">[out] Pointer to a buffer in which to place the context.</span></span>  
  
 <span data-ttu-id="5ffab-112">`context` Arabellekteki verilerin Win32 `CONTEXT` yapısı biçiminde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5ffab-112">The data in the `context` buffer must be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="5ffab-113">Bağlam, işlemciye özgü kayıt verilerini belirtir, bu nedenle Win32 `CONTEXT` yapısının tanımı işlemcinin mimarisine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="5ffab-113">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="5ffab-114">Win32 `CONTEXT` yapısının tanımı için Winnt. h üst bilgi dosyasına bakın.</span><span class="sxs-lookup"><span data-stu-id="5ffab-114">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ffab-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ffab-115">Remarks</span></span>  
 <span data-ttu-id="5ffab-116">Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="5ffab-116">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ffab-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5ffab-117">Requirements</span></span>  
 <span data-ttu-id="5ffab-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ffab-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ffab-119">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="5ffab-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="5ffab-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5ffab-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ffab-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ffab-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ffab-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ffab-122">See also</span></span>

- [<span data-ttu-id="5ffab-123">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5ffab-123">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
