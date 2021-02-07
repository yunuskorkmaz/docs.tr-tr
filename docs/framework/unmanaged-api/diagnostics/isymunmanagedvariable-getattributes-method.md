---
description: 'Şu konuda daha fazla bilgi edinin: ıdimunmanagedvariable:: GetAttributes yöntemi'
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
ms.openlocfilehash: 0adaeaf512f129f92b7f15cdba375395a0a81855
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762844"
---
# <a name="isymunmanagedvariablegetattributes-method"></a><span data-ttu-id="c6cf6-103">ISymUnmanagedVariable::GetAttributes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c6cf6-103">ISymUnmanagedVariable::GetAttributes Method</span></span>

<span data-ttu-id="c6cf6-104">Bu değişken için öznitelik bayraklarını alır.</span><span class="sxs-lookup"><span data-stu-id="c6cf6-104">Gets the attribute flags for this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6cf6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c6cf6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAttributes(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6cf6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c6cf6-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="c6cf6-107">dışı Öznitelikleri alan öğesine yönelik bir işaretçi `ULONG32` .</span><span class="sxs-lookup"><span data-stu-id="c6cf6-107">[out] A pointer to a `ULONG32` that receives the attributes.</span></span> <span data-ttu-id="c6cf6-108">Döndürülen değer [CorSymVarFlag](corsymvarflag-enumeration.md) numaralandırmasında tanımlanan değerlerden biri olacaktır.</span><span class="sxs-lookup"><span data-stu-id="c6cf6-108">The returned value will be one of the values defined in the [CorSymVarFlag](corsymvarflag-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c6cf6-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c6cf6-109">Return Value</span></span>  

 <span data-ttu-id="c6cf6-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="c6cf6-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6cf6-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c6cf6-111">Requirements</span></span>  

 <span data-ttu-id="c6cf6-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="c6cf6-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6cf6-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6cf6-113">See also</span></span>

- [<span data-ttu-id="c6cf6-114">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c6cf6-114">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
