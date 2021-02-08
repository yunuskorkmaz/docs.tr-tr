---
description: ': ICLRDataTarget:: GetThreadContext metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 210f4294aed31307557db419a0fb567cc71d4354
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785698"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a><span data-ttu-id="7175d-103">ICLRDataTarget::GetThreadContext Metodu</span><span class="sxs-lookup"><span data-stu-id="7175d-103">ICLRDataTarget::GetThreadContext Method</span></span>

<span data-ttu-id="7175d-104">Hedef işlemde verilen iş parçacığı için geçerli yürütme bağlamını alır.</span><span class="sxs-lookup"><span data-stu-id="7175d-104">Gets the current execution context for the given thread in the target process.</span></span> <span data-ttu-id="7175d-105">Bu yöntem, ortak dil çalışma zamanı veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="7175d-105">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7175d-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7175d-106">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]
        BYTE                *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7175d-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7175d-107">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="7175d-108">'ndaki Hedef işlemdeki bir iş parçacığının işletim sistemi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="7175d-108">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="7175d-109">'ndaki Bağlamın hangi bölümlerinin dönebileceği belirten bayraklar.</span><span class="sxs-lookup"><span data-stu-id="7175d-109">[in] Flags that specify which parts of the context to return.</span></span> <span data-ttu-id="7175d-110">Uygulama, en azından bu içeriğin bölümlerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="7175d-110">The implementation will return at least these parts of the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="7175d-111">'ndaki Bağlam boyutu.</span><span class="sxs-lookup"><span data-stu-id="7175d-111">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="7175d-112">dışı İçeriğin yerleştirileceği bir arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="7175d-112">[out] Pointer to a buffer in which to place the context.</span></span>  
  
 <span data-ttu-id="7175d-113">`context`Arabellekteki verilerin Win32 yapısı biçiminde olması gerekir `CONTEXT` .</span><span class="sxs-lookup"><span data-stu-id="7175d-113">The data in the `context` buffer must be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="7175d-114">Bağlam, işlemciye özgü kayıt verilerini belirtir, bu nedenle Win32 `CONTEXT` yapısının tanımı işlemcinin mimarisine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="7175d-114">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="7175d-115">Win32 yapısının tanımı için WinNT. h üst bilgi dosyasına bakın `CONTEXT` .</span><span class="sxs-lookup"><span data-stu-id="7175d-115">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7175d-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7175d-116">Remarks</span></span>  

 <span data-ttu-id="7175d-117">Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="7175d-117">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7175d-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7175d-118">Requirements</span></span>  

 <span data-ttu-id="7175d-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7175d-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7175d-120">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="7175d-120">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="7175d-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7175d-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7175d-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7175d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7175d-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7175d-123">See also</span></span>

- [<span data-ttu-id="7175d-124">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7175d-124">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
