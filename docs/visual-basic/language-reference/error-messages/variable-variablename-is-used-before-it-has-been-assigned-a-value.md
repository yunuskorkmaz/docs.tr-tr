---
title: "'<variablename>' değişkenine bir değer atanmadan kullanıldı"
ms.date: 07/20/2015
f1_keywords:
- vbc42104
- BC42104
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
ms.openlocfilehash: a2ba752b95933d146da090a58c416015db75e106
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662679"
---
# <a name="variable-variablename-is-used-before-it-has-been-assigned-a-value"></a><span data-ttu-id="fd749-102">Değişken '\<variablename >' bir değer atanmadan önce kullanıldı</span><span class="sxs-lookup"><span data-stu-id="fd749-102">Variable '\<variablename>' is used before it has been assigned a value</span></span>
<span data-ttu-id="fd749-103">Değişken '\<variablename >' bir değer atanmadan önce kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fd749-103">Variable '\<variablename>' is used before it has been assigned a value.</span></span> <span data-ttu-id="fd749-104">Çalışma zamanında null başvurusu özel durumu neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="fd749-104">A null reference exception could result at run time.</span></span>  
  
 <span data-ttu-id="fd749-105">Bir uygulama için herhangi bir değere atanmadan önce değişken okur, kod aracılığıyla en az bir yol vardır.</span><span class="sxs-lookup"><span data-stu-id="fd749-105">An application has at least one possible path through its code that reads a variable before any value is assigned to it.</span></span>  
  
 <span data-ttu-id="fd749-106">Bir değişkene bir değer hiçbir zaman atandıysa, kendi veri türü için varsayılan değeri içerir.</span><span class="sxs-lookup"><span data-stu-id="fd749-106">If a variable has never been assigned a value, it holds the default value for its data type.</span></span> <span data-ttu-id="fd749-107">Başvuru veri türleri için bu varsayılan değerdir [hiçbir şey](../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="fd749-107">For a reference data type, that default value is [Nothing](../../../visual-basic/language-reference/nothing.md).</span></span> <span data-ttu-id="fd749-108">Bir değeri olan bir başvuru değişkenini okuma `Nothing` neden olabilir bir <xref:System.NullReferenceException> bazı durumlarda.</span><span class="sxs-lookup"><span data-stu-id="fd749-108">Reading a reference variable that has a value of `Nothing` can cause a <xref:System.NullReferenceException> in some circumstances.</span></span>  
  
 <span data-ttu-id="fd749-109">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="fd749-109">By default, this message is a warning.</span></span> <span data-ttu-id="fd749-110">Uyarıları gizleme veya uyarıları hata olarak değerlendirmesini daha fazla bilgi için bkz: [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="fd749-110">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="fd749-111">**Hata Kimliği:** BC42104</span><span class="sxs-lookup"><span data-stu-id="fd749-111">**Error ID:** BC42104</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fd749-112">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="fd749-112">To correct this error</span></span>  
  
- <span data-ttu-id="fd749-113">Denetim akışı mantığınızı denetleyin ve denetim okuduğu herhangi bir deyimle geçirmeden önce değişkeni geçerli bir değere sahip olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="fd749-113">Check your control flow logic and make sure the variable has a valid value before control passes to any statement that reads it.</span></span>  
  
- <span data-ttu-id="fd749-114">Değişken geçerli bir değer her zaman sahip olacağı garanti edilir bir bildiriminin bir parçası olarak başlatmak için yoludur.</span><span class="sxs-lookup"><span data-stu-id="fd749-114">One way to guarantee that the variable always has a valid value is to initialize it as part of its declaration.</span></span> <span data-ttu-id="fd749-115">"Başlatma" konusuna bakın [Dim deyimi](../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fd749-115">See "Initialization" in [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd749-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd749-116">See also</span></span>

- [<span data-ttu-id="fd749-117">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="fd749-117">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="fd749-118">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="fd749-118">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="fd749-119">Değişkenlerle İlgili Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="fd749-119">Troubleshooting Variables</span></span>](../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)
