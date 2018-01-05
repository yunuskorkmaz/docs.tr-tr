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
ms.workload: dotnet
ms.openlocfilehash: cb283198de5621748b37fe8e22f2fbc408754ad6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter5openmaptokenstosourcespans-method"></a><span data-ttu-id="72f9e-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Yöntemi</span><span class="sxs-lookup"><span data-stu-id="72f9e-102">ISymUnmanagedWriter5::OpenMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="72f9e-103">Belirteç kaynak aralık eşleme bilgilerini içine yaymak üzere özel özel veri bölümü açın.</span><span class="sxs-lookup"><span data-stu-id="72f9e-103">Open a special custom data section to emit token-to-source span mapping information into.</span></span> <span data-ttu-id="72f9e-104">Bu bölümde, bir yöntem zaten açık olan veya bunun tam tersi bir hata olduğunda açılıyor.</span><span class="sxs-lookup"><span data-stu-id="72f9e-104">Opening this section when a method is already open, or vice versa, is an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72f9e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="72f9e-105">Syntax</span></span>  
  
```idl  
HRESULT OpenMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="72f9e-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="72f9e-106">Return Value</span></span>  
 <span data-ttu-id="72f9e-107">Döndürür `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="72f9e-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72f9e-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="72f9e-108">Requirements</span></span>  
 <span data-ttu-id="72f9e-109">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="72f9e-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72f9e-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="72f9e-110">See Also</span></span>  
 [<span data-ttu-id="72f9e-111">ISymUnmanagedWriter5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="72f9e-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
