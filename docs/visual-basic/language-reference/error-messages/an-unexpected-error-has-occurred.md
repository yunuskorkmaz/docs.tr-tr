---
title: Tek örnek başlatmak için gerekli olan bir işletim sistemi kaynağı alınamadığından, beklenmeyen bir hata oluştu
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_CantGetMemoryMappedFile
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
ms.openlocfilehash: 82b513b89d661e49853e55f26df13eb354945038
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58828606"
---
# <a name="an-unexpected-error-has-occurred-because-an-operating-system-resource-required-for-single-instance-startup-cannot-be-acquired"></a><span data-ttu-id="87096-102">Tek örnek başlatmak için gerekli olan bir işletim sistemi kaynağı alınamadığından, beklenmeyen bir hata oluştu</span><span class="sxs-lookup"><span data-stu-id="87096-102">An unexpected error has occurred because an operating system resource required for single instance startup cannot be acquired</span></span>
<span data-ttu-id="87096-103">Uygulamayı gerekli işletim sistemi kaynak alınamadı.</span><span class="sxs-lookup"><span data-stu-id="87096-103">The application could not acquire a necessary operating system resource.</span></span> <span data-ttu-id="87096-104">Bu sorunun olası nedeni bazıları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="87096-104">Some of the possible causes for this problem are:</span></span>  
  
-   <span data-ttu-id="87096-105">Uygulamanın işletim sistemi bir adlandırılan nesne oluşturma izniniz yok.</span><span class="sxs-lookup"><span data-stu-id="87096-105">The application does not have permissions to create named operating-system objects.</span></span>  
  
-   <span data-ttu-id="87096-106">Ortak dil çalışma zamanı bellek eşlemeli dosyalar oluşturma izniniz yok.</span><span class="sxs-lookup"><span data-stu-id="87096-106">The common language runtime does not have permissions to create memory-mapped files.</span></span>  
  
-   <span data-ttu-id="87096-107">Uygulamasının bir işletim sistemi nesne erişmesi gerekir, ancak başka bir işlem tarafından kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="87096-107">The application needs to access an operating-system object, but another process is using it.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="87096-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="87096-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="87096-109">Uygulamanın işletim sistemi bir adlandırılan nesne oluşturmak için yeterli izinlere sahip olduğunu denetleyin.</span><span class="sxs-lookup"><span data-stu-id="87096-109">Check that the application has sufficient permissions to create named operating-system objects.</span></span>  
  
2.  <span data-ttu-id="87096-110">Ortak dil çalışma zamanı bellek eşlemeli dosyalar oluşturmak için yeterli izinlere sahip olduğunu denetleyin.</span><span class="sxs-lookup"><span data-stu-id="87096-110">Check that the common language runtime has sufficient permissions to create memory-mapped files.</span></span>  
  
3.  <span data-ttu-id="87096-111">Özgün örnek uygulamaya bağlanmak için gereken kaynak kullanarak herhangi bir işlem temizlemek için bilgisayarı yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="87096-111">Restart the computer to clear any process that may be using the resource needed to connect to the original instance application.</span></span>  
  
4.  <span data-ttu-id="87096-112">Altında hatanın gerçekleştiği durumlarda dikkat edin ve Microsoft Ürün Destek Hizmetleri'ni arayın</span><span class="sxs-lookup"><span data-stu-id="87096-112">Note the circumstances under which the error occurred, and call Microsoft Product Support Services</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87096-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87096-113">See also</span></span>

- [<span data-ttu-id="87096-114">Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87096-114">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [<span data-ttu-id="87096-115">Hata Ayıklayıcısı Temel Bilgileri</span><span class="sxs-lookup"><span data-stu-id="87096-115">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)
- [<span data-ttu-id="87096-116">Bizimle İletişime Geçin</span><span class="sxs-lookup"><span data-stu-id="87096-116">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
