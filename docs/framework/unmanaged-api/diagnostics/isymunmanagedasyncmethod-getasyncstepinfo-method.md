---
title: ISymUnmanagedAsyncMethod::GetAsyncStepInfo Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3ef5b4b8-4ac7-4906-849b-f932c5e3db07
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f999e8cfba38ff4b4b15baea7ca9fa89606cb0ce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodgetasyncstepinfo-method"></a><span data-ttu-id="23b35-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="23b35-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo Method</span></span>
<span data-ttu-id="23b35-103">Bkz: [Defineasyncstepınfo yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="23b35-103">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23b35-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="23b35-104">Syntax</span></span>  
  
```idl  
HRESULT GetAsyncStepInfo(    [in] ULONG32 cStepInfo,    [out] ULONG32 *pcStepInfo,    [in, size_is(cStepInfo)] ULONG32 yieldOffsets[],    [in, size_is(cStepInfo)] ULONG32 breakpointOffset[],    [in, size_is(cStepInfo)] mdToken breakpointMethod[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="23b35-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="23b35-105">Parameters</span></span>  
  
|<span data-ttu-id="23b35-106">Parametre</span><span class="sxs-lookup"><span data-stu-id="23b35-106">Parameter</span></span>|<span data-ttu-id="23b35-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="23b35-107">Description</span></span>|  
|---------------|-----------------|  
|`cStepInfo`||  
|`pcStepInfo`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="23b35-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="23b35-108">Return Value</span></span>  
 <span data-ttu-id="23b35-109">Döndürür `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="23b35-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23b35-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="23b35-110">Requirements</span></span>  
 <span data-ttu-id="23b35-111">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="23b35-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23b35-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="23b35-112">See Also</span></span>  
 [<span data-ttu-id="23b35-113">ISymUnmanagedAsyncMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="23b35-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
