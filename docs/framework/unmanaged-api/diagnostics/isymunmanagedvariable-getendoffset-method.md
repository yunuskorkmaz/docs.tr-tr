---
title: ISymUnmanagedVariable::GetEndOffset Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedVariable::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: e5d777c5-d450-4c0f-999c-b3953ee22cfb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e0f11614c6fa15034ef5fa3d68e41a936a9ff764
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427863"
---
# <a name="isymunmanagedvariablegetendoffset-method"></a><span data-ttu-id="c9693-102">ISymUnmanagedVariable::GetEndOffset Metodu</span><span class="sxs-lookup"><span data-stu-id="c9693-102">ISymUnmanagedVariable::GetEndOffset Method</span></span>
<span data-ttu-id="c9693-103">Bu değişken, üst içinde son uzaklığını alır.</span><span class="sxs-lookup"><span data-stu-id="c9693-103">Gets the end offset of this variable within its parent.</span></span> <span data-ttu-id="c9693-104">Bu kapsam içinde yerel bir değişken ise bitiş uzaklığı kapsam için tanımlanan uzaklıkları içinde döner.</span><span class="sxs-lookup"><span data-stu-id="c9693-104">If this is a local variable within a scope, the end offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9693-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c9693-105">Syntax</span></span>  
  
```  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c9693-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c9693-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="c9693-107">[out] Bir işaretçi bir `ULONG32` bitiş uzaklığı alır.</span><span class="sxs-lookup"><span data-stu-id="c9693-107">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9693-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c9693-108">Return Value</span></span>  
 <span data-ttu-id="c9693-109">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="c9693-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9693-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c9693-110">Requirements</span></span>  
 <span data-ttu-id="c9693-111">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c9693-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9693-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c9693-112">See Also</span></span>  
 [<span data-ttu-id="c9693-113">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c9693-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="c9693-114">GetStartOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c9693-114">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)
