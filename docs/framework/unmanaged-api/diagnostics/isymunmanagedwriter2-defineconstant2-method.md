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
ms.openlocfilehash: 70ee853ff657a75dcc4df1454c4354f9d3f8202f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614727"
---
# <a name="isymunmanagedwriter2defineconstant2-method"></a><span data-ttu-id="be9e8-102">ISymUnmanagedWriter2::DefineConstant2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="be9e8-102">ISymUnmanagedWriter2::DefineConstant2 Method</span></span>
<span data-ttu-id="be9e8-103">Sabit değer için bir ad tanımlar.</span><span class="sxs-lookup"><span data-stu-id="be9e8-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be9e8-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="be9e8-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineConstant2(  
    [in] const WCHAR  *name,  
    [in] VARIANT      value,  
    [in] mdSignature  sigToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be9e8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="be9e8-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="be9e8-106">'ndaki Sabit adı.</span><span class="sxs-lookup"><span data-stu-id="be9e8-106">[in] The constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="be9e8-107">'ndaki Sabitin değeri.</span><span class="sxs-lookup"><span data-stu-id="be9e8-107">[in] The value of the constant.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="be9e8-108">'ndaki Sabitin meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="be9e8-108">[in] The metadata token of the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="be9e8-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="be9e8-109">Return Value</span></span>  
 <span data-ttu-id="be9e8-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="be9e8-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be9e8-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="be9e8-111">Requirements</span></span>  
 <span data-ttu-id="be9e8-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="be9e8-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be9e8-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be9e8-113">See also</span></span>

- [<span data-ttu-id="be9e8-114">ISymUnmanagedWriter2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="be9e8-114">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="be9e8-115">DefineConstant Yöntemi</span><span class="sxs-lookup"><span data-stu-id="be9e8-115">DefineConstant Method</span></span>](isymunmanagedwriter-defineconstant-method.md)
