---
title: ISymUnmanagedWriter::DefineParameter Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineParameter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineParameter
helpviewer_keywords:
- DefineParameter method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineParameter method [.NET Framework debugging]
ms.assetid: a8e3dd32-6a44-4371-9a74-f417b11998c8
topic_type:
- apiref
ms.openlocfilehash: c695aa80ea3bf90a29ce7c5d11eda7fae5fe7b2d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614818"
---
# <a name="isymunmanagedwriterdefineparameter-method"></a><span data-ttu-id="793d8-102">ISymUnmanagedWriter::DefineParameter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="793d8-102">ISymUnmanagedWriter::DefineParameter Method</span></span>
<span data-ttu-id="793d8-103">Geçerli yöntemde tek bir parametre tanımlar.</span><span class="sxs-lookup"><span data-stu-id="793d8-103">Defines a single parameter in the current method.</span></span> <span data-ttu-id="793d8-104">Parametre türü, yöntemin imzasında parametre konumundan (sıra) alınır.</span><span class="sxs-lookup"><span data-stu-id="793d8-104">The parameter type is taken from the parameter's position (sequence) within the method's signature.</span></span>  
  
 <span data-ttu-id="793d8-105">Belirli bir yöntemin meta verilerinde Parametreler tanımlanmışsa, bu yöntemi kullanarak bunları tekrar tanımlamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="793d8-105">If parameters are defined in the metadata for a given method, you do not have to define them again by using this method.</span></span> <span data-ttu-id="793d8-106">Sembol okuyucuları, sembol deposunu denetlemeden önce parametrelerin normal meta verilerini denetmelidir.</span><span class="sxs-lookup"><span data-stu-id="793d8-106">The symbol readers must check the normal metadata for the parameters before checking the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="793d8-107">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="793d8-107">Syntax</span></span>  
  
```cpp  
HRESULT DefineParameter(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      sequence,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="793d8-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="793d8-108">Parameters</span></span>  
 `name`  
 <span data-ttu-id="793d8-109">'ndaki Parametre adı.</span><span class="sxs-lookup"><span data-stu-id="793d8-109">[in] The parameter name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="793d8-110">'ndaki Parametre öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="793d8-110">[in] The parameter attributes.</span></span>  
  
 `sequence`  
 <span data-ttu-id="793d8-111">'ndaki Parametre imzası.</span><span class="sxs-lookup"><span data-stu-id="793d8-111">[in] The parameter signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="793d8-112">'ndaki Adres türü.</span><span class="sxs-lookup"><span data-stu-id="793d8-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="793d8-113">'ndaki Parametre belirtiminin ilk adresi.</span><span class="sxs-lookup"><span data-stu-id="793d8-113">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="793d8-114">'ndaki Parametre belirtiminin ikinci adresi.</span><span class="sxs-lookup"><span data-stu-id="793d8-114">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="793d8-115">'ndaki Parametre belirtiminin üçüncü adresi.</span><span class="sxs-lookup"><span data-stu-id="793d8-115">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="793d8-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="793d8-116">Return Value</span></span>  
 <span data-ttu-id="793d8-117">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="793d8-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="793d8-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="793d8-118">Requirements</span></span>  
 <span data-ttu-id="793d8-119">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="793d8-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="793d8-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="793d8-120">See also</span></span>

- [<span data-ttu-id="793d8-121">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="793d8-121">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
