---
title: "Tek örnek başlatmak için gerekli olan bir işletim sistemi kaynağı alınamadığından, beklenmeyen bir hata oluştu"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrAppModel_CantGetMemoryMappedFile
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8969303d66e946d5579c6cca592b5701c4ebd632
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="an-unexpected-error-has-occurred-because-an-operating-system-resource-required-for-single-instance-startup-cannot-be-acquired"></a><span data-ttu-id="5912d-102">Tek örnek başlatmak için gerekli olan bir işletim sistemi kaynağı alınamadığından, beklenmeyen bir hata oluştu</span><span class="sxs-lookup"><span data-stu-id="5912d-102">An unexpected error has occurred because an operating system resource required for single instance startup cannot be acquired</span></span>
<span data-ttu-id="5912d-103">Uygulamayı gerekli işletim sistemi kaynağı alınamadı.</span><span class="sxs-lookup"><span data-stu-id="5912d-103">The application could not acquire a necessary operating system resource.</span></span> <span data-ttu-id="5912d-104">Bu sorunun olası nedeni bazıları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="5912d-104">Some of the possible causes for this problem are:</span></span>  
  
-   <span data-ttu-id="5912d-105">Uygulaması adlandırılmış işletim sistemi nesneleri oluşturma izni yok.</span><span class="sxs-lookup"><span data-stu-id="5912d-105">The application does not have permissions to create named operating-system objects.</span></span>  
  
-   <span data-ttu-id="5912d-106">Ortak dil çalışma zamanı bellek eşlemeli dosyalar oluşturmak için izinlere sahip değil.</span><span class="sxs-lookup"><span data-stu-id="5912d-106">The common language runtime does not have permissions to create memory-mapped files.</span></span>  
  
-   <span data-ttu-id="5912d-107">İşletim sistemi nesnenin erişmek uygulama gerekiyor, ancak başka bir işlem kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="5912d-107">The application needs to access an operating-system object, but another process is using it.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5912d-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="5912d-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="5912d-109">Uygulaması adlandırılmış işletim sistemi nesneleri oluşturmak için yeterli izinlere sahip olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5912d-109">Check that the application has sufficient permissions to create named operating-system objects.</span></span>  
  
2.  <span data-ttu-id="5912d-110">Ortak dil çalışma zamanı bellek eşlemeli dosyalar oluşturmak için yeterli izinlere sahip olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5912d-110">Check that the common language runtime has sufficient permissions to create memory-mapped files.</span></span>  
  
3.  <span data-ttu-id="5912d-111">Özgün örnek uygulamaya bağlanmak için gereken kaynak kullanarak herhangi bir işlem temizlemek için bilgisayarı yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="5912d-111">Restart the computer to clear any process that may be using the resource needed to connect to the original instance application.</span></span>  
  
4.  <span data-ttu-id="5912d-112">Hata oluştuğu durumlarda dikkat edin ve Microsoft Ürün Destek Hizmetleri'ne çağırın</span><span class="sxs-lookup"><span data-stu-id="5912d-112">Note the circumstances under which the error occurred, and call Microsoft Product Support Services</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5912d-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5912d-113">See Also</span></span>  
 [<span data-ttu-id="5912d-114">Uygulama sayfası, Proje Tasarımcısı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5912d-114">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)  
 [<span data-ttu-id="5912d-115">Hata ayıklayıcı temel bilgileri</span><span class="sxs-lookup"><span data-stu-id="5912d-115">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)  
 [<span data-ttu-id="5912d-116">Bizimle iletişime geçin</span><span class="sxs-lookup"><span data-stu-id="5912d-116">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
