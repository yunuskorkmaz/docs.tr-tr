---
title: "Değer türü &#39; &lt;typename1&gt;&#39; dönüştürülemiyor &#39;&lt; TypeName2&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30955
- bc30955
helpviewer_keywords: BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2154a56f9ff004f906cb2b571f8771e74cfca9c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39"></a><span data-ttu-id="8c9dd-102">Değer türü &#39; &lt;typename1&gt;&#39; dönüştürülemiyor &#39;&lt; TypeName2&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="8c9dd-102">Value of type &#39;&lt;typename1&gt;&#39; cannot be converted to &#39;&lt;typename2&gt;&#39;</span></span>
<span data-ttu-id="8c9dd-103">Türündeki değeri '\<typename1 >' şekilde dönüştürülemeyen '\<typename2 >'.</span><span class="sxs-lookup"><span data-stu-id="8c9dd-103">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="8c9dd-104">Tür uyuşmazlığı proje başvurusu derleme dosyası başvurusuyla karıştırılması nedeniyle olabilir '\<assemblyname >'.</span><span class="sxs-lookup"><span data-stu-id="8c9dd-104">Type mismatch could be due to the mixing of a file reference with a project reference to assembly '\<assemblyname>'.</span></span> <span data-ttu-id="8c9dd-105">Dosya başvurusunu değiştirmeyi deneyin '\<filepath >' projesindeki '\<projectname1 >' proje başvuru '\<projectname2 >'.</span><span class="sxs-lookup"><span data-stu-id="8c9dd-105">Try replacing the file reference to '\<filepath>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>  
  
 <span data-ttu-id="8c9dd-106">Burada bir proje proje başvurusu ve bir dosya başvuru yapar bir durumda, bir tür için başka bir dönüştürülebileceğinden derleyici garanti edemez.</span><span class="sxs-lookup"><span data-stu-id="8c9dd-106">In a situation where a project makes both a project reference and a file reference, the compiler cannot guarantee that one type can be converted to another.</span></span>  
  
 <span data-ttu-id="8c9dd-107">Aşağıdaki sözde kod bu hatayı üreten bir durumu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8c9dd-107">The following pseudo-code illustrates a situation that can generate this error.</span></span>  
  
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
  
 <span data-ttu-id="8c9dd-108">Proje `P1` dolaylı proje başvurusu aracılığıyla projeyi yapar `P2` projesine `P3`ve aynı zamanda doğrudan dosya başvurusu `P3`.</span><span class="sxs-lookup"><span data-stu-id="8c9dd-108">Project `P1` makes an indirect project reference through project `P2` to project `P3`, and also a direct file reference to `P3`.</span></span> <span data-ttu-id="8c9dd-109">Bildirimi `commonObject` dosya başvurusu için kullandığı `P3`, while çağrısı `P2.getCommonClass` proje başvurusu kullanan `P3`.</span><span class="sxs-lookup"><span data-stu-id="8c9dd-109">The declaration of `commonObject` uses the file reference to `P3`, while the call to `P2.getCommonClass` uses the project reference to `P3`.</span></span>  
  
 <span data-ttu-id="8c9dd-110">Bu durumda dosya başvurusunu bir dosya yolu ve çıkış dosyasının adı belirtir bir sorundur `P3` (genellikle p3.dll) kaynak projesini proje başvuruları tanımlayın sırada (`P3`) proje adıyla.</span><span class="sxs-lookup"><span data-stu-id="8c9dd-110">The problem in this situation is that the file reference specifies a file path and name for the output file of `P3` (typically p3.dll), while the project references identify the source project (`P3`) by project name.</span></span> <span data-ttu-id="8c9dd-111">Bu nedenle, derleme, tür garanti edemez `P3.commonClass` iki farklı başvurular aracılığıyla aynı kaynak kodu alanından gelir.</span><span class="sxs-lookup"><span data-stu-id="8c9dd-111">Because of this, the compiler cannot guarantee that the type `P3.commonClass` comes from the same source code through the two different references.</span></span>  
  
 <span data-ttu-id="8c9dd-112">Bu durum genellikle ortaya başvuruları'ne zaman proje ve başvurulara karma.</span><span class="sxs-lookup"><span data-stu-id="8c9dd-112">This situation typically occurs when project references and file references are mixed.</span></span> <span data-ttu-id="8c9dd-113">Önceki çizimde, sorun varsa oluşmaz `P1` doğrudan proje başvurusu yapılan `P3` yerine dosya başvurusu.</span><span class="sxs-lookup"><span data-stu-id="8c9dd-113">In the preceding illustration, the problem would not occur if `P1` made a direct project reference to `P3` instead of a file reference.</span></span>  
  
 <span data-ttu-id="8c9dd-114">**Hata Kimliği:** BC30955</span><span class="sxs-lookup"><span data-stu-id="8c9dd-114">**Error ID:** BC30955</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8c9dd-115">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="8c9dd-115">To correct this error</span></span>  
  
-   <span data-ttu-id="8c9dd-116">Proje başvurusu dosya başvurusunu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="8c9dd-116">Change the file reference to a project reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c9dd-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8c9dd-117">See Also</span></span>  
 [<span data-ttu-id="8c9dd-118">Visual Basic'de tür dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="8c9dd-118">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="8c9dd-119">Bir projedeki başvuruları yönetme</span><span class="sxs-lookup"><span data-stu-id="8c9dd-119">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)  
 [<span data-ttu-id="8c9dd-120">NIB nasıl yapılır: başvuru ekleme veya kaldırma Başvuru Ekle iletişim kutusunu kullanarak</span><span class="sxs-lookup"><span data-stu-id="8c9dd-120">NIB How to: Add or Remove References By Using the Add Reference Dialog Box</span></span>](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)
