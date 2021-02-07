---
description: 'Daha fazla bilgi edinin: ISymUnmanagedWriter5 Interface'
title: ISymUnmanagedWriter5 Arabirimi
ms.date: 03/30/2017
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
ms.openlocfilehash: 0902385576e1eed17cea672b04858c7e3ef7add8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761635"
---
# <a name="isymunmanagedwriter5-interface"></a><span data-ttu-id="4d68a-103">ISymUnmanagedWriter5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4d68a-103">ISymUnmanagedWriter5 Interface</span></span>

<span data-ttu-id="4d68a-104">ISymUnmanagedWriter5 arabirimi.</span><span class="sxs-lookup"><span data-stu-id="4d68a-104">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d68a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4d68a-105">Syntax</span></span>  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a><span data-ttu-id="4d68a-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4d68a-106">Methods</span></span>  

 <span data-ttu-id="4d68a-107">Bu arabirim aşağıdaki yöntemleri içerir:</span><span class="sxs-lookup"><span data-stu-id="4d68a-107">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="4d68a-108">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4d68a-108">Method</span></span>|<span data-ttu-id="4d68a-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4d68a-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4d68a-110">CloseMapTokensToSourceSpans Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4d68a-110">CloseMapTokensToSourceSpans Method</span></span>](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|<span data-ttu-id="4d68a-111">Belirteçten kaynağa yayılma eşleme bilgileri için özel özel veri bölümünü kapatın.</span><span class="sxs-lookup"><span data-stu-id="4d68a-111">Close the special custom data section for token-to- source span mapping information.</span></span> <span data-ttu-id="4d68a-112">Kapatıldıktan sonra, daha fazla eşleme bilgisi eklenemez.</span><span class="sxs-lookup"><span data-stu-id="4d68a-112">After it is closed, no more mapping information can be added.</span></span>|  
|[<span data-ttu-id="4d68a-113">MapTokenToSourceSpan Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4d68a-113">MapTokenToSourceSpan Method</span></span>](isymunmanagedwriter5-maptokentosourcespan-method.md)|<span data-ttu-id="4d68a-114">Verilen meta veri belirtecini belirtilen kaynak dosyadaki verilen kaynak satır aralığına eşler.</span><span class="sxs-lookup"><span data-stu-id="4d68a-114">Maps the given metadata token to the given source line span in the specified source file.</span></span><br /><br /> <span data-ttu-id="4d68a-115">[OpenMapTokensToSourceSpans Yöntemi](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) ve [CloseMapTokensToSourceSpans Yöntemi](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)çağrıları arasında çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4d68a-115">Must be called between calls to [OpenMapTokensToSourceSpans Method](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>|  
|[<span data-ttu-id="4d68a-116">OpenMapTokensToSourceSpans Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4d68a-116">OpenMapTokensToSourceSpans Method</span></span>](isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|<span data-ttu-id="4d68a-117">Belirteçten kaynağa yayılma eşleme bilgilerini içine göstermek için özel bir özel veri bölümünü açın.</span><span class="sxs-lookup"><span data-stu-id="4d68a-117">Open a special custom data section to emit token-to- source span mapping information into.</span></span> <span data-ttu-id="4d68a-118">Bir yöntem zaten açık olduğunda veya bunun tersi durumda, bu bölümü açmak bir hatadır.</span><span class="sxs-lookup"><span data-stu-id="4d68a-118">Opening this section when a method is already open, or vice versa, is an error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4d68a-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4d68a-119">Requirements</span></span>  

 <span data-ttu-id="4d68a-120">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="4d68a-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d68a-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d68a-121">See also</span></span>

- [<span data-ttu-id="4d68a-122">Tanılama Sembol Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4d68a-122">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="4d68a-123">ISymUnmanagedWriter4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4d68a-123">ISymUnmanagedWriter4 Interface</span></span>](isymunmanagedwriter4-interface.md)
