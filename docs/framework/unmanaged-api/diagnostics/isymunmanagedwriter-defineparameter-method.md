---
title: "ISymUnmanagedWriter::DefineParameter Yöntemi"
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
- ISymUnmanagedWriter.DefineParameter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineParameter
helpviewer_keywords:
- DefineParameter method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineParameter method [.NET Framework debugging]
ms.assetid: a8e3dd32-6a44-4371-9a74-f417b11998c8
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7fe62a8f6b48d1a9931cc0310811d7fc42f7029b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterdefineparameter-method"></a><span data-ttu-id="5f5b2-102">ISymUnmanagedWriter::DefineParameter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5f5b2-102">ISymUnmanagedWriter::DefineParameter Method</span></span>
<span data-ttu-id="5f5b2-103">Tek bir parametre geçerli yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5f5b2-103">Defines a single parameter in the current method.</span></span> <span data-ttu-id="5f5b2-104">Parametre türü yöntemin imzası parametre konumlarını (sıralı) alınır.</span><span class="sxs-lookup"><span data-stu-id="5f5b2-104">The parameter type is taken from the parameter's position (sequence) within the method's signature.</span></span>  
  
 <span data-ttu-id="5f5b2-105">Parametreleri, verilen bir yöntem için meta verilerde tanımlanmışsa, bu yöntemi kullanarak bunları yeniden tanımlamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="5f5b2-105">If parameters are defined in the metadata for a given method, you do not have to define them again by using this method.</span></span> <span data-ttu-id="5f5b2-106">Sembol okuyucular parametreler için normal meta veriler sembol deposu denetlemeden önce denetlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5f5b2-106">The symbol readers must check the normal metadata for the parameters before checking the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f5b2-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5f5b2-107">Syntax</span></span>  
  
```  
HRESULT DefineParameter(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      sequence,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5f5b2-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5f5b2-108">Parameters</span></span>  
 `name`  
 <span data-ttu-id="5f5b2-109">[in] Parametre adı.</span><span class="sxs-lookup"><span data-stu-id="5f5b2-109">[in] The parameter name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="5f5b2-110">[in] Parametre öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="5f5b2-110">[in] The parameter attributes.</span></span>  
  
 `sequence`  
 <span data-ttu-id="5f5b2-111">[in] Parametre imzası.</span><span class="sxs-lookup"><span data-stu-id="5f5b2-111">[in] The parameter signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="5f5b2-112">[in] Adres türü.</span><span class="sxs-lookup"><span data-stu-id="5f5b2-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="5f5b2-113">[in] Parametre belirtimini ilk adresi.</span><span class="sxs-lookup"><span data-stu-id="5f5b2-113">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="5f5b2-114">[in] Parametre belirtimini ikinci adresi.</span><span class="sxs-lookup"><span data-stu-id="5f5b2-114">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="5f5b2-115">[in] Parametre belirtimini üçüncü adresi.</span><span class="sxs-lookup"><span data-stu-id="5f5b2-115">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5f5b2-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5f5b2-116">Return Value</span></span>  
 <span data-ttu-id="5f5b2-117">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="5f5b2-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f5b2-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5f5b2-118">Requirements</span></span>  
 <span data-ttu-id="5f5b2-119">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5f5b2-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f5b2-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5f5b2-120">See Also</span></span>  
 [<span data-ttu-id="5f5b2-121">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5f5b2-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
