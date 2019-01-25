---
title: Özel Denetimlerde Yöntem Uygulama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user controls [Windows Forms], method implementation
- custom controls [Windows Forms], overloading methods
- custom controls [Windows Forms], method implementation
- methods [Windows Forms]
- methods [Windows Forms], custom controls
ms.assetid: 35d14fca-4bb4-4a27-8211-1f7a98ea27de
ms.openlocfilehash: f65c34c965ddf19c7a287eeeaafe2583c97583ef
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506076"
---
# <a name="method-implementation-in-custom-controls"></a><span data-ttu-id="2eeb8-102">Özel Denetimlerde Yöntem Uygulama</span><span class="sxs-lookup"><span data-stu-id="2eeb8-102">Method Implementation in Custom Controls</span></span>
<span data-ttu-id="2eeb8-103">Bir yöntem bir denetimde bir yöntem içinde başka bir bileşen uygulanması aynı şekilde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="2eeb8-103">A method is implemented in a control in the same manner a method would be implemented in any other component.</span></span>  
  
 <span data-ttu-id="2eeb8-104">Bir yöntem bir değer döndürmesi gerekiyorsa Visual Basic'te olarak uygulandığı bir `Public Function`.</span><span class="sxs-lookup"><span data-stu-id="2eeb8-104">In Visual Basic, if a method is required to return a value, it is implemented as a `Public Function`.</span></span> <span data-ttu-id="2eeb8-105">Herhangi bir değer döndürülürse, olarak uygulandığı bir `Public Sub`.</span><span class="sxs-lookup"><span data-stu-id="2eeb8-105">If no value is returned, it is implemented as a `Public Sub`.</span></span> <span data-ttu-id="2eeb8-106">Yöntemleri, aşağıdaki sözdizimini kullanarak bildirilir:</span><span class="sxs-lookup"><span data-stu-id="2eeb8-106">Methods are declared using the following syntax:</span></span>  
  
```vb  
Public Function ConvertMatterToEnergy(Matter as Integer) As Integer  
   ' Conversion code goes here.  
End Function  
```  
  
 <span data-ttu-id="2eeb8-107">İşlevler bir değer döndürdüğünden, tamsayı, dize, nesne ve benzeri gibi bir dönüş türü belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2eeb8-107">Because functions return a value, they must specify a return type, such as integer, string, object, and so on.</span></span> <span data-ttu-id="2eeb8-108">Bağımsız değişkenler `Function` veya `Sub` herhangi biri, ayrıca belirtilmesi gerekir, yordamları Al.</span><span class="sxs-lookup"><span data-stu-id="2eeb8-108">The arguments `Function` or `Sub` procedures take, if any, must also be specified.</span></span>  
  
 <span data-ttu-id="2eeb8-109">C#Visual Basic gibi işlevleri ve yordamları arasında bir ayrım yapar.</span><span class="sxs-lookup"><span data-stu-id="2eeb8-109">C# makes no distinction between functions and procedures, as Visual Basic does.</span></span> <span data-ttu-id="2eeb8-110">Bir yöntem bir değer döndürür veya döndürür `void`.</span><span class="sxs-lookup"><span data-stu-id="2eeb8-110">A method either returns a value or returns `void`.</span></span> <span data-ttu-id="2eeb8-111">Bildirmek için söz dizimi bir C# genel yöntemdir:</span><span class="sxs-lookup"><span data-stu-id="2eeb8-111">The syntax for declaring a C# public method is:</span></span>  
  
