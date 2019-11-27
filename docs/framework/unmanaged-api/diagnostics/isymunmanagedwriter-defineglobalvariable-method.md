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
ms.openlocfilehash: 94d1aa5bba87e8ca11b58bdf89a697e1ccf500b1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428027"
---
# <a name="isymunmanagedwriterdefineglobalvariable-method"></a><span data-ttu-id="03843-102">ISymUnmanagedWriter::DefineGlobalVariable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="03843-102">ISymUnmanagedWriter::DefineGlobalVariable Method</span></span>
<span data-ttu-id="03843-103">Tek bir genel değişkeni tanımlar.</span><span class="sxs-lookup"><span data-stu-id="03843-103">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03843-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="03843-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="03843-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="03843-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="03843-106">'ndaki Genel değişken adını tanımlayan bir `WCHAR` işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="03843-106">[in] A pointer to a `WCHAR` that defines the global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="03843-107">'ndaki Genel değişken öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="03843-107">[in] The global variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="03843-108">'ndaki `signature` arabelleğinin karakter cinsinden boyutunu belirten `ULONG32`.</span><span class="sxs-lookup"><span data-stu-id="03843-108">[in] A `ULONG32` that indicates the size, in characters, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="03843-109">'ndaki Genel değişken imzası.</span><span class="sxs-lookup"><span data-stu-id="03843-109">[in] The global variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="03843-110">'ndaki Adres türü.</span><span class="sxs-lookup"><span data-stu-id="03843-110">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="03843-111">'ndaki Parametre belirtiminin ilk adresi.</span><span class="sxs-lookup"><span data-stu-id="03843-111">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="03843-112">'ndaki Parametre belirtiminin ikinci adresi.</span><span class="sxs-lookup"><span data-stu-id="03843-112">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="03843-113">'ndaki Parametre belirtiminin üçüncü adresi.</span><span class="sxs-lookup"><span data-stu-id="03843-113">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="03843-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="03843-114">Return Value</span></span>  
 <span data-ttu-id="03843-115">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="03843-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03843-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="03843-116">Requirements</span></span>  
 <span data-ttu-id="03843-117">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="03843-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03843-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03843-118">See also</span></span>

- [<span data-ttu-id="03843-119">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="03843-119">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="03843-120">DefineLocalVariable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="03843-120">DefineLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
- [<span data-ttu-id="03843-121">DefineGlobalVariable2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="03843-121">DefineGlobalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineglobalvariable2-method.md)
