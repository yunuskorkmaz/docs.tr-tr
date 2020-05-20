---
title: ISymUnmanagedMethod::GetScopeFromOffset Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetScopeFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetScopeFromOffset
helpviewer_keywords:
- GetScopeFromOffset method [.NET Framework debugging]
- ISymUnmanagedMethod::GetScopeFromOffset method [.NET Framework debugging]
ms.assetid: d14cf210-81f8-46e1-8b19-6ddec0ba8b11
topic_type:
- apiref
ms.openlocfilehash: 4eefd019280f501a6ce194e5ce84388e32cc66e1
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615169"
---
# <a name="isymunmanagedmethodgetscopefromoffset-method"></a><span data-ttu-id="fccc1-102">ISymUnmanagedMethod::GetScopeFromOffset Metodu</span><span class="sxs-lookup"><span data-stu-id="fccc1-102">ISymUnmanagedMethod::GetScopeFromOffset Method</span></span>
<span data-ttu-id="fccc1-103">Bu yöntem içinde verilen sapmayı kapsayan en kapsamlı sözcük kapsamını alır.</span><span class="sxs-lookup"><span data-stu-id="fccc1-103">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span> <span data-ttu-id="fccc1-104">Bu, yerel değişken aramalarını başlatmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fccc1-104">This can be used to start local variable searches.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fccc1-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="fccc1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetScopeFromOffset(  
    [in]  ULONG32 offset,  
    [out, retval] ISymUnmanagedScope**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fccc1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fccc1-106">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="fccc1-107">'ndaki `ULONG`Bu, sapmayı içeren bir.</span><span class="sxs-lookup"><span data-stu-id="fccc1-107">[in] A `ULONG` that contains the offset.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="fccc1-108">dışı Döndürülen [ıdimunmanagedscope](isymunmanagedscope-interface.md) arabirimine ayarlanmış bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fccc1-108">[out] A pointer that is set to the returned [ISymUnmanagedScope](isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fccc1-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fccc1-109">Return Value</span></span>  
 <span data-ttu-id="fccc1-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="fccc1-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fccc1-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fccc1-111">Requirements</span></span>  
 <span data-ttu-id="fccc1-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="fccc1-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fccc1-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fccc1-113">See also</span></span>

- [<span data-ttu-id="fccc1-114">ISymUnmanagedMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fccc1-114">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
