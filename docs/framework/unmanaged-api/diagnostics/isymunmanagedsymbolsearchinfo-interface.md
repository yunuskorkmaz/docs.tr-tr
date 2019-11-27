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
ms.openlocfilehash: d7371361b074454e8aa359c49b964193c12f3034
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446152"
---
# <a name="isymunmanagedsymbolsearchinfo-interface"></a><span data-ttu-id="a13d3-102">ISymUnmanagedSymbolSearchInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a13d3-102">ISymUnmanagedSymbolSearchInfo Interface</span></span>
<span data-ttu-id="a13d3-103">Arama yolu hakkında bilgi almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a13d3-103">Provides methods that get information about the search path.</span></span> <span data-ttu-id="a13d3-104">[Idimunmanagedreader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) arabirimini uygulayan bir nesne üzerinde `QueryInterface` çağırarak bu arabirimi elde edin.</span><span class="sxs-lookup"><span data-stu-id="a13d3-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a13d3-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a13d3-105">Methods</span></span>  
  
|<span data-ttu-id="a13d3-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a13d3-106">Method</span></span>|<span data-ttu-id="a13d3-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a13d3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a13d3-108">GetHRESULT Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a13d3-108">GetHRESULT Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-gethresult-method.md)|<span data-ttu-id="a13d3-109">HRESULT 'yi alır.</span><span class="sxs-lookup"><span data-stu-id="a13d3-109">Gets the HRESULT.</span></span>|  
|[<span data-ttu-id="a13d3-110">GetSearchPath Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a13d3-110">GetSearchPath Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpath-method.md)|<span data-ttu-id="a13d3-111">Arama yolunu alır.</span><span class="sxs-lookup"><span data-stu-id="a13d3-111">Gets the search path.</span></span>|  
|[<span data-ttu-id="a13d3-112">GetSearchPathLength Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a13d3-112">GetSearchPathLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-getsearchpathlength-method.md)|<span data-ttu-id="a13d3-113">Arama yolu uzunluğunu alır.</span><span class="sxs-lookup"><span data-stu-id="a13d3-113">Gets the search path length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a13d3-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a13d3-114">Requirements</span></span>  
 <span data-ttu-id="a13d3-115">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="a13d3-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a13d3-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a13d3-116">See also</span></span>

- [<span data-ttu-id="a13d3-117">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a13d3-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
