---
description: ': ICLRDataTarget:: SetThreadContext yöntemi hakkında daha fazla bilgi edinin'
title: ICLRDataTarget::SetThreadContext Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::SetThreadContext
helpviewer_keywords:
- SetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::SetThreadContext method [.NET Framework debugging]
ms.assetid: 103c8502-81fe-40d7-9c1e-9008d8fb19e1
topic_type:
- apiref
ms.openlocfilehash: fc428bc887f7ba10f3096cdf17a757fb252418f0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738211"
---
# <a name="iclrdatatargetsetthreadcontext-method"></a><span data-ttu-id="2b1c5-103">ICLRDataTarget::SetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2b1c5-103">ICLRDataTarget::SetThreadContext Method</span></span>

<span data-ttu-id="2b1c5-104">Hedef işlemde belirtilen iş parçacığının geçerli bağlamını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2b1c5-104">Sets the current context of the specified thread in the target process.</span></span> <span data-ttu-id="2b1c5-105">Bu yöntem, ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="2b1c5-105">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b1c5-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2b1c5-106">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextSize,  
    [in, size_is(contextSize)]
         BYTE               *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b1c5-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2b1c5-107">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="2b1c5-108">'ndaki Hedef işlemdeki bir iş parçacığının işletim sistemi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="2b1c5-108">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="2b1c5-109">'ndaki Bağlam boyutu.</span><span class="sxs-lookup"><span data-stu-id="2b1c5-109">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="2b1c5-110">'ndaki Bağlamı içeren bir arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="2b1c5-110">[in] Pointer to a buffer containing the context.</span></span>  
  
 <span data-ttu-id="2b1c5-111">`context`Arabellekteki veriler Win32 yapısının biçiminde olacaktır `CONTEXT` .</span><span class="sxs-lookup"><span data-stu-id="2b1c5-111">The data in the `context` buffer will be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="2b1c5-112">Bağlam, işlemciye özgü kayıt verilerini belirtir, bu nedenle Win32 `CONTEXT` yapısının tanımı işlemcinin mimarisine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="2b1c5-112">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="2b1c5-113">Win32 yapısının tanımı için WinNT. h üst bilgi dosyasına bakın `CONTEXT` .</span><span class="sxs-lookup"><span data-stu-id="2b1c5-113">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b1c5-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2b1c5-114">Remarks</span></span>  

 <span data-ttu-id="2b1c5-115">Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="2b1c5-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b1c5-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2b1c5-116">Requirements</span></span>  

 <span data-ttu-id="2b1c5-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b1c5-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b1c5-118">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="2b1c5-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="2b1c5-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2b1c5-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b1c5-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b1c5-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b1c5-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b1c5-121">See also</span></span>

- [<span data-ttu-id="2b1c5-122">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2b1c5-122">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
