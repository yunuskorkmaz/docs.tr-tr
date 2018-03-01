---
title: ISymUnmanagedSymbolSearchInfo Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 441330471906a891646ad55eb73ec25b44800cbc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedsymbolsearchinfo-interface"></a><span data-ttu-id="76459-102">ISymUnmanagedSymbolSearchInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="76459-102">ISymUnmanagedSymbolSearchInfo Interface</span></span>
<span data-ttu-id="76459-103">Arama yolu hakkında bilgi edinme yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="76459-103">Provides methods that get information about the search path.</span></span> <span data-ttu-id="76459-104">Bu arabirim çağırarak elde `QueryInterface` uygulayan bir nesne üzerinde [Isymunmanagedreader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="76459-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="76459-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="76459-105">Methods</span></span>  
  
|<span data-ttu-id="76459-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="76459-106">Method</span></span>|<span data-ttu-id="76459-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="76459-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="76459-108">GetHRESULT Yöntemi</span><span class="sxs-lookup"><span data-stu-id="76459-108">GetHRESULT Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-gethresult-method.md)|<span data-ttu-id="76459-109">HRESULT alır.</span><span class="sxs-lookup"><span data-stu-id="76459-109">Gets the HRESULT.</span></span>|  
|[<span data-ttu-id="76459-110">GetSearchPath Yöntemi</span><span class="sxs-lookup"><span data-stu-id="76459-110">GetSearchPath Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpath-method.md)|<span data-ttu-id="76459-111">Arama yolu alır.</span><span class="sxs-lookup"><span data-stu-id="76459-111">Gets the search path.</span></span>|  
|[<span data-ttu-id="76459-112">GetSearchPathLength Yöntemi</span><span class="sxs-lookup"><span data-stu-id="76459-112">GetSearchPathLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpathlength-method.md)|<span data-ttu-id="76459-113">Arama yolu uzunluğunu alır.</span><span class="sxs-lookup"><span data-stu-id="76459-113">Gets the search path length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="76459-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="76459-114">Requirements</span></span>  
 <span data-ttu-id="76459-115">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="76459-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76459-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="76459-116">See Also</span></span>  
 [<span data-ttu-id="76459-117">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="76459-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
