---
description: "Hakkında daha fazla bilgi edinin: BC30955: ' ' türünün değeri <typename1> ' olarak dönüştürülemez<typename2>"
title: "'<typename1>' türünün değeri '<typename2>' olarak değiştirilemez"
ms.date: 07/20/2015
f1_keywords:
- vbc30955
- bc30955
helpviewer_keywords:
- BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
ms.openlocfilehash: e03201d5dbb84faf06b7acbe42fe6b3bb4272ab9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666257"
---
# <a name="bc30955-value-of-type-typename1-cannot-be-converted-to-typename2"></a><span data-ttu-id="7eca9-103">BC30955: ' ' türünün değeri \<typename1> ' ' olarak dönüştürülemez \<typename2></span><span class="sxs-lookup"><span data-stu-id="7eca9-103">BC30955: Value of type '\<typename1>' cannot be converted to '\<typename2>'</span></span>

<span data-ttu-id="7eca9-104">' ' Türünün değeri \<typename1> ' ' olarak dönüştürülemez \<typename2> .</span><span class="sxs-lookup"><span data-stu-id="7eca9-104">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="7eca9-105">Tür uyumsuzluğu, ' ' derlemesine bir proje başvurusuyla bir dosya başvurusunun karıştırılması nedeniyle olabilir \<assemblyname> .</span><span class="sxs-lookup"><span data-stu-id="7eca9-105">Type mismatch could be due to the mixing of a file reference with a project reference to assembly '\<assemblyname>'.</span></span> <span data-ttu-id="7eca9-106">' ' Projesindeki ' ' adlı dosya başvurusunu ' ' \<filepath> \<projectname1> için bir proje başvurusuyla değiştirmeyi deneyin \<projectname2> .</span><span class="sxs-lookup"><span data-stu-id="7eca9-106">Try replacing the file reference to '\<filepath>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>

 <span data-ttu-id="7eca9-107">Bir projenin hem bir proje başvurusu hem de bir dosya başvurusu yaptığı durumlarda, derleyici bir türün diğerine dönüştürülebileceğini garanti edemez.</span><span class="sxs-lookup"><span data-stu-id="7eca9-107">In a situation where a project makes both a project reference and a file reference, the compiler cannot guarantee that one type can be converted to another.</span></span>

 <span data-ttu-id="7eca9-108">Aşağıdaki sözde kod, bu hatayı oluşturabilecek bir durumu gösterir.</span><span class="sxs-lookup"><span data-stu-id="7eca9-108">The following pseudo-code illustrates a situation that can generate this error.</span></span>

 `' ================ Visual Basic project P1 ================`

 `'        P1 makes a PROJECT REFERENCE to project P2`

 `'        and a FILE REFERENCE to project P3.`

 `Public commonObject As P3.commonClass`

 `commonObject = P2.getCommonClass()`

 `' ================ Visual Basic project P2 ================`

 `'        P2 makes a PROJECT REFERENCE to project P3`

 `Public Function getCommonClass() As P3.commonClass`

 `Return New P3.commonClass`

 `End Function`

 `' ================ Visual Basic project P3 ================`

 `Public Class commonClass`

 `End Class`

 <span data-ttu-id="7eca9-109">Project `P1` , proje aracılığıyla dolaylı bir proje başvurusunu `P2` `P3` ve ayrıca öğesine doğrudan bir dosya başvurusu yapar `P3` .</span><span class="sxs-lookup"><span data-stu-id="7eca9-109">Project `P1` makes an indirect project reference through project `P2` to project `P3`, and also a direct file reference to `P3`.</span></span> <span data-ttu-id="7eca9-110">Bildirimi, için `commonObject` Dosya başvurusunu kullanır `P3` , ancak öğesine yapılan çağrı, `P2.getCommonClass` proje başvurusunu kullanır `P3` .</span><span class="sxs-lookup"><span data-stu-id="7eca9-110">The declaration of `commonObject` uses the file reference to `P3`, while the call to `P2.getCommonClass` uses the project reference to `P3`.</span></span>

 <span data-ttu-id="7eca9-111">Bu durumda, dosya başvurusunun çıkış dosyası (genellikle p3.dll) için bir dosya yolu ve adı ve proje, proje `P3` adına göre kaynak projeyi ( `P3` ) tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7eca9-111">The problem in this situation is that the file reference specifies a file path and name for the output file of `P3` (typically p3.dll), while the project references identify the source project (`P3`) by project name.</span></span> <span data-ttu-id="7eca9-112">Bu nedenle, derleyici türün `P3.commonClass` iki farklı başvuru aracılığıyla aynı kaynak kodundan geldiğini garanti edemez.</span><span class="sxs-lookup"><span data-stu-id="7eca9-112">Because of this, the compiler cannot guarantee that the type `P3.commonClass` comes from the same source code through the two different references.</span></span>

 <span data-ttu-id="7eca9-113">Bu durum genellikle proje başvuruları ve dosya başvuruları karmaysa oluşur.</span><span class="sxs-lookup"><span data-stu-id="7eca9-113">This situation typically occurs when project references and file references are mixed.</span></span> <span data-ttu-id="7eca9-114">Önceki çizimde, `P1` `P3` bir dosya başvurusu yerine öğesine doğrudan proje başvurusu yapıldıysa sorun oluşmaz.</span><span class="sxs-lookup"><span data-stu-id="7eca9-114">In the preceding illustration, the problem would not occur if `P1` made a direct project reference to `P3` instead of a file reference.</span></span>

 <span data-ttu-id="7eca9-115">**Hata kimliği:** BC30955</span><span class="sxs-lookup"><span data-stu-id="7eca9-115">**Error ID:** BC30955</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="7eca9-116">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="7eca9-116">To correct this error</span></span>

- <span data-ttu-id="7eca9-117">Dosya başvurusunu bir proje başvurusuyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7eca9-117">Change the file reference to a project reference.</span></span>

## <a name="see-also"></a><span data-ttu-id="7eca9-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7eca9-118">See also</span></span>

- [<span data-ttu-id="7eca9-119">Visual Basic'de Tür Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="7eca9-119">Type Conversions in Visual Basic</span></span>](../../programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="7eca9-120">Bir projedeki başvuruları yönetme</span><span class="sxs-lookup"><span data-stu-id="7eca9-120">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
