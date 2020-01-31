---
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
ms.openlocfilehash: cdf5776e1ac9907e63aba0e0d400e48aff683d51
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785294"
---
# <a name="iclrdatatargetsetthreadcontext-method"></a><span data-ttu-id="5ea15-102">ICLRDataTarget::SetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5ea15-102">ICLRDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="5ea15-103">Hedef işlemde belirtilen iş parçacığının geçerli bağlamını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5ea15-103">Sets the current context of the specified thread in the target process.</span></span> <span data-ttu-id="5ea15-104">Bu yöntem, ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5ea15-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ea15-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ea15-105">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextSize,  
    [in, size_is(contextSize)]   
         BYTE               *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ea15-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5ea15-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="5ea15-107">'ndaki Hedef işlemdeki bir iş parçacığının işletim sistemi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="5ea15-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="5ea15-108">'ndaki Bağlam boyutu.</span><span class="sxs-lookup"><span data-stu-id="5ea15-108">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="5ea15-109">'ndaki Bağlamı içeren bir arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="5ea15-109">[in] Pointer to a buffer containing the context.</span></span>  
  
 <span data-ttu-id="5ea15-110">`context` arabelleğindeki veriler Win32 `CONTEXT` yapısı biçiminde olacaktır.</span><span class="sxs-lookup"><span data-stu-id="5ea15-110">The data in the `context` buffer will be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="5ea15-111">Bağlam, işlemciye özgü kayıt verilerini belirtir, bu nedenle Win32 `CONTEXT` yapısının tanımı işlemcinin mimarisine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="5ea15-111">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="5ea15-112">Win32 `CONTEXT` yapısının tanımı için WinNT. h üst bilgi dosyasına bakın.</span><span class="sxs-lookup"><span data-stu-id="5ea15-112">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ea15-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ea15-113">Remarks</span></span>  
 <span data-ttu-id="5ea15-114">Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="5ea15-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ea15-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5ea15-115">Requirements</span></span>  
 <span data-ttu-id="5ea15-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ea15-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ea15-117">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="5ea15-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="5ea15-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5ea15-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ea15-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ea15-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ea15-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ea15-120">See also</span></span>

- [<span data-ttu-id="5ea15-121">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5ea15-121">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
