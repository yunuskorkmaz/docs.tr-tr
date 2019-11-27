---
title: ISymUnmanagedWriter2::DefineLocalVariable2 Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineLocalVariable2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2 method [.NET Framework debugging]
- DefineLocalVariable2 method [.NET Framework debugging]
ms.assetid: e774eefe-858c-4362-8d2d-28ebf2ba1a24
topic_type:
- apiref
ms.openlocfilehash: 73f536b4ab98aa596c2395810cb8b616ffd309e9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438299"
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a><span data-ttu-id="52cdc-102">ISymUnmanagedWriter2::DefineLocalVariable2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="52cdc-102">ISymUnmanagedWriter2::DefineLocalVariable2 Method</span></span>
<span data-ttu-id="52cdc-103">Geçerli sözcük kapsamındaki tek bir değişkeni tanımlar.</span><span class="sxs-lookup"><span data-stu-id="52cdc-103">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="52cdc-104">Bu yöntem, bir kapsam genelinde birden çok evye sahip olan aynı ada sahip bir değişken için birden çok kez çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="52cdc-104">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="52cdc-105">Ancak, bu durumda, `startOffset` ve `endOffset` parametrelerinin değerleri çakışmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="52cdc-105">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52cdc-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="52cdc-106">Syntax</span></span>  
  
```cpp  
HRESULT DefineLocalVariable2(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] mdSignature  sigToken,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52cdc-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="52cdc-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="52cdc-108">'ndaki Yerel değişken adı.</span><span class="sxs-lookup"><span data-stu-id="52cdc-108">[in] The local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="52cdc-109">'ndaki Yerel değişken öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="52cdc-109">[in] The local variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="52cdc-110">'ndaki İmzanın meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="52cdc-110">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="52cdc-111">'ndaki Adres türü.</span><span class="sxs-lookup"><span data-stu-id="52cdc-111">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="52cdc-112">'ndaki Parametre belirtiminin ilk adresi.</span><span class="sxs-lookup"><span data-stu-id="52cdc-112">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="52cdc-113">'ndaki Parametre belirtiminin ikinci adresi.</span><span class="sxs-lookup"><span data-stu-id="52cdc-113">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="52cdc-114">'ndaki Parametre belirtiminin üçüncü adresi.</span><span class="sxs-lookup"><span data-stu-id="52cdc-114">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="52cdc-115">'ndaki Değişkenin başlangıç boşluğu.</span><span class="sxs-lookup"><span data-stu-id="52cdc-115">[in] The start offset for the variable.</span></span> <span data-ttu-id="52cdc-116">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="52cdc-116">This parameter is optional.</span></span> <span data-ttu-id="52cdc-117">0 ise, bu parametre yok sayılır ve değişken tüm kapsam genelinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="52cdc-117">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="52cdc-118">Sıfır olmayan bir değerse, değişken geçerli kapsamın uzaklıkları dahilinde olur.</span><span class="sxs-lookup"><span data-stu-id="52cdc-118">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="52cdc-119">'ndaki Değişkenin bitiş boşluğu.</span><span class="sxs-lookup"><span data-stu-id="52cdc-119">[in] The end offset for the variable.</span></span> <span data-ttu-id="52cdc-120">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="52cdc-120">This parameter is optional.</span></span> <span data-ttu-id="52cdc-121">0 ise, bu parametre yok sayılır ve değişken tüm kapsam genelinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="52cdc-121">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="52cdc-122">Sıfır olmayan bir değerse, değişken geçerli kapsamın uzaklıkları dahilinde olur.</span><span class="sxs-lookup"><span data-stu-id="52cdc-122">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="52cdc-123">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="52cdc-123">Return Value</span></span>  
 <span data-ttu-id="52cdc-124">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="52cdc-124">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52cdc-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="52cdc-125">Requirements</span></span>  
 <span data-ttu-id="52cdc-126">**Üst bilgi:** Corsya. IDL</span><span class="sxs-lookup"><span data-stu-id="52cdc-126">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52cdc-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52cdc-127">See also</span></span>

- [<span data-ttu-id="52cdc-128">ISymUnmanagedWriter2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="52cdc-128">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="52cdc-129">DefineLocalVariable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="52cdc-129">DefineLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
