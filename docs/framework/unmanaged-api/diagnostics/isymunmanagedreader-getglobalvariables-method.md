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
ms.openlocfilehash: 299787ea4eb8a5c25bdab64ad08445839c9f24d6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707548"
---
# <a name="isymunmanagedreadergetglobalvariables-method"></a><span data-ttu-id="1b6ae-102">ISymUnmanagedReader::GetGlobalVariables Metodu</span><span class="sxs-lookup"><span data-stu-id="1b6ae-102">ISymUnmanagedReader::GetGlobalVariables Method</span></span>

<span data-ttu-id="1b6ae-103">Tüm genel değişkenleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="1b6ae-103">Returns all global variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b6ae-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1b6ae-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGlobalVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars),  
        length_is(*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b6ae-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1b6ae-105">Parameters</span></span>  

 `cVars`  
 <span data-ttu-id="1b6ae-106">'ndaki Tarafından işaret edilen arabelleğin uzunluğu `pcVars` .</span><span class="sxs-lookup"><span data-stu-id="1b6ae-106">[in] The length of the buffer pointed to by `pcVars`.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="1b6ae-107">dışı `ULONG32` Değişkenleri içermesi için gereken arabelleğin boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1b6ae-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the variables.</span></span>  
  
 `pVars`  
 <span data-ttu-id="1b6ae-108">dışı Değişkenleri içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="1b6ae-108">[out] A buffer that contains the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1b6ae-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1b6ae-109">Return Value</span></span>  

 <span data-ttu-id="1b6ae-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="1b6ae-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b6ae-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1b6ae-111">Requirements</span></span>  

 <span data-ttu-id="1b6ae-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="1b6ae-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b6ae-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b6ae-113">See also</span></span>

- [<span data-ttu-id="1b6ae-114">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1b6ae-114">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
