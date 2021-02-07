---
description: 'Şu konuda daha fazla bilgi edinin: ırivmanagedasyncmethod:: GetAsyncStepInfo Yöntemi'
title: ISymUnmanagedAsyncMethod::GetAsyncStepInfo Metodu
ms.date: 03/30/2017
ms.assetid: 3ef5b4b8-4ac7-4906-849b-f932c5e3db07
ms.openlocfilehash: dc255323f103b3422b927b0489402b24767dcd92
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737850"
---
# <a name="isymunmanagedasyncmethodgetasyncstepinfo-method"></a><span data-ttu-id="a6b6e-103">ISymUnmanagedAsyncMethod::GetAsyncStepInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="a6b6e-103">ISymUnmanagedAsyncMethod::GetAsyncStepInfo Method</span></span>

<span data-ttu-id="a6b6e-104">Bkz. [DefineAsyncStepInfo Yöntemi](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="a6b6e-104">See [DefineAsyncStepInfo Method](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6b6e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a6b6e-105">Syntax</span></span>  
  
```idl  
HRESULT GetAsyncStepInfo(    [in] ULONG32 cStepInfo,    [out] ULONG32 *pcStepInfo,    [in, size_is(cStepInfo)] ULONG32 yieldOffsets[],    [in, size_is(cStepInfo)] ULONG32 breakpointOffset[],    [in, size_is(cStepInfo)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6b6e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a6b6e-106">Parameters</span></span>  
  
|<span data-ttu-id="a6b6e-107">Parametre</span><span class="sxs-lookup"><span data-stu-id="a6b6e-107">Parameter</span></span>|<span data-ttu-id="a6b6e-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a6b6e-108">Description</span></span>|  
|---------------|-----------------|  
|`cStepInfo`||  
|`pcStepInfo`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="a6b6e-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a6b6e-109">Return Value</span></span>  

 <span data-ttu-id="a6b6e-110">`HRESULT` döndürür.</span><span class="sxs-lookup"><span data-stu-id="a6b6e-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6b6e-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a6b6e-111">Requirements</span></span>  

 <span data-ttu-id="a6b6e-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="a6b6e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6b6e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6b6e-113">See also</span></span>

- [<span data-ttu-id="a6b6e-114">ISymUnmanagedAsyncMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a6b6e-114">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)
