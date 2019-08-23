---
title: Error bildirisi (Visual Basic)
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
ms.openlocfilehash: 7b926214d3be7f5f57783a8599acf1bb1042f956
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944451"
---
# <a name="error-statement"></a><span data-ttu-id="5cc8f-102">Error Deyimi</span><span class="sxs-lookup"><span data-stu-id="5cc8f-102">Error Statement</span></span>
<span data-ttu-id="5cc8f-103">Bir hata oluşumunun benzetimini yapar.</span><span class="sxs-lookup"><span data-stu-id="5cc8f-103">Simulates the occurrence of an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cc8f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5cc8f-104">Syntax</span></span>  
  
```  
Error errornumber  
```  
  
## <a name="parts"></a><span data-ttu-id="5cc8f-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="5cc8f-105">Parts</span></span>  
 `errornumber`  
 <span data-ttu-id="5cc8f-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="5cc8f-106">Required.</span></span> <span data-ttu-id="5cc8f-107">Herhangi bir geçerli hata numarası olabilir.</span><span class="sxs-lookup"><span data-stu-id="5cc8f-107">Can be any valid error number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5cc8f-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5cc8f-108">Remarks</span></span>  
 <span data-ttu-id="5cc8f-109">Bildirim `Error` , geriye dönük uyumluluk için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="5cc8f-109">The `Error` statement is supported for backward compatibility.</span></span> <span data-ttu-id="5cc8f-110">Yeni kodda, özellikle nesne oluştururken, çalışma zamanı hataları oluşturmak `Err` için `Raise` nesnenin metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="5cc8f-110">In new code, especially when creating objects, use the `Err` object's `Raise` method to generate run-time errors.</span></span>  
  
 <span data-ttu-id="5cc8f-111">Tanımlanmışsa, nesne özellikleri aşağıdaki varsayılan değerlere atandıktan sonraifadehataişleyicisiniçağırır:`Error` `Err` `errornumber`</span><span class="sxs-lookup"><span data-stu-id="5cc8f-111">If `errornumber` is defined, the `Error` statement calls the error handler after the properties of the `Err` object are assigned the following default values:</span></span>  
  
|<span data-ttu-id="5cc8f-112">Özellik</span><span class="sxs-lookup"><span data-stu-id="5cc8f-112">Property</span></span>|<span data-ttu-id="5cc8f-113">Değer</span><span class="sxs-lookup"><span data-stu-id="5cc8f-113">Value</span></span>|  
|--------------|-----------|  
|`Number`|<span data-ttu-id="5cc8f-114">`Error` Deyimin bağımsız değişkeni olarak belirtilen değer.</span><span class="sxs-lookup"><span data-stu-id="5cc8f-114">Value specified as argument to `Error` statement.</span></span> <span data-ttu-id="5cc8f-115">Herhangi bir geçerli hata numarası olabilir.</span><span class="sxs-lookup"><span data-stu-id="5cc8f-115">Can be any valid error number.</span></span>|  
|`Source`|<span data-ttu-id="5cc8f-116">Geçerli Visual Basic projesinin adı.</span><span class="sxs-lookup"><span data-stu-id="5cc8f-116">Name of the current Visual Basic project.</span></span>|  
|`Description`|<span data-ttu-id="5cc8f-117">Bu dize varsa, belirtilen `Error` `Number`için işlevin dönüş değerine karşılık gelen dize ifadesi.</span><span class="sxs-lookup"><span data-stu-id="5cc8f-117">String expression corresponding to the return value of the `Error` function for the specified `Number`, if this string exists.</span></span> <span data-ttu-id="5cc8f-118">Dize yoksa, `Description` sıfır uzunluklu bir dize ("") içerir.</span><span class="sxs-lookup"><span data-stu-id="5cc8f-118">If the string does not exist, `Description` contains a zero-length string ("").</span></span>|  
|`HelpFile`|<span data-ttu-id="5cc8f-119">Uygun Visual Basic Yardım dosyasının tam sürücü, yol ve dosya adı.</span><span class="sxs-lookup"><span data-stu-id="5cc8f-119">The fully qualified drive, path, and file name of the appropriate Visual Basic Help file.</span></span>|  
|`HelpContext`|<span data-ttu-id="5cc8f-120">`Number` Özelliğe karşılık gelen hata için uygun Visual Basic Yardım dosyası bağlam kimliği.</span><span class="sxs-lookup"><span data-stu-id="5cc8f-120">The appropriate Visual Basic Help file context ID for the error corresponding to the `Number` property.</span></span>|  
|`LastDLLError`|<span data-ttu-id="5cc8f-121">Sıfırlama.</span><span class="sxs-lookup"><span data-stu-id="5cc8f-121">Zero.</span></span>|  
  
 <span data-ttu-id="5cc8f-122">Herhangi bir hata işleyicisi yoksa veya hiçbiri etkinleştirilmemişse, `Err` nesne özelliklerinden bir hata iletisi oluşturulur ve görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5cc8f-122">If no error handler exists, or if none is enabled, an error message is created and displayed from the `Err` object properties.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5cc8f-123">Bazı Visual Basic ana bilgisayar uygulamaları nesne oluşturamaz.</span><span class="sxs-lookup"><span data-stu-id="5cc8f-123">Some Visual Basic host applications cannot create objects.</span></span> <span data-ttu-id="5cc8f-124">Sınıf ve nesne oluşturup oluşturamayacağını öğrenmek için ana bilgisayar uygulamanızın belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="5cc8f-124">See your host application's documentation to determine whether it can create classes and objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5cc8f-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="5cc8f-125">Example</span></span>  
 <span data-ttu-id="5cc8f-126">Bu örnek, `Error` 11 hata numarasını oluşturmak için ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="5cc8f-126">This example uses the `Error` statement to generate error number 11.</span></span>  
  
```  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a><span data-ttu-id="5cc8f-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5cc8f-127">Requirements</span></span>  
 <span data-ttu-id="5cc8f-128">**Uzayına** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="5cc8f-128">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="5cc8f-129">**Derleme** Visual Basic Çalışma Zamanı Kitaplığı (Microsoft.VisualBasic.dll içinde)</span><span class="sxs-lookup"><span data-stu-id="5cc8f-129">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cc8f-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5cc8f-130">See also</span></span>

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [<span data-ttu-id="5cc8f-131">On Error Deyimi</span><span class="sxs-lookup"><span data-stu-id="5cc8f-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
- [<span data-ttu-id="5cc8f-132">Resume Deyimi</span><span class="sxs-lookup"><span data-stu-id="5cc8f-132">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)
- [<span data-ttu-id="5cc8f-133">Hata İletileri</span><span class="sxs-lookup"><span data-stu-id="5cc8f-133">Error Messages</span></span>](../../../visual-basic/language-reference/error-messages/index.md)
