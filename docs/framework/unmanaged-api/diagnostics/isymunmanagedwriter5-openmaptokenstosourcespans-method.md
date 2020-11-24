---
title: ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Yöntemi
ms.date: 03/30/2017
ms.assetid: 93ad2517-b0dc-464c-8688-a58a30eda18d
ms.openlocfilehash: 95976e2f331252c88eab717e184abc284842e3b3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683270"
---
# <a name="isymunmanagedwriter5openmaptokenstosourcespans-method"></a><span data-ttu-id="2e8d5-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2e8d5-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Method</span></span>

<span data-ttu-id="2e8d5-103">Belirteçten kaynağa yayılma eşleme bilgilerini içine göstermek için özel bir özel veri bölümünü açın.</span><span class="sxs-lookup"><span data-stu-id="2e8d5-103">Open a special custom data section to emit token-to-source span mapping information into.</span></span> <span data-ttu-id="2e8d5-104">Bir yöntem zaten açık olduğunda veya bunun tersi durumda, bu bölümü açmak bir hatadır.</span><span class="sxs-lookup"><span data-stu-id="2e8d5-104">Opening this section when a method is already open, or vice versa, is an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e8d5-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="2e8d5-105">Syntax</span></span>  
  
```idl  
HRESULT OpenMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="2e8d5-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2e8d5-106">Return Value</span></span>  

 <span data-ttu-id="2e8d5-107">`HRESULT` döndürür.</span><span class="sxs-lookup"><span data-stu-id="2e8d5-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e8d5-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2e8d5-108">Requirements</span></span>  

 <span data-ttu-id="2e8d5-109">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2e8d5-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e8d5-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e8d5-110">See also</span></span>

- [<span data-ttu-id="2e8d5-111">ISymUnmanagedWriter5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2e8d5-111">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)
