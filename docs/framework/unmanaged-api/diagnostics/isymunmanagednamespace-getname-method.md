---
title: ISymUnmanagedNamespace::GetName Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetName
helpviewer_keywords:
- ISymUnmanagedNamespace::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: 657bf91d-005a-4ea4-9298-04d1291c0bc3
topic_type:
- apiref
ms.openlocfilehash: 84b2f1226c84713483499c7ff777838058cb0f95
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615117"
---
# <a name="isymunmanagednamespacegetname-method"></a><span data-ttu-id="106fe-102">ISymUnmanagedNamespace::GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="106fe-102">ISymUnmanagedNamespace::GetName Method</span></span>
<span data-ttu-id="106fe-103">Bu ad alanının adını alır.</span><span class="sxs-lookup"><span data-stu-id="106fe-103">Gets the name of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="106fe-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="106fe-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="106fe-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="106fe-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="106fe-106">'ndaki `ULONG32`Arabellek boyutunu belirten bir `szName` .</span><span class="sxs-lookup"><span data-stu-id="106fe-106">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="106fe-107">dışı `ULONG32`Null sonlandırma dahil olmak üzere ad alanı adını içermesi için gereken arabelleğin karakter cinsinden boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="106fe-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespace name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="106fe-108">dışı Ad alanı adını içeren bir arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="106fe-108">[out] A pointer to a buffer that contains the namespace name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="106fe-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="106fe-109">Return Value</span></span>  
 <span data-ttu-id="106fe-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="106fe-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="106fe-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="106fe-111">Requirements</span></span>  
 <span data-ttu-id="106fe-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="106fe-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="106fe-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="106fe-113">See also</span></span>

- [<span data-ttu-id="106fe-114">ISymUnmanagedNamespace Arabirimi</span><span class="sxs-lookup"><span data-stu-id="106fe-114">ISymUnmanagedNamespace Interface</span></span>](isymunmanagednamespace-interface.md)
