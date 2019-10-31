---
title: ISymUnmanagedWriter5::MapTokenToSourceSpan Yöntemi
ms.date: 03/30/2017
ms.assetid: d0fbbf61-71c6-4fb1-8c9f-d619ca5d7d68
ms.openlocfilehash: 876804e7b825443116b1f44a02a685a73153915c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121619"
---
# <a name="isymunmanagedwriter5maptokentosourcespan-method"></a><span data-ttu-id="c2ec7-102">ISymUnmanagedWriter5::MapTokenToSourceSpan Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c2ec7-102">ISymUnmanagedWriter5::MapTokenToSourceSpan Method</span></span>
<span data-ttu-id="c2ec7-103">Verilen meta veri belirtecini belirtilen kaynak dosyadaki verilen kaynak satır aralığına eşler.</span><span class="sxs-lookup"><span data-stu-id="c2ec7-103">Maps the given metadata token to the given source line span in the specified source file.</span></span>  
  
 <span data-ttu-id="c2ec7-104">[OpenMapTokensToSourceSpans Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) ve [CloseMapTokensToSourceSpans Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)çağrıları arasında çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c2ec7-104">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2ec7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c2ec7-105">Syntax</span></span>  
  
```idl  
HRESULT MapTokenToSourceSpan(    [in] mdToken token,    [in] ISymUnmanagedDocumentWriter* document,    [in] ULONG32 line,    [in] ULONG32 column,    [in] ULONG32 endLine,    [in] ULONG32 endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2ec7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c2ec7-106">Parameters</span></span>  
  
|<span data-ttu-id="c2ec7-107">Parametre</span><span class="sxs-lookup"><span data-stu-id="c2ec7-107">Parameter</span></span>|<span data-ttu-id="c2ec7-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c2ec7-108">Description</span></span>|  
|---------------|-----------------|  
|`token`||  
|`document`||  
|`line`||  
|`column`||  
|`endLine`||  
|`endColumn`||  
  
## <a name="return-value"></a><span data-ttu-id="c2ec7-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c2ec7-109">Return Value</span></span>  
 <span data-ttu-id="c2ec7-110">`HRESULT`döndürür.</span><span class="sxs-lookup"><span data-stu-id="c2ec7-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2ec7-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c2ec7-111">Requirements</span></span>  
 <span data-ttu-id="c2ec7-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="c2ec7-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2ec7-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2ec7-113">See also</span></span>

- [<span data-ttu-id="c2ec7-114">ISymUnmanagedWriter5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c2ec7-114">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
