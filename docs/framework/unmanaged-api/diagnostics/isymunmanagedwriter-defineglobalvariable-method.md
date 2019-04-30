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
ms.openlocfilehash: 66efe5ae1fe2154684d2ac6791895b7fcbe4f7b6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763594"
---
# <a name="isymunmanagedwriterdefineglobalvariable-method"></a><span data-ttu-id="6b4a6-102">ISymUnmanagedWriter::DefineGlobalVariable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6b4a6-102">ISymUnmanagedWriter::DefineGlobalVariable Method</span></span>
<span data-ttu-id="6b4a6-103">Tek bir genel değişken tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6b4a6-103">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b4a6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6b4a6-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="6b4a6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6b4a6-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="6b4a6-106">[in] Bir işaretçi bir `WCHAR` tanımlayan genel değişkenin adı.</span><span class="sxs-lookup"><span data-stu-id="6b4a6-106">[in] A pointer to a `WCHAR` that defines the global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="6b4a6-107">[in] Genel değişken öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="6b4a6-107">[in] The global variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="6b4a6-108">[in] A `ULONG32` karakter cinsinden boyutunu belirten `signature` arabellek.</span><span class="sxs-lookup"><span data-stu-id="6b4a6-108">[in] A `ULONG32` that indicates the size, in characters, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="6b4a6-109">[in] Genel değişken imzası.</span><span class="sxs-lookup"><span data-stu-id="6b4a6-109">[in] The global variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="6b4a6-110">[in] Adres türü.</span><span class="sxs-lookup"><span data-stu-id="6b4a6-110">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="6b4a6-111">[in] Parametre belirtimine ilk adresi.</span><span class="sxs-lookup"><span data-stu-id="6b4a6-111">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="6b4a6-112">[in] Parametre belirtimine ikinci adresi.</span><span class="sxs-lookup"><span data-stu-id="6b4a6-112">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="6b4a6-113">[in] Parametre belirtimine üçüncü adresi.</span><span class="sxs-lookup"><span data-stu-id="6b4a6-113">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6b4a6-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6b4a6-114">Return Value</span></span>  
 <span data-ttu-id="6b4a6-115">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="6b4a6-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b4a6-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6b4a6-116">Requirements</span></span>  
 <span data-ttu-id="6b4a6-117">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6b4a6-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b4a6-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b4a6-118">See also</span></span>

- [<span data-ttu-id="6b4a6-119">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6b4a6-119">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="6b4a6-120">DefineLocalVariable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6b4a6-120">DefineLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
- [<span data-ttu-id="6b4a6-121">DefineGlobalVariable2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6b4a6-121">DefineGlobalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineglobalvariable2-method.md)
