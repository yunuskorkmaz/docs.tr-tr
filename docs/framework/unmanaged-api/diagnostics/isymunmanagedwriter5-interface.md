---
title: ISymUnmanagedWriter5 Arabirimi
ms.date: 03/30/2017
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f5fd7c2bd4fae94d1ef5021b558a04b734803b68
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430563"
---
# <a name="isymunmanagedwriter5-interface"></a><span data-ttu-id="9446a-102">ISymUnmanagedWriter5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9446a-102">ISymUnmanagedWriter5 Interface</span></span>
<span data-ttu-id="9446a-103">Isymunmanagedwriter5 arabirimi.</span><span class="sxs-lookup"><span data-stu-id="9446a-103">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9446a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9446a-104">Syntax</span></span>  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a><span data-ttu-id="9446a-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9446a-105">Methods</span></span>  
 <span data-ttu-id="9446a-106">Bu arabirim, aşağıdaki yöntemleri içerir:</span><span class="sxs-lookup"><span data-stu-id="9446a-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="9446a-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9446a-107">Method</span></span>|<span data-ttu-id="9446a-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9446a-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9446a-109">CloseMapTokensToSourceSpans Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9446a-109">CloseMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|<span data-ttu-id="9446a-110">Belirteç kaynak aralık bilgi eşleme için özel özel veri bölümü kapatın.</span><span class="sxs-lookup"><span data-stu-id="9446a-110">Close the special custom data section for token-to- source span mapping information.</span></span> <span data-ttu-id="9446a-111">Kapalı olduğu sonra daha fazla eşleme bilgi eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="9446a-111">After it is closed, no more mapping information can be added.</span></span>|  
|[<span data-ttu-id="9446a-112">MapTokenToSourceSpan Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9446a-112">MapTokenToSourceSpan Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-maptokentosourcespan-method.md)|<span data-ttu-id="9446a-113">Belirtilen kaynak satırı verilen meta veri simgesi eşlemeleri belirtilen kaynak dosyasında span.</span><span class="sxs-lookup"><span data-stu-id="9446a-113">Maps the given metadata token to the given source line span in the specified source file.</span></span><br /><br /> <span data-ttu-id="9446a-114">Yapılan çağrılar arasında çağrılmalıdır [OpenMapTokensToSourceSpans yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) ve [CloseMapTokensToSourceSpans yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="9446a-114">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>|  
|[<span data-ttu-id="9446a-115">OpenMapTokensToSourceSpans Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9446a-115">OpenMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|<span data-ttu-id="9446a-116">Belirteç kaynak aralık eşleme bilgilerini içine yaymak üzere özel özel veri bölümü açın.</span><span class="sxs-lookup"><span data-stu-id="9446a-116">Open a special custom data section to emit token-to- source span mapping information into.</span></span> <span data-ttu-id="9446a-117">Bu bölümde, bir yöntem zaten açık olan veya bunun tam tersi bir hata olduğunda açılıyor.</span><span class="sxs-lookup"><span data-stu-id="9446a-117">Opening this section when a method is already open, or vice versa, is an error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9446a-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9446a-118">Requirements</span></span>  
 <span data-ttu-id="9446a-119">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9446a-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9446a-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9446a-120">See Also</span></span>  
 [<span data-ttu-id="9446a-121">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9446a-121">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="9446a-122">ISymUnmanagedWriter4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9446a-122">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
