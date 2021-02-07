---
description: 'Hakkında daha fazla bilgi edinin: ISymUnmanagedWriter2::D efineLocalVariable2 yöntemi'
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
ms.openlocfilehash: 169a086b8420b5dbe20af8e16b21d5b41a958ead
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761817"
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a><span data-ttu-id="0c0b6-103">ISymUnmanagedWriter2::DefineLocalVariable2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0c0b6-103">ISymUnmanagedWriter2::DefineLocalVariable2 Method</span></span>

<span data-ttu-id="0c0b6-104">Geçerli sözcük kapsamındaki tek bir değişkeni tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0c0b6-104">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="0c0b6-105">Bu yöntem, bir kapsam genelinde birden çok evye sahip olan aynı ada sahip bir değişken için birden çok kez çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="0c0b6-105">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="0c0b6-106">Ancak bu durumda, `startOffset` ve `endOffset` parametrelerinin değerleri çakışmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="0c0b6-106">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c0b6-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0c0b6-107">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="0c0b6-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0c0b6-108">Parameters</span></span>  

 `name`  
 <span data-ttu-id="0c0b6-109">'ndaki Yerel değişken adı.</span><span class="sxs-lookup"><span data-stu-id="0c0b6-109">[in] The local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="0c0b6-110">'ndaki Yerel değişken öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="0c0b6-110">[in] The local variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="0c0b6-111">'ndaki İmzanın meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="0c0b6-111">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="0c0b6-112">'ndaki Adres türü.</span><span class="sxs-lookup"><span data-stu-id="0c0b6-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="0c0b6-113">'ndaki Parametre belirtiminin ilk adresi.</span><span class="sxs-lookup"><span data-stu-id="0c0b6-113">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="0c0b6-114">'ndaki Parametre belirtiminin ikinci adresi.</span><span class="sxs-lookup"><span data-stu-id="0c0b6-114">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="0c0b6-115">'ndaki Parametre belirtiminin üçüncü adresi.</span><span class="sxs-lookup"><span data-stu-id="0c0b6-115">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="0c0b6-116">'ndaki Değişkenin başlangıç boşluğu.</span><span class="sxs-lookup"><span data-stu-id="0c0b6-116">[in] The start offset for the variable.</span></span> <span data-ttu-id="0c0b6-117">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0c0b6-117">This parameter is optional.</span></span> <span data-ttu-id="0c0b6-118">0 ise, bu parametre yok sayılır ve değişken tüm kapsam genelinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="0c0b6-118">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="0c0b6-119">Sıfır olmayan bir değerse, değişken geçerli kapsamın uzaklıkları dahilinde olur.</span><span class="sxs-lookup"><span data-stu-id="0c0b6-119">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="0c0b6-120">'ndaki Değişkenin bitiş boşluğu.</span><span class="sxs-lookup"><span data-stu-id="0c0b6-120">[in] The end offset for the variable.</span></span> <span data-ttu-id="0c0b6-121">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0c0b6-121">This parameter is optional.</span></span> <span data-ttu-id="0c0b6-122">0 ise, bu parametre yok sayılır ve değişken tüm kapsam genelinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="0c0b6-122">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="0c0b6-123">Sıfır olmayan bir değerse, değişken geçerli kapsamın uzaklıkları dahilinde olur.</span><span class="sxs-lookup"><span data-stu-id="0c0b6-123">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0c0b6-124">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0c0b6-124">Return Value</span></span>  

 <span data-ttu-id="0c0b6-125">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="0c0b6-125">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c0b6-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0c0b6-126">Requirements</span></span>  

 <span data-ttu-id="0c0b6-127">**Üst bilgi:** Corsya. IDL</span><span class="sxs-lookup"><span data-stu-id="0c0b6-127">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c0b6-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c0b6-128">See also</span></span>

- [<span data-ttu-id="0c0b6-129">ISymUnmanagedWriter2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0c0b6-129">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="0c0b6-130">DefineLocalVariable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0c0b6-130">DefineLocalVariable Method</span></span>](isymunmanagedwriter-definelocalvariable-method.md)
