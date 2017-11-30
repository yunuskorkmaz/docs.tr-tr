---
title: "Bu bağımsız değişkenlerden tür parametrelerinin veri türleri çıkarılamıyor"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36644
- bc36647
- vbc36647
- vbc36644
helpviewer_keywords:
- BC36644
- BC36647
ms.assetid: 0e0050f2-2039-4311-b260-f0ebfde84189
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b290c25286dce2236823919e8287db9abefc0dd7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="data-types-of-the-type-parameters-cannot-be-inferred-from-these-arguments"></a><span data-ttu-id="16df7-102">Bu bağımsız değişkenlerden tür parametrelerinin veri türleri çıkarılamıyor</span><span class="sxs-lookup"><span data-stu-id="16df7-102">Data type(s) of the type parameter(s) cannot be inferred from these arguments</span></span>
<span data-ttu-id="16df7-103">Bu bağımsız değişkenlerden tür parametrelerinin veri türleri çıkarılamıyor.</span><span class="sxs-lookup"><span data-stu-id="16df7-103">Data type(s) of the type parameter(s) cannot be inferred from these arguments.</span></span> <span data-ttu-id="16df7-104">Verileri belirten türlerini açıkça bu hatayı düzeltmek.</span><span class="sxs-lookup"><span data-stu-id="16df7-104">Specifying the data type(s) explicitly might correct this error.</span></span>  
  
 <span data-ttu-id="16df7-105">Aşırı yükleme çözünürlüğü başarısız olduğunda bu hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="16df7-105">This error occurs when overload resolution has failed.</span></span> <span data-ttu-id="16df7-106">Neden belirli aşırı aday ortadan kaldırılmıştır bildiren bir alt ileti gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="16df7-106">It occurs as a subordinate message that states why a particular overload candidate has been eliminated.</span></span> <span data-ttu-id="16df7-107">Hata iletisi, veri türleri için tür parametreleri bulmak için derleyici tür çıkarımı kullanamazsınız açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="16df7-107">The error message explains that the compiler cannot use type inference to find data types for the type parameters.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16df7-108">Bağımsız değişkenleri (örneğin, sorgu işleçleri için sorgu ifadelerinde) bir seçenek olmadığı durumlarda, ikinci cümlesi hata iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="16df7-108">When specifying arguments is not an option (for example, for query operators in query expressions), the error message appears without the second sentence.</span></span>  
  
 <span data-ttu-id="16df7-109">Aşağıdaki kod hata gösterir.</span><span class="sxs-lookup"><span data-stu-id="16df7-109">The following code demonstrates the error.</span></span>  
  
```vb  
Module Module1  
  
    Sub Main()  
  
        '' Not Valid.  
        'OverloadedGenericMethod("Hello", "World")  
  
    End Sub  
  
    Sub OverloadedGenericMethod(Of T)(ByVal x As String,   
                                      ByVal y As InterfaceExample(Of T))  
    End Sub  
  
    Sub OverloadedGenericMethod(Of T, R)(ByVal x As T,   
                                         ByVal y As InterfaceExample(Of R))  
    End Sub  
  
End Module  
  
Interface InterfaceExample(Of T)  
End Interface  
```  
  
 <span data-ttu-id="16df7-110">**Hata Kimliği:** BC36647 ve BC36644</span><span class="sxs-lookup"><span data-stu-id="16df7-110">**Error ID:** BC36647 and BC36644</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="16df7-111">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="16df7-111">To correct this error</span></span>  
  
-   <span data-ttu-id="16df7-112">Tür parametresi veya tür çıkarımı kalmak yerine parametreleri için bir veri türü belirtmek mümkün olabilir.</span><span class="sxs-lookup"><span data-stu-id="16df7-112">You may be able to specify a data type for the type parameter or parameters instead of relying on type inference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16df7-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="16df7-113">See Also</span></span>  
 [<span data-ttu-id="16df7-114">Gevşek temsilci dönüşümü</span><span class="sxs-lookup"><span data-stu-id="16df7-114">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)  
 [<span data-ttu-id="16df7-115">Visual Basic'de genel yordamlar</span><span class="sxs-lookup"><span data-stu-id="16df7-115">Generic Procedures in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)  
 [<span data-ttu-id="16df7-116">Visual Basic'de tür dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="16df7-116">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
