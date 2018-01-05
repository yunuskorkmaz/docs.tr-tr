---
title: "&lt;İleti&gt; bu hata, ayrıca bir proje başvurusu derleme &#39; dosya başvurusuyla karıştırılması nedeniyle olabilir&lt; AssemblyName&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords: BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0fcbcc48928b1b03487f31930e3d14051ddd990a
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="ltmessagegt-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-39ltassemblynamegt39"></a><span data-ttu-id="69e5d-102">&lt;İleti&gt; bu hata, ayrıca bir proje başvurusu derleme &#39; dosya başvurusuyla karıştırılması nedeniyle olabilir&lt; AssemblyName&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="69e5d-102">&lt;message&gt; This error could also be due to mixing a file reference with a project reference to assembly &#39;&lt;assemblyname&gt;&#39;</span></span>
<span data-ttu-id="69e5d-103">\<İleti > Bu hata, ayrıca bir proje başvurusu derleme dosyası başvurusuyla karıştırılması nedeniyle olabilir '\<assemblyname >.</span><span class="sxs-lookup"><span data-stu-id="69e5d-103">\<message> This error could also be due to mixing a file reference with a project reference to assembly '\<assemblyname>.</span></span> <span data-ttu-id="69e5d-104">Bu durumda, dosya başvurusunu değiştirmeyi deneyin '\<assemblyfilename >' projesindeki '\<projectname1 >' proje başvuru '\<projectname2 >'.</span><span class="sxs-lookup"><span data-stu-id="69e5d-104">In this case, try replacing the file reference to '\<assemblyfilename>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>  
  
 <span data-ttu-id="69e5d-105">Projenizdeki kod erişen başka bir projeye üyesi ancak çözümünüz yapılandırılmasına izin vermez [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] derleyici başvurusu çözümlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="69e5d-105">Code in your project accesses a member of another project, but the configuration of your solution does not allow the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler to resolve the reference.</span></span>  
  
 <span data-ttu-id="69e5d-106">Başka bir derlemede tanımlanan bir türü erişmek için [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] derleyici, bu derleme başvurusu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="69e5d-106">To access a type defined in another assembly, the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler must have a reference to that assembly.</span></span> <span data-ttu-id="69e5d-107">Bu, projeler arasında döngüsel başvuru neden olmaz tek ve anlaşılır bir başvurusu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="69e5d-107">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>  
  
 <span data-ttu-id="69e5d-108">**Hata Kimliği:** BC30971</span><span class="sxs-lookup"><span data-stu-id="69e5d-108">**Error ID:** BC30971</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="69e5d-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="69e5d-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="69e5d-110">Başvurmak için en iyi derleme projeniz için hangi proje üreten belirler.</span><span class="sxs-lookup"><span data-stu-id="69e5d-110">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="69e5d-111">Bu karar, dosya erişim kolaylığı ve güncelleştirme sıklığını gibi ölçütlere kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="69e5d-111">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>  
  
2.  <span data-ttu-id="69e5d-112">Proje Özellikleri'nde, kullanmakta olduğunuz türü tanımlayan derleme içeren projesine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="69e5d-112">In your project properties, add a reference to the project that contains the assembly that defines the type you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69e5d-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="69e5d-113">See Also</span></span>  
 [<span data-ttu-id="69e5d-114">Bir projedeki başvuruları yönetme</span><span class="sxs-lookup"><span data-stu-id="69e5d-114">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)  
 [<span data-ttu-id="69e5d-115">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="69e5d-115">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
   
 [<span data-ttu-id="69e5d-116">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="69e5d-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 [<span data-ttu-id="69e5d-117">Bozuk Başvurularda Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="69e5d-117">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
