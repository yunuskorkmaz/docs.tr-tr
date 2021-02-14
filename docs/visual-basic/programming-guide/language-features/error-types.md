---
description: 'Daha fazla bilgi edinin: hata türleri (Visual Basic)'
title: Hata Türleri
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, types
- errors [Visual Basic], types
- errors [Visual Basic], logic
- errors [Visual Basic], syntax
- logic errors [Visual Basic], Visual Basic
- run-time errors [Visual Basic], types of errors
- syntax errors [Visual Basic], Visual Basic
ms.assetid: 3048aabf-8c97-4e13-9150-853769cb5f6f
ms.openlocfilehash: cc4fce5e0ce77a4e402ba832fd6f4e36e6feed07
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100423777"
---
# <a name="error-types-visual-basic"></a><span data-ttu-id="9721e-103">Hata Türleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9721e-103">Error Types (Visual Basic)</span></span>

<span data-ttu-id="9721e-104">Visual Basic, hatalar üç kategoriden birine ayrılır: sözdizimi hataları, çalışma zamanı hataları ve mantık hataları.</span><span class="sxs-lookup"><span data-stu-id="9721e-104">In Visual Basic, errors fall into one of three categories: syntax errors, run-time errors, and logic errors.</span></span>

## <a name="syntax-errors"></a><span data-ttu-id="9721e-105">Sözdizimi hataları</span><span class="sxs-lookup"><span data-stu-id="9721e-105">Syntax Errors</span></span>

 <span data-ttu-id="9721e-106">*Sözdizimi hataları* , kod yazarken görüntülenen olanlardır.</span><span class="sxs-lookup"><span data-stu-id="9721e-106">*Syntax errors* are those that appear while you write code.</span></span> <span data-ttu-id="9721e-107">Visual Studio kullanıyorsanız Visual Basic, kodu **kod düzenleyici** penceresinde yazarken kodu denetler ve bir sözcüğün yanlış olması veya bir dil öğesinin yanlış şekilde kullanılması gibi bir hata yaparsanız sizi uyarır.</span><span class="sxs-lookup"><span data-stu-id="9721e-107">If you're using Visual Studio, Visual Basic checks your code as you type it in the **Code Editor** window and alerts you if you make a mistake, such as misspelling a word or using a language element improperly.</span></span> <span data-ttu-id="9721e-108">Komut satırından derlerseniz Visual Basic sözdizimi hatası hakkında bilgi içeren bir derleyici hatası görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9721e-108">If you compile from the command line, Visual Basic displays a compiler error with information about the syntax error.</span></span> <span data-ttu-id="9721e-109">Sözdizimi hataları en yaygın hata türüdür.</span><span class="sxs-lookup"><span data-stu-id="9721e-109">Syntax errors are the most common type of errors.</span></span> <span data-ttu-id="9721e-110">Bunları, kodlama ortamında, her gerçekleştiğinde kolayca çözebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9721e-110">You can fix them easily in the coding environment as soon as they occur.</span></span>

> [!NOTE]
> <span data-ttu-id="9721e-111">`Option Explicit`İfade, sözdizimi hatalarından kaçınmanın bir yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="9721e-111">The `Option Explicit` statement is one means of avoiding syntax errors.</span></span> <span data-ttu-id="9721e-112">Bu, uygulamada kullanılacak tüm değişkenleri önceden bildirmeye zorlar.</span><span class="sxs-lookup"><span data-stu-id="9721e-112">It forces you to declare, in advance, all the variables to be used in the application.</span></span> <span data-ttu-id="9721e-113">Bu nedenle, bu değişkenler kodda kullanıldığında, her tipografik hata hemen yakalanır ve düzeltilebilir.</span><span class="sxs-lookup"><span data-stu-id="9721e-113">Therefore, when those variables are used in the code, any typographic errors are caught immediately and can be fixed.</span></span>

