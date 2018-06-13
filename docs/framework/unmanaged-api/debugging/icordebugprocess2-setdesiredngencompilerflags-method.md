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
ms.openlocfilehash: 94ba2b0cf7d88104eaadd434732edf3c1d4060e2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422707"
---
# <a name="icordebugprocess2setdesiredngencompilerflags-method"></a><span data-ttu-id="10507-102">ICorDebugProcess2::SetDesiredNGENCompilerFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="10507-102">ICorDebugProcess2::SetDesiredNGENCompilerFlags Method</span></span>
<span data-ttu-id="10507-103">Sırada, görüntü geçerli işlemine yüklemek çalışma zamanı için önceden derlenmiş görüntüsündeki gömülü gerekir bayrakları ayarlar.</span><span class="sxs-lookup"><span data-stu-id="10507-103">Sets the flags that must be embedded in a precompiled image in order for the runtime to load that image into the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10507-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="10507-104">Syntax</span></span>  
  
```  
HRESULT SetDesiredNGENCompilerFlags (  
    [in] DWORD    pdwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="10507-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="10507-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="10507-106">[in] Değerini [Cordebugjıtcompilerflags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) derleyici bayrakları belirtir numaralandırması önceden derlenmiş doğru görüntüyü seçmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="10507-106">[in] A value of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration that specifies the compiler flags used to select the correct pre-compiled image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10507-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="10507-107">Remarks</span></span>  
 <span data-ttu-id="10507-108">`SetDesiredNGENCompilerFlags` Yöntemi önceden derlenmiş bir görüntüde gömülü gerekir ve böylece çalışma zamanı bu işlemine bu görüntüyü yükler bayrakları belirtir.</span><span class="sxs-lookup"><span data-stu-id="10507-108">The `SetDesiredNGENCompilerFlags` method specifies the flags that must be embedded in a precompiled image so that the runtime will load that image into this process.</span></span> <span data-ttu-id="10507-109">Bu yöntem tarafından ayarlanan bayraklar yalnızca doğru önceden derlenmiş görüntüyü seçmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="10507-109">The flags set by this method are used only to select the correct precompiled image.</span></span> <span data-ttu-id="10507-110">Çalışma zamanı Microsoft Ara dili (MSIL) görüntüsü ve tam zamanında (JIT) derleyici böyle bir görüntü varsa, bunun yerine yükler.</span><span class="sxs-lookup"><span data-stu-id="10507-110">If no such image exists, the runtime will load the Microsoft intermediate language (MSIL) image and the just-in-time (JIT) compiler instead.</span></span> <span data-ttu-id="10507-111">Bu durumda, hata ayıklayıcı hala kullanmalısınız [Icordebugmodule2::setjıtcompilerflags](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md) yöntemi JIT derleme için istediğiniz gibi bayraklarını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="10507-111">In that case, the debugger must still use the [ICorDebugModule2::SetJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md) method to set the flags as desired for the JIT compilation.</span></span>  
  
 <span data-ttu-id="10507-112">Bir görüntü yüklenir, ancak bazı JIT derleme (görüntü genel türler içeriyorsa olacağı durum) bu görüntü için gerçekleşmesi gerekir tarafından belirtilen derleyici bayrakları `SetDesiredNGENCompilerFlags` yöntemi ek JIT derleme uygulanacaktır.</span><span class="sxs-lookup"><span data-stu-id="10507-112">If an image is loaded, but some JIT compiling must take place for that image (which will be the case if the image contains generics), the compiler flags specified by the `SetDesiredNGENCompilerFlags` method will apply to the extra JIT compilation.</span></span>  
  
 <span data-ttu-id="10507-113">`SetDesiredNGENCompilerFlags` Yöntemi çağrılır, sırasında [Icordebugmanagedcallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="10507-113">The `SetDesiredNGENCompilerFlags` method must be called during the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="10507-114">Arama girişiminde `SetDesiredNGENCompilerFlags` yöntemi daha sonra başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="10507-114">Attempts to call the `SetDesiredNGENCompilerFlags` method afterwards will fail.</span></span> <span data-ttu-id="10507-115">Ya da olan bayrakları ayarlamaya çalışır Ayrıca, tanımlanan `CorDebugJITCompilerFlags` numaralandırma veya belirli bir işlemi için yasal değil misiniz başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="10507-115">Also, attempts to set flags that are either not defined in the `CorDebugJITCompilerFlags` enumeration or are not legal for the given process will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10507-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="10507-116">Requirements</span></span>  
 <span data-ttu-id="10507-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10507-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10507-118">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="10507-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="10507-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10507-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10507-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10507-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10507-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="10507-121">See Also</span></span>  
 [<span data-ttu-id="10507-122">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="10507-122">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [<span data-ttu-id="10507-123">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="10507-123">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
