---
title: ISymUnmanagedWriter2::DefineGlobalVariable2 Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineGlobalVariable2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineGlobalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineGlobalVariable2 method [.NET Framework debugging]
- DefineGlobalVariable2 method [.NET Framework debugging]
ms.assetid: 04d569d6-a151-4957-9872-f3f694c3e4a9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a6bc6c52374ea047d2e76d346ee8bbc3faaa7bb2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59145229"
---
# <a name="isymunmanagedwriter2defineglobalvariable2-method"></a><span data-ttu-id="5a205-102">ISymUnmanagedWriter2::DefineGlobalVariable2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5a205-102">ISymUnmanagedWriter2::DefineGlobalVariable2 Method</span></span>
<span data-ttu-id="5a205-103">Tek bir genel değişken tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5a205-103">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a205-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5a205-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="5a205-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5a205-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="5a205-106">[in] Genel değişkenin adı.</span><span class="sxs-lookup"><span data-stu-id="5a205-106">[in] The global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="5a205-107">[in] Genel değişken öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="5a205-107">[in] The global variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="5a205-108">[in] Meta veri belirteci imzası.</span><span class="sxs-lookup"><span data-stu-id="5a205-108">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="5a205-109">[in] Adres türü.</span><span class="sxs-lookup"><span data-stu-id="5a205-109">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="5a205-110">[in] Parametre belirtimine ilk adresi.</span><span class="sxs-lookup"><span data-stu-id="5a205-110">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="5a205-111">[in] Parametre belirtimine ikinci adresi.</span><span class="sxs-lookup"><span data-stu-id="5a205-111">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="5a205-112">[in] Parametre belirtimine üçüncü adresi.</span><span class="sxs-lookup"><span data-stu-id="5a205-112">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5a205-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5a205-113">Return Value</span></span>  
 <span data-ttu-id="5a205-114">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="5a205-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a205-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5a205-115">Requirements</span></span>  
 <span data-ttu-id="5a205-116">**Üst bilgi:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="5a205-116">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a205-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a205-117">See also</span></span>

- [<span data-ttu-id="5a205-118">ISymUnmanagedWriter2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5a205-118">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="5a205-119">DefineGlobalVariable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5a205-119">DefineGlobalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)
