---
title: ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Yöntemi
ms.date: 03/30/2017
ms.assetid: 93ad2517-b0dc-464c-8688-a58a30eda18d
ms.openlocfilehash: 82b46ea315009b65254735d44e355154b83b22e2
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609501"
---
# <a name="isymunmanagedwriter5openmaptokenstosourcespans-method"></a><span data-ttu-id="6d91e-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6d91e-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="6d91e-103">Belirteçten kaynağa yayılma eşleme bilgilerini içine göstermek için özel bir özel veri bölümünü açın.</span><span class="sxs-lookup"><span data-stu-id="6d91e-103">Open a special custom data section to emit token-to-source span mapping information into.</span></span> <span data-ttu-id="6d91e-104">Bir yöntem zaten açık olduğunda veya bunun tersi durumda, bu bölümü açmak bir hatadır.</span><span class="sxs-lookup"><span data-stu-id="6d91e-104">Opening this section when a method is already open, or vice versa, is an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d91e-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="6d91e-105">Syntax</span></span>  
  
```idl  
HRESULT OpenMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="6d91e-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6d91e-106">Return Value</span></span>  
 <span data-ttu-id="6d91e-107">`HRESULT` döndürür.</span><span class="sxs-lookup"><span data-stu-id="6d91e-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d91e-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6d91e-108">Requirements</span></span>  
 <span data-ttu-id="6d91e-109">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="6d91e-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d91e-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d91e-110">See also</span></span>

- [<span data-ttu-id="6d91e-111">ISymUnmanagedWriter5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6d91e-111">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)
