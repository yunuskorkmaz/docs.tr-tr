---
title: "Değişken &#39; &lt;variablename&gt;&#39; bir değer atanan önce kullanıldı"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42104
- BC42104
helpviewer_keywords: BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 201667c250e15bb9af73e64e2d8c924c1952d1be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="variable-39ltvariablenamegt39-is-used-before-it-has-been-assigned-a-value"></a><span data-ttu-id="8b0b0-102">Değişken &#39; &lt;variablename&gt;&#39; bir değer atanan önce kullanıldı</span><span class="sxs-lookup"><span data-stu-id="8b0b0-102">Variable &#39;&lt;variablename&gt;&#39; is used before it has been assigned a value</span></span>
<span data-ttu-id="8b0b0-103">Değişken '\<variablename >' değeri atanmış önce kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8b0b0-103">Variable '\<variablename>' is used before it has been assigned a value.</span></span> <span data-ttu-id="8b0b0-104">Bir null başvuru özel durumu, çalışma zamanında neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="8b0b0-104">A null reference exception could result at run time.</span></span>  
  
 <span data-ttu-id="8b0b0-105">Bir uygulama bir değişken herhangi bir değer atanmış önce okuyan kendi kod aracılığıyla en az bir olası yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="8b0b0-105">An application has at least one possible path through its code that reads a variable before any value is assigned to it.</span></span>  
  
 <span data-ttu-id="8b0b0-106">Bir değişken hiçbir zaman bir değer atanmışsa, veri türü için varsayılan değer tutar.</span><span class="sxs-lookup"><span data-stu-id="8b0b0-106">If a variable has never been assigned a value, it holds the default value for its data type.</span></span> <span data-ttu-id="8b0b0-107">Bir başvuru veri türleri için bu varsayılan değerdir [hiçbir şey](../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="8b0b0-107">For a reference data type, that default value is [Nothing](../../../visual-basic/language-reference/nothing.md).</span></span> <span data-ttu-id="8b0b0-108">Değerine sahip bir başvuru değişken okuma `Nothing` neden olabilir bir <xref:System.NullReferenceException> bazı durumlarda.</span><span class="sxs-lookup"><span data-stu-id="8b0b0-108">Reading a reference variable that has a value of `Nothing` can cause a <xref:System.NullReferenceException> in some circumstances.</span></span>  
  
 <span data-ttu-id="8b0b0-109">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="8b0b0-109">By default, this message is a warning.</span></span> <span data-ttu-id="8b0b0-110">Uyarıları gizleme veya uyarıları hata olarak davranma daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="8b0b0-110">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="8b0b0-111">**Hata Kimliği:** BC42104</span><span class="sxs-lookup"><span data-stu-id="8b0b0-111">**Error ID:** BC42104</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8b0b0-112">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="8b0b0-112">To correct this error</span></span>  
  
-   <span data-ttu-id="8b0b0-113">Denetim akışı mantığınızı denetleyin ve bunu okuyan herhangi bir deyimle denetim geçirmeden önce değişkeni geçerli bir değere sahip olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="8b0b0-113">Check your control flow logic and make sure the variable has a valid value before control passes to any statement that reads it.</span></span>  
  
-   <span data-ttu-id="8b0b0-114">Değişken her zaman geçerli bir değere sahip olmasını garanti etmek için bir bildiriminden bir parçası olarak başlatmak için yoludur.</span><span class="sxs-lookup"><span data-stu-id="8b0b0-114">One way to guarantee that the variable always has a valid value is to initialize it as part of its declaration.</span></span> <span data-ttu-id="8b0b0-115">"Başlatma" konusuna bakın [Dim deyimi](../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8b0b0-115">See "Initialization" in [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b0b0-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8b0b0-116">See Also</span></span>  
 [<span data-ttu-id="8b0b0-117">Dim deyimi</span><span class="sxs-lookup"><span data-stu-id="8b0b0-117">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="8b0b0-118">Değişken bildirimi</span><span class="sxs-lookup"><span data-stu-id="8b0b0-118">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="8b0b0-119">Değişkenlerle ilgili sorun giderme</span><span class="sxs-lookup"><span data-stu-id="8b0b0-119">Troubleshooting Variables</span></span>](../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)
