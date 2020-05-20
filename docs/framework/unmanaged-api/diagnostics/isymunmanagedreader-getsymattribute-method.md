---
title: ISymUnmanagedReader::GetSymAttribute Yöntemi
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
ms.openlocfilehash: b7e2814e56765037b69c6ef7ca0ba610dd7d3c95
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614935"
---
# <a name="isymunmanagedreadergetsymattribute-method"></a><span data-ttu-id="dfaca-102">ISymUnmanagedReader::GetSymAttribute Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dfaca-102">ISymUnmanagedReader::GetSymAttribute Method</span></span>
<span data-ttu-id="dfaca-103">Özel bir özniteliği adına göre alır.</span><span class="sxs-lookup"><span data-stu-id="dfaca-103">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="dfaca-104">Meta veri özel özniteliklerinin aksine, bu özel öznitelikler sembol deposunda tutulur.</span><span class="sxs-lookup"><span data-stu-id="dfaca-104">Unlike metadata custom attributes, these custom attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfaca-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="dfaca-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSymAttribute (  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is (cBuffer),  
        length_is (*pcBuffer)] BYTE buffer[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dfaca-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dfaca-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="dfaca-107">'ndaki Özniteliği istenen nesnenin meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="dfaca-107">[in] The metadata token for the object for which the attribute is requested.</span></span>  
  
 `name`  
 <span data-ttu-id="dfaca-108">'ndaki Alınacak özniteliği belirten değişkene yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dfaca-108">[in] A pointer to the variable that indicates the attribute to retrieve.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="dfaca-109">'ndaki `buffer`Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="dfaca-109">[in] The size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="dfaca-110">dışı Öznitelik verilerinin uzunluğunu alan değişkene yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dfaca-110">[out] A pointer to the variable that receives the length of the attribute data.</span></span>  
  
 `buffer`  
 <span data-ttu-id="dfaca-111">dışı Öznitelik verilerini alan değişkene yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dfaca-111">[out] A pointer to the variable that receives the attribute data.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dfaca-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="dfaca-112">Return Value</span></span>  
 <span data-ttu-id="dfaca-113">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="dfaca-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfaca-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dfaca-114">Requirements</span></span>  
 <span data-ttu-id="dfaca-115">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="dfaca-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfaca-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dfaca-116">See also</span></span>

- [<span data-ttu-id="dfaca-117">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dfaca-117">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
