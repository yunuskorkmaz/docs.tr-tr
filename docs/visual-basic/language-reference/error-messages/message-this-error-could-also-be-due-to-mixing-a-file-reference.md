---
title: <message> Bu hataya bir dosya başvurusu ile '<assemblyname>' derlemesine yapılan proje başvurusunun karışması da neden olmuş olabilir
ms.date: 07/20/2015
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords:
- BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
ms.openlocfilehash: cd2c00bda5b63abbd6bf7069ef28d0a812b22044
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873782"
---
# <a name="message-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-assemblyname"></a><span data-ttu-id="5bfe7-102">\<message> Bu hataya bir dosya başvurusu ile '\<assemblyname>' derlemesine yapılan proje başvurusunun karışması da neden olmuş olabilir</span><span class="sxs-lookup"><span data-stu-id="5bfe7-102">\<message> This error could also be due to mixing a file reference with a project reference to assembly '\<assemblyname>'</span></span>

<span data-ttu-id="5bfe7-103">\<message> Bu hata, bir dosya başvurusunu derleme ' a bir proje başvurusuyla karıştırmaya neden olmuş olabilir \<assemblyname> .</span><span class="sxs-lookup"><span data-stu-id="5bfe7-103">\<message> This error could also be due to mixing a file reference with a project reference to assembly '\<assemblyname>.</span></span> <span data-ttu-id="5bfe7-104">Bu durumda, ' ' projesindeki ' ' adlı dosya başvurusunu ' ' \<assemblyfilename> \<projectname1> için bir proje başvurusuyla değiştirmeyi deneyin \<projectname2> .</span><span class="sxs-lookup"><span data-stu-id="5bfe7-104">In this case, try replacing the file reference to '\<assemblyfilename>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>  
  
 <span data-ttu-id="5bfe7-105">Projenizdeki kod başka bir projenin üyesine erişir, ancak çözümünüzün yapılandırması, Visual Basic derleyicisinin başvuruyu çözümlemesine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="5bfe7-105">Code in your project accesses a member of another project, but the configuration of your solution does not allow the Visual Basic compiler to resolve the reference.</span></span>  
  
 <span data-ttu-id="5bfe7-106">Başka bir derlemede tanımlı bir türe erişmek için, Visual Basic derleyicisinin bu derlemeye bir başvurusu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5bfe7-106">To access a type defined in another assembly, the Visual Basic compiler must have a reference to that assembly.</span></span> <span data-ttu-id="5bfe7-107">Bu, projeler arasında döngüsel başvurulara neden olmayan tek, belirsiz bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5bfe7-107">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>  
  
 <span data-ttu-id="5bfe7-108">**Hata kimliği:** BC30971</span><span class="sxs-lookup"><span data-stu-id="5bfe7-108">**Error ID:** BC30971</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5bfe7-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="5bfe7-109">To correct this error</span></span>  
  
1. <span data-ttu-id="5bfe7-110">Projenizin başvurması için en iyi derlemeyi hangi projenin ürettiğini belirleme.</span><span class="sxs-lookup"><span data-stu-id="5bfe7-110">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="5bfe7-111">Bu karar için dosya erişiminin ve güncelleştirme sıklığının kolaylığı gibi ölçütleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5bfe7-111">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>  
  
2. <span data-ttu-id="5bfe7-112">Proje özelliklerinde, kullanmakta olduğunuz türü tanımlayan derlemeyi içeren projeye bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5bfe7-112">In your project properties, add a reference to the project that contains the assembly that defines the type you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bfe7-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5bfe7-113">See also</span></span>

- [<span data-ttu-id="5bfe7-114">Bir projedeki başvuruları yönetme</span><span class="sxs-lookup"><span data-stu-id="5bfe7-114">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="5bfe7-115">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="5bfe7-115">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [<span data-ttu-id="5bfe7-116">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="5bfe7-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="5bfe7-117">Bozuk Başvurularda Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="5bfe7-117">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
