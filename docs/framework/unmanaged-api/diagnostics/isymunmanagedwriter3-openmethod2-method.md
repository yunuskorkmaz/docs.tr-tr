---
title: ISymUnmanagedWriter3::OpenMethod2 Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3.OpenMethod2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3::OpenMethod2
helpviewer_keywords:
- ISymUnmanagedWriter3::OpenMethod2 method [.NET Framework debugging]
- OpenMethod2 method [.NET Framework debugging]
ms.assetid: 025e358c-448f-4423-a2f2-57acf437c8a5
topic_type:
- apiref
ms.openlocfilehash: 39235c5c26cb168dfc995de97f72b80dccb6b818
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720301"
---
# <a name="isymunmanagedwriter3openmethod2-method"></a><span data-ttu-id="f9bb3-102">ISymUnmanagedWriter3::OpenMethod2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f9bb3-102">ISymUnmanagedWriter3::OpenMethod2 Method</span></span>

<span data-ttu-id="f9bb3-103">Bir yöntemi açar ve görüntüde gerçek bölüm konumunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="f9bb3-103">Opens a method and provides its real section offset in the image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9bb3-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f9bb3-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenMethod2(
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9bb3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f9bb3-105">Parameters</span></span>  

 `method`  
 <span data-ttu-id="f9bb3-106">'ndaki Açılacak yöntemin meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="f9bb3-106">[in] The metadata token for the method to be opened.</span></span>  
  
 `isect`  
 <span data-ttu-id="f9bb3-107">'ndaki Görüntüdeki bölüm boşluğu.</span><span class="sxs-lookup"><span data-stu-id="f9bb3-107">[in] The section offset in the image.</span></span>  
  
 `offset`  
 <span data-ttu-id="f9bb3-108">'ndaki Görüntüdeki fark.</span><span class="sxs-lookup"><span data-stu-id="f9bb3-108">[in] The offset in the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f9bb3-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f9bb3-109">Return Value</span></span>  

 <span data-ttu-id="f9bb3-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="f9bb3-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9bb3-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f9bb3-111">Requirements</span></span>  

 <span data-ttu-id="f9bb3-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="f9bb3-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9bb3-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9bb3-113">See also</span></span>

- [<span data-ttu-id="f9bb3-114">ISymUnmanagedWriter3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f9bb3-114">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)
- [<span data-ttu-id="f9bb3-115">OpenMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f9bb3-115">OpenMethod Method</span></span>](isymunmanagedwriter-openmethod-method.md)
