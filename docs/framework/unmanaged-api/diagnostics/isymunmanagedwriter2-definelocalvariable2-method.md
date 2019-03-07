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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d336b35e91abd1b7180c2b918edeba2e1eccdbde
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499595"
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a><span data-ttu-id="7a80f-102">ISymUnmanagedWriter2::DefineLocalVariable2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7a80f-102">ISymUnmanagedWriter2::DefineLocalVariable2 Method</span></span>
<span data-ttu-id="7a80f-103">Tek bir değişken, geçerli sözlü kapsamda tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7a80f-103">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="7a80f-104">Bu yöntem, bir kapsam boyunca birden çok havaalanlarından olan aynı ada sahip bir değişken için birden çok kez çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="7a80f-104">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="7a80f-105">Bu durumda, ancak değerlerini `startOffset` ve `endOffset` parametreleri örtüşmemelidir.</span><span class="sxs-lookup"><span data-stu-id="7a80f-105">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a80f-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7a80f-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="7a80f-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7a80f-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="7a80f-108">[in] Yerel değişken adı.</span><span class="sxs-lookup"><span data-stu-id="7a80f-108">[in] The local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="7a80f-109">[in] Yerel değişken öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="7a80f-109">[in] The local variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="7a80f-110">[in] Meta veri belirteci imzası.</span><span class="sxs-lookup"><span data-stu-id="7a80f-110">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="7a80f-111">[in] Adres türü.</span><span class="sxs-lookup"><span data-stu-id="7a80f-111">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="7a80f-112">[in] Parametre belirtimine ilk adresi.</span><span class="sxs-lookup"><span data-stu-id="7a80f-112">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="7a80f-113">[in] Parametre belirtimine ikinci adresi.</span><span class="sxs-lookup"><span data-stu-id="7a80f-113">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="7a80f-114">[in] Parametre belirtimine üçüncü adresi.</span><span class="sxs-lookup"><span data-stu-id="7a80f-114">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="7a80f-115">[in] Değişken için başlangıç uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="7a80f-115">[in] The start offset for the variable.</span></span> <span data-ttu-id="7a80f-116">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="7a80f-116">This parameter is optional.</span></span> <span data-ttu-id="7a80f-117">0 ise, bu parametre yoksayılır ve tüm kapsam boyunca değişkeni tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="7a80f-117">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="7a80f-118">Sıfır dışında bir değeri ise, geçerli kapsam içinde uzaklıklarını değişkeni döner.</span><span class="sxs-lookup"><span data-stu-id="7a80f-118">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="7a80f-119">[in] Değişken için bitiş uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="7a80f-119">[in] The end offset for the variable.</span></span> <span data-ttu-id="7a80f-120">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="7a80f-120">This parameter is optional.</span></span> <span data-ttu-id="7a80f-121">0 ise, bu parametre yoksayılır ve tüm kapsam boyunca değişkeni tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="7a80f-121">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="7a80f-122">Sıfır dışında bir değeri ise, geçerli kapsam içinde uzaklıklarını değişkeni döner.</span><span class="sxs-lookup"><span data-stu-id="7a80f-122">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7a80f-123">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7a80f-123">Return Value</span></span>  
 <span data-ttu-id="7a80f-124">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="7a80f-124">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a80f-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7a80f-125">Requirements</span></span>  
 <span data-ttu-id="7a80f-126">**Üst bilgi:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="7a80f-126">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a80f-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a80f-127">See also</span></span>
- [<span data-ttu-id="7a80f-128">ISymUnmanagedWriter2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7a80f-128">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="7a80f-129">DefineLocalVariable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7a80f-129">DefineLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
