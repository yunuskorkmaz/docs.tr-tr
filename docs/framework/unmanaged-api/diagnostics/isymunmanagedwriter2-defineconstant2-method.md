---
title: "ISymUnmanagedWriter2::DefineConstant2 Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter2.DefineConstant2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter2::DefineConstant2
helpviewer_keywords:
- DefineConstant2 method [.NET Framework debugging]
- ISymUnmanagedWriter2::DefineConstant2 method [.NET Framework debugging]
ms.assetid: dd2bc956-7dbe-49fc-a646-daa0d267f2df
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 998916ab485042ba2f8493afe84ea5375f3eb740
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriter2defineconstant2-method"></a><span data-ttu-id="0e4cf-102">ISymUnmanagedWriter2::DefineConstant2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0e4cf-102">ISymUnmanagedWriter2::DefineConstant2 Method</span></span>
<span data-ttu-id="0e4cf-103">Sabit bir değer için bir ad tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0e4cf-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e4cf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0e4cf-104">Syntax</span></span>  
  
```  
HRESULT DefineConstant2(  
    [in] const WCHAR  *name,  
    [in] VARIANT      value,  
    [in] mdSignature  sigToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0e4cf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0e4cf-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="0e4cf-106">[in] Sabit adı.</span><span class="sxs-lookup"><span data-stu-id="0e4cf-106">[in] The constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="0e4cf-107">[in] Sabit değer.</span><span class="sxs-lookup"><span data-stu-id="0e4cf-107">[in] The value of the constant.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="0e4cf-108">[in] Sabit meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="0e4cf-108">[in] The metadata token of the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0e4cf-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0e4cf-109">Return Value</span></span>  
 <span data-ttu-id="0e4cf-110">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="0e4cf-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e4cf-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0e4cf-111">Requirements</span></span>  
 <span data-ttu-id="0e4cf-112">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0e4cf-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e4cf-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0e4cf-113">See Also</span></span>  
 [<span data-ttu-id="0e4cf-114">Isymunmanagedwriter2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="0e4cf-114">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 [<span data-ttu-id="0e4cf-115">DefineConstant yöntemi</span><span class="sxs-lookup"><span data-stu-id="0e4cf-115">DefineConstant Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineconstant-method.md)
