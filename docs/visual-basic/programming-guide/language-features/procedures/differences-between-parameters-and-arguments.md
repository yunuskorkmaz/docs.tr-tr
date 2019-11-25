---
title: Parametreler ve Bağımsız Değişkenler Arasındaki Farklar
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- parameters [Visual Basic], and arguments
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], and parameters
- procedure parameters
- parameters [Visual Basic], definition
ms.assetid: c237c056-74f4-4749-9f2c-15864f139a31
ms.openlocfilehash: c4249dbf86bd1bfa7ef08e94059d2880333e9a92
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74341370"
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a><span data-ttu-id="f8521-102">Parametreler ve Bağımsız Değişkenler Arasındaki Farklar (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8521-102">Differences Between Parameters and Arguments (Visual Basic)</span></span>
<span data-ttu-id="f8521-103">In most cases, a procedure must have some information about the circumstances in which it has been called.</span><span class="sxs-lookup"><span data-stu-id="f8521-103">In most cases, a procedure must have some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="f8521-104">A procedure that performs repeated or shared tasks uses different information for each call.</span><span class="sxs-lookup"><span data-stu-id="f8521-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="f8521-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span><span class="sxs-lookup"><span data-stu-id="f8521-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="f8521-106">To communicate this information to the procedure, the procedure defines a *parameter*, and the calling code passes an *argument* to that parameter.</span><span class="sxs-lookup"><span data-stu-id="f8521-106">To communicate this information to the procedure, the procedure defines a *parameter*, and the calling code passes an *argument* to that parameter.</span></span> <span data-ttu-id="f8521-107">You can think of the parameter as a parking space and the argument as an automobile.</span><span class="sxs-lookup"><span data-stu-id="f8521-107">You can think of the parameter as a parking space and the argument as an automobile.</span></span> <span data-ttu-id="f8521-108">Just as different automobiles can park in a parking space at different times, the calling code can pass a different argument to the same parameter every time that it calls the procedure.</span><span class="sxs-lookup"><span data-stu-id="f8521-108">Just as different automobiles can park in a parking space at different times, the calling code can pass a different argument to the same parameter every time that it calls the procedure.</span></span>  
  
## <a name="parameters"></a><span data-ttu-id="f8521-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f8521-109">Parameters</span></span>  
 <span data-ttu-id="f8521-110">A *parameter* represents a value that the procedure expects you to pass when you call it.</span><span class="sxs-lookup"><span data-stu-id="f8521-110">A *parameter* represents a value that the procedure expects you to pass when you call it.</span></span> <span data-ttu-id="f8521-111">The procedure's declaration defines its parameters.</span><span class="sxs-lookup"><span data-stu-id="f8521-111">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="f8521-112">When you define a `Function` or `Sub` procedure, you specify a *parameter list* in parentheses immediately following the procedure name.</span><span class="sxs-lookup"><span data-stu-id="f8521-112">When you define a `Function` or `Sub` procedure, you specify a *parameter list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="f8521-113">For each parameter, you specify a name, a data type, and a passing mechanism ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)).</span><span class="sxs-lookup"><span data-stu-id="f8521-113">For each parameter, you specify a name, a data type, and a passing mechanism ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)).</span></span> <span data-ttu-id="f8521-114">You can also indicate that a parameter is optional.</span><span class="sxs-lookup"><span data-stu-id="f8521-114">You can also indicate that a parameter is optional.</span></span> <span data-ttu-id="f8521-115">This means that the calling code does not have to pass a value for it.</span><span class="sxs-lookup"><span data-stu-id="f8521-115">This means that the calling code does not have to pass a value for it.</span></span>  
  
 <span data-ttu-id="f8521-116">The name of each parameter serves as a *local variable* in the procedure.</span><span class="sxs-lookup"><span data-stu-id="f8521-116">The name of each parameter serves as a *local variable* in the procedure.</span></span> <span data-ttu-id="f8521-117">You use the parameter name the same way you use any other variable.</span><span class="sxs-lookup"><span data-stu-id="f8521-117">You use the parameter name the same way you use any other variable.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="f8521-118">Arguments</span><span class="sxs-lookup"><span data-stu-id="f8521-118">Arguments</span></span>  
 <span data-ttu-id="f8521-119">An *argument* represents the value that you pass to a procedure parameter when you call the procedure.</span><span class="sxs-lookup"><span data-stu-id="f8521-119">An *argument* represents the value that you pass to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="f8521-120">The calling code supplies the arguments when it calls the procedure.</span><span class="sxs-lookup"><span data-stu-id="f8521-120">The calling code supplies the arguments when it calls the procedure.</span></span>  
  
 <span data-ttu-id="f8521-121">When you call a `Function` or `Sub` procedure, you include an *argument list* in parentheses immediately following the procedure name.</span><span class="sxs-lookup"><span data-stu-id="f8521-121">When you call a `Function` or `Sub` procedure, you include an *argument list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="f8521-122">Each argument corresponds to the parameter in the same position in the list.</span><span class="sxs-lookup"><span data-stu-id="f8521-122">Each argument corresponds to the parameter in the same position in the list.</span></span>  
  
 <span data-ttu-id="f8521-123">In contrast to parameter definition, arguments do not have names.</span><span class="sxs-lookup"><span data-stu-id="f8521-123">In contrast to parameter definition, arguments do not have names.</span></span> <span data-ttu-id="f8521-124">Each argument is an expression, which can contain zero or more variables, constants, and literals.</span><span class="sxs-lookup"><span data-stu-id="f8521-124">Each argument is an expression, which can contain zero or more variables, constants, and literals.</span></span> <span data-ttu-id="f8521-125">The data type of the evaluated expression should typically match the data type defined for the corresponding parameter, and in any case it must be convertible to the parameter type.</span><span class="sxs-lookup"><span data-stu-id="f8521-125">The data type of the evaluated expression should typically match the data type defined for the corresponding parameter, and in any case it must be convertible to the parameter type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8521-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8521-126">See also</span></span>

- [<span data-ttu-id="f8521-127">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="f8521-127">Procedures</span></span>](./index.md)
- [<span data-ttu-id="f8521-128">Alt Yordamlar</span><span class="sxs-lookup"><span data-stu-id="f8521-128">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="f8521-129">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="f8521-129">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="f8521-130">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="f8521-130">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="f8521-131">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="f8521-131">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="f8521-132">Nasıl yapılır: Bir Yordamın Parametresini Tanımlama</span><span class="sxs-lookup"><span data-stu-id="f8521-132">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="f8521-133">Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme</span><span class="sxs-lookup"><span data-stu-id="f8521-133">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="f8521-134">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="f8521-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="f8521-135">Özyinelemeli Yordamlar</span><span class="sxs-lookup"><span data-stu-id="f8521-135">Recursive Procedures</span></span>](./recursive-procedures.md)
- [<span data-ttu-id="f8521-136">Yordam Aşırı Yüklemesi</span><span class="sxs-lookup"><span data-stu-id="f8521-136">Procedure Overloading</span></span>](./procedure-overloading.md)
