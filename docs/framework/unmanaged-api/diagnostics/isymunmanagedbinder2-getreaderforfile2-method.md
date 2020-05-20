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
ms.openlocfilehash: 97b9fa537fdd9147d6d9eda036013add5393e33c
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441714"
---
# <a name="isymunmanagedbinder2getreaderforfile2-method"></a><span data-ttu-id="f69e1-102">ISymUnmanagedBinder2::GetReaderForFile2 Metodu</span><span class="sxs-lookup"><span data-stu-id="f69e1-102">ISymUnmanagedBinder2::GetReaderForFile2 Method</span></span>
<span data-ttu-id="f69e1-103">Meta veri arabirimi ve dosya adı verildiğinde, modülle ilişkili hata ayıklama sembollerini okuyacak doğru [ıdimunmanagedreader](isymunmanagedreader-interface.md) arabirimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="f69e1-103">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="f69e1-104">Bu yöntem, program veritabanı (PDB) dosyası için [ıstreamunmanagedciltçi:: GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md) yönteminden daha kapsamlı bir arama sağlar.</span><span class="sxs-lookup"><span data-stu-id="f69e1-104">This method provides a more extensive search for the program database (PDB) file than the [ISymUnmanagedBinder::GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f69e1-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f69e1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderForFile2(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f69e1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f69e1-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="f69e1-107">'ndaki Meta veri içeri aktarma arabirimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f69e1-107">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="f69e1-108">'ndaki Dosya adı işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="f69e1-108">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="f69e1-109">'ndaki Arama yoluna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f69e1-109">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="f69e1-110">'ndaki Bir sembol okuyucu ararken kullanılacak ilkeyi belirten [CorSymSearchPolicyAttributes](corsymsearchpolicyattributes-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="f69e1-110">[in] A value of the [CorSymSearchPolicyAttributes](corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="f69e1-111">dışı Döndürülen [ıdimunmanagedreader](isymunmanagedreader-interface.md) arabirimine ayarlanmış bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f69e1-111">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f69e1-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f69e1-112">Return Value</span></span>  
 <span data-ttu-id="f69e1-113">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="f69e1-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f69e1-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f69e1-114">Requirements</span></span>  
 <span data-ttu-id="f69e1-115">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="f69e1-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f69e1-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f69e1-116">Remarks</span></span>  
 <span data-ttu-id="f69e1-117">Yönteminin bu sürümü, modülün hemen yanında bulunan bölümlerde PDB dosyasını arayabilir.</span><span class="sxs-lookup"><span data-stu-id="f69e1-117">This version of the method can search for the PDB file in areas other than right next to the module.</span></span> <span data-ttu-id="f69e1-118">Arama İlkesi [CorSymSearchPolicyAttributes](corsymsearchpolicyattributes-enumeration.md)birleştirilerek denetlenebilir.</span><span class="sxs-lookup"><span data-stu-id="f69e1-118">The search policy can be controlled by combining [CorSymSearchPolicyAttributes](corsymsearchpolicyattributes-enumeration.md).</span></span> <span data-ttu-id="f69e1-119">Örneğin, `AllowReferencePathAccess | AllowSymbolServerAccess` yürütülebilir dosyanın yanında ve bir sembol sunucusunda pdb 'yi arar, ancak kayıt defterini sorgulamaz veya yürütülebilir dosyadaki yolu kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="f69e1-119">For example, `AllowReferencePathAccess | AllowSymbolServerAccess` looks for the PDB next to the executable file and on a symbol server, but does not query the registry or use the path in the executable file.</span></span> <span data-ttu-id="f69e1-120">`searchPath`Parametresi sağlanmışsa, bu dizinler her zaman aranır.</span><span class="sxs-lookup"><span data-stu-id="f69e1-120">If the `searchPath` parameter is provided, those directories will always be searched.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f69e1-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f69e1-121">See also</span></span>

- [<span data-ttu-id="f69e1-122">ISymUnmanagedBinder2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f69e1-122">ISymUnmanagedBinder2 Interface</span></span>](isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="f69e1-123">GetReaderForFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f69e1-123">GetReaderForFile Method</span></span>](isymunmanagedbinder-getreaderforfile-method.md)
