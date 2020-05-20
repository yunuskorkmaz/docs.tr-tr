---
title: ISymUnmanagedScope::GetChildren Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetChildren
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetChildren
helpviewer_keywords:
- ISymUnmanagedScope::GetChildren method [.NET Framework debugging]
- GetChildren method [.NET Framework debugging]
ms.assetid: 0bed524e-cc48-4bf0-b9fa-25d665e63ddb
topic_type:
- apiref
ms.openlocfilehash: c6d21f40c260890c9c88dcdfccd7e31161024ba3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614870"
---
# <a name="isymunmanagedscopegetchildren-method"></a><span data-ttu-id="07832-102">ISymUnmanagedScope::GetChildren Metodu</span><span class="sxs-lookup"><span data-stu-id="07832-102">ISymUnmanagedScope::GetChildren Method</span></span>
<span data-ttu-id="07832-103">Bu kapsamın alt öğelerini alır.</span><span class="sxs-lookup"><span data-stu-id="07832-103">Gets the children of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07832-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="07832-104">Syntax</span></span>  
  
```cpp  
HRESULT GetChildren(  
    [in]  ULONG32  cChildren,  
    [out] ULONG32  *pcChildren,  
    [out, size_is(cChildren),  
        length_is(*pcChildren)] ISymUnmanagedScope* children[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07832-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="07832-105">Parameters</span></span>  
 `cChildren`  
 <span data-ttu-id="07832-106">'ndaki `ULONG32`Dizi boyutunu belirten bir `children` .</span><span class="sxs-lookup"><span data-stu-id="07832-106">[in] A `ULONG32` that indicates the size of the `children` array.</span></span>  
  
 `pcChildren`  
 <span data-ttu-id="07832-107">dışı `ULONG32`Alt öğeleri içermesi için gereken arabelleğin boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="07832-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the children.</span></span>  
  
 `children`  
 <span data-ttu-id="07832-108">dışı Döndürülen alt öğe dizisi.</span><span class="sxs-lookup"><span data-stu-id="07832-108">[out] The returned array of children.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="07832-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="07832-109">Return Value</span></span>  
 <span data-ttu-id="07832-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="07832-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07832-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="07832-111">Requirements</span></span>  
 <span data-ttu-id="07832-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="07832-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07832-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07832-113">See also</span></span>

- [<span data-ttu-id="07832-114">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="07832-114">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
- [<span data-ttu-id="07832-115">GetParent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="07832-115">GetParent Method</span></span>](isymunmanagedscope-getparent-method.md)
