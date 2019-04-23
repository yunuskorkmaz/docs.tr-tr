---
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 809368ea19528a7ce00d4fcada06ef5724eb79a6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59228165"
---
# <a name="isymunmanagedscope-interface"></a><span data-ttu-id="829df-102">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="829df-102">ISymUnmanagedScope Interface</span></span>
<span data-ttu-id="829df-103">Bir sözlü kapsamda bir yöntemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="829df-103">Represents a lexical scope within a method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="829df-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="829df-104">Methods</span></span>  
  
|<span data-ttu-id="829df-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="829df-105">Method</span></span>|<span data-ttu-id="829df-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="829df-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="829df-107">GetChildren Yöntemi</span><span class="sxs-lookup"><span data-stu-id="829df-107">GetChildren Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getchildren-method.md)|<span data-ttu-id="829df-108">Bu kapsamın alt öğeleri alır.</span><span class="sxs-lookup"><span data-stu-id="829df-108">Gets the children of this scope.</span></span>|  
|[<span data-ttu-id="829df-109">GetEndOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="829df-109">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)|<span data-ttu-id="829df-110">Bu kapsam için bitiş uzaklığı alır.</span><span class="sxs-lookup"><span data-stu-id="829df-110">Gets the end offset for this scope.</span></span>|  
|[<span data-ttu-id="829df-111">GetLocalCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="829df-111">GetLocalCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocalcount-method.md)|<span data-ttu-id="829df-112">Bu kapsam içinde tanımlanan yerel değişkenler sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="829df-112">Gets a count of the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="829df-113">GetLocals Yöntemi</span><span class="sxs-lookup"><span data-stu-id="829df-113">GetLocals Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocals-method.md)|<span data-ttu-id="829df-114">Bu kapsam içinde tanımlanan yerel değişkenler alır.</span><span class="sxs-lookup"><span data-stu-id="829df-114">Gets the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="829df-115">GetMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="829df-115">GetMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getmethod-method.md)|<span data-ttu-id="829df-116">Bu kapsam içeren yöntemi alır.</span><span class="sxs-lookup"><span data-stu-id="829df-116">Gets the method that contains this scope.</span></span>|  
|[<span data-ttu-id="829df-117">GetNamespaces Yöntemi</span><span class="sxs-lookup"><span data-stu-id="829df-117">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getnamespaces-method.md)|<span data-ttu-id="829df-118">Bu kapsam içinde kullanılan ad alanlarını alır.</span><span class="sxs-lookup"><span data-stu-id="829df-118">Gets the namespaces that are being used within this scope.</span></span>|  
|[<span data-ttu-id="829df-119">GetParent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="829df-119">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)|<span data-ttu-id="829df-120">Bu kapsam üst kapsamı alır.</span><span class="sxs-lookup"><span data-stu-id="829df-120">Gets the parent scope of this scope.</span></span>|  
|[<span data-ttu-id="829df-121">GetStartOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="829df-121">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)|<span data-ttu-id="829df-122">Bu kapsam için başlangıç uzaklığını alır.</span><span class="sxs-lookup"><span data-stu-id="829df-122">Gets the start offset for this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="829df-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="829df-123">Requirements</span></span>  
 <span data-ttu-id="829df-124">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="829df-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="829df-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="829df-125">See also</span></span>

- [<span data-ttu-id="829df-126">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="829df-126">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="829df-127">ISymUnmanagedScope2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="829df-127">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
