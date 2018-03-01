---
title: "ISymUnmanagedWriter::Initialize2 Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedWriter.Initialize2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Initialize2
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize2 method [.NET Framework debugging]
- Initialize2 method [.NET Framework debugging]
ms.assetid: 93de56b6-4ae8-4cca-acdc-25a434623509
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 015c7d43a856990251b3e67febe685759cc4e5fb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterinitialize2-method"></a><span data-ttu-id="fa45c-102">ISymUnmanagedWriter::Initialize2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa45c-102">ISymUnmanagedWriter::Initialize2 Method</span></span>
<span data-ttu-id="fa45c-103">İle bu yazıcısı ilişkili olacağı meta verileri verici arabirimi ayarlar ve hata ayıklama simgeleri yazılacak çıktı dosyası adını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="fa45c-103">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span> <span data-ttu-id="fa45c-104">Bu yöntem, ayrıca program veritabanı (PDB) dosyasının son konumunu ayarlamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="fa45c-104">This method also lets you set the final location of the program database (PDB) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa45c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fa45c-105">Syntax</span></span>  
  
```  
HRESULT Initialize2(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *tempfilename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild,  
    [in] const WCHAR  *finalfilename);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fa45c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fa45c-106">Parameters</span></span>  
 `emitter`  
 <span data-ttu-id="fa45c-107">[in] Meta veri verici arayüzü için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fa45c-107">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `tempfilename`  
 <span data-ttu-id="fa45c-108">[in] Bir işaretçi bir `WCHAR` hata ayıklama simgeleri yazılır dosya adını içerir.</span><span class="sxs-lookup"><span data-stu-id="fa45c-108">[in] A pointer to a `WCHAR` that contains the file name to which the debugging symbols are written.</span></span> <span data-ttu-id="fa45c-109">Dosya adları kullanmayan bir yazıcı için bir dosya adı belirtilirse, bu parametre yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="fa45c-109">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="fa45c-110">[in] Belirtilmişse, simge yazan simgeleri yayar verilen <xref:System.Runtime.InteropServices.ComTypes.IStream> yerine belirtilen dosyaya `filename` parametresi.</span><span class="sxs-lookup"><span data-stu-id="fa45c-110">[in] If specified, the symbol writer emits the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="fa45c-111">`pIStream` Parametresi isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="fa45c-111">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="fa45c-112">[in] `true` bu tam bir yeniden oluşturma; ise `false` bu artımlı bir derleme ise.</span><span class="sxs-lookup"><span data-stu-id="fa45c-112">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
 `finalfilename`  
 <span data-ttu-id="fa45c-113">[in] Bir işaretçi bir `WCHAR` diğer bir deyişle PDB dosyasının son konumu yol dizesini.</span><span class="sxs-lookup"><span data-stu-id="fa45c-113">[in] A pointer to a `WCHAR` that is the path string to the final location of the PDB file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fa45c-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fa45c-114">Return Value</span></span>  
 <span data-ttu-id="fa45c-115">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="fa45c-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa45c-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fa45c-116">Requirements</span></span>  
 <span data-ttu-id="fa45c-117">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fa45c-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa45c-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fa45c-118">See Also</span></span>  
 [<span data-ttu-id="fa45c-119">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fa45c-119">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="fa45c-120">Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa45c-120">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)
