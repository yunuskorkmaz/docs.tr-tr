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
ms.openlocfilehash: aa3b742babe4a94a43e4e6168dea67c0a0245eb0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720587"
---
# <a name="isymunmanagedreadergetsymattribute-method"></a><span data-ttu-id="8ddd7-102">ISymUnmanagedReader::GetSymAttribute Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8ddd7-102">ISymUnmanagedReader::GetSymAttribute Method</span></span>

<span data-ttu-id="8ddd7-103">Özel bir özniteliği adına göre alır.</span><span class="sxs-lookup"><span data-stu-id="8ddd7-103">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="8ddd7-104">Meta veri özel özniteliklerinin aksine, bu özel öznitelikler sembol deposunda tutulur.</span><span class="sxs-lookup"><span data-stu-id="8ddd7-104">Unlike metadata custom attributes, these custom attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ddd7-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="8ddd7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSymAttribute (  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is (cBuffer),  
        length_is (*pcBuffer)] BYTE buffer[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ddd7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8ddd7-106">Parameters</span></span>  

 `parent`  
 <span data-ttu-id="8ddd7-107">'ndaki Özniteliği istenen nesnenin meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="8ddd7-107">[in] The metadata token for the object for which the attribute is requested.</span></span>  
  
 `name`  
 <span data-ttu-id="8ddd7-108">'ndaki Alınacak özniteliği belirten değişkene yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8ddd7-108">[in] A pointer to the variable that indicates the attribute to retrieve.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="8ddd7-109">'ndaki `buffer` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="8ddd7-109">[in] The size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="8ddd7-110">dışı Öznitelik verilerinin uzunluğunu alan değişkene yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8ddd7-110">[out] A pointer to the variable that receives the length of the attribute data.</span></span>  
  
 `buffer`  
 <span data-ttu-id="8ddd7-111">dışı Öznitelik verilerini alan değişkene yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8ddd7-111">[out] A pointer to the variable that receives the attribute data.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8ddd7-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8ddd7-112">Return Value</span></span>  

 <span data-ttu-id="8ddd7-113">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="8ddd7-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ddd7-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8ddd7-114">Requirements</span></span>  

 <span data-ttu-id="8ddd7-115">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="8ddd7-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ddd7-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ddd7-116">See also</span></span>

- [<span data-ttu-id="8ddd7-117">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8ddd7-117">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
