---
title: ISymUnmanagedWriter5 Arabirimi
ms.date: 03/30/2017
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6ed8c6e61c558a4bc9e3f92d559615ac93ecff8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59144241"
---
# <a name="isymunmanagedwriter5-interface"></a><span data-ttu-id="5ae67-102">ISymUnmanagedWriter5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5ae67-102">ISymUnmanagedWriter5 Interface</span></span>
<span data-ttu-id="5ae67-103">Isymunmanagedwriter5 arabirimi.</span><span class="sxs-lookup"><span data-stu-id="5ae67-103">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ae67-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ae67-104">Syntax</span></span>  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a><span data-ttu-id="5ae67-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5ae67-105">Methods</span></span>  
 <span data-ttu-id="5ae67-106">Bu arabirimi aşağıdaki yöntemleri içerir:</span><span class="sxs-lookup"><span data-stu-id="5ae67-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="5ae67-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="5ae67-107">Method</span></span>|<span data-ttu-id="5ae67-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ae67-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5ae67-109">CloseMapTokensToSourceSpans Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5ae67-109">CloseMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|<span data-ttu-id="5ae67-110">Eşleme bilgileri belirteci kaynak yayılma için özel bir özel veri bölümü kapatın.</span><span class="sxs-lookup"><span data-stu-id="5ae67-110">Close the special custom data section for token-to- source span mapping information.</span></span> <span data-ttu-id="5ae67-111">Daha fazla bilgi eşleme, kapatıldıktan sonra eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="5ae67-111">After it is closed, no more mapping information can be added.</span></span>|  
|[<span data-ttu-id="5ae67-112">MapTokenToSourceSpan Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5ae67-112">MapTokenToSourceSpan Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-maptokentosourcespan-method.md)|<span data-ttu-id="5ae67-113">Haritalar belirtilen kaynak dosyasında belirtilen kaynak satırı verilen bir meta veri belirteci yayılır.</span><span class="sxs-lookup"><span data-stu-id="5ae67-113">Maps the given metadata token to the given source line span in the specified source file.</span></span><br /><br /> <span data-ttu-id="5ae67-114">Yapılan çağrılar arasında çağrılmalıdır [OpenMapTokensToSourceSpans yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) ve [CloseMapTokensToSourceSpans yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="5ae67-114">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>|  
|[<span data-ttu-id="5ae67-115">OpenMapTokensToSourceSpans Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5ae67-115">OpenMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|<span data-ttu-id="5ae67-116">Belirteç kaynağı eşleştirme bilgileri yaymak için bir özel özel veri bölümünü açın.</span><span class="sxs-lookup"><span data-stu-id="5ae67-116">Open a special custom data section to emit token-to- source span mapping information into.</span></span> <span data-ttu-id="5ae67-117">Bu bölümde, bir yöntem zaten açık olan veya tam tersi bir hata olduğunda açılıyor.</span><span class="sxs-lookup"><span data-stu-id="5ae67-117">Opening this section when a method is already open, or vice versa, is an error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5ae67-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5ae67-118">Requirements</span></span>  
 <span data-ttu-id="5ae67-119">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5ae67-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ae67-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ae67-120">See also</span></span>

- [<span data-ttu-id="5ae67-121">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5ae67-121">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="5ae67-122">ISymUnmanagedWriter4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5ae67-122">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
