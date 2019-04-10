---
title: ICorDebugProcess2::SetDesiredNGENCompilerFlags Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.SetDesiredNGENCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::SetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::SetDesiredNGENCompilerFlags method [.NET Framework debugging]
- SetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: 98320175-7c5e-4dbb-8683-86fa82e2641f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e061c3f3dc95e63339d6fd5f82b3cb4d38a4b6c6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206713"
---
# <a name="icordebugprocess2setdesiredngencompilerflags-method"></a><span data-ttu-id="0c2c2-102">ICorDebugProcess2::SetDesiredNGENCompilerFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0c2c2-102">ICorDebugProcess2::SetDesiredNGENCompilerFlags Method</span></span>
<span data-ttu-id="0c2c2-103">Geçerli işleme bu görüntüyü yüklemek çalışma zamanı için sırayla önceden derlenmiş bir görüntüde gömülü gerekir bayraklarını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0c2c2-103">Sets the flags that must be embedded in a precompiled image in order for the runtime to load that image into the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c2c2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0c2c2-104">Syntax</span></span>  
  
```  
HRESULT SetDesiredNGENCompilerFlags (  
    [in] DWORD    pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c2c2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0c2c2-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="0c2c2-106">[in] Değerini [Cordebugjıtcompilerflags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) derleyici bayraklarına belirten sabit listesi önceden derlenmiş doğru görüntüyü seçmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0c2c2-106">[in] A value of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration that specifies the compiler flags used to select the correct pre-compiled image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c2c2-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0c2c2-107">Remarks</span></span>  
 <span data-ttu-id="0c2c2-108">`SetDesiredNGENCompilerFlags` Yöntemi önceden derlenmiş bir görüntüde gömülü olması gerekir ve böylece çalışma zamanı bu işlemine o yansıma yükleyecek bayrakları belirtir.</span><span class="sxs-lookup"><span data-stu-id="0c2c2-108">The `SetDesiredNGENCompilerFlags` method specifies the flags that must be embedded in a precompiled image so that the runtime will load that image into this process.</span></span> <span data-ttu-id="0c2c2-109">Bu yöntem tarafından ayarlanan bayraklar yalnızca önceden derlenmiş doğru görüntüyü seçmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0c2c2-109">The flags set by this method are used only to select the correct precompiled image.</span></span> <span data-ttu-id="0c2c2-110">Çalışma zamanı Microsoft Ara dili (MSIL) görüntüsü ve just-ın-time (JIT) derleyici bu tür bir görüntü varsa, bunun yerine yükler.</span><span class="sxs-lookup"><span data-stu-id="0c2c2-110">If no such image exists, the runtime will load the Microsoft intermediate language (MSIL) image and the just-in-time (JIT) compiler instead.</span></span> <span data-ttu-id="0c2c2-111">Bu durumda, hata ayıklayıcı hala kullanmalısınız [Icordebugmodule2::setjıtcompilerflags](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md) istenen JIT derlemesi için bayrakları ayarlamanızı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0c2c2-111">In that case, the debugger must still use the [ICorDebugModule2::SetJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md) method to set the flags as desired for the JIT compilation.</span></span>  
  
 <span data-ttu-id="0c2c2-112">Görüntü yüklendi, ancak bazı JIT derleme bu görüntüyü (görüntü, genel türler içeriyorsa, olacaktır) yer almalıdır tarafından belirtilen derleyici bayraklarına `SetDesiredNGENCompilerFlags` yöntemi ek JIT derlemesi için uygulanır.</span><span class="sxs-lookup"><span data-stu-id="0c2c2-112">If an image is loaded, but some JIT compiling must take place for that image (which will be the case if the image contains generics), the compiler flags specified by the `SetDesiredNGENCompilerFlags` method will apply to the extra JIT compilation.</span></span>  
  
 <span data-ttu-id="0c2c2-113">`SetDesiredNGENCompilerFlags` Sırasında metodu çağrılmalıdır [Icordebugmanagedcallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="0c2c2-113">The `SetDesiredNGENCompilerFlags` method must be called during the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="0c2c2-114">Arama girişiminde `SetDesiredNGENCompilerFlags` yöntemi daha sonra başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="0c2c2-114">Attempts to call the `SetDesiredNGENCompilerFlags` method afterwards will fail.</span></span> <span data-ttu-id="0c2c2-115">Olan bayrakları ayarlamaya çalışır ayrıca tanımlanan `CorDebugJITCompilerFlags` numaralandırma veya verilen işlem için yasal değil misiniz başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="0c2c2-115">Also, attempts to set flags that are either not defined in the `CorDebugJITCompilerFlags` enumeration or are not legal for the given process will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c2c2-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0c2c2-116">Requirements</span></span>  
 <span data-ttu-id="0c2c2-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c2c2-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c2c2-118">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0c2c2-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0c2c2-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c2c2-119">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="0c2c2-120">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="0c2c2-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0c2c2-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c2c2-121">See also</span></span>

- [<span data-ttu-id="0c2c2-122">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0c2c2-122">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="0c2c2-123">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0c2c2-123">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
