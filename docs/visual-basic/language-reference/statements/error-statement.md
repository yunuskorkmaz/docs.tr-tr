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
ms.openlocfilehash: 35ba1f19654d1d23ac1ec73564bc36b0af4f6777
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404751"
---
# <a name="error-statement"></a><span data-ttu-id="ccc14-102">Error Deyimi</span><span class="sxs-lookup"><span data-stu-id="ccc14-102">Error Statement</span></span>
<span data-ttu-id="ccc14-103">Bir hata oluşumunun benzetimini yapar.</span><span class="sxs-lookup"><span data-stu-id="ccc14-103">Simulates the occurrence of an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccc14-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ccc14-104">Syntax</span></span>  
  
```vb  
Error errornumber  
```  
  
## <a name="parts"></a><span data-ttu-id="ccc14-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="ccc14-105">Parts</span></span>  
 `errornumber`  
 <span data-ttu-id="ccc14-106">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ccc14-106">Required.</span></span> <span data-ttu-id="ccc14-107">Herhangi bir geçerli hata numarası olabilir.</span><span class="sxs-lookup"><span data-stu-id="ccc14-107">Can be any valid error number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ccc14-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ccc14-108">Remarks</span></span>  
 <span data-ttu-id="ccc14-109">`Error`Bildirim, geriye dönük uyumluluk için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="ccc14-109">The `Error` statement is supported for backward compatibility.</span></span> <span data-ttu-id="ccc14-110">Yeni kodda, özellikle nesne oluştururken, `Err` `Raise` çalışma zamanı hataları oluşturmak için nesnenin metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="ccc14-110">In new code, especially when creating objects, use the `Err` object's `Raise` method to generate run-time errors.</span></span>  
  
 <span data-ttu-id="ccc14-111">`errornumber`Tanımlanmışsa, `Error` `Err` nesne özellikleri aşağıdaki varsayılan değerlere atandıktan sonra ifade hata işleyicisini çağırır:</span><span class="sxs-lookup"><span data-stu-id="ccc14-111">If `errornumber` is defined, the `Error` statement calls the error handler after the properties of the `Err` object are assigned the following default values:</span></span>  
  
|<span data-ttu-id="ccc14-112">Özellik</span><span class="sxs-lookup"><span data-stu-id="ccc14-112">Property</span></span>|<span data-ttu-id="ccc14-113">Değer</span><span class="sxs-lookup"><span data-stu-id="ccc14-113">Value</span></span>|  
|--------------|-----------|  
|`Number`|<span data-ttu-id="ccc14-114">Deyimin bağımsız değişkeni olarak belirtilen değer `Error` .</span><span class="sxs-lookup"><span data-stu-id="ccc14-114">Value specified as argument to `Error` statement.</span></span> <span data-ttu-id="ccc14-115">Herhangi bir geçerli hata numarası olabilir.</span><span class="sxs-lookup"><span data-stu-id="ccc14-115">Can be any valid error number.</span></span>|  
|`Source`|<span data-ttu-id="ccc14-116">Geçerli Visual Basic projesinin adı.</span><span class="sxs-lookup"><span data-stu-id="ccc14-116">Name of the current Visual Basic project.</span></span>|  
|`Description`|<span data-ttu-id="ccc14-117">`Error`Bu dize varsa, belirtilen için işlevin dönüş değerine karşılık gelen dize ifadesi `Number` .</span><span class="sxs-lookup"><span data-stu-id="ccc14-117">String expression corresponding to the return value of the `Error` function for the specified `Number`, if this string exists.</span></span> <span data-ttu-id="ccc14-118">Dize yoksa, `Description` sıfır uzunluklu bir dize ("") içerir.</span><span class="sxs-lookup"><span data-stu-id="ccc14-118">If the string does not exist, `Description` contains a zero-length string ("").</span></span>|  
|`HelpFile`|<span data-ttu-id="ccc14-119">Uygun Visual Basic Yardım dosyasının tam sürücü, yol ve dosya adı.</span><span class="sxs-lookup"><span data-stu-id="ccc14-119">The fully qualified drive, path, and file name of the appropriate Visual Basic Help file.</span></span>|  
|`HelpContext`|<span data-ttu-id="ccc14-120">Özelliğe karşılık gelen hata için uygun Visual Basic Yardım dosyası bağlam KIMLIĞI `Number` .</span><span class="sxs-lookup"><span data-stu-id="ccc14-120">The appropriate Visual Basic Help file context ID for the error corresponding to the `Number` property.</span></span>|  
|`LastDLLError`|<span data-ttu-id="ccc14-121">Sıfır.</span><span class="sxs-lookup"><span data-stu-id="ccc14-121">Zero.</span></span>|  
  
 <span data-ttu-id="ccc14-122">Herhangi bir hata işleyicisi yoksa veya hiçbiri etkinleştirilmemişse, nesne özelliklerinden bir hata iletisi oluşturulur ve görüntülenir `Err` .</span><span class="sxs-lookup"><span data-stu-id="ccc14-122">If no error handler exists, or if none is enabled, an error message is created and displayed from the `Err` object properties.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ccc14-123">Bazı Visual Basic ana bilgisayar uygulamaları nesne oluşturamaz.</span><span class="sxs-lookup"><span data-stu-id="ccc14-123">Some Visual Basic host applications cannot create objects.</span></span> <span data-ttu-id="ccc14-124">Sınıf ve nesne oluşturup oluşturamayacağını öğrenmek için ana bilgisayar uygulamanızın belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="ccc14-124">See your host application's documentation to determine whether it can create classes and objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ccc14-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="ccc14-125">Example</span></span>  
 <span data-ttu-id="ccc14-126">Bu örnek, `Error` 11 hata numarasını oluşturmak için ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ccc14-126">This example uses the `Error` statement to generate error number 11.</span></span>  
  
```vb  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a><span data-ttu-id="ccc14-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ccc14-127">Requirements</span></span>  
 <span data-ttu-id="ccc14-128">**Ad alanı:** [Microsoft. VisualBasic](../runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="ccc14-128">**Namespace:** [Microsoft.VisualBasic](../runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="ccc14-129">**Bütünleştirilmiş kod:** Visual Basic çalışma zamanı kitaplığı (Microsoft. VisualBasic. dll içinde)</span><span class="sxs-lookup"><span data-stu-id="ccc14-129">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccc14-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ccc14-130">See also</span></span>

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [<span data-ttu-id="ccc14-131">On Error Deyimi</span><span class="sxs-lookup"><span data-stu-id="ccc14-131">On Error Statement</span></span>](on-error-statement.md)
- [<span data-ttu-id="ccc14-132">Resume Deyimi</span><span class="sxs-lookup"><span data-stu-id="ccc14-132">Resume Statement</span></span>](resume-statement.md)
- [<span data-ttu-id="ccc14-133">Hata İletileri</span><span class="sxs-lookup"><span data-stu-id="ccc14-133">Error Messages</span></span>](../error-messages/index.md)
