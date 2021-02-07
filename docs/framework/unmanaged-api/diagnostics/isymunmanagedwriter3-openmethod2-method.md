---
description: 'Daha fazla bilgi edinin: ISymUnmanagedWriter3:: OpenMethod2 Yöntemi'
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
ms.openlocfilehash: 7e76be03598599a6498ed45bc3799c6d6f21e088
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761700"
---
# <a name="isymunmanagedwriter3openmethod2-method"></a><span data-ttu-id="ce62a-103">ISymUnmanagedWriter3::OpenMethod2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ce62a-103">ISymUnmanagedWriter3::OpenMethod2 Method</span></span>

<span data-ttu-id="ce62a-104">Bir yöntemi açar ve görüntüde gerçek bölüm konumunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="ce62a-104">Opens a method and provides its real section offset in the image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce62a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ce62a-105">Syntax</span></span>  
  
```cpp  
HRESULT OpenMethod2(
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce62a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ce62a-106">Parameters</span></span>  

 `method`  
 <span data-ttu-id="ce62a-107">'ndaki Açılacak yöntemin meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="ce62a-107">[in] The metadata token for the method to be opened.</span></span>  
  
 `isect`  
 <span data-ttu-id="ce62a-108">'ndaki Görüntüdeki bölüm boşluğu.</span><span class="sxs-lookup"><span data-stu-id="ce62a-108">[in] The section offset in the image.</span></span>  
  
 `offset`  
 <span data-ttu-id="ce62a-109">'ndaki Görüntüdeki fark.</span><span class="sxs-lookup"><span data-stu-id="ce62a-109">[in] The offset in the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ce62a-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ce62a-110">Return Value</span></span>  

 <span data-ttu-id="ce62a-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="ce62a-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce62a-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ce62a-112">Requirements</span></span>  

 <span data-ttu-id="ce62a-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="ce62a-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce62a-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce62a-114">See also</span></span>

- [<span data-ttu-id="ce62a-115">ISymUnmanagedWriter3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ce62a-115">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)
- [<span data-ttu-id="ce62a-116">OpenMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ce62a-116">OpenMethod Method</span></span>](isymunmanagedwriter-openmethod-method.md)
