---
title: "ISymUnmanagedWriter5::MapTokenToSourceSpan Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: d0fbbf61-71c6-4fb1-8c9f-d619ca5d7d68
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: adcdf44582aaf801a39c9beb9831c493a9945fd0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriter5maptokentosourcespan-method"></a><span data-ttu-id="bfaa5-102">ISymUnmanagedWriter5::MapTokenToSourceSpan Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bfaa5-102">ISymUnmanagedWriter5::MapTokenToSourceSpan Method</span></span>
<span data-ttu-id="bfaa5-103">Belirtilen kaynak satırı verilen meta veri simgesi eşlemeleri belirtilen kaynak dosyasında span.</span><span class="sxs-lookup"><span data-stu-id="bfaa5-103">Maps the given metadata token to the given source line span in the specified source file.</span></span>  
  
 <span data-ttu-id="bfaa5-104">Yapılan çağrılar arasında çağrılmalıdır [OpenMapTokensToSourceSpans yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) ve [CloseMapTokensToSourceSpans yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="bfaa5-104">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfaa5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bfaa5-105">Syntax</span></span>  
  
```idl  
HRESULT MapTokenToSourceSpan(    [in] mdToken token,    [in] ISymUnmanagedDocumentWriter* document,    [in] ULONG32 line,    [in] ULONG32 column,    [in] ULONG32 endLine,    [in] ULONG32 endColumn);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bfaa5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bfaa5-106">Parameters</span></span>  
  
|<span data-ttu-id="bfaa5-107">Parametre</span><span class="sxs-lookup"><span data-stu-id="bfaa5-107">Parameter</span></span>|<span data-ttu-id="bfaa5-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bfaa5-108">Description</span></span>|  
|---------------|-----------------|  
|`token`||  
|`document`||  
|`line`||  
|`column`||  
|`endLine`||  
|`endColumn`||  
  
## <a name="return-value"></a><span data-ttu-id="bfaa5-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bfaa5-109">Return Value</span></span>  
 <span data-ttu-id="bfaa5-110">Döndürür `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="bfaa5-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfaa5-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bfaa5-111">Requirements</span></span>  
 <span data-ttu-id="bfaa5-112">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="bfaa5-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfaa5-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bfaa5-113">See Also</span></span>  
 [<span data-ttu-id="bfaa5-114">Isymunmanagedwriter5 arabirimi</span><span class="sxs-lookup"><span data-stu-id="bfaa5-114">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
