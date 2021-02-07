---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagednamespace:: GetName Yöntemi'
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
ms.openlocfilehash: f4d366363cd089995f98039389f59077e949fb79
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721222"
---
# <a name="isymunmanagednamespacegetname-method"></a><span data-ttu-id="8e11c-103">ISymUnmanagedNamespace::GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8e11c-103">ISymUnmanagedNamespace::GetName Method</span></span>

<span data-ttu-id="8e11c-104">Bu ad alanının adını alır.</span><span class="sxs-lookup"><span data-stu-id="8e11c-104">Gets the name of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e11c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8e11c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e11c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8e11c-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="8e11c-107">'ndaki `ULONG32` Arabellek boyutunu belirten bir `szName` .</span><span class="sxs-lookup"><span data-stu-id="8e11c-107">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="8e11c-108">dışı `ULONG32` Null sonlandırma dahil olmak üzere ad alanı adını içermesi için gereken arabelleğin karakter cinsinden boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="8e11c-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespace name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="8e11c-109">dışı Ad alanı adını içeren bir arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="8e11c-109">[out] A pointer to a buffer that contains the namespace name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8e11c-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8e11c-110">Return Value</span></span>  

 <span data-ttu-id="8e11c-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="8e11c-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e11c-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8e11c-112">Requirements</span></span>  

 <span data-ttu-id="8e11c-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="8e11c-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e11c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e11c-114">See also</span></span>

- [<span data-ttu-id="8e11c-115">ISymUnmanagedNamespace Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8e11c-115">ISymUnmanagedNamespace Interface</span></span>](isymunmanagednamespace-interface.md)
