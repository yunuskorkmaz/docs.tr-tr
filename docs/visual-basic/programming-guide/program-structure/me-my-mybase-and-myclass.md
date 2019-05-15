---
title: Visual Basic'de Me, My, MyBase ve MyClass
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
ms.openlocfilehash: 3eca756429c5fec8f324a17350844b59baf9ccf7
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586259"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a><span data-ttu-id="c0fbd-102">Visual Basic'de Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="c0fbd-102">Me, My, MyBase, and MyClass in Visual Basic</span></span>
<span data-ttu-id="c0fbd-103">`Me`, `My`, `MyBase`, ve `MyClass` Visual Basic'te adlarının benzer ancak farklı amaçlara sahip.</span><span class="sxs-lookup"><span data-stu-id="c0fbd-103">`Me`, `My`, `MyBase`, and `MyClass` in Visual Basic have similar names, but different purposes.</span></span> <span data-ttu-id="c0fbd-104">Bu konuda bunları ayırt etmek için bunların her biri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c0fbd-104">This topic describes each of these entities in order to distinguish them.</span></span>  
  
## <a name="me"></a><span data-ttu-id="c0fbd-105">Beni</span><span class="sxs-lookup"><span data-stu-id="c0fbd-105">Me</span></span>  
 <span data-ttu-id="c0fbd-106">`Me` Anahtar sözcüğü bir sınıf veya yapı içinde kod şu anda Yürütülüyor belirli örneğine başvurmak için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="c0fbd-106">The `Me` keyword provides a way to refer to the specific instance of a class or structure in which the code is currently executing.</span></span> <span data-ttu-id="c0fbd-107">`Me` bir nesne değişkeni veya bir yapı değişken geçerli örneğine başvurma gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="c0fbd-107">`Me` behaves like either an object variable or a structure variable referring to the current instance.</span></span> <span data-ttu-id="c0fbd-108">Kullanarak `Me` başka bir sınıf, yapı veya modül bir yordam için bir sınıf veya yapı şu anda yürütülen örneği hakkında bilgi geçirmek için özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="c0fbd-108">Using `Me` is particularly useful for passing information about the currently executing instance of a class or structure to a procedure in another class, structure, or module.</span></span>  
  
 <span data-ttu-id="c0fbd-109">Örneğin, bir modülde aşağıdaki yordam olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="c0fbd-109">For example, suppose you have the following procedure in a module.</span></span>  
  
```  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 <span data-ttu-id="c0fbd-110">Bu yordam çağrısı ve geçerli örneğini geçirin <xref:System.Windows.Forms.Form> aşağıdaki deyimi kullanarak bir bağımsız değişken olarak sınıf.</span><span class="sxs-lookup"><span data-stu-id="c0fbd-110">You can call this procedure and pass the current instance of the <xref:System.Windows.Forms.Form> class as an argument by using the following statement.</span></span>  
  
```  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a><span data-ttu-id="c0fbd-111">Benim</span><span class="sxs-lookup"><span data-stu-id="c0fbd-111">My</span></span>  
 <span data-ttu-id="c0fbd-112">`My` Özellik .NET Framework sınıfları, bilgisayar, uygulama, ayarları, kaynakları ve benzeri ile etkileşim kurmak Visual Basic kullanıcı etkinleştirme sayısını kolay ve sezgisel erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="c0fbd-112">The `My` feature provides easy and intuitive access to a number of .NET Framework classes, enabling the Visual Basic user to interact with the computer, application, settings, resources, and so on.</span></span>  
  
## <a name="mybase"></a><span data-ttu-id="c0fbd-113">MyBase</span><span class="sxs-lookup"><span data-stu-id="c0fbd-113">MyBase</span></span>  
 <span data-ttu-id="c0fbd-114">`MyBase` Anahtar sözcüğü davranacağını gibi geçerli bir sınıf örneğinin temel sınıfına başvuran bir nesne değişkeni.</span><span class="sxs-lookup"><span data-stu-id="c0fbd-114">The `MyBase` keyword behaves like an object variable referring to the base class of the current instance of a class.</span></span> <span data-ttu-id="c0fbd-115">`MyBase` yaygın olarak geçersiz kılınan ya da türetilen bir sınıfta gölgeli bir temel sınıf üyelerinin erişmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c0fbd-115">`MyBase` is commonly used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="c0fbd-116">`MyBase.New` bir temel sınıf oluşturucusu bir türetilmiş sınıf oluşturucusunda açıkça çağırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c0fbd-116">`MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>  
  
## <a name="myclass"></a><span data-ttu-id="c0fbd-117">MyClass</span><span class="sxs-lookup"><span data-stu-id="c0fbd-117">MyClass</span></span>  
 <span data-ttu-id="c0fbd-118">`MyClass` Anahtar sözcüğü davranacağını gibi bir nesne değişkeninin özgün olarak uygulandığı bir sınıfın geçerli örneğine başvurma.</span><span class="sxs-lookup"><span data-stu-id="c0fbd-118">The `MyClass` keyword behaves like an object variable referring to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="c0fbd-119">`MyClass` benzer `Me`, ancak yöntem'ymiş gibi üzerindeki tüm yöntem çağrılarını kabul edilir `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="c0fbd-119">`MyClass` is similar to `Me`, but all method calls on it are treated as if the method were `NotOverridable`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0fbd-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c0fbd-120">See also</span></span>

- [<span data-ttu-id="c0fbd-121">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="c0fbd-121">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
