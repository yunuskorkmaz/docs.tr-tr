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
ms.openlocfilehash: 7f04b5c100f1fd9c44e671b883fe469b16d33fa6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440144"
---
# <a name="isymunmanagedreadergetsymattribute-method"></a><span data-ttu-id="bc7b9-102">ISymUnmanagedReader::GetSymAttribute Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bc7b9-102">ISymUnmanagedReader::GetSymAttribute Method</span></span>
<span data-ttu-id="bc7b9-103">Özel bir özniteliği adına göre alır.</span><span class="sxs-lookup"><span data-stu-id="bc7b9-103">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="bc7b9-104">Meta veri özel özniteliklerinin aksine, bu özel öznitelikler sembol deposunda tutulur.</span><span class="sxs-lookup"><span data-stu-id="bc7b9-104">Unlike metadata custom attributes, these custom attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc7b9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bc7b9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSymAttribute (  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is (cBuffer),  
        length_is (*pcBuffer)] BYTE buffer[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc7b9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bc7b9-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="bc7b9-107">'ndaki Özniteliği istenen nesnenin meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="bc7b9-107">[in] The metadata token for the object for which the attribute is requested.</span></span>  
  
 `name`  
 <span data-ttu-id="bc7b9-108">'ndaki Alınacak özniteliği belirten değişkene yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bc7b9-108">[in] A pointer to the variable that indicates the attribute to retrieve.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="bc7b9-109">'ndaki `buffer` dizisinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="bc7b9-109">[in] The size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="bc7b9-110">dışı Öznitelik verilerinin uzunluğunu alan değişkene yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bc7b9-110">[out] A pointer to the variable that receives the length of the attribute data.</span></span>  
  
 `buffer`  
 <span data-ttu-id="bc7b9-111">dışı Öznitelik verilerini alan değişkene yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bc7b9-111">[out] A pointer to the variable that receives the attribute data.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bc7b9-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bc7b9-112">Return Value</span></span>  
 <span data-ttu-id="bc7b9-113">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="bc7b9-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc7b9-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bc7b9-114">Requirements</span></span>  
 <span data-ttu-id="bc7b9-115">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="bc7b9-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc7b9-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc7b9-116">See also</span></span>

- [<span data-ttu-id="bc7b9-117">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc7b9-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
