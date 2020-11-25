---
title: ISymUnmanagedENCUpdate::GetLocalVariables Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.GetLocalVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables method [.NET Framework debugging]
- GetLocalVariables method [.NET Framework debugging]
ms.assetid: 5c8840be-ffea-447f-9c8d-178f1eaf8d06
topic_type:
- apiref
ms.openlocfilehash: 9e907450b4ae985ee30d9958eec8baba797b495a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728608"
---
# <a name="isymunmanagedencupdategetlocalvariables-method"></a><span data-ttu-id="d7bf8-102">ISymUnmanagedENCUpdate::GetLocalVariables Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d7bf8-102">ISymUnmanagedENCUpdate::GetLocalVariables Method</span></span>

<span data-ttu-id="d7bf8-103">Yerel değişkenleri alır.</span><span class="sxs-lookup"><span data-stu-id="d7bf8-103">Gets the local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7bf8-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d7bf8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVariables(  
    [in]  mdMethodDef  mdMethodToken,  
    [in]  ULONG        cLocals,  
    [out, size_is(cLocals), length_is(*pceltFetched)]  
        ISymUnmanagedVariable *rgLocals[],  
    [out] ULONG        *pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7bf8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d7bf8-105">Parameters</span></span>  

 `mdMethodToken`  
 <span data-ttu-id="d7bf8-106">'ndaki Metodun meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="d7bf8-106">[in] The metadata token of the method.</span></span>  
  
 `cLocals`  
 <span data-ttu-id="d7bf8-107">'ndaki `ULONG` Parametresinin boyutunu gösteren bir `rgLocals` .</span><span class="sxs-lookup"><span data-stu-id="d7bf8-107">[in] A `ULONG` that indicates the size of the `rgLocals` parameter.</span></span>  
  
 `rgLocals`  
 <span data-ttu-id="d7bf8-108">dışı [Imımunmanagedvariable](isymunmanagedvariable-interface.md) örneklerinin döndürülen dizisi.</span><span class="sxs-lookup"><span data-stu-id="d7bf8-108">[out] The returned array of [ISymUnmanagedVariable](isymunmanagedvariable-interface.md) instances.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="d7bf8-109">dışı `ULONG` `rgLocals` Yerelleri içermesi için gereken arabellek boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d7bf8-109">[out] A pointer to a `ULONG` that receives the size of the `rgLocals` buffer required to contain the locals.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d7bf8-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d7bf8-110">Return Value</span></span>  

 <span data-ttu-id="d7bf8-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="d7bf8-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7bf8-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d7bf8-112">Requirements</span></span>  

 <span data-ttu-id="d7bf8-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="d7bf8-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7bf8-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d7bf8-114">See also</span></span>

- [<span data-ttu-id="d7bf8-115">ISymUnmanagedENCUpdate Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d7bf8-115">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)
