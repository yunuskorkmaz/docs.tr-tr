---
title: ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Yöntemi
ms.date: 03/30/2017
ms.assetid: f8a0c0a2-a11d-436c-aa85-bc110215cfd6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b3dea6b9710f1ee5ccf8c51261f59b2de026f5e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127783"
---
# <a name="isymunmanagedwriter5closemaptokenstosourcespans-method"></a><span data-ttu-id="be3f5-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Yöntemi</span><span class="sxs-lookup"><span data-stu-id="be3f5-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="be3f5-103">Eşleme bilgileri belirteci kaynak yayılma için özel bir özel veri bölümü kapatın.</span><span class="sxs-lookup"><span data-stu-id="be3f5-103">Close the special custom data section for token-to-source span mapping information.</span></span> <span data-ttu-id="be3f5-104">Daha fazla bilgi eşleme, kapatıldıktan sonra eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="be3f5-104">After it is closed, no more mapping information can be added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be3f5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="be3f5-105">Syntax</span></span>  
  
```idl  
HRESULT CloseMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="be3f5-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="be3f5-106">Return Value</span></span>  
 <span data-ttu-id="be3f5-107">Döndürür `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="be3f5-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be3f5-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="be3f5-108">Requirements</span></span>  
 <span data-ttu-id="be3f5-109">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="be3f5-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be3f5-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be3f5-110">See also</span></span>

- [<span data-ttu-id="be3f5-111">ISymUnmanagedWriter5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="be3f5-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
