---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagedreader:: UpdateSymbolStore yöntemi'
title: ISymUnmanagedReader::UpdateSymbolStore Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.UpdateSymbolStore
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::UpdateSymbolStore
helpviewer_keywords:
- UpdateSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::UpdateSymbolStore method [.NET Framework debugging]
ms.assetid: 4a17d723-86b9-4f27-bd0d-b70c3259011c
topic_type:
- apiref
ms.openlocfilehash: eb6ca01b7978b66d0a8674e5b83ce26ee341e890
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763754"
---
# <a name="isymunmanagedreaderupdatesymbolstore-method"></a><span data-ttu-id="47785-103">ISymUnmanagedReader::UpdateSymbolStore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="47785-103">ISymUnmanagedReader::UpdateSymbolStore Method</span></span>

<span data-ttu-id="47785-104">Var olan sembol deposunu bir Delta sembol deposu ile güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="47785-104">Updates the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="47785-105">Bu yöntem, sembol deposunu değişimleri ile orijinal taşınabilir yürütülebilir (PE) dosyası eşleşecek şekilde güncelleştirmek için Düzenle ve devam et senaryolarında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="47785-105">This method is used in edit-and-continue scenarios to update the symbol store to match deltas to the original portable executable (PE) file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="47785-106">Ya da parametrelerinden yalnızca birini belirtmeniz gerekir `filename` `pIStream` .</span><span class="sxs-lookup"><span data-stu-id="47785-106">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="47785-107">`filename`Belirtilmişse, sembol deposu bu dosyadaki simgelerle güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="47785-107">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="47785-108">`pIStream`Belirtilmişse, mağaza içindeki verilerle güncelleştirilir <xref:System.Runtime.InteropServices.ComTypes.IStream> .</span><span class="sxs-lookup"><span data-stu-id="47785-108">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47785-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="47785-109">Syntax</span></span>  
  
```cpp  
HRESULT UpdateSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47785-110">Parametreler</span><span class="sxs-lookup"><span data-stu-id="47785-110">Parameters</span></span>  

 `filename`  
 <span data-ttu-id="47785-111">'ndaki Sembol deposunu içeren dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="47785-111">[in] The name of the file that contains the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="47785-112">'ndaki Parametresi için alternatif olarak kullanılan dosya akışı `filename` .</span><span class="sxs-lookup"><span data-stu-id="47785-112">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="47785-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="47785-113">Return Value</span></span>  

 <span data-ttu-id="47785-114">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="47785-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47785-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="47785-115">Requirements</span></span>  

 <span data-ttu-id="47785-116">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="47785-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47785-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47785-117">See also</span></span>

- [<span data-ttu-id="47785-118">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="47785-118">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
