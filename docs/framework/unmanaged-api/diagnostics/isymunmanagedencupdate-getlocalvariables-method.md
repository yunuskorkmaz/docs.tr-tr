---
description: 'Şu konuda daha fazla bilgi edinin: ırivmanagedencupdate:: GetLocalVariables Yöntemi'
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
ms.openlocfilehash: bc034603dd6a09ea78dad789e11ea951d65e839b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721469"
---
# <a name="isymunmanagedencupdategetlocalvariables-method"></a><span data-ttu-id="4170c-103">ISymUnmanagedENCUpdate::GetLocalVariables Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4170c-103">ISymUnmanagedENCUpdate::GetLocalVariables Method</span></span>

<span data-ttu-id="4170c-104">Yerel değişkenleri alır.</span><span class="sxs-lookup"><span data-stu-id="4170c-104">Gets the local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4170c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4170c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVariables(  
    [in]  mdMethodDef  mdMethodToken,  
    [in]  ULONG        cLocals,  
    [out, size_is(cLocals), length_is(*pceltFetched)]  
        ISymUnmanagedVariable *rgLocals[],  
    [out] ULONG        *pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4170c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4170c-106">Parameters</span></span>  

 `mdMethodToken`  
 <span data-ttu-id="4170c-107">'ndaki Metodun meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="4170c-107">[in] The metadata token of the method.</span></span>  
  
 `cLocals`  
 <span data-ttu-id="4170c-108">'ndaki `ULONG` Parametresinin boyutunu gösteren bir `rgLocals` .</span><span class="sxs-lookup"><span data-stu-id="4170c-108">[in] A `ULONG` that indicates the size of the `rgLocals` parameter.</span></span>  
  
 `rgLocals`  
 <span data-ttu-id="4170c-109">dışı [Imımunmanagedvariable](isymunmanagedvariable-interface.md) örneklerinin döndürülen dizisi.</span><span class="sxs-lookup"><span data-stu-id="4170c-109">[out] The returned array of [ISymUnmanagedVariable](isymunmanagedvariable-interface.md) instances.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="4170c-110">dışı `ULONG` `rgLocals` Yerelleri içermesi için gereken arabellek boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="4170c-110">[out] A pointer to a `ULONG` that receives the size of the `rgLocals` buffer required to contain the locals.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4170c-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4170c-111">Return Value</span></span>  

 <span data-ttu-id="4170c-112">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="4170c-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4170c-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4170c-113">Requirements</span></span>  

 <span data-ttu-id="4170c-114">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="4170c-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4170c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4170c-115">See also</span></span>

- [<span data-ttu-id="4170c-116">ISymUnmanagedENCUpdate Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4170c-116">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)
