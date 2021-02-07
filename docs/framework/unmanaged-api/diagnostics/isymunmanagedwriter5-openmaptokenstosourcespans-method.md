---
description: 'Şu konuda daha fazla bilgi edinin: ISymUnmanagedWriter5:: OpenMapTokensToSourceSpans Yöntemi'
title: ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Yöntemi
ms.date: 03/30/2017
ms.assetid: 93ad2517-b0dc-464c-8688-a58a30eda18d
ms.openlocfilehash: 1feeecaf943e3eed228ced2b0c968f3fe4b49f62
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761518"
---
# <a name="isymunmanagedwriter5openmaptokenstosourcespans-method"></a><span data-ttu-id="d0852-103">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d0852-103">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Method</span></span>

<span data-ttu-id="d0852-104">Belirteçten kaynağa yayılma eşleme bilgilerini içine göstermek için özel bir özel veri bölümünü açın.</span><span class="sxs-lookup"><span data-stu-id="d0852-104">Open a special custom data section to emit token-to-source span mapping information into.</span></span> <span data-ttu-id="d0852-105">Bir yöntem zaten açık olduğunda veya bunun tersi durumda, bu bölümü açmak bir hatadır.</span><span class="sxs-lookup"><span data-stu-id="d0852-105">Opening this section when a method is already open, or vice versa, is an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0852-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="d0852-106">Syntax</span></span>  
  
```idl  
HRESULT OpenMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="d0852-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d0852-107">Return Value</span></span>  

 <span data-ttu-id="d0852-108">`HRESULT` döndürür.</span><span class="sxs-lookup"><span data-stu-id="d0852-108">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0852-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d0852-109">Requirements</span></span>  

 <span data-ttu-id="d0852-110">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="d0852-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0852-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0852-111">See also</span></span>

- [<span data-ttu-id="d0852-112">ISymUnmanagedWriter5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d0852-112">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)
