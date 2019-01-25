---
title: ISymUnmanagedWriter5::MapTokenToSourceSpan Yöntemi
ms.date: 03/30/2017
ms.assetid: d0fbbf61-71c6-4fb1-8c9f-d619ca5d7d68
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 158ff204d57c3b08ced91d397ef71f24c5f44248
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54499216"
---
# <a name="isymunmanagedwriter5maptokentosourcespan-method"></a><span data-ttu-id="62976-102">ISymUnmanagedWriter5::MapTokenToSourceSpan Yöntemi</span><span class="sxs-lookup"><span data-stu-id="62976-102">ISymUnmanagedWriter5::MapTokenToSourceSpan Method</span></span>
<span data-ttu-id="62976-103">Haritalar belirtilen kaynak dosyasında belirtilen kaynak satırı verilen bir meta veri belirteci yayılır.</span><span class="sxs-lookup"><span data-stu-id="62976-103">Maps the given metadata token to the given source line span in the specified source file.</span></span>  
  
 <span data-ttu-id="62976-104">Yapılan çağrılar arasında çağrılmalıdır [OpenMapTokensToSourceSpans yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) ve [CloseMapTokensToSourceSpans yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="62976-104">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62976-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="62976-105">Syntax</span></span>  
  
```idl  
HRESULT MapTokenToSourceSpan(    [in] mdToken token,    [in] ISymUnmanagedDocumentWriter* document,    [in] ULONG32 line,    [in] ULONG32 column,    [in] ULONG32 endLine,    [in] ULONG32 endColumn);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="62976-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="62976-106">Parameters</span></span>  
  
|<span data-ttu-id="62976-107">Parametre</span><span class="sxs-lookup"><span data-stu-id="62976-107">Parameter</span></span>|<span data-ttu-id="62976-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62976-108">Description</span></span>|  
|---------------|-----------------|  
|`token`||  
|`document`||  
|`line`||  
|`column`||  
|`endLine`||  
|`endColumn`||  
  
## <a name="return-value"></a><span data-ttu-id="62976-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="62976-109">Return Value</span></span>  
 <span data-ttu-id="62976-110">Döndürür `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="62976-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62976-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="62976-111">Requirements</span></span>  
 <span data-ttu-id="62976-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="62976-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62976-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62976-113">See also</span></span>
- [<span data-ttu-id="62976-114">ISymUnmanagedWriter5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="62976-114">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
