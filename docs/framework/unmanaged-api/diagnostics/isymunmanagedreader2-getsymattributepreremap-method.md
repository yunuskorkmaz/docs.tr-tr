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
ms.openlocfilehash: 4009f8988c90ed090c0cc3d86164af347055722f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446427"
---
# <a name="isymunmanagedreader2getsymattributepreremap-method"></a><span data-ttu-id="a65df-102">ISymUnmanagedReader2::GetSymAttributePreRemap Metodu</span><span class="sxs-lookup"><span data-stu-id="a65df-102">ISymUnmanagedReader2::GetSymAttributePreRemap Method</span></span>
<span data-ttu-id="a65df-103">Özel bir özniteliği adına göre alır.</span><span class="sxs-lookup"><span data-stu-id="a65df-103">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="a65df-104">Meta veri özel özniteliklerinin aksine, bu öznitelikler sembol deposunda tutulur.</span><span class="sxs-lookup"><span data-stu-id="a65df-104">Unlike metadata custom attributes, these attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a65df-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a65df-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSymAttributePreRemap(  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is(cBuffer),  
        length_is(*pcBuffer)] BYTE buffer[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a65df-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a65df-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="a65df-107">'ndaki Üst öğenin meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="a65df-107">[in] The metadata token of the parent.</span></span>  
  
 `name`  
 <span data-ttu-id="a65df-108">'ndaki Adı içeren `WCHAR` işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a65df-108">[in] A pointer to a `WCHAR` that contains the name.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="a65df-109">'ndaki `buffer` dizisinin boyutunu belirten `ULONG32`.</span><span class="sxs-lookup"><span data-stu-id="a65df-109">[in] A `ULONG32` that indicates the size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="a65df-110">dışı Öznitelik baytlarını içermesi için gereken arabelleğin boyutunu alan bir `ULONG32` işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a65df-110">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the attribute bytes.</span></span>  
  
 `buffer`  
 <span data-ttu-id="a65df-111">dışı Öznitelik baytlarını alan arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a65df-111">[out] A pointer to the buffer that receives the attribute bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a65df-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a65df-112">Return Value</span></span>  
 <span data-ttu-id="a65df-113">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="a65df-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a65df-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a65df-114">Requirements</span></span>  
 <span data-ttu-id="a65df-115">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="a65df-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a65df-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a65df-116">See also</span></span>

- [<span data-ttu-id="a65df-117">ISymUnmanagedReader2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a65df-117">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
