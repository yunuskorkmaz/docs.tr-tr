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
ms.openlocfilehash: e863640e18ca64de084331327e0fa39468b54b60
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797546"
---
# <a name="isymunmanagedvariablegetname-method"></a><span data-ttu-id="1ede9-102">ISymUnmanagedVariable::GetName Metodu</span><span class="sxs-lookup"><span data-stu-id="1ede9-102">ISymUnmanagedVariable::GetName Method</span></span>
<span data-ttu-id="1ede9-103">Bu değişken adını alır.</span><span class="sxs-lookup"><span data-stu-id="1ede9-103">Gets the name of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ede9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1ede9-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ede9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1ede9-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="1ede9-106">[in] Arabellek uzunluğu, `pcchName` parametre işaret eder.</span><span class="sxs-lookup"><span data-stu-id="1ede9-106">[in] The length of the buffer that the `pcchName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="1ede9-107">[out] Bir işaretçi bir `ULONG32` karakter null sonlandırma dahil olmak üzere adını içerecek şekilde gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="1ede9-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="1ede9-108">[out] Adı depolayan arabellek.</span><span class="sxs-lookup"><span data-stu-id="1ede9-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1ede9-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1ede9-109">Return Value</span></span>  
 <span data-ttu-id="1ede9-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="1ede9-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ede9-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1ede9-111">Requirements</span></span>  
 <span data-ttu-id="1ede9-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1ede9-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ede9-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ede9-113">See also</span></span>

- [<span data-ttu-id="1ede9-114">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1ede9-114">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
