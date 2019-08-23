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
ms.openlocfilehash: 867bf97ea13654de6f9c0209c64b9320824f9665
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931746"
---
# <a name="method-implementation-in-custom-controls"></a><span data-ttu-id="27a9c-102">Özel Denetimlerde Yöntem Uygulama</span><span class="sxs-lookup"><span data-stu-id="27a9c-102">Method Implementation in Custom Controls</span></span>
<span data-ttu-id="27a9c-103">Bir yöntem, bir denetime aynı şekilde, başka bir bileşende de uygulanacak şekilde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="27a9c-103">A method is implemented in a control in the same manner a method would be implemented in any other component.</span></span>  
  
 <span data-ttu-id="27a9c-104">Visual Basic, bir yöntemin bir değer döndürmesi gerekiyorsa, olarak `Public Function`uygulanır.</span><span class="sxs-lookup"><span data-stu-id="27a9c-104">In Visual Basic, if a method is required to return a value, it is implemented as a `Public Function`.</span></span> <span data-ttu-id="27a9c-105">Değer döndürülmezse, bir `Public Sub`olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="27a9c-105">If no value is returned, it is implemented as a `Public Sub`.</span></span> <span data-ttu-id="27a9c-106">Yöntemler aşağıdaki sözdizimi kullanılarak bildirilmiştir:</span><span class="sxs-lookup"><span data-stu-id="27a9c-106">Methods are declared using the following syntax:</span></span>  
  
```vb  
Public Function ConvertMatterToEnergy(Matter as Integer) As Integer  
   ' Conversion code goes here.  
End Function  
```  
  
 <span data-ttu-id="27a9c-107">İşlevler bir değer döndürdüğü için, tamsayı, dize, nesne vb. gibi bir dönüş türü belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="27a9c-107">Because functions return a value, they must specify a return type, such as integer, string, object, and so on.</span></span> <span data-ttu-id="27a9c-108">Varsa bağımsız `Function` değişkenler `Sub` veya yordamlar de belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="27a9c-108">The arguments `Function` or `Sub` procedures take, if any, must also be specified.</span></span>  
  
 <span data-ttu-id="27a9c-109">C#Visual Basic gibi işlevler ve yordamlar arasında ayrım yapmaz.</span><span class="sxs-lookup"><span data-stu-id="27a9c-109">C# makes no distinction between functions and procedures, as Visual Basic does.</span></span> <span data-ttu-id="27a9c-110">Bir yöntem bir değer ya da döndürür `void`.</span><span class="sxs-lookup"><span data-stu-id="27a9c-110">A method either returns a value or returns `void`.</span></span> <span data-ttu-id="27a9c-111">Ortak bir C# yöntemi bildirmek için sözdizimi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="27a9c-111">The syntax for declaring a C# public method is:</span></span>  
  
```csharp  
public int ConvertMatterToEnergy(int matter)  
{  
   // Conversion code goes here.  
}  
```  
  
 <span data-ttu-id="27a9c-112">Bir yöntemi bildirdiğinizde, tüm bağımsız değişkenlerini mümkün olduğunda açık veri türleri olarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="27a9c-112">When you declare a method, declare all of its arguments as explicit data types whenever possible.</span></span> <span data-ttu-id="27a9c-113">Nesne başvurularını alan bağımsız değişkenler belirli sınıf türleri olarak bildirilmelidir — Örneğin, `As Widget` `As Object`yerine.</span><span class="sxs-lookup"><span data-stu-id="27a9c-113">Arguments that take object references should be declared as specific class types — for example, `As Widget` instead of `As Object`.</span></span> <span data-ttu-id="27a9c-114">Visual Basic, varsayılan ayar `Option Strict` otomatik olarak bu kuralı zorlar.</span><span class="sxs-lookup"><span data-stu-id="27a9c-114">In Visual Basic, the default setting `Option Strict` automatically enforces this rule.</span></span>  
  
 <span data-ttu-id="27a9c-115">Yazılan bağımsız değişkenler, birçok geliştirici hatasının çalışma süresi yerine derleyici tarafından yakalanarak oluşmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="27a9c-115">Typed arguments allow many developer errors to be caught by the compiler, rather than at run time.</span></span> <span data-ttu-id="27a9c-116">Derleyici her zaman hataları yakalar, ancak çalışma zamanı testi yalnızca test paketi kadar iyidir.</span><span class="sxs-lookup"><span data-stu-id="27a9c-116">The compiler always catches errors, whereas run-time testing is only as good as the test suite.</span></span>  
  
## <a name="overloaded-methods"></a><span data-ttu-id="27a9c-117">Aşırı yüklenmiş yöntemler</span><span class="sxs-lookup"><span data-stu-id="27a9c-117">Overloaded Methods</span></span>  
 <span data-ttu-id="27a9c-118">Denetiminizin kullanıcılarının bir yönteme farklı parametre bileşimleri sağlamasına izin vermek istiyorsanız, açık veri türleri kullanarak yönteminin birden çok aşırı yüklemesini sağlayın.</span><span class="sxs-lookup"><span data-stu-id="27a9c-118">If you want to allow users of your control to supply different combinations of parameters to a method, provide multiple overloads of the method, using explicit data types.</span></span> <span data-ttu-id="27a9c-119">Herhangi bir veri türü `As Object` içerebilen bir parametre oluşturmaktan kaçının. Bu, test sırasında yakalanmayan hatalara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="27a9c-119">Avoid creating parameters declared `As Object` that can contain any data type, as this can lead to errors that might not be caught in testing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="27a9c-120">Ortak dil çalışma zamanındaki `Object` evrensel veri türü `Variant`yerine.</span><span class="sxs-lookup"><span data-stu-id="27a9c-120">The universal data type in the common language runtime is `Object` rather than `Variant`.</span></span> <span data-ttu-id="27a9c-121">`Variant`dilden kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="27a9c-121">`Variant` has been removed from the language.</span></span>  
  
 <span data-ttu-id="27a9c-122">Örneğin, `Spin` bir kuramsal `Widget` denetim yöntemi, doğrudan döndürme yönlerinin ve hızının belirtimindeki ya da angular itici güç 'in emin olduğu `Widget` başka bir nesnenin belirtimine izin verebilir:</span><span class="sxs-lookup"><span data-stu-id="27a9c-122">For example, the `Spin` method of a hypothetical `Widget` control might allow either direct specification of spin direction and speed, or specification of another `Widget` object from which angular momentum is to be absorbed:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="27a9c-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27a9c-123">See also</span></span>

- [<span data-ttu-id="27a9c-124">Olaylar</span><span class="sxs-lookup"><span data-stu-id="27a9c-124">Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="27a9c-125">Windows Forms Denetimlerindeki Özellikler</span><span class="sxs-lookup"><span data-stu-id="27a9c-125">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
