---
title: ISymUnmanagedWriter::DefineParameter Yöntemi
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d5b82415635980f5bd4e13e87a0a03ec5b7032bb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777330"
---
# <a name="isymunmanagedwriterdefineparameter-method"></a><span data-ttu-id="c34d2-102">ISymUnmanagedWriter::DefineParameter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c34d2-102">ISymUnmanagedWriter::DefineParameter Method</span></span>
<span data-ttu-id="c34d2-103">Tek bir parametre, geçerli yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c34d2-103">Defines a single parameter in the current method.</span></span> <span data-ttu-id="c34d2-104">Parametre türü yöntemin imzasını içinde parametrenin konumu (sıra) alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="c34d2-104">The parameter type is taken from the parameter's position (sequence) within the method's signature.</span></span>  
  
 <span data-ttu-id="c34d2-105">Parametreler için belirli bir yöntemin meta verilerindeki tanımlanmışsa, bu yöntemi kullanarak bunları yeniden tanımlamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="c34d2-105">If parameters are defined in the metadata for a given method, you do not have to define them again by using this method.</span></span> <span data-ttu-id="c34d2-106">Sembol okuyucu parametreleri için normal meta veriler, sembol deposuna iade etmeden önce işaretlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c34d2-106">The symbol readers must check the normal metadata for the parameters before checking the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c34d2-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c34d2-107">Syntax</span></span>  
  
```cpp  
HRESULT DefineParameter(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      sequence,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c34d2-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c34d2-108">Parameters</span></span>  
 `name`  
 <span data-ttu-id="c34d2-109">[in] Parametre adı.</span><span class="sxs-lookup"><span data-stu-id="c34d2-109">[in] The parameter name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="c34d2-110">[in] Parametre öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="c34d2-110">[in] The parameter attributes.</span></span>  
  
 `sequence`  
 <span data-ttu-id="c34d2-111">[in] Parametre imzası.</span><span class="sxs-lookup"><span data-stu-id="c34d2-111">[in] The parameter signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="c34d2-112">[in] Adres türü.</span><span class="sxs-lookup"><span data-stu-id="c34d2-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="c34d2-113">[in] Parametre belirtimine ilk adresi.</span><span class="sxs-lookup"><span data-stu-id="c34d2-113">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="c34d2-114">[in] Parametre belirtimine ikinci adresi.</span><span class="sxs-lookup"><span data-stu-id="c34d2-114">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="c34d2-115">[in] Parametre belirtimine üçüncü adresi.</span><span class="sxs-lookup"><span data-stu-id="c34d2-115">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c34d2-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c34d2-116">Return Value</span></span>  
 <span data-ttu-id="c34d2-117">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="c34d2-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c34d2-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c34d2-118">Requirements</span></span>  
 <span data-ttu-id="c34d2-119">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c34d2-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c34d2-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c34d2-120">See also</span></span>

- [<span data-ttu-id="c34d2-121">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c34d2-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
