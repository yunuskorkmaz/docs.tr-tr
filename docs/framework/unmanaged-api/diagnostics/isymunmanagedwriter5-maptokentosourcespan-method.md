---
description: 'Şu konuda daha fazla bilgi edinin: ISymUnmanagedWriter5:: MapTokenToSourceSpan yöntemi'
title: ISymUnmanagedWriter5::MapTokenToSourceSpan Yöntemi
ms.date: 03/30/2017
ms.assetid: d0fbbf61-71c6-4fb1-8c9f-d619ca5d7d68
ms.openlocfilehash: b30d8051f5d2872488639ce999cccd4248af367f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761622"
---
# <a name="isymunmanagedwriter5maptokentosourcespan-method"></a><span data-ttu-id="877ba-103">ISymUnmanagedWriter5::MapTokenToSourceSpan Yöntemi</span><span class="sxs-lookup"><span data-stu-id="877ba-103">ISymUnmanagedWriter5::MapTokenToSourceSpan Method</span></span>

<span data-ttu-id="877ba-104">Verilen meta veri belirtecini belirtilen kaynak dosyadaki verilen kaynak satır aralığına eşler.</span><span class="sxs-lookup"><span data-stu-id="877ba-104">Maps the given metadata token to the given source line span in the specified source file.</span></span>  
  
 <span data-ttu-id="877ba-105">[OpenMapTokensToSourceSpans Yöntemi](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) ve [CloseMapTokensToSourceSpans Yöntemi](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)çağrıları arasında çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="877ba-105">Must be called between calls to [OpenMapTokensToSourceSpans Method](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="877ba-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="877ba-106">Syntax</span></span>  
  
```idl  
HRESULT MapTokenToSourceSpan(    [in] mdToken token,    [in] ISymUnmanagedDocumentWriter* document,    [in] ULONG32 line,    [in] ULONG32 column,    [in] ULONG32 endLine,    [in] ULONG32 endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="877ba-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="877ba-107">Parameters</span></span>  
  
|<span data-ttu-id="877ba-108">Parametre</span><span class="sxs-lookup"><span data-stu-id="877ba-108">Parameter</span></span>|<span data-ttu-id="877ba-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="877ba-109">Description</span></span>|  
|---------------|-----------------|  
|`token`||  
|`document`||  
|`line`||  
|`column`||  
|`endLine`||  
|`endColumn`||  
  
## <a name="return-value"></a><span data-ttu-id="877ba-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="877ba-110">Return Value</span></span>  

 <span data-ttu-id="877ba-111">`HRESULT` döndürür.</span><span class="sxs-lookup"><span data-stu-id="877ba-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="877ba-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="877ba-112">Requirements</span></span>  

 <span data-ttu-id="877ba-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="877ba-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="877ba-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="877ba-114">See also</span></span>

- [<span data-ttu-id="877ba-115">ISymUnmanagedWriter5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="877ba-115">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)
