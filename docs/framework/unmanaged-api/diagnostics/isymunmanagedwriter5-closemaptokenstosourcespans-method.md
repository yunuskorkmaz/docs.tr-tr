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
ms.workload: dotnet
ms.openlocfilehash: 2f8a89532999f599c8ec595fa709044b7d13a53a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter5closemaptokenstosourcespans-method"></a><span data-ttu-id="00b32-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Yöntemi</span><span class="sxs-lookup"><span data-stu-id="00b32-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="00b32-103">Belirteç kaynak aralık bilgi eşleme için özel özel veri bölümü kapatın.</span><span class="sxs-lookup"><span data-stu-id="00b32-103">Close the special custom data section for token-to-source span mapping information.</span></span> <span data-ttu-id="00b32-104">Kapalı olduğu sonra daha fazla eşleme bilgi eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="00b32-104">After it is closed, no more mapping information can be added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00b32-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="00b32-105">Syntax</span></span>  
  
```idl  
HRESULT CloseMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="00b32-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="00b32-106">Return Value</span></span>  
 <span data-ttu-id="00b32-107">Döndürür `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="00b32-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00b32-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="00b32-108">Requirements</span></span>  
 <span data-ttu-id="00b32-109">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="00b32-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00b32-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="00b32-110">See Also</span></span>  
 [<span data-ttu-id="00b32-111">ISymUnmanagedWriter5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00b32-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
