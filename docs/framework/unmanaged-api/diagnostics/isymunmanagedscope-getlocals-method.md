---
description: 'Şu konuda daha fazla bilgi edinin: ıdimunmanagedscope:: GetLocals yöntemi'
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
ms.openlocfilehash: 6b20d8a79e826be0bd191d46e794f8dad45c4810
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763416"
---
# <a name="isymunmanagedscopegetlocals-method"></a><span data-ttu-id="469fa-103">ISymUnmanagedScope::GetLocals Metodu</span><span class="sxs-lookup"><span data-stu-id="469fa-103">ISymUnmanagedScope::GetLocals Method</span></span>

<span data-ttu-id="469fa-104">Bu kapsam içinde tanımlanan yerel değişkenleri alır.</span><span class="sxs-lookup"><span data-stu-id="469fa-104">Gets the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="469fa-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="469fa-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLocals(  
    [in]  ULONG32  cLocals,  
    [out] ULONG32  *pcLocals,  
    [out, size_is(cLocals),  
        length_is(*pcLocals)] ISymUnmanagedVariable* locals[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="469fa-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="469fa-106">Parameters</span></span>  

 `cLocals`  
 <span data-ttu-id="469fa-107">'ndaki `ULONG32` Dizi boyutunu belirten bir `locals` .</span><span class="sxs-lookup"><span data-stu-id="469fa-107">[in] A `ULONG32` that indicates the size of the `locals` array.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="469fa-108">dışı `ULONG32` Yerel değişkenleri içermesi için gereken arabellek boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="469fa-108">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the local variables.</span></span>  
  
 `locals`  
 <span data-ttu-id="469fa-109">dışı Yerel değişkenleri alan dizi.</span><span class="sxs-lookup"><span data-stu-id="469fa-109">[out] The array that receives the local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="469fa-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="469fa-110">Return Value</span></span>  

 <span data-ttu-id="469fa-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="469fa-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="469fa-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="469fa-112">Requirements</span></span>  

 <span data-ttu-id="469fa-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="469fa-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="469fa-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="469fa-114">See also</span></span>

- [<span data-ttu-id="469fa-115">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="469fa-115">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
