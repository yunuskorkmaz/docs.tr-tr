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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 03c0a9d7315f5158948701d4322887104f0844c9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603670"
---
# <a name="isymunmanagedwriterdefinefield-method"></a><span data-ttu-id="f5e69-102">ISymUnmanagedWriter::DefineField Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f5e69-102">ISymUnmanagedWriter::DefineField Method</span></span>
<span data-ttu-id="f5e69-103">Bir yöntem içinde değil tek bir değişkeni tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f5e69-103">Defines a single variable that is not within a method.</span></span> <span data-ttu-id="f5e69-104">Bu, kullanılan belirli alanları sınıflarda, bit alanları ve benzeri yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="f5e69-104">This method is used for certain fields in classes, bit fields, and so on.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5e69-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f5e69-105">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="f5e69-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f5e69-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="f5e69-107">[in] Meta veri türünde veya yönteminde ' belirteci.</span><span class="sxs-lookup"><span data-stu-id="f5e69-107">[in] The metadata type or method token.</span></span>  
  
 `name`  
 <span data-ttu-id="f5e69-108">[in] Alan adı.</span><span class="sxs-lookup"><span data-stu-id="f5e69-108">[in] The field name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="f5e69-109">[in] Alan öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="f5e69-109">[in] The field attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="f5e69-110">[in] A `ULONG32` alan imzası içermesi gereken arabelleğin karakter cinsinden boyutu diğer bir deyişle.</span><span class="sxs-lookup"><span data-stu-id="f5e69-110">[in] A `ULONG32` that is the size, in characters, of the buffer required to contain the field signature.</span></span>  
  
 `signature`  
 <span data-ttu-id="f5e69-111">[in] Alan imzaları dizisi.</span><span class="sxs-lookup"><span data-stu-id="f5e69-111">[in] The array of field signatures.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="f5e69-112">[in] Adres türü.</span><span class="sxs-lookup"><span data-stu-id="f5e69-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="f5e69-113">[in] İlk adres alanı belirtimi için.</span><span class="sxs-lookup"><span data-stu-id="f5e69-113">[in] The first address for the field specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="f5e69-114">[in] İkinci bir adres alanı belirtimi için.</span><span class="sxs-lookup"><span data-stu-id="f5e69-114">[in] The second address for the field specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="f5e69-115">[in] Üçüncü adres alanı belirtimi için.</span><span class="sxs-lookup"><span data-stu-id="f5e69-115">[in] The third address for the field specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f5e69-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f5e69-116">Return Value</span></span>  
 <span data-ttu-id="f5e69-117">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="f5e69-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5e69-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f5e69-118">Requirements</span></span>  
 <span data-ttu-id="f5e69-119">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f5e69-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5e69-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5e69-120">See also</span></span>
- [<span data-ttu-id="f5e69-121">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f5e69-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
