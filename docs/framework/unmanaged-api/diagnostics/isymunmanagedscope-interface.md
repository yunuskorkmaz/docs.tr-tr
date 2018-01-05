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
ms.workload: dotnet
ms.openlocfilehash: 1e4d4c83b754945c126913a9d96db47966959fed
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedscope-interface"></a><span data-ttu-id="56ce0-102">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="56ce0-102">ISymUnmanagedScope Interface</span></span>
<span data-ttu-id="56ce0-103">Bir yöntem sözcük kapsamında temsil eder.</span><span class="sxs-lookup"><span data-stu-id="56ce0-103">Represents a lexical scope within a method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="56ce0-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="56ce0-104">Methods</span></span>  
  
|<span data-ttu-id="56ce0-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="56ce0-105">Method</span></span>|<span data-ttu-id="56ce0-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="56ce0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="56ce0-107">GetChildren Yöntemi</span><span class="sxs-lookup"><span data-stu-id="56ce0-107">GetChildren Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getchildren-method.md)|<span data-ttu-id="56ce0-108">Bu kapsamın alt öğelerini alır.</span><span class="sxs-lookup"><span data-stu-id="56ce0-108">Gets the children of this scope.</span></span>|  
|[<span data-ttu-id="56ce0-109">GetEndOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="56ce0-109">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)|<span data-ttu-id="56ce0-110">Bitiş uzaklığı için bu kapsamı alır.</span><span class="sxs-lookup"><span data-stu-id="56ce0-110">Gets the end offset for this scope.</span></span>|  
|[<span data-ttu-id="56ce0-111">GetLocalCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="56ce0-111">GetLocalCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocalcount-method.md)|<span data-ttu-id="56ce0-112">Bu kapsam içinde tanımlanan yerel değişkenler sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="56ce0-112">Gets a count of the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="56ce0-113">GetLocals Yöntemi</span><span class="sxs-lookup"><span data-stu-id="56ce0-113">GetLocals Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocals-method.md)|<span data-ttu-id="56ce0-114">Bu kapsam içinde tanımlanan yerel değişkenleri alır.</span><span class="sxs-lookup"><span data-stu-id="56ce0-114">Gets the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="56ce0-115">GetMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="56ce0-115">GetMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getmethod-method.md)|<span data-ttu-id="56ce0-116">Bu kapsam içeren yöntemi alır.</span><span class="sxs-lookup"><span data-stu-id="56ce0-116">Gets the method that contains this scope.</span></span>|  
|[<span data-ttu-id="56ce0-117">GetNamespaces Yöntemi</span><span class="sxs-lookup"><span data-stu-id="56ce0-117">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getnamespaces-method.md)|<span data-ttu-id="56ce0-118">Bu kapsam içinde kullanılan ad alanlarını alır.</span><span class="sxs-lookup"><span data-stu-id="56ce0-118">Gets the namespaces that are being used within this scope.</span></span>|  
|[<span data-ttu-id="56ce0-119">GetParent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="56ce0-119">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)|<span data-ttu-id="56ce0-120">Bu kapsam üst kapsamı alır.</span><span class="sxs-lookup"><span data-stu-id="56ce0-120">Gets the parent scope of this scope.</span></span>|  
|[<span data-ttu-id="56ce0-121">GetStartOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="56ce0-121">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)|<span data-ttu-id="56ce0-122">Bu kapsam için başlangıç uzaklığı alır.</span><span class="sxs-lookup"><span data-stu-id="56ce0-122">Gets the start offset for this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="56ce0-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="56ce0-123">Requirements</span></span>  
 <span data-ttu-id="56ce0-124">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="56ce0-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56ce0-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="56ce0-125">See Also</span></span>  
 [<span data-ttu-id="56ce0-126">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="56ce0-126">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="56ce0-127">ISymUnmanagedScope2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="56ce0-127">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
