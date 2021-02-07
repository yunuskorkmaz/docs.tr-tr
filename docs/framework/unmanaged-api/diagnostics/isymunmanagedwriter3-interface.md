---
description: 'Daha fazla bilgi edinin: ISymUnmanagedWriter3 Interface'
title: ISymUnmanagedWriter3 Arabirimi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3
helpviewer_keywords:
- ISymUnmanagedWriter3 interface [.NET Framework debugging]
ms.assetid: a034c21e-e371-4360-b470-29e88288948f
topic_type:
- apiref
ms.openlocfilehash: 586220af85f193b43acf0578706d9f67e3e83386
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761739"
---
# <a name="isymunmanagedwriter3-interface"></a><span data-ttu-id="28d2b-103">ISymUnmanagedWriter3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="28d2b-103">ISymUnmanagedWriter3 Interface</span></span>

<span data-ttu-id="28d2b-104">Bir sembol yazıcısını temsil eder ve belgeleri, dizi noktalarını, sözcük temelli kapsamları ve değişkenleri tanımlamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="28d2b-104">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="28d2b-105">Bu arabirim [ıstreamunmanagedwriter](isymunmanagedwriter-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="28d2b-105">This interface extends the [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="28d2b-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="28d2b-106">Methods</span></span>  
  
|<span data-ttu-id="28d2b-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="28d2b-107">Method</span></span>|<span data-ttu-id="28d2b-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="28d2b-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="28d2b-109">COMMIT yöntemi</span><span class="sxs-lookup"><span data-stu-id="28d2b-109">Commit Method</span></span>](isymunmanagedwriter3-commit-method.md)|<span data-ttu-id="28d2b-110">Şimdiye kadar yazılı olan değişiklikleri akışa kaydeder.</span><span class="sxs-lookup"><span data-stu-id="28d2b-110">Commits the changes written so far to the stream.</span></span>|  
|[<span data-ttu-id="28d2b-111">OpenMethod2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="28d2b-111">OpenMethod2 Method</span></span>](isymunmanagedwriter3-openmethod2-method.md)|<span data-ttu-id="28d2b-112">Bir yöntemi açar ve görüntüde gerçek bölüm konumunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="28d2b-112">Opens a method and provides its real section offset in the image.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="28d2b-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="28d2b-113">Requirements</span></span>  

 <span data-ttu-id="28d2b-114">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="28d2b-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28d2b-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28d2b-115">See also</span></span>

- [<span data-ttu-id="28d2b-116">Tanılama Sembol Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="28d2b-116">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="28d2b-117">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="28d2b-117">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="28d2b-118">ISymUnmanagedWriter2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="28d2b-118">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)
