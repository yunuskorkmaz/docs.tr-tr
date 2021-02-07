---
description: 'Şu konuda daha fazla bilgi edinin: ıdimunmanagedvariable:: GetName Yöntemi'
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
ms.openlocfilehash: 88d8cf4c81200a30e2a102b63af2817fef2b50c9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762792"
---
# <a name="isymunmanagedvariablegetname-method"></a><span data-ttu-id="0f88b-103">ISymUnmanagedVariable::GetName Metodu</span><span class="sxs-lookup"><span data-stu-id="0f88b-103">ISymUnmanagedVariable::GetName Method</span></span>

<span data-ttu-id="0f88b-104">Bu değişkenin adını alır.</span><span class="sxs-lookup"><span data-stu-id="0f88b-104">Gets the name of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f88b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0f88b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f88b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0f88b-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="0f88b-107">'ndaki `pcchName` Parametrenin işaret ettiği arabelleğin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="0f88b-107">[in] The length of the buffer that the `pcchName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="0f88b-108">dışı `ULONG32` Null sonlandırma dahil olmak üzere, adı içermesi için gereken arabelleğin karakter cinsinden boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="0f88b-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="0f88b-109">dışı Adı depolayan arabellek.</span><span class="sxs-lookup"><span data-stu-id="0f88b-109">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f88b-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0f88b-110">Return Value</span></span>  

 <span data-ttu-id="0f88b-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="0f88b-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f88b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0f88b-112">Requirements</span></span>  

 <span data-ttu-id="0f88b-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="0f88b-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f88b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f88b-114">See also</span></span>

- [<span data-ttu-id="0f88b-115">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f88b-115">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
