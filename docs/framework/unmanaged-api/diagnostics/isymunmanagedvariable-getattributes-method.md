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
ms.openlocfilehash: cfc28dfcda7bf4b3d1fc6fe3530a212ee76fadd2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446079"
---
# <a name="isymunmanagedvariablegetattributes-method"></a><span data-ttu-id="303a7-102">ISymUnmanagedVariable::GetAttributes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="303a7-102">ISymUnmanagedVariable::GetAttributes Method</span></span>
<span data-ttu-id="303a7-103">Bu değişken için öznitelik bayraklarını alır.</span><span class="sxs-lookup"><span data-stu-id="303a7-103">Gets the attribute flags for this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="303a7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="303a7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAttributes(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="303a7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="303a7-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="303a7-106">dışı Öznitelikleri alan `ULONG32` için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="303a7-106">[out] A pointer to a `ULONG32` that receives the attributes.</span></span> <span data-ttu-id="303a7-107">Döndürülen değer [CorSymVarFlag](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md) numaralandırmasında tanımlanan değerlerden biri olacaktır.</span><span class="sxs-lookup"><span data-stu-id="303a7-107">The returned value will be one of the values defined in the [CorSymVarFlag](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="303a7-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="303a7-108">Return Value</span></span>  
 <span data-ttu-id="303a7-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="303a7-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="303a7-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="303a7-110">Requirements</span></span>  
 <span data-ttu-id="303a7-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="303a7-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="303a7-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="303a7-112">See also</span></span>

- [<span data-ttu-id="303a7-113">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="303a7-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
