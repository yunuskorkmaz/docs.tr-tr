---
title: ISymUnmanagedReader::GetSymAttribute Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetSymAttribute
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetSymAttribute
helpviewer_keywords:
- GetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedReader::GetSymAttribute method [.NET Framework debugging]
ms.assetid: c675ce7e-76e7-45ff-8273-3b6489a2767c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c9f22f23835f01022d5d62596b2cf63425759193
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426069"
---
# <a name="isymunmanagedreadergetsymattribute-method"></a><span data-ttu-id="68d53-102">ISymUnmanagedReader::GetSymAttribute Metodu</span><span class="sxs-lookup"><span data-stu-id="68d53-102">ISymUnmanagedReader::GetSymAttribute Method</span></span>
<span data-ttu-id="68d53-103">Adını dayalı özel bir öznitelik alır.</span><span class="sxs-lookup"><span data-stu-id="68d53-103">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="68d53-104">Meta veri özel öznitelikler, bu özel öznitelikler simgesi deposunda tutulur.</span><span class="sxs-lookup"><span data-stu-id="68d53-104">Unlike metadata custom attributes, these custom attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68d53-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="68d53-105">Syntax</span></span>  
  
```  
HRESULT GetSymAttribute (  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is (cBuffer),  
        length_is (*pcBuffer)] BYTE buffer[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="68d53-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="68d53-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="68d53-107">[in] Öznitelik istenen nesnesi için meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="68d53-107">[in] The metadata token for the object for which the attribute is requested.</span></span>  
  
 `name`  
 <span data-ttu-id="68d53-108">[in] Bir işaretçi değişkenine almak için özniteliğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="68d53-108">[in] A pointer to the variable that indicates the attribute to retrieve.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="68d53-109">[in] Boyutunu `buffer` dizi.</span><span class="sxs-lookup"><span data-stu-id="68d53-109">[in] The size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="68d53-110">[out] Öznitelik verilerini uzunluğunu alır değişkeni için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="68d53-110">[out] A pointer to the variable that receives the length of the attribute data.</span></span>  
  
 `buffer`  
 <span data-ttu-id="68d53-111">[out] Öznitelik verileri alan değişkeni için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="68d53-111">[out] A pointer to the variable that receives the attribute data.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="68d53-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="68d53-112">Return Value</span></span>  
 <span data-ttu-id="68d53-113">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu...</span><span class="sxs-lookup"><span data-stu-id="68d53-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code..</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68d53-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="68d53-114">Requirements</span></span>  
 <span data-ttu-id="68d53-115">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="68d53-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68d53-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="68d53-116">See Also</span></span>  
 [<span data-ttu-id="68d53-117">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="68d53-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
