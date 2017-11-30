---
title: "Derleme &#39;için gereken başvuru; &lt;assemblyIdentity&gt;&#39; içeren türü &#39;&lt; TypeName&gt;&#39; ancak uygun bir başvuru projeleri &#39; arasındaki belirsizlik nedeniyle bulunamadı&lt; projectname1&gt;&#39; ve &#39;&lt; projectname2&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords: BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 04a1b16a10d2a3945d1efbe3a2bd0850f1da39fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="reference-required-to-assembly-39ltassemblyidentitygt39-containing-type-39lttypenamegt39-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-39ltprojectname1gt39-and-39ltprojectname2gt39"></a><span data-ttu-id="2336c-102">Derleme &#39;için gereken başvuru; &lt;assemblyIdentity&gt;&#39; içeren türü &#39;&lt; TypeName&gt;&#39; ancak uygun bir başvuru projeleri &#39; arasındaki belirsizlik nedeniyle bulunamadı&lt; projectname1&gt;&#39; ve &#39;&lt; projectname2&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="2336c-102">Reference required to assembly &#39;&lt;assemblyidentity&gt;&#39; containing type &#39;&lt;typename&gt;&#39;, but a suitable reference could not be found due to ambiguity between projects &#39;&lt;projectname1&gt;&#39; and &#39;&lt;projectname2&gt;&#39;</span></span>
<span data-ttu-id="2336c-103">Sınıfı, yapısı, arabirim, numaralandırma veya projenizin dışında tanımlı temsilci, gibi bir tür bir ifade kullanır.</span><span class="sxs-lookup"><span data-stu-id="2336c-103">An expression uses a type, such as a class, structure, interface, enumeration, or delegate, that is defined outside your project.</span></span> <span data-ttu-id="2336c-104">Ancak, birden fazla derleme bu türünü tanımlamak için proje başvuruları sahip.</span><span class="sxs-lookup"><span data-stu-id="2336c-104">However, you have project references to more than one assembly defining that type.</span></span>  
  
 <span data-ttu-id="2336c-105">Alıntı projeleri aynı ada sahip derlemeler üretir.</span><span class="sxs-lookup"><span data-stu-id="2336c-105">The cited projects produce assemblies with the same name.</span></span> <span data-ttu-id="2336c-106">Bu nedenle, derleyicinin türü için kullanmak üzere hangi derleme erişme belirleyemiyor.</span><span class="sxs-lookup"><span data-stu-id="2336c-106">Therefore, the compiler cannot determine which assembly to use for the type you are accessing.</span></span>  
  
 <span data-ttu-id="2336c-107">Başka bir derlemede tanımlanan bir türü erişmek için [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] derleyici, bu derleme başvurusu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2336c-107">To access a type defined in another assembly, the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler must have a reference to that assembly.</span></span> <span data-ttu-id="2336c-108">Bu, projeler arasında döngüsel başvuru neden olmaz tek ve anlaşılır bir başvurusu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2336c-108">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>  
  
 <span data-ttu-id="2336c-109">**Hata Kimliği:** BC30969</span><span class="sxs-lookup"><span data-stu-id="2336c-109">**Error ID:** BC30969</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2336c-110">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="2336c-110">To correct this error</span></span>  
  
1.  <span data-ttu-id="2336c-111">Başvurmak için en iyi derleme projeniz için hangi proje üreten belirler.</span><span class="sxs-lookup"><span data-stu-id="2336c-111">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="2336c-112">Bu karar, dosya erişim kolaylığı ve güncelleştirme sıklığını gibi ölçütlere kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="2336c-112">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>  
  
2.  <span data-ttu-id="2336c-113">Proje Özellikleri'nde, kullanmakta olduğunuz türü tanımlayan derleme içeren dosyaya bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2336c-113">In your project properties, add a reference to the file that contains the assembly that defines the type you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2336c-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2336c-114">See Also</span></span>  
 [<span data-ttu-id="2336c-115">Bir projedeki başvuruları yönetme</span><span class="sxs-lookup"><span data-stu-id="2336c-115">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)  
 [<span data-ttu-id="2336c-116">Bildirilmiş öğelere başvurular</span><span class="sxs-lookup"><span data-stu-id="2336c-116">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="2336c-117">NIB nasıl yapılır: başvuru ekleme veya kaldırma Başvuru Ekle iletişim kutusunu kullanarak</span><span class="sxs-lookup"><span data-stu-id="2336c-117">NIB How to: Add or Remove References By Using the Add Reference Dialog Box</span></span>](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)  
 [<span data-ttu-id="2336c-118">Proje ve çözüm özelliklerini yönetme</span><span class="sxs-lookup"><span data-stu-id="2336c-118">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 [<span data-ttu-id="2336c-119">Bozuk başvurularda sorun giderme</span><span class="sxs-lookup"><span data-stu-id="2336c-119">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
