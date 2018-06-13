---
title: Tek örnek başlatmak için gerekli olan bir işletim sistemi kaynağı alınamadığından, beklenmeyen bir hata oluştu
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_CantGetMemoryMappedFile
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
ms.openlocfilehash: 313128d5511ddd0f3b75c58e2c10a74eb967d130
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587658"
---
# <a name="an-unexpected-error-has-occurred-because-an-operating-system-resource-required-for-single-instance-startup-cannot-be-acquired"></a><span data-ttu-id="b1b81-102">Tek örnek başlatmak için gerekli olan bir işletim sistemi kaynağı alınamadığından, beklenmeyen bir hata oluştu</span><span class="sxs-lookup"><span data-stu-id="b1b81-102">An unexpected error has occurred because an operating system resource required for single instance startup cannot be acquired</span></span>
<span data-ttu-id="b1b81-103">Uygulamayı gerekli işletim sistemi kaynağı alınamadı.</span><span class="sxs-lookup"><span data-stu-id="b1b81-103">The application could not acquire a necessary operating system resource.</span></span> <span data-ttu-id="b1b81-104">Bu sorunun olası nedeni bazıları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b1b81-104">Some of the possible causes for this problem are:</span></span>  
  
-   <span data-ttu-id="b1b81-105">Uygulaması adlandırılmış işletim sistemi nesneleri oluşturma izni yok.</span><span class="sxs-lookup"><span data-stu-id="b1b81-105">The application does not have permissions to create named operating-system objects.</span></span>  
  
-   <span data-ttu-id="b1b81-106">Ortak dil çalışma zamanı bellek eşlemeli dosyalar oluşturmak için izinlere sahip değil.</span><span class="sxs-lookup"><span data-stu-id="b1b81-106">The common language runtime does not have permissions to create memory-mapped files.</span></span>  
  
-   <span data-ttu-id="b1b81-107">İşletim sistemi nesnenin erişmek uygulama gerekiyor, ancak başka bir işlem kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="b1b81-107">The application needs to access an operating-system object, but another process is using it.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b1b81-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="b1b81-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="b1b81-109">Uygulaması adlandırılmış işletim sistemi nesneleri oluşturmak için yeterli izinlere sahip olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b1b81-109">Check that the application has sufficient permissions to create named operating-system objects.</span></span>  
  
2.  <span data-ttu-id="b1b81-110">Ortak dil çalışma zamanı bellek eşlemeli dosyalar oluşturmak için yeterli izinlere sahip olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b1b81-110">Check that the common language runtime has sufficient permissions to create memory-mapped files.</span></span>  
  
3.  <span data-ttu-id="b1b81-111">Özgün örnek uygulamaya bağlanmak için gereken kaynak kullanarak herhangi bir işlem temizlemek için bilgisayarı yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="b1b81-111">Restart the computer to clear any process that may be using the resource needed to connect to the original instance application.</span></span>  
  
4.  <span data-ttu-id="b1b81-112">Hata oluştuğu durumlarda dikkat edin ve Microsoft Ürün Destek Hizmetleri'ne çağırın</span><span class="sxs-lookup"><span data-stu-id="b1b81-112">Note the circumstances under which the error occurred, and call Microsoft Product Support Services</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1b81-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b1b81-113">See Also</span></span>  
 [<span data-ttu-id="b1b81-114">Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b1b81-114">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)  
 [<span data-ttu-id="b1b81-115">Hata ayıklayıcı temel bilgileri</span><span class="sxs-lookup"><span data-stu-id="b1b81-115">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)  
 [<span data-ttu-id="b1b81-116">Bizimle İletişime Geçin</span><span class="sxs-lookup"><span data-stu-id="b1b81-116">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
