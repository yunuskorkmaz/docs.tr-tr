---
description: 'Şu konuda daha fazla bilgi edinin: ıdimunmanagedscope:: GetChildren Yöntemi'
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
ms.openlocfilehash: 55d72c98d34fcb30a479611895228fbc1b9f7f55
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763507"
---
# <a name="isymunmanagedscopegetchildren-method"></a><span data-ttu-id="749de-103">ISymUnmanagedScope::GetChildren Metodu</span><span class="sxs-lookup"><span data-stu-id="749de-103">ISymUnmanagedScope::GetChildren Method</span></span>

<span data-ttu-id="749de-104">Bu kapsamın alt öğelerini alır.</span><span class="sxs-lookup"><span data-stu-id="749de-104">Gets the children of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="749de-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="749de-105">Syntax</span></span>  
  
```cpp  
HRESULT GetChildren(  
    [in]  ULONG32  cChildren,  
    [out] ULONG32  *pcChildren,  
    [out, size_is(cChildren),  
        length_is(*pcChildren)] ISymUnmanagedScope* children[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="749de-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="749de-106">Parameters</span></span>  

 `cChildren`  
 <span data-ttu-id="749de-107">'ndaki `ULONG32` Dizi boyutunu belirten bir `children` .</span><span class="sxs-lookup"><span data-stu-id="749de-107">[in] A `ULONG32` that indicates the size of the `children` array.</span></span>  
  
 `pcChildren`  
 <span data-ttu-id="749de-108">dışı `ULONG32` Alt öğeleri içermesi için gereken arabelleğin boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="749de-108">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the children.</span></span>  
  
 `children`  
 <span data-ttu-id="749de-109">dışı Döndürülen alt öğe dizisi.</span><span class="sxs-lookup"><span data-stu-id="749de-109">[out] The returned array of children.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="749de-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="749de-110">Return Value</span></span>  

 <span data-ttu-id="749de-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="749de-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="749de-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="749de-112">Requirements</span></span>  

 <span data-ttu-id="749de-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="749de-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="749de-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="749de-114">See also</span></span>

- [<span data-ttu-id="749de-115">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="749de-115">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
- [<span data-ttu-id="749de-116">GetParent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="749de-116">GetParent Method</span></span>](isymunmanagedscope-getparent-method.md)
