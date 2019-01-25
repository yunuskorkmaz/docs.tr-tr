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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9018ccc27d0afc35b9dfa2d2ebad323c9150ae60
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580700"
---
# <a name="iclrdatatargetsetthreadcontext-method"></a><span data-ttu-id="d5c2c-102">ICLRDataTarget::SetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5c2c-102">ICLRDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="d5c2c-103">Belirtilen iş parçacığının geçerli bağlam hedef işlemde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-103">Sets the current context of the specified thread in the target process.</span></span> <span data-ttu-id="d5c2c-104">Bu yöntem, ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5c2c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d5c2c-105">Syntax</span></span>  
  
```  
HRESULT SetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextSize,  
    [in, size_is(contextSize)]   
         BYTE               *context  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d5c2c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d5c2c-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="d5c2c-107">[in] Bir iş parçacığı hedef işlem, işletim sistemi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="d5c2c-108">[in] İçerik boyutu.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-108">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="d5c2c-109">[in] Bağlamını içeren bir arabellek için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-109">[in] Pointer to a buffer containing the context.</span></span>  
  
 <span data-ttu-id="d5c2c-110">Verileri `context` arabellek Win32 biçiminde olacaktır `CONTEXT` yapısı.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-110">The data in the `context` buffer will be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="d5c2c-111">Bağlam nedenle işlemciye özel kayıt veri belirtir Win32 tanımını `CONTEXT` yapısı işlemci mimarisine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-111">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="d5c2c-112">Win32 tanımını WinNT.h üstbilgi dosyasına `CONTEXT` yapısı.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-112">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5c2c-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d5c2c-113">Remarks</span></span>  
 <span data-ttu-id="d5c2c-114">Bu yöntem, hata ayıklama uygulamanın yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5c2c-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d5c2c-115">Requirements</span></span>  
 <span data-ttu-id="d5c2c-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5c2c-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5c2c-117">**Üst bilgi:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="d5c2c-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="d5c2c-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5c2c-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5c2c-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5c2c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5c2c-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-120">See also</span></span>
- [<span data-ttu-id="d5c2c-121">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d5c2c-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
