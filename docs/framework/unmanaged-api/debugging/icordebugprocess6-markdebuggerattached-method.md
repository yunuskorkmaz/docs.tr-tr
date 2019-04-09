---
title: ICorDebugProcess6::MarkDebuggerAttached Yöntemi
ms.date: 03/30/2017
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 15e2e94ac4e30fbdb375175148a5b448c51821f0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59128030"
---
# <a name="icordebugprocess6markdebuggerattached-method"></a><span data-ttu-id="3d2d5-102">ICorDebugProcess6::MarkDebuggerAttached Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3d2d5-102">ICorDebugProcess6::MarkDebuggerAttached Method</span></span>
<span data-ttu-id="3d2d5-103">Debugee iç durumunu değiştiren böylece <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> yöntem .NET Framework sınıf kitaplığındaki döndürür `true`.</span><span class="sxs-lookup"><span data-stu-id="3d2d5-103">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d2d5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3d2d5-104">Syntax</span></span>  
  
```  
HRESULT MarkDebuggerAttached(  
    BOOL fIsAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d2d5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3d2d5-105">Parameters</span></span>  
 `fIsAttached`  
 `true` <span data-ttu-id="3d2d5-106">varsa <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> yöntemi belirten bir hata ayıklayıcının bağlı olduğu; `false` Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="3d2d5-106">if the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method should indicate that a debugger is attached; `false` otherwise.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3d2d5-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3d2d5-107">Return Value</span></span>  
 <span data-ttu-id="3d2d5-108">Yöntem aşağıdaki tabloda listelenen değerler döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="3d2d5-108">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="3d2d5-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="3d2d5-109">Return value</span></span>|<span data-ttu-id="3d2d5-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3d2d5-110">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="3d2d5-111">Hata ayıklanan başarıyla güncelleştirildi.</span><span class="sxs-lookup"><span data-stu-id="3d2d5-111">The debuggee was successfully updated.</span></span>|  
|`CORDBG_E_MODULE_NOT_LOADED`|<span data-ttu-id="3d2d5-112">İçeren derleme <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> yöntemi yüklü değil veya eksik meta verileri gibi bazı diğer hata, kabul engelliyor.</span><span class="sxs-lookup"><span data-stu-id="3d2d5-112">The assembly that contains the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method is not loaded, or some other error, such as missing metadata, is preventing it from being recognized.</span></span><br /><br /> <span data-ttu-id="3d2d5-113">Bu, genel ve zararsız hatasıdır.</span><span class="sxs-lookup"><span data-stu-id="3d2d5-113">This error is common and benign.</span></span> <span data-ttu-id="3d2d5-114">Ek derlemeler yüklediğinizde yeniden yöntemini çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3d2d5-114">You should call the method again when additional assemblies load.</span></span>|  
|<span data-ttu-id="3d2d5-115">Diğer başarısız `HRESULT` değerleri.</span><span class="sxs-lookup"><span data-stu-id="3d2d5-115">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="3d2d5-116">Büyük olasılıkla diğer değerler, hatalı davranan hata ayıklayıcı veya derleyici bileşenleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="3d2d5-116">Other values likely indicate misbehaving debugger or compiler components.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d2d5-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3d2d5-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3d2d5-118">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3d2d5-118">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d2d5-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3d2d5-119">Requirements</span></span>  
 <span data-ttu-id="3d2d5-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d2d5-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d2d5-121">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3d2d5-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3d2d5-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d2d5-122">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="3d2d5-123">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="3d2d5-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3d2d5-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d2d5-124">See also</span></span>

- [<span data-ttu-id="3d2d5-125">ICorDebugProcess6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3d2d5-125">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="3d2d5-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3d2d5-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
