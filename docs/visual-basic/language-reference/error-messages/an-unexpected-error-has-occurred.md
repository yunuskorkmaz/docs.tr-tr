---
description: 'Hakkında daha fazla bilgi edinin: tek örnekli bir başlatma için gerekli olan bir işletim sistemi kaynağı alınamadığından beklenmeyen bir hata oluştu'
title: Tek örnek başlatmak için gerekli olan bir işletim sistemi kaynağı alınamadığından, beklenmeyen bir hata oluştu
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_CantGetMemoryMappedFile
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
ms.openlocfilehash: 76f7bd43c05ea3bd46b352a791debac984ca8fcd
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102103614"
---
# <a name="an-unexpected-error-has-occurred-because-an-operating-system-resource-required-for-single-instance-startup-cannot-be-acquired"></a><span data-ttu-id="55dd4-103">Tek örnek başlatmak için gerekli olan bir işletim sistemi kaynağı alınamadığından, beklenmeyen bir hata oluştu</span><span class="sxs-lookup"><span data-stu-id="55dd4-103">An unexpected error has occurred because an operating system resource required for single instance startup cannot be acquired</span></span>

<span data-ttu-id="55dd4-104">Uygulama gerekli bir işletim sistemi kaynağını alamadı.</span><span class="sxs-lookup"><span data-stu-id="55dd4-104">The application could not acquire a necessary operating system resource.</span></span> <span data-ttu-id="55dd4-105">Bu sorunun olası nedenlerinden bazıları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="55dd4-105">Some of the possible causes for this problem are:</span></span>  
  
- <span data-ttu-id="55dd4-106">Uygulamanın adlandırılmış işletim sistemi nesneleri oluşturma izni yok.</span><span class="sxs-lookup"><span data-stu-id="55dd4-106">The application does not have permissions to create named operating-system objects.</span></span>  
  
- <span data-ttu-id="55dd4-107">Ortak dil çalışma zamanının bellekle eşlenen dosyalar oluşturma izni yok.</span><span class="sxs-lookup"><span data-stu-id="55dd4-107">The common language runtime does not have permissions to create memory-mapped files.</span></span>  
  
- <span data-ttu-id="55dd4-108">Uygulamanın bir işletim sistemi nesnesine erişmesi gerekir, ancak başka bir işlem onu kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="55dd4-108">The application needs to access an operating-system object, but another process is using it.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="55dd4-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="55dd4-109">To correct this error</span></span>  
  
1. <span data-ttu-id="55dd4-110">Uygulamanın adlandırılmış işletim sistemi nesneleri oluşturmak için yeterli izinlere sahip olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="55dd4-110">Check that the application has sufficient permissions to create named operating-system objects.</span></span>  
  
2. <span data-ttu-id="55dd4-111">Ortak dil çalışma zamanının, bellek eşlemeli dosyalar oluşturmak için yeterli izinlere sahip olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="55dd4-111">Check that the common language runtime has sufficient permissions to create memory-mapped files.</span></span>  
  
3. <span data-ttu-id="55dd4-112">Özgün örnek uygulamasına bağlanmak için gereken kaynağı kullanıyor olabilecek tüm işlemleri temizlemek için bilgisayarı yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="55dd4-112">Restart the computer to clear any process that may be using the resource needed to connect to the original instance application.</span></span>  
  
4. <span data-ttu-id="55dd4-113">Hatanın oluştuğu koşulları göz önünde, Microsoft Ürün Destek Hizmetleri 'ni çağıran</span><span class="sxs-lookup"><span data-stu-id="55dd4-113">Note the circumstances under which the error occurred, and call Microsoft Product Support Services</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55dd4-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55dd4-114">See also</span></span>

- [<span data-ttu-id="55dd4-115">Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="55dd4-115">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [<span data-ttu-id="55dd4-116">Hata Ayıklayıcı Temel Bilgileri</span><span class="sxs-lookup"><span data-stu-id="55dd4-116">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)
- [<span data-ttu-id="55dd4-117">Visual Studio geri bildirim seçenekleri</span><span class="sxs-lookup"><span data-stu-id="55dd4-117">Visual Studio feedback options</span></span>](/visualstudio/ide/feedback-options)
