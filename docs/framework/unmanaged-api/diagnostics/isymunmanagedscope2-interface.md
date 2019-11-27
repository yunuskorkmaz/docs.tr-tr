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
ms.openlocfilehash: 3374097c8d343fed6badf046742ca556d2a92f3e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446223"
---
# <a name="isymunmanagedscope2-interface"></a><span data-ttu-id="90aff-102">ISymUnmanagedScope2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="90aff-102">ISymUnmanagedScope2 Interface</span></span>
<span data-ttu-id="90aff-103">Bir yöntem içindeki bir sözcük temelli kapsamı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="90aff-103">Represents a lexical scope within a method.</span></span> <span data-ttu-id="90aff-104">Bu arabirim, [ıstreamunmanagedscope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) arabirimini kapsam içinde tanımlanan sabitler hakkında bilgi alan yöntemlerle genişletir.</span><span class="sxs-lookup"><span data-stu-id="90aff-104">This interface extends the [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface with methods that get information about constants defined within the scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="90aff-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="90aff-105">Methods</span></span>  
  
|<span data-ttu-id="90aff-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="90aff-106">Method</span></span>|<span data-ttu-id="90aff-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="90aff-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="90aff-108">GetConstantCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="90aff-108">GetConstantCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstantcount-method.md)|<span data-ttu-id="90aff-109">Bu kapsam içinde tanımlanan sabitlerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="90aff-109">Gets a count of the constants defined within this scope.</span></span>|  
|[<span data-ttu-id="90aff-110">GetConstants Yöntemi</span><span class="sxs-lookup"><span data-stu-id="90aff-110">GetConstants Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstants-method.md)|<span data-ttu-id="90aff-111">Bu kapsam içinde tanımlanan yerel sabitleri alır.</span><span class="sxs-lookup"><span data-stu-id="90aff-111">Gets the local constants defined within this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="90aff-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="90aff-112">Requirements</span></span>  
 <span data-ttu-id="90aff-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="90aff-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90aff-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="90aff-114">See also</span></span>

- [<span data-ttu-id="90aff-115">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="90aff-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="90aff-116">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="90aff-116">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
