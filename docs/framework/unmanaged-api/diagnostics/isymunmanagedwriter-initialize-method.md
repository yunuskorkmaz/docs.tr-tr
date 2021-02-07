---
description: 'Şu konuda daha fazla bilgi edinin: ıdimunmanagedwriter:: Initialize yöntemi'
title: ISymUnmanagedWriter::Initialize Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Initialize
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Initialize
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: e0ebd793-3764-4df0-8f12-0e95f60b9eae
topic_type:
- apiref
ms.openlocfilehash: eab60e9539df3d43a1602268d704ac324f028915
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762298"
---
# <a name="isymunmanagedwriterinitialize-method"></a><span data-ttu-id="b6b83-103">ISymUnmanagedWriter::Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b6b83-103">ISymUnmanagedWriter::Initialize Method</span></span>

<span data-ttu-id="b6b83-104">Bu yazıcının ilişkilendirileceği meta veri verici arabirimini ayarlar ve hata ayıklama simgelerinin yazılacağı çıkış dosyası adını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b6b83-104">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span>  
  
 <span data-ttu-id="b6b83-105">Bu yöntem yalnızca bir kez çağrılabilir ve diğer herhangi bir yazıcı yönteminden önce çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b6b83-105">This method can be called only once, and it must be called before any other writer methods.</span></span> <span data-ttu-id="b6b83-106">Bazı yazarlar bir dosya adı gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="b6b83-106">Some writers may require a file name.</span></span> <span data-ttu-id="b6b83-107">Ancak, dosya adını kullanmayan yazarlar üzerinde herhangi bir olumsuz etkisi olmadan bu yönteme her zaman bir dosya adı geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6b83-107">However, you can always pass a file name to this method without any negative effect on writers that do not use the file name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6b83-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b6b83-108">Syntax</span></span>  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *filename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6b83-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b6b83-109">Parameters</span></span>  

 `emitter`  
 <span data-ttu-id="b6b83-110">'ndaki Meta veri verici arabirimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b6b83-110">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `filename`  
 <span data-ttu-id="b6b83-111">'ndaki Hata ayıklama simgelerinin yazıldığı dosya adı.</span><span class="sxs-lookup"><span data-stu-id="b6b83-111">[in] The file name to which the debugging symbols are written.</span></span> <span data-ttu-id="b6b83-112">Dosya adları kullanmayan bir yazıcı için dosya adı belirtilmişse, bu parametre yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="b6b83-112">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="b6b83-113">'ndaki Belirtilmişse, sembol yazıcı sembolleri <xref:System.Runtime.InteropServices.ComTypes.IStream> parametresinde belirtilen dosya yerine verilen öğesine yayar `filename` .</span><span class="sxs-lookup"><span data-stu-id="b6b83-113">[in] If specified, the symbol writer will emit the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="b6b83-114">`pIStream`Parametresi isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b6b83-114">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="b6b83-115">[in] `true` Bu bir tam yeniden oluşturma ise `false` Bu bir artımlı derleme ise.</span><span class="sxs-lookup"><span data-stu-id="b6b83-115">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b6b83-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b6b83-116">Return Value</span></span>  

 <span data-ttu-id="b6b83-117">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="b6b83-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6b83-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b6b83-118">Requirements</span></span>  

 <span data-ttu-id="b6b83-119">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="b6b83-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6b83-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6b83-120">See also</span></span>

- [<span data-ttu-id="b6b83-121">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b6b83-121">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="b6b83-122">Initialize2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b6b83-122">Initialize2 Method</span></span>](isymunmanagedwriter-initialize2-method.md)
