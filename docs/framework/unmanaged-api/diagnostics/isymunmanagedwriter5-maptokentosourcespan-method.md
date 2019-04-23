---
title: ISymUnmanagedWriter5::MapTokenToSourceSpan Yöntemi
ms.date: 03/30/2017
ms.assetid: d0fbbf61-71c6-4fb1-8c9f-d619ca5d7d68
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08c219dd033b39fc07159875b184cdf70e3aa3ed
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59181525"
---
# <a name="isymunmanagedwriter5maptokentosourcespan-method"></a><span data-ttu-id="0149b-102">ISymUnmanagedWriter5::MapTokenToSourceSpan Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0149b-102">ISymUnmanagedWriter5::MapTokenToSourceSpan Method</span></span>
<span data-ttu-id="0149b-103">Haritalar belirtilen kaynak dosyasında belirtilen kaynak satırı verilen bir meta veri belirteci yayılır.</span><span class="sxs-lookup"><span data-stu-id="0149b-103">Maps the given metadata token to the given source line span in the specified source file.</span></span>  
  
 <span data-ttu-id="0149b-104">Yapılan çağrılar arasında çağrılmalıdır [OpenMapTokensToSourceSpans yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) ve [CloseMapTokensToSourceSpans yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="0149b-104">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0149b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0149b-105">Syntax</span></span>  
  
```idl  
HRESULT MapTokenToSourceSpan(    [in] mdToken token,    [in] ISymUnmanagedDocumentWriter* document,    [in] ULONG32 line,    [in] ULONG32 column,    [in] ULONG32 endLine,    [in] ULONG32 endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0149b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0149b-106">Parameters</span></span>  
  
|<span data-ttu-id="0149b-107">Parametre</span><span class="sxs-lookup"><span data-stu-id="0149b-107">Parameter</span></span>|<span data-ttu-id="0149b-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0149b-108">Description</span></span>|  
|---------------|-----------------|  
|`token`||  
|`document`||  
|`line`||  
|`column`||  
|`endLine`||  
|`endColumn`||  
  
## <a name="return-value"></a><span data-ttu-id="0149b-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0149b-109">Return Value</span></span>  
 <span data-ttu-id="0149b-110">Döndürür `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="0149b-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0149b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0149b-111">Requirements</span></span>  
 <span data-ttu-id="0149b-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0149b-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0149b-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0149b-113">See also</span></span>

- [<span data-ttu-id="0149b-114">ISymUnmanagedWriter5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0149b-114">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
