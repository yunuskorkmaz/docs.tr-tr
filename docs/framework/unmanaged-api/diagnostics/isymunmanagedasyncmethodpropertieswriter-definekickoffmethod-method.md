---
description: 'Şu konuda daha fazla bilgi edinin: ırivmanagedasyncmethodpropertieswriter::D efineKickoffMethod yöntemi'
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Yöntemi
ms.date: 03/30/2017
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
ms.openlocfilehash: 7333823bce27eace4e9cb988ac31252743cca952
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790236"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="072ec-103">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="072ec-103">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>

<span data-ttu-id="072ec-104">Zaman uyumsuz işlemi başlatan başlangıç yöntemini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="072ec-104">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="072ec-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="072ec-105">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="072ec-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="072ec-106">Parameters</span></span>  
  
|<span data-ttu-id="072ec-107">Parametre</span><span class="sxs-lookup"><span data-stu-id="072ec-107">Parameter</span></span>|<span data-ttu-id="072ec-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="072ec-108">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="072ec-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="072ec-109">Return Value</span></span>  

 <span data-ttu-id="072ec-110">`HRESULT` döndürür.</span><span class="sxs-lookup"><span data-stu-id="072ec-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="072ec-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="072ec-111">Requirements</span></span>  

 <span data-ttu-id="072ec-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="072ec-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="072ec-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="072ec-113">See also</span></span>

- [<span data-ttu-id="072ec-114">ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="072ec-114">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)
