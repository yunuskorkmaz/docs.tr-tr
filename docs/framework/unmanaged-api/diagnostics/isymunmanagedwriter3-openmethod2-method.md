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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 14a8acc2e3babd376cb9754d35ce8fc5eaa1fd7c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492328"
---
# <a name="isymunmanagedwriter3openmethod2-method"></a><span data-ttu-id="7a799-102">ISymUnmanagedWriter3::OpenMethod2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7a799-102">ISymUnmanagedWriter3::OpenMethod2 Method</span></span>
<span data-ttu-id="7a799-103">Bir yöntem açılır ve gerçek bölüm uzaklığı görüntüde sağlar.</span><span class="sxs-lookup"><span data-stu-id="7a799-103">Opens a method and provides its real section offset in the image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a799-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7a799-104">Syntax</span></span>  
  
```  
HRESULT OpenMethod2(   
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a799-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7a799-105">Parameters</span></span>  
 `method`  
 <span data-ttu-id="7a799-106">[in] Meta veri belirteci açılması yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7a799-106">[in] The metadata token for the method to be opened.</span></span>  
  
 `isect`  
 <span data-ttu-id="7a799-107">[in] Görüntüde bölüm uzaklık.</span><span class="sxs-lookup"><span data-stu-id="7a799-107">[in] The section offset in the image.</span></span>  
  
 `offset`  
 <span data-ttu-id="7a799-108">[in] Görüntüde uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="7a799-108">[in] The offset in the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7a799-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7a799-109">Return Value</span></span>  
 <span data-ttu-id="7a799-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="7a799-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a799-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7a799-111">Requirements</span></span>  
 <span data-ttu-id="7a799-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7a799-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a799-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a799-113">See also</span></span>
- [<span data-ttu-id="7a799-114">ISymUnmanagedWriter3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7a799-114">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
- [<span data-ttu-id="7a799-115">OpenMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7a799-115">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
