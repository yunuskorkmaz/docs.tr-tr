---
title: ISymUnmanagedSymbolSearchInfo Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedSymbolSearchInfo
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedSymbolSearchInfo
helpviewer_keywords: ISymUnmanagedSymbolSearchInfo interface [.NET Framework debugging]
ms.assetid: 30817373-0a21-49c1-a0c4-8e8daeecb8db
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 967511238dceb752ab30ce10dcaba8b65f4dd9fb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedsymbolsearchinfo-interface"></a><span data-ttu-id="1deae-102">ISymUnmanagedSymbolSearchInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1deae-102">ISymUnmanagedSymbolSearchInfo Interface</span></span>
<span data-ttu-id="1deae-103">Arama yolu hakkında bilgi edinme yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="1deae-103">Provides methods that get information about the search path.</span></span> <span data-ttu-id="1deae-104">Bu arabirim çağırarak elde `QueryInterface` uygulayan bir nesne üzerinde [Isymunmanagedreader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="1deae-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1deae-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1deae-105">Methods</span></span>  
  
|<span data-ttu-id="1deae-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1deae-106">Method</span></span>|<span data-ttu-id="1deae-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1deae-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1deae-108">GetHRESULT yöntemi</span><span class="sxs-lookup"><span data-stu-id="1deae-108">GetHRESULT Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-gethresult-method.md)|<span data-ttu-id="1deae-109">HRESULT alır.</span><span class="sxs-lookup"><span data-stu-id="1deae-109">Gets the HRESULT.</span></span>|  
|[<span data-ttu-id="1deae-110">GetSearchPath yöntemi</span><span class="sxs-lookup"><span data-stu-id="1deae-110">GetSearchPath Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpath-method.md)|<span data-ttu-id="1deae-111">Arama yolu alır.</span><span class="sxs-lookup"><span data-stu-id="1deae-111">Gets the search path.</span></span>|  
|[<span data-ttu-id="1deae-112">GetSearchPathLength yöntemi</span><span class="sxs-lookup"><span data-stu-id="1deae-112">GetSearchPathLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpathlength-method.md)|<span data-ttu-id="1deae-113">Arama yolu uzunluğunu alır.</span><span class="sxs-lookup"><span data-stu-id="1deae-113">Gets the search path length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1deae-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1deae-114">Requirements</span></span>  
 <span data-ttu-id="1deae-115">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1deae-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1deae-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1deae-116">See Also</span></span>  
 [<span data-ttu-id="1deae-117">Tanılama sembol deposu arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1deae-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
