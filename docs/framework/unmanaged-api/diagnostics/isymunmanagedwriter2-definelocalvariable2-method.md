---
title: "ISymUnmanagedWriter2::DefineLocalVariable2 Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1124b57bed16e349c753be872c1b709a287e6237
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a><span data-ttu-id="974be-102">ISymUnmanagedWriter2::DefineLocalVariable2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="974be-102">ISymUnmanagedWriter2::DefineLocalVariable2 Method</span></span>
<span data-ttu-id="974be-103">Tek bir değişken geçerli sözcük kapsamda tanımlar.</span><span class="sxs-lookup"><span data-stu-id="974be-103">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="974be-104">Bu yöntem, birden çok ev bir kapsama sahip aynı ada sahip bir değişken için birden çok kez çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="974be-104">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="974be-105">Bu durumda, ancak değerlerini `startOffset` ve `endOffset` parametreleri çakışmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="974be-105">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="974be-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="974be-106">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="974be-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="974be-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="974be-108">[in] Yerel değişken adı.</span><span class="sxs-lookup"><span data-stu-id="974be-108">[in] The local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="974be-109">[in] Yerel değişken öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="974be-109">[in] The local variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="974be-110">[in] İmza meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="974be-110">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="974be-111">[in] Adres türü.</span><span class="sxs-lookup"><span data-stu-id="974be-111">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="974be-112">[in] Parametre belirtimini ilk adresi.</span><span class="sxs-lookup"><span data-stu-id="974be-112">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="974be-113">[in] Parametre belirtimini ikinci adresi.</span><span class="sxs-lookup"><span data-stu-id="974be-113">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="974be-114">[in] Parametre belirtimini üçüncü adresi.</span><span class="sxs-lookup"><span data-stu-id="974be-114">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="974be-115">[in] Değişken için başlangıç uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="974be-115">[in] The start offset for the variable.</span></span> <span data-ttu-id="974be-116">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="974be-116">This parameter is optional.</span></span> <span data-ttu-id="974be-117">0 ise, bu parametre yoksayılır ve değişken tüm kapsam boyunca tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="974be-117">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="974be-118">Bir değerse değişkeni geçerli kapsam uzaklıkları içinde döner.</span><span class="sxs-lookup"><span data-stu-id="974be-118">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="974be-119">[in] Değişken için bitiş uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="974be-119">[in] The end offset for the variable.</span></span> <span data-ttu-id="974be-120">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="974be-120">This parameter is optional.</span></span> <span data-ttu-id="974be-121">0 ise, bu parametre yoksayılır ve değişken tüm kapsam boyunca tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="974be-121">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="974be-122">Bir değerse değişkeni geçerli kapsam uzaklıkları içinde döner.</span><span class="sxs-lookup"><span data-stu-id="974be-122">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="974be-123">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="974be-123">Return Value</span></span>  
 <span data-ttu-id="974be-124">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="974be-124">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="974be-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="974be-125">Requirements</span></span>  
 <span data-ttu-id="974be-126">**Başlık:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="974be-126">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="974be-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="974be-127">See Also</span></span>  
 [<span data-ttu-id="974be-128">ISymUnmanagedWriter2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="974be-128">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 [<span data-ttu-id="974be-129">DefineLocalVariable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="974be-129">DefineLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
