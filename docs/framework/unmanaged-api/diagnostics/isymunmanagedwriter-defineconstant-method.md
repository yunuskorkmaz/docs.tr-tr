---
title: ISymUnmanagedWriter::DefineConstant Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineConstant
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineConstant
helpviewer_keywords:
- DefineConstant method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineConstant method [.NET Framework debugging]
ms.assetid: 9e986986-2223-4d5f-b040-85d716146924
topic_type:
- apiref
ms.openlocfilehash: c8d0145b9dffe1c0ff6ed3281c90f3bcec082ab8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428065"
---
# <a name="isymunmanagedwriterdefineconstant-method"></a><span data-ttu-id="8bba7-102">ISymUnmanagedWriter::DefineConstant Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8bba7-102">ISymUnmanagedWriter::DefineConstant Method</span></span>
<span data-ttu-id="8bba7-103">Sabit değer için bir ad tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8bba7-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bba7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8bba7-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineConstant(  
    [in] const WCHAR *name,  
    [in] VARIANT value,  
    [in] ULONG32 cSig,  
    [in, size_is(cSig)] unsigned char signature[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8bba7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8bba7-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="8bba7-106">'ndaki Sabit adı tanımlayan `WCHAR` için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8bba7-106">[in] A pointer to a `WCHAR` that defines the constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="8bba7-107">'ndaki Sabitin değeri.</span><span class="sxs-lookup"><span data-stu-id="8bba7-107">[in] The value of the constant.</span></span>  
  
 `cSig`  
 <span data-ttu-id="8bba7-108">'ndaki `signature` dizisinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="8bba7-108">[in] The size of the `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="8bba7-109">'ndaki Sabit için tür imzası.</span><span class="sxs-lookup"><span data-stu-id="8bba7-109">[in] The type signature for the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8bba7-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8bba7-110">Return Value</span></span>  
 <span data-ttu-id="8bba7-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="8bba7-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bba7-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8bba7-112">Requirements</span></span>  
 <span data-ttu-id="8bba7-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="8bba7-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bba7-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8bba7-114">See also</span></span>

- [<span data-ttu-id="8bba7-115">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8bba7-115">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="8bba7-116">DefineConstant2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8bba7-116">DefineConstant2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineconstant2-method.md)
