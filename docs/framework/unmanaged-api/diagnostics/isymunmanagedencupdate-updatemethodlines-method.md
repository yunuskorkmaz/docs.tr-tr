---
title: ISymUnmanagedENCUpdate::UpdateMethodLines Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.UpdateMethodLines
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::UpdateMethodLines
helpviewer_keywords:
- UpdateMethodLines method [.NET Framework debugging]
- ISymUnmanagedENCUpdate::UpdateMethodLines method [.NET Framework debugging]
ms.assetid: 275ef87b-0b53-49f9-af6b-58506335dc06
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bd1f101e2e9cf9baeb28290c7607ccab3d8d7440
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178925"
---
# <a name="isymunmanagedencupdateupdatemethodlines-method"></a><span data-ttu-id="124b1-102">ISymUnmanagedENCUpdate::UpdateMethodLines Yöntemi</span><span class="sxs-lookup"><span data-stu-id="124b1-102">ISymUnmanagedENCUpdate::UpdateMethodLines Method</span></span>
<span data-ttu-id="124b1-103">Değil derlendiği ancak olan satırları bağımsız olarak taşınmış bir yöntem için satır bilgileri güncelleniyor sağlar.</span><span class="sxs-lookup"><span data-stu-id="124b1-103">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="124b1-104">Her deyim için bir delta izin verilir.</span><span class="sxs-lookup"><span data-stu-id="124b1-104">A delta for each statement is allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="124b1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="124b1-105">Syntax</span></span>  
  
```  
HRESULT UpdateMethodLines(  
    [in]  mdMethodDef  mdMethodToken,  
    [in, size_is(cDeltas)] INT32*  pDeltas,  
    [in]  ULONG        cDeltas);  
```  
  
## <a name="parameters"></a><span data-ttu-id="124b1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="124b1-106">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="124b1-107">[in] Token metody meta veriler.</span><span class="sxs-lookup"><span data-stu-id="124b1-107">[in] The metadata of the method token.</span></span>  
  
 `pDeltas`  
 <span data-ttu-id="124b1-108">[in] Bir dizi `INT32` yöntem her bir dizi noktası için farkları gösteren değer.</span><span class="sxs-lookup"><span data-stu-id="124b1-108">[in] An array of `INT32` values that indicates deltas for each sequence point in the method.</span></span>  
  
 `cDeltas`  
 <span data-ttu-id="124b1-109">[in] A `ULONG` boyutunu içeren `pDeltas` parametresi.</span><span class="sxs-lookup"><span data-stu-id="124b1-109">[in] A `ULONG` containing the size of the `pDeltas` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="124b1-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="124b1-110">Return Value</span></span>  
 <span data-ttu-id="124b1-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="124b1-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="124b1-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="124b1-112">Requirements</span></span>  
 <span data-ttu-id="124b1-113">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="124b1-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="124b1-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="124b1-114">See also</span></span>

- [<span data-ttu-id="124b1-115">ISymUnmanagedENCUpdate Arabirimi</span><span class="sxs-lookup"><span data-stu-id="124b1-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
