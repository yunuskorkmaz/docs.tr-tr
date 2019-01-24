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
ms.openlocfilehash: f7905b3ee83378ed1a27501b082dbfca01d6436c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54688070"
---
# <a name="isymunmanagedencupdateupdatemethodlines-method"></a><span data-ttu-id="e6b80-102">ISymUnmanagedENCUpdate::UpdateMethodLines Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e6b80-102">ISymUnmanagedENCUpdate::UpdateMethodLines Method</span></span>
<span data-ttu-id="e6b80-103">Değil derlendiği ancak olan satırları bağımsız olarak taşınmış bir yöntem için satır bilgileri güncelleniyor sağlar.</span><span class="sxs-lookup"><span data-stu-id="e6b80-103">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="e6b80-104">Her deyim için bir delta izin verilir.</span><span class="sxs-lookup"><span data-stu-id="e6b80-104">A delta for each statement is allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6b80-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e6b80-105">Syntax</span></span>  
  
```  
HRESULT UpdateMethodLines(  
    [in]  mdMethodDef  mdMethodToken,  
    [in, size_is(cDeltas)] INT32*  pDeltas,  
    [in]  ULONG        cDeltas);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e6b80-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e6b80-106">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="e6b80-107">[in] Token metody meta veriler.</span><span class="sxs-lookup"><span data-stu-id="e6b80-107">[in] The metadata of the method token.</span></span>  
  
 `pDeltas`  
 <span data-ttu-id="e6b80-108">[in] Bir dizi `INT32` yöntem her bir dizi noktası için farkları gösteren değer.</span><span class="sxs-lookup"><span data-stu-id="e6b80-108">[in] An array of `INT32` values that indicates deltas for each sequence point in the method.</span></span>  
  
 `cDeltas`  
 <span data-ttu-id="e6b80-109">[in] A `ULONG` boyutunu içeren `pDeltas` parametresi.</span><span class="sxs-lookup"><span data-stu-id="e6b80-109">[in] A `ULONG` containing the size of the `pDeltas` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e6b80-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e6b80-110">Return Value</span></span>  
 <span data-ttu-id="e6b80-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="e6b80-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6b80-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e6b80-112">Requirements</span></span>  
 <span data-ttu-id="e6b80-113">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e6b80-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6b80-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6b80-114">See also</span></span>
- [<span data-ttu-id="e6b80-115">ISymUnmanagedENCUpdate Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e6b80-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
