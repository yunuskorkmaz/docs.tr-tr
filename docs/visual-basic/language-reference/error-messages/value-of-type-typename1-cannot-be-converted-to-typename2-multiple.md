---
title: "Değer türü &#39; &lt;typename1&gt;&#39; dönüştürülemiyor &#39;&lt; TypeName2&gt;&#39; (Birden çok dosya başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords: BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cc6138c7a7ca7d50a56fdd1f536e8d2dc3462a08
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39-multiple-file-references"></a><span data-ttu-id="476b4-102">Değer türü &#39; &lt;typename1&gt;&#39; dönüştürülemiyor &#39;&lt; TypeName2&gt;&#39; (Birden çok dosya başvurusu)</span><span class="sxs-lookup"><span data-stu-id="476b4-102">Value of type &#39;&lt;typename1&gt;&#39; cannot be converted to &#39;&lt;typename2&gt;&#39; (Multiple file references)</span></span>
<span data-ttu-id="476b4-103">Türündeki değeri '\<typename1 >' şekilde dönüştürülemeyen '\<typename2 >'.</span><span class="sxs-lookup"><span data-stu-id="476b4-103">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="476b4-104">Tür uyuşmazlığı dosya başvurusu karıştırma nedeniyle olabilir '\<filepath1 >' projesindeki '\<projectname1 >' dosya başvuru '\<filepath2 >' projesindeki '\<projectname2 >'.</span><span class="sxs-lookup"><span data-stu-id="476b4-104">Type mismatch could be due to mixing a file reference to '\<filepath1>' in project '\<projectname1>' with a file reference to '\<filepath2>' in project '\<projectname2>'.</span></span> <span data-ttu-id="476b4-105">Her iki derlemeleri özdeş ise, her iki başvuruları aynı konumdan; bu nedenle bu başvuruları değiştirmeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="476b4-105">If both assemblies are identical, try replacing these references so both references are from the same location.</span></span>  
  
 <span data-ttu-id="476b4-106">Burada bir proje derleme birden fazla dosya başvuru yapar bir durumda, bir tür için başka bir dönüştürülebileceğinden derleyici garanti edemez.</span><span class="sxs-lookup"><span data-stu-id="476b4-106">In a situation where a project makes more than one file reference to an assembly, the compiler cannot guarantee that one type can be converted to another.</span></span>  
  
 <span data-ttu-id="476b4-107">Her dosya başvurusu, bir dosya yolu ve bir proje (genellikle bir DLL dosyası) çıkış dosyasının adı belirtir.</span><span class="sxs-lookup"><span data-stu-id="476b4-107">Each file reference specifies a file path and name for the output file of a project (typically a DLL file).</span></span> <span data-ttu-id="476b4-108">Derleyici çıktı dosyaları aynı kaynaktan geldiği ya da aynı bütünleştirilmiş kodda aynı sürümünü temsil ettiğini garanti edemez.</span><span class="sxs-lookup"><span data-stu-id="476b4-108">The compiler cannot guarantee that the output files come from the same source, or that they represent the same version of the same assembly.</span></span> <span data-ttu-id="476b4-109">Bu nedenle, onu farklı başvuru türlerinde aynı türde olan veya hatta bir diğerine dönüştürülebilir garanti edemez.</span><span class="sxs-lookup"><span data-stu-id="476b4-109">Therefore, it cannot guarantee that the types in the different references are the same type, or even that one can be converted to the other.</span></span>  
  
 <span data-ttu-id="476b4-110">Başvurulan derlemeler aynı derleme kimliğine sahip olduğunu biliyorsanız, tek bir dosya başvuru kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="476b4-110">You can use a single file reference if you know that the referenced assemblies have the same assembly identity.</span></span> <span data-ttu-id="476b4-111">*Derleme kimliği* derlemenin adı, sürüm, ortak anahtar varsa ve kültür içerir.</span><span class="sxs-lookup"><span data-stu-id="476b4-111">The *assembly identity* includes the assembly's name, version, public key if any, and culture.</span></span> <span data-ttu-id="476b4-112">Bu bilgiler, derleme benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="476b4-112">This information uniquely identifies the assembly.</span></span>  
  
 <span data-ttu-id="476b4-113">**Hata Kimliği:** BC30961</span><span class="sxs-lookup"><span data-stu-id="476b4-113">**Error ID:** BC30961</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="476b4-114">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="476b4-114">To correct this error</span></span>  
  
-   <span data-ttu-id="476b4-115">Başvurulan derlemeler aynı derleme kimliğine varsa, kaldırın veya yalnızca tek bir dosya başvuru olmasını sağlamak başvurulara birini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="476b4-115">If the referenced assemblies have the same assembly identity, then remove or replace one of the file references so that there is only a single file reference.</span></span>  
  
-   <span data-ttu-id="476b4-116">Başvurulan derlemeler aynı derleme kimliğine yoksa türü bir diğer türüne dönüştürmek denemez şekilde ardından kodunuzu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="476b4-116">If the referenced assemblies do not have the same assembly identity, then change your code so that it does not attempt to convert a type in one to a type in the other.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="476b4-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="476b4-117">See Also</span></span>  
 [<span data-ttu-id="476b4-118">Visual Basic'de tür dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="476b4-118">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="476b4-119">Bir projedeki başvuruları yönetme</span><span class="sxs-lookup"><span data-stu-id="476b4-119">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)  
 [<span data-ttu-id="476b4-120">NIB nasıl yapılır: başvuru ekleme veya kaldırma Başvuru Ekle iletişim kutusunu kullanarak</span><span class="sxs-lookup"><span data-stu-id="476b4-120">NIB How to: Add or Remove References By Using the Add Reference Dialog Box</span></span>](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)
