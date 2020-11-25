---
title: ISymUnmanagedDispose Arabirimi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDispose
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDispose
helpviewer_keywords:
- ISymUnmanagedDispose interface [.NET Framework debugging]
ms.assetid: b1d74e83-a200-4d00-8fbd-27918808616d
topic_type:
- apiref
ms.openlocfilehash: 932e76e73d5d40b36abcb17d8a53e6745927d873
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719612"
---
# <a name="isymunmanageddispose-interface"></a><span data-ttu-id="054e7-102">ISymUnmanagedDispose Arabirimi</span><span class="sxs-lookup"><span data-stu-id="054e7-102">ISymUnmanagedDispose Interface</span></span>

<span data-ttu-id="054e7-103">Yönetilmeyen kaynakları ortadan kaldırın.</span><span class="sxs-lookup"><span data-stu-id="054e7-103">Disposes of unmanaged resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="054e7-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="054e7-104">Methods</span></span>  
  
|<span data-ttu-id="054e7-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="054e7-105">Method</span></span>|<span data-ttu-id="054e7-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="054e7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="054e7-107">Destroy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="054e7-107">Destroy Method</span></span>](isymunmanageddispose-destroy-method.md)|<span data-ttu-id="054e7-108">Alttaki nesnenin tüm iç başvuruları serbest bırakmaya ve sonraki yöntem çağrılarında hata döndürmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="054e7-108">Causes the underlying object to release all internal references and return failure on any subsequent method calls.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="054e7-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="054e7-109">Requirements</span></span>  

 <span data-ttu-id="054e7-110">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="054e7-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="054e7-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="054e7-111">See also</span></span>

- [<span data-ttu-id="054e7-112">Tanılama Sembol Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="054e7-112">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
