---
description: 'Şu konuda daha fazla bilgi edinin: ıdimunmanagedwriter::D efineLocalVariable yöntemi'
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
ms.openlocfilehash: cd817e3002c2a55fd8bbd7e565283752926f746b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762376"
---
# <a name="isymunmanagedwriterdefinelocalvariable-method"></a><span data-ttu-id="9a498-103">ISymUnmanagedWriter::DefineLocalVariable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9a498-103">ISymUnmanagedWriter::DefineLocalVariable Method</span></span>

<span data-ttu-id="9a498-104">Geçerli sözcük kapsamındaki tek bir değişkeni tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9a498-104">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="9a498-105">Bu yöntem, bir kapsam genelinde birden çok evye sahip olan aynı ada sahip bir değişken için birden çok kez çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="9a498-105">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="9a498-106">Ancak bu durumda, `startOffset` ve `endOffset` parametrelerinin değerleri çakışmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="9a498-106">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a498-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9a498-107">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="9a498-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9a498-108">Parameters</span></span>  

 `name`  
 <span data-ttu-id="9a498-109">'ndaki `WCHAR` Yerel değişken adını tanımlayan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="9a498-109">[in] A pointer to a `WCHAR` that defines the local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="9a498-110">'ndaki Yerel değişken öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="9a498-110">[in] The local variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="9a498-111">'ndaki `ULONG32` Bu, arabelleğin bayt cinsinden boyutunu belirten bir `signature` .</span><span class="sxs-lookup"><span data-stu-id="9a498-111">[in] A `ULONG32` that indicates the size, in bytes, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="9a498-112">'ndaki Yerel değişken imzası.</span><span class="sxs-lookup"><span data-stu-id="9a498-112">[in] The local variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="9a498-113">'ndaki Adres türü.</span><span class="sxs-lookup"><span data-stu-id="9a498-113">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="9a498-114">'ndaki Parametre belirtiminin ilk adresi.</span><span class="sxs-lookup"><span data-stu-id="9a498-114">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="9a498-115">'ndaki Parametre belirtiminin ikinci adresi.</span><span class="sxs-lookup"><span data-stu-id="9a498-115">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="9a498-116">'ndaki Parametre belirtiminin üçüncü adresi.</span><span class="sxs-lookup"><span data-stu-id="9a498-116">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="9a498-117">'ndaki Değişkenin başlangıç boşluğu.</span><span class="sxs-lookup"><span data-stu-id="9a498-117">[in] The start offset for the variable.</span></span> <span data-ttu-id="9a498-118">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="9a498-118">This parameter is optional.</span></span> <span data-ttu-id="9a498-119">0 ise, bu parametre yok sayılır ve değişken tüm kapsam genelinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="9a498-119">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="9a498-120">Sıfır olmayan bir değerse, değişken geçerli kapsamın uzaklıkları dahilinde olur.</span><span class="sxs-lookup"><span data-stu-id="9a498-120">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="9a498-121">'ndaki Değişkenin bitiş boşluğu.</span><span class="sxs-lookup"><span data-stu-id="9a498-121">[in] The end offset for the variable.</span></span> <span data-ttu-id="9a498-122">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="9a498-122">This parameter is optional.</span></span> <span data-ttu-id="9a498-123">0 ise, bu parametre yok sayılır ve değişken tüm kapsam genelinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="9a498-123">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="9a498-124">Sıfır olmayan bir değerse, değişken geçerli kapsamın uzaklıkları dahilinde olur.</span><span class="sxs-lookup"><span data-stu-id="9a498-124">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9a498-125">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9a498-125">Return Value</span></span>  

 <span data-ttu-id="9a498-126">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="9a498-126">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a498-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9a498-127">Requirements</span></span>  

 <span data-ttu-id="9a498-128">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="9a498-128">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a498-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a498-129">See also</span></span>

- [<span data-ttu-id="9a498-130">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9a498-130">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="9a498-131">DefineGlobalVariable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9a498-131">DefineGlobalVariable Method</span></span>](isymunmanagedwriter-defineglobalvariable-method.md)
- [<span data-ttu-id="9a498-132">DefineLocalVariable2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9a498-132">DefineLocalVariable2 Method</span></span>](isymunmanagedwriter2-definelocalvariable2-method.md)
