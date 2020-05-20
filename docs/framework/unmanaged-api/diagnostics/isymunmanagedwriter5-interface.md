---
title: ISymUnmanagedWriter5 Arabirimi
ms.date: 03/30/2017
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
ms.openlocfilehash: bdc630c3c94c7d03b736efa0a95665f10aac7c6e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609436"
---
# <a name="isymunmanagedwriter5-interface"></a><span data-ttu-id="9924b-102">ISymUnmanagedWriter5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9924b-102">ISymUnmanagedWriter5 Interface</span></span>
<span data-ttu-id="9924b-103">ISymUnmanagedWriter5 arabirimi.</span><span class="sxs-lookup"><span data-stu-id="9924b-103">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9924b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9924b-104">Syntax</span></span>  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a><span data-ttu-id="9924b-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9924b-105">Methods</span></span>  
 <span data-ttu-id="9924b-106">Bu arabirim aşağıdaki yöntemleri içerir:</span><span class="sxs-lookup"><span data-stu-id="9924b-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="9924b-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9924b-107">Method</span></span>|<span data-ttu-id="9924b-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9924b-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9924b-109">CloseMapTokensToSourceSpans Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9924b-109">CloseMapTokensToSourceSpans Method</span></span>](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|<span data-ttu-id="9924b-110">Belirteçten kaynağa yayılma eşleme bilgileri için özel özel veri bölümünü kapatın.</span><span class="sxs-lookup"><span data-stu-id="9924b-110">Close the special custom data section for token-to- source span mapping information.</span></span> <span data-ttu-id="9924b-111">Kapatıldıktan sonra, daha fazla eşleme bilgisi eklenemez.</span><span class="sxs-lookup"><span data-stu-id="9924b-111">After it is closed, no more mapping information can be added.</span></span>|  
|[<span data-ttu-id="9924b-112">MapTokenToSourceSpan Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9924b-112">MapTokenToSourceSpan Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-maptokentosourcespan-method.md)|<span data-ttu-id="9924b-113">Verilen meta veri belirtecini belirtilen kaynak dosyadaki verilen kaynak satır aralığına eşler.</span><span class="sxs-lookup"><span data-stu-id="9924b-113">Maps the given metadata token to the given source line span in the specified source file.</span></span><br /><br /> <span data-ttu-id="9924b-114">[OpenMapTokensToSourceSpans Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) ve [CloseMapTokensToSourceSpans Yöntemi](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)çağrıları arasında çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9924b-114">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>|  
|[<span data-ttu-id="9924b-115">OpenMapTokensToSourceSpans Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9924b-115">OpenMapTokensToSourceSpans Method</span></span>](isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|<span data-ttu-id="9924b-116">Belirteçten kaynağa yayılma eşleme bilgilerini içine göstermek için özel bir özel veri bölümünü açın.</span><span class="sxs-lookup"><span data-stu-id="9924b-116">Open a special custom data section to emit token-to- source span mapping information into.</span></span> <span data-ttu-id="9924b-117">Bir yöntem zaten açık olduğunda veya bunun tersi durumda, bu bölümü açmak bir hatadır.</span><span class="sxs-lookup"><span data-stu-id="9924b-117">Opening this section when a method is already open, or vice versa, is an error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9924b-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9924b-118">Requirements</span></span>  
 <span data-ttu-id="9924b-119">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="9924b-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9924b-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9924b-120">See also</span></span>

- [<span data-ttu-id="9924b-121">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9924b-121">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="9924b-122">ISymUnmanagedWriter4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9924b-122">ISymUnmanagedWriter4 Interface</span></span>](isymunmanagedwriter4-interface.md)
