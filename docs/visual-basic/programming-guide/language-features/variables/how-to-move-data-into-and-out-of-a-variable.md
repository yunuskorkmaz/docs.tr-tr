---
title: "Nasıl yapılır: Bir Değişkende Veri Ekleme Çıkarma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fefb1979e35cd7b5fa1917f8f1a57af575e51234
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-move-data-into-and-out-of-a-variable-visual-basic"></a><span data-ttu-id="33c34-102">Nasıl yapılır: Bir Değişkende Veri Ekleme Çıkarma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33c34-102">How to: Move Data Into and Out of a Variable (Visual Basic)</span></span>
<span data-ttu-id="33c34-103">Atama ifadesinin sol tarafta değişken adını koyarak bir değer bir değişkende saklayın.</span><span class="sxs-lookup"><span data-stu-id="33c34-103">You store a value in a variable by putting the variable name on the left side of an assignment statement.</span></span>  
  
## <a name="putting-data-in-a-variable"></a><span data-ttu-id="33c34-104">Bir değişkende veri koyma</span><span class="sxs-lookup"><span data-stu-id="33c34-104">Putting Data in a Variable</span></span>  
  
#### <a name="to-store-a-value-in-a-variable"></a><span data-ttu-id="33c34-105">Bir değişkene bir değer depolamak için</span><span class="sxs-lookup"><span data-stu-id="33c34-105">To store a value in a variable</span></span>  
  
-   <span data-ttu-id="33c34-106">Değişken adı atama ifadesinin sol taraftaki kullanın.</span><span class="sxs-lookup"><span data-stu-id="33c34-106">Use the variable name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="33c34-107">Aşağıdaki örnekte değişken değerini ayarlar `alpha`.</span><span class="sxs-lookup"><span data-stu-id="33c34-107">The following example sets the value of the variable `alpha`.</span></span>  
  
    ```  
    alpha = (beta * 6.27) / (gamma + 2.1)  
    ```  
  
     <span data-ttu-id="33c34-108">Atama ifadesinin sağ tarafında oluşturulan değeri değişkende depolanır.</span><span class="sxs-lookup"><span data-stu-id="33c34-108">The value generated on the right side of the assignment statement is stored in the variable.</span></span>  
  
## <a name="getting-data-from-a-variable"></a><span data-ttu-id="33c34-109">Bir değişkeninden veri alma</span><span class="sxs-lookup"><span data-stu-id="33c34-109">Getting Data from a Variable</span></span>  
 <span data-ttu-id="33c34-110">Bir deyimde değişken adı dahil olmak üzere bir değişkenin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="33c34-110">You retrieve a variable's value by including the variable name in an expression.</span></span>  
  
#### <a name="to-retrieve-a-value-from-a-variable"></a><span data-ttu-id="33c34-111">Bir değişkeninden bir değer almak için</span><span class="sxs-lookup"><span data-stu-id="33c34-111">To retrieve a value from a variable</span></span>  
  
-   <span data-ttu-id="33c34-112">Değişken adı bir ifade kullanın.</span><span class="sxs-lookup"><span data-stu-id="33c34-112">Use the variable name in an expression.</span></span> <span data-ttu-id="33c34-113">Bir değişken kullanabilirsiniz herhangi bir yerde bir sabit ya da bir hazır değer dışında bir sabit değer tanımlayan bir ifade kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="33c34-113">You can use a variable anywhere you can use a constant or a literal, except in an expression that defines the value of a constant.</span></span>  
  
     <span data-ttu-id="33c34-114">veya</span><span class="sxs-lookup"><span data-stu-id="33c34-114">-or-</span></span>  
  
-   <span data-ttu-id="33c34-115">Eşittir aşağıdaki değişken adını kullanın (`=`) bir atama deyiminde oturum açın.</span><span class="sxs-lookup"><span data-stu-id="33c34-115">Use the variable name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="33c34-116">Aşağıdaki örnek değişkenin değeri olarak okur `startValue` ve değişkenin değerini kullanır `counter` deyimde.</span><span class="sxs-lookup"><span data-stu-id="33c34-116">The following example reads the value of the variable `startValue` and then uses the value of the variable `counter` in an expression.</span></span>  
  
    ```  
    counter = startValue  
    cellValue = (counter + 5) ^ 2  
    ```  
  
     <span data-ttu-id="33c34-117">Değişkenin değeri olarak yalnızca bir sabit gerekir ve ardından değişkeni veya özellikte Atama ifadesinin sol tarafında depolanır ifade katılır.</span><span class="sxs-lookup"><span data-stu-id="33c34-117">The value of the variable participates in the expression just as a constant would, and then it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33c34-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="33c34-118">See Also</span></span>  
 [<span data-ttu-id="33c34-119">Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="33c34-119">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [<span data-ttu-id="33c34-120">Değişken bildirimi</span><span class="sxs-lookup"><span data-stu-id="33c34-120">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="33c34-121">Nesne değişkenleri</span><span class="sxs-lookup"><span data-stu-id="33c34-121">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
