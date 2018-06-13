---
title: ISymUnmanagedWriter::DefineGlobalVariable Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineGlobalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable method [.NET Framework debugging]
- DefineGlobalVariable method [.NET Framework debugging]
ms.assetid: 843c904a-8176-4d8f-bd47-b4d4c29f4c5c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f1dd657c004c58480ea2f603ad4494753463c79b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428451"
---
# <a name="isymunmanagedwriterdefineglobalvariable-method"></a><span data-ttu-id="302fd-102">ISymUnmanagedWriter::DefineGlobalVariable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="302fd-102">ISymUnmanagedWriter::DefineGlobalVariable Method</span></span>
<span data-ttu-id="302fd-103">Tek bir genel değişkeni tanımlar.</span><span class="sxs-lookup"><span data-stu-id="302fd-103">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="302fd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="302fd-104">Syntax</span></span>  
  
```  
HRESULT DefineGlobalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="302fd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="302fd-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="302fd-106">[in] Bir işaretçi bir `WCHAR` genel değişken adını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="302fd-106">[in] A pointer to a `WCHAR` that defines the global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="302fd-107">[in] Genel değişken öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="302fd-107">[in] The global variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="302fd-108">[in] A `ULONG32` boyutunda karakterleri belirten `signature` arabellek.</span><span class="sxs-lookup"><span data-stu-id="302fd-108">[in] A `ULONG32` that indicates the size, in characters, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="302fd-109">[in] Genel değişken imzası.</span><span class="sxs-lookup"><span data-stu-id="302fd-109">[in] The global variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="302fd-110">[in] Adres türü.</span><span class="sxs-lookup"><span data-stu-id="302fd-110">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="302fd-111">[in] Parametre belirtimini ilk adresi.</span><span class="sxs-lookup"><span data-stu-id="302fd-111">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="302fd-112">[in] Parametre belirtimini ikinci adresi.</span><span class="sxs-lookup"><span data-stu-id="302fd-112">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="302fd-113">[in] Parametre belirtimini üçüncü adresi.</span><span class="sxs-lookup"><span data-stu-id="302fd-113">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="302fd-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="302fd-114">Return Value</span></span>  
 <span data-ttu-id="302fd-115">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="302fd-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="302fd-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="302fd-116">Requirements</span></span>  
 <span data-ttu-id="302fd-117">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="302fd-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="302fd-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="302fd-118">See Also</span></span>  
 [<span data-ttu-id="302fd-119">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="302fd-119">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="302fd-120">DefineLocalVariable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="302fd-120">DefineLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)  
 [<span data-ttu-id="302fd-121">DefineGlobalVariable2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="302fd-121">DefineGlobalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineglobalvariable2-method.md)
