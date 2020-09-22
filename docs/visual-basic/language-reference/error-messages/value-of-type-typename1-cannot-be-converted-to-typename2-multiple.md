---
title: "'<typename1>' türünün değeri '<typename2>' olarak dönüştürülemez (Birden fazla dosya başvurusu)"
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 4b74fdc5584fd296d4bbe36034920d4b467dbb7a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875074"
---
# <a name="value-of-type-typename1-cannot-be-converted-to-typename2-multiple-file-references"></a><span data-ttu-id="2a4fd-102">'\<typename1>' türünün değeri '\<typename2>' olarak dönüştürülemez (Birden fazla dosya başvurusu)</span><span class="sxs-lookup"><span data-stu-id="2a4fd-102">Value of type '\<typename1>' cannot be converted to '\<typename2>' (Multiple file references)</span></span>

<span data-ttu-id="2a4fd-103">' ' Türünün değeri \<typename1> ' ' olarak dönüştürülemez \<typename2> .</span><span class="sxs-lookup"><span data-stu-id="2a4fd-103">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="2a4fd-104">' ' Projesindeki ' ' \<filepath1> \<projectname1> öğesine bir dosya başvurusu olan ' ' projesindeki ' ' öğesine bir dosya başvurusu karıştırılması nedeniyle tür uyumsuzluğu olabilir \<filepath2> \<projectname2> .</span><span class="sxs-lookup"><span data-stu-id="2a4fd-104">Type mismatch could be due to mixing a file reference to '\<filepath1>' in project '\<projectname1>' with a file reference to '\<filepath2>' in project '\<projectname2>'.</span></span> <span data-ttu-id="2a4fd-105">Her iki derleme de aynıysa, bu başvuruları her iki başvuruyu da aynı konumdan değiştirmeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="2a4fd-105">If both assemblies are identical, try replacing these references so both references are from the same location.</span></span>  
  
 <span data-ttu-id="2a4fd-106">Bir projenin bir derlemeye birden fazla dosya başvurusu yaptığı durumlarda, derleyici bir türün diğerine dönüştürülebileceğini garanti edemez.</span><span class="sxs-lookup"><span data-stu-id="2a4fd-106">In a situation where a project makes more than one file reference to an assembly, the compiler cannot guarantee that one type can be converted to another.</span></span>  
  
 <span data-ttu-id="2a4fd-107">Her dosya başvurusu, bir projenin çıkış dosyası (genellikle bir DLL dosyası) için bir dosya yolu ve adı belirtir.</span><span class="sxs-lookup"><span data-stu-id="2a4fd-107">Each file reference specifies a file path and name for the output file of a project (typically a DLL file).</span></span> <span data-ttu-id="2a4fd-108">Derleyici, çıkış dosyalarının aynı kaynaktan gelmesini veya aynı derlemenin aynı sürümünü temsil ettiğini garanti edemez.</span><span class="sxs-lookup"><span data-stu-id="2a4fd-108">The compiler cannot guarantee that the output files come from the same source, or that they represent the same version of the same assembly.</span></span> <span data-ttu-id="2a4fd-109">Bu nedenle, farklı başvurularda bulunan türlerin aynı türde veya hatta diğeri diğerine dönüştürülebileceğinizin garantisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="2a4fd-109">Therefore, it cannot guarantee that the types in the different references are the same type, or even that one can be converted to the other.</span></span>  
  
 <span data-ttu-id="2a4fd-110">Başvurulan derlemelerin aynı derleme kimliğine sahip olduğunu biliyorsanız, tek bir dosya başvurusu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a4fd-110">You can use a single file reference if you know that the referenced assemblies have the same assembly identity.</span></span> <span data-ttu-id="2a4fd-111">*Derleme kimliği* , derleme adı, sürümü, varsa ortak anahtar ve kültür içerir.</span><span class="sxs-lookup"><span data-stu-id="2a4fd-111">The *assembly identity* includes the assembly's name, version, public key if any, and culture.</span></span> <span data-ttu-id="2a4fd-112">Bu bilgiler derlemeyi benzersiz şekilde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2a4fd-112">This information uniquely identifies the assembly.</span></span>  
  
 <span data-ttu-id="2a4fd-113">**Hata kimliği:** BC30961</span><span class="sxs-lookup"><span data-stu-id="2a4fd-113">**Error ID:** BC30961</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2a4fd-114">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="2a4fd-114">To correct this error</span></span>  
  
- <span data-ttu-id="2a4fd-115">Başvurulan derlemeler aynı derleme kimliğine sahip ise, yalnızca tek bir dosya başvurusu olacak şekilde dosya başvurularından birini kaldırın veya değiştirin.</span><span class="sxs-lookup"><span data-stu-id="2a4fd-115">If the referenced assemblies have the same assembly identity, then remove or replace one of the file references so that there is only a single file reference.</span></span>  
  
- <span data-ttu-id="2a4fd-116">Başvurulan derlemeler aynı derleme kimliğine sahip değilse, bir türü birindeki bir türe dönüştürmeye çalışmayacak şekilde kodunuzu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="2a4fd-116">If the referenced assemblies do not have the same assembly identity, then change your code so that it does not attempt to convert a type in one to a type in the other.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a4fd-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a4fd-117">See also</span></span>

- [<span data-ttu-id="2a4fd-118">Visual Basic'de Tür Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="2a4fd-118">Type Conversions in Visual Basic</span></span>](../../programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="2a4fd-119">Bir projedeki başvuruları yönetme</span><span class="sxs-lookup"><span data-stu-id="2a4fd-119">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
