---
description: "Şu konuda daha fazla bilgi edinin: BC30969: ' ' <assemblyidentity> türünü içeren ' ' derlemesine başvuru gerekiyor <typename> , ancak ' <projectname1> ' ve ' ' projeleri arasındaki belirsizlik nedeniyle uygun bir başvuru bulunamadı <projectname2>"
title: "'<assemblyidentity>' türünü içeren '<typename>' derlemesi için başvuru gerekiyordu, ancak '<projectname1>' ile '<projectname2>' projeleri arasındaki belirsizlik nedeniyle uygun bir başvuru bulunamadı"
ms.date: 07/20/2015
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords:
- BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
ms.openlocfilehash: 93713fe2175c303b7d126a7c3d5e33f9990955a1
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481668"
---
# <a name="bc30969-reference-required-to-assembly-assemblyidentity-containing-type-typename-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-projectname1-and-projectname2"></a><span data-ttu-id="629a9-103">BC30969: ' ' türünü içeren ' ' derlemesi için başvuru gerekiyordu \<assemblyidentity> \<typename> , ancak ' \<projectname1> ' ve ' ' projeleri arasındaki belirsizlik nedeniyle uygun bir başvuru bulunamadı \<projectname2></span><span class="sxs-lookup"><span data-stu-id="629a9-103">BC30969: Reference required to assembly '\<assemblyidentity>' containing type '\<typename>', but a suitable reference could not be found due to ambiguity between projects '\<projectname1>' and '\<projectname2>'</span></span>

<span data-ttu-id="629a9-104">Bir ifade, projenizin dışında tanımlanan bir sınıf, yapı, arabirim, numaralandırma veya temsilci gibi bir tür kullanır.</span><span class="sxs-lookup"><span data-stu-id="629a9-104">An expression uses a type, such as a class, structure, interface, enumeration, or delegate, that is defined outside your project.</span></span> <span data-ttu-id="629a9-105">Ancak, bu türü tanımlayan birden fazla derlemeye proje başvuruları vardır.</span><span class="sxs-lookup"><span data-stu-id="629a9-105">However, you have project references to more than one assembly defining that type.</span></span>

 <span data-ttu-id="629a9-106">Alıntı yapılan projeler aynı ada sahip derlemeler üretir.</span><span class="sxs-lookup"><span data-stu-id="629a9-106">The cited projects produce assemblies with the same name.</span></span> <span data-ttu-id="629a9-107">Bu nedenle, derleyici eriştiğiniz tür için hangi derlemeyi kullanacağınızı belirleyemez.</span><span class="sxs-lookup"><span data-stu-id="629a9-107">Therefore, the compiler cannot determine which assembly to use for the type you are accessing.</span></span>

 <span data-ttu-id="629a9-108">Başka bir derlemede tanımlı bir türe erişmek için, Visual Basic derleyicisinin bu derlemeye bir başvurusu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="629a9-108">To access a type defined in another assembly, the Visual Basic compiler must have a reference to that assembly.</span></span> <span data-ttu-id="629a9-109">Bu, projeler arasında döngüsel başvurulara neden olmayan tek, belirsiz bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="629a9-109">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>

 <span data-ttu-id="629a9-110">**Hata kimliği:** BC30969</span><span class="sxs-lookup"><span data-stu-id="629a9-110">**Error ID:** BC30969</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="629a9-111">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="629a9-111">To correct this error</span></span>

1. <span data-ttu-id="629a9-112">Projenizin başvurması için en iyi derlemeyi hangi projenin ürettiğini belirleme.</span><span class="sxs-lookup"><span data-stu-id="629a9-112">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="629a9-113">Bu karar için dosya erişiminin ve güncelleştirme sıklığının kolaylığı gibi ölçütleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="629a9-113">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>

2. <span data-ttu-id="629a9-114">Proje özelliklerinde, kullanmakta olduğunuz türü tanımlayan derlemeyi içeren dosyaya bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="629a9-114">In your project properties, add a reference to the file that contains the assembly that defines the type you are using.</span></span>

## <a name="see-also"></a><span data-ttu-id="629a9-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="629a9-115">See also</span></span>

- [<span data-ttu-id="629a9-116">Bir projedeki başvuruları yönetme</span><span class="sxs-lookup"><span data-stu-id="629a9-116">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="629a9-117">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="629a9-117">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [<span data-ttu-id="629a9-118">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="629a9-118">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="629a9-119">Bozuk Başvurularda Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="629a9-119">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
