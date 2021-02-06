---
description: "Hakkında daha fazla bilgi edinin: BC30961: ' ' türünün değeri <typename1> ' ' olarak dönüştürülemez <typename2> (birden fazla dosya başvurusu)"
title: "'<typename1>' türünün değeri '<typename2>' olarak dönüştürülemez (Birden fazla dosya başvurusu)"
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 77f8f3c500f9f395d3998261a218175e49f0f52b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640868"
---
# <a name="bc30961-value-of-type-typename1-cannot-be-converted-to-typename2-multiple-file-references"></a><span data-ttu-id="db5ce-103">BC30961: ' ' türünün değeri \<typename1> ' ' olarak dönüştürülemez \<typename2> (birden fazla dosya başvurusu)</span><span class="sxs-lookup"><span data-stu-id="db5ce-103">BC30961: Value of type '\<typename1>' cannot be converted to '\<typename2>' (Multiple file references)</span></span>

<span data-ttu-id="db5ce-104">' ' Türünün değeri \<typename1> ' ' olarak dönüştürülemez \<typename2> .</span><span class="sxs-lookup"><span data-stu-id="db5ce-104">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="db5ce-105">' ' Projesindeki ' ' \<filepath1> \<projectname1> öğesine bir dosya başvurusu olan ' ' projesindeki ' ' öğesine bir dosya başvurusu karıştırılması nedeniyle tür uyumsuzluğu olabilir \<filepath2> \<projectname2> .</span><span class="sxs-lookup"><span data-stu-id="db5ce-105">Type mismatch could be due to mixing a file reference to '\<filepath1>' in project '\<projectname1>' with a file reference to '\<filepath2>' in project '\<projectname2>'.</span></span> <span data-ttu-id="db5ce-106">Her iki derleme de aynıysa, bu başvuruları her iki başvuruyu da aynı konumdan değiştirmeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="db5ce-106">If both assemblies are identical, try replacing these references so both references are from the same location.</span></span>

 <span data-ttu-id="db5ce-107">Bir projenin bir derlemeye birden fazla dosya başvurusu yaptığı durumlarda, derleyici bir türün diğerine dönüştürülebileceğini garanti edemez.</span><span class="sxs-lookup"><span data-stu-id="db5ce-107">In a situation where a project makes more than one file reference to an assembly, the compiler cannot guarantee that one type can be converted to another.</span></span>

 <span data-ttu-id="db5ce-108">Her dosya başvurusu, bir projenin çıkış dosyası (genellikle bir DLL dosyası) için bir dosya yolu ve adı belirtir.</span><span class="sxs-lookup"><span data-stu-id="db5ce-108">Each file reference specifies a file path and name for the output file of a project (typically a DLL file).</span></span> <span data-ttu-id="db5ce-109">Derleyici, çıkış dosyalarının aynı kaynaktan gelmesini veya aynı derlemenin aynı sürümünü temsil ettiğini garanti edemez.</span><span class="sxs-lookup"><span data-stu-id="db5ce-109">The compiler cannot guarantee that the output files come from the same source, or that they represent the same version of the same assembly.</span></span> <span data-ttu-id="db5ce-110">Bu nedenle, farklı başvurularda bulunan türlerin aynı türde veya hatta diğeri diğerine dönüştürülebileceğinizin garantisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="db5ce-110">Therefore, it cannot guarantee that the types in the different references are the same type, or even that one can be converted to the other.</span></span>

 <span data-ttu-id="db5ce-111">Başvurulan derlemelerin aynı derleme kimliğine sahip olduğunu biliyorsanız, tek bir dosya başvurusu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db5ce-111">You can use a single file reference if you know that the referenced assemblies have the same assembly identity.</span></span> <span data-ttu-id="db5ce-112">*Derleme kimliği* , derleme adı, sürümü, varsa ortak anahtar ve kültür içerir.</span><span class="sxs-lookup"><span data-stu-id="db5ce-112">The *assembly identity* includes the assembly's name, version, public key if any, and culture.</span></span> <span data-ttu-id="db5ce-113">Bu bilgiler derlemeyi benzersiz şekilde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="db5ce-113">This information uniquely identifies the assembly.</span></span>

 <span data-ttu-id="db5ce-114">**Hata kimliği:** BC30961</span><span class="sxs-lookup"><span data-stu-id="db5ce-114">**Error ID:** BC30961</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="db5ce-115">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="db5ce-115">To correct this error</span></span>

- <span data-ttu-id="db5ce-116">Başvurulan derlemeler aynı derleme kimliğine sahip ise, yalnızca tek bir dosya başvurusu olacak şekilde dosya başvurularından birini kaldırın veya değiştirin.</span><span class="sxs-lookup"><span data-stu-id="db5ce-116">If the referenced assemblies have the same assembly identity, then remove or replace one of the file references so that there is only a single file reference.</span></span>

- <span data-ttu-id="db5ce-117">Başvurulan derlemeler aynı derleme kimliğine sahip değilse, bir türü birindeki bir türe dönüştürmeye çalışmayacak şekilde kodunuzu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="db5ce-117">If the referenced assemblies do not have the same assembly identity, then change your code so that it does not attempt to convert a type in one to a type in the other.</span></span>

## <a name="see-also"></a><span data-ttu-id="db5ce-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db5ce-118">See also</span></span>

- [<span data-ttu-id="db5ce-119">Visual Basic'de Tür Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="db5ce-119">Type Conversions in Visual Basic</span></span>](../../programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="db5ce-120">Bir projedeki başvuruları yönetme</span><span class="sxs-lookup"><span data-stu-id="db5ce-120">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
