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
ms.openlocfilehash: 0c112819ef3bc4f9a7146ee80f55202ff89d689a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178323"
---
# <a name="isymunmanagedwriter3openmethod2-method"></a><span data-ttu-id="2c665-102">ISymUnmanagedWriter3::OpenMethod2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2c665-102">ISymUnmanagedWriter3::OpenMethod2 Method</span></span>
<span data-ttu-id="2c665-103">Bir yöntem açar ve görüntüde gerçek bölüm ofset sağlar.</span><span class="sxs-lookup"><span data-stu-id="2c665-103">Opens a method and provides its real section offset in the image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c665-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2c665-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenMethod2(
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c665-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2c665-105">Parameters</span></span>  
 `method`  
 <span data-ttu-id="2c665-106">[içinde] Açılacak yöntem için meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="2c665-106">[in] The metadata token for the method to be opened.</span></span>  
  
 `isect`  
 <span data-ttu-id="2c665-107">[içinde] Görüntüdeki bölüm ofset.</span><span class="sxs-lookup"><span data-stu-id="2c665-107">[in] The section offset in the image.</span></span>  
  
 `offset`  
 <span data-ttu-id="2c665-108">[içinde] Görüntüdeki ofset.</span><span class="sxs-lookup"><span data-stu-id="2c665-108">[in] The offset in the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2c665-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2c665-109">Return Value</span></span>  
 <span data-ttu-id="2c665-110">yöntem başarılı olursa S_OK; aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="2c665-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c665-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2c665-111">Requirements</span></span>  
 <span data-ttu-id="2c665-112">**Üstbilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2c665-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c665-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c665-113">See also</span></span>

- [<span data-ttu-id="2c665-114">ISymUnmanagedWriter3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2c665-114">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
- [<span data-ttu-id="2c665-115">OpenMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2c665-115">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
