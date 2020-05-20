---
title: ISymUnmanagedVariable::GetAttributes Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAttributes
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAttributes
helpviewer_keywords:
- GetAttributes method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAttributes method [.NET Framework debugging]
ms.assetid: 80f168af-a6a6-4c8f-b9e6-8a82dc834ed5
topic_type:
- apiref
ms.openlocfilehash: 29869abdd39f61c6c9cb51d6b2be50fa462c5b70
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615260"
---
# <a name="isymunmanagedvariablegetattributes-method"></a><span data-ttu-id="165e5-102">ISymUnmanagedVariable::GetAttributes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="165e5-102">ISymUnmanagedVariable::GetAttributes Method</span></span>
<span data-ttu-id="165e5-103">Bu değişken için öznitelik bayraklarını alır.</span><span class="sxs-lookup"><span data-stu-id="165e5-103">Gets the attribute flags for this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="165e5-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="165e5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAttributes(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="165e5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="165e5-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="165e5-106">dışı Öznitelikleri alan öğesine yönelik bir işaretçi `ULONG32` .</span><span class="sxs-lookup"><span data-stu-id="165e5-106">[out] A pointer to a `ULONG32` that receives the attributes.</span></span> <span data-ttu-id="165e5-107">Döndürülen değer [CorSymVarFlag](corsymvarflag-enumeration.md) numaralandırmasında tanımlanan değerlerden biri olacaktır.</span><span class="sxs-lookup"><span data-stu-id="165e5-107">The returned value will be one of the values defined in the [CorSymVarFlag](corsymvarflag-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="165e5-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="165e5-108">Return Value</span></span>  
 <span data-ttu-id="165e5-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="165e5-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="165e5-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="165e5-110">Requirements</span></span>  
 <span data-ttu-id="165e5-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="165e5-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="165e5-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="165e5-112">See also</span></span>

- [<span data-ttu-id="165e5-113">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="165e5-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
