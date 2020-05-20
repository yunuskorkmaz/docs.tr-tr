---
title: ISymUnmanagedReader::GetGlobalVariables Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetGlobalVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetGlobalVariables
helpviewer_keywords:
- GetGlobalVariables method [.NET Framework debugging]
- ISymUnmanagedReader::GetGlobalVariables method [.NET Framework debugging]
ms.assetid: a2dd5098-3e58-4be5-b7a2-e4160b3b505a
topic_type:
- apiref
ms.openlocfilehash: 20bfb3e48f411524bd4d9798f17dd935595a12bb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615026"
---
# <a name="isymunmanagedreadergetglobalvariables-method"></a><span data-ttu-id="23203-102">ISymUnmanagedReader::GetGlobalVariables Metodu</span><span class="sxs-lookup"><span data-stu-id="23203-102">ISymUnmanagedReader::GetGlobalVariables Method</span></span>
<span data-ttu-id="23203-103">Tüm genel değişkenleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="23203-103">Returns all global variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23203-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="23203-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGlobalVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars),  
        length_is(*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="23203-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="23203-105">Parameters</span></span>  
 `cVars`  
 <span data-ttu-id="23203-106">'ndaki Tarafından işaret edilen arabelleğin uzunluğu `pcVars` .</span><span class="sxs-lookup"><span data-stu-id="23203-106">[in] The length of the buffer pointed to by `pcVars`.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="23203-107">dışı `ULONG32`Değişkenleri içermesi için gereken arabelleğin boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="23203-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the variables.</span></span>  
  
 `pVars`  
 <span data-ttu-id="23203-108">dışı Değişkenleri içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="23203-108">[out] A buffer that contains the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="23203-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="23203-109">Return Value</span></span>  
 <span data-ttu-id="23203-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="23203-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23203-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="23203-111">Requirements</span></span>  
 <span data-ttu-id="23203-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="23203-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23203-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23203-113">See also</span></span>

- [<span data-ttu-id="23203-114">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="23203-114">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
