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
ms.openlocfilehash: 40b944f6a1204bfe506ed64408be30f68adf3170
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675262"
---
# <a name="icordebugprocess2setdesiredngencompilerflags-method"></a><span data-ttu-id="094d2-102">ICorDebugProcess2::SetDesiredNGENCompilerFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="094d2-102">ICorDebugProcess2::SetDesiredNGENCompilerFlags Method</span></span>

<span data-ttu-id="094d2-103">Çalışma zamanının o görüntüyü geçerli işleme yüklemesi için, önceden derlenmiş bir görüntüye katıştırılması gereken bayrakları ayarlar.</span><span class="sxs-lookup"><span data-stu-id="094d2-103">Sets the flags that must be embedded in a precompiled image in order for the runtime to load that image into the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="094d2-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="094d2-104">Syntax</span></span>  
  
```cpp  
HRESULT SetDesiredNGENCompilerFlags (  
    [in] DWORD    pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="094d2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="094d2-105">Parameters</span></span>  

 `pdwFlags`  
 <span data-ttu-id="094d2-106">'ndaki Doğru önceden derlenmiş görüntüyü seçmek için kullanılan derleyici bayraklarını belirten [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="094d2-106">[in] A value of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration that specifies the compiler flags used to select the correct pre-compiled image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="094d2-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="094d2-107">Remarks</span></span>  

 <span data-ttu-id="094d2-108">`SetDesiredNGENCompilerFlags`Yöntemi, önceden derlenmiş bir görüntüye katıştırılması gereken bayrakları belirtir, böylece çalışma zamanı bu görüntüyü bu işleme yükleyecek.</span><span class="sxs-lookup"><span data-stu-id="094d2-108">The `SetDesiredNGENCompilerFlags` method specifies the flags that must be embedded in a precompiled image so that the runtime will load that image into this process.</span></span> <span data-ttu-id="094d2-109">Bu yöntem tarafından ayarlanan bayraklar yalnızca doğru ön derlenmiş görüntüyü seçmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="094d2-109">The flags set by this method are used only to select the correct precompiled image.</span></span> <span data-ttu-id="094d2-110">Böyle bir görüntü yoksa, çalışma zamanı bunun yerine Microsoft ara dili (MSIL) görüntüsünü ve tam zamanında (JıT) derleyicisini yükler.</span><span class="sxs-lookup"><span data-stu-id="094d2-110">If no such image exists, the runtime will load the Microsoft intermediate language (MSIL) image and the just-in-time (JIT) compiler instead.</span></span> <span data-ttu-id="094d2-111">Bu durumda, hata ayıklayıcı yine de [ICorDebugModule2:: SetJITCompilerFlags](icordebugmodule2-setjitcompilerflags-method.md) metodunu kullanarak bayrakları JIT derlemesi için istediğiniz şekilde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="094d2-111">In that case, the debugger must still use the [ICorDebugModule2::SetJITCompilerFlags](icordebugmodule2-setjitcompilerflags-method.md) method to set the flags as desired for the JIT compilation.</span></span>  
  
 <span data-ttu-id="094d2-112">Bir görüntü yüklenirse, ancak bu görüntü için bazı JıT derleme gerçekleşmelidir (görüntü genel türler içerdiğinde durum olacaktır), yöntem tarafından belirtilen derleyici bayrakları `SetDesiredNGENCompilerFlags` ekstra JIT derlemesi için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="094d2-112">If an image is loaded, but some JIT compiling must take place for that image (which will be the case if the image contains generics), the compiler flags specified by the `SetDesiredNGENCompilerFlags` method will apply to the extra JIT compilation.</span></span>  
  
 <span data-ttu-id="094d2-113">`SetDesiredNGENCompilerFlags`Metodun [ICorDebugManagedCallback:: CreateProcess](icordebugmanagedcallback-createprocess-method.md) geri çağırması sırasında çağrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="094d2-113">The `SetDesiredNGENCompilerFlags` method must be called during the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="094d2-114">`SetDesiredNGENCompilerFlags`Daha sonra yöntemi çağırma girişimleri başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="094d2-114">Attempts to call the `SetDesiredNGENCompilerFlags` method afterwards will fail.</span></span> <span data-ttu-id="094d2-115">Ayrıca, `CorDebugJITCompilerFlags` numaralandırmada tanımlanmayan veya verilen işlem için geçerli olmayan bayrakları ayarlama girişimleri başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="094d2-115">Also, attempts to set flags that are either not defined in the `CorDebugJITCompilerFlags` enumeration or are not legal for the given process will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="094d2-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="094d2-116">Requirements</span></span>  

 <span data-ttu-id="094d2-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="094d2-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="094d2-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="094d2-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="094d2-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="094d2-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="094d2-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="094d2-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="094d2-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="094d2-121">See also</span></span>

- [<span data-ttu-id="094d2-122">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="094d2-122">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="094d2-123">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="094d2-123">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
