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
ms.openlocfilehash: 091f497024b48589953456e1ea6daf6635738240
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615091"
---
# <a name="isymunmanagednamespacegetvariables-method"></a><span data-ttu-id="50500-102">ISymUnmanagedNamespace::GetVariables Metodu</span><span class="sxs-lookup"><span data-stu-id="50500-102">ISymUnmanagedNamespace::GetVariables Method</span></span>
<span data-ttu-id="50500-103">Bu ad alanı içinde genel kapsamda tanımlanan tüm değişkenleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="50500-103">Returns all variables defined at global scope within this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50500-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="50500-104">Syntax</span></span>  
  
```cpp
HRESULT GetVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars), length_is(*pcVars)]  
        ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50500-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="50500-105">Parameters</span></span>  
 `cVars`  
 <span data-ttu-id="50500-106">'ndaki `ULONG32`Dizi boyutunu belirten bir `pVars` .</span><span class="sxs-lookup"><span data-stu-id="50500-106">[in] A `ULONG32` that indicates the size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="50500-107">dışı `ULONG32`Ad alanlarını içermesi için gereken arabellek boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="50500-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `pVars`  
 <span data-ttu-id="50500-108">dışı Ad alanlarını içeren bir arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="50500-108">[out] A pointer to a buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="50500-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="50500-109">Return Value</span></span>  
 <span data-ttu-id="50500-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="50500-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50500-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="50500-111">Requirements</span></span>  
 <span data-ttu-id="50500-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="50500-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50500-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50500-113">See also</span></span>

- [<span data-ttu-id="50500-114">ISymUnmanagedNamespace Arabirimi</span><span class="sxs-lookup"><span data-stu-id="50500-114">ISymUnmanagedNamespace Interface</span></span>](isymunmanagednamespace-interface.md)
