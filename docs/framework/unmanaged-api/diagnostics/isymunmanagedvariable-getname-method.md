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
ms.openlocfilehash: 77dec4332aa65f6125685db607169b3398bcab98
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446062"
---
# <a name="isymunmanagedvariablegetname-method"></a><span data-ttu-id="0890e-102">ISymUnmanagedVariable::GetName Metodu</span><span class="sxs-lookup"><span data-stu-id="0890e-102">ISymUnmanagedVariable::GetName Method</span></span>
<span data-ttu-id="0890e-103">Bu değişkenin adını alır.</span><span class="sxs-lookup"><span data-stu-id="0890e-103">Gets the name of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0890e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0890e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0890e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0890e-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="0890e-106">'ndaki `pcchName` parametresinin işaret ettiği arabelleğin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="0890e-106">[in] The length of the buffer that the `pcchName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="0890e-107">dışı Null sonlandırma dahil olmak üzere, adı içermesi için gereken arabelleğin karakter cinsinden boyutunu alan bir `ULONG32` işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="0890e-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="0890e-108">dışı Adı depolayan arabellek.</span><span class="sxs-lookup"><span data-stu-id="0890e-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0890e-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0890e-109">Return Value</span></span>  
 <span data-ttu-id="0890e-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="0890e-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0890e-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0890e-111">Requirements</span></span>  
 <span data-ttu-id="0890e-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="0890e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0890e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0890e-113">See also</span></span>

- [<span data-ttu-id="0890e-114">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0890e-114">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
