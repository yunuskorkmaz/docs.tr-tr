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
ms.openlocfilehash: c5e36443295395997303cb94202f534a83d086f4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677875"
---
# <a name="isymunmanagedwriterdefineparameter-method"></a><span data-ttu-id="cae9a-102">ISymUnmanagedWriter::DefineParameter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cae9a-102">ISymUnmanagedWriter::DefineParameter Method</span></span>

<span data-ttu-id="cae9a-103">Geçerli yöntemde tek bir parametre tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cae9a-103">Defines a single parameter in the current method.</span></span> <span data-ttu-id="cae9a-104">Parametre türü, yöntemin imzasında parametre konumundan (sıra) alınır.</span><span class="sxs-lookup"><span data-stu-id="cae9a-104">The parameter type is taken from the parameter's position (sequence) within the method's signature.</span></span>  
  
 <span data-ttu-id="cae9a-105">Belirli bir yöntemin meta verilerinde Parametreler tanımlanmışsa, bu yöntemi kullanarak bunları tekrar tanımlamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="cae9a-105">If parameters are defined in the metadata for a given method, you do not have to define them again by using this method.</span></span> <span data-ttu-id="cae9a-106">Sembol okuyucuları, sembol deposunu denetlemeden önce parametrelerin normal meta verilerini denetmelidir.</span><span class="sxs-lookup"><span data-stu-id="cae9a-106">The symbol readers must check the normal metadata for the parameters before checking the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cae9a-107">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="cae9a-107">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="cae9a-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cae9a-108">Parameters</span></span>  

 `name`  
 <span data-ttu-id="cae9a-109">'ndaki Parametre adı.</span><span class="sxs-lookup"><span data-stu-id="cae9a-109">[in] The parameter name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="cae9a-110">'ndaki Parametre öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="cae9a-110">[in] The parameter attributes.</span></span>  
  
 `sequence`  
 <span data-ttu-id="cae9a-111">'ndaki Parametre imzası.</span><span class="sxs-lookup"><span data-stu-id="cae9a-111">[in] The parameter signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="cae9a-112">'ndaki Adres türü.</span><span class="sxs-lookup"><span data-stu-id="cae9a-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="cae9a-113">'ndaki Parametre belirtiminin ilk adresi.</span><span class="sxs-lookup"><span data-stu-id="cae9a-113">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="cae9a-114">'ndaki Parametre belirtiminin ikinci adresi.</span><span class="sxs-lookup"><span data-stu-id="cae9a-114">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="cae9a-115">'ndaki Parametre belirtiminin üçüncü adresi.</span><span class="sxs-lookup"><span data-stu-id="cae9a-115">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cae9a-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cae9a-116">Return Value</span></span>  

 <span data-ttu-id="cae9a-117">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="cae9a-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cae9a-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cae9a-118">Requirements</span></span>  

 <span data-ttu-id="cae9a-119">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="cae9a-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cae9a-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cae9a-120">See also</span></span>

- [<span data-ttu-id="cae9a-121">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cae9a-121">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
