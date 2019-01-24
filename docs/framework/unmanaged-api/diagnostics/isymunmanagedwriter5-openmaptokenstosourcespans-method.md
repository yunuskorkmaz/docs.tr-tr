---
title: ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Yöntemi
ms.date: 03/30/2017
ms.assetid: 93ad2517-b0dc-464c-8688-a58a30eda18d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60c1984e6193481efdaaeb82a2bc025aef67a33f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54534452"
---
# <a name="isymunmanagedwriter5openmaptokenstosourcespans-method"></a><span data-ttu-id="bd7f2-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bd7f2-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="bd7f2-103">Belirteç kaynağı eşleştirme bilgileri yaymak için bir özel özel veri bölümünü açın.</span><span class="sxs-lookup"><span data-stu-id="bd7f2-103">Open a special custom data section to emit token-to-source span mapping information into.</span></span> <span data-ttu-id="bd7f2-104">Bu bölümde, bir yöntem zaten açık olan veya tam tersi bir hata olduğunda açılıyor.</span><span class="sxs-lookup"><span data-stu-id="bd7f2-104">Opening this section when a method is already open, or vice versa, is an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd7f2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bd7f2-105">Syntax</span></span>  
  
```idl  
HRESULT OpenMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="bd7f2-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bd7f2-106">Return Value</span></span>  
 <span data-ttu-id="bd7f2-107">Döndürür `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="bd7f2-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd7f2-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bd7f2-108">Requirements</span></span>  
 <span data-ttu-id="bd7f2-109">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="bd7f2-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd7f2-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd7f2-110">See also</span></span>
- [<span data-ttu-id="bd7f2-111">ISymUnmanagedWriter5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bd7f2-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
