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
ms.openlocfilehash: 308c501e17446719067d2dc0580d698c1770bf53
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610671"
---
# <a name="isymunmanagedsymbolsearchinfo-interface"></a><span data-ttu-id="a575e-102">ISymUnmanagedSymbolSearchInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a575e-102">ISymUnmanagedSymbolSearchInfo Interface</span></span>
<span data-ttu-id="a575e-103">Arama yolu hakkında bilgi almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a575e-103">Provides methods that get information about the search path.</span></span> <span data-ttu-id="a575e-104">`QueryInterface` [Istreamunmanagedreader](isymunmanagedreader-interface.md) arabirimini uygulayan bir nesne çağırarak bu arabirimi elde edin.</span><span class="sxs-lookup"><span data-stu-id="a575e-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a575e-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a575e-105">Methods</span></span>  
  
|<span data-ttu-id="a575e-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a575e-106">Method</span></span>|<span data-ttu-id="a575e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a575e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a575e-108">GetHRESULT Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a575e-108">GetHRESULT Method</span></span>](isymunmanagedsymbolsearchinfo-gethresult-method.md)|<span data-ttu-id="a575e-109">HRESULT 'yi alır.</span><span class="sxs-lookup"><span data-stu-id="a575e-109">Gets the HRESULT.</span></span>|  
|[<span data-ttu-id="a575e-110">GetSearchPath Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a575e-110">GetSearchPath Method</span></span>](isymunmanagedsymbolsearchinfo-getsearchpath-method.md)|<span data-ttu-id="a575e-111">Arama yolunu alır.</span><span class="sxs-lookup"><span data-stu-id="a575e-111">Gets the search path.</span></span>|  
|[<span data-ttu-id="a575e-112">GetSearchPathLength Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a575e-112">GetSearchPathLength Method</span></span>](isymunmanagedsymbolsearchinfo-getsearchpathlength-method.md)|<span data-ttu-id="a575e-113">Arama yolu uzunluğunu alır.</span><span class="sxs-lookup"><span data-stu-id="a575e-113">Gets the search path length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a575e-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a575e-114">Requirements</span></span>  
 <span data-ttu-id="a575e-115">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="a575e-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a575e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a575e-116">See also</span></span>

- [<span data-ttu-id="a575e-117">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a575e-117">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
