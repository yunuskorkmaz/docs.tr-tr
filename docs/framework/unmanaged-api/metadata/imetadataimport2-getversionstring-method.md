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
ms.openlocfilehash: 3e62b1177c0161883ad03086723cc43b71292df5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702569"
---
# <a name="imetadataimport2getversionstring-method"></a><span data-ttu-id="ac3ac-102">IMetaDataImport2::GetVersionString Metodu</span><span class="sxs-lookup"><span data-stu-id="ac3ac-102">IMetaDataImport2::GetVersionString Method</span></span>

<span data-ttu-id="ac3ac-103">Derlemeyi oluşturmak için kullanılan çalışma zamanının sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="ac3ac-103">Gets the version number of the runtime that was used to build the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac3ac-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ac3ac-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac3ac-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ac3ac-105">Parameters</span></span>  

 `pwzBuf`  
 <span data-ttu-id="ac3ac-106">dışı Sürümü belirten dizeyi depolayan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="ac3ac-106">[out] An array to store the string that specifies the version.</span></span>  
  
 `ccBufSize`  
 <span data-ttu-id="ac3ac-107">'ndaki Dizinin geniş karakterdeki boyutu `pwzBuf` .</span><span class="sxs-lookup"><span data-stu-id="ac3ac-107">[in] The size, in wide characters, of the `pwzBuf` array.</span></span>  
  
 `pccBufSize`  
 <span data-ttu-id="ac3ac-108">dışı Dizide döndürülen bir null Sonlandırıcı dahil olmak üzere geniş karakter sayısı `pwzBuf` .</span><span class="sxs-lookup"><span data-stu-id="ac3ac-108">[out] The number of wide characters, including a null terminator, returned in the `pwzBuf` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac3ac-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ac3ac-109">Remarks</span></span>  

 <span data-ttu-id="ac3ac-110">`GetVersionString`Yöntemi, geçerli meta veri kapsamının yerleşik sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="ac3ac-110">The `GetVersionString` method gets the built-for version of the current metadata scope.</span></span> <span data-ttu-id="ac3ac-111">Kapsam hiç kaydedilmediğinde, yerleşik bir sürüme sahip olmaz ve boş bir dize döndürülür.</span><span class="sxs-lookup"><span data-stu-id="ac3ac-111">If the scope has never been saved, it will not have a built-for version, and an empty string will be returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac3ac-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ac3ac-112">Requirements</span></span>  

 <span data-ttu-id="ac3ac-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac3ac-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac3ac-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ac3ac-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ac3ac-115">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="ac3ac-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ac3ac-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac3ac-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac3ac-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac3ac-117">See also</span></span>

- [<span data-ttu-id="ac3ac-118">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac3ac-118">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="ac3ac-119">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac3ac-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
