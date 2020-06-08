---
title: ISymUnmanagedWriter5 Arabirimi
ms.date: 03/30/2017
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
ms.openlocfilehash: d9204457b71b670e1c96ed228ad11116bdf41fe6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493584"
---
# <a name="isymunmanagedwriter5-interface"></a><span data-ttu-id="ca29b-102">ISymUnmanagedWriter5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ca29b-102">ISymUnmanagedWriter5 Interface</span></span>
<span data-ttu-id="ca29b-103">ISymUnmanagedWriter5 arabirimi.</span><span class="sxs-lookup"><span data-stu-id="ca29b-103">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca29b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ca29b-104">Syntax</span></span>  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a><span data-ttu-id="ca29b-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ca29b-105">Methods</span></span>  
 <span data-ttu-id="ca29b-106">Bu arabirim aşağıdaki yöntemleri içerir:</span><span class="sxs-lookup"><span data-stu-id="ca29b-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="ca29b-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ca29b-107">Method</span></span>|<span data-ttu-id="ca29b-108">Description</span><span class="sxs-lookup"><span data-stu-id="ca29b-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ca29b-109">CloseMapTokensToSourceSpans Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ca29b-109">CloseMapTokensToSourceSpans Method</span></span>](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|<span data-ttu-id="ca29b-110">Belirteçten kaynağa yayılma eşleme bilgileri için özel özel veri bölümünü kapatın.</span><span class="sxs-lookup"><span data-stu-id="ca29b-110">Close the special custom data section for token-to- source span mapping information.</span></span> <span data-ttu-id="ca29b-111">Kapatıldıktan sonra, daha fazla eşleme bilgisi eklenemez.</span><span class="sxs-lookup"><span data-stu-id="ca29b-111">After it is closed, no more mapping information can be added.</span></span>|  
|[<span data-ttu-id="ca29b-112">MapTokenToSourceSpan Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ca29b-112">MapTokenToSourceSpan Method</span></span>](isymunmanagedwriter5-maptokentosourcespan-method.md)|<span data-ttu-id="ca29b-113">Verilen meta veri belirtecini belirtilen kaynak dosyadaki verilen kaynak satır aralığına eşler.</span><span class="sxs-lookup"><span data-stu-id="ca29b-113">Maps the given metadata token to the given source line span in the specified source file.</span></span><br /><br /> <span data-ttu-id="ca29b-114">[OpenMapTokensToSourceSpans Yöntemi](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) ve [CloseMapTokensToSourceSpans Yöntemi](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)çağrıları arasında çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ca29b-114">Must be called between calls to [OpenMapTokensToSourceSpans Method](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>|  
|[<span data-ttu-id="ca29b-115">OpenMapTokensToSourceSpans Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ca29b-115">OpenMapTokensToSourceSpans Method</span></span>](isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|<span data-ttu-id="ca29b-116">Belirteçten kaynağa yayılma eşleme bilgilerini içine göstermek için özel bir özel veri bölümünü açın.</span><span class="sxs-lookup"><span data-stu-id="ca29b-116">Open a special custom data section to emit token-to- source span mapping information into.</span></span> <span data-ttu-id="ca29b-117">Bir yöntem zaten açık olduğunda veya bunun tersi durumda, bu bölümü açmak bir hatadır.</span><span class="sxs-lookup"><span data-stu-id="ca29b-117">Opening this section when a method is already open, or vice versa, is an error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ca29b-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ca29b-118">Requirements</span></span>  
 <span data-ttu-id="ca29b-119">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="ca29b-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca29b-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca29b-120">See also</span></span>

- [<span data-ttu-id="ca29b-121">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ca29b-121">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="ca29b-122">ISymUnmanagedWriter4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ca29b-122">ISymUnmanagedWriter4 Interface</span></span>](isymunmanagedwriter4-interface.md)
