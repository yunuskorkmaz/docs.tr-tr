---
title: ISymUnmanagedWriter5 Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c5ac543ad98cc14382f0fb6d0d04fafa7136136e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriter5-interface"></a><span data-ttu-id="661dc-102">ISymUnmanagedWriter5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="661dc-102">ISymUnmanagedWriter5 Interface</span></span>
<span data-ttu-id="661dc-103">Isymunmanagedwriter5 arabirimi.</span><span class="sxs-lookup"><span data-stu-id="661dc-103">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="661dc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="661dc-104">Syntax</span></span>  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a><span data-ttu-id="661dc-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="661dc-105">Methods</span></span>  
 <span data-ttu-id="661dc-106">Bu arabirim, aşağıdaki yöntemleri içerir:</span><span class="sxs-lookup"><span data-stu-id="661dc-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="661dc-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="661dc-107">Method</span></span>|<span data-ttu-id="661dc-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="661dc-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="661dc-109">CloseMapTokensToSourceSpans yöntemi</span><span class="sxs-lookup"><span data-stu-id="661dc-109">CloseMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|<span data-ttu-id="661dc-110">Belirteç kaynak aralık bilgi eşleme için özel özel veri bölümü kapatın.</span><span class="sxs-lookup"><span data-stu-id="661dc-110">Close the special custom data section for token-to- source span mapping information.</span></span> <span data-ttu-id="661dc-111">Kapalı olduğu sonra daha fazla eşleme bilgi eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="661dc-111">After it is closed, no more mapping information can be added.</span></span>|  
|[<span data-ttu-id="661dc-112">MapTokenToSourceSpan yöntemi</span><span class="sxs-lookup"><span data-stu-id="661dc-112">MapTokenToSourceSpan Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-maptokentosourcespan-method.md)|<span data-ttu-id="661dc-113">Belirtilen kaynak satırı verilen meta veri simgesi eşlemeleri belirtilen kaynak dosyasında span.</span><span class="sxs-lookup"><span data-stu-id="661dc-113">Maps the given metadata token to the given source line span in the specified source file.</span></span><br /><br /> <span data-ttu-id="661dc-114">Yapılan çağrılar arasında çağrılmalıdır [OpenMapTokensToSourceSpans yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) ve [CloseMapTokensToSourceSpans yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="661dc-114">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>|  
|[<span data-ttu-id="661dc-115">OpenMapTokensToSourceSpans yöntemi</span><span class="sxs-lookup"><span data-stu-id="661dc-115">OpenMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|<span data-ttu-id="661dc-116">Belirteç kaynak aralık eşleme bilgilerini içine yaymak üzere özel özel veri bölümü açın.</span><span class="sxs-lookup"><span data-stu-id="661dc-116">Open a special custom data section to emit token-to- source span mapping information into.</span></span> <span data-ttu-id="661dc-117">Bu bölümde, bir yöntem zaten açık olan veya bunun tam tersi bir hata olduğunda açılıyor.</span><span class="sxs-lookup"><span data-stu-id="661dc-117">Opening this section when a method is already open, or vice versa, is an error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="661dc-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="661dc-118">Requirements</span></span>  
 <span data-ttu-id="661dc-119">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="661dc-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="661dc-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="661dc-120">See Also</span></span>  
 [<span data-ttu-id="661dc-121">Tanılama sembol deposu arabirimleri</span><span class="sxs-lookup"><span data-stu-id="661dc-121">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="661dc-122">Isymunmanagedwriter4 arabirimi</span><span class="sxs-lookup"><span data-stu-id="661dc-122">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
