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
ms.openlocfilehash: e88a844a7f79f14c717a5966b345588b3b3b9f81
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609423"
---
# <a name="isymunmanagedwriter3openmethod2-method"></a><span data-ttu-id="13c21-102">ISymUnmanagedWriter3::OpenMethod2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="13c21-102">ISymUnmanagedWriter3::OpenMethod2 Method</span></span>
<span data-ttu-id="13c21-103">Bir yöntemi açar ve görüntüde gerçek bölüm konumunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="13c21-103">Opens a method and provides its real section offset in the image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13c21-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="13c21-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenMethod2(
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13c21-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="13c21-105">Parameters</span></span>  
 `method`  
 <span data-ttu-id="13c21-106">'ndaki Açılacak yöntemin meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="13c21-106">[in] The metadata token for the method to be opened.</span></span>  
  
 `isect`  
 <span data-ttu-id="13c21-107">'ndaki Görüntüdeki bölüm boşluğu.</span><span class="sxs-lookup"><span data-stu-id="13c21-107">[in] The section offset in the image.</span></span>  
  
 `offset`  
 <span data-ttu-id="13c21-108">'ndaki Görüntüdeki fark.</span><span class="sxs-lookup"><span data-stu-id="13c21-108">[in] The offset in the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13c21-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="13c21-109">Return Value</span></span>  
 <span data-ttu-id="13c21-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="13c21-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13c21-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="13c21-111">Requirements</span></span>  
 <span data-ttu-id="13c21-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="13c21-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13c21-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13c21-113">See also</span></span>

- [<span data-ttu-id="13c21-114">ISymUnmanagedWriter3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13c21-114">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)
- [<span data-ttu-id="13c21-115">OpenMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="13c21-115">OpenMethod Method</span></span>](isymunmanagedwriter-openmethod-method.md)
