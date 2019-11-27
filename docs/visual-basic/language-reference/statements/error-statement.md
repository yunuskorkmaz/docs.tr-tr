---
title: Error Deyimi
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
ms.openlocfilehash: 668ffbc7b8db73a706c5771bb0734a77f8fc0206
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351242"
---
# <a name="error-statement"></a><span data-ttu-id="f5c4e-102">Error Deyimi</span><span class="sxs-lookup"><span data-stu-id="f5c4e-102">Error Statement</span></span>
<span data-ttu-id="f5c4e-103">Bir hata oluşumunun benzetimini yapar.</span><span class="sxs-lookup"><span data-stu-id="f5c4e-103">Simulates the occurrence of an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5c4e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f5c4e-104">Syntax</span></span>  
  
```vb  
Error errornumber  
```  
  
## <a name="parts"></a><span data-ttu-id="f5c4e-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="f5c4e-105">Parts</span></span>  
 `errornumber`  
 <span data-ttu-id="f5c4e-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="f5c4e-106">Required.</span></span> <span data-ttu-id="f5c4e-107">Herhangi bir geçerli hata numarası olabilir.</span><span class="sxs-lookup"><span data-stu-id="f5c4e-107">Can be any valid error number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5c4e-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f5c4e-108">Remarks</span></span>  
 <span data-ttu-id="f5c4e-109">`Error` deyimleri geriye dönük uyumluluk için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="f5c4e-109">The `Error` statement is supported for backward compatibility.</span></span> <span data-ttu-id="f5c4e-110">Yeni kodda, özellikle nesne oluştururken, çalışma zamanı hataları oluşturmak için `Err` nesnenin `Raise` metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="f5c4e-110">In new code, especially when creating objects, use the `Err` object's `Raise` method to generate run-time errors.</span></span>  
  
 <span data-ttu-id="f5c4e-111">`errornumber` tanımlanmışsa, `Error` ifade, `Err` nesnesinin özelliklerine aşağıdaki varsayılan değerler atandıktan sonra hata işleyicisini çağırır:</span><span class="sxs-lookup"><span data-stu-id="f5c4e-111">If `errornumber` is defined, the `Error` statement calls the error handler after the properties of the `Err` object are assigned the following default values:</span></span>  
  
|<span data-ttu-id="f5c4e-112">Özellik</span><span class="sxs-lookup"><span data-stu-id="f5c4e-112">Property</span></span>|<span data-ttu-id="f5c4e-113">Value</span><span class="sxs-lookup"><span data-stu-id="f5c4e-113">Value</span></span>|  
|--------------|-----------|  
|`Number`|<span data-ttu-id="f5c4e-114">`Error` deyimin bağımsız değişkeni olarak belirtilen değer.</span><span class="sxs-lookup"><span data-stu-id="f5c4e-114">Value specified as argument to `Error` statement.</span></span> <span data-ttu-id="f5c4e-115">Herhangi bir geçerli hata numarası olabilir.</span><span class="sxs-lookup"><span data-stu-id="f5c4e-115">Can be any valid error number.</span></span>|  
|`Source`|<span data-ttu-id="f5c4e-116">Geçerli Visual Basic projesinin adı.</span><span class="sxs-lookup"><span data-stu-id="f5c4e-116">Name of the current Visual Basic project.</span></span>|  
|`Description`|<span data-ttu-id="f5c4e-117">Bu dize varsa, belirtilen `Number`için `Error` işlevinin dönüş değerine karşılık gelen dize ifadesi.</span><span class="sxs-lookup"><span data-stu-id="f5c4e-117">String expression corresponding to the return value of the `Error` function for the specified `Number`, if this string exists.</span></span> <span data-ttu-id="f5c4e-118">Dize yoksa, `Description` sıfır uzunluklu bir dize ("") içerir.</span><span class="sxs-lookup"><span data-stu-id="f5c4e-118">If the string does not exist, `Description` contains a zero-length string ("").</span></span>|  
|`HelpFile`|<span data-ttu-id="f5c4e-119">Uygun Visual Basic Yardım dosyasının tam sürücü, yol ve dosya adı.</span><span class="sxs-lookup"><span data-stu-id="f5c4e-119">The fully qualified drive, path, and file name of the appropriate Visual Basic Help file.</span></span>|  
|`HelpContext`|<span data-ttu-id="f5c4e-120">`Number` özelliğine karşılık gelen hata için uygun Visual Basic Yardım dosyası bağlam KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="f5c4e-120">The appropriate Visual Basic Help file context ID for the error corresponding to the `Number` property.</span></span>|  
|`LastDLLError`|<span data-ttu-id="f5c4e-121">Sıfırlama.</span><span class="sxs-lookup"><span data-stu-id="f5c4e-121">Zero.</span></span>|  
  
 <span data-ttu-id="f5c4e-122">Herhangi bir hata işleyicisi yoksa veya hiçbiri etkin değilse, `Err` nesne özelliklerinden bir hata iletisi oluşturulur ve görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f5c4e-122">If no error handler exists, or if none is enabled, an error message is created and displayed from the `Err` object properties.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f5c4e-123">Bazı Visual Basic ana bilgisayar uygulamaları nesne oluşturamaz.</span><span class="sxs-lookup"><span data-stu-id="f5c4e-123">Some Visual Basic host applications cannot create objects.</span></span> <span data-ttu-id="f5c4e-124">Sınıf ve nesne oluşturup oluşturamayacağını öğrenmek için ana bilgisayar uygulamanızın belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="f5c4e-124">See your host application's documentation to determine whether it can create classes and objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5c4e-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="f5c4e-125">Example</span></span>  
 <span data-ttu-id="f5c4e-126">Bu örnek, 11 hata numarasını oluşturmak için `Error` ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f5c4e-126">This example uses the `Error` statement to generate error number 11.</span></span>  
  
```vb  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a><span data-ttu-id="f5c4e-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f5c4e-127">Requirements</span></span>  
 <span data-ttu-id="f5c4e-128">**Ad alanı:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="f5c4e-128">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="f5c4e-129">**Bütünleştirilmiş kod:** Visual Basic çalışma zamanı kitaplığı (Microsoft. VisualBasic. dll içinde)</span><span class="sxs-lookup"><span data-stu-id="f5c4e-129">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5c4e-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5c4e-130">See also</span></span>

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [<span data-ttu-id="f5c4e-131">On Error Deyimi</span><span class="sxs-lookup"><span data-stu-id="f5c4e-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
- [<span data-ttu-id="f5c4e-132">Resume Deyimi</span><span class="sxs-lookup"><span data-stu-id="f5c4e-132">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)
- [<span data-ttu-id="f5c4e-133">Hata İletileri</span><span class="sxs-lookup"><span data-stu-id="f5c4e-133">Error Messages</span></span>](../../../visual-basic/language-reference/error-messages/index.md)
