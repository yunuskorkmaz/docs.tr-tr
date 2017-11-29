---
title: ISymUnmanagedScope Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope
helpviewer_keywords: ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 3db7a220-cfe9-4810-8ca8-a094bb8e0f5b
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d25d62dd42e3e93124c9a3bd8945be265f192663
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedscope-interface"></a><span data-ttu-id="1788b-102">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1788b-102">ISymUnmanagedScope Interface</span></span>
<span data-ttu-id="1788b-103">Bir yöntem sözcük kapsamında temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1788b-103">Represents a lexical scope within a method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1788b-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1788b-104">Methods</span></span>  
  
|<span data-ttu-id="1788b-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1788b-105">Method</span></span>|<span data-ttu-id="1788b-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1788b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1788b-107">GetChildren yöntemi</span><span class="sxs-lookup"><span data-stu-id="1788b-107">GetChildren Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getchildren-method.md)|<span data-ttu-id="1788b-108">Bu kapsamın alt öğelerini alır.</span><span class="sxs-lookup"><span data-stu-id="1788b-108">Gets the children of this scope.</span></span>|  
|[<span data-ttu-id="1788b-109">GetEndOffset yöntemi</span><span class="sxs-lookup"><span data-stu-id="1788b-109">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)|<span data-ttu-id="1788b-110">Bitiş uzaklığı için bu kapsamı alır.</span><span class="sxs-lookup"><span data-stu-id="1788b-110">Gets the end offset for this scope.</span></span>|  
|[<span data-ttu-id="1788b-111">GetLocalCount yöntemi</span><span class="sxs-lookup"><span data-stu-id="1788b-111">GetLocalCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocalcount-method.md)|<span data-ttu-id="1788b-112">Bu kapsam içinde tanımlanan yerel değişkenler sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="1788b-112">Gets a count of the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="1788b-113">GetLocals yöntemi</span><span class="sxs-lookup"><span data-stu-id="1788b-113">GetLocals Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocals-method.md)|<span data-ttu-id="1788b-114">Bu kapsam içinde tanımlanan yerel değişkenleri alır.</span><span class="sxs-lookup"><span data-stu-id="1788b-114">Gets the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="1788b-115">GetMethod yöntemi</span><span class="sxs-lookup"><span data-stu-id="1788b-115">GetMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getmethod-method.md)|<span data-ttu-id="1788b-116">Bu kapsam içeren yöntemi alır.</span><span class="sxs-lookup"><span data-stu-id="1788b-116">Gets the method that contains this scope.</span></span>|  
|[<span data-ttu-id="1788b-117">GetNamespaces yöntemi</span><span class="sxs-lookup"><span data-stu-id="1788b-117">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getnamespaces-method.md)|<span data-ttu-id="1788b-118">Bu kapsam içinde kullanılan ad alanlarını alır.</span><span class="sxs-lookup"><span data-stu-id="1788b-118">Gets the namespaces that are being used within this scope.</span></span>|  
|[<span data-ttu-id="1788b-119">GetParent yöntemi</span><span class="sxs-lookup"><span data-stu-id="1788b-119">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)|<span data-ttu-id="1788b-120">Bu kapsam üst kapsamı alır.</span><span class="sxs-lookup"><span data-stu-id="1788b-120">Gets the parent scope of this scope.</span></span>|  
|[<span data-ttu-id="1788b-121">GetStartOffset yöntemi</span><span class="sxs-lookup"><span data-stu-id="1788b-121">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)|<span data-ttu-id="1788b-122">Bu kapsam için başlangıç uzaklığı alır.</span><span class="sxs-lookup"><span data-stu-id="1788b-122">Gets the start offset for this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1788b-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1788b-123">Requirements</span></span>  
 <span data-ttu-id="1788b-124">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1788b-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1788b-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1788b-125">See Also</span></span>  
 [<span data-ttu-id="1788b-126">Tanılama sembol deposu arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1788b-126">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="1788b-127">Isymunmanagedscope2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="1788b-127">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
