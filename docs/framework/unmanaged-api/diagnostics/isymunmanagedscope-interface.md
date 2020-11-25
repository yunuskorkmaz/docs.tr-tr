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
ms.openlocfilehash: 9256342ad3a91e6770d6fd19d9d2f94fab267d3e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725891"
---
# <a name="isymunmanagedscope-interface"></a><span data-ttu-id="55258-102">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="55258-102">ISymUnmanagedScope Interface</span></span>

<span data-ttu-id="55258-103">Bir yöntem içindeki bir sözcük temelli kapsamı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="55258-103">Represents a lexical scope within a method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="55258-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="55258-104">Methods</span></span>  
  
|<span data-ttu-id="55258-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="55258-105">Method</span></span>|<span data-ttu-id="55258-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55258-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="55258-107">GetChildren Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55258-107">GetChildren Method</span></span>](isymunmanagedscope-getchildren-method.md)|<span data-ttu-id="55258-108">Bu kapsamın alt öğelerini alır.</span><span class="sxs-lookup"><span data-stu-id="55258-108">Gets the children of this scope.</span></span>|  
|[<span data-ttu-id="55258-109">GetEndOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55258-109">GetEndOffset Method</span></span>](isymunmanagedscope-getendoffset-method.md)|<span data-ttu-id="55258-110">Bu kapsamın bitiş sapmasını alır.</span><span class="sxs-lookup"><span data-stu-id="55258-110">Gets the end offset for this scope.</span></span>|  
|[<span data-ttu-id="55258-111">GetLocalCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55258-111">GetLocalCount Method</span></span>](isymunmanagedscope-getlocalcount-method.md)|<span data-ttu-id="55258-112">Bu kapsam içinde tanımlanan yerel değişkenlerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="55258-112">Gets a count of the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="55258-113">GetLocals Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55258-113">GetLocals Method</span></span>](isymunmanagedscope-getlocals-method.md)|<span data-ttu-id="55258-114">Bu kapsam içinde tanımlanan yerel değişkenleri alır.</span><span class="sxs-lookup"><span data-stu-id="55258-114">Gets the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="55258-115">GetMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55258-115">GetMethod Method</span></span>](isymunmanagedscope-getmethod-method.md)|<span data-ttu-id="55258-116">Bu kapsamı içeren yöntemi alır.</span><span class="sxs-lookup"><span data-stu-id="55258-116">Gets the method that contains this scope.</span></span>|  
|[<span data-ttu-id="55258-117">GetNamespaces Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55258-117">GetNamespaces Method</span></span>](isymunmanagedscope-getnamespaces-method.md)|<span data-ttu-id="55258-118">Bu kapsam içinde kullanılmakta olan ad alanlarını alır.</span><span class="sxs-lookup"><span data-stu-id="55258-118">Gets the namespaces that are being used within this scope.</span></span>|  
|[<span data-ttu-id="55258-119">GetParent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55258-119">GetParent Method</span></span>](isymunmanagedscope-getparent-method.md)|<span data-ttu-id="55258-120">Bu kapsamın üst kapsamını alır.</span><span class="sxs-lookup"><span data-stu-id="55258-120">Gets the parent scope of this scope.</span></span>|  
|[<span data-ttu-id="55258-121">GetStartOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55258-121">GetStartOffset Method</span></span>](isymunmanagedscope-getstartoffset-method.md)|<span data-ttu-id="55258-122">Bu kapsamın başlangıç sapmasını alır.</span><span class="sxs-lookup"><span data-stu-id="55258-122">Gets the start offset for this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="55258-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="55258-123">Requirements</span></span>  

 <span data-ttu-id="55258-124">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="55258-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55258-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55258-125">See also</span></span>

- [<span data-ttu-id="55258-126">Tanılama Sembol Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="55258-126">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="55258-127">ISymUnmanagedScope2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="55258-127">ISymUnmanagedScope2 Interface</span></span>](isymunmanagedscope2-interface.md)
