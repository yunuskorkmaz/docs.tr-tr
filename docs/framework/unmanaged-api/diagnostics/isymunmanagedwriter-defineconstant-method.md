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
ms.openlocfilehash: 7c4589c3371d2c66279684a365cde102bef58c6e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727594"
---
# <a name="isymunmanagedwriterdefineconstant-method"></a><span data-ttu-id="76eba-102">ISymUnmanagedWriter::DefineConstant Yöntemi</span><span class="sxs-lookup"><span data-stu-id="76eba-102">ISymUnmanagedWriter::DefineConstant Method</span></span>

<span data-ttu-id="76eba-103">Sabit değer için bir ad tanımlar.</span><span class="sxs-lookup"><span data-stu-id="76eba-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76eba-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="76eba-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineConstant(  
    [in] const WCHAR *name,  
    [in] VARIANT value,  
    [in] ULONG32 cSig,  
    [in, size_is(cSig)] unsigned char signature[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76eba-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="76eba-105">Parameters</span></span>  

 `name`  
 <span data-ttu-id="76eba-106">'ndaki `WCHAR` Sabit adı tanımlayan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="76eba-106">[in] A pointer to a `WCHAR` that defines the constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="76eba-107">'ndaki Sabitin değeri.</span><span class="sxs-lookup"><span data-stu-id="76eba-107">[in] The value of the constant.</span></span>  
  
 `cSig`  
 <span data-ttu-id="76eba-108">'ndaki `signature` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="76eba-108">[in] The size of the `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="76eba-109">'ndaki Sabit için tür imzası.</span><span class="sxs-lookup"><span data-stu-id="76eba-109">[in] The type signature for the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="76eba-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="76eba-110">Return Value</span></span>  

 <span data-ttu-id="76eba-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="76eba-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76eba-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="76eba-112">Requirements</span></span>  

 <span data-ttu-id="76eba-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="76eba-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76eba-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76eba-114">See also</span></span>

- [<span data-ttu-id="76eba-115">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="76eba-115">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="76eba-116">DefineConstant2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="76eba-116">DefineConstant2 Method</span></span>](isymunmanagedwriter2-defineconstant2-method.md)
