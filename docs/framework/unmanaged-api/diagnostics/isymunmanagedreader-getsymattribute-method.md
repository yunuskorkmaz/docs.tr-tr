---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagedreader:: GetSymAttribute yöntemi'
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
ms.openlocfilehash: cd1c453e9f2ef68799fc5eccf1288a7665c5cfdf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763975"
---
# <a name="isymunmanagedreadergetsymattribute-method"></a><span data-ttu-id="27889-103">ISymUnmanagedReader::GetSymAttribute Yöntemi</span><span class="sxs-lookup"><span data-stu-id="27889-103">ISymUnmanagedReader::GetSymAttribute Method</span></span>

<span data-ttu-id="27889-104">Özel bir özniteliği adına göre alır.</span><span class="sxs-lookup"><span data-stu-id="27889-104">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="27889-105">Meta veri özel özniteliklerinin aksine, bu özel öznitelikler sembol deposunda tutulur.</span><span class="sxs-lookup"><span data-stu-id="27889-105">Unlike metadata custom attributes, these custom attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27889-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="27889-106">Syntax</span></span>  
  
```cpp  
HRESULT GetSymAttribute (  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is (cBuffer),  
        length_is (*pcBuffer)] BYTE buffer[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27889-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="27889-107">Parameters</span></span>  

 `parent`  
 <span data-ttu-id="27889-108">'ndaki Özniteliği istenen nesnenin meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="27889-108">[in] The metadata token for the object for which the attribute is requested.</span></span>  
  
 `name`  
 <span data-ttu-id="27889-109">'ndaki Alınacak özniteliği belirten değişkene yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="27889-109">[in] A pointer to the variable that indicates the attribute to retrieve.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="27889-110">'ndaki `buffer` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="27889-110">[in] The size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="27889-111">dışı Öznitelik verilerinin uzunluğunu alan değişkene yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="27889-111">[out] A pointer to the variable that receives the length of the attribute data.</span></span>  
  
 `buffer`  
 <span data-ttu-id="27889-112">dışı Öznitelik verilerini alan değişkene yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="27889-112">[out] A pointer to the variable that receives the attribute data.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="27889-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="27889-113">Return Value</span></span>  

 <span data-ttu-id="27889-114">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="27889-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27889-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="27889-115">Requirements</span></span>  

 <span data-ttu-id="27889-116">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="27889-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27889-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27889-117">See also</span></span>

- [<span data-ttu-id="27889-118">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="27889-118">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
