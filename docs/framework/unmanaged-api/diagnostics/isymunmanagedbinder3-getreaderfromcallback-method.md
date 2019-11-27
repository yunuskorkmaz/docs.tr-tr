---
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
ms.openlocfilehash: a0cccc0adfc666cc8e373bc1f89c8f6f97068fde
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449304"
---
# <a name="isymunmanagedbinder3getreaderfromcallback-method"></a><span data-ttu-id="599fb-102">ISymUnmanagedBinder3::GetReaderFromCallback Metodu</span><span class="sxs-lookup"><span data-stu-id="599fb-102">ISymUnmanagedBinder3::GetReaderFromCallback Method</span></span>
<span data-ttu-id="599fb-103">Kullanıcının bellekten hata ayıklama dizini bilgilerini elde etmek için bir `IID_IDiaReadExeAtRVACallback` veya `IID_IDiaReadExeAtOffsetCallback` geri çağırma yoluyla uygulama veya sağlama olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="599fb-103">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the debug directory information from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="599fb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="599fb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderFromCallback(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [in]  IUnknown     *callback,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="599fb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="599fb-105">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="599fb-106">'ndaki Meta veri içeri aktarma arabirimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="599fb-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="599fb-107">'ndaki Dosya adı işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="599fb-107">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="599fb-108">'ndaki Arama yoluna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="599fb-108">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="599fb-109">'ndaki Bir sembol okuyucu ararken kullanılacak ilkeyi belirten [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="599fb-109">[in] A value of the [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `callback`  
 <span data-ttu-id="599fb-110">'ndaki Geri çağırma işlevine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="599fb-110">[in] A pointer to the callback function.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="599fb-111">dışı Döndürülen [ıdimunmanagedreader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) arabirimine ayarlanmış bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="599fb-111">[out] A pointer that is set to the returned [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="599fb-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="599fb-112">Return Value</span></span>  
 <span data-ttu-id="599fb-113">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="599fb-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="599fb-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="599fb-114">Requirements</span></span>  
 <span data-ttu-id="599fb-115">**Üst bilgi:** Corsya. IDL</span><span class="sxs-lookup"><span data-stu-id="599fb-115">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="599fb-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="599fb-116">See also</span></span>

- [<span data-ttu-id="599fb-117">ISymUnmanagedBinder3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="599fb-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
