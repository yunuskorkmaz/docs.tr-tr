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
ms.openlocfilehash: d3f98ab65512a380ebd4dc0ecd50e36f94a6d6b5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104162"
---
# <a name="iclrdatatargetsetthreadcontext-method"></a><span data-ttu-id="15abb-102">ICLRDataTarget::SetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="15abb-102">ICLRDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="15abb-103">Belirtilen iş parçacığının geçerli bağlam hedef işlemde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="15abb-103">Sets the current context of the specified thread in the target process.</span></span> <span data-ttu-id="15abb-104">Bu yöntem, ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="15abb-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15abb-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="15abb-105">Syntax</span></span>  
  
```  
HRESULT SetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextSize,  
    [in, size_is(contextSize)]   
         BYTE               *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15abb-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="15abb-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="15abb-107">[in] Bir iş parçacığı hedef işlem, işletim sistemi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="15abb-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="15abb-108">[in] İçerik boyutu.</span><span class="sxs-lookup"><span data-stu-id="15abb-108">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="15abb-109">[in] Bağlamını içeren bir arabellek için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="15abb-109">[in] Pointer to a buffer containing the context.</span></span>  
  
 <span data-ttu-id="15abb-110">Verileri `context` arabellek Win32 biçiminde olacaktır `CONTEXT` yapısı.</span><span class="sxs-lookup"><span data-stu-id="15abb-110">The data in the `context` buffer will be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="15abb-111">Bağlam nedenle işlemciye özel kayıt veri belirtir Win32 tanımını `CONTEXT` yapısı işlemci mimarisine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="15abb-111">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="15abb-112">Win32 tanımını WinNT.h üstbilgi dosyasına `CONTEXT` yapısı.</span><span class="sxs-lookup"><span data-stu-id="15abb-112">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15abb-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="15abb-113">Remarks</span></span>  
 <span data-ttu-id="15abb-114">Bu yöntem, hata ayıklama uygulamanın yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="15abb-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15abb-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="15abb-115">Requirements</span></span>  
 <span data-ttu-id="15abb-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15abb-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15abb-117">**Üst bilgi:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="15abb-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="15abb-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15abb-118">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="15abb-119">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="15abb-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="15abb-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15abb-120">See also</span></span>

- [<span data-ttu-id="15abb-121">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="15abb-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
