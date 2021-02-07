---
description: 'Şu konuda daha fazla bilgi edinin: ırivmanagedencupdate:: UpdateMethodLines yöntemi'
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
ms.openlocfilehash: 6174f3aa980ccf2cdc07720e3aa90b7bb74a77af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710068"
---
# <a name="isymunmanagedencupdateupdatemethodlines-method"></a><span data-ttu-id="754fc-103">ISymUnmanagedENCUpdate::UpdateMethodLines Yöntemi</span><span class="sxs-lookup"><span data-stu-id="754fc-103">ISymUnmanagedENCUpdate::UpdateMethodLines Method</span></span>

<span data-ttu-id="754fc-104">Yeniden derlenmedi ancak satırları bağımsız olarak taşınmış olan bir yöntem için satır bilgilerinin güncelleştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="754fc-104">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="754fc-105">Her ifadeye yönelik bir Delta kullanımına izin verilir.</span><span class="sxs-lookup"><span data-stu-id="754fc-105">A delta for each statement is allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="754fc-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="754fc-106">Syntax</span></span>  
  
```cpp  
HRESULT UpdateMethodLines(  
    [in]  mdMethodDef  mdMethodToken,  
    [in, size_is(cDeltas)] INT32*  pDeltas,  
    [in]  ULONG        cDeltas);  
```  
  
## <a name="parameters"></a><span data-ttu-id="754fc-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="754fc-107">Parameters</span></span>  

 `mdMethodToken`  
 <span data-ttu-id="754fc-108">'ndaki Yöntem belirtecinin meta verileri.</span><span class="sxs-lookup"><span data-stu-id="754fc-108">[in] The metadata of the method token.</span></span>  
  
 `pDeltas`  
 <span data-ttu-id="754fc-109">'ndaki `INT32` Yöntemdeki her bir sıra noktası için değişimleri 'yi gösteren bir değerler dizisi.</span><span class="sxs-lookup"><span data-stu-id="754fc-109">[in] An array of `INT32` values that indicates deltas for each sequence point in the method.</span></span>  
  
 `cDeltas`  
 <span data-ttu-id="754fc-110">'ndaki `ULONG` Parametresinin boyutunu içeren bir `pDeltas` .</span><span class="sxs-lookup"><span data-stu-id="754fc-110">[in] A `ULONG` containing the size of the `pDeltas` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="754fc-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="754fc-111">Return Value</span></span>  

 <span data-ttu-id="754fc-112">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="754fc-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="754fc-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="754fc-113">Requirements</span></span>  

 <span data-ttu-id="754fc-114">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="754fc-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="754fc-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="754fc-115">See also</span></span>

- [<span data-ttu-id="754fc-116">ISymUnmanagedENCUpdate Arabirimi</span><span class="sxs-lookup"><span data-stu-id="754fc-116">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)
