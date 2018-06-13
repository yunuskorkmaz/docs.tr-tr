---
title: ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Yöntemi
ms.date: 03/30/2017
ms.assetid: 93ad2517-b0dc-464c-8688-a58a30eda18d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d3bc8b00b568f96cd55b7811f310d34c1ff700d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428654"
---
# <a name="isymunmanagedwriter5openmaptokenstosourcespans-method"></a><span data-ttu-id="2053a-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2053a-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="2053a-103">Belirteç kaynak aralık eşleme bilgilerini içine yaymak üzere özel özel veri bölümü açın.</span><span class="sxs-lookup"><span data-stu-id="2053a-103">Open a special custom data section to emit token-to-source span mapping information into.</span></span> <span data-ttu-id="2053a-104">Bu bölümde, bir yöntem zaten açık olan veya bunun tam tersi bir hata olduğunda açılıyor.</span><span class="sxs-lookup"><span data-stu-id="2053a-104">Opening this section when a method is already open, or vice versa, is an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2053a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2053a-105">Syntax</span></span>  
  
```idl  
HRESULT OpenMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="2053a-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2053a-106">Return Value</span></span>  
 <span data-ttu-id="2053a-107">Döndürür `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="2053a-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2053a-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2053a-108">Requirements</span></span>  
 <span data-ttu-id="2053a-109">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2053a-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2053a-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2053a-110">See Also</span></span>  
 [<span data-ttu-id="2053a-111">ISymUnmanagedWriter5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2053a-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
