---
title: ISymUnmanagedNamespace::GetVariables Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetVariables
helpviewer_keywords:
- ISymUnmanagedNamespace::GetVariables method [.NET Framework debugging]
- GetVariables method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: ea7c1617-f3ce-4220-8288-f2b50eaf0f0f
topic_type:
- apiref
ms.openlocfilehash: 98ed5556020b93fb1f31d1dde84690fc33092627
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448365"
---
# <a name="isymunmanagednamespacegetvariables-method"></a><span data-ttu-id="4f707-102">ISymUnmanagedNamespace::GetVariables Metodu</span><span class="sxs-lookup"><span data-stu-id="4f707-102">ISymUnmanagedNamespace::GetVariables Method</span></span>
<span data-ttu-id="4f707-103">Bu ad alanı içinde genel kapsamda tanımlanan tüm değişkenleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="4f707-103">Returns all variables defined at global scope within this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f707-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4f707-104">Syntax</span></span>  
  
```cpp
HRESULT GetVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars), length_is(*pcVars)]  
        ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f707-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4f707-105">Parameters</span></span>  
 `cVars`  
 <span data-ttu-id="4f707-106">'ndaki `pVars` dizisinin boyutunu belirten `ULONG32`.</span><span class="sxs-lookup"><span data-stu-id="4f707-106">[in] A `ULONG32` that indicates the size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="4f707-107">dışı Ad alanlarını içermesi için gereken arabelleğin boyutunu alan bir `ULONG32` işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="4f707-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `pVars`  
 <span data-ttu-id="4f707-108">dışı Ad alanlarını içeren bir arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="4f707-108">[out] A pointer to a buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4f707-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4f707-109">Return Value</span></span>  
 <span data-ttu-id="4f707-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="4f707-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f707-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4f707-111">Requirements</span></span>  
 <span data-ttu-id="4f707-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="4f707-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f707-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f707-113">See also</span></span>

- [<span data-ttu-id="4f707-114">ISymUnmanagedNamespace Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4f707-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)
