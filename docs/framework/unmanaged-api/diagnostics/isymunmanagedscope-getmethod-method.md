---
title: ISymUnmanagedScope::GetMethod Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetMethod
helpviewer_keywords:
- GetMethod method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetMethod method [.NET Framework debugging]
ms.assetid: a61866ee-221a-45b9-a1b7-395825b77872
topic_type:
- apiref
ms.openlocfilehash: cdbffe71540b51ff539a45861546efd761761892
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615377"
---
# <a name="isymunmanagedscopegetmethod-method"></a><span data-ttu-id="f4d6d-102">ISymUnmanagedScope::GetMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4d6d-102">ISymUnmanagedScope::GetMethod Method</span></span>
<span data-ttu-id="f4d6d-103">Bu kapsamı içeren yöntemi alır.</span><span class="sxs-lookup"><span data-stu-id="f4d6d-103">Gets the method that contains this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4d6d-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f4d6d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethod(  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4d6d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f4d6d-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="f4d6d-106">dışı Döndürülen [ıdimunmanagedmethod](isymunmanagedmethod-interface.md) arabirimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f4d6d-106">[out] A pointer to the returned [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f4d6d-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f4d6d-107">Return Value</span></span>  
 <span data-ttu-id="f4d6d-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="f4d6d-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4d6d-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f4d6d-109">Requirements</span></span>  
 <span data-ttu-id="f4d6d-110">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="f4d6d-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4d6d-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4d6d-111">See also</span></span>

- [<span data-ttu-id="f4d6d-112">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f4d6d-112">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
