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
ms.openlocfilehash: cea8a322fab6ef76873e668c622ac63e3a3f2862
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428231"
---
# <a name="isymunmanagedbinder2getreaderforfile2-method"></a><span data-ttu-id="b5405-102">ISymUnmanagedBinder2::GetReaderForFile2 Metodu</span><span class="sxs-lookup"><span data-stu-id="b5405-102">ISymUnmanagedBinder2::GetReaderForFile2 Method</span></span>
<span data-ttu-id="b5405-103">Bir meta veri arabirimi ve bir dosya adı doğru döndürür <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> modülü ile ilişkili hata ayıklama simgeleri okuma yapacak arabirimi.</span><span class="sxs-lookup"><span data-stu-id="b5405-103">Given a metadata interface and a file name, returns the correct <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interface that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="b5405-104">Bu yöntem program veritabanı (PDB) dosyası için daha kapsamlı bir arama sağlar [Isymunmanagedbinder::getreaderforfile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b5405-104">This method provides a more extensive search for the program database (PDB) file than the [ISymUnmanagedBinder::GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5405-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b5405-105">Syntax</span></span>  
  
```  
HRESULT GetReaderForFile2(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b5405-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b5405-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="b5405-107">[in] Meta veri alma arayüzü için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b5405-107">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="b5405-108">[in] Dosya adı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b5405-108">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="b5405-109">[in] Arama yolu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b5405-109">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="b5405-110">[in] Değerini [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) bir simge Okuyucu için arama yaparken kullanılacak ilkeyi belirtir numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="b5405-110">[in] A value of the [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="b5405-111">[out] Ayarlanmış bir işaretçi döndürülen için <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="b5405-111">[out] A pointer that is set to the returned <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b5405-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b5405-112">Return Value</span></span>  
 <span data-ttu-id="b5405-113">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="b5405-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5405-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b5405-114">Requirements</span></span>  
 <span data-ttu-id="b5405-115">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b5405-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5405-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b5405-116">Remarks</span></span>  
 <span data-ttu-id="b5405-117">Bu yöntemin sürümü modülü yanındaki sağ dışındaki alanlarda PDB dosyası arayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5405-117">This version of the method can search for the PDB file in areas other than right next to the module.</span></span> <span data-ttu-id="b5405-118">Arama İlkesi birleştirerek denetlenebilir [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="b5405-118">The search policy can be controlled by combining [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md).</span></span> <span data-ttu-id="b5405-119">Örneğin, `AllowReferencePathAccess | AllowSymbolServerAccess` yürütülebilir dosyanın yanındaki ve bir simge sunucuda PDB arar ancak kayıt defterini sorgulayın veya yürütülebilir dosyanın yolunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="b5405-119">For example, `AllowReferencePathAccess | AllowSymbolServerAccess` looks for the PDB next to the executable file and on a symbol server, but does not query the registry or use the path in the executable file.</span></span> <span data-ttu-id="b5405-120">Varsa `searchPath` parametresi sağlanır, bu dizinlerin her zaman aranır.</span><span class="sxs-lookup"><span data-stu-id="b5405-120">If the `searchPath` parameter is provided, those directories will always be searched.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5405-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b5405-121">See Also</span></span>  
 [<span data-ttu-id="b5405-122">ISymUnmanagedBinder2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b5405-122">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 [<span data-ttu-id="b5405-123">GetReaderForFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b5405-123">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)
