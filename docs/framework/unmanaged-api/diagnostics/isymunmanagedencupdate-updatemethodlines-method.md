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
ms.openlocfilehash: 54789003f7454a65449e55ea4d990edd672d9c1b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774690"
---
# <a name="isymunmanagedencupdateupdatemethodlines-method"></a><span data-ttu-id="29316-102">ISymUnmanagedENCUpdate::UpdateMethodLines Yöntemi</span><span class="sxs-lookup"><span data-stu-id="29316-102">ISymUnmanagedENCUpdate::UpdateMethodLines Method</span></span>
<span data-ttu-id="29316-103">Değil derlendiği ancak olan satırları bağımsız olarak taşınmış bir yöntem için satır bilgileri güncelleniyor sağlar.</span><span class="sxs-lookup"><span data-stu-id="29316-103">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="29316-104">Her deyim için bir delta izin verilir.</span><span class="sxs-lookup"><span data-stu-id="29316-104">A delta for each statement is allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29316-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="29316-105">Syntax</span></span>  
  
```cpp  
HRESULT UpdateMethodLines(  
    [in]  mdMethodDef  mdMethodToken,  
    [in, size_is(cDeltas)] INT32*  pDeltas,  
    [in]  ULONG        cDeltas);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29316-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="29316-106">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="29316-107">[in] Token metody meta veriler.</span><span class="sxs-lookup"><span data-stu-id="29316-107">[in] The metadata of the method token.</span></span>  
  
 `pDeltas`  
 <span data-ttu-id="29316-108">[in] Bir dizi `INT32` yöntem her bir dizi noktası için farkları gösteren değer.</span><span class="sxs-lookup"><span data-stu-id="29316-108">[in] An array of `INT32` values that indicates deltas for each sequence point in the method.</span></span>  
  
 `cDeltas`  
 <span data-ttu-id="29316-109">[in] A `ULONG` boyutunu içeren `pDeltas` parametresi.</span><span class="sxs-lookup"><span data-stu-id="29316-109">[in] A `ULONG` containing the size of the `pDeltas` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29316-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="29316-110">Return Value</span></span>  
 <span data-ttu-id="29316-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="29316-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29316-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="29316-112">Requirements</span></span>  
 <span data-ttu-id="29316-113">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="29316-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29316-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29316-114">See also</span></span>

- [<span data-ttu-id="29316-115">ISymUnmanagedENCUpdate Arabirimi</span><span class="sxs-lookup"><span data-stu-id="29316-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
