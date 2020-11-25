---
title: ISymUnmanagedVariable::GetName Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetName
helpviewer_keywords:
- GetName method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetName method [.NET Framework debugging]
ms.assetid: eedf1ef0-9d4a-4847-a201-4e99572dfe5e
topic_type:
- apiref
ms.openlocfilehash: f9da3ca8684da3bbc87146b3b52effdc4f91393d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726892"
---
# <a name="isymunmanagedvariablegetname-method"></a><span data-ttu-id="e6528-102">ISymUnmanagedVariable::GetName Metodu</span><span class="sxs-lookup"><span data-stu-id="e6528-102">ISymUnmanagedVariable::GetName Method</span></span>

<span data-ttu-id="e6528-103">Bu değişkenin adını alır.</span><span class="sxs-lookup"><span data-stu-id="e6528-103">Gets the name of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6528-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e6528-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6528-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e6528-105">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="e6528-106">'ndaki `pcchName` Parametrenin işaret ettiği arabelleğin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="e6528-106">[in] The length of the buffer that the `pcchName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="e6528-107">dışı `ULONG32` Null sonlandırma dahil olmak üzere, adı içermesi için gereken arabelleğin karakter cinsinden boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e6528-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="e6528-108">dışı Adı depolayan arabellek.</span><span class="sxs-lookup"><span data-stu-id="e6528-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e6528-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e6528-109">Return Value</span></span>  

 <span data-ttu-id="e6528-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="e6528-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6528-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e6528-111">Requirements</span></span>  

 <span data-ttu-id="e6528-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e6528-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6528-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6528-113">See also</span></span>

- [<span data-ttu-id="e6528-114">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e6528-114">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
