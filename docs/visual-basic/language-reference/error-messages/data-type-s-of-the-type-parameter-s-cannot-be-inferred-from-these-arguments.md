---
title: Bu bağımsız değişkenlerden tür parametrelerinin veri türleri çıkarılamıyor
ms.date: 07/20/2015
f1_keywords:
- bc36644
- bc36647
- vbc36647
- vbc36644
helpviewer_keywords:
- BC36644
- BC36647
ms.assetid: 0e0050f2-2039-4311-b260-f0ebfde84189
ms.openlocfilehash: 91ee4bf9242df822890b0a171061f375a3b24cbc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803876"
---
# <a name="data-types-of-the-type-parameters-cannot-be-inferred-from-these-arguments"></a><span data-ttu-id="49030-102">Bu bağımsız değişkenlerden tür parametrelerinin veri türleri çıkarılamıyor</span><span class="sxs-lookup"><span data-stu-id="49030-102">Data type(s) of the type parameter(s) cannot be inferred from these arguments</span></span>
<span data-ttu-id="49030-103">Yöntemindeki tür parametrelerinin veri türleri bu bağımsız değişkenlerden çıkarsanamıyor.</span><span class="sxs-lookup"><span data-stu-id="49030-103">Data type(s) of the type parameter(s) cannot be inferred from these arguments.</span></span> <span data-ttu-id="49030-104">Verileri belirleyerek türleri açıkça bu hatayı düzeltebilir.</span><span class="sxs-lookup"><span data-stu-id="49030-104">Specifying the data type(s) explicitly might correct this error.</span></span>  
  
 <span data-ttu-id="49030-105">Aşırı yükleme çözümlemesi başarısız olduğunda bu hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="49030-105">This error occurs when overload resolution has failed.</span></span> <span data-ttu-id="49030-106">Belirli bir aşırı yükleme aday neden ortadan kaldırılmıştır bildiren bir alt ileti gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="49030-106">It occurs as a subordinate message that states why a particular overload candidate has been eliminated.</span></span> <span data-ttu-id="49030-107">Hata iletisi, tür parametreleri için veri türlerini bulmak için derleyicinin tür çıkarımı kullanamazsınız açıklar.</span><span class="sxs-lookup"><span data-stu-id="49030-107">The error message explains that the compiler cannot use type inference to find data types for the type parameters.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="49030-108">Bağımsız değişkenleri belirtme (örneğin, sorgu işleçleri için sorgu ifadelerinde) bir seçenek olmadığı durumlarda, ikinci cümlesi hata iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="49030-108">When specifying arguments is not an option (for example, for query operators in query expressions), the error message appears without the second sentence.</span></span>  
  
 <span data-ttu-id="49030-109">Aşağıdaki kod, hatayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="49030-109">The following code demonstrates the error.</span></span>  
  
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
  
 <span data-ttu-id="49030-110">**Hata Kimliği:** BC36647 ve BC36644</span><span class="sxs-lookup"><span data-stu-id="49030-110">**Error ID:** BC36647 and BC36644</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="49030-111">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="49030-111">To correct this error</span></span>  
  
- <span data-ttu-id="49030-112">Tür parametresi veya tür çıkarımı üzerinde kalmak yerine parametreleri için bir veri türü belirtmek mümkün olabilir.</span><span class="sxs-lookup"><span data-stu-id="49030-112">You may be able to specify a data type for the type parameter or parameters instead of relying on type inference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49030-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49030-113">See also</span></span>

- [<span data-ttu-id="49030-114">Gevşek Temsilci Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="49030-114">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [<span data-ttu-id="49030-115">Visual Basic'de genel yordamlar</span><span class="sxs-lookup"><span data-stu-id="49030-115">Generic Procedures in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)
- [<span data-ttu-id="49030-116">Visual Basic'de tür dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="49030-116">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
