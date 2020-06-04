---
title: "'<assemblyidentity>' türünü içeren '<typename>' derlemesi için başvuru gerekiyordu, ancak '<projectname1>' ile '<projectname2>' projeleri arasındaki belirsizlik nedeniyle uygun bir başvuru bulunamadı"
ms.date: 07/20/2015
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords:
- BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
ms.openlocfilehash: 4b9f74f0627268752b0ba3c3816fe9d4cc8a231b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404829"
---
# <a name="reference-required-to-assembly-assemblyidentity-containing-type-typename-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-projectname1-and-projectname2"></a><span data-ttu-id="3b9cd-102">'\<assemblyidentity>' türünü içeren '\<typename>' derlemesi için başvuru gerekiyordu, ancak '\<projectname1>' ile '\<projectname2>' projeleri arasındaki belirsizlik nedeniyle uygun bir başvuru bulunamadı</span><span class="sxs-lookup"><span data-stu-id="3b9cd-102">Reference required to assembly '\<assemblyidentity>' containing type '\<typename>', but a suitable reference could not be found due to ambiguity between projects '\<projectname1>' and '\<projectname2>'</span></span>
<span data-ttu-id="3b9cd-103">Bir ifade, projenizin dışında tanımlanan bir sınıf, yapı, arabirim, numaralandırma veya temsilci gibi bir tür kullanır.</span><span class="sxs-lookup"><span data-stu-id="3b9cd-103">An expression uses a type, such as a class, structure, interface, enumeration, or delegate, that is defined outside your project.</span></span> <span data-ttu-id="3b9cd-104">Ancak, bu türü tanımlayan birden fazla derlemeye proje başvuruları vardır.</span><span class="sxs-lookup"><span data-stu-id="3b9cd-104">However, you have project references to more than one assembly defining that type.</span></span>  
  
 <span data-ttu-id="3b9cd-105">Alıntı yapılan projeler aynı ada sahip derlemeler üretir.</span><span class="sxs-lookup"><span data-stu-id="3b9cd-105">The cited projects produce assemblies with the same name.</span></span> <span data-ttu-id="3b9cd-106">Bu nedenle, derleyici eriştiğiniz tür için hangi derlemeyi kullanacağınızı belirleyemez.</span><span class="sxs-lookup"><span data-stu-id="3b9cd-106">Therefore, the compiler cannot determine which assembly to use for the type you are accessing.</span></span>  
  
 <span data-ttu-id="3b9cd-107">Başka bir derlemede tanımlı bir türe erişmek için, Visual Basic derleyicisinin bu derlemeye bir başvurusu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3b9cd-107">To access a type defined in another assembly, the Visual Basic compiler must have a reference to that assembly.</span></span> <span data-ttu-id="3b9cd-108">Bu, projeler arasında döngüsel başvurulara neden olmayan tek, belirsiz bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3b9cd-108">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>  
  
 <span data-ttu-id="3b9cd-109">**Hata kimliği:** BC30969</span><span class="sxs-lookup"><span data-stu-id="3b9cd-109">**Error ID:** BC30969</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3b9cd-110">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="3b9cd-110">To correct this error</span></span>  
  
1. <span data-ttu-id="3b9cd-111">Projenizin başvurması için en iyi derlemeyi hangi projenin ürettiğini belirleme.</span><span class="sxs-lookup"><span data-stu-id="3b9cd-111">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="3b9cd-112">Bu karar için dosya erişiminin ve güncelleştirme sıklığının kolaylığı gibi ölçütleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b9cd-112">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>  
  
2. <span data-ttu-id="3b9cd-113">Proje özelliklerinde, kullanmakta olduğunuz türü tanımlayan derlemeyi içeren dosyaya bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3b9cd-113">In your project properties, add a reference to the file that contains the assembly that defines the type you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b9cd-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b9cd-114">See also</span></span>

- [<span data-ttu-id="3b9cd-115">Bir projedeki başvuruları yönetme</span><span class="sxs-lookup"><span data-stu-id="3b9cd-115">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="3b9cd-116">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="3b9cd-116">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [<span data-ttu-id="3b9cd-117">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="3b9cd-117">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="3b9cd-118">Bozuk Başvurularda Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="3b9cd-118">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
