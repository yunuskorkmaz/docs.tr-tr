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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f7e71315b5ff99a550ae4a59f3b0d444093dac01
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778281"
---
# <a name="isymunmanagedvariablegetattributes-method"></a><span data-ttu-id="307d1-102">ISymUnmanagedVariable::GetAttributes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="307d1-102">ISymUnmanagedVariable::GetAttributes Method</span></span>
<span data-ttu-id="307d1-103">Bu değişken için öznitelik bayrakları alır.</span><span class="sxs-lookup"><span data-stu-id="307d1-103">Gets the attribute flags for this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="307d1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="307d1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAttributes(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="307d1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="307d1-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="307d1-106">[out] Bir işaretçi bir `ULONG32` , özniteliklerini alır.</span><span class="sxs-lookup"><span data-stu-id="307d1-106">[out] A pointer to a `ULONG32` that receives the attributes.</span></span> <span data-ttu-id="307d1-107">Döndürülen değer tanımlanan değerlerden biri [CorSymVarFlag](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md) sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="307d1-107">The returned value will be one of the values defined in the [CorSymVarFlag](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="307d1-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="307d1-108">Return Value</span></span>  
 <span data-ttu-id="307d1-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="307d1-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="307d1-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="307d1-110">Requirements</span></span>  
 <span data-ttu-id="307d1-111">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="307d1-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="307d1-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="307d1-112">See also</span></span>

- [<span data-ttu-id="307d1-113">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="307d1-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
