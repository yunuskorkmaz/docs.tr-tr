---
title: "Nasıl yapılır: Boş Değer Atanabilir bir Tür Belirleme (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- nullable types [C#], identifying
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 610ed18308df02c5632361cd09ef94330dea598b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-identify-a-nullable-type-c-programming-guide"></a><span data-ttu-id="7a62b-102">Nasıl yapılır: Boş Değer Atanabilir bir Tür Belirleme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="7a62b-102">How to: Identify a Nullable Type (C# Programming Guide)</span></span>
<span data-ttu-id="7a62b-103">C# kullanabilirsiniz [typeof](../../../csharp/language-reference/keywords/typeof.md) oluşturmak için işleç bir <xref:System.Type> null atanabilir bir tür temsil eden nesnesi:</span><span class="sxs-lookup"><span data-stu-id="7a62b-103">You can use the C# [typeof](../../../csharp/language-reference/keywords/typeof.md) operator to create a <xref:System.Type> object that represents a Nullable type:</span></span>  
  
```  
System.Type type = typeof(int?);  
```  
  
 <span data-ttu-id="7a62b-104">Sınıflar ve yöntemler birini de kullanabilirsiniz <xref:System.Reflection> oluşturmak için ad alanı <xref:System.Type> boş değer atanabilir türleri temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="7a62b-104">You can also use the classes and methods of the <xref:System.Reflection> namespace to generate <xref:System.Type> objects that represent Nullable types.</span></span> <span data-ttu-id="7a62b-105">Ancak, kullanarak boş değer atanabilir değişkenlerden çalışma zamanında tür bilgilerini edinmek için deneyin <xref:System.Object.GetType%2A> yöntemi veya `is` işleç sonucu olan bir <xref:System.Type> temel alınan türü, null atanabilir olmayan temsil eden nesnesi kendisini yazın.</span><span class="sxs-lookup"><span data-stu-id="7a62b-105">However, if you try to obtain type information from Nullable variables at runtime by using the <xref:System.Object.GetType%2A> method or the `is` operator, the result is a <xref:System.Type> object that represents the underlying type, not the Nullable type itself.</span></span>  
  
 <span data-ttu-id="7a62b-106">Çağırma `GetType` üzerinde null atanabilir tür türü örtük olarak dönüştürülür olduğunda gerçekleştirilecek kutulama işlemi neden <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="7a62b-106">Calling `GetType` on a Nullable type causes a boxing operation to be performed when the type is implicitly converted to <xref:System.Object>.</span></span> <span data-ttu-id="7a62b-107">Bu nedenle <xref:System.Object.GetType%2A> her zaman döndüren bir <xref:System.Type> temel alınan türü, boş değer atanabilir tür temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="7a62b-107">Therefore <xref:System.Object.GetType%2A> always returns a <xref:System.Type> object that represents the underlying type, not the Nullable type.</span></span>  
  
```  
int? i = 5;  
Type t = i.GetType();  
Console.WriteLine(t.FullName); //"System.Int32"  
```  
  
 <span data-ttu-id="7a62b-108">C# [olan](../../../csharp/language-reference/keywords/is.md) işleci null atanabilir'ın temel alınan tür üzerinde de çalışır.</span><span class="sxs-lookup"><span data-stu-id="7a62b-108">The C# [is](../../../csharp/language-reference/keywords/is.md) operator also operates on a Nullable's underlying type.</span></span> <span data-ttu-id="7a62b-109">Bu nedenle kullanamazsınız `is` bir değişken null atanabilir bir tür olup olmadığını belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="7a62b-109">Therefore you cannot use `is` to determine whether a variable is a Nullable type.</span></span> <span data-ttu-id="7a62b-110">Aşağıdaki örnekte gösterilir `is` işleci değerlendirir bir null atanabilir\<int > bir tamsayı olarak değişken</span><span class="sxs-lookup"><span data-stu-id="7a62b-110">The following example shows that the `is` operator treats a Nullable\<int> variable as an int.</span></span>  
  
```  
static void Main(string[] args)  
{  
  int? i = 5;  
  if (i is int) // true  
    //…  
}  
```  
  
## <a name="example"></a><span data-ttu-id="7a62b-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="7a62b-111">Example</span></span>  
 <span data-ttu-id="7a62b-112">Belirlemek için aşağıdaki kodu kullanmak isteyip bir <xref:System.Type> nesnesi, null atanabilir bir tür temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7a62b-112">Use the following code to determine whether a <xref:System.Type> object represents a Nullable type.</span></span> <span data-ttu-id="7a62b-113">Bu kodu yanlış olmadığını her zaman döndürdüğünü unutmayın `Type` çağrısından döndürülen nesne <xref:System.Object.GetType%2A>, bu konunun önceki kısımlarında açıklandığı gibi.</span><span class="sxs-lookup"><span data-stu-id="7a62b-113">Remember that this code always returns false if the `Type` object was returned from a call to <xref:System.Object.GetType%2A>, as explained earlier in this topic.</span></span>  
  
```  
if (type.IsGenericType && type.GetGenericTypeDefinition() == typeof(Nullable<>)) {…}  
```  
  
## <a name="see-also"></a><span data-ttu-id="7a62b-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7a62b-114">See Also</span></span>  
 [<span data-ttu-id="7a62b-115">Boş değer atanabilir türler</span><span class="sxs-lookup"><span data-stu-id="7a62b-115">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
 [<span data-ttu-id="7a62b-116">Boş değer atanabilir türleri kutulama</span><span class="sxs-lookup"><span data-stu-id="7a62b-116">Boxing Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)
