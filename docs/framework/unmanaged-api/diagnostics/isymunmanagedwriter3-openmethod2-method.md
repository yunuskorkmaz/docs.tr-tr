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
ms.openlocfilehash: b641f463eb9b664597b4806a6353278e8027d5b8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709110"
---
# <a name="isymunmanagedwriter3openmethod2-method"></a><span data-ttu-id="1d523-102">ISymUnmanagedWriter3::OpenMethod2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1d523-102">ISymUnmanagedWriter3::OpenMethod2 Method</span></span>
<span data-ttu-id="1d523-103">Bir yöntem açılır ve gerçek bölüm uzaklığı görüntüde sağlar.</span><span class="sxs-lookup"><span data-stu-id="1d523-103">Opens a method and provides its real section offset in the image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d523-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1d523-104">Syntax</span></span>  
  
```  
HRESULT OpenMethod2(   
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1d523-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1d523-105">Parameters</span></span>  
 `method`  
 <span data-ttu-id="1d523-106">[in] Meta veri belirteci açılması yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1d523-106">[in] The metadata token for the method to be opened.</span></span>  
  
 `isect`  
 <span data-ttu-id="1d523-107">[in] Görüntüde bölüm uzaklık.</span><span class="sxs-lookup"><span data-stu-id="1d523-107">[in] The section offset in the image.</span></span>  
  
 `offset`  
 <span data-ttu-id="1d523-108">[in] Görüntüde uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="1d523-108">[in] The offset in the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1d523-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1d523-109">Return Value</span></span>  
 <span data-ttu-id="1d523-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="1d523-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d523-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1d523-111">Requirements</span></span>  
 <span data-ttu-id="1d523-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1d523-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d523-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d523-113">See also</span></span>
- [<span data-ttu-id="1d523-114">ISymUnmanagedWriter3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1d523-114">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
- [<span data-ttu-id="1d523-115">OpenMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1d523-115">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
