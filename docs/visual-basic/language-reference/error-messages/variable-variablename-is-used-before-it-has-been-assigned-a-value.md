---
title: "'<variablename>' değişkenine bir değer atanmadan kullanıldı"
ms.date: 07/20/2015
f1_keywords:
- vbc42104
- BC42104
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
ms.openlocfilehash: 34718243172d3b1a238a813268e672d62c4eeb6c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406540"
---
# <a name="variable-variablename-is-used-before-it-has-been-assigned-a-value"></a><span data-ttu-id="cfdef-102">'\<variablename>' değişkenine bir değer atanmadan kullanıldı</span><span class="sxs-lookup"><span data-stu-id="cfdef-102">Variable '\<variablename>' is used before it has been assigned a value</span></span>
<span data-ttu-id="cfdef-103">' \<variablename> ' Değişkeni bir değer atanmadan önce kullanıldı.</span><span class="sxs-lookup"><span data-stu-id="cfdef-103">Variable '\<variablename>' is used before it has been assigned a value.</span></span> <span data-ttu-id="cfdef-104">Çalışma zamanında null başvurusu özel durumu oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="cfdef-104">A null reference exception could result at run time.</span></span>  
  
 <span data-ttu-id="cfdef-105">Bir uygulamanın, herhangi bir değer atanmadan önce bir değişkeni okuyan kodu aracılığıyla olası en az bir yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="cfdef-105">An application has at least one possible path through its code that reads a variable before any value is assigned to it.</span></span>  
  
 <span data-ttu-id="cfdef-106">Bir değişkene hiç bir değer atanmamışsa, veri türü için varsayılan değeri barındırır.</span><span class="sxs-lookup"><span data-stu-id="cfdef-106">If a variable has never been assigned a value, it holds the default value for its data type.</span></span> <span data-ttu-id="cfdef-107">Başvuru veri türü için bu varsayılan değer [Nothing](../nothing.md)' dir.</span><span class="sxs-lookup"><span data-stu-id="cfdef-107">For a reference data type, that default value is [Nothing](../nothing.md).</span></span> <span data-ttu-id="cfdef-108">Bir değere sahip bir başvuru değişkenini okumak `Nothing` bazı koşullarda bir oluşturulmasına neden olabilir <xref:System.NullReferenceException> .</span><span class="sxs-lookup"><span data-stu-id="cfdef-108">Reading a reference variable that has a value of `Nothing` can cause a <xref:System.NullReferenceException> in some circumstances.</span></span>  
  
 <span data-ttu-id="cfdef-109">Bu ileti, varsayılan olarak bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="cfdef-109">By default, this message is a warning.</span></span> <span data-ttu-id="cfdef-110">Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="cfdef-110">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="cfdef-111">**Hata kimliği:** BC42104</span><span class="sxs-lookup"><span data-stu-id="cfdef-111">**Error ID:** BC42104</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cfdef-112">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="cfdef-112">To correct this error</span></span>  
  
- <span data-ttu-id="cfdef-113">Denetim akışı mantığınızı denetleyin ve denetimin kendisini okuyan hiçbir ifadeye geçmeden önce değişkenin geçerli bir değere sahip olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="cfdef-113">Check your control flow logic and make sure the variable has a valid value before control passes to any statement that reads it.</span></span>  
  
- <span data-ttu-id="cfdef-114">Değişkenin her zaman geçerli bir değere sahip olduğundan emin olmanın bir yolu, bildiriminin bir parçası olarak bunu başlatmaktır.</span><span class="sxs-lookup"><span data-stu-id="cfdef-114">One way to guarantee that the variable always has a valid value is to initialize it as part of its declaration.</span></span> <span data-ttu-id="cfdef-115">[Dim ifadesinde](../statements/dim-statement.md)"başlatma" konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="cfdef-115">See "Initialization" in [Dim Statement](../statements/dim-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfdef-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cfdef-116">See also</span></span>

- [<span data-ttu-id="cfdef-117">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="cfdef-117">Dim Statement</span></span>](../statements/dim-statement.md)
- [<span data-ttu-id="cfdef-118">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="cfdef-118">Variable Declaration</span></span>](../../programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="cfdef-119">Değişkenlerle İlgili Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="cfdef-119">Troubleshooting Variables</span></span>](../../programming-guide/language-features/variables/troubleshooting-variables.md)
