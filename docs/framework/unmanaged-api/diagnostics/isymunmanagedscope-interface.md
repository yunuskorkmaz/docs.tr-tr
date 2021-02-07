---
description: 'Daha fazla bilgi edinin: ıstreamunmanagedscope arabirimi'
title: ISymUnmanagedScope Arabirimi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope
helpviewer_keywords:
- ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 3db7a220-cfe9-4810-8ca8-a094bb8e0f5b
topic_type:
- apiref
ms.openlocfilehash: f1175656fb49ee16fd1cd676d08f6ebb76f40c6d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763273"
---
# <a name="isymunmanagedscope-interface"></a><span data-ttu-id="e3569-103">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e3569-103">ISymUnmanagedScope Interface</span></span>

<span data-ttu-id="e3569-104">Bir yöntem içindeki bir sözcük temelli kapsamı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e3569-104">Represents a lexical scope within a method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e3569-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e3569-105">Methods</span></span>  
  
|<span data-ttu-id="e3569-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e3569-106">Method</span></span>|<span data-ttu-id="e3569-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3569-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e3569-108">GetChildren Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e3569-108">GetChildren Method</span></span>](isymunmanagedscope-getchildren-method.md)|<span data-ttu-id="e3569-109">Bu kapsamın alt öğelerini alır.</span><span class="sxs-lookup"><span data-stu-id="e3569-109">Gets the children of this scope.</span></span>|  
|[<span data-ttu-id="e3569-110">GetEndOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e3569-110">GetEndOffset Method</span></span>](isymunmanagedscope-getendoffset-method.md)|<span data-ttu-id="e3569-111">Bu kapsamın bitiş sapmasını alır.</span><span class="sxs-lookup"><span data-stu-id="e3569-111">Gets the end offset for this scope.</span></span>|  
|[<span data-ttu-id="e3569-112">GetLocalCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e3569-112">GetLocalCount Method</span></span>](isymunmanagedscope-getlocalcount-method.md)|<span data-ttu-id="e3569-113">Bu kapsam içinde tanımlanan yerel değişkenlerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="e3569-113">Gets a count of the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="e3569-114">GetLocals Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e3569-114">GetLocals Method</span></span>](isymunmanagedscope-getlocals-method.md)|<span data-ttu-id="e3569-115">Bu kapsam içinde tanımlanan yerel değişkenleri alır.</span><span class="sxs-lookup"><span data-stu-id="e3569-115">Gets the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="e3569-116">GetMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e3569-116">GetMethod Method</span></span>](isymunmanagedscope-getmethod-method.md)|<span data-ttu-id="e3569-117">Bu kapsamı içeren yöntemi alır.</span><span class="sxs-lookup"><span data-stu-id="e3569-117">Gets the method that contains this scope.</span></span>|  
|[<span data-ttu-id="e3569-118">GetNamespaces Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e3569-118">GetNamespaces Method</span></span>](isymunmanagedscope-getnamespaces-method.md)|<span data-ttu-id="e3569-119">Bu kapsam içinde kullanılmakta olan ad alanlarını alır.</span><span class="sxs-lookup"><span data-stu-id="e3569-119">Gets the namespaces that are being used within this scope.</span></span>|  
|[<span data-ttu-id="e3569-120">GetParent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e3569-120">GetParent Method</span></span>](isymunmanagedscope-getparent-method.md)|<span data-ttu-id="e3569-121">Bu kapsamın üst kapsamını alır.</span><span class="sxs-lookup"><span data-stu-id="e3569-121">Gets the parent scope of this scope.</span></span>|  
|[<span data-ttu-id="e3569-122">GetStartOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e3569-122">GetStartOffset Method</span></span>](isymunmanagedscope-getstartoffset-method.md)|<span data-ttu-id="e3569-123">Bu kapsamın başlangıç sapmasını alır.</span><span class="sxs-lookup"><span data-stu-id="e3569-123">Gets the start offset for this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e3569-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e3569-124">Requirements</span></span>  

 <span data-ttu-id="e3569-125">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e3569-125">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3569-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e3569-126">See also</span></span>

- [<span data-ttu-id="e3569-127">Tanılama Sembol Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e3569-127">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="e3569-128">ISymUnmanagedScope2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e3569-128">ISymUnmanagedScope2 Interface</span></span>](isymunmanagedscope2-interface.md)
