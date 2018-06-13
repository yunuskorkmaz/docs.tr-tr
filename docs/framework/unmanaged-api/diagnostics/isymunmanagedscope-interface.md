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
ms.openlocfilehash: 6305338a95d7710a5feda2dc4c89e5a92262514c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428719"
---
# <a name="isymunmanagedscope-interface"></a><span data-ttu-id="26ec5-102">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="26ec5-102">ISymUnmanagedScope Interface</span></span>
<span data-ttu-id="26ec5-103">Bir yöntem sözcük kapsamında temsil eder.</span><span class="sxs-lookup"><span data-stu-id="26ec5-103">Represents a lexical scope within a method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="26ec5-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="26ec5-104">Methods</span></span>  
  
|<span data-ttu-id="26ec5-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="26ec5-105">Method</span></span>|<span data-ttu-id="26ec5-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="26ec5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="26ec5-107">GetChildren Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26ec5-107">GetChildren Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getchildren-method.md)|<span data-ttu-id="26ec5-108">Bu kapsamın alt öğelerini alır.</span><span class="sxs-lookup"><span data-stu-id="26ec5-108">Gets the children of this scope.</span></span>|  
|[<span data-ttu-id="26ec5-109">GetEndOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26ec5-109">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)|<span data-ttu-id="26ec5-110">Bitiş uzaklığı için bu kapsamı alır.</span><span class="sxs-lookup"><span data-stu-id="26ec5-110">Gets the end offset for this scope.</span></span>|  
|[<span data-ttu-id="26ec5-111">GetLocalCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26ec5-111">GetLocalCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocalcount-method.md)|<span data-ttu-id="26ec5-112">Bu kapsam içinde tanımlanan yerel değişkenler sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="26ec5-112">Gets a count of the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="26ec5-113">GetLocals Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26ec5-113">GetLocals Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocals-method.md)|<span data-ttu-id="26ec5-114">Bu kapsam içinde tanımlanan yerel değişkenleri alır.</span><span class="sxs-lookup"><span data-stu-id="26ec5-114">Gets the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="26ec5-115">GetMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26ec5-115">GetMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getmethod-method.md)|<span data-ttu-id="26ec5-116">Bu kapsam içeren yöntemi alır.</span><span class="sxs-lookup"><span data-stu-id="26ec5-116">Gets the method that contains this scope.</span></span>|  
|[<span data-ttu-id="26ec5-117">GetNamespaces Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26ec5-117">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getnamespaces-method.md)|<span data-ttu-id="26ec5-118">Bu kapsam içinde kullanılan ad alanlarını alır.</span><span class="sxs-lookup"><span data-stu-id="26ec5-118">Gets the namespaces that are being used within this scope.</span></span>|  
|[<span data-ttu-id="26ec5-119">GetParent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26ec5-119">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)|<span data-ttu-id="26ec5-120">Bu kapsam üst kapsamı alır.</span><span class="sxs-lookup"><span data-stu-id="26ec5-120">Gets the parent scope of this scope.</span></span>|  
|[<span data-ttu-id="26ec5-121">GetStartOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26ec5-121">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)|<span data-ttu-id="26ec5-122">Bu kapsam için başlangıç uzaklığı alır.</span><span class="sxs-lookup"><span data-stu-id="26ec5-122">Gets the start offset for this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="26ec5-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="26ec5-123">Requirements</span></span>  
 <span data-ttu-id="26ec5-124">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="26ec5-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26ec5-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="26ec5-125">See Also</span></span>  
 [<span data-ttu-id="26ec5-126">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="26ec5-126">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="26ec5-127">ISymUnmanagedScope2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26ec5-127">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
