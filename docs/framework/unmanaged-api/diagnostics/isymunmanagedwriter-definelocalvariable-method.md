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
ms.openlocfilehash: f6a741df3ea57b5e9b4fa8bc5d304bfedd1d6c15
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428014"
---
# <a name="isymunmanagedwriterdefinelocalvariable-method"></a><span data-ttu-id="39627-102">ISymUnmanagedWriter::DefineLocalVariable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="39627-102">ISymUnmanagedWriter::DefineLocalVariable Method</span></span>
<span data-ttu-id="39627-103">Geçerli sözcük kapsamındaki tek bir değişkeni tanımlar.</span><span class="sxs-lookup"><span data-stu-id="39627-103">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="39627-104">Bu yöntem, bir kapsam genelinde birden çok evye sahip olan aynı ada sahip bir değişken için birden çok kez çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="39627-104">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="39627-105">Ancak, bu durumda, `startOffset` ve `endOffset` parametrelerinin değerleri çakışmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="39627-105">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39627-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="39627-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="39627-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="39627-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="39627-108">'ndaki Yerel değişken adını tanımlayan bir `WCHAR` işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="39627-108">[in] A pointer to a `WCHAR` that defines the local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="39627-109">'ndaki Yerel değişken öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="39627-109">[in] The local variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="39627-110">'ndaki `signature` arabelleğinin boyutunu bayt cinsinden belirten bir `ULONG32`.</span><span class="sxs-lookup"><span data-stu-id="39627-110">[in] A `ULONG32` that indicates the size, in bytes, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="39627-111">'ndaki Yerel değişken imzası.</span><span class="sxs-lookup"><span data-stu-id="39627-111">[in] The local variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="39627-112">'ndaki Adres türü.</span><span class="sxs-lookup"><span data-stu-id="39627-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="39627-113">'ndaki Parametre belirtiminin ilk adresi.</span><span class="sxs-lookup"><span data-stu-id="39627-113">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="39627-114">'ndaki Parametre belirtiminin ikinci adresi.</span><span class="sxs-lookup"><span data-stu-id="39627-114">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="39627-115">'ndaki Parametre belirtiminin üçüncü adresi.</span><span class="sxs-lookup"><span data-stu-id="39627-115">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="39627-116">'ndaki Değişkenin başlangıç boşluğu.</span><span class="sxs-lookup"><span data-stu-id="39627-116">[in] The start offset for the variable.</span></span> <span data-ttu-id="39627-117">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="39627-117">This parameter is optional.</span></span> <span data-ttu-id="39627-118">0 ise, bu parametre yok sayılır ve değişken tüm kapsam genelinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="39627-118">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="39627-119">Sıfır olmayan bir değerse, değişken geçerli kapsamın uzaklıkları dahilinde olur.</span><span class="sxs-lookup"><span data-stu-id="39627-119">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="39627-120">'ndaki Değişkenin bitiş boşluğu.</span><span class="sxs-lookup"><span data-stu-id="39627-120">[in] The end offset for the variable.</span></span> <span data-ttu-id="39627-121">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="39627-121">This parameter is optional.</span></span> <span data-ttu-id="39627-122">0 ise, bu parametre yok sayılır ve değişken tüm kapsam genelinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="39627-122">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="39627-123">Sıfır olmayan bir değerse, değişken geçerli kapsamın uzaklıkları dahilinde olur.</span><span class="sxs-lookup"><span data-stu-id="39627-123">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="39627-124">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="39627-124">Return Value</span></span>  
 <span data-ttu-id="39627-125">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="39627-125">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39627-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="39627-126">Requirements</span></span>  
 <span data-ttu-id="39627-127">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="39627-127">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39627-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39627-128">See also</span></span>

- [<span data-ttu-id="39627-129">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="39627-129">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="39627-130">DefineGlobalVariable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="39627-130">DefineGlobalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)
- [<span data-ttu-id="39627-131">DefineLocalVariable2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="39627-131">DefineLocalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)
