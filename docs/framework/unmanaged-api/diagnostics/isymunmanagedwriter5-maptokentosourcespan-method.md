---
title: ISymUnmanagedWriter5::MapTokenToSourceSpan Yöntemi
ms.date: 03/30/2017
ms.assetid: d0fbbf61-71c6-4fb1-8c9f-d619ca5d7d68
ms.openlocfilehash: 0f00dd34ffbdd58a46260132d8d7ace74ec2f294
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501683"
---
# <a name="isymunmanagedwriter5maptokentosourcespan-method"></a><span data-ttu-id="e61f7-102">ISymUnmanagedWriter5::MapTokenToSourceSpan Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e61f7-102">ISymUnmanagedWriter5::MapTokenToSourceSpan Method</span></span>
<span data-ttu-id="e61f7-103">Verilen meta veri belirtecini belirtilen kaynak dosyadaki verilen kaynak satır aralığına eşler.</span><span class="sxs-lookup"><span data-stu-id="e61f7-103">Maps the given metadata token to the given source line span in the specified source file.</span></span>  
  
 <span data-ttu-id="e61f7-104">[OpenMapTokensToSourceSpans Yöntemi](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) ve [CloseMapTokensToSourceSpans Yöntemi](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)çağrıları arasında çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e61f7-104">Must be called between calls to [OpenMapTokensToSourceSpans Method](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e61f7-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e61f7-105">Syntax</span></span>  
  
```idl  
HRESULT MapTokenToSourceSpan(    [in] mdToken token,    [in] ISymUnmanagedDocumentWriter* document,    [in] ULONG32 line,    [in] ULONG32 column,    [in] ULONG32 endLine,    [in] ULONG32 endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e61f7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e61f7-106">Parameters</span></span>  
  
|<span data-ttu-id="e61f7-107">Parametre</span><span class="sxs-lookup"><span data-stu-id="e61f7-107">Parameter</span></span>|<span data-ttu-id="e61f7-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e61f7-108">Description</span></span>|  
|---------------|-----------------|  
|`token`||  
|`document`||  
|`line`||  
|`column`||  
|`endLine`||  
|`endColumn`||  
  
## <a name="return-value"></a><span data-ttu-id="e61f7-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e61f7-109">Return Value</span></span>  
 <span data-ttu-id="e61f7-110">`HRESULT` döndürür.</span><span class="sxs-lookup"><span data-stu-id="e61f7-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e61f7-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e61f7-111">Requirements</span></span>  
 <span data-ttu-id="e61f7-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e61f7-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e61f7-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e61f7-113">See also</span></span>

- [<span data-ttu-id="e61f7-114">ISymUnmanagedWriter5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e61f7-114">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)
