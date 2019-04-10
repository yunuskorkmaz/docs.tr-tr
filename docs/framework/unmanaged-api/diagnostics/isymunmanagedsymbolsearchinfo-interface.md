---
title: ISymUnmanagedSymbolSearchInfo Arabirimi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo
helpviewer_keywords:
- ISymUnmanagedSymbolSearchInfo interface [.NET Framework debugging]
ms.assetid: 30817373-0a21-49c1-a0c4-8e8daeecb8db
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d573264bb7a3cac02dd41afacaa2bc4a6f9e6dcd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207558"
---
# <a name="isymunmanagedsymbolsearchinfo-interface"></a><span data-ttu-id="d2b67-102">ISymUnmanagedSymbolSearchInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d2b67-102">ISymUnmanagedSymbolSearchInfo Interface</span></span>
<span data-ttu-id="d2b67-103">Arama yolu hakkında bilgi almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d2b67-103">Provides methods that get information about the search path.</span></span> <span data-ttu-id="d2b67-104">Bu arabirim çağırarak elde `QueryInterface` uygulayan bir nesne üzerinde [Isymunmanagedreader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d2b67-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d2b67-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d2b67-105">Methods</span></span>  
  
|<span data-ttu-id="d2b67-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d2b67-106">Method</span></span>|<span data-ttu-id="d2b67-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2b67-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d2b67-108">GetHRESULT Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d2b67-108">GetHRESULT Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-gethresult-method.md)|<span data-ttu-id="d2b67-109">HRESULT alır.</span><span class="sxs-lookup"><span data-stu-id="d2b67-109">Gets the HRESULT.</span></span>|  
|[<span data-ttu-id="d2b67-110">GetSearchPath Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d2b67-110">GetSearchPath Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpath-method.md)|<span data-ttu-id="d2b67-111">Arama yolunu alır.</span><span class="sxs-lookup"><span data-stu-id="d2b67-111">Gets the search path.</span></span>|  
|[<span data-ttu-id="d2b67-112">GetSearchPathLength Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d2b67-112">GetSearchPathLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpathlength-method.md)|<span data-ttu-id="d2b67-113">Arama yolu uzunluğunu alır.</span><span class="sxs-lookup"><span data-stu-id="d2b67-113">Gets the search path length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d2b67-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d2b67-114">Requirements</span></span>  
 <span data-ttu-id="d2b67-115">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d2b67-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2b67-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2b67-116">See also</span></span>

- [<span data-ttu-id="d2b67-117">Tanılama Sembol Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d2b67-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
