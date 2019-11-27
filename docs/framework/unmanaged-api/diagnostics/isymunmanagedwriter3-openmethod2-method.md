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
ms.openlocfilehash: 3a628aec0823c5db07d31d33813a020606906163
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438127"
---
# <a name="isymunmanagedwriter3openmethod2-method"></a><span data-ttu-id="58dc0-102">ISymUnmanagedWriter3::OpenMethod2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="58dc0-102">ISymUnmanagedWriter3::OpenMethod2 Method</span></span>
<span data-ttu-id="58dc0-103">Bir yöntemi açar ve görüntüde gerçek bölüm konumunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="58dc0-103">Opens a method and provides its real section offset in the image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58dc0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="58dc0-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenMethod2(   
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58dc0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="58dc0-105">Parameters</span></span>  
 `method`  
 <span data-ttu-id="58dc0-106">'ndaki Açılacak yöntemin meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="58dc0-106">[in] The metadata token for the method to be opened.</span></span>  
  
 `isect`  
 <span data-ttu-id="58dc0-107">'ndaki Görüntüdeki bölüm boşluğu.</span><span class="sxs-lookup"><span data-stu-id="58dc0-107">[in] The section offset in the image.</span></span>  
  
 `offset`  
 <span data-ttu-id="58dc0-108">'ndaki Görüntüdeki fark.</span><span class="sxs-lookup"><span data-stu-id="58dc0-108">[in] The offset in the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="58dc0-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="58dc0-109">Return Value</span></span>  
 <span data-ttu-id="58dc0-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="58dc0-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58dc0-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="58dc0-111">Requirements</span></span>  
 <span data-ttu-id="58dc0-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="58dc0-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58dc0-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58dc0-113">See also</span></span>

- [<span data-ttu-id="58dc0-114">ISymUnmanagedWriter3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="58dc0-114">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
- [<span data-ttu-id="58dc0-115">OpenMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="58dc0-115">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
