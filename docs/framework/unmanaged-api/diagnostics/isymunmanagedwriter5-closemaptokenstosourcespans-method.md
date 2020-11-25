---
title: ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Yöntemi
ms.date: 03/30/2017
ms.assetid: f8a0c0a2-a11d-436c-aa85-bc110215cfd6
ms.openlocfilehash: b57174f9f76b174927b8f1997beac3dd1482583a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725917"
---
# <a name="isymunmanagedwriter5closemaptokenstosourcespans-method"></a><span data-ttu-id="fccb4-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fccb4-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Method</span></span>

<span data-ttu-id="fccb4-103">Belirteçten kaynağa yayılma eşleme bilgileri için özel özel veri bölümünü kapatın.</span><span class="sxs-lookup"><span data-stu-id="fccb4-103">Close the special custom data section for token-to-source span mapping information.</span></span> <span data-ttu-id="fccb4-104">Kapatıldıktan sonra, daha fazla eşleme bilgisi eklenemez.</span><span class="sxs-lookup"><span data-stu-id="fccb4-104">After it is closed, no more mapping information can be added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fccb4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="fccb4-105">Syntax</span></span>  
  
```idl  
HRESULT CloseMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="fccb4-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fccb4-106">Return Value</span></span>  

 <span data-ttu-id="fccb4-107">`HRESULT` döndürür.</span><span class="sxs-lookup"><span data-stu-id="fccb4-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fccb4-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fccb4-108">Requirements</span></span>  

 <span data-ttu-id="fccb4-109">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="fccb4-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fccb4-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fccb4-110">See also</span></span>

- [<span data-ttu-id="fccb4-111">ISymUnmanagedWriter5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fccb4-111">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)
