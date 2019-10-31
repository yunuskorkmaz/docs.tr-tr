---
title: ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Yöntemi
ms.date: 03/30/2017
ms.assetid: 93ad2517-b0dc-464c-8688-a58a30eda18d
ms.openlocfilehash: 004e1ddae8a6c0262846422a2eeb4314a4c82f65
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121609"
---
# <a name="isymunmanagedwriter5openmaptokenstosourcespans-method"></a><span data-ttu-id="eda54-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eda54-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="eda54-103">Belirteçten kaynağa yayılma eşleme bilgilerini içine göstermek için özel bir özel veri bölümünü açın.</span><span class="sxs-lookup"><span data-stu-id="eda54-103">Open a special custom data section to emit token-to-source span mapping information into.</span></span> <span data-ttu-id="eda54-104">Bir yöntem zaten açık olduğunda veya bunun tersi durumda, bu bölümü açmak bir hatadır.</span><span class="sxs-lookup"><span data-stu-id="eda54-104">Opening this section when a method is already open, or vice versa, is an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eda54-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eda54-105">Syntax</span></span>  
  
```idl  
HRESULT OpenMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="eda54-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="eda54-106">Return Value</span></span>  
 <span data-ttu-id="eda54-107">`HRESULT`döndürür.</span><span class="sxs-lookup"><span data-stu-id="eda54-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eda54-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eda54-108">Requirements</span></span>  
 <span data-ttu-id="eda54-109">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="eda54-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eda54-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eda54-110">See also</span></span>

- [<span data-ttu-id="eda54-111">ISymUnmanagedWriter5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eda54-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
