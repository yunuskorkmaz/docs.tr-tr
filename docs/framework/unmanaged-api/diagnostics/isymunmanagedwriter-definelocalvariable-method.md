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
ms.openlocfilehash: c561eb70f0e3d243984decfb39629601f8eeea37
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59125308"
---
# <a name="isymunmanagedwriterdefinelocalvariable-method"></a><span data-ttu-id="a20e4-102">ISymUnmanagedWriter::DefineLocalVariable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a20e4-102">ISymUnmanagedWriter::DefineLocalVariable Method</span></span>
<span data-ttu-id="a20e4-103">Tek bir değişken, geçerli sözlü kapsamda tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a20e4-103">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="a20e4-104">Bu yöntem, bir kapsam boyunca birden çok havaalanlarından olan aynı ada sahip bir değişken için birden çok kez çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="a20e4-104">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="a20e4-105">Bu durumda, ancak değerlerini `startOffset` ve `endOffset` parametreleri örtüşmemelidir.</span><span class="sxs-lookup"><span data-stu-id="a20e4-105">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a20e4-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a20e4-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="a20e4-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a20e4-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="a20e4-108">[in] Bir işaretçi bir `WCHAR` , yerel değişken adını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a20e4-108">[in] A pointer to a `WCHAR` that defines the local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="a20e4-109">[in] Yerel değişken öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="a20e4-109">[in] The local variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="a20e4-110">[in] A `ULONG32` bayt cinsinden boyutunu belirten `signature` arabellek.</span><span class="sxs-lookup"><span data-stu-id="a20e4-110">[in] A `ULONG32` that indicates the size, in bytes, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="a20e4-111">[in] Yerel değişken imzası.</span><span class="sxs-lookup"><span data-stu-id="a20e4-111">[in] The local variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="a20e4-112">[in] Adres türü.</span><span class="sxs-lookup"><span data-stu-id="a20e4-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="a20e4-113">[in] Parametre belirtimine ilk adresi.</span><span class="sxs-lookup"><span data-stu-id="a20e4-113">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="a20e4-114">[in] Parametre belirtimine ikinci adresi.</span><span class="sxs-lookup"><span data-stu-id="a20e4-114">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="a20e4-115">[in] Parametre belirtimine üçüncü adresi.</span><span class="sxs-lookup"><span data-stu-id="a20e4-115">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="a20e4-116">[in] Değişken için başlangıç uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="a20e4-116">[in] The start offset for the variable.</span></span> <span data-ttu-id="a20e4-117">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a20e4-117">This parameter is optional.</span></span> <span data-ttu-id="a20e4-118">0 ise, bu parametre yoksayılır ve tüm kapsam boyunca değişkeni tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="a20e4-118">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="a20e4-119">Sıfır dışında bir değeri ise, geçerli kapsam içinde uzaklıklarını değişkeni döner.</span><span class="sxs-lookup"><span data-stu-id="a20e4-119">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="a20e4-120">[in] Değişken için bitiş uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="a20e4-120">[in] The end offset for the variable.</span></span> <span data-ttu-id="a20e4-121">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a20e4-121">This parameter is optional.</span></span> <span data-ttu-id="a20e4-122">0 ise, bu parametre yoksayılır ve tüm kapsam boyunca değişkeni tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="a20e4-122">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="a20e4-123">Sıfır dışında bir değeri ise, geçerli kapsam içinde uzaklıklarını değişkeni döner.</span><span class="sxs-lookup"><span data-stu-id="a20e4-123">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a20e4-124">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a20e4-124">Return Value</span></span>  
 <span data-ttu-id="a20e4-125">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="a20e4-125">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a20e4-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a20e4-126">Requirements</span></span>  
 <span data-ttu-id="a20e4-127">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a20e4-127">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a20e4-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a20e4-128">See also</span></span>

- [<span data-ttu-id="a20e4-129">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a20e4-129">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="a20e4-130">DefineGlobalVariable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a20e4-130">DefineGlobalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)
- [<span data-ttu-id="a20e4-131">DefineLocalVariable2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a20e4-131">DefineLocalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)
