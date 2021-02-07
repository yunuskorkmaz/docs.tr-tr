---
description: 'Daha fazla bilgi edinin: ICorDebugProcess6:: Markdebuggerekli yöntemi'
title: ICorDebugProcess6::MarkDebuggerAttached Yöntemi
ms.date: 03/30/2017
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
ms.openlocfilehash: adbe16049cea73ca5e797f7758a17902b33645c5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691386"
---
# <a name="icordebugprocess6markdebuggerattached-method"></a><span data-ttu-id="236e8-103">ICorDebugProcess6::MarkDebuggerAttached Yöntemi</span><span class="sxs-lookup"><span data-stu-id="236e8-103">ICorDebugProcess6::MarkDebuggerAttached Method</span></span>

<span data-ttu-id="236e8-104"><xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType>.NET Framework sınıf kitaplığındaki yöntemin döndürdüğü şekilde, hata ayıklayıcı 'nın iç durumunu değiştirir `true` .</span><span class="sxs-lookup"><span data-stu-id="236e8-104">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="236e8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="236e8-105">Syntax</span></span>  
  
```cpp  
HRESULT MarkDebuggerAttached(  
    BOOL fIsAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="236e8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="236e8-106">Parameters</span></span>  

 `fIsAttached`  
 <span data-ttu-id="236e8-107">`true`<xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType>yöntemin bir hata ayıklayıcının bağlı olduğunu belirtmesi gerekiyorsa, `false` Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="236e8-107">`true` if the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method should indicate that a debugger is attached; `false` otherwise.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="236e8-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="236e8-108">Return Value</span></span>  

 <span data-ttu-id="236e8-109">Yöntemi aşağıdaki tabloda listelenen değerleri döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="236e8-109">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="236e8-110">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="236e8-110">Return value</span></span>|<span data-ttu-id="236e8-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="236e8-111">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="236e8-112">Hata ayıklanan başarıyla güncelleştirildi.</span><span class="sxs-lookup"><span data-stu-id="236e8-112">The debuggee was successfully updated.</span></span>|  
|`CORDBG_E_MODULE_NOT_LOADED`|<span data-ttu-id="236e8-113">Yöntemi içeren derleme <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> yüklü değil veya eksik meta veriler gibi başka bir hata da tanınmasını engellemektedir.</span><span class="sxs-lookup"><span data-stu-id="236e8-113">The assembly that contains the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method is not loaded, or some other error, such as missing metadata, is preventing it from being recognized.</span></span><br /><br /> <span data-ttu-id="236e8-114">Bu hata yaygın ve zararsız.</span><span class="sxs-lookup"><span data-stu-id="236e8-114">This error is common and benign.</span></span> <span data-ttu-id="236e8-115">Ek derlemeler yüklenirken yöntemi tekrar çağırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="236e8-115">You should call the method again when additional assemblies load.</span></span>|  
|<span data-ttu-id="236e8-116">Diğer başarısız `HRESULT` değerler.</span><span class="sxs-lookup"><span data-stu-id="236e8-116">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="236e8-117">Diğer değerler muhtemelen hatalı hata ayıklayıcı veya derleyici bileşenlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="236e8-117">Other values likely indicate misbehaving debugger or compiler components.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="236e8-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="236e8-118">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="236e8-119">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="236e8-119">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="236e8-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="236e8-120">Requirements</span></span>  

 <span data-ttu-id="236e8-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="236e8-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="236e8-122">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="236e8-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="236e8-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="236e8-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="236e8-124">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="236e8-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="236e8-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="236e8-125">See also</span></span>

- [<span data-ttu-id="236e8-126">ICorDebugProcess6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="236e8-126">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="236e8-127">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="236e8-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
