---
title: ISymUnmanagedVariable::GetAttributes Metodu
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
ms.openlocfilehash: dc0f72168e076f661bfefc17c851d7d353e5e742
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426758"
---
# <a name="isymunmanagedvariablegetattributes-method"></a><span data-ttu-id="78f1f-102">ISymUnmanagedVariable::GetAttributes Metodu</span><span class="sxs-lookup"><span data-stu-id="78f1f-102">ISymUnmanagedVariable::GetAttributes Method</span></span>
<span data-ttu-id="78f1f-103">Öznitelik bayrakları için bu değişkeni alır.</span><span class="sxs-lookup"><span data-stu-id="78f1f-103">Gets the attribute flags for this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78f1f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="78f1f-104">Syntax</span></span>  
  
```  
HRESULT GetAttributes(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="78f1f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="78f1f-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="78f1f-106">[out] Bir işaretçi bir `ULONG32` özniteliklerini alır.</span><span class="sxs-lookup"><span data-stu-id="78f1f-106">[out] A pointer to a `ULONG32` that receives the attributes.</span></span> <span data-ttu-id="78f1f-107">Döndürülen değer tanımlanan değerlerden biri olacaktır [CorSymVarFlag](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md) numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="78f1f-107">The returned value will be one of the values defined in the [CorSymVarFlag](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="78f1f-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="78f1f-108">Return Value</span></span>  
 <span data-ttu-id="78f1f-109">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="78f1f-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78f1f-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="78f1f-110">Requirements</span></span>  
 <span data-ttu-id="78f1f-111">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="78f1f-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78f1f-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="78f1f-112">See Also</span></span>  
 [<span data-ttu-id="78f1f-113">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="78f1f-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
