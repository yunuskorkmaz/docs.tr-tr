---
title: "ISymUnmanagedWriter2::DefineLocalVariable2 Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter2.DefineLocalVariable2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter2::DefineLocalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2 method [.NET Framework debugging]
- DefineLocalVariable2 method [.NET Framework debugging]
ms.assetid: e774eefe-858c-4362-8d2d-28ebf2ba1a24
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 595cc3d8c503a5a6b2cbcb6665f7ff8aff5044d7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a><span data-ttu-id="ebb7f-102">ISymUnmanagedWriter2::DefineLocalVariable2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ebb7f-102">ISymUnmanagedWriter2::DefineLocalVariable2 Method</span></span>
<span data-ttu-id="ebb7f-103">Tek bir değişken geçerli sözcük kapsamda tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ebb7f-103">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="ebb7f-104">Bu yöntem, birden çok ev bir kapsama sahip aynı ada sahip bir değişken için birden çok kez çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="ebb7f-104">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="ebb7f-105">Bu durumda, ancak değerlerini `startOffset` ve `endOffset` parametreleri çakışmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="ebb7f-105">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebb7f-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ebb7f-106">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="ebb7f-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ebb7f-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="ebb7f-108">[in] Yerel değişken adı.</span><span class="sxs-lookup"><span data-stu-id="ebb7f-108">[in] The local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="ebb7f-109">[in] Yerel değişken öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="ebb7f-109">[in] The local variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="ebb7f-110">[in] İmza meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="ebb7f-110">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="ebb7f-111">[in] Adres türü.</span><span class="sxs-lookup"><span data-stu-id="ebb7f-111">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="ebb7f-112">[in] Parametre belirtimini ilk adresi.</span><span class="sxs-lookup"><span data-stu-id="ebb7f-112">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="ebb7f-113">[in] Parametre belirtimini ikinci adresi.</span><span class="sxs-lookup"><span data-stu-id="ebb7f-113">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="ebb7f-114">[in] Parametre belirtimini üçüncü adresi.</span><span class="sxs-lookup"><span data-stu-id="ebb7f-114">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="ebb7f-115">[in] Değişken için başlangıç uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="ebb7f-115">[in] The start offset for the variable.</span></span> <span data-ttu-id="ebb7f-116">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="ebb7f-116">This parameter is optional.</span></span> <span data-ttu-id="ebb7f-117">0 ise, bu parametre yoksayılır ve değişken tüm kapsam boyunca tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="ebb7f-117">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="ebb7f-118">Bir değerse değişkeni geçerli kapsam uzaklıkları içinde döner.</span><span class="sxs-lookup"><span data-stu-id="ebb7f-118">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="ebb7f-119">[in] Değişken için bitiş uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="ebb7f-119">[in] The end offset for the variable.</span></span> <span data-ttu-id="ebb7f-120">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="ebb7f-120">This parameter is optional.</span></span> <span data-ttu-id="ebb7f-121">0 ise, bu parametre yoksayılır ve değişken tüm kapsam boyunca tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="ebb7f-121">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="ebb7f-122">Bir değerse değişkeni geçerli kapsam uzaklıkları içinde döner.</span><span class="sxs-lookup"><span data-stu-id="ebb7f-122">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ebb7f-123">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ebb7f-123">Return Value</span></span>  
 <span data-ttu-id="ebb7f-124">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="ebb7f-124">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebb7f-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ebb7f-125">Requirements</span></span>  
 <span data-ttu-id="ebb7f-126">**Başlık:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="ebb7f-126">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebb7f-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ebb7f-127">See Also</span></span>  
 [<span data-ttu-id="ebb7f-128">Isymunmanagedwriter2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="ebb7f-128">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 [<span data-ttu-id="ebb7f-129">DefineLocalVariable yöntemi</span><span class="sxs-lookup"><span data-stu-id="ebb7f-129">DefineLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
