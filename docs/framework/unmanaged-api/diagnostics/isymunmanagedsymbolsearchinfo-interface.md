---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagedsymbolsearchınfo arabirimi'
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
ms.openlocfilehash: 2f2ab198d2c54a9fcc5fa2e24b9196a38c583f81
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762987"
---
# <a name="isymunmanagedsymbolsearchinfo-interface"></a><span data-ttu-id="8a570-103">ISymUnmanagedSymbolSearchInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8a570-103">ISymUnmanagedSymbolSearchInfo Interface</span></span>

<span data-ttu-id="8a570-104">Arama yolu hakkında bilgi almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="8a570-104">Provides methods that get information about the search path.</span></span> <span data-ttu-id="8a570-105">`QueryInterface` [Istreamunmanagedreader](isymunmanagedreader-interface.md) arabirimini uygulayan bir nesne çağırarak bu arabirimi elde edin.</span><span class="sxs-lookup"><span data-stu-id="8a570-105">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8a570-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8a570-106">Methods</span></span>  
  
|<span data-ttu-id="8a570-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8a570-107">Method</span></span>|<span data-ttu-id="8a570-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8a570-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8a570-109">GetHRESULT Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8a570-109">GetHRESULT Method</span></span>](isymunmanagedsymbolsearchinfo-gethresult-method.md)|<span data-ttu-id="8a570-110">HRESULT 'yi alır.</span><span class="sxs-lookup"><span data-stu-id="8a570-110">Gets the HRESULT.</span></span>|  
|[<span data-ttu-id="8a570-111">GetSearchPath Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8a570-111">GetSearchPath Method</span></span>](isymunmanagedsymbolsearchinfo-getsearchpath-method.md)|<span data-ttu-id="8a570-112">Arama yolunu alır.</span><span class="sxs-lookup"><span data-stu-id="8a570-112">Gets the search path.</span></span>|  
|[<span data-ttu-id="8a570-113">GetSearchPathLength Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8a570-113">GetSearchPathLength Method</span></span>](isymunmanagedsymbolsearchinfo-getsearchpathlength-method.md)|<span data-ttu-id="8a570-114">Arama yolu uzunluğunu alır.</span><span class="sxs-lookup"><span data-stu-id="8a570-114">Gets the search path length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8a570-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8a570-115">Requirements</span></span>  

 <span data-ttu-id="8a570-116">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="8a570-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a570-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a570-117">See also</span></span>

- [<span data-ttu-id="8a570-118">Tanılama Sembol Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8a570-118">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
