---
title: ISymUnmanagedAsyncMethod::GetAsyncStepInfo Metodu
ms.date: 03/30/2017
ms.assetid: 3ef5b4b8-4ac7-4906-849b-f932c5e3db07
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f7c72d0766580f9aa3aa678aacd872b804172a8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59131436"
---
# <a name="isymunmanagedasyncmethodgetasyncstepinfo-method"></a><span data-ttu-id="c0397-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="c0397-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo Method</span></span>
<span data-ttu-id="c0397-103">Bkz: [Defineasyncstepınfo yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="c0397-103">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0397-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c0397-104">Syntax</span></span>  
  
```idl  
HRESULT GetAsyncStepInfo(    [in] ULONG32 cStepInfo,    [out] ULONG32 *pcStepInfo,    [in, size_is(cStepInfo)] ULONG32 yieldOffsets[],    [in, size_is(cStepInfo)] ULONG32 breakpointOffset[],    [in, size_is(cStepInfo)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0397-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c0397-105">Parameters</span></span>  
  
|<span data-ttu-id="c0397-106">Parametre</span><span class="sxs-lookup"><span data-stu-id="c0397-106">Parameter</span></span>|<span data-ttu-id="c0397-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c0397-107">Description</span></span>|  
|---------------|-----------------|  
|`cStepInfo`||  
|`pcStepInfo`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="c0397-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c0397-108">Return Value</span></span>  
 <span data-ttu-id="c0397-109">Döndürür `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="c0397-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0397-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c0397-110">Requirements</span></span>  
 <span data-ttu-id="c0397-111">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c0397-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0397-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c0397-112">See also</span></span>

- [<span data-ttu-id="c0397-113">ISymUnmanagedAsyncMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c0397-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
