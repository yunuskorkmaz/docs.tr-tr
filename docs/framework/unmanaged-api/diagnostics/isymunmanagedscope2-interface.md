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
ms.openlocfilehash: 886ba693183a6b99eb03635e95a9661d105de40e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610866"
---
# <a name="isymunmanagedscope2-interface"></a><span data-ttu-id="c5a39-102">ISymUnmanagedScope2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c5a39-102">ISymUnmanagedScope2 Interface</span></span>
<span data-ttu-id="c5a39-103">Bir yöntem içindeki bir sözcük temelli kapsamı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c5a39-103">Represents a lexical scope within a method.</span></span> <span data-ttu-id="c5a39-104">Bu arabirim, [ıstreamunmanagedscope](isymunmanagedscope-interface.md) arabirimini kapsam içinde tanımlanan sabitler hakkında bilgi alan yöntemlerle genişletir.</span><span class="sxs-lookup"><span data-stu-id="c5a39-104">This interface extends the [ISymUnmanagedScope](isymunmanagedscope-interface.md) interface with methods that get information about constants defined within the scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c5a39-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c5a39-105">Methods</span></span>  
  
|<span data-ttu-id="c5a39-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c5a39-106">Method</span></span>|<span data-ttu-id="c5a39-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5a39-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c5a39-108">GetConstantCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c5a39-108">GetConstantCount Method</span></span>](isymunmanagedscope2-getconstantcount-method.md)|<span data-ttu-id="c5a39-109">Bu kapsam içinde tanımlanan sabitlerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="c5a39-109">Gets a count of the constants defined within this scope.</span></span>|  
|[<span data-ttu-id="c5a39-110">GetConstants Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c5a39-110">GetConstants Method</span></span>](isymunmanagedscope2-getconstants-method.md)|<span data-ttu-id="c5a39-111">Bu kapsam içinde tanımlanan yerel sabitleri alır.</span><span class="sxs-lookup"><span data-stu-id="c5a39-111">Gets the local constants defined within this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c5a39-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c5a39-112">Requirements</span></span>  
 <span data-ttu-id="c5a39-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="c5a39-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5a39-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5a39-114">See also</span></span>

- [<span data-ttu-id="c5a39-115">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c5a39-115">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="c5a39-116">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c5a39-116">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
