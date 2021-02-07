---
description: "Hakkında daha fazla bilgi edinin: BC42104: ' <variablename> ' değişkeni bir değer atanmadan kullanıldı"
title: "'<variablename>' değişkenine bir değer atanmadan kullanıldı"
ms.date: 07/20/2015
f1_keywords:
- vbc42104
- BC42104
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
ms.openlocfilehash: 501c3e3971c5ca0ebdba6981134f5029b77d0075
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701501"
---
# <a name="bc42104-variable-variablename-is-used-before-it-has-been-assigned-a-value"></a><span data-ttu-id="fecce-103">BC42104: ' \<variablename> ' değişkeni bir değer atanmadan kullanıldı</span><span class="sxs-lookup"><span data-stu-id="fecce-103">BC42104: Variable '\<variablename>' is used before it has been assigned a value</span></span>

<span data-ttu-id="fecce-104">' \<variablename> ' Değişkeni bir değer atanmadan önce kullanıldı.</span><span class="sxs-lookup"><span data-stu-id="fecce-104">Variable '\<variablename>' is used before it has been assigned a value.</span></span> <span data-ttu-id="fecce-105">Çalışma zamanında null başvurusu özel durumu oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="fecce-105">A null reference exception could result at run time.</span></span>

 <span data-ttu-id="fecce-106">Bir uygulamanın, herhangi bir değer atanmadan önce bir değişkeni okuyan kodu aracılığıyla olası en az bir yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="fecce-106">An application has at least one possible path through its code that reads a variable before any value is assigned to it.</span></span>

 <span data-ttu-id="fecce-107">Bir değişkene hiç bir değer atanmamışsa, veri türü için varsayılan değeri barındırır.</span><span class="sxs-lookup"><span data-stu-id="fecce-107">If a variable has never been assigned a value, it holds the default value for its data type.</span></span> <span data-ttu-id="fecce-108">Başvuru veri türü için bu varsayılan değer [Nothing](../nothing.md)' dir.</span><span class="sxs-lookup"><span data-stu-id="fecce-108">For a reference data type, that default value is [Nothing](../nothing.md).</span></span> <span data-ttu-id="fecce-109">Bir değere sahip bir başvuru değişkenini okumak `Nothing` bazı koşullarda bir oluşturulmasına neden olabilir <xref:System.NullReferenceException> .</span><span class="sxs-lookup"><span data-stu-id="fecce-109">Reading a reference variable that has a value of `Nothing` can cause a <xref:System.NullReferenceException> in some circumstances.</span></span>

 <span data-ttu-id="fecce-110">Bu ileti, varsayılan olarak bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="fecce-110">By default, this message is a warning.</span></span> <span data-ttu-id="fecce-111">Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="fecce-111">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="fecce-112">**Hata kimliği:** BC42104</span><span class="sxs-lookup"><span data-stu-id="fecce-112">**Error ID:** BC42104</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="fecce-113">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="fecce-113">To correct this error</span></span>

- <span data-ttu-id="fecce-114">Denetim akışı mantığınızı denetleyin ve denetimin kendisini okuyan hiçbir ifadeye geçmeden önce değişkenin geçerli bir değere sahip olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="fecce-114">Check your control flow logic and make sure the variable has a valid value before control passes to any statement that reads it.</span></span>

- <span data-ttu-id="fecce-115">Değişkenin her zaman geçerli bir değere sahip olduğundan emin olmanın bir yolu, bildiriminin bir parçası olarak bunu başlatmaktır.</span><span class="sxs-lookup"><span data-stu-id="fecce-115">One way to guarantee that the variable always has a valid value is to initialize it as part of its declaration.</span></span> <span data-ttu-id="fecce-116">[Dim ifadesinde](../statements/dim-statement.md)"başlatma" konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="fecce-116">See "Initialization" in [Dim Statement](../statements/dim-statement.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fecce-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fecce-117">See also</span></span>

- [<span data-ttu-id="fecce-118">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="fecce-118">Dim Statement</span></span>](../statements/dim-statement.md)
- [<span data-ttu-id="fecce-119">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="fecce-119">Variable Declaration</span></span>](../../programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="fecce-120">Değişkenlerle İlgili Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="fecce-120">Troubleshooting Variables</span></span>](../../programming-guide/language-features/variables/troubleshooting-variables.md)
