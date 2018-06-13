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
ms.openlocfilehash: 326f970f53293b74bbf8c5e77830f3f6ce1b73ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427043"
---
# <a name="isymunmanagedreader2getsymattributepreremap-method"></a><span data-ttu-id="810c0-102">ISymUnmanagedReader2::GetSymAttributePreRemap Metodu</span><span class="sxs-lookup"><span data-stu-id="810c0-102">ISymUnmanagedReader2::GetSymAttributePreRemap Method</span></span>
<span data-ttu-id="810c0-103">Adını dayalı özel bir öznitelik alır.</span><span class="sxs-lookup"><span data-stu-id="810c0-103">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="810c0-104">Meta veri özel öznitelikler farklı olarak bu öznitelikler simgesi deposunda tutulur.</span><span class="sxs-lookup"><span data-stu-id="810c0-104">Unlike metadata custom attributes, these attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="810c0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="810c0-105">Syntax</span></span>  
  
```  
HRESULT GetSymAttributePreRemap(  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is(cBuffer),  
        length_is(*pcBuffer)] BYTE buffer[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="810c0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="810c0-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="810c0-107">[in] Üst meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="810c0-107">[in] The metadata token of the parent.</span></span>  
  
 `name`  
 <span data-ttu-id="810c0-108">[in] Bir işaretçi bir `WCHAR` adı içeriyor.</span><span class="sxs-lookup"><span data-stu-id="810c0-108">[in] A pointer to a `WCHAR` that contains the name.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="810c0-109">[in] A `ULONG32` boyutunu gösterir `buffer` dizi.</span><span class="sxs-lookup"><span data-stu-id="810c0-109">[in] A `ULONG32` that indicates the size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="810c0-110">[out] Bir işaretçi bir `ULONG32` özniteliği bayt içermesi gerekir arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="810c0-110">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the attribute bytes.</span></span>  
  
 `buffer`  
 <span data-ttu-id="810c0-111">[out] Öznitelik bayt alır arabellek için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="810c0-111">[out] A pointer to the buffer that receives the attribute bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="810c0-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="810c0-112">Return Value</span></span>  
 <span data-ttu-id="810c0-113">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="810c0-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="810c0-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="810c0-114">Requirements</span></span>  
 <span data-ttu-id="810c0-115">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="810c0-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="810c0-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="810c0-116">See Also</span></span>  
 [<span data-ttu-id="810c0-117">ISymUnmanagedReader2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="810c0-117">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
