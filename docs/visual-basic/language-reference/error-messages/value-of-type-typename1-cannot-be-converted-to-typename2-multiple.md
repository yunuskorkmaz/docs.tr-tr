---
title: Türü değeri &#39; &lt;typename1&gt; &#39; dönüştürülemez &#39; &lt;typename2&gt; &#39; (birden fazla dosya başvurusu)
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 943b9612a9217b90c19f34285e812c4e1cccf81a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54691383"
---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39-multiple-file-references"></a><span data-ttu-id="8718c-102">Türü değeri &#39; &lt;typename1&gt; &#39; dönüştürülemez &#39; &lt;typename2&gt; &#39; (birden fazla dosya başvurusu)</span><span class="sxs-lookup"><span data-stu-id="8718c-102">Value of type &#39;&lt;typename1&gt;&#39; cannot be converted to &#39;&lt;typename2&gt;&#39; (Multiple file references)</span></span>
<span data-ttu-id="8718c-103">Türünün değeri '\<typename1 >' olarak değiştirilemez '\<typename2 >'.</span><span class="sxs-lookup"><span data-stu-id="8718c-103">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="8718c-104">Bir dosya başvurusu karışması tür uyuşmazlığı olabilir '\<filepath1 >' projesindeki '\<projectname1 >' için bir dosya başvurusu ile '\<filepath2 >' projesindeki '\<projectname2 >'.</span><span class="sxs-lookup"><span data-stu-id="8718c-104">Type mismatch could be due to mixing a file reference to '\<filepath1>' in project '\<projectname1>' with a file reference to '\<filepath2>' in project '\<projectname2>'.</span></span> <span data-ttu-id="8718c-105">İki derleme de aynıysa, bu başvuruları her iki başvuru aynı konumdan olacak şekilde değiştirmeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="8718c-105">If both assemblies are identical, try replacing these references so both references are from the same location.</span></span>  
  
 <span data-ttu-id="8718c-106">Burada bir derlemeyi birden fazla dosya başvurusu bir proje yapar bir durumda, derleyici bir türden diğerine dönüştürülüp dönüştürülemeyeceği garanti edemez.</span><span class="sxs-lookup"><span data-stu-id="8718c-106">In a situation where a project makes more than one file reference to an assembly, the compiler cannot guarantee that one type can be converted to another.</span></span>  
  
 <span data-ttu-id="8718c-107">Her dosya başvurusu bir dosya yolu ve adı (genellikle bir DLL dosyası) projenin çıkış dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8718c-107">Each file reference specifies a file path and name for the output file of a project (typically a DLL file).</span></span> <span data-ttu-id="8718c-108">Derleyici çıktı dosyaları aynı kaynaktan gelen veya aynı bütünleştirilmiş kodun aynı sürümü temsil ettiğini garanti edemez.</span><span class="sxs-lookup"><span data-stu-id="8718c-108">The compiler cannot guarantee that the output files come from the same source, or that they represent the same version of the same assembly.</span></span> <span data-ttu-id="8718c-109">Bu nedenle, farklı başvuruları türleri aynı türdeyse veya hatta bir diğerine dönüştürülebilir belirleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="8718c-109">Therefore, it cannot guarantee that the types in the different references are the same type, or even that one can be converted to the other.</span></span>  
  
 <span data-ttu-id="8718c-110">Başvurulan derlemeler aynı derleme kimliğine sahip olduğunu biliyorsanız, tek bir dosya başvurusu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8718c-110">You can use a single file reference if you know that the referenced assemblies have the same assembly identity.</span></span> <span data-ttu-id="8718c-111">*Derleme kimliği* derlemenin adı, sürümü, ortak anahtar varsa ve kültür içerir.</span><span class="sxs-lookup"><span data-stu-id="8718c-111">The *assembly identity* includes the assembly's name, version, public key if any, and culture.</span></span> <span data-ttu-id="8718c-112">Bu bilgiler derlemenin benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8718c-112">This information uniquely identifies the assembly.</span></span>  
  
 <span data-ttu-id="8718c-113">**Hata Kimliği:** BC30961</span><span class="sxs-lookup"><span data-stu-id="8718c-113">**Error ID:** BC30961</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8718c-114">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="8718c-114">To correct this error</span></span>  
  
-   <span data-ttu-id="8718c-115">Başvurulan derlemeler aynı derleme kimliği varsa, kaldırın veya yalnızca tek bir dosya başvurusu yani dosya başvurulardan birini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="8718c-115">If the referenced assemblies have the same assembly identity, then remove or replace one of the file references so that there is only a single file reference.</span></span>  
  
-   <span data-ttu-id="8718c-116">Başvurulan derlemeler aynı derleme kimliği yoksa, diğer bir tür için tür dönüştürme denemez sonra kodunuzu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="8718c-116">If the referenced assemblies do not have the same assembly identity, then change your code so that it does not attempt to convert a type in one to a type in the other.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8718c-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8718c-117">See also</span></span>
- [<span data-ttu-id="8718c-118">Visual Basic'de tür dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="8718c-118">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="8718c-119">Bir projedeki başvuruları yönetme</span><span class="sxs-lookup"><span data-stu-id="8718c-119">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)

