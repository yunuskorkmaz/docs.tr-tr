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
ms.openlocfilehash: beb48835039f142ea1d9e18871f77ada1b6f4f3e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706319"
---
# <a name="isymunmanagedscope2-interface"></a><span data-ttu-id="a6050-102">ISymUnmanagedScope2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a6050-102">ISymUnmanagedScope2 Interface</span></span>
<span data-ttu-id="a6050-103">Bir sözlü kapsamda bir yöntemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a6050-103">Represents a lexical scope within a method.</span></span> <span data-ttu-id="a6050-104">Bu arabirim genişletir [Isymunmanagedscope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) arabirim yöntemleriyle kapsamında tanımlanmış sabitleri hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="a6050-104">This interface extends the [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface with methods that get information about constants defined within the scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a6050-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a6050-105">Methods</span></span>  
  
|<span data-ttu-id="a6050-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a6050-106">Method</span></span>|<span data-ttu-id="a6050-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a6050-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a6050-108">GetConstantCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a6050-108">GetConstantCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstantcount-method.md)|<span data-ttu-id="a6050-109">Bu kapsam içinde tanımlı sabitlerden sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="a6050-109">Gets a count of the constants defined within this scope.</span></span>|  
|[<span data-ttu-id="a6050-110">GetConstants Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a6050-110">GetConstants Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstants-method.md)|<span data-ttu-id="a6050-111">Bu kapsam içinde tanımlanan yerel sabitleri alır.</span><span class="sxs-lookup"><span data-stu-id="a6050-111">Gets the local constants defined within this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a6050-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a6050-112">Requirements</span></span>  
 <span data-ttu-id="a6050-113">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a6050-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6050-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6050-114">See also</span></span>
- [<span data-ttu-id="a6050-115">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a6050-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="a6050-116">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a6050-116">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
