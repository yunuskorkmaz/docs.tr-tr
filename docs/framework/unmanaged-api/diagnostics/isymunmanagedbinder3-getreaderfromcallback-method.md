---
description: 'Şu konuda daha fazla bilgi edinin: ISymUnmanagedBinder3:: GetReaderFromCallback yöntemi'
title: ISymUnmanagedBinder3::GetReaderFromCallback Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder3.GetReaderFromCallback
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder3::GetReaderFromCallback
helpviewer_keywords:
- GetReaderFromCallback method [.NET Framework debugging]
- ISymUnmanagedBinder3::GetReaderFromCallback method [.NET Framework debugging]
ms.assetid: 4ef83bd2-3d8e-499e-8a12-d9d6fd6ced30
topic_type:
- apiref
ms.openlocfilehash: ba7c819678fee7625f3cddb29d99f5d7f4c6f991
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689878"
---
# <a name="isymunmanagedbinder3getreaderfromcallback-method"></a><span data-ttu-id="b1799-103">ISymUnmanagedBinder3::GetReaderFromCallback Metodu</span><span class="sxs-lookup"><span data-stu-id="b1799-103">ISymUnmanagedBinder3::GetReaderFromCallback Method</span></span>

<span data-ttu-id="b1799-104">Kullanıcının `IID_IDiaReadExeAtRVACallback` `IID_IDiaReadExeAtOffsetCallback` bellekten hata ayıklama dizini bilgilerini elde etmek için bir veya geri çağırma yoluyla uygulama veya sağlama yapmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="b1799-104">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the debug directory information from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1799-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b1799-105">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderFromCallback(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [in]  IUnknown     *callback,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1799-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b1799-106">Parameters</span></span>  

 `importer`  
 <span data-ttu-id="b1799-107">'ndaki Meta veri içeri aktarma arabirimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b1799-107">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="b1799-108">'ndaki Dosya adı işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="b1799-108">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="b1799-109">'ndaki Arama yoluna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b1799-109">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="b1799-110">'ndaki Bir sembol okuyucu ararken kullanılacak ilkeyi belirten [CorSymSearchPolicyAttributes](corsymsearchpolicyattributes-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="b1799-110">[in] A value of the [CorSymSearchPolicyAttributes](corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `callback`  
 <span data-ttu-id="b1799-111">'ndaki Geri çağırma işlevine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b1799-111">[in] A pointer to the callback function.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="b1799-112">dışı Döndürülen [ıdimunmanagedreader](isymunmanagedreader-interface.md) arabirimine ayarlanmış bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b1799-112">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1799-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b1799-113">Return Value</span></span>  

 <span data-ttu-id="b1799-114">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="b1799-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1799-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b1799-115">Requirements</span></span>  

 <span data-ttu-id="b1799-116">**Üst bilgi:** Corsya. IDL</span><span class="sxs-lookup"><span data-stu-id="b1799-116">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1799-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1799-117">See also</span></span>

- [<span data-ttu-id="b1799-118">ISymUnmanagedBinder3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b1799-118">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)
