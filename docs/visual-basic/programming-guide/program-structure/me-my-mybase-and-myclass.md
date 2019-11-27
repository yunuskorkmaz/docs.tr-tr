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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347345"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a><span data-ttu-id="08cd6-102">Visual Basic'de Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="08cd6-102">Me, My, MyBase, and MyClass in Visual Basic</span></span>
<span data-ttu-id="08cd6-103">Visual Basic 'de `Me`, `My`, `MyBase`ve `MyClass` benzer adlara sahiptir ancak farklı amaçlar vardır.</span><span class="sxs-lookup"><span data-stu-id="08cd6-103">`Me`, `My`, `MyBase`, and `MyClass` in Visual Basic have similar names, but different purposes.</span></span> <span data-ttu-id="08cd6-104">Bu konu, bu varlıkların her birini ayırt edebilmek için açıklar.</span><span class="sxs-lookup"><span data-stu-id="08cd6-104">This topic describes each of these entities in order to distinguish them.</span></span>  
  
## <a name="me"></a><span data-ttu-id="08cd6-105">Beni</span><span class="sxs-lookup"><span data-stu-id="08cd6-105">Me</span></span>  
 <span data-ttu-id="08cd6-106">`Me` anahtar sözcüğü, kodun Şu anda yürütüldüğü bir sınıfın veya yapının belirli bir örneğine başvurmak için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="08cd6-106">The `Me` keyword provides a way to refer to the specific instance of a class or structure in which the code is currently executing.</span></span> <span data-ttu-id="08cd6-107">`Me`, nesne değişkeni ya da geçerli örneğe başvuran bir yapı değişkeni gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="08cd6-107">`Me` behaves like either an object variable or a structure variable referring to the current instance.</span></span> <span data-ttu-id="08cd6-108">`Me` kullanmak, bir sınıfın veya yapının Şu anda yürütülmekte olan örneği hakkındaki bilgileri başka bir sınıf, yapı veya modüldeki bir yordama iletmek için özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="08cd6-108">Using `Me` is particularly useful for passing information about the currently executing instance of a class or structure to a procedure in another class, structure, or module.</span></span>  
  
 <span data-ttu-id="08cd6-109">Örneğin, bir modülde aşağıdaki yordama sahip olduğunuzu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="08cd6-109">For example, suppose you have the following procedure in a module.</span></span>  
  
```vb  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 <span data-ttu-id="08cd6-110">Aşağıdaki ifadeyi kullanarak, bu yordamı çağırabilir ve <xref:System.Windows.Forms.Form> sınıfının geçerli örneğini bir bağımsız değişken olarak geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08cd6-110">You can call this procedure and pass the current instance of the <xref:System.Windows.Forms.Form> class as an argument by using the following statement.</span></span>  
  
```vb  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a><span data-ttu-id="08cd6-111">My</span><span class="sxs-lookup"><span data-stu-id="08cd6-111">My</span></span>  
 <span data-ttu-id="08cd6-112">`My` özelliği, Visual Basic kullanıcının bilgisayar, uygulama, ayarlar, kaynaklar vb. ile etkileşime geçmesini sağlayan bir dizi .NET Framework sınıfına kolay ve sezgisel erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="08cd6-112">The `My` feature provides easy and intuitive access to a number of .NET Framework classes, enabling the Visual Basic user to interact with the computer, application, settings, resources, and so on.</span></span>  
  
## <a name="mybase"></a><span data-ttu-id="08cd6-113">MyBase</span><span class="sxs-lookup"><span data-stu-id="08cd6-113">MyBase</span></span>  
 <span data-ttu-id="08cd6-114">`MyBase` anahtar sözcüğü, sınıfın geçerli örneğinin temel sınıfına başvuran bir nesne değişkeni gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="08cd6-114">The `MyBase` keyword behaves like an object variable referring to the base class of the current instance of a class.</span></span> <span data-ttu-id="08cd6-115">`MyBase`, türetilmiş bir sınıfta geçersiz kılınan veya gölgeli temel sınıf üyelerine erişmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="08cd6-115">`MyBase` is commonly used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="08cd6-116">`MyBase.New`, türetilmiş bir sınıf oluşturucusundan bir taban sınıf oluşturucuyu açıkça çağırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="08cd6-116">`MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>  
  
## <a name="myclass"></a><span data-ttu-id="08cd6-117">Sınıfım</span><span class="sxs-lookup"><span data-stu-id="08cd6-117">MyClass</span></span>  
 <span data-ttu-id="08cd6-118">`MyClass` anahtar sözcüğü, başlangıçta uygulanmış olan bir sınıfın geçerli örneğine başvuran bir nesne değişkeni gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="08cd6-118">The `MyClass` keyword behaves like an object variable referring to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="08cd6-119">`MyClass`, `Me`benzerdir, ancak tüm Yöntem çağrıları Yöntem `NotOverridable`olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="08cd6-119">`MyClass` is similar to `Me`, but all method calls on it are treated as if the method were `NotOverridable`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08cd6-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08cd6-120">See also</span></span>

- [<span data-ttu-id="08cd6-121">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="08cd6-121">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
