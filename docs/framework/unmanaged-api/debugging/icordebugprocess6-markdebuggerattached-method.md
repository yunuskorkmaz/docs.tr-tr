---
title: ICorDebugProcess6::MarkDebuggerAttached Yöntemi
ms.date: 03/30/2017
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
ms.openlocfilehash: b2ecd6da11bffb156826fa0c31b5f32abb54ff4a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792217"
---
# <a name="icordebugprocess6markdebuggerattached-method"></a><span data-ttu-id="37c3d-102">ICorDebugProcess6::MarkDebuggerAttached Yöntemi</span><span class="sxs-lookup"><span data-stu-id="37c3d-102">ICorDebugProcess6::MarkDebuggerAttached Method</span></span>
<span data-ttu-id="37c3d-103">.NET Framework sınıf kitaplığındaki <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> yönteminin `true`döndürmesi için hata ayıklayıcı 'nın iç durumunu değiştirir.</span><span class="sxs-lookup"><span data-stu-id="37c3d-103">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37c3d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="37c3d-104">Syntax</span></span>  
  
```cpp  
HRESULT MarkDebuggerAttached(  
    BOOL fIsAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37c3d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="37c3d-105">Parameters</span></span>  
 `fIsAttached`  
 <span data-ttu-id="37c3d-106"><xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> yöntemi bir hata ayıklayıcının ekli olduğunu belirtmesi gerekiyorsa `true`; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="37c3d-106">`true` if the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method should indicate that a debugger is attached; `false` otherwise.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37c3d-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="37c3d-107">Return Value</span></span>  
 <span data-ttu-id="37c3d-108">Yöntemi aşağıdaki tabloda listelenen değerleri döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="37c3d-108">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="37c3d-109">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="37c3d-109">Return value</span></span>|<span data-ttu-id="37c3d-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="37c3d-110">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="37c3d-111">Hata ayıklanan başarıyla güncelleştirildi.</span><span class="sxs-lookup"><span data-stu-id="37c3d-111">The debuggee was successfully updated.</span></span>|  
|`CORDBG_E_MODULE_NOT_LOADED`|<span data-ttu-id="37c3d-112"><xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> yöntemi içeren derleme yüklü değil veya eksik meta veriler gibi başka bir hata, tanınmasını engellemektedir.</span><span class="sxs-lookup"><span data-stu-id="37c3d-112">The assembly that contains the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method is not loaded, or some other error, such as missing metadata, is preventing it from being recognized.</span></span><br /><br /> <span data-ttu-id="37c3d-113">Bu hata yaygın ve zararsız.</span><span class="sxs-lookup"><span data-stu-id="37c3d-113">This error is common and benign.</span></span> <span data-ttu-id="37c3d-114">Ek derlemeler yüklenirken yöntemi tekrar çağırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="37c3d-114">You should call the method again when additional assemblies load.</span></span>|  
|<span data-ttu-id="37c3d-115">Başarısız olan diğer `HRESULT` değerleri.</span><span class="sxs-lookup"><span data-stu-id="37c3d-115">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="37c3d-116">Diğer değerler muhtemelen hatalı hata ayıklayıcı veya derleyici bileşenlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="37c3d-116">Other values likely indicate misbehaving debugger or compiler components.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37c3d-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="37c3d-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="37c3d-118">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="37c3d-118">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37c3d-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="37c3d-119">Requirements</span></span>  
 <span data-ttu-id="37c3d-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37c3d-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37c3d-121">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="37c3d-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="37c3d-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="37c3d-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37c3d-123">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37c3d-123">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37c3d-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37c3d-124">See also</span></span>

- [<span data-ttu-id="37c3d-125">ICorDebugProcess6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="37c3d-125">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="37c3d-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="37c3d-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
