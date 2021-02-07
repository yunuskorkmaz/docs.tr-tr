---
description: 'Daha fazla bilgi edinin: SetManifestFile Yöntemi'
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
ms.openlocfilehash: fe91c7f2b4e6f58a0a740de84e055ead49adb77d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662331"
---
# <a name="setmanifestfile-method"></a><span data-ttu-id="f9bc2-103">SetManifestFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f9bc2-103">SetManifestFile Method</span></span>

<span data-ttu-id="f9bc2-104">Bağlayıcının, derlemeyi oluşturduğunda kullandığı bildirim dosyasını belirtmenize veya sıfırlamasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f9bc2-104">Enables you to specify or reset the manifest file that the linker uses when it creates the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9bc2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f9bc2-105">Syntax</span></span>  
  
```cpp  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9bc2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f9bc2-106">Parameters</span></span>  

 `pszFile`  
  
 <span data-ttu-id="f9bc2-107">İçeriği Win32 kaynakları blobuna yerleştirilen bildirim dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="f9bc2-107">The name of the manifest file whose contents are put into the Win32 resources blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f9bc2-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f9bc2-108">Return Value</span></span>  

 <span data-ttu-id="f9bc2-109">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="f9bc2-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9bc2-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f9bc2-110">Remarks</span></span>  

 <span data-ttu-id="f9bc2-111">Win32ResBlob sorulmadan önce bunu çağırın.</span><span class="sxs-lookup"><span data-stu-id="f9bc2-111">Call this before asking for the Win32ResBlob.</span></span> <span data-ttu-id="f9bc2-112">Parametresinin değeri, `pszFile` içeriği okunan ve RT_MANIFEST kimliği olan Win32 kaynaklarına yerleştirilen bildirim dosyasının adıdır.</span><span class="sxs-lookup"><span data-stu-id="f9bc2-112">The value of the `pszFile` parameter is the name of the manifest file whose contents are read and put in the Win32 resources with ID of RT_MANIFEST.</span></span> <span data-ttu-id="f9bc2-113">NULL parametresi kullanılarak çağrıldığında, daha önce okuma bildirimi temizlenir.</span><span class="sxs-lookup"><span data-stu-id="f9bc2-113">When called by using a parameter of NULL, any previously read manifest is cleared.</span></span> <span data-ttu-id="f9bc2-114">Bu, bir tane, bağlayıcının durumunu başlatma zamanına sıfırlamasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f9bc2-114">This enables one to reset the state of the linker to that of initialization time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9bc2-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f9bc2-115">Requirements</span></span>  

 <span data-ttu-id="f9bc2-116">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="f9bc2-116">Requires aLink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9bc2-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9bc2-117">See also</span></span>

- [<span data-ttu-id="f9bc2-118">IALink3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f9bc2-118">IALink3 Interface</span></span>](ialink3-interface.md)
- [<span data-ttu-id="f9bc2-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="f9bc2-119">ALink API</span></span>](index.md)
- [<span data-ttu-id="f9bc2-120">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f9bc2-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="f9bc2-121">Al.exe (bütünleştirilmiş kod bağlayıcı)</span><span class="sxs-lookup"><span data-stu-id="f9bc2-121">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
