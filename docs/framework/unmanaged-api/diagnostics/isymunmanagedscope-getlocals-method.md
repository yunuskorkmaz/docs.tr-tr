---
title: ISymUnmanagedScope::GetLocals Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetLocals
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetLocals
helpviewer_keywords:
- GetLocals method [.NET Framework debugging]
- ISymUnmanagedScope::GetLocals method [.NET Framework debugging]
ms.assetid: 17c45f15-8c44-44da-b070-f902077b36e4
topic_type:
- apiref
ms.openlocfilehash: 3a2045466340f92dd8421090c74a442068e8bfaf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731416"
---
# <a name="isymunmanagedscopegetlocals-method"></a><span data-ttu-id="07e4d-102">ISymUnmanagedScope::GetLocals Metodu</span><span class="sxs-lookup"><span data-stu-id="07e4d-102">ISymUnmanagedScope::GetLocals Method</span></span>

<span data-ttu-id="07e4d-103">Bu kapsam içinde tanımlanan yerel değişkenleri alır.</span><span class="sxs-lookup"><span data-stu-id="07e4d-103">Gets the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07e4d-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="07e4d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocals(  
    [in]  ULONG32  cLocals,  
    [out] ULONG32  *pcLocals,  
    [out, size_is(cLocals),  
        length_is(*pcLocals)] ISymUnmanagedVariable* locals[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07e4d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="07e4d-105">Parameters</span></span>  

 `cLocals`  
 <span data-ttu-id="07e4d-106">'ndaki `ULONG32` Dizi boyutunu belirten bir `locals` .</span><span class="sxs-lookup"><span data-stu-id="07e4d-106">[in] A `ULONG32` that indicates the size of the `locals` array.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="07e4d-107">dışı `ULONG32` Yerel değişkenleri içermesi için gereken arabellek boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="07e4d-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the local variables.</span></span>  
  
 `locals`  
 <span data-ttu-id="07e4d-108">dışı Yerel değişkenleri alan dizi.</span><span class="sxs-lookup"><span data-stu-id="07e4d-108">[out] The array that receives the local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="07e4d-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="07e4d-109">Return Value</span></span>  

 <span data-ttu-id="07e4d-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="07e4d-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07e4d-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="07e4d-111">Requirements</span></span>  

 <span data-ttu-id="07e4d-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="07e4d-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07e4d-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07e4d-113">See also</span></span>

- [<span data-ttu-id="07e4d-114">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="07e4d-114">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
