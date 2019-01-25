---
title: ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Yöntemi
ms.date: 03/30/2017
ms.assetid: f8a0c0a2-a11d-436c-aa85-bc110215cfd6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce4b41854d5d9324169b1873f431ef81c0a4c5be
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54677925"
---
# <a name="isymunmanagedwriter5closemaptokenstosourcespans-method"></a><span data-ttu-id="2d9f0-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2d9f0-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="2d9f0-103">Eşleme bilgileri belirteci kaynak yayılma için özel bir özel veri bölümü kapatın.</span><span class="sxs-lookup"><span data-stu-id="2d9f0-103">Close the special custom data section for token-to-source span mapping information.</span></span> <span data-ttu-id="2d9f0-104">Daha fazla bilgi eşleme, kapatıldıktan sonra eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="2d9f0-104">After it is closed, no more mapping information can be added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d9f0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2d9f0-105">Syntax</span></span>  
  
```idl  
HRESULT CloseMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="2d9f0-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2d9f0-106">Return Value</span></span>  
 <span data-ttu-id="2d9f0-107">Döndürür `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="2d9f0-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d9f0-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2d9f0-108">Requirements</span></span>  
 <span data-ttu-id="2d9f0-109">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2d9f0-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d9f0-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d9f0-110">See also</span></span>
- [<span data-ttu-id="2d9f0-111">ISymUnmanagedWriter5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2d9f0-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
