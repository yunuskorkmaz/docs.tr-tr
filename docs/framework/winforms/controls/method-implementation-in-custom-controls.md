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
ms.openlocfilehash: 9df2bc9257c3f697f30cbe8c679ffc88ec34517b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538119"
---
# <a name="method-implementation-in-custom-controls"></a><span data-ttu-id="ecc8b-102">Özel Denetimlerde Yöntem Uygulama</span><span class="sxs-lookup"><span data-stu-id="ecc8b-102">Method Implementation in Custom Controls</span></span>
<span data-ttu-id="ecc8b-103">Bir yöntem bir denetimde bir yöntem içindeki herhangi bir bileşen uygulanması aynı şekilde uygulanır.</span><span class="sxs-lookup"><span data-stu-id="ecc8b-103">A method is implemented in a control in the same manner a method would be implemented in any other component.</span></span>  
  
 <span data-ttu-id="ecc8b-104">Bir yöntem için bir değer döndürmek için gerekliyse, Visual Basic'te şu olarak uygulanan bir `Public Function`.</span><span class="sxs-lookup"><span data-stu-id="ecc8b-104">In Visual Basic, if a method is required to return a value, it is implemented as a `Public Function`.</span></span> <span data-ttu-id="ecc8b-105">Herhangi bir değer döndürürse, olarak uygulandığı bir `Public Sub`.</span><span class="sxs-lookup"><span data-stu-id="ecc8b-105">If no value is returned, it is implemented as a `Public Sub`.</span></span> <span data-ttu-id="ecc8b-106">Yöntemleri aşağıdaki sözdizimini kullanarak bildirilir:</span><span class="sxs-lookup"><span data-stu-id="ecc8b-106">Methods are declared using the following syntax:</span></span>  
  
```vb  
Public Function ConvertMatterToEnergy(Matter as Integer) As Integer  
   ' Conversion code goes here.  
End Function  
```  
  
 <span data-ttu-id="ecc8b-107">İşlevler bir değer döndürür olduğundan, tamsayı, dize, nesne vb. gibi bir dönüş türü belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ecc8b-107">Because functions return a value, they must specify a return type, such as integer, string, object, and so on.</span></span> <span data-ttu-id="ecc8b-108">Bağımsız değişkenler `Function` veya `Sub` herhangi biri, aynı zamanda belirtilmesi gerekir, yordamları gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="ecc8b-108">The arguments `Function` or `Sub` procedures take, if any, must also be specified.</span></span>  
  
 <span data-ttu-id="ecc8b-109">Visual Basic yaptığı gibi C# işlevleri ve yordamlar arasında ayrım sağlar.</span><span class="sxs-lookup"><span data-stu-id="ecc8b-109">C# makes no distinction between functions and procedures, as Visual Basic does.</span></span> <span data-ttu-id="ecc8b-110">Bir yöntemi bir değer döndürür veya verir `void`.</span><span class="sxs-lookup"><span data-stu-id="ecc8b-110">A method either returns a value or returns `void`.</span></span> <span data-ttu-id="ecc8b-111">Bir C# genel yöntem bildirmek için sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="ecc8b-111">The syntax for declaring a C# public method is:</span></span>  
  
```csharp  
public int ConvertMatterToEnergy(int matter)  
{  
   // Conversion code goes here.  
}  
```  
  
 <span data-ttu-id="ecc8b-112">Bir yöntem bildirin, tüm bağımsız değişkenlerinin açık veri türleri olarak mümkün olduğunca bildirin.</span><span class="sxs-lookup"><span data-stu-id="ecc8b-112">When you declare a method, declare all of its arguments as explicit data types whenever possible.</span></span> <span data-ttu-id="ecc8b-113">Nesne başvuruları ele bağımsız değişkenleri belirli bir sınıf türü olarak bildirilmiş — Örneğin, `As Widget` yerine `As Object`.</span><span class="sxs-lookup"><span data-stu-id="ecc8b-113">Arguments that take object references should be declared as specific class types — for example, `As Widget` instead of `As Object`.</span></span> <span data-ttu-id="ecc8b-114">Visual Basic'de varsayılan ayar `Option Strict` otomatik olarak bu kural zorlar.</span><span class="sxs-lookup"><span data-stu-id="ecc8b-114">In Visual Basic, the default setting `Option Strict` automatically enforces this rule.</span></span>  
  
 <span data-ttu-id="ecc8b-115">Yazılı bağımsız değişkenler derleyici yerine çalışma zamanında Yakalanacak birçok geliştirici hata izin verir.</span><span class="sxs-lookup"><span data-stu-id="ecc8b-115">Typed arguments allow many developer errors to be caught by the compiler, rather than at run time.</span></span> <span data-ttu-id="ecc8b-116">Çalışma zamanı test yalnızca test paketi kadar iyi iken derleyici hataları, her zaman yakalar.</span><span class="sxs-lookup"><span data-stu-id="ecc8b-116">The compiler always catches errors, whereas run-time testing is only as good as the test suite.</span></span>  
  
## <a name="overloaded-methods"></a><span data-ttu-id="ecc8b-117">Aşırı yüklenmiş yöntemler</span><span class="sxs-lookup"><span data-stu-id="ecc8b-117">Overloaded Methods</span></span>  
 <span data-ttu-id="ecc8b-118">Farklı bir yöntem için parametre birleşimleri sağlamak kullanıcıların denetiminizin izin vermek istiyorsanız, birden çok aşırı açık veri türlerini kullanma yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="ecc8b-118">If you want to allow users of your control to supply different combinations of parameters to a method, provide multiple overloads of the method, using explicit data types.</span></span> <span data-ttu-id="ecc8b-119">Bildirilen parametreleri oluşturmamak `As Object` , içerebilir herhangi bir veri türü olarak bu testinde yakalandı hatalara yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="ecc8b-119">Avoid creating parameters declared `As Object` that can contain any data type, as this can lead to errors that might not be caught in testing.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ecc8b-120">Ortak dil çalışma zamanında evrensel veri türü `Object` yerine `Variant`.</span><span class="sxs-lookup"><span data-stu-id="ecc8b-120">The universal data type in the common language runtime is `Object` rather than `Variant`.</span></span> <span data-ttu-id="ecc8b-121">`Variant` dilden kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="ecc8b-121">`Variant` has been removed from the language.</span></span>  
  
 <span data-ttu-id="ecc8b-122">Örneğin, `Spin` bir kuramsal yöntemi `Widget` denetimi izin döndürme yön ve hız doğrudan belirtimi ya da başka bir belirtim `Widget` hangi angular satışlarının nesnesinden olduğu absorbed olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="ecc8b-122">For example, the `Spin` method of a hypothetical `Widget` control might allow either direct specification of spin direction and speed, or specification of another `Widget` object from which angular momentum is to be absorbed:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ecc8b-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ecc8b-123">See Also</span></span>  
 [<span data-ttu-id="ecc8b-124">Olaylar</span><span class="sxs-lookup"><span data-stu-id="ecc8b-124">Events</span></span>](../../../../docs/standard/events/index.md)  
 [<span data-ttu-id="ecc8b-125">Windows Forms Denetimlerindeki Özellikler</span><span class="sxs-lookup"><span data-stu-id="ecc8b-125">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)
