---
title: ISymUnmanagedWriter2 Arabirimi
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
- ISymUnmanagedWriter2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2
helpviewer_keywords:
- ISymUnmanagedWriter2 interface [.NET Framework debugging]
ms.assetid: 8e78faa4-cf43-44fb-a91d-94d6df692a25
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 98461cd2c2bc26d78f3f3f747b95d46576ba01e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter2-interface"></a><span data-ttu-id="6c605-102">ISymUnmanagedWriter2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6c605-102">ISymUnmanagedWriter2 Interface</span></span>
<span data-ttu-id="6c605-103">Sembol yazıcıyı temsil eder ve belgeleri, sıralama noktaları, sözcük kapsamlar ve değişkenleri tanımlamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c605-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="6c605-104">Bu arabirim genişletir [Isymunmanagedwriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="6c605-104">This interface extends the [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6c605-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6c605-105">Methods</span></span>  
  
|<span data-ttu-id="6c605-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6c605-106">Method</span></span>|<span data-ttu-id="6c605-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c605-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6c605-108">DefineConstant2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6c605-108">DefineConstant2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineconstant2-method.md)|<span data-ttu-id="6c605-109">Sabit bir değer için bir ad tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6c605-109">Defines a name for a constant value.</span></span>|  
|[<span data-ttu-id="6c605-110">DefineGlobalVariable2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6c605-110">DefineGlobalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineglobalvariable2-method.md)|<span data-ttu-id="6c605-111">Tek bir genel değişkeni tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6c605-111">Defines a single global variable.</span></span>|  
|[<span data-ttu-id="6c605-112">DefineLocalVariable2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6c605-112">DefineLocalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)|<span data-ttu-id="6c605-113">Tek bir değişken geçerli sözcük kapsamda tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6c605-113">Defines a single variable in the current lexical scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6c605-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6c605-114">Requirements</span></span>  
 <span data-ttu-id="6c605-115">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6c605-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c605-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6c605-116">See Also</span></span>  
 [<span data-ttu-id="6c605-117">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6c605-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="6c605-118">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6c605-118">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="6c605-119">ISymUnmanagedWriter3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6c605-119">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
