---
title: ISymUnmanagedWriter2 Arabirimi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2
helpviewer_keywords:
- ISymUnmanagedWriter2 interface [.NET Framework debugging]
ms.assetid: 8e78faa4-cf43-44fb-a91d-94d6df692a25
topic_type:
- apiref
ms.openlocfilehash: 6feb48b7c78dda64ba372e470b83ffb14f21f2f9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683335"
---
# <a name="isymunmanagedwriter2-interface"></a><span data-ttu-id="5a4ac-102">ISymUnmanagedWriter2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5a4ac-102">ISymUnmanagedWriter2 Interface</span></span>

<span data-ttu-id="5a4ac-103">Bir sembol yazıcısını temsil eder ve belgeleri, dizi noktalarını, sözcük temelli kapsamları ve değişkenleri tanımlamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5a4ac-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="5a4ac-104">Bu arabirim [ıstreamunmanagedwriter](isymunmanagedwriter-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="5a4ac-104">This interface extends the [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5a4ac-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5a4ac-105">Methods</span></span>  
  
|<span data-ttu-id="5a4ac-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="5a4ac-106">Method</span></span>|<span data-ttu-id="5a4ac-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5a4ac-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5a4ac-108">DefineConstant2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5a4ac-108">DefineConstant2 Method</span></span>](isymunmanagedwriter2-defineconstant2-method.md)|<span data-ttu-id="5a4ac-109">Sabit değer için bir ad tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5a4ac-109">Defines a name for a constant value.</span></span>|  
|[<span data-ttu-id="5a4ac-110">DefineGlobalVariable2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5a4ac-110">DefineGlobalVariable2 Method</span></span>](isymunmanagedwriter2-defineglobalvariable2-method.md)|<span data-ttu-id="5a4ac-111">Tek bir genel değişkeni tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5a4ac-111">Defines a single global variable.</span></span>|  
|[<span data-ttu-id="5a4ac-112">DefineLocalVariable2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5a4ac-112">DefineLocalVariable2 Method</span></span>](isymunmanagedwriter2-definelocalvariable2-method.md)|<span data-ttu-id="5a4ac-113">Geçerli sözcük kapsamındaki tek bir değişkeni tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5a4ac-113">Defines a single variable in the current lexical scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5a4ac-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5a4ac-114">Requirements</span></span>  

 <span data-ttu-id="5a4ac-115">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="5a4ac-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a4ac-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a4ac-116">See also</span></span>

- [<span data-ttu-id="5a4ac-117">Tanılama Sembol Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5a4ac-117">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="5a4ac-118">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5a4ac-118">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="5a4ac-119">ISymUnmanagedWriter3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5a4ac-119">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)
