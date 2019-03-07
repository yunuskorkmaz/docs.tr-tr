---
title: ISymUnmanagedAsyncMethod::GetAsyncStepInfo Metodu
ms.date: 03/30/2017
ms.assetid: 3ef5b4b8-4ac7-4906-849b-f932c5e3db07
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 34792ddc7d32c89f6572a48e4636a63881611b88
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57473558"
---
# <a name="isymunmanagedasyncmethodgetasyncstepinfo-method"></a><span data-ttu-id="9f022-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="9f022-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo Method</span></span>
<span data-ttu-id="9f022-103">Bkz: [Defineasyncstepınfo yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="9f022-103">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f022-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9f022-104">Syntax</span></span>  
  
```idl  
HRESULT GetAsyncStepInfo(    [in] ULONG32 cStepInfo,    [out] ULONG32 *pcStepInfo,    [in, size_is(cStepInfo)] ULONG32 yieldOffsets[],    [in, size_is(cStepInfo)] ULONG32 breakpointOffset[],    [in, size_is(cStepInfo)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f022-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9f022-105">Parameters</span></span>  
  
|<span data-ttu-id="9f022-106">Parametre</span><span class="sxs-lookup"><span data-stu-id="9f022-106">Parameter</span></span>|<span data-ttu-id="9f022-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f022-107">Description</span></span>|  
|---------------|-----------------|  
|`cStepInfo`||  
|`pcStepInfo`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="9f022-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9f022-108">Return Value</span></span>  
 <span data-ttu-id="9f022-109">Döndürür `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="9f022-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f022-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9f022-110">Requirements</span></span>  
 <span data-ttu-id="9f022-111">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9f022-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f022-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f022-112">See also</span></span>
- [<span data-ttu-id="9f022-113">ISymUnmanagedAsyncMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9f022-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
