---
title: ISymUnmanagedAsyncMethod::GetAsyncStepInfo Metodu
ms.date: 03/30/2017
ms.assetid: 3ef5b4b8-4ac7-4906-849b-f932c5e3db07
ms.openlocfilehash: e3c0d7b8eeded403ce8391cff00ee18dccc38ed5
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441896"
---
# <a name="isymunmanagedasyncmethodgetasyncstepinfo-method"></a><span data-ttu-id="4e4c9-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="4e4c9-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo Method</span></span>
<span data-ttu-id="4e4c9-103">Bkz. [DefineAsyncStepInfo Yöntemi](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="4e4c9-103">See [DefineAsyncStepInfo Method](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e4c9-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="4e4c9-104">Syntax</span></span>  
  
```idl  
HRESULT GetAsyncStepInfo(    [in] ULONG32 cStepInfo,    [out] ULONG32 *pcStepInfo,    [in, size_is(cStepInfo)] ULONG32 yieldOffsets[],    [in, size_is(cStepInfo)] ULONG32 breakpointOffset[],    [in, size_is(cStepInfo)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e4c9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4e4c9-105">Parameters</span></span>  
  
|<span data-ttu-id="4e4c9-106">Parametre</span><span class="sxs-lookup"><span data-stu-id="4e4c9-106">Parameter</span></span>|<span data-ttu-id="4e4c9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4e4c9-107">Description</span></span>|  
|---------------|-----------------|  
|`cStepInfo`||  
|`pcStepInfo`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="4e4c9-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4e4c9-108">Return Value</span></span>  
 <span data-ttu-id="4e4c9-109">`HRESULT` döndürür.</span><span class="sxs-lookup"><span data-stu-id="4e4c9-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e4c9-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4e4c9-110">Requirements</span></span>  
 <span data-ttu-id="4e4c9-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="4e4c9-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e4c9-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e4c9-112">See also</span></span>

- [<span data-ttu-id="4e4c9-113">ISymUnmanagedAsyncMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4e4c9-113">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)
