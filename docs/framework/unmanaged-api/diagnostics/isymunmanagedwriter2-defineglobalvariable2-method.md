---
title: "ISymUnmanagedWriter2::DefineGlobalVariable2 Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter2.DefineGlobalVariable2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter2::DefineGlobalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineGlobalVariable2 method [.NET Framework debugging]
- DefineGlobalVariable2 method [.NET Framework debugging]
ms.assetid: 04d569d6-a151-4957-9872-f3f694c3e4a9
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 617e3f03f4b1c126a56b47db34ec7044bea8c58b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter2defineglobalvariable2-method"></a><span data-ttu-id="365bb-102">ISymUnmanagedWriter2::DefineGlobalVariable2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="365bb-102">ISymUnmanagedWriter2::DefineGlobalVariable2 Method</span></span>
<span data-ttu-id="365bb-103">Tek bir genel değişkeni tanımlar.</span><span class="sxs-lookup"><span data-stu-id="365bb-103">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="365bb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="365bb-104">Syntax</span></span>  
  
```  
HRESULT DefineGlobalVariable2(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] mdSignature  sigToken,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="365bb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="365bb-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="365bb-106">[in] Genel değişken adı.</span><span class="sxs-lookup"><span data-stu-id="365bb-106">[in] The global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="365bb-107">[in] Genel değişken öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="365bb-107">[in] The global variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="365bb-108">[in] İmza meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="365bb-108">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="365bb-109">[in] Adres türü.</span><span class="sxs-lookup"><span data-stu-id="365bb-109">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="365bb-110">[in] Parametre belirtimini ilk adresi.</span><span class="sxs-lookup"><span data-stu-id="365bb-110">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="365bb-111">[in] Parametre belirtimini ikinci adresi.</span><span class="sxs-lookup"><span data-stu-id="365bb-111">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="365bb-112">[in] Parametre belirtimini üçüncü adresi.</span><span class="sxs-lookup"><span data-stu-id="365bb-112">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="365bb-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="365bb-113">Return Value</span></span>  
 <span data-ttu-id="365bb-114">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="365bb-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="365bb-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="365bb-115">Requirements</span></span>  
 <span data-ttu-id="365bb-116">**Başlık:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="365bb-116">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="365bb-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="365bb-117">See Also</span></span>  
 [<span data-ttu-id="365bb-118">ISymUnmanagedWriter2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="365bb-118">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 [<span data-ttu-id="365bb-119">DefineGlobalVariable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="365bb-119">DefineGlobalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)
