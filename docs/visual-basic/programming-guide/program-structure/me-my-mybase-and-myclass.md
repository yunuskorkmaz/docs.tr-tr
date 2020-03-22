---
title: Me, My, MyBase ve MyClass
ms.date: 07/20/2015
f1_keywords:
- MyClass
- vb.Me
- MyBase
- vb.MyBase
- Me
- vb.MyClass
- vb.This
- vb.My
helpviewer_keywords:
- My object
- self-reference [Visual Basic], Me keyword
- MyClass keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], referring to the current instance of an object
- Me keyword [Visual Basic]
- self-reference
- current instance [Visual Basic], Me keyword
- MyBase keyword [Visual Basic], relationship to similar programming elements
ms.assetid: f8e241ae-b1ed-4886-9aa0-08c632154029
ms.openlocfilehash: a21dfeb12e8d99f5f8b8afede084846711c299ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400850"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a><span data-ttu-id="62bcb-102">Visual Basic'de Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="62bcb-102">Me, My, MyBase, and MyClass in Visual Basic</span></span>
<span data-ttu-id="62bcb-103">`Me`, `My` `MyBase`, `MyClass` , , ve Visual Basic'te benzer adlar vardır, ancak farklı amaçlara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="62bcb-103">`Me`, `My`, `MyBase`, and `MyClass` in Visual Basic have similar names, but different purposes.</span></span> <span data-ttu-id="62bcb-104">Bu konu, bunları ayırt etmek için bu varlıkların her birini açıklar.</span><span class="sxs-lookup"><span data-stu-id="62bcb-104">This topic describes each of these entities in order to distinguish them.</span></span>  
  
## <a name="me"></a><span data-ttu-id="62bcb-105">Ben</span><span class="sxs-lookup"><span data-stu-id="62bcb-105">Me</span></span>  
 <span data-ttu-id="62bcb-106">Anahtar `Me` kelime, kodun şu anda yürütüldettiği bir sınıfın veya yapının belirli örneğine başvurmak için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="62bcb-106">The `Me` keyword provides a way to refer to the specific instance of a class or structure in which the code is currently executing.</span></span> <span data-ttu-id="62bcb-107">`Me`bir nesne değişkeni veya geçerli örne atıfta bulunan bir yapı değişkeni gibi olur.</span><span class="sxs-lookup"><span data-stu-id="62bcb-107">`Me` behaves like either an object variable or a structure variable referring to the current instance.</span></span> <span data-ttu-id="62bcb-108">Kullanmak, `Me` özellikle bir sınıfın veya yapının şu anda yürütülen örneği hakkında başka bir sınıf, yapı veya modüldeki bir yordamhakkında bilgi aktarmak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="62bcb-108">Using `Me` is particularly useful for passing information about the currently executing instance of a class or structure to a procedure in another class, structure, or module.</span></span>  
  
 <span data-ttu-id="62bcb-109">Örneğin, bir modülde aşağıdaki yordamı gördüğünüzün olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="62bcb-109">For example, suppose you have the following procedure in a module.</span></span>  
  
```vb  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 <span data-ttu-id="62bcb-110">Aşağıdaki deyimi kullanarak bu yordamı arayabilir <xref:System.Windows.Forms.Form> ve sınıfın geçerli örneğini bağımsız değişken olarak geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62bcb-110">You can call this procedure and pass the current instance of the <xref:System.Windows.Forms.Form> class as an argument by using the following statement.</span></span>  
  
```vb  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a><span data-ttu-id="62bcb-111">Benim</span><span class="sxs-lookup"><span data-stu-id="62bcb-111">My</span></span>  
 <span data-ttu-id="62bcb-112">Bu `My` özellik, Visual Basic kullanıcısının bilgisayar, uygulama, ayarlar, kaynaklar ve benzeri şeylerle etkileşimkurmasını sağlayarak bir dizi .NET Framework sınıfına kolay ve sezgisel erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="62bcb-112">The `My` feature provides easy and intuitive access to a number of .NET Framework classes, enabling the Visual Basic user to interact with the computer, application, settings, resources, and so on.</span></span>  
  
## <a name="mybase"></a><span data-ttu-id="62bcb-113">Mybase</span><span class="sxs-lookup"><span data-stu-id="62bcb-113">MyBase</span></span>  
 <span data-ttu-id="62bcb-114">Anahtar `MyBase` kelime, bir sınıfın geçerli örneğinin taban sınıfına atıfta bulunan bir nesne değişkeni gibi olur.</span><span class="sxs-lookup"><span data-stu-id="62bcb-114">The `MyBase` keyword behaves like an object variable referring to the base class of the current instance of a class.</span></span> <span data-ttu-id="62bcb-115">`MyBase`türemiş bir sınıfta geçersiz kılınan veya gölgelenen taban sınıf üyelerine erişmek için genellikle kullanılır.</span><span class="sxs-lookup"><span data-stu-id="62bcb-115">`MyBase` is commonly used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="62bcb-116">`MyBase.New`türemiş bir sınıf oluşturucudan taban sınıf oluşturucusu çağırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="62bcb-116">`MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>  
  
## <a name="myclass"></a><span data-ttu-id="62bcb-117">Myclass</span><span class="sxs-lookup"><span data-stu-id="62bcb-117">MyClass</span></span>  
 <span data-ttu-id="62bcb-118">Anahtar `MyClass` kelime, başlangıçta uygulanan bir sınıfın geçerli örneğine atıfta bulunan bir nesne değişkeni gibi olur.</span><span class="sxs-lookup"><span data-stu-id="62bcb-118">The `MyClass` keyword behaves like an object variable referring to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="62bcb-119">`MyClass``Me`benzer, ancak tüm yöntem çağrıları yöntem gibi `NotOverridable`kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="62bcb-119">`MyClass` is similar to `Me`, but all method calls on it are treated as if the method were `NotOverridable`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62bcb-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62bcb-120">See also</span></span>

- [<span data-ttu-id="62bcb-121">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="62bcb-121">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
