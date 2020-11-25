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
ms.openlocfilehash: f554fa95f552285ad92d9f780a8d77f53e6890b6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707704"
---
# <a name="isymunmanagednamespacegetvariables-method"></a><span data-ttu-id="2982a-102">ISymUnmanagedNamespace::GetVariables Metodu</span><span class="sxs-lookup"><span data-stu-id="2982a-102">ISymUnmanagedNamespace::GetVariables Method</span></span>

<span data-ttu-id="2982a-103">Bu ad alanı içinde genel kapsamda tanımlanan tüm değişkenleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="2982a-103">Returns all variables defined at global scope within this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2982a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2982a-104">Syntax</span></span>  
  
```cpp
HRESULT GetVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars), length_is(*pcVars)]  
        ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2982a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2982a-105">Parameters</span></span>  

 `cVars`  
 <span data-ttu-id="2982a-106">'ndaki `ULONG32` Dizi boyutunu belirten bir `pVars` .</span><span class="sxs-lookup"><span data-stu-id="2982a-106">[in] A `ULONG32` that indicates the size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="2982a-107">dışı `ULONG32` Ad alanlarını içermesi için gereken arabellek boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="2982a-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `pVars`  
 <span data-ttu-id="2982a-108">dışı Ad alanlarını içeren bir arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="2982a-108">[out] A pointer to a buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2982a-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2982a-109">Return Value</span></span>  

 <span data-ttu-id="2982a-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="2982a-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2982a-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2982a-111">Requirements</span></span>  

 <span data-ttu-id="2982a-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2982a-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2982a-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2982a-113">See also</span></span>

- [<span data-ttu-id="2982a-114">ISymUnmanagedNamespace Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2982a-114">ISymUnmanagedNamespace Interface</span></span>](isymunmanagednamespace-interface.md)
