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
ms.openlocfilehash: 3777ad4b12c7d0593c095c470aba81088137a859
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179174"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a><span data-ttu-id="5dfd6-102">ICLRDataTarget::GetThreadContext Metodu</span><span class="sxs-lookup"><span data-stu-id="5dfd6-102">ICLRDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="5dfd6-103">Hedef işlemde verilen iş parçacığı için geçerli yürütme bağlamını alır.</span><span class="sxs-lookup"><span data-stu-id="5dfd6-103">Gets the current execution context for the given thread in the target process.</span></span> <span data-ttu-id="5dfd6-104">Bu yöntem, ortak dil çalışma zamanı veri erişim hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5dfd6-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5dfd6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5dfd6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]
        BYTE                *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5dfd6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5dfd6-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="5dfd6-107">[içinde] Hedef işlemdeki bir iş parçacığının işletim sistemi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="5dfd6-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="5dfd6-108">[içinde] Bağlamın hangi bölümlerinin döndürülecek olduğunu belirten bayraklar.</span><span class="sxs-lookup"><span data-stu-id="5dfd6-108">[in] Flags that specify which parts of the context to return.</span></span> <span data-ttu-id="5dfd6-109">Uygulama bağlamın en azından bu bölümleri döndürecektir.</span><span class="sxs-lookup"><span data-stu-id="5dfd6-109">The implementation will return at least these parts of the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="5dfd6-110">[içinde] Bağlamın boyutu.</span><span class="sxs-lookup"><span data-stu-id="5dfd6-110">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="5dfd6-111">[çıkış] Bağlamı yerleştirmek için bir arabellek işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="5dfd6-111">[out] Pointer to a buffer in which to place the context.</span></span>  
  
 <span data-ttu-id="5dfd6-112">Arabellekteki `context` veriler Win32 `CONTEXT` yapısı biçiminde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5dfd6-112">The data in the `context` buffer must be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="5dfd6-113">Bağlam işlemciye özgü kayıt verilerini belirtir, bu nedenle Win32 `CONTEXT` yapısının tanımı işlemcinin mimarisine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="5dfd6-113">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="5dfd6-114">Win32 `CONTEXT` yapısının tanımı için WinNT.h üstbilgi dosyasına bakın.</span><span class="sxs-lookup"><span data-stu-id="5dfd6-114">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5dfd6-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5dfd6-115">Remarks</span></span>  
 <span data-ttu-id="5dfd6-116">Bu yöntem hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="5dfd6-116">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5dfd6-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5dfd6-117">Requirements</span></span>  
 <span data-ttu-id="5dfd6-118">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5dfd6-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5dfd6-119">**Üstbilgi:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="5dfd6-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="5dfd6-120">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5dfd6-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5dfd6-121">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5dfd6-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dfd6-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5dfd6-122">See also</span></span>

- [<span data-ttu-id="5dfd6-123">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5dfd6-123">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
