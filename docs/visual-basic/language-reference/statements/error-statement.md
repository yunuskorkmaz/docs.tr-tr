---
description: 'Daha fazla bilgi edinin: hata açıklaması'
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
ms.openlocfilehash: 6c152e9e4fb4fa3a937042761c7d776b337f4fef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99769149"
---
# <a name="error-statement"></a><span data-ttu-id="ae060-103">Error Deyimi</span><span class="sxs-lookup"><span data-stu-id="ae060-103">Error Statement</span></span>

<span data-ttu-id="ae060-104">Bir hata oluşumunun benzetimini yapar.</span><span class="sxs-lookup"><span data-stu-id="ae060-104">Simulates the occurrence of an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae060-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ae060-105">Syntax</span></span>  
  
```vb  
Error errornumber  
```  
  
## <a name="parts"></a><span data-ttu-id="ae060-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="ae060-106">Parts</span></span>  

 `errornumber`  
 <span data-ttu-id="ae060-107">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ae060-107">Required.</span></span> <span data-ttu-id="ae060-108">Herhangi bir geçerli hata numarası olabilir.</span><span class="sxs-lookup"><span data-stu-id="ae060-108">Can be any valid error number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae060-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ae060-109">Remarks</span></span>  

 <span data-ttu-id="ae060-110">`Error`Bildirim, geriye dönük uyumluluk için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ae060-110">The `Error` statement is supported for backward compatibility.</span></span> <span data-ttu-id="ae060-111">Yeni kodda, özellikle nesne oluştururken, `Err` `Raise` çalışma zamanı hataları oluşturmak için nesnenin metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="ae060-111">In new code, especially when creating objects, use the `Err` object's `Raise` method to generate run-time errors.</span></span>  
  
 <span data-ttu-id="ae060-112">`errornumber`Tanımlanmışsa, `Error` `Err` nesne özellikleri aşağıdaki varsayılan değerlere atandıktan sonra ifade hata işleyicisini çağırır:</span><span class="sxs-lookup"><span data-stu-id="ae060-112">If `errornumber` is defined, the `Error` statement calls the error handler after the properties of the `Err` object are assigned the following default values:</span></span>  
  
|<span data-ttu-id="ae060-113">Özellik</span><span class="sxs-lookup"><span data-stu-id="ae060-113">Property</span></span>|<span data-ttu-id="ae060-114">Değer</span><span class="sxs-lookup"><span data-stu-id="ae060-114">Value</span></span>|  
|--------------|-----------|  
|`Number`|<span data-ttu-id="ae060-115">Deyimin bağımsız değişkeni olarak belirtilen değer `Error` .</span><span class="sxs-lookup"><span data-stu-id="ae060-115">Value specified as argument to `Error` statement.</span></span> <span data-ttu-id="ae060-116">Herhangi bir geçerli hata numarası olabilir.</span><span class="sxs-lookup"><span data-stu-id="ae060-116">Can be any valid error number.</span></span>|  
|`Source`|<span data-ttu-id="ae060-117">Geçerli Visual Basic projesinin adı.</span><span class="sxs-lookup"><span data-stu-id="ae060-117">Name of the current Visual Basic project.</span></span>|  
|`Description`|<span data-ttu-id="ae060-118">`Error`Bu dize varsa, belirtilen için işlevin dönüş değerine karşılık gelen dize ifadesi `Number` .</span><span class="sxs-lookup"><span data-stu-id="ae060-118">String expression corresponding to the return value of the `Error` function for the specified `Number`, if this string exists.</span></span> <span data-ttu-id="ae060-119">Dize yoksa, `Description` sıfır uzunluklu bir dize ("") içerir.</span><span class="sxs-lookup"><span data-stu-id="ae060-119">If the string does not exist, `Description` contains a zero-length string ("").</span></span>|  
|`HelpFile`|<span data-ttu-id="ae060-120">Uygun Visual Basic Yardım dosyasının tam sürücü, yol ve dosya adı.</span><span class="sxs-lookup"><span data-stu-id="ae060-120">The fully qualified drive, path, and file name of the appropriate Visual Basic Help file.</span></span>|  
|`HelpContext`|<span data-ttu-id="ae060-121">Özelliğe karşılık gelen hata için uygun Visual Basic Yardım dosyası bağlam KIMLIĞI `Number` .</span><span class="sxs-lookup"><span data-stu-id="ae060-121">The appropriate Visual Basic Help file context ID for the error corresponding to the `Number` property.</span></span>|  
|`LastDLLError`|<span data-ttu-id="ae060-122">Sıfır.</span><span class="sxs-lookup"><span data-stu-id="ae060-122">Zero.</span></span>|  
  
 <span data-ttu-id="ae060-123">Herhangi bir hata işleyicisi yoksa veya hiçbiri etkinleştirilmemişse, nesne özelliklerinden bir hata iletisi oluşturulur ve görüntülenir `Err` .</span><span class="sxs-lookup"><span data-stu-id="ae060-123">If no error handler exists, or if none is enabled, an error message is created and displayed from the `Err` object properties.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ae060-124">Bazı Visual Basic ana bilgisayar uygulamaları nesne oluşturamaz.</span><span class="sxs-lookup"><span data-stu-id="ae060-124">Some Visual Basic host applications cannot create objects.</span></span> <span data-ttu-id="ae060-125">Sınıf ve nesne oluşturup oluşturamayacağını öğrenmek için ana bilgisayar uygulamanızın belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="ae060-125">See your host application's documentation to determine whether it can create classes and objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae060-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="ae060-126">Example</span></span>  

 <span data-ttu-id="ae060-127">Bu örnek, `Error` 11 hata numarasını oluşturmak için ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ae060-127">This example uses the `Error` statement to generate error number 11.</span></span>  
  
```vb  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a><span data-ttu-id="ae060-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ae060-128">Requirements</span></span>  

 <span data-ttu-id="ae060-129">**Ad alanı:** [Microsoft. VisualBasic](../runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="ae060-129">**Namespace:** [Microsoft.VisualBasic](../runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="ae060-130">**Bütünleştirilmiş kod:** Visual Basic çalışma zamanı kitaplığı (Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="ae060-130">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae060-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae060-131">See also</span></span>

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [<span data-ttu-id="ae060-132">On Error Deyimi</span><span class="sxs-lookup"><span data-stu-id="ae060-132">On Error Statement</span></span>](on-error-statement.md)
- [<span data-ttu-id="ae060-133">Resume Deyimi</span><span class="sxs-lookup"><span data-stu-id="ae060-133">Resume Statement</span></span>](resume-statement.md)
- [<span data-ttu-id="ae060-134">Hata Iletileri</span><span class="sxs-lookup"><span data-stu-id="ae060-134">Error Messages</span></span>](../error-messages/index.md)
