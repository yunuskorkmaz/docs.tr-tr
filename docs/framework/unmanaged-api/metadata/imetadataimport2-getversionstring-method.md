---
description: ': IMetaDataImport2:: GetVersionString metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 6f7e296607dc3167936c69d52a8baae4f5555b88
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688565"
---
# <a name="imetadataimport2getversionstring-method"></a><span data-ttu-id="8ecad-103">IMetaDataImport2::GetVersionString Metodu</span><span class="sxs-lookup"><span data-stu-id="8ecad-103">IMetaDataImport2::GetVersionString Method</span></span>

<span data-ttu-id="8ecad-104">Derlemeyi oluşturmak için kullanılan çalışma zamanının sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="8ecad-104">Gets the version number of the runtime that was used to build the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ecad-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8ecad-105">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ecad-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8ecad-106">Parameters</span></span>  

 `pwzBuf`  
 <span data-ttu-id="8ecad-107">dışı Sürümü belirten dizeyi depolayan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="8ecad-107">[out] An array to store the string that specifies the version.</span></span>  
  
 `ccBufSize`  
 <span data-ttu-id="8ecad-108">'ndaki Dizinin geniş karakterdeki boyutu `pwzBuf` .</span><span class="sxs-lookup"><span data-stu-id="8ecad-108">[in] The size, in wide characters, of the `pwzBuf` array.</span></span>  
  
 `pccBufSize`  
 <span data-ttu-id="8ecad-109">dışı Dizide döndürülen bir null Sonlandırıcı dahil olmak üzere geniş karakter sayısı `pwzBuf` .</span><span class="sxs-lookup"><span data-stu-id="8ecad-109">[out] The number of wide characters, including a null terminator, returned in the `pwzBuf` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ecad-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8ecad-110">Remarks</span></span>  

 <span data-ttu-id="8ecad-111">`GetVersionString`Yöntemi, geçerli meta veri kapsamının yerleşik sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="8ecad-111">The `GetVersionString` method gets the built-for version of the current metadata scope.</span></span> <span data-ttu-id="8ecad-112">Kapsam hiç kaydedilmediğinde, yerleşik bir sürüme sahip olmaz ve boş bir dize döndürülür.</span><span class="sxs-lookup"><span data-stu-id="8ecad-112">If the scope has never been saved, it will not have a built-for version, and an empty string will be returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ecad-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8ecad-113">Requirements</span></span>  

 <span data-ttu-id="8ecad-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ecad-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ecad-115">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8ecad-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8ecad-116">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="8ecad-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8ecad-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ecad-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ecad-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ecad-118">See also</span></span>

- [<span data-ttu-id="8ecad-119">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8ecad-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="8ecad-120">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8ecad-120">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
