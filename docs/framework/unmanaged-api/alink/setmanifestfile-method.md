---
title: SetManifestFile Yöntemi
ms.date: 03/30/2017
api_name:
- IALink3.SetManifestFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetManifestFile
helpviewer_keywords:
- SetManifestFile method
ms.assetid: 1b33de4c-19cb-4a36-a93f-8675b2a36d58
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f22927b388a62ee6025c987bb107b2dfd51da0e3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489009"
---
# <a name="setmanifestfile-method"></a><span data-ttu-id="fdbd6-102">SetManifestFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fdbd6-102">SetManifestFile Method</span></span>
<span data-ttu-id="fdbd6-103">Bağlayıcı derleme oluşturduğunda kullandığı bildirim dosyası sıfırlamak sağlar.</span><span class="sxs-lookup"><span data-stu-id="fdbd6-103">Enables you to specify or reset the manifest file that the linker uses when it creates the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdbd6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fdbd6-104">Syntax</span></span>  
  
```  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="fdbd6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fdbd6-105">Parameters</span></span>  
 `pszFile`  
  
 <span data-ttu-id="fdbd6-106">İçerikleri Win32 kaynakları blob yerleştirilir bildirimi dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="fdbd6-106">The name of the manifest file whose contents are put into the Win32 resources blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fdbd6-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fdbd6-107">Return Value</span></span>  
 <span data-ttu-id="fdbd6-108">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="fdbd6-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fdbd6-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fdbd6-109">Remarks</span></span>  
 <span data-ttu-id="fdbd6-110">Bu, Win32ResBlob için soran önce çağırın.</span><span class="sxs-lookup"><span data-stu-id="fdbd6-110">Call this before asking for the Win32ResBlob.</span></span> <span data-ttu-id="fdbd6-111">Değerini `pszFile` parametredir içerikleri okuma ve Win32 kaynakları, kimliği rt_manıfest ile koymak bildirim dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="fdbd6-111">The value of the `pszFile` parameter is the name of the manifest file whose contents are read and put in the Win32 resources with ID of RT_MANIFEST.</span></span> <span data-ttu-id="fdbd6-112">Bir parametre null kullanarak çağrıldığında, daha önce okuma herhangi bir bildirim temizlenir.</span><span class="sxs-lookup"><span data-stu-id="fdbd6-112">When called by using a parameter of NULL, any previously read manifest is cleared.</span></span> <span data-ttu-id="fdbd6-113">Bu, bir başlatma süresi, bağlayıcı durumunu sıfırlamak sağlar.</span><span class="sxs-lookup"><span data-stu-id="fdbd6-113">This enables one to reset the state of the linker to that of initialization time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdbd6-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fdbd6-114">Requirements</span></span>  
 <span data-ttu-id="fdbd6-115">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="fdbd6-115">Requires aLink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdbd6-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fdbd6-116">See also</span></span>
- [<span data-ttu-id="fdbd6-117">IALink3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fdbd6-117">IALink3 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink3-interface.md)
- [<span data-ttu-id="fdbd6-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="fdbd6-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
- [<span data-ttu-id="fdbd6-119">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fdbd6-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="fdbd6-120">Al.exe (Bütünleştirilmiş Kod Bağlayıcı)</span><span class="sxs-lookup"><span data-stu-id="fdbd6-120">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
