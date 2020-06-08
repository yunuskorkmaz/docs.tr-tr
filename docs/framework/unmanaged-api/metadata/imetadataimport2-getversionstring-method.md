---
title: IMetaDataImport2::GetVersionString Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetVersionString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetVersionString
helpviewer_keywords:
- GetVersionString method, IMetaDataImport2 interface [.NET Framework metadata]
- IMetaDataImport2::GetVersionString method [.NET Framework metadata]
ms.assetid: 308183ee-fd44-4432-9d86-ef00d181b49b
topic_type:
- apiref
ms.openlocfilehash: 84cf5ac9eab5749d3bdc63670fe5c31bfb62abcd
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490413"
---
# <a name="imetadataimport2getversionstring-method"></a><span data-ttu-id="e17fc-102">IMetaDataImport2::GetVersionString Metodu</span><span class="sxs-lookup"><span data-stu-id="e17fc-102">IMetaDataImport2::GetVersionString Method</span></span>
<span data-ttu-id="e17fc-103">Derlemeyi oluşturmak için kullanılan çalışma zamanının sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="e17fc-103">Gets the version number of the runtime that was used to build the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e17fc-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e17fc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e17fc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e17fc-105">Parameters</span></span>  
 `pwzBuf`  
 <span data-ttu-id="e17fc-106">dışı Sürümü belirten dizeyi depolayan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="e17fc-106">[out] An array to store the string that specifies the version.</span></span>  
  
 `ccBufSize`  
 <span data-ttu-id="e17fc-107">'ndaki Dizinin geniş karakterdeki boyutu `pwzBuf` .</span><span class="sxs-lookup"><span data-stu-id="e17fc-107">[in] The size, in wide characters, of the `pwzBuf` array.</span></span>  
  
 `pccBufSize`  
 <span data-ttu-id="e17fc-108">dışı Dizide döndürülen bir null Sonlandırıcı dahil olmak üzere geniş karakter sayısı `pwzBuf` .</span><span class="sxs-lookup"><span data-stu-id="e17fc-108">[out] The number of wide characters, including a null terminator, returned in the `pwzBuf` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e17fc-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e17fc-109">Remarks</span></span>  
 <span data-ttu-id="e17fc-110">`GetVersionString`Yöntemi, geçerli meta veri kapsamının yerleşik sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="e17fc-110">The `GetVersionString` method gets the built-for version of the current metadata scope.</span></span> <span data-ttu-id="e17fc-111">Kapsam hiç kaydedilmediğinde, yerleşik bir sürüme sahip olmaz ve boş bir dize döndürülür.</span><span class="sxs-lookup"><span data-stu-id="e17fc-111">If the scope has never been saved, it will not have a built-for version, and an empty string will be returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e17fc-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e17fc-112">Requirements</span></span>  
 <span data-ttu-id="e17fc-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e17fc-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e17fc-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e17fc-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e17fc-115">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="e17fc-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e17fc-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e17fc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e17fc-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e17fc-117">See also</span></span>

- [<span data-ttu-id="e17fc-118">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e17fc-118">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="e17fc-119">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e17fc-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
