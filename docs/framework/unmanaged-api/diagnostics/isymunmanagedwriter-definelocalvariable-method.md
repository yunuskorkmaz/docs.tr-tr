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
ms.openlocfilehash: b8b9f8e63a0b52dde0e814f53cfc75e6f6d48e78
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723031"
---
# <a name="isymunmanagedwriterdefinelocalvariable-method"></a><span data-ttu-id="6a219-102">ISymUnmanagedWriter::DefineLocalVariable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6a219-102">ISymUnmanagedWriter::DefineLocalVariable Method</span></span>

<span data-ttu-id="6a219-103">Geçerli sözcük kapsamındaki tek bir değişkeni tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6a219-103">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="6a219-104">Bu yöntem, bir kapsam genelinde birden çok evye sahip olan aynı ada sahip bir değişken için birden çok kez çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="6a219-104">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="6a219-105">Ancak bu durumda, `startOffset` ve `endOffset` parametrelerinin değerleri çakışmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="6a219-105">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a219-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="6a219-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="6a219-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6a219-107">Parameters</span></span>  

 `name`  
 <span data-ttu-id="6a219-108">'ndaki `WCHAR` Yerel değişken adını tanımlayan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="6a219-108">[in] A pointer to a `WCHAR` that defines the local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="6a219-109">'ndaki Yerel değişken öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="6a219-109">[in] The local variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="6a219-110">'ndaki `ULONG32` Bu, arabelleğin bayt cinsinden boyutunu belirten bir `signature` .</span><span class="sxs-lookup"><span data-stu-id="6a219-110">[in] A `ULONG32` that indicates the size, in bytes, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="6a219-111">'ndaki Yerel değişken imzası.</span><span class="sxs-lookup"><span data-stu-id="6a219-111">[in] The local variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="6a219-112">'ndaki Adres türü.</span><span class="sxs-lookup"><span data-stu-id="6a219-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="6a219-113">'ndaki Parametre belirtiminin ilk adresi.</span><span class="sxs-lookup"><span data-stu-id="6a219-113">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="6a219-114">'ndaki Parametre belirtiminin ikinci adresi.</span><span class="sxs-lookup"><span data-stu-id="6a219-114">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="6a219-115">'ndaki Parametre belirtiminin üçüncü adresi.</span><span class="sxs-lookup"><span data-stu-id="6a219-115">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="6a219-116">'ndaki Değişkenin başlangıç boşluğu.</span><span class="sxs-lookup"><span data-stu-id="6a219-116">[in] The start offset for the variable.</span></span> <span data-ttu-id="6a219-117">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="6a219-117">This parameter is optional.</span></span> <span data-ttu-id="6a219-118">0 ise, bu parametre yok sayılır ve değişken tüm kapsam genelinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="6a219-118">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="6a219-119">Sıfır olmayan bir değerse, değişken geçerli kapsamın uzaklıkları dahilinde olur.</span><span class="sxs-lookup"><span data-stu-id="6a219-119">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="6a219-120">'ndaki Değişkenin bitiş boşluğu.</span><span class="sxs-lookup"><span data-stu-id="6a219-120">[in] The end offset for the variable.</span></span> <span data-ttu-id="6a219-121">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="6a219-121">This parameter is optional.</span></span> <span data-ttu-id="6a219-122">0 ise, bu parametre yok sayılır ve değişken tüm kapsam genelinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="6a219-122">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="6a219-123">Sıfır olmayan bir değerse, değişken geçerli kapsamın uzaklıkları dahilinde olur.</span><span class="sxs-lookup"><span data-stu-id="6a219-123">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6a219-124">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6a219-124">Return Value</span></span>  

 <span data-ttu-id="6a219-125">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="6a219-125">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a219-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6a219-126">Requirements</span></span>  

 <span data-ttu-id="6a219-127">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="6a219-127">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a219-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a219-128">See also</span></span>

- [<span data-ttu-id="6a219-129">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6a219-129">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="6a219-130">DefineGlobalVariable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6a219-130">DefineGlobalVariable Method</span></span>](isymunmanagedwriter-defineglobalvariable-method.md)
- [<span data-ttu-id="6a219-131">DefineLocalVariable2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6a219-131">DefineLocalVariable2 Method</span></span>](isymunmanagedwriter2-definelocalvariable2-method.md)
