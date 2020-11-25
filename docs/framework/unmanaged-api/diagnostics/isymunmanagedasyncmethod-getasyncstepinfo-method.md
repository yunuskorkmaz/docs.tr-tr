---
title: ISymUnmanagedAsyncMethod::GetAsyncStepInfo Metodu
ms.date: 03/30/2017
ms.assetid: 3ef5b4b8-4ac7-4906-849b-f932c5e3db07
ms.openlocfilehash: f9392dae4119e59b4eb0fdb87e2b334b32b77109
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707262"
---
# <a name="isymunmanagedasyncmethodgetasyncstepinfo-method"></a><span data-ttu-id="42cca-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="42cca-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo Method</span></span>

<span data-ttu-id="42cca-103">Bkz. [DefineAsyncStepInfo Yöntemi](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="42cca-103">See [DefineAsyncStepInfo Method](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42cca-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="42cca-104">Syntax</span></span>  
  
```idl  
HRESULT GetAsyncStepInfo(    [in] ULONG32 cStepInfo,    [out] ULONG32 *pcStepInfo,    [in, size_is(cStepInfo)] ULONG32 yieldOffsets[],    [in, size_is(cStepInfo)] ULONG32 breakpointOffset[],    [in, size_is(cStepInfo)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42cca-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="42cca-105">Parameters</span></span>  
  
|<span data-ttu-id="42cca-106">Parametre</span><span class="sxs-lookup"><span data-stu-id="42cca-106">Parameter</span></span>|<span data-ttu-id="42cca-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="42cca-107">Description</span></span>|  
|---------------|-----------------|  
|`cStepInfo`||  
|`pcStepInfo`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="42cca-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="42cca-108">Return Value</span></span>  

 <span data-ttu-id="42cca-109">`HRESULT` döndürür.</span><span class="sxs-lookup"><span data-stu-id="42cca-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42cca-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="42cca-110">Requirements</span></span>  

 <span data-ttu-id="42cca-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="42cca-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42cca-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42cca-112">See also</span></span>

- [<span data-ttu-id="42cca-113">ISymUnmanagedAsyncMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="42cca-113">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)
