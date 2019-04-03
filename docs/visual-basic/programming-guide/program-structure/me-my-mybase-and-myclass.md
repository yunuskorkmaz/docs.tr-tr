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
ms.openlocfilehash: a8df6e48fd5bce9bb28d8aef7e031f36741ad0ad
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58813398"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a><span data-ttu-id="42af3-102">Visual Basic'de Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="42af3-102">Me, My, MyBase, and MyClass in Visual Basic</span></span>
<span data-ttu-id="42af3-103">`Me`, `My`, `MyBase`, ve `MyClass` Visual Basic'te adlarının benzer ancak farklı amaçlara sahip.</span><span class="sxs-lookup"><span data-stu-id="42af3-103">`Me`, `My`, `MyBase`, and `MyClass` in Visual Basic have similar names, but different purposes.</span></span> <span data-ttu-id="42af3-104">Bu konuda bunları ayırt etmek için bunların her biri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="42af3-104">This topic describes each of these entities in order to distinguish them.</span></span>  
  
## <a name="me"></a><span data-ttu-id="42af3-105">Beni</span><span class="sxs-lookup"><span data-stu-id="42af3-105">Me</span></span>  
 <span data-ttu-id="42af3-106">`Me` Anahtar sözcüğü bir sınıf veya yapı içinde kod şu anda Yürütülüyor belirli örneğine başvurmak için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="42af3-106">The `Me` keyword provides a way to refer to the specific instance of a class or structure in which the code is currently executing.</span></span> <span data-ttu-id="42af3-107">`Me` bir nesne değişkeni veya bir yapı değişken geçerli örneğine başvurma gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="42af3-107">`Me` behaves like either an object variable or a structure variable referring to the current instance.</span></span> <span data-ttu-id="42af3-108">Kullanarak `Me` başka bir sınıf, yapı veya modül bir yordam için bir sınıf veya yapı şu anda yürütülen örneği hakkında bilgi geçirmek için özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="42af3-108">Using `Me` is particularly useful for passing information about the currently executing instance of a class or structure to a procedure in another class, structure, or module.</span></span>  
  
 <span data-ttu-id="42af3-109">Örneğin, bir modülde aşağıdaki yordam olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="42af3-109">For example, suppose you have the following procedure in a module.</span></span>  
  
```  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 <span data-ttu-id="42af3-110">Bu yordam çağrısı ve geçerli örneğini geçirin <xref:System.Windows.Forms.Form> aşağıdaki deyimi kullanarak bir bağımsız değişken olarak sınıf.</span><span class="sxs-lookup"><span data-stu-id="42af3-110">You can call this procedure and pass the current instance of the <xref:System.Windows.Forms.Form> class as an argument by using the following statement.</span></span>  
  
```  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a><span data-ttu-id="42af3-111">Benim</span><span class="sxs-lookup"><span data-stu-id="42af3-111">My</span></span>  
 <span data-ttu-id="42af3-112">`My` Özelliği için çok sayıda kolay ve sezgisel erişim sunar [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sınıfları, bilgisayar, uygulama, ayarları, kaynakları ve benzeri ile etkileşim kurmak Visual Basic kullanıcı etkinleştirme.</span><span class="sxs-lookup"><span data-stu-id="42af3-112">The `My` feature provides easy and intuitive access to a number of [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] classes, enabling the Visual Basic user to interact with the computer, application, settings, resources, and so on.</span></span>  
  
## <a name="mybase"></a><span data-ttu-id="42af3-113">MyBase</span><span class="sxs-lookup"><span data-stu-id="42af3-113">MyBase</span></span>  
 <span data-ttu-id="42af3-114">`MyBase` Anahtar sözcüğü davranacağını gibi geçerli bir sınıf örneğinin temel sınıfına başvuran bir nesne değişkeni.</span><span class="sxs-lookup"><span data-stu-id="42af3-114">The `MyBase` keyword behaves like an object variable referring to the base class of the current instance of a class.</span></span> <span data-ttu-id="42af3-115">`MyBase` yaygın olarak geçersiz kılınan ya da türetilen bir sınıfta gölgeli bir temel sınıf üyelerinin erişmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="42af3-115">`MyBase` is commonly used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="42af3-116">`MyBase.New` bir temel sınıf oluşturucusu bir türetilmiş sınıf oluşturucusunda açıkça çağırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="42af3-116">`MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>  
  
## <a name="myclass"></a><span data-ttu-id="42af3-117">MyClass</span><span class="sxs-lookup"><span data-stu-id="42af3-117">MyClass</span></span>  
 <span data-ttu-id="42af3-118">`MyClass` Anahtar sözcüğü davranacağını gibi bir nesne değişkeninin özgün olarak uygulandığı bir sınıfın geçerli örneğine başvurma.</span><span class="sxs-lookup"><span data-stu-id="42af3-118">The `MyClass` keyword behaves like an object variable referring to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="42af3-119">`MyClass` benzer `Me`, ancak yöntem'ymiş gibi üzerindeki tüm yöntem çağrılarını kabul edilir `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="42af3-119">`MyClass` is similar to `Me`, but all method calls on it are treated as if the method were `NotOverridable`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42af3-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42af3-120">See also</span></span>

- [<span data-ttu-id="42af3-121">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="42af3-121">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