## <a name="run-time-errors"></a><span data-ttu-id="9721e-114">Run-Time hataları</span><span class="sxs-lookup"><span data-stu-id="9721e-114">Run-Time Errors</span></span>

 <span data-ttu-id="9721e-115">*Çalışma zamanı hataları* yalnızca kodunuzu derleyip çalıştırdıktan sonra görüntülenen olanlardır.</span><span class="sxs-lookup"><span data-stu-id="9721e-115">*Run-time errors* are those that appear only after you compile and run your code.</span></span> <span data-ttu-id="9721e-116">Bunlar, sözdizimi hataları olmayan, ancak yürütülmeyecek şekilde doğru görünebilen kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="9721e-116">These involve code that may appear to be correct in that it has no syntax errors, but that will not execute.</span></span> <span data-ttu-id="9721e-117">Örneğin, bir dosyayı açmak için doğru bir kod satırı yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9721e-117">For example, you might correctly write a line of code to open a file.</span></span> <span data-ttu-id="9721e-118">Ancak dosya yoksa, uygulama dosyayı açamaz ve bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9721e-118">But if the file does not exist, the application cannot open the file, and it throws an exception.</span></span> <span data-ttu-id="9721e-119">Hatalı kodu yeniden yazarak veya [özel durum işlemeyi](../../language-reference/statements/try-catch-finally-statement.md)kullanarak ve sonra yeniden oluşturup yeniden çalıştırarak birçok çalışma zamanı hatasını giderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9721e-119">You can fix most run-time errors by rewriting the faulty code or by using [exception handling](../../language-reference/statements/try-catch-finally-statement.md), and then recompiling and rerunning it.</span></span>
  
## <a name="logic-errors"></a><span data-ttu-id="9721e-120">Mantık hataları</span><span class="sxs-lookup"><span data-stu-id="9721e-120">Logic Errors</span></span>

 <span data-ttu-id="9721e-121">*Mantık hataları* , uygulama kullanımda olduktan sonra görüntülenen olanlardır.</span><span class="sxs-lookup"><span data-stu-id="9721e-121">*Logic errors* are those that appear once the application is in use.</span></span> <span data-ttu-id="9721e-122">Bunlar genellikle geliştirici tarafından yapılan hatalı varsayımlar veya kullanıcı eylemlerine yanıt olarak istenmeyen ya da beklenmeyen sonuçlardır.</span><span class="sxs-lookup"><span data-stu-id="9721e-122">They are most often faulty assumptions made by the developer, or unwanted or unexpected results in response to user actions.</span></span> <span data-ttu-id="9721e-123">Örneğin, yanlış yazılan bir anahtar bir yönteme yanlış bilgiler verebilir ya da bu durum olmadığı zaman bir yönteme geçerli bir değer sağlanması gerektiğini varsayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9721e-123">For example, a mistyped key might provide incorrect information to a method, or you may assume that a valid value is always supplied to a method when that is not the case.</span></span> <span data-ttu-id="9721e-124">Mantıksal hatalar [özel durum işleme](../../language-reference/statements/try-catch-finally-statement.md) kullanılarak işlenebilse de (örneğin, bir bağımsız değişkenin olup olmadığını test ederek `Nothing` <xref:System.ArgumentNullException> ), en yaygın olarak, mantığdaki hatayı düzelterek ve uygulamayı yeniden derlemeden değinilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="9721e-124">Although logic errors can be handled by using [exception handling](../../language-reference/statements/try-catch-finally-statement.md) (for example, by testing whether an argument is `Nothing` and throwing an <xref:System.ArgumentNullException>), most commonly they should be addressed by correcting the error in logic and recompiling the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="9721e-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9721e-125">See also</span></span>

- [<span data-ttu-id="9721e-126">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="9721e-126">Try...Catch...Finally Statement</span></span>](../../language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="9721e-127">Hata Ayıklayıcı Temel Bilgileri</span><span class="sxs-lookup"><span data-stu-id="9721e-127">Debugger Basics</span></span>](/visualstudio/debugger/debugger-feature-tour)
