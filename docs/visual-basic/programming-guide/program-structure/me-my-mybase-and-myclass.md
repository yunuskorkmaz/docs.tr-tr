---
title: Visual Basic'de Me, My, MyBase ve MyClass
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bebf404cd65d1b3a2c4059d3a7c986f0157dfe2d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a><span data-ttu-id="816eb-102">Visual Basic'de Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="816eb-102">Me, My, MyBase, and MyClass in Visual Basic</span></span>
<span data-ttu-id="816eb-103">`Me`, `My`, `MyBase`, ve `MyClass` içinde [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] adlarının benzer ancak farklı amaçlar.</span><span class="sxs-lookup"><span data-stu-id="816eb-103">`Me`, `My`, `MyBase`, and `MyClass` in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] have similar names, but different purposes.</span></span> <span data-ttu-id="816eb-104">Bu konuda bunları ayırt etmek için bunların her biri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="816eb-104">This topic describes each of these entities in order to distinguish them.</span></span>  
  
## <a name="me"></a><span data-ttu-id="816eb-105">Beni</span><span class="sxs-lookup"><span data-stu-id="816eb-105">Me</span></span>  
 <span data-ttu-id="816eb-106">`Me` Anahtar sözcüğü bir sınıf veya yapı içinde kod şu anda yürütülmekte olan belirli örneğine başvurmak için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="816eb-106">The `Me` keyword provides a way to refer to the specific instance of a class or structure in which the code is currently executing.</span></span> <span data-ttu-id="816eb-107">`Me`bir nesne değişkeni veya geçerli örneğine başvurma yapısı değişkeni gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="816eb-107">`Me` behaves like either an object variable or a structure variable referring to the current instance.</span></span> <span data-ttu-id="816eb-108">Kullanarak `Me` başka bir sınıf, yapı veya modülü bir yordam için bir sınıf veya yapı şu anda yürütülen örneği hakkında bilgi geçirme özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="816eb-108">Using `Me` is particularly useful for passing information about the currently executing instance of a class or structure to a procedure in another class, structure, or module.</span></span>  
  
 <span data-ttu-id="816eb-109">Örneğin, aşağıdaki yordamda bir modülde olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="816eb-109">For example, suppose you have the following procedure in a module.</span></span>  
  
```  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 <span data-ttu-id="816eb-110">Bu yordam çağrısı ve geçerli örneği geçirin <xref:System.Windows.Forms.Form> şu deyimi kullanarak bağımsız değişken olarak sınıfı.</span><span class="sxs-lookup"><span data-stu-id="816eb-110">You can call this procedure and pass the current instance of the <xref:System.Windows.Forms.Form> class as an argument by using the following statement.</span></span>  
  
```  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a><span data-ttu-id="816eb-111">Benim</span><span class="sxs-lookup"><span data-stu-id="816eb-111">My</span></span>  
 <span data-ttu-id="816eb-112">`My` Özelliği için bir dizi kolay ve sezgisel erişim sağlar [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] etkinleştirme sınıfları [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] bilgisayar, uygulama, ayarları, kaynaklar vb. ile etkileşim kurmak için kullanıcı.</span><span class="sxs-lookup"><span data-stu-id="816eb-112">The `My` feature provides easy and intuitive access to a number of [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] classes, enabling the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] user to interact with the computer, application, settings, resources, and so on.</span></span>  
  
## <a name="mybase"></a><span data-ttu-id="816eb-113">MyBase</span><span class="sxs-lookup"><span data-stu-id="816eb-113">MyBase</span></span>  
 <span data-ttu-id="816eb-114">`MyBase` Anahtar sözcüğü sınıfının geçerli örneği için temel sınıf başvuran bir nesne değişkeni gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="816eb-114">The `MyBase` keyword behaves like an object variable referring to the base class of the current instance of a class.</span></span> <span data-ttu-id="816eb-115">`MyBase`yaygın olarak geçersiz kılınan veya türetilen bir sınıfta gölgeli taban sınıfı üyeleri erişmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="816eb-115">`MyBase` is commonly used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="816eb-116">`MyBase.New`bir temel sınıf oluşturucu türetilmiş bir sınıf oluşturucudan açıkça çağırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="816eb-116">`MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>  
  
## <a name="myclass"></a><span data-ttu-id="816eb-117">MyClass</span><span class="sxs-lookup"><span data-stu-id="816eb-117">MyClass</span></span>  
 <span data-ttu-id="816eb-118">`MyClass` Anahtar sözcüğü olarak ilk olarak uygulanan sınıfının geçerli örneği başvuran bir nesne değişkeni gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="816eb-118">The `MyClass` keyword behaves like an object variable referring to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="816eb-119">`MyClass`benzer `Me`, ancak yöntemi değilmiş gibi onu tüm yöntemi çağrılarını kabul edilir `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="816eb-119">`MyClass` is similar to `Me`, but all method calls on it are treated as if the method were `NotOverridable`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="816eb-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="816eb-120">See Also</span></span>  
 [<span data-ttu-id="816eb-121">Devralma temelleri</span><span class="sxs-lookup"><span data-stu-id="816eb-121">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
