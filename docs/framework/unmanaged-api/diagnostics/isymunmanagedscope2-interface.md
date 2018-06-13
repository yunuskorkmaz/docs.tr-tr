---
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a33d8b489551dc69542e1b12bcf83602ec5a2008
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427254"
---
# <a name="isymunmanagedscope2-interface"></a><span data-ttu-id="ff61b-102">ISymUnmanagedScope2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ff61b-102">ISymUnmanagedScope2 Interface</span></span>
<span data-ttu-id="ff61b-103">Bir yöntem sözcük kapsamında temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ff61b-103">Represents a lexical scope within a method.</span></span> <span data-ttu-id="ff61b-104">Bu arabirim genişletir [Isymunmanagedscope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) kapsamı içinde tanımlanan sabitleri hakkında bilgi alma yöntemleriyle arabirimi.</span><span class="sxs-lookup"><span data-stu-id="ff61b-104">This interface extends the [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface with methods that get information about constants defined within the scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ff61b-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ff61b-105">Methods</span></span>  
  
|<span data-ttu-id="ff61b-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ff61b-106">Method</span></span>|<span data-ttu-id="ff61b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ff61b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ff61b-108">GetConstantCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ff61b-108">GetConstantCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstantcount-method.md)|<span data-ttu-id="ff61b-109">Bu kapsam içinde tanımlanan sabitleri sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="ff61b-109">Gets a count of the constants defined within this scope.</span></span>|  
|[<span data-ttu-id="ff61b-110">GetConstants Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ff61b-110">GetConstants Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstants-method.md)|<span data-ttu-id="ff61b-111">Bu kapsam içinde tanımlanan yerel sabitleri alır.</span><span class="sxs-lookup"><span data-stu-id="ff61b-111">Gets the local constants defined within this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ff61b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ff61b-112">Requirements</span></span>  
 <span data-ttu-id="ff61b-113">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ff61b-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff61b-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ff61b-114">See Also</span></span>  
 [<span data-ttu-id="ff61b-115">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ff61b-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="ff61b-116">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ff61b-116">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
