---
title: ISymUnmanagedWriter::DefineLocalVariable Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineLocalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineLocalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineLocalVariable method [.NET Framework debugging]
- DefineLocalVariable method [.NET Framework debugging]
ms.assetid: 6fab8a58-3883-490f-8b27-64042c90f104
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d6f8b896d50bb659897291d7bf85e836482611a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428992"
---
# <a name="isymunmanagedwriterdefinelocalvariable-method"></a><span data-ttu-id="32a02-102">ISymUnmanagedWriter::DefineLocalVariable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="32a02-102">ISymUnmanagedWriter::DefineLocalVariable Method</span></span>
<span data-ttu-id="32a02-103">Tek bir değişken geçerli sözcük kapsamda tanımlar.</span><span class="sxs-lookup"><span data-stu-id="32a02-103">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="32a02-104">Bu yöntem, birden çok ev bir kapsama sahip aynı ada sahip bir değişken için birden çok kez çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="32a02-104">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="32a02-105">Bu durumda, ancak değerlerini `startOffset` ve `endOffset` parametreleri çakışmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="32a02-105">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32a02-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="32a02-106">Syntax</span></span>  
  
```  
HRESULT DefineLocalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="32a02-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="32a02-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="32a02-108">[in] Bir işaretçi bir `WCHAR` yerel değişken adını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="32a02-108">[in] A pointer to a `WCHAR` that defines the local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="32a02-109">[in] Yerel değişken öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="32a02-109">[in] The local variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="32a02-110">[in] A `ULONG32` bayt cinsinden boyutu belirten `signature` arabellek.</span><span class="sxs-lookup"><span data-stu-id="32a02-110">[in] A `ULONG32` that indicates the size, in bytes, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="32a02-111">[in] Yerel değişken imzası.</span><span class="sxs-lookup"><span data-stu-id="32a02-111">[in] The local variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="32a02-112">[in] Adres türü.</span><span class="sxs-lookup"><span data-stu-id="32a02-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="32a02-113">[in] Parametre belirtimini ilk adresi.</span><span class="sxs-lookup"><span data-stu-id="32a02-113">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="32a02-114">[in] Parametre belirtimini ikinci adresi.</span><span class="sxs-lookup"><span data-stu-id="32a02-114">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="32a02-115">[in] Parametre belirtimini üçüncü adresi.</span><span class="sxs-lookup"><span data-stu-id="32a02-115">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="32a02-116">[in] Değişken için başlangıç uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="32a02-116">[in] The start offset for the variable.</span></span> <span data-ttu-id="32a02-117">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="32a02-117">This parameter is optional.</span></span> <span data-ttu-id="32a02-118">0 ise, bu parametre yoksayılır ve değişken tüm kapsam boyunca tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="32a02-118">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="32a02-119">Bir değerse değişkeni geçerli kapsam uzaklıkları içinde döner.</span><span class="sxs-lookup"><span data-stu-id="32a02-119">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="32a02-120">[in] Değişken için bitiş uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="32a02-120">[in] The end offset for the variable.</span></span> <span data-ttu-id="32a02-121">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="32a02-121">This parameter is optional.</span></span> <span data-ttu-id="32a02-122">0 ise, bu parametre yoksayılır ve değişken tüm kapsam boyunca tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="32a02-122">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="32a02-123">Bir değerse değişkeni geçerli kapsam uzaklıkları içinde döner.</span><span class="sxs-lookup"><span data-stu-id="32a02-123">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="32a02-124">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="32a02-124">Return Value</span></span>  
 <span data-ttu-id="32a02-125">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="32a02-125">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32a02-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="32a02-126">Requirements</span></span>  
 <span data-ttu-id="32a02-127">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="32a02-127">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32a02-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="32a02-128">See Also</span></span>  
 [<span data-ttu-id="32a02-129">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="32a02-129">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="32a02-130">DefineGlobalVariable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="32a02-130">DefineGlobalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)  
 [<span data-ttu-id="32a02-131">DefineLocalVariable2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="32a02-131">DefineLocalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)
