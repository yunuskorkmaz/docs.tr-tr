---
title: ICorDebugVirtualUnwinder::GetContext yöntemi
ms.date: 03/30/2017
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3125fd5081e68237714bcb10f760b73ce7509f6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119235"
---
# <a name="icordebugvirtualunwindergetcontext-method"></a><span data-ttu-id="24db4-102">ICorDebugVirtualUnwinder::GetContext yöntemi</span><span class="sxs-lookup"><span data-stu-id="24db4-102">ICorDebugVirtualUnwinder::GetContext Method</span></span>
<span data-ttu-id="24db4-103">Bu unwinder geçerli bağlamı alır.</span><span class="sxs-lookup"><span data-stu-id="24db4-103">Gets the current context of this unwinder.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24db4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="24db4-104">Syntax</span></span>  
  
```  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24db4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="24db4-105">Parameters</span></span>  
 `contextFlags`  
 <span data-ttu-id="24db4-106">[in] Hangi parçalarının (WinNT.h içinde tanımlanan) dönmek bağlamının belirten bayraklar.</span><span class="sxs-lookup"><span data-stu-id="24db4-106">[in] Flags that specify which parts of the context to return (defined in WinNT.h).</span></span>  
  
 `cbContextBuf`  
 <span data-ttu-id="24db4-107">[in] Bayt sayısı `contextBuf`.</span><span class="sxs-lookup"><span data-stu-id="24db4-107">[in] The number of bytes in `contextBuf`.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="24db4-108">[out] Gerçekte yazılan bayt sayısı için bir işaretçi `contextBuf`.</span><span class="sxs-lookup"><span data-stu-id="24db4-108">[out] A pointer to the number of bytes actually written to `contextBuf`.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="24db4-109">[out] Bu unwinder geçerli bağlamını içeren bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="24db4-109">[out] A byte array that contains the current context of this unwinder.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="24db4-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="24db4-110">Return Value</span></span>  
 <span data-ttu-id="24db4-111">Tüm önemli kabul edilir ve Icordebug döndürülecek API'leri neden olacak mscordbi tarafından alınan HRESULT değerini başarısız `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="24db4-111">Any failing HRESULT value received by mscordbi is considered fatal and will cause ICorDebug APIs to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24db4-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="24db4-112">Remarks</span></span>  
 <span data-ttu-id="24db4-113">Başlangıç değeri ayarlamak `contextBuf` bağımsız değişkeni çağrılarak döndürülen bağlamı arabelleğine [Icordebugstackwalk::getcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="24db4-113">You set the initial value of the `contextBuf` argument to the context buffer returned by calling the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24db4-114">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="24db4-114">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="24db4-115">Yalnızca geriye doğru Mayıs yalnızca geri yükleme bulmasına geçici olmayan gibi yazmaçların kaydeder olduğundan, bağlamı tam olarak zaman gerçek bir yöntem çağrısının kayıt durumu eşleşmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="24db4-115">Because unwinding may only restore a subset of the registers, such as the non-volatile registers only, the context may not exactly match the register state at the time of the actual method call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24db4-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="24db4-116">Requirements</span></span>  
 <span data-ttu-id="24db4-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24db4-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24db4-118">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="24db4-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="24db4-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24db4-119">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="24db4-120">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="24db4-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="24db4-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="24db4-121">See also</span></span>

- [<span data-ttu-id="24db4-122">ICorDebugMemoryBuffer Arabirimi</span><span class="sxs-lookup"><span data-stu-id="24db4-122">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="24db4-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="24db4-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
