---
title: Error deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.error
helpviewer_keywords:
- Error statement [Visual Basic], syntax
- Error statement [Visual Basic]
- Error keyword [Visual Basic]
- run-time errors [Visual Basic], codes
- errors [Visual Basic], simulating
ms.assetid: 85cd5c59-5224-4f02-aaf5-fcfefab17a29
ms.openlocfilehash: 84fce92183228cbfa5554a3ba45770a86e83bff5
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43885675"
---
# <a name="error-statement"></a><span data-ttu-id="ea202-102">Error Deyimi</span><span class="sxs-lookup"><span data-stu-id="ea202-102">Error Statement</span></span>
<span data-ttu-id="ea202-103">Bir hatanın oluşum benzetimini yapar.</span><span class="sxs-lookup"><span data-stu-id="ea202-103">Simulates the occurrence of an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea202-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ea202-104">Syntax</span></span>  
  
```  
Error errornumber  
```  
  
## <a name="parts"></a><span data-ttu-id="ea202-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="ea202-105">Parts</span></span>  
 `errornumber`  
 <span data-ttu-id="ea202-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="ea202-106">Required.</span></span> <span data-ttu-id="ea202-107">Herhangi bir geçerli hata sayı olabilir.</span><span class="sxs-lookup"><span data-stu-id="ea202-107">Can be any valid error number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea202-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ea202-108">Remarks</span></span>  
 <span data-ttu-id="ea202-109">`Error` Deyimi, geriye dönük uyumluluk için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ea202-109">The `Error` statement is supported for backward compatibility.</span></span> <span data-ttu-id="ea202-110">Özellikle, nesneleri oluştururken yeni kodda, kullanın `Err` nesnenin `Raise` çalışma zamanı hataları oluşturmasına yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ea202-110">In new code, especially when creating objects, use the `Err` object's `Raise` method to generate run-time errors.</span></span>  
  
 <span data-ttu-id="ea202-111">Varsa `errornumber` tanımlanan `Error` ifade, sonra özelliklerini hata işleyicisini çağırır `Err` nesne, aşağıdaki varsayılan değerler atanır:</span><span class="sxs-lookup"><span data-stu-id="ea202-111">If `errornumber` is defined, the `Error` statement calls the error handler after the properties of the `Err` object are assigned the following default values:</span></span>  
  
|<span data-ttu-id="ea202-112">Özellik</span><span class="sxs-lookup"><span data-stu-id="ea202-112">Property</span></span>|<span data-ttu-id="ea202-113">Değer</span><span class="sxs-lookup"><span data-stu-id="ea202-113">Value</span></span>|  
|--------------|-----------|  
|`Number`|<span data-ttu-id="ea202-114">Bağımsız değişkeni olarak belirtilen değeri `Error` deyimi.</span><span class="sxs-lookup"><span data-stu-id="ea202-114">Value specified as argument to `Error` statement.</span></span> <span data-ttu-id="ea202-115">Herhangi bir geçerli hata sayı olabilir.</span><span class="sxs-lookup"><span data-stu-id="ea202-115">Can be any valid error number.</span></span>|  
|`Source`|<span data-ttu-id="ea202-116">Geçerli Visual Basic projesi adı.</span><span class="sxs-lookup"><span data-stu-id="ea202-116">Name of the current Visual Basic project.</span></span>|  
|`Description`|<span data-ttu-id="ea202-117">Dize ifadesi dönüş değerine karşılık gelen `Error` işlevi için belirtilen `Number`, bu dizenin varsa.</span><span class="sxs-lookup"><span data-stu-id="ea202-117">String expression corresponding to the return value of the `Error` function for the specified `Number`, if this string exists.</span></span> <span data-ttu-id="ea202-118">Dize mevcut değilse `Description` sıfır uzunlukta bir dize içerir ("").</span><span class="sxs-lookup"><span data-stu-id="ea202-118">If the string does not exist, `Description` contains a zero-length string ("").</span></span>|  
|`HelpFile`|<span data-ttu-id="ea202-119">Tam sürücü yolu ve uygun Visual Basic Yardım dosyasının dosya adı.</span><span class="sxs-lookup"><span data-stu-id="ea202-119">The fully qualified drive, path, and file name of the appropriate Visual Basic Help file.</span></span>|  
|`HelpContext`|<span data-ttu-id="ea202-120">Visual Basic uygun Yardım dosyası hata karşılık gelen için bir bağlam kimliği `Number` özelliği.</span><span class="sxs-lookup"><span data-stu-id="ea202-120">The appropriate Visual Basic Help file context ID for the error corresponding to the `Number` property.</span></span>|  
|`LastDLLError`|<span data-ttu-id="ea202-121">Sıfır.</span><span class="sxs-lookup"><span data-stu-id="ea202-121">Zero.</span></span>|  
  
 <span data-ttu-id="ea202-122">Hiçbir hata işleyicisi yok veya etkinse, bir hata iletisi oluşturulur ve gelen görüntülenen `Err` nesne özellikleri.</span><span class="sxs-lookup"><span data-stu-id="ea202-122">If no error handler exists, or if none is enabled, an error message is created and displayed from the `Err` object properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea202-123">Bazı Visual Basic ana bilgisayar uygulamalarını nesneler oluşturamaz.</span><span class="sxs-lookup"><span data-stu-id="ea202-123">Some Visual Basic host applications cannot create objects.</span></span> <span data-ttu-id="ea202-124">Sınıflar ve nesneler oluşturabilir olup olmadığını belirlemek için konak uygulamanızın belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="ea202-124">See your host application's documentation to determine whether it can create classes and objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea202-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="ea202-125">Example</span></span>  
 <span data-ttu-id="ea202-126">Bu örnekte `Error` hata numarası 11 oluşturulacak deyimi.</span><span class="sxs-lookup"><span data-stu-id="ea202-126">This example uses the `Error` statement to generate error number 11.</span></span>  
  
```  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a><span data-ttu-id="ea202-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ea202-127">Requirements</span></span>  
 <span data-ttu-id="ea202-128">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="ea202-128">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="ea202-129">**Bütünleştirilmiş kod:** Visual Basic çalışma zamanı kitaplığı (Microsoft.VisualBasic.dll içinde)</span><span class="sxs-lookup"><span data-stu-id="ea202-129">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea202-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ea202-130">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>  
 <xref:Microsoft.VisualBasic.Information.Err%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>  
 [<span data-ttu-id="ea202-131">On Error Deyimi</span><span class="sxs-lookup"><span data-stu-id="ea202-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)  
 [<span data-ttu-id="ea202-132">Resume Deyimi</span><span class="sxs-lookup"><span data-stu-id="ea202-132">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [<span data-ttu-id="ea202-133">Hata İletileri</span><span class="sxs-lookup"><span data-stu-id="ea202-133">Error Messages</span></span>](../../../visual-basic/language-reference/error-messages/index.md)
