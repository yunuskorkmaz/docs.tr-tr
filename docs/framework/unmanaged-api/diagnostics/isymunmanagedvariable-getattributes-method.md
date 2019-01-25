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
ms.openlocfilehash: d418a1088f9ee23a088ab4c8246810d2c9bee4fa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574345"
---
# <a name="isymunmanagedvariablegetattributes-method"></a><span data-ttu-id="2be78-102">ISymUnmanagedVariable::GetAttributes Metodu</span><span class="sxs-lookup"><span data-stu-id="2be78-102">ISymUnmanagedVariable::GetAttributes Method</span></span>
<span data-ttu-id="2be78-103">Bu değişken için öznitelik bayrakları alır.</span><span class="sxs-lookup"><span data-stu-id="2be78-103">Gets the attribute flags for this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2be78-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2be78-104">Syntax</span></span>  
  
```  
HRESULT GetAttributes(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2be78-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2be78-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="2be78-106">[out] Bir işaretçi bir `ULONG32` , özniteliklerini alır.</span><span class="sxs-lookup"><span data-stu-id="2be78-106">[out] A pointer to a `ULONG32` that receives the attributes.</span></span> <span data-ttu-id="2be78-107">Döndürülen değer tanımlanan değerlerden biri [CorSymVarFlag](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md) sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="2be78-107">The returned value will be one of the values defined in the [CorSymVarFlag](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2be78-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2be78-108">Return Value</span></span>  
 <span data-ttu-id="2be78-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="2be78-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2be78-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2be78-110">Requirements</span></span>  
 <span data-ttu-id="2be78-111">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2be78-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2be78-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2be78-112">See also</span></span>
- [<span data-ttu-id="2be78-113">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2be78-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
