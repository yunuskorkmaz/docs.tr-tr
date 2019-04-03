---
title: "'<typename1>' türünün değeri '<typename2>' olarak değiştirilemez"
ms.date: 07/20/2015
f1_keywords:
- vbc30955
- bc30955
helpviewer_keywords:
- BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
ms.openlocfilehash: 5f313a43bc3a2f983dabbd45477d120fdb80d063
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58829035"
---
# <a name="value-of-type-typename1-cannot-be-converted-to-typename2"></a><span data-ttu-id="6d4be-102">Türünün değeri '\<typename1 >' olarak değiştirilemez '\<typename2 >'</span><span class="sxs-lookup"><span data-stu-id="6d4be-102">Value of type '\<typename1>' cannot be converted to '\<typename2>'</span></span>
<span data-ttu-id="6d4be-103">Türünün değeri '\<typename1 >' olarak değiştirilemez '\<typename2 >'.</span><span class="sxs-lookup"><span data-stu-id="6d4be-103">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="6d4be-104">Derleme bir proje başvurusu olan bir dosya başvurusunun karışması tür uyuşmazlığı olabilir '\<assemblyname >'.</span><span class="sxs-lookup"><span data-stu-id="6d4be-104">Type mismatch could be due to the mixing of a file reference with a project reference to assembly '\<assemblyname>'.</span></span> <span data-ttu-id="6d4be-105">Dosya başvurusu değiştirmeyi deneyin '\<DosyaYolu >' projesinde '\<projectname1 >' proje başvurusu ile '\<projectname2 >'.</span><span class="sxs-lookup"><span data-stu-id="6d4be-105">Try replacing the file reference to '\<filepath>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>  
  
 <span data-ttu-id="6d4be-106">Bir proje, hem bir proje başvurusu hem de bir dosya başvurusu burada yapar bir durumda, derleyici bir türden diğerine dönüştürülüp dönüştürülemeyeceği garanti edemez.</span><span class="sxs-lookup"><span data-stu-id="6d4be-106">In a situation where a project makes both a project reference and a file reference, the compiler cannot guarantee that one type can be converted to another.</span></span>  
  
 <span data-ttu-id="6d4be-107">Bu hatayı oluşturan durumu aşağıdaki sözde kod gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6d4be-107">The following pseudo-code illustrates a situation that can generate this error.</span></span>  
  
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
  
 <span data-ttu-id="6d4be-108">Proje `P1` bir proje aracılığıyla dolaylı proje başvuru yapar `P2` projesine `P3`ve ayrıca doğrudan bir dosya başvurusu `P3`.</span><span class="sxs-lookup"><span data-stu-id="6d4be-108">Project `P1` makes an indirect project reference through project `P2` to project `P3`, and also a direct file reference to `P3`.</span></span> <span data-ttu-id="6d4be-109">Bildirimi `commonObject` dosya başvurur `P3`, while çağrısı `P2.getCommonClass` proje başvurur `P3`.</span><span class="sxs-lookup"><span data-stu-id="6d4be-109">The declaration of `commonObject` uses the file reference to `P3`, while the call to `P2.getCommonClass` uses the project reference to `P3`.</span></span>  
  
 <span data-ttu-id="6d4be-110">Dosya başvurusu bir dosya yolu ve çıkış dosyasının adını belirtir, bu durum sorun olduğunu `P3` (genellikle p3.dll) kaynak projenin proje başvurularını tanımlamak sırada (`P3`) tarafından proje adı.</span><span class="sxs-lookup"><span data-stu-id="6d4be-110">The problem in this situation is that the file reference specifies a file path and name for the output file of `P3` (typically p3.dll), while the project references identify the source project (`P3`) by project name.</span></span> <span data-ttu-id="6d4be-111">Bu nedenle, derleyici bu tür garanti edemez `P3.commonClass` aynı kaynak kodunun iki farklı başvuruları ile gelir.</span><span class="sxs-lookup"><span data-stu-id="6d4be-111">Because of this, the compiler cannot guarantee that the type `P3.commonClass` comes from the same source code through the two different references.</span></span>  
  
 <span data-ttu-id="6d4be-112">Bu durum genellikle ortaya başvurular'ne zaman proje ve dosya başvuruları karma.</span><span class="sxs-lookup"><span data-stu-id="6d4be-112">This situation typically occurs when project references and file references are mixed.</span></span> <span data-ttu-id="6d4be-113">Önceki çizimde, sorun oluşmaz `P1` doğrudan proje başvurusu yapılan `P3` yerine dosya başvurusu.</span><span class="sxs-lookup"><span data-stu-id="6d4be-113">In the preceding illustration, the problem would not occur if `P1` made a direct project reference to `P3` instead of a file reference.</span></span>  
  
 <span data-ttu-id="6d4be-114">**Hata Kimliği:** BC30955</span><span class="sxs-lookup"><span data-stu-id="6d4be-114">**Error ID:** BC30955</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6d4be-115">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="6d4be-115">To correct this error</span></span>  
  
-   <span data-ttu-id="6d4be-116">Dosya başvurusu bir proje başvurusu olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6d4be-116">Change the file reference to a project reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d4be-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d4be-117">See also</span></span>

- [<span data-ttu-id="6d4be-118">Visual Basic'de tür dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="6d4be-118">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="6d4be-119">Bir projedeki başvuruları yönetme</span><span class="sxs-lookup"><span data-stu-id="6d4be-119">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
