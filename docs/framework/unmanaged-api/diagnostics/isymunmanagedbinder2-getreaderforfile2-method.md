---
description: 'Daha fazla bilgi edinin: ISymUnmanagedBinder2:: GetReaderForFile2 yöntemi'
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
ms.openlocfilehash: c1a180ceec07c3087150613365acfce646adc34e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689943"
---
# <a name="isymunmanagedbinder2getreaderforfile2-method"></a><span data-ttu-id="72bfd-103">ISymUnmanagedBinder2::GetReaderForFile2 Metodu</span><span class="sxs-lookup"><span data-stu-id="72bfd-103">ISymUnmanagedBinder2::GetReaderForFile2 Method</span></span>

<span data-ttu-id="72bfd-104">Meta veri arabirimi ve dosya adı verildiğinde, modülle ilişkili hata ayıklama sembollerini okuyacak doğru [ıdimunmanagedreader](isymunmanagedreader-interface.md) arabirimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="72bfd-104">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="72bfd-105">Bu yöntem, program veritabanı (PDB) dosyası için [ıstreamunmanagedciltçi:: GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md) yönteminden daha kapsamlı bir arama sağlar.</span><span class="sxs-lookup"><span data-stu-id="72bfd-105">This method provides a more extensive search for the program database (PDB) file than the [ISymUnmanagedBinder::GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72bfd-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="72bfd-106">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderForFile2(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72bfd-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="72bfd-107">Parameters</span></span>  

 `importer`  
 <span data-ttu-id="72bfd-108">'ndaki Meta veri içeri aktarma arabirimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="72bfd-108">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="72bfd-109">'ndaki Dosya adı işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="72bfd-109">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="72bfd-110">'ndaki Arama yoluna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="72bfd-110">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="72bfd-111">'ndaki Bir sembol okuyucu ararken kullanılacak ilkeyi belirten [CorSymSearchPolicyAttributes](corsymsearchpolicyattributes-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="72bfd-111">[in] A value of the [CorSymSearchPolicyAttributes](corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="72bfd-112">dışı Döndürülen [ıdimunmanagedreader](isymunmanagedreader-interface.md) arabirimine ayarlanmış bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="72bfd-112">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="72bfd-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="72bfd-113">Return Value</span></span>  

 <span data-ttu-id="72bfd-114">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="72bfd-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72bfd-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="72bfd-115">Requirements</span></span>  

 <span data-ttu-id="72bfd-116">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="72bfd-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72bfd-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="72bfd-117">Remarks</span></span>  

 <span data-ttu-id="72bfd-118">Yönteminin bu sürümü, modülün hemen yanında bulunan bölümlerde PDB dosyasını arayabilir.</span><span class="sxs-lookup"><span data-stu-id="72bfd-118">This version of the method can search for the PDB file in areas other than right next to the module.</span></span> <span data-ttu-id="72bfd-119">Arama İlkesi [CorSymSearchPolicyAttributes](corsymsearchpolicyattributes-enumeration.md)birleştirilerek denetlenebilir.</span><span class="sxs-lookup"><span data-stu-id="72bfd-119">The search policy can be controlled by combining [CorSymSearchPolicyAttributes](corsymsearchpolicyattributes-enumeration.md).</span></span> <span data-ttu-id="72bfd-120">Örneğin, `AllowReferencePathAccess | AllowSymbolServerAccess` yürütülebilir dosyanın yanında ve bir sembol sunucusunda pdb 'yi arar, ancak kayıt defterini sorgulamaz veya yürütülebilir dosyadaki yolu kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="72bfd-120">For example, `AllowReferencePathAccess | AllowSymbolServerAccess` looks for the PDB next to the executable file and on a symbol server, but does not query the registry or use the path in the executable file.</span></span> <span data-ttu-id="72bfd-121">`searchPath`Parametresi sağlanmışsa, bu dizinler her zaman aranır.</span><span class="sxs-lookup"><span data-stu-id="72bfd-121">If the `searchPath` parameter is provided, those directories will always be searched.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72bfd-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72bfd-122">See also</span></span>

- [<span data-ttu-id="72bfd-123">ISymUnmanagedBinder2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="72bfd-123">ISymUnmanagedBinder2 Interface</span></span>](isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="72bfd-124">GetReaderForFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="72bfd-124">GetReaderForFile Method</span></span>](isymunmanagedbinder-getreaderforfile-method.md)
