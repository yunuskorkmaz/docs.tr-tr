---
title: ISymUnmanagedWriter::DefineField Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineField
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineField
helpviewer_keywords:
- ISymUnmanagedWriter::DefineField method [.NET Framework debugging]
- DefineField method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: c6a1f797-dbf4-40f5-ab99-d9b4bfb26148
topic_type:
- apiref
ms.openlocfilehash: 7eea63cae27c08260177dfc7746046b975434611
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428042"
---
# <a name="isymunmanagedwriterdefinefield-method"></a><span data-ttu-id="78b88-102">ISymUnmanagedWriter::DefineField Yöntemi</span><span class="sxs-lookup"><span data-stu-id="78b88-102">ISymUnmanagedWriter::DefineField Method</span></span>
<span data-ttu-id="78b88-103">Defines a single variable that is not within a method.</span><span class="sxs-lookup"><span data-stu-id="78b88-103">Defines a single variable that is not within a method.</span></span> <span data-ttu-id="78b88-104">This method is used for certain fields in classes, bit fields, and so on.</span><span class="sxs-lookup"><span data-stu-id="78b88-104">This method is used for certain fields in classes, bit fields, and so on.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78b88-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="78b88-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineField(  
    [in] mdTypeDef    parent,  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78b88-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="78b88-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="78b88-107">[in] The metadata type or method token.</span><span class="sxs-lookup"><span data-stu-id="78b88-107">[in] The metadata type or method token.</span></span>  
  
 `name`  
 <span data-ttu-id="78b88-108">[in] The field name.</span><span class="sxs-lookup"><span data-stu-id="78b88-108">[in] The field name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="78b88-109">[in] The field attributes.</span><span class="sxs-lookup"><span data-stu-id="78b88-109">[in] The field attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="78b88-110">[in] A `ULONG32` that is the size, in characters, of the buffer required to contain the field signature.</span><span class="sxs-lookup"><span data-stu-id="78b88-110">[in] A `ULONG32` that is the size, in characters, of the buffer required to contain the field signature.</span></span>  
  
 `signature`  
 <span data-ttu-id="78b88-111">[in] The array of field signatures.</span><span class="sxs-lookup"><span data-stu-id="78b88-111">[in] The array of field signatures.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="78b88-112">[in] The address type.</span><span class="sxs-lookup"><span data-stu-id="78b88-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="78b88-113">[in] The first address for the field specification.</span><span class="sxs-lookup"><span data-stu-id="78b88-113">[in] The first address for the field specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="78b88-114">[in] The second address for the field specification.</span><span class="sxs-lookup"><span data-stu-id="78b88-114">[in] The second address for the field specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="78b88-115">[in] The third address for the field specification.</span><span class="sxs-lookup"><span data-stu-id="78b88-115">[in] The third address for the field specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="78b88-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="78b88-116">Return Value</span></span>  
 <span data-ttu-id="78b88-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="78b88-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78b88-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="78b88-118">Requirements</span></span>  
 <span data-ttu-id="78b88-119">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="78b88-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78b88-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78b88-120">See also</span></span>

- [<span data-ttu-id="78b88-121">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="78b88-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
