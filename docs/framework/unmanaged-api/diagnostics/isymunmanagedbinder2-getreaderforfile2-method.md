---
title: ISymUnmanagedBinder2::GetReaderForFile2 Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder2.GetReaderForFile2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2
helpviewer_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2 method [.NET Framework debugging]
- GetReaderForFile2 method [.NET Framework debugging]
ms.assetid: dd92dcaf-403c-464d-a254-21594985dddd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fed289b2776e8ac4a12969060cd16c6163ebed2f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091973"
---
# <a name="isymunmanagedbinder2getreaderforfile2-method"></a><span data-ttu-id="4cf2a-102">ISymUnmanagedBinder2::GetReaderForFile2 Metodu</span><span class="sxs-lookup"><span data-stu-id="4cf2a-102">ISymUnmanagedBinder2::GetReaderForFile2 Method</span></span>
<span data-ttu-id="4cf2a-103">Meta veri arayüzü ve bir dosya adı, doğru döndürür [Isymunmanagedreader](isymunmanagedreader-interface.md) modülle ilişkili hata ayıklama sembolleri okuyacaksa arabirimi.</span><span class="sxs-lookup"><span data-stu-id="4cf2a-103">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="4cf2a-104">Bu yöntem program veritabanı (PDB) dosyası için daha kapsamlı bir arama sağlar [Isymunmanagedbinder::getreaderforfile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4cf2a-104">This method provides a more extensive search for the program database (PDB) file than the [ISymUnmanagedBinder::GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cf2a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4cf2a-105">Syntax</span></span>  
  
```  
HRESULT GetReaderForFile2(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4cf2a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4cf2a-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="4cf2a-107">[in] Meta veri alma arayüzü işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="4cf2a-107">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="4cf2a-108">[in] Dosya adı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4cf2a-108">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="4cf2a-109">[in] Arama yolu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4cf2a-109">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="4cf2a-110">[in] Değerini [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) sembol Okuyucu için arama yaparken kullanılacak ilkeyi belirten sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="4cf2a-110">[in] A value of the [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="4cf2a-111">[out] Ayarlanmış bir işaretçi ve döndürülen [Isymunmanagedreader](isymunmanagedreader-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="4cf2a-111">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4cf2a-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4cf2a-112">Return Value</span></span>  
 <span data-ttu-id="4cf2a-113">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="4cf2a-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4cf2a-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4cf2a-114">Requirements</span></span>  
 <span data-ttu-id="4cf2a-115">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4cf2a-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4cf2a-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4cf2a-116">Remarks</span></span>  
 <span data-ttu-id="4cf2a-117">Yöntemi bu sürümü, modül yanındaki sağ dışındaki alanlarda PDB dosyası için arama yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4cf2a-117">This version of the method can search for the PDB file in areas other than right next to the module.</span></span> <span data-ttu-id="4cf2a-118">Arama ilke birleştirerek denetlenebilir [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="4cf2a-118">The search policy can be controlled by combining [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md).</span></span> <span data-ttu-id="4cf2a-119">Örneğin, `AllowReferencePathAccess | AllowSymbolServerAccess` pdb yürütülebilir dosyanın yanındaki ve bir sembol sunucusu üzerinde görünür ancak kayıt defterini sorgulayın veya yürütülebilir dosyanın yolunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="4cf2a-119">For example, `AllowReferencePathAccess | AllowSymbolServerAccess` looks for the PDB next to the executable file and on a symbol server, but does not query the registry or use the path in the executable file.</span></span> <span data-ttu-id="4cf2a-120">Varsa `searchPath` parametresi sağlanır, bu dizinlerin her zaman aranır.</span><span class="sxs-lookup"><span data-stu-id="4cf2a-120">If the `searchPath` parameter is provided, those directories will always be searched.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cf2a-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4cf2a-121">See also</span></span>

- [<span data-ttu-id="4cf2a-122">ISymUnmanagedBinder2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4cf2a-122">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="4cf2a-123">GetReaderForFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4cf2a-123">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)
