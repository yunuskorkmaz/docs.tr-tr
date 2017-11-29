---
title: "ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f8a0c0a2-a11d-436c-aa85-bc110215cfd6
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f5f23c3fe39adcebcfdfadb9e9c2b639f16330d1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriter5closemaptokenstosourcespans-method"></a><span data-ttu-id="c81e6-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c81e6-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="c81e6-103">Belirteç kaynak aralık bilgi eşleme için özel özel veri bölümü kapatın.</span><span class="sxs-lookup"><span data-stu-id="c81e6-103">Close the special custom data section for token-to-source span mapping information.</span></span> <span data-ttu-id="c81e6-104">Kapalı olduğu sonra daha fazla eşleme bilgi eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="c81e6-104">After it is closed, no more mapping information can be added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c81e6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c81e6-105">Syntax</span></span>  
  
```idl  
HRESULT CloseMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c81e6-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c81e6-106">Return Value</span></span>  
 <span data-ttu-id="c81e6-107">Döndürür `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="c81e6-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c81e6-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c81e6-108">Requirements</span></span>  
 <span data-ttu-id="c81e6-109">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c81e6-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c81e6-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c81e6-110">See Also</span></span>  
 [<span data-ttu-id="c81e6-111">Isymunmanagedwriter5 arabirimi</span><span class="sxs-lookup"><span data-stu-id="c81e6-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