```csharp  
public int ConvertMatterToEnergy(int matter)  
{  
   // Conversion code goes here.  
}  
```  
  
 <span data-ttu-id="2eeb8-112">Tüm bağımsız değişkenleri, bir yöntem bildirdiğinizde, mümkün olduğunda açık veri türleri olarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="2eeb8-112">When you declare a method, declare all of its arguments as explicit data types whenever possible.</span></span> <span data-ttu-id="2eeb8-113">Nesne başvurularını alan bağımsız değişkenleri belirli sınıf türleri bildirilmelidir — Örneğin, `As Widget` yerine `As Object`.</span><span class="sxs-lookup"><span data-stu-id="2eeb8-113">Arguments that take object references should be declared as specific class types — for example, `As Widget` instead of `As Object`.</span></span> <span data-ttu-id="2eeb8-114">Visual Basic'te, varsayılan ayarı `Option Strict` otomatik olarak bu kural uygular.</span><span class="sxs-lookup"><span data-stu-id="2eeb8-114">In Visual Basic, the default setting `Option Strict` automatically enforces this rule.</span></span>  
  
 <span data-ttu-id="2eeb8-115">Yazılı bağımsız değişkenler, birçok geliştirici hataları çalışma zamanında değil, derleyici tarafından yakalanan izin verin.</span><span class="sxs-lookup"><span data-stu-id="2eeb8-115">Typed arguments allow many developer errors to be caught by the compiler, rather than at run time.</span></span> <span data-ttu-id="2eeb8-116">Çalışma zamanı sınaması yalnızca test paketi iyidir ancak derleyici her zaman hataları yakalar.</span><span class="sxs-lookup"><span data-stu-id="2eeb8-116">The compiler always catches errors, whereas run-time testing is only as good as the test suite.</span></span>  
  
## <a name="overloaded-methods"></a><span data-ttu-id="2eeb8-117">Aşırı yüklenmiş yöntemler</span><span class="sxs-lookup"><span data-stu-id="2eeb8-117">Overloaded Methods</span></span>  
 <span data-ttu-id="2eeb8-118">Bir yöntem için parametrelerin farklı birleşimlerini sağlamak üzere kullanıcı denetiminizin izin vermek istiyorsanız, birden çok aşırı yükleme açık veri türleri kullanılarak yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="2eeb8-118">If you want to allow users of your control to supply different combinations of parameters to a method, provide multiple overloads of the method, using explicit data types.</span></span> <span data-ttu-id="2eeb8-119">Olarak bildirilen parametreleri oluşturmaktan kaçının `As Object` dahil olabilir herhangi bir veri türü olarak bu sınamada Yakalanacak değil hatalara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="2eeb8-119">Avoid creating parameters declared `As Object` that can contain any data type, as this can lead to errors that might not be caught in testing.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2eeb8-120">Evrensel veri türü ortak dil çalışma zamanı `Object` yerine `Variant`.</span><span class="sxs-lookup"><span data-stu-id="2eeb8-120">The universal data type in the common language runtime is `Object` rather than `Variant`.</span></span> <span data-ttu-id="2eeb8-121">`Variant` dili kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="2eeb8-121">`Variant` has been removed from the language.</span></span>  
  
 <span data-ttu-id="2eeb8-122">Örneğin, `Spin` bir kuramsal yöntemi `Widget` denetimi izin döndürme yön ve hız doğrudan belirtimi veya başka bir belirtim `Widget` hangi angular İtici Güç nesnesinden olan absorbed olacak:</span><span class="sxs-lookup"><span data-stu-id="2eeb8-122">For example, the `Spin` method of a hypothetical `Widget` control might allow either direct specification of spin direction and speed, or specification of another `Widget` object from which angular momentum is to be absorbed:</span></span>  
  
```vb  
Overloads Public Sub Spin( _  
   ByVal SpinDirection As SpinDirectionsEnum, _  
   ByVal RevolutionsPerSecond As Double)  
   ' Implementation code here.  
End Sub  
Overloads Public Sub Spin(ByVal Driver As Widget) _  
   ' Implementation code here.  
End Sub  
```  
  
```csharp  
public void Spin(SpinDirectionsEnum spinDirection, double revolutionsPerSecond)  
{  
   // Implementation code here.  
}  
  
public void Spin(Widget driver)  
{  
   // Implementation code here.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="2eeb8-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2eeb8-123">See also</span></span>
- [<span data-ttu-id="2eeb8-124">Olaylar</span><span class="sxs-lookup"><span data-stu-id="2eeb8-124">Events</span></span>](../../../../docs/standard/events/index.md)
- [<span data-ttu-id="2eeb8-125">Windows Forms Denetimlerindeki Özellikler</span><span class="sxs-lookup"><span data-stu-id="2eeb8-125">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)
