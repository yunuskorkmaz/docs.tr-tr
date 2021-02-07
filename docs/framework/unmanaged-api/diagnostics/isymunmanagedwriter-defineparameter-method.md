---
description: 'Şu konuda daha fazla bilgi edinin: ı, Efınımalewriter::D efineParameter yöntemi'
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
ms.openlocfilehash: 1e42140e33a99b224ccf3eff7ea29b7aa3ff1b15
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762363"
---
# <a name="isymunmanagedwriterdefineparameter-method"></a><span data-ttu-id="b1c25-103">ISymUnmanagedWriter::DefineParameter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1c25-103">ISymUnmanagedWriter::DefineParameter Method</span></span>

<span data-ttu-id="b1c25-104">Geçerli yöntemde tek bir parametre tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b1c25-104">Defines a single parameter in the current method.</span></span> <span data-ttu-id="b1c25-105">Parametre türü, yöntemin imzasında parametre konumundan (sıra) alınır.</span><span class="sxs-lookup"><span data-stu-id="b1c25-105">The parameter type is taken from the parameter's position (sequence) within the method's signature.</span></span>  
  
 <span data-ttu-id="b1c25-106">Belirli bir yöntemin meta verilerinde Parametreler tanımlanmışsa, bu yöntemi kullanarak bunları tekrar tanımlamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="b1c25-106">If parameters are defined in the metadata for a given method, you do not have to define them again by using this method.</span></span> <span data-ttu-id="b1c25-107">Sembol okuyucuları, sembol deposunu denetlemeden önce parametrelerin normal meta verilerini denetmelidir.</span><span class="sxs-lookup"><span data-stu-id="b1c25-107">The symbol readers must check the normal metadata for the parameters before checking the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1c25-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b1c25-108">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="b1c25-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b1c25-109">Parameters</span></span>  

 `name`  
 <span data-ttu-id="b1c25-110">'ndaki Parametre adı.</span><span class="sxs-lookup"><span data-stu-id="b1c25-110">[in] The parameter name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="b1c25-111">'ndaki Parametre öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="b1c25-111">[in] The parameter attributes.</span></span>  
  
 `sequence`  
 <span data-ttu-id="b1c25-112">'ndaki Parametre imzası.</span><span class="sxs-lookup"><span data-stu-id="b1c25-112">[in] The parameter signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="b1c25-113">'ndaki Adres türü.</span><span class="sxs-lookup"><span data-stu-id="b1c25-113">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="b1c25-114">'ndaki Parametre belirtiminin ilk adresi.</span><span class="sxs-lookup"><span data-stu-id="b1c25-114">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="b1c25-115">'ndaki Parametre belirtiminin ikinci adresi.</span><span class="sxs-lookup"><span data-stu-id="b1c25-115">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="b1c25-116">'ndaki Parametre belirtiminin üçüncü adresi.</span><span class="sxs-lookup"><span data-stu-id="b1c25-116">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1c25-117">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b1c25-117">Return Value</span></span>  

 <span data-ttu-id="b1c25-118">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="b1c25-118">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1c25-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b1c25-119">Requirements</span></span>  

 <span data-ttu-id="b1c25-120">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="b1c25-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1c25-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1c25-121">See also</span></span>

- [<span data-ttu-id="b1c25-122">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b1c25-122">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
