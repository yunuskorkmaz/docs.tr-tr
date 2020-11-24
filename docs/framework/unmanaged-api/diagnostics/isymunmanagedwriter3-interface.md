---
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
ms.openlocfilehash: dfc2e39a6a39e7386bd7358d422d5c6978ec42ec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683296"
---
# <a name="isymunmanagedwriter3-interface"></a><span data-ttu-id="119eb-102">ISymUnmanagedWriter3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="119eb-102">ISymUnmanagedWriter3 Interface</span></span>

<span data-ttu-id="119eb-103">Bir sembol yazıcısını temsil eder ve belgeleri, dizi noktalarını, sözcük temelli kapsamları ve değişkenleri tanımlamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="119eb-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="119eb-104">Bu arabirim [ıstreamunmanagedwriter](isymunmanagedwriter-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="119eb-104">This interface extends the [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="119eb-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="119eb-105">Methods</span></span>  
  
|<span data-ttu-id="119eb-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="119eb-106">Method</span></span>|<span data-ttu-id="119eb-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="119eb-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="119eb-108">COMMIT yöntemi</span><span class="sxs-lookup"><span data-stu-id="119eb-108">Commit Method</span></span>](isymunmanagedwriter3-commit-method.md)|<span data-ttu-id="119eb-109">Şimdiye kadar yazılı olan değişiklikleri akışa kaydeder.</span><span class="sxs-lookup"><span data-stu-id="119eb-109">Commits the changes written so far to the stream.</span></span>|  
|[<span data-ttu-id="119eb-110">OpenMethod2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="119eb-110">OpenMethod2 Method</span></span>](isymunmanagedwriter3-openmethod2-method.md)|<span data-ttu-id="119eb-111">Bir yöntemi açar ve görüntüde gerçek bölüm konumunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="119eb-111">Opens a method and provides its real section offset in the image.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="119eb-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="119eb-112">Requirements</span></span>  

 <span data-ttu-id="119eb-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="119eb-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="119eb-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="119eb-114">See also</span></span>

- [<span data-ttu-id="119eb-115">Tanılama Sembol Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="119eb-115">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="119eb-116">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="119eb-116">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="119eb-117">ISymUnmanagedWriter2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="119eb-117">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)
