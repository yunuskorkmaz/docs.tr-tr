---
title: ISymUnmanagedWriter5 Arabirimi
ms.date: 03/30/2017
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
ms.openlocfilehash: 18371b6aefb002f5adf27d43f85194c6c35f6ef5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121633"
---
# <a name="isymunmanagedwriter5-interface"></a><span data-ttu-id="eb339-102">ISymUnmanagedWriter5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eb339-102">ISymUnmanagedWriter5 Interface</span></span>
<span data-ttu-id="eb339-103">ISymUnmanagedWriter5 arabirimi.</span><span class="sxs-lookup"><span data-stu-id="eb339-103">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb339-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eb339-104">Syntax</span></span>  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a><span data-ttu-id="eb339-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="eb339-105">Methods</span></span>  
 <span data-ttu-id="eb339-106">Bu arabirim aşağıdaki yöntemleri içerir:</span><span class="sxs-lookup"><span data-stu-id="eb339-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="eb339-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="eb339-107">Method</span></span>|<span data-ttu-id="eb339-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eb339-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eb339-109">CloseMapTokensToSourceSpans Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eb339-109">CloseMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|<span data-ttu-id="eb339-110">Belirteçten kaynağa yayılma eşleme bilgileri için özel özel veri bölümünü kapatın.</span><span class="sxs-lookup"><span data-stu-id="eb339-110">Close the special custom data section for token-to- source span mapping information.</span></span> <span data-ttu-id="eb339-111">Kapatıldıktan sonra, daha fazla eşleme bilgisi eklenemez.</span><span class="sxs-lookup"><span data-stu-id="eb339-111">After it is closed, no more mapping information can be added.</span></span>|  
|[<span data-ttu-id="eb339-112">MapTokenToSourceSpan Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eb339-112">MapTokenToSourceSpan Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-maptokentosourcespan-method.md)|<span data-ttu-id="eb339-113">Verilen meta veri belirtecini belirtilen kaynak dosyadaki verilen kaynak satır aralığına eşler.</span><span class="sxs-lookup"><span data-stu-id="eb339-113">Maps the given metadata token to the given source line span in the specified source file.</span></span><br /><br /> <span data-ttu-id="eb339-114">[OpenMapTokensToSourceSpans Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) ve [CloseMapTokensToSourceSpans Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)çağrıları arasında çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="eb339-114">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>|  
|[<span data-ttu-id="eb339-115">OpenMapTokensToSourceSpans Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eb339-115">OpenMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|<span data-ttu-id="eb339-116">Belirteçten kaynağa yayılma eşleme bilgilerini içine göstermek için özel bir özel veri bölümünü açın.</span><span class="sxs-lookup"><span data-stu-id="eb339-116">Open a special custom data section to emit token-to- source span mapping information into.</span></span> <span data-ttu-id="eb339-117">Bir yöntem zaten açık olduğunda veya bunun tersi durumda, bu bölümü açmak bir hatadır.</span><span class="sxs-lookup"><span data-stu-id="eb339-117">Opening this section when a method is already open, or vice versa, is an error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="eb339-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eb339-118">Requirements</span></span>  
 <span data-ttu-id="eb339-119">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="eb339-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb339-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb339-120">See also</span></span>

- [<span data-ttu-id="eb339-121">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="eb339-121">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="eb339-122">ISymUnmanagedWriter4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eb339-122">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
