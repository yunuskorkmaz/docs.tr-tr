---
title: "ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 93ad2517-b0dc-464c-8688-a58a30eda18d
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f226a71ac6381c8ca04093beb1d9772d6e6c75e3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriter5openmaptokenstosourcespans-method"></a><span data-ttu-id="5a6b8-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5a6b8-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="5a6b8-103">Belirteç kaynak aralık eşleme bilgilerini içine yaymak üzere özel özel veri bölümü açın.</span><span class="sxs-lookup"><span data-stu-id="5a6b8-103">Open a special custom data section to emit token-to-source span mapping information into.</span></span> <span data-ttu-id="5a6b8-104">Bu bölümde, bir yöntem zaten açık olan veya bunun tam tersi bir hata olduğunda açılıyor.</span><span class="sxs-lookup"><span data-stu-id="5a6b8-104">Opening this section when a method is already open, or vice versa, is an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a6b8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5a6b8-105">Syntax</span></span>  
  
```idl  
HRESULT OpenMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="5a6b8-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5a6b8-106">Return Value</span></span>  
 <span data-ttu-id="5a6b8-107">Döndürür `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="5a6b8-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a6b8-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5a6b8-108">Requirements</span></span>  
 <span data-ttu-id="5a6b8-109">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5a6b8-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a6b8-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5a6b8-110">See Also</span></span>  
 [<span data-ttu-id="5a6b8-111">Isymunmanagedwriter5 arabirimi</span><span class="sxs-lookup"><span data-stu-id="5a6b8-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
