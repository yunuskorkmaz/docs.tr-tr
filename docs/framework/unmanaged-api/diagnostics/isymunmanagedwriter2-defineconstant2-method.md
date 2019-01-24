---
title: ISymUnmanagedWriter2::DefineConstant2 Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineConstant2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineConstant2
helpviewer_keywords:
- DefineConstant2 method [.NET Framework debugging]
- ISymUnmanagedWriter2::DefineConstant2 method [.NET Framework debugging]
ms.assetid: dd2bc956-7dbe-49fc-a646-daa0d267f2df
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e843acc82d52e2c7a772f4799e7bb0af8ecff10d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54545731"
---
# <a name="isymunmanagedwriter2defineconstant2-method"></a><span data-ttu-id="5a528-102">ISymUnmanagedWriter2::DefineConstant2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5a528-102">ISymUnmanagedWriter2::DefineConstant2 Method</span></span>
<span data-ttu-id="5a528-103">Sabit değer için bir ad tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5a528-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a528-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5a528-104">Syntax</span></span>  
  
```  
HRESULT DefineConstant2(  
    [in] const WCHAR  *name,  
    [in] VARIANT      value,  
    [in] mdSignature  sigToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5a528-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5a528-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="5a528-106">[in] Sabit adı.</span><span class="sxs-lookup"><span data-stu-id="5a528-106">[in] The constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="5a528-107">[in] Sabit değer.</span><span class="sxs-lookup"><span data-stu-id="5a528-107">[in] The value of the constant.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="5a528-108">[in] Meta veri belirteci sabit.</span><span class="sxs-lookup"><span data-stu-id="5a528-108">[in] The metadata token of the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5a528-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5a528-109">Return Value</span></span>  
 <span data-ttu-id="5a528-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="5a528-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a528-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5a528-111">Requirements</span></span>  
 <span data-ttu-id="5a528-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5a528-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a528-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a528-113">See also</span></span>
- [<span data-ttu-id="5a528-114">ISymUnmanagedWriter2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5a528-114">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="5a528-115">DefineConstant Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5a528-115">DefineConstant Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineconstant-method.md)
