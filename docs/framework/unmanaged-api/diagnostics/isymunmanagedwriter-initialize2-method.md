---
description: 'Şu konuda daha fazla bilgi edinin: ıdimunmanagedwriter:: Initialize2 yöntemi'
title: ISymUnmanagedWriter::Initialize2 Yöntemi
ms.date: 03/30/2017
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
ms.openlocfilehash: 0d4c769c9f1b571296cbfe159057df083a6d5ca6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762285"
---
# <a name="isymunmanagedwriterinitialize2-method"></a><span data-ttu-id="079ad-103">ISymUnmanagedWriter::Initialize2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="079ad-103">ISymUnmanagedWriter::Initialize2 Method</span></span>

<span data-ttu-id="079ad-104">Bu yazıcının ilişkilendirileceği meta veri verici arabirimini ayarlar ve hata ayıklama simgelerinin yazılacağı çıkış dosyası adını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="079ad-104">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span> <span data-ttu-id="079ad-105">Bu yöntem, program veritabanı (PDB) dosyasının son konumunu ayarlamanıza de olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="079ad-105">This method also lets you set the final location of the program database (PDB) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="079ad-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="079ad-106">Syntax</span></span>  
  
```cpp  
HRESULT Initialize2(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *tempfilename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild,  
    [in] const WCHAR  *finalfilename);  
```  
  
## <a name="parameters"></a><span data-ttu-id="079ad-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="079ad-107">Parameters</span></span>  

 `emitter`  
 <span data-ttu-id="079ad-108">'ndaki Meta veri verici arabirimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="079ad-108">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `tempfilename`  
 <span data-ttu-id="079ad-109">'ndaki `WCHAR` Hata ayıklama simgelerinin yazıldığı dosya adını içeren bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="079ad-109">[in] A pointer to a `WCHAR` that contains the file name to which the debugging symbols are written.</span></span> <span data-ttu-id="079ad-110">Dosya adları kullanmayan bir yazıcı için dosya adı belirtilmişse, bu parametre yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="079ad-110">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="079ad-111">'ndaki Belirtilmişse, sembol yazıcı sembolleri <xref:System.Runtime.InteropServices.ComTypes.IStream> parametresinde belirtilen dosya yerine, belirtilen içine yayar `filename` .</span><span class="sxs-lookup"><span data-stu-id="079ad-111">[in] If specified, the symbol writer emits the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="079ad-112">`pIStream`Parametresi isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="079ad-112">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="079ad-113">[in] `true` Bu bir tam yeniden oluşturma ise `false` Bu bir artımlı derleme ise.</span><span class="sxs-lookup"><span data-stu-id="079ad-113">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
 `finalfilename`  
 <span data-ttu-id="079ad-114">'ndaki , `WCHAR` Pdb dosyasının son konumunun yol dizesi olan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="079ad-114">[in] A pointer to a `WCHAR` that is the path string to the final location of the PDB file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="079ad-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="079ad-115">Return Value</span></span>  

 <span data-ttu-id="079ad-116">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="079ad-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="079ad-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="079ad-117">Requirements</span></span>  

 <span data-ttu-id="079ad-118">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="079ad-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="079ad-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="079ad-119">See also</span></span>

- [<span data-ttu-id="079ad-120">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="079ad-120">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="079ad-121">Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="079ad-121">Initialize Method</span></span>](isymunmanagedwriter-initialize-method.md)
