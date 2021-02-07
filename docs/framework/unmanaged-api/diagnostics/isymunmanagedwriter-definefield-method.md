---
description: 'Hakkında daha fazla bilgi edinin: ırivefield yöntemi:D'
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
ms.openlocfilehash: f5bb47d4691780d94baf50cc9ceb3c14b1fa16ec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762402"
---
# <a name="isymunmanagedwriterdefinefield-method"></a><span data-ttu-id="90ec9-103">ISymUnmanagedWriter::DefineField Yöntemi</span><span class="sxs-lookup"><span data-stu-id="90ec9-103">ISymUnmanagedWriter::DefineField Method</span></span>

<span data-ttu-id="90ec9-104">Bir yöntem içinde olmayan tek bir değişkeni tanımlar.</span><span class="sxs-lookup"><span data-stu-id="90ec9-104">Defines a single variable that is not within a method.</span></span> <span data-ttu-id="90ec9-105">Bu yöntem, sınıflardaki belirli alanlar, bit alanları vb. için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="90ec9-105">This method is used for certain fields in classes, bit fields, and so on.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90ec9-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="90ec9-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="90ec9-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="90ec9-107">Parameters</span></span>  

 `parent`  
 <span data-ttu-id="90ec9-108">'ndaki Meta veri türü veya yöntem belirteci.</span><span class="sxs-lookup"><span data-stu-id="90ec9-108">[in] The metadata type or method token.</span></span>  
  
 `name`  
 <span data-ttu-id="90ec9-109">'ndaki Alan adı.</span><span class="sxs-lookup"><span data-stu-id="90ec9-109">[in] The field name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="90ec9-110">'ndaki Alan öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="90ec9-110">[in] The field attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="90ec9-111">'ndaki `ULONG32` Bu, alan imzasını içermesi için gereken arabelleğin karakter cinsinden boyutudur.</span><span class="sxs-lookup"><span data-stu-id="90ec9-111">[in] A `ULONG32` that is the size, in characters, of the buffer required to contain the field signature.</span></span>  
  
 `signature`  
 <span data-ttu-id="90ec9-112">'ndaki Alan imzalarının dizisi.</span><span class="sxs-lookup"><span data-stu-id="90ec9-112">[in] The array of field signatures.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="90ec9-113">'ndaki Adres türü.</span><span class="sxs-lookup"><span data-stu-id="90ec9-113">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="90ec9-114">'ndaki Alan belirtiminin ilk adresi.</span><span class="sxs-lookup"><span data-stu-id="90ec9-114">[in] The first address for the field specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="90ec9-115">'ndaki Alan belirtiminin ikinci adresi.</span><span class="sxs-lookup"><span data-stu-id="90ec9-115">[in] The second address for the field specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="90ec9-116">'ndaki Alan belirtiminin üçüncü adresi.</span><span class="sxs-lookup"><span data-stu-id="90ec9-116">[in] The third address for the field specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="90ec9-117">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="90ec9-117">Return Value</span></span>  

 <span data-ttu-id="90ec9-118">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="90ec9-118">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90ec9-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="90ec9-119">Requirements</span></span>  

 <span data-ttu-id="90ec9-120">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="90ec9-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90ec9-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="90ec9-121">See also</span></span>

- [<span data-ttu-id="90ec9-122">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="90ec9-122">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
