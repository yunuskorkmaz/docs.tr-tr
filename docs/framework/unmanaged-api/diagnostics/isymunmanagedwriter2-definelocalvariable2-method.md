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
ms.openlocfilehash: cdbb09d25f51e479a8a8ddfc23348305ba7c0a71
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683426"
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a><span data-ttu-id="95b44-102">ISymUnmanagedWriter2::DefineLocalVariable2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="95b44-102">ISymUnmanagedWriter2::DefineLocalVariable2 Method</span></span>

<span data-ttu-id="95b44-103">Geçerli sözcük kapsamındaki tek bir değişkeni tanımlar.</span><span class="sxs-lookup"><span data-stu-id="95b44-103">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="95b44-104">Bu yöntem, bir kapsam genelinde birden çok evye sahip olan aynı ada sahip bir değişken için birden çok kez çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="95b44-104">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="95b44-105">Ancak bu durumda, `startOffset` ve `endOffset` parametrelerinin değerleri çakışmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="95b44-105">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95b44-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="95b44-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="95b44-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="95b44-107">Parameters</span></span>  

 `name`  
 <span data-ttu-id="95b44-108">'ndaki Yerel değişken adı.</span><span class="sxs-lookup"><span data-stu-id="95b44-108">[in] The local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="95b44-109">'ndaki Yerel değişken öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="95b44-109">[in] The local variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="95b44-110">'ndaki İmzanın meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="95b44-110">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="95b44-111">'ndaki Adres türü.</span><span class="sxs-lookup"><span data-stu-id="95b44-111">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="95b44-112">'ndaki Parametre belirtiminin ilk adresi.</span><span class="sxs-lookup"><span data-stu-id="95b44-112">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="95b44-113">'ndaki Parametre belirtiminin ikinci adresi.</span><span class="sxs-lookup"><span data-stu-id="95b44-113">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="95b44-114">'ndaki Parametre belirtiminin üçüncü adresi.</span><span class="sxs-lookup"><span data-stu-id="95b44-114">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="95b44-115">'ndaki Değişkenin başlangıç boşluğu.</span><span class="sxs-lookup"><span data-stu-id="95b44-115">[in] The start offset for the variable.</span></span> <span data-ttu-id="95b44-116">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="95b44-116">This parameter is optional.</span></span> <span data-ttu-id="95b44-117">0 ise, bu parametre yok sayılır ve değişken tüm kapsam genelinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="95b44-117">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="95b44-118">Sıfır olmayan bir değerse, değişken geçerli kapsamın uzaklıkları dahilinde olur.</span><span class="sxs-lookup"><span data-stu-id="95b44-118">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="95b44-119">'ndaki Değişkenin bitiş boşluğu.</span><span class="sxs-lookup"><span data-stu-id="95b44-119">[in] The end offset for the variable.</span></span> <span data-ttu-id="95b44-120">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="95b44-120">This parameter is optional.</span></span> <span data-ttu-id="95b44-121">0 ise, bu parametre yok sayılır ve değişken tüm kapsam genelinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="95b44-121">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="95b44-122">Sıfır olmayan bir değerse, değişken geçerli kapsamın uzaklıkları dahilinde olur.</span><span class="sxs-lookup"><span data-stu-id="95b44-122">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="95b44-123">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="95b44-123">Return Value</span></span>  

 <span data-ttu-id="95b44-124">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="95b44-124">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95b44-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="95b44-125">Requirements</span></span>  

 <span data-ttu-id="95b44-126">**Üst bilgi:** Corsya. IDL</span><span class="sxs-lookup"><span data-stu-id="95b44-126">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95b44-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95b44-127">See also</span></span>

- [<span data-ttu-id="95b44-128">ISymUnmanagedWriter2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="95b44-128">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="95b44-129">DefineLocalVariable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="95b44-129">DefineLocalVariable Method</span></span>](isymunmanagedwriter-definelocalvariable-method.md)
