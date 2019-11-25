---
title: Tek örnek başlatmak için gerekli olan bir işletim sistemi kaynağı alınamadığından, beklenmeyen bir hata oluştu
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_CantGetMemoryMappedFile
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
ms.openlocfilehash: 640e32dc7f748ecd0a999a8432512103f46862c2
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976172"
---
# <a name="an-unexpected-error-has-occurred-because-an-operating-system-resource-required-for-single-instance-startup-cannot-be-acquired"></a><span data-ttu-id="0628c-102">Tek örnek başlatmak için gerekli olan bir işletim sistemi kaynağı alınamadığından, beklenmeyen bir hata oluştu</span><span class="sxs-lookup"><span data-stu-id="0628c-102">An unexpected error has occurred because an operating system resource required for single instance startup cannot be acquired</span></span>

<span data-ttu-id="0628c-103">Uygulama gerekli bir işletim sistemi kaynağını alamadı.</span><span class="sxs-lookup"><span data-stu-id="0628c-103">The application could not acquire a necessary operating system resource.</span></span> <span data-ttu-id="0628c-104">Bu sorunun olası nedenlerinden bazıları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="0628c-104">Some of the possible causes for this problem are:</span></span>  
  
- <span data-ttu-id="0628c-105">Uygulamanın adlandırılmış işletim sistemi nesneleri oluşturma izni yok.</span><span class="sxs-lookup"><span data-stu-id="0628c-105">The application does not have permissions to create named operating-system objects.</span></span>  
  
- <span data-ttu-id="0628c-106">Ortak dil çalışma zamanının bellekle eşlenen dosyalar oluşturma izni yok.</span><span class="sxs-lookup"><span data-stu-id="0628c-106">The common language runtime does not have permissions to create memory-mapped files.</span></span>  
  
- <span data-ttu-id="0628c-107">Uygulamanın bir işletim sistemi nesnesine erişmesi gerekir, ancak başka bir işlem onu kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="0628c-107">The application needs to access an operating-system object, but another process is using it.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0628c-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="0628c-108">To correct this error</span></span>  
  
1. <span data-ttu-id="0628c-109">Uygulamanın adlandırılmış işletim sistemi nesneleri oluşturmak için yeterli izinlere sahip olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="0628c-109">Check that the application has sufficient permissions to create named operating-system objects.</span></span>  
  
2. <span data-ttu-id="0628c-110">Ortak dil çalışma zamanının, bellek eşlemeli dosyalar oluşturmak için yeterli izinlere sahip olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="0628c-110">Check that the common language runtime has sufficient permissions to create memory-mapped files.</span></span>  
  
3. <span data-ttu-id="0628c-111">Özgün örnek uygulamasına bağlanmak için gereken kaynağı kullanıyor olabilecek tüm işlemleri temizlemek için bilgisayarı yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="0628c-111">Restart the computer to clear any process that may be using the resource needed to connect to the original instance application.</span></span>  
  
4. <span data-ttu-id="0628c-112">Hatanın oluştuğu koşulları göz önünde, Microsoft Ürün Destek Hizmetleri 'ni çağıran</span><span class="sxs-lookup"><span data-stu-id="0628c-112">Note the circumstances under which the error occurred, and call Microsoft Product Support Services</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0628c-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0628c-113">See also</span></span>

- [<span data-ttu-id="0628c-114">Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0628c-114">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [<span data-ttu-id="0628c-115">Hata Ayıklayıcısı Temel Bilgileri</span><span class="sxs-lookup"><span data-stu-id="0628c-115">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)
- [<span data-ttu-id="0628c-116">Bizimle İletişime Geçin</span><span class="sxs-lookup"><span data-stu-id="0628c-116">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
