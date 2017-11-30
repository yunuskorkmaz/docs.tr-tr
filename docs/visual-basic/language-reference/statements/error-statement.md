---
title: Error Deyimi
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.error
helpviewer_keywords:
- Error statement [Visual Basic], syntax
- Error statement [Visual Basic]
- Error keyword [Visual Basic]
- run-time errors [Visual Basic], codes
- errors [Visual Basic], simulating
ms.assetid: 85cd5c59-5224-4f02-aaf5-fcfefab17a29
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3cd3245fd3e9e62b1b6443e9787c97808a0d179d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="error-statement"></a><span data-ttu-id="06f84-102">Error Deyimi</span><span class="sxs-lookup"><span data-stu-id="06f84-102">Error Statement</span></span>
<span data-ttu-id="06f84-103">Bir hata oluşması benzetimini yapar.</span><span class="sxs-lookup"><span data-stu-id="06f84-103">Simulates the occurrence of an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06f84-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="06f84-104">Syntax</span></span>  
  
```  
Error errornumber  
```  
  
## <a name="parts"></a><span data-ttu-id="06f84-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="06f84-105">Parts</span></span>  
 `errornumber`  
 <span data-ttu-id="06f84-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="06f84-106">Required.</span></span> <span data-ttu-id="06f84-107">Herhangi bir geçerli hata sayı olabilir.</span><span class="sxs-lookup"><span data-stu-id="06f84-107">Can be any valid error number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06f84-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="06f84-108">Remarks</span></span>  
 <span data-ttu-id="06f84-109">`Error` Deyimi, geriye dönük uyumluluk için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="06f84-109">The `Error` statement is supported for backward compatibility.</span></span> <span data-ttu-id="06f84-110">Özellikle nesneleri oluştururken, yeni kodda, kullanın `Err` nesnenin `Raise` çalışma zamanı hataları oluşturmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="06f84-110">In new code, especially when creating objects, use the `Err` object's `Raise` method to generate run-time errors.</span></span>  
  
 <span data-ttu-id="06f84-111">Varsa `errornumber` tanımlanan `Error` deyimi özelliklerini sonra hata işleyici çağırır `Err` nesne aşağıdaki varsayılan değerler atanır:</span><span class="sxs-lookup"><span data-stu-id="06f84-111">If `errornumber` is defined, the `Error` statement calls the error handler after the properties of the `Err` object are assigned the following default values:</span></span>  
  
|<span data-ttu-id="06f84-112">Özellik</span><span class="sxs-lookup"><span data-stu-id="06f84-112">Property</span></span>|<span data-ttu-id="06f84-113">Değer</span><span class="sxs-lookup"><span data-stu-id="06f84-113">Value</span></span>|  
|--------------|-----------|  
|`Number`|<span data-ttu-id="06f84-114">Bağımsız değişkeni olarak belirtilen değeri `Error` deyimi.</span><span class="sxs-lookup"><span data-stu-id="06f84-114">Value specified as argument to `Error` statement.</span></span> <span data-ttu-id="06f84-115">Herhangi bir geçerli hata sayı olabilir.</span><span class="sxs-lookup"><span data-stu-id="06f84-115">Can be any valid error number.</span></span>|  
|`Source`|<span data-ttu-id="06f84-116">Geçerli Visual Basic proje adı.</span><span class="sxs-lookup"><span data-stu-id="06f84-116">Name of the current Visual Basic project.</span></span>|  
|`Description`|<span data-ttu-id="06f84-117">Dize ifadesi dönüş değerine karşılık gelen `Error` işlevi için belirtilen `Number`, bu dize varsa.</span><span class="sxs-lookup"><span data-stu-id="06f84-117">String expression corresponding to the return value of the `Error` function for the specified `Number`, if this string exists.</span></span> <span data-ttu-id="06f84-118">Dize mevcut değilse `Description` sıfır uzunlukta bir dize içeriyor ("").</span><span class="sxs-lookup"><span data-stu-id="06f84-118">If the string does not exist, `Description` contains a zero-length string ("").</span></span>|  
|`HelpFile`|<span data-ttu-id="06f84-119">Tam sürücü, yol ve uygun Visual Basic Yardım dosyasının dosya adı.</span><span class="sxs-lookup"><span data-stu-id="06f84-119">The fully qualified drive, path, and file name of the appropriate Visual Basic Help file.</span></span>|  
|`HelpContext`|<span data-ttu-id="06f84-120">Visual Basic uygun Yardım dosyası hata karşılık gelen için bağlam kimliği `Number` özelliği.</span><span class="sxs-lookup"><span data-stu-id="06f84-120">The appropriate Visual Basic Help file context ID for the error corresponding to the `Number` property.</span></span>|  
|`LastDLLError`|<span data-ttu-id="06f84-121">Sıfır.</span><span class="sxs-lookup"><span data-stu-id="06f84-121">Zero.</span></span>|  
  
 <span data-ttu-id="06f84-122">Hiçbir hata işleyici olup olmadığını veya hiçbiri etkinleştirilirse, hata iletisi oluşturulur ve gelen görüntülenen olmadığını `Err` nesne özellikleri.</span><span class="sxs-lookup"><span data-stu-id="06f84-122">If no error handler exists, or if none is enabled, an error message is created and displayed from the `Err` object properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06f84-123">Bazı Visual Basic konak uygulamaların nesneler oluşturamaz.</span><span class="sxs-lookup"><span data-stu-id="06f84-123">Some Visual Basic host applications cannot create objects.</span></span> <span data-ttu-id="06f84-124">Bunu sınıflar ve nesneler oluşturabilirsiniz olup olmadığını belirlemek için ana bilgisayar uygulamanızın belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="06f84-124">See your host application's documentation to determine whether it can create classes and objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06f84-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="06f84-125">Example</span></span>  
 <span data-ttu-id="06f84-126">Bu örnekte `Error` hata numarası 11 oluşturmak için ifade.</span><span class="sxs-lookup"><span data-stu-id="06f84-126">This example uses the `Error` statement to generate error number 11.</span></span>  
  
```  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a><span data-ttu-id="06f84-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="06f84-127">Requirements</span></span>  
 <span data-ttu-id="06f84-128">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="06f84-128">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="06f84-129">**Derleme:** Visual Basic çalışma zamanı kitaplığı (Microsoft.VisualBasic.dll içinde)</span><span class="sxs-lookup"><span data-stu-id="06f84-129">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06f84-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="06f84-130">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>  
 <xref:Microsoft.VisualBasic.Information.Err%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>  
 [<span data-ttu-id="06f84-131">On Error deyimi</span><span class="sxs-lookup"><span data-stu-id="06f84-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)  
 [<span data-ttu-id="06f84-132">Resume deyimi</span><span class="sxs-lookup"><span data-stu-id="06f84-132">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [<span data-ttu-id="06f84-133">Hata iletileri</span><span class="sxs-lookup"><span data-stu-id="06f84-133">Error Messages</span></span>](../../../visual-basic/language-reference/error-messages/index.md)
