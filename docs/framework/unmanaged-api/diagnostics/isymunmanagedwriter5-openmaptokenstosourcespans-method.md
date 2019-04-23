---
title: ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Yöntemi
ms.date: 03/30/2017
ms.assetid: 93ad2517-b0dc-464c-8688-a58a30eda18d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82dc2ced988f7277c994eb9449e7c26efa5450b7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59222685"
---
# <a name="isymunmanagedwriter5openmaptokenstosourcespans-method"></a><span data-ttu-id="58420-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Yöntemi</span><span class="sxs-lookup"><span data-stu-id="58420-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="58420-103">Belirteç kaynağı eşleştirme bilgileri yaymak için bir özel özel veri bölümünü açın.</span><span class="sxs-lookup"><span data-stu-id="58420-103">Open a special custom data section to emit token-to-source span mapping information into.</span></span> <span data-ttu-id="58420-104">Bu bölümde, bir yöntem zaten açık olan veya tam tersi bir hata olduğunda açılıyor.</span><span class="sxs-lookup"><span data-stu-id="58420-104">Opening this section when a method is already open, or vice versa, is an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58420-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="58420-105">Syntax</span></span>  
  
```idl  
HRESULT OpenMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="58420-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="58420-106">Return Value</span></span>  
 <span data-ttu-id="58420-107">Döndürür `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="58420-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58420-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="58420-108">Requirements</span></span>  
 <span data-ttu-id="58420-109">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="58420-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58420-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58420-110">See also</span></span>

- [<span data-ttu-id="58420-111">ISymUnmanagedWriter5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="58420-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
