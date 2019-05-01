---
title: <message> Bu hata, bir dosya başvurusu ile derleme yapılan proje başvurusunun karışması da olabilir '<assemblyname>'
ms.date: 07/20/2015
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords:
- BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
ms.openlocfilehash: 951f90a9209ff31896f4426ceb75f05b012897a6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921023"
---
# <a name="message-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-assemblyname"></a><span data-ttu-id="7fa0e-102">\<İleti > Bu hata, bir dosya başvurusu ile derleme yapılan proje başvurusunun karışması da olabilir '\<assemblyname >'</span><span class="sxs-lookup"><span data-stu-id="7fa0e-102">\<message> This error could also be due to mixing a file reference with a project reference to assembly '\<assemblyname>'</span></span>
<span data-ttu-id="7fa0e-103">\<İleti > Bu hata, bir dosya başvurusu ile derleme yapılan proje başvurusunun karışması da olabilir '\<assemblyname >.</span><span class="sxs-lookup"><span data-stu-id="7fa0e-103">\<message> This error could also be due to mixing a file reference with a project reference to assembly '\<assemblyname>.</span></span> <span data-ttu-id="7fa0e-104">Bu durumda, dosya başvurusu değiştirmeyi deneyin. '\<assemblyfilename >' projesindeki '\<projectname1 >' proje başvurusu ile '\<projectname2 >'.</span><span class="sxs-lookup"><span data-stu-id="7fa0e-104">In this case, try replacing the file reference to '\<assemblyfilename>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>  
  
 <span data-ttu-id="7fa0e-105">Kodu, projenizdeki başka bir proje üyesi erişen ancak çözümünüz yapılandırmasını başvuru çözmek Visual Basic Derleyicisi izin vermiyor.</span><span class="sxs-lookup"><span data-stu-id="7fa0e-105">Code in your project accesses a member of another project, but the configuration of your solution does not allow the Visual Basic compiler to resolve the reference.</span></span>  
  
 <span data-ttu-id="7fa0e-106">Başka bir derlemede tanımlanan bir türü erişmek için Visual Basic Derleyicisi derlemeye bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7fa0e-106">To access a type defined in another assembly, the Visual Basic compiler must have a reference to that assembly.</span></span> <span data-ttu-id="7fa0e-107">Bu projeler arasında döngüsel başvurulara neden olmaz tek ve eksiksiz bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7fa0e-107">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>  
  
 <span data-ttu-id="7fa0e-108">**Hata Kimliği:** BC30971</span><span class="sxs-lookup"><span data-stu-id="7fa0e-108">**Error ID:** BC30971</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7fa0e-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="7fa0e-109">To correct this error</span></span>  
  
1. <span data-ttu-id="7fa0e-110">Başvurmak için en iyi derleme projeniz için proje üretir belirleyin.</span><span class="sxs-lookup"><span data-stu-id="7fa0e-110">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="7fa0e-111">Bu kararı, dosya erişim kolaylığı ve güncelleştirmelerinin sıklığı gibi ölçütlere kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="7fa0e-111">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>  
  
2. <span data-ttu-id="7fa0e-112">Proje özelliklerinizi kullanmakta olduğunuz türü tanımlayan derleme içeren projeye başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7fa0e-112">In your project properties, add a reference to the project that contains the assembly that defines the type you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fa0e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7fa0e-113">See also</span></span>

- [<span data-ttu-id="7fa0e-114">Bir projedeki başvuruları yönetme</span><span class="sxs-lookup"><span data-stu-id="7fa0e-114">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="7fa0e-115">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="7fa0e-115">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [<span data-ttu-id="7fa0e-116">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="7fa0e-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="7fa0e-117">Bozuk Başvurularda Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="7fa0e-117">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
