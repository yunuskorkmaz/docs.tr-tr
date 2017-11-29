---
title: "ISymUnmanagedWriter::DefineParameter Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.DefineParameter
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::DefineParameter
helpviewer_keywords:
- DefineParameter method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineParameter method [.NET Framework debugging]
ms.assetid: a8e3dd32-6a44-4371-9a74-f417b11998c8
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 166087a27d0aa7b100da563c25f7e5a52612ce50
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriterdefineparameter-method"></a><span data-ttu-id="20d81-102">ISymUnmanagedWriter::DefineParameter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="20d81-102">ISymUnmanagedWriter::DefineParameter Method</span></span>
<span data-ttu-id="20d81-103">Tek bir parametre geçerli yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="20d81-103">Defines a single parameter in the current method.</span></span> <span data-ttu-id="20d81-104">Parametre türü yöntemin imzası parametre konumlarını (sıralı) alınır.</span><span class="sxs-lookup"><span data-stu-id="20d81-104">The parameter type is taken from the parameter's position (sequence) within the method's signature.</span></span>  
  
 <span data-ttu-id="20d81-105">Parametreleri, verilen bir yöntem için meta verilerde tanımlanmışsa, bu yöntemi kullanarak bunları yeniden tanımlamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="20d81-105">If parameters are defined in the metadata for a given method, you do not have to define them again by using this method.</span></span> <span data-ttu-id="20d81-106">Sembol okuyucular parametreler için normal meta veriler sembol deposu denetlemeden önce denetlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="20d81-106">The symbol readers must check the normal metadata for the parameters before checking the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20d81-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="20d81-107">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="20d81-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="20d81-108">Parameters</span></span>  
 `name`  
 <span data-ttu-id="20d81-109">[in] Parametre adı.</span><span class="sxs-lookup"><span data-stu-id="20d81-109">[in] The parameter name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="20d81-110">[in] Parametre öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="20d81-110">[in] The parameter attributes.</span></span>  
  
 `sequence`  
 <span data-ttu-id="20d81-111">[in] Parametre imzası.</span><span class="sxs-lookup"><span data-stu-id="20d81-111">[in] The parameter signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="20d81-112">[in] Adres türü.</span><span class="sxs-lookup"><span data-stu-id="20d81-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="20d81-113">[in] Parametre belirtimini ilk adresi.</span><span class="sxs-lookup"><span data-stu-id="20d81-113">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="20d81-114">[in] Parametre belirtimini ikinci adresi.</span><span class="sxs-lookup"><span data-stu-id="20d81-114">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="20d81-115">[in] Parametre belirtimini üçüncü adresi.</span><span class="sxs-lookup"><span data-stu-id="20d81-115">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20d81-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="20d81-116">Return Value</span></span>  
 <span data-ttu-id="20d81-117">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="20d81-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20d81-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="20d81-118">Requirements</span></span>  
 <span data-ttu-id="20d81-119">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="20d81-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20d81-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="20d81-120">See Also</span></span>  
 [<span data-ttu-id="20d81-121">Isymunmanagedwriter arabirimi</span><span class="sxs-lookup"><span data-stu-id="20d81-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
