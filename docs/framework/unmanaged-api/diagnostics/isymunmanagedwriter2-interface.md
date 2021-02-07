---
description: 'Daha fazla bilgi edinin: ISymUnmanagedWriter2 Interface'
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
ms.openlocfilehash: 228bae40e12376b3b5e8ca3bbd3463ba70a6d67b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761786"
---
# <a name="isymunmanagedwriter2-interface"></a><span data-ttu-id="3c4eb-103">ISymUnmanagedWriter2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3c4eb-103">ISymUnmanagedWriter2 Interface</span></span>

<span data-ttu-id="3c4eb-104">Bir sembol yazıcısını temsil eder ve belgeleri, dizi noktalarını, sözcük temelli kapsamları ve değişkenleri tanımlamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c4eb-104">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="3c4eb-105">Bu arabirim [ıstreamunmanagedwriter](isymunmanagedwriter-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="3c4eb-105">This interface extends the [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3c4eb-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="3c4eb-106">Methods</span></span>  
  
|<span data-ttu-id="3c4eb-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="3c4eb-107">Method</span></span>|<span data-ttu-id="3c4eb-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3c4eb-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3c4eb-109">DefineConstant2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3c4eb-109">DefineConstant2 Method</span></span>](isymunmanagedwriter2-defineconstant2-method.md)|<span data-ttu-id="3c4eb-110">Sabit değer için bir ad tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3c4eb-110">Defines a name for a constant value.</span></span>|  
|[<span data-ttu-id="3c4eb-111">DefineGlobalVariable2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3c4eb-111">DefineGlobalVariable2 Method</span></span>](isymunmanagedwriter2-defineglobalvariable2-method.md)|<span data-ttu-id="3c4eb-112">Tek bir genel değişkeni tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3c4eb-112">Defines a single global variable.</span></span>|  
|[<span data-ttu-id="3c4eb-113">DefineLocalVariable2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3c4eb-113">DefineLocalVariable2 Method</span></span>](isymunmanagedwriter2-definelocalvariable2-method.md)|<span data-ttu-id="3c4eb-114">Geçerli sözcük kapsamındaki tek bir değişkeni tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3c4eb-114">Defines a single variable in the current lexical scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3c4eb-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3c4eb-115">Requirements</span></span>  

 <span data-ttu-id="3c4eb-116">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="3c4eb-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c4eb-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c4eb-117">See also</span></span>

- [<span data-ttu-id="3c4eb-118">Tanılama Sembol Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3c4eb-118">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="3c4eb-119">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3c4eb-119">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="3c4eb-120">ISymUnmanagedWriter3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3c4eb-120">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)
