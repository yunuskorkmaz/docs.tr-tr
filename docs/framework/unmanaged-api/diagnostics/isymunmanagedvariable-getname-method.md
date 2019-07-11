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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8298e7240052bdd859dbe414281d8e78984342e8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778247"
---
# <a name="isymunmanagedvariablegetname-method"></a><span data-ttu-id="eff99-102">ISymUnmanagedVariable::GetName Metodu</span><span class="sxs-lookup"><span data-stu-id="eff99-102">ISymUnmanagedVariable::GetName Method</span></span>
<span data-ttu-id="eff99-103">Bu değişken adını alır.</span><span class="sxs-lookup"><span data-stu-id="eff99-103">Gets the name of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eff99-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eff99-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eff99-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="eff99-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="eff99-106">[in] Arabellek uzunluğu, `pcchName` parametre işaret eder.</span><span class="sxs-lookup"><span data-stu-id="eff99-106">[in] The length of the buffer that the `pcchName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="eff99-107">[out] Bir işaretçi bir `ULONG32` karakter null sonlandırma dahil olmak üzere adını içerecek şekilde gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="eff99-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="eff99-108">[out] Adı depolayan arabellek.</span><span class="sxs-lookup"><span data-stu-id="eff99-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eff99-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="eff99-109">Return Value</span></span>  
 <span data-ttu-id="eff99-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="eff99-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eff99-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eff99-111">Requirements</span></span>  
 <span data-ttu-id="eff99-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="eff99-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eff99-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eff99-113">See also</span></span>

- [<span data-ttu-id="eff99-114">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eff99-114">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
