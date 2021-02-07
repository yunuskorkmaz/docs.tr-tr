---
description: 'Daha fazla bilgi edinin: ISymUnmanagedScope2 Interface'
title: ISymUnmanagedScope2 Arabirimi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2
helpviewer_keywords:
- ISymUnmanagedScope2 interface [.NET Framework debugging]
ms.assetid: 2ed6a387-ba45-483e-9a1e-b0c69f67998b
topic_type:
- apiref
ms.openlocfilehash: a15094da68b00dbec454b2f6a642ac333f9a34ed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763156"
---
# <a name="isymunmanagedscope2-interface"></a><span data-ttu-id="fb1de-103">ISymUnmanagedScope2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fb1de-103">ISymUnmanagedScope2 Interface</span></span>

<span data-ttu-id="fb1de-104">Bir yöntem içindeki bir sözcük temelli kapsamı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fb1de-104">Represents a lexical scope within a method.</span></span> <span data-ttu-id="fb1de-105">Bu arabirim, [ıstreamunmanagedscope](isymunmanagedscope-interface.md) arabirimini kapsam içinde tanımlanan sabitler hakkında bilgi alan yöntemlerle genişletir.</span><span class="sxs-lookup"><span data-stu-id="fb1de-105">This interface extends the [ISymUnmanagedScope](isymunmanagedscope-interface.md) interface with methods that get information about constants defined within the scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fb1de-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="fb1de-106">Methods</span></span>  
  
|<span data-ttu-id="fb1de-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="fb1de-107">Method</span></span>|<span data-ttu-id="fb1de-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fb1de-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fb1de-109">GetConstantCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fb1de-109">GetConstantCount Method</span></span>](isymunmanagedscope2-getconstantcount-method.md)|<span data-ttu-id="fb1de-110">Bu kapsam içinde tanımlanan sabitlerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="fb1de-110">Gets a count of the constants defined within this scope.</span></span>|  
|[<span data-ttu-id="fb1de-111">GetConstants Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fb1de-111">GetConstants Method</span></span>](isymunmanagedscope2-getconstants-method.md)|<span data-ttu-id="fb1de-112">Bu kapsam içinde tanımlanan yerel sabitleri alır.</span><span class="sxs-lookup"><span data-stu-id="fb1de-112">Gets the local constants defined within this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fb1de-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fb1de-113">Requirements</span></span>  

 <span data-ttu-id="fb1de-114">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="fb1de-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb1de-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb1de-115">See also</span></span>

- [<span data-ttu-id="fb1de-116">Tanılama Sembol Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fb1de-116">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="fb1de-117">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fb1de-117">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
