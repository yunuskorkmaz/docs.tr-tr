---
description: 'Şu konuda daha fazla bilgi edinin: ı, efineGlobalVariable yöntemi:D'
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
ms.openlocfilehash: 70dccfed054a9ac79baf3f28683edc9a14d3cdf7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762389"
---
# <a name="isymunmanagedwriterdefineglobalvariable-method"></a><span data-ttu-id="cd2a6-103">ISymUnmanagedWriter::DefineGlobalVariable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cd2a6-103">ISymUnmanagedWriter::DefineGlobalVariable Method</span></span>

<span data-ttu-id="cd2a6-104">Tek bir genel değişkeni tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cd2a6-104">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd2a6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cd2a6-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="cd2a6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cd2a6-106">Parameters</span></span>  

 `name`  
 <span data-ttu-id="cd2a6-107">'ndaki `WCHAR` Genel değişken adını tanımlayan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="cd2a6-107">[in] A pointer to a `WCHAR` that defines the global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="cd2a6-108">'ndaki Genel değişken öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="cd2a6-108">[in] The global variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="cd2a6-109">'ndaki `ULONG32` Bu, arabelleğin karakter cinsinden boyutunu belirten bir `signature` .</span><span class="sxs-lookup"><span data-stu-id="cd2a6-109">[in] A `ULONG32` that indicates the size, in characters, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="cd2a6-110">'ndaki Genel değişken imzası.</span><span class="sxs-lookup"><span data-stu-id="cd2a6-110">[in] The global variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="cd2a6-111">'ndaki Adres türü.</span><span class="sxs-lookup"><span data-stu-id="cd2a6-111">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="cd2a6-112">'ndaki Parametre belirtiminin ilk adresi.</span><span class="sxs-lookup"><span data-stu-id="cd2a6-112">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="cd2a6-113">'ndaki Parametre belirtiminin ikinci adresi.</span><span class="sxs-lookup"><span data-stu-id="cd2a6-113">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="cd2a6-114">'ndaki Parametre belirtiminin üçüncü adresi.</span><span class="sxs-lookup"><span data-stu-id="cd2a6-114">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cd2a6-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cd2a6-115">Return Value</span></span>  

 <span data-ttu-id="cd2a6-116">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="cd2a6-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd2a6-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cd2a6-117">Requirements</span></span>  

 <span data-ttu-id="cd2a6-118">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="cd2a6-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd2a6-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd2a6-119">See also</span></span>

- [<span data-ttu-id="cd2a6-120">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cd2a6-120">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="cd2a6-121">DefineLocalVariable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cd2a6-121">DefineLocalVariable Method</span></span>](isymunmanagedwriter-definelocalvariable-method.md)
- [<span data-ttu-id="cd2a6-122">DefineGlobalVariable2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cd2a6-122">DefineGlobalVariable2 Method</span></span>](isymunmanagedwriter2-defineglobalvariable2-method.md)
