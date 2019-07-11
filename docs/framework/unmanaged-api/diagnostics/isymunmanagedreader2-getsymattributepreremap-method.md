---
title: ISymUnmanagedReader2::GetSymAttributePreRemap Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetSymAttributePreRemap
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetSymAttributePreRemap
helpviewer_keywords:
- GetSymAttributePreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetSymAttributePreRemap method [.NET Framework debugging]
ms.assetid: 7580d546-a709-40c5-ad02-aa70d774fd0b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 46c608a644619c28709de135d7c062175b012d80
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777385"
---
# <a name="isymunmanagedreader2getsymattributepreremap-method"></a><span data-ttu-id="31718-102">ISymUnmanagedReader2::GetSymAttributePreRemap Metodu</span><span class="sxs-lookup"><span data-stu-id="31718-102">ISymUnmanagedReader2::GetSymAttributePreRemap Method</span></span>
<span data-ttu-id="31718-103">Özel bir öznitelik adı üzerinde temel alır.</span><span class="sxs-lookup"><span data-stu-id="31718-103">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="31718-104">Meta veri özel öznitelikleri farklı olarak bu öznitelikler sembol deposundaki tutulur.</span><span class="sxs-lookup"><span data-stu-id="31718-104">Unlike metadata custom attributes, these attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31718-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="31718-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSymAttributePreRemap(  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is(cBuffer),  
        length_is(*pcBuffer)] BYTE buffer[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31718-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="31718-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="31718-107">[in] Ana meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="31718-107">[in] The metadata token of the parent.</span></span>  
  
 `name`  
 <span data-ttu-id="31718-108">[in] Bir işaretçi bir `WCHAR` , adı içeriyor.</span><span class="sxs-lookup"><span data-stu-id="31718-108">[in] A pointer to a `WCHAR` that contains the name.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="31718-109">[in] A `ULONG32` boyutunu gösteren `buffer` dizisi.</span><span class="sxs-lookup"><span data-stu-id="31718-109">[in] A `ULONG32` that indicates the size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="31718-110">[out] Bir işaretçi bir `ULONG32` içeren öznitelik bayt için gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="31718-110">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the attribute bytes.</span></span>  
  
 `buffer`  
 <span data-ttu-id="31718-111">[out] Öznitelik bayt alan arabellek için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="31718-111">[out] A pointer to the buffer that receives the attribute bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="31718-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="31718-112">Return Value</span></span>  
 <span data-ttu-id="31718-113">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="31718-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31718-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="31718-114">Requirements</span></span>  
 <span data-ttu-id="31718-115">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="31718-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31718-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31718-116">See also</span></span>

- [<span data-ttu-id="31718-117">ISymUnmanagedReader2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="31718-117">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
