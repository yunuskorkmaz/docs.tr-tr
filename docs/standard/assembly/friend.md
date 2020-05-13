---
title: Arkadaş derlemeleri
description: Arkadaş derlemesi, başka bir derlemenin iç (C#) veya arkadaş (Visual Basic) türlerine ve üyelerine erişebilen bir .NET derlemesidir.
ms.date: 08/20/2019
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
dev_langs:
- csharp
- vb
ms.openlocfilehash: 105621da2bd418c6294fa2bbec474809599cb6a5
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378928"
---
# <a name="friend-assemblies"></a><span data-ttu-id="46cd0-103">Arkadaş derlemeleri</span><span class="sxs-lookup"><span data-stu-id="46cd0-103">Friend assemblies</span></span>

<span data-ttu-id="46cd0-104">*Arkadaş derlemesi* , başka bir derlemenin [iç](../../csharp/language-reference/keywords/internal.md) (C#) veya [arkadaş](../../visual-basic/language-reference/modifiers/friend.md) (Visual Basic) türlerine ve üyelerine erişebilen bir derlemedir.</span><span class="sxs-lookup"><span data-stu-id="46cd0-104">A *friend assembly* is an assembly that can access another assembly's [internal](../../csharp/language-reference/keywords/internal.md) (C#) or [Friend](../../visual-basic/language-reference/modifiers/friend.md) (Visual Basic) types and members.</span></span> <span data-ttu-id="46cd0-105">Bir derlemeyi arkadaş derleme olarak belirlerseniz, diğer derlemeler tarafından erişilebilmesi için artık türleri ve üyeleri ortak olarak işaretlemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="46cd0-105">If you identify an assembly as a friend assembly, you no longer have to mark types and members as public in order for them to be accessed by other assemblies.</span></span> <span data-ttu-id="46cd0-106">Bu, özellikle aşağıdaki senaryolarda kullanışlıdır:</span><span class="sxs-lookup"><span data-stu-id="46cd0-106">This is especially convenient in the following scenarios:</span></span>

- <span data-ttu-id="46cd0-107">Birim testi sırasında, test kodu ayrı bir derlemede çalışırken, ancak test edilen derlemede C# veya Visual Basic olarak işaretlenen üyelere erişim gerektirir `internal` `Friend` .</span><span class="sxs-lookup"><span data-stu-id="46cd0-107">During unit testing, when test code runs in a separate assembly but requires access to members in the assembly being tested that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

- <span data-ttu-id="46cd0-108">Bir sınıf kitaplığı geliştirirken ve kitaplığa eklemeler ayrı derlemelerde bulunur, ancak `internal` C# dilinde veya Visual Basic olarak işaretlenen mevcut derlemelerdeki üyelere erişim gerektirir `Friend` .</span><span class="sxs-lookup"><span data-stu-id="46cd0-108">When you are developing a class library and additions to the library are contained in separate assemblies but require access to members in existing assemblies that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

## <a name="remarks"></a><span data-ttu-id="46cd0-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="46cd0-109">Remarks</span></span>

<span data-ttu-id="46cd0-110"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>Belirli bir derleme için bir veya daha fazla Friend derlemesini tanımlamak üzere özniteliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46cd0-110">You can use the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to identify one or more friend assemblies for a given assembly.</span></span> <span data-ttu-id="46cd0-111">Aşağıdaki örnek, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> *derleme a* içindeki özniteliğini kullanır ve bir Friend derlemesi olarak bir derlemeyi *AssemblyB* olarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="46cd0-111">The following example uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute in *Assembly A* and specifies assembly *AssemblyB* as a friend assembly.</span></span> <span data-ttu-id="46cd0-112">Bu, bütünleştirilmiş kod, C# ' de veya Visual Basic olarak işaretlenen *derleme A* 'daki tüm türlere ve üyelere derleme Için *AssemblyB* erişimi sağlar `internal` `Friend` .</span><span class="sxs-lookup"><span data-stu-id="46cd0-112">This gives assembly *AssemblyB* access to all types and members in *Assembly A* that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

> [!NOTE]
> <span data-ttu-id="46cd0-113">*Derleme A*gibi başka bir derlemenin iç türlerine veya iç üyelerine erişecek *AssemblyB* gibi bir derlemeyi derlerken, **-Out** derleyici seçeneğini kullanarak çıkış dosyasının (*. exe* veya *. dll*) adını açıkça belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="46cd0-113">When you compile an assembly like *AssemblyB* that will access internal types or internal members of another assembly like *Assembly A*, you must explicitly specify the name of the output file (*.exe* or *.dll*) by using the **-out** compiler option.</span></span> <span data-ttu-id="46cd0-114">Bu gereklidir çünkü derleyici, dış başvurulara bağlama sırasında oluşturmakta olduğu derlemenin adını henüz üretmemiştir.</span><span class="sxs-lookup"><span data-stu-id="46cd0-114">This is required because the compiler has not yet generated the name for the assembly it is building at the time it is binding to external references.</span></span> <span data-ttu-id="46cd0-115">Daha fazla bilgi için bkz. [-Out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) veya [-Out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="46cd0-115">For more information, see [-out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span></span>

```csharp
using System.Runtime.CompilerServices;
using System;

[assembly: InternalsVisibleTo("AssemblyB")]

// The class is internal by default.
class FriendClass
{
    public void Test()
    {
        Console.WriteLine("Sample Class");
    }
}

// Public class that has an internal method.
public class ClassWithFriendMethod
{
    internal void Test()
    {
        Console.WriteLine("Sample Method");
    }

}
```

```vb
Imports System.Runtime.CompilerServices
<Assembly: InternalsVisibleTo("AssemblyB")>

' Friend class.
Friend Class FriendClass
    Public Sub Test()
        Console.WriteLine("Sample Class")
    End Sub
End Class

' Public class with a Friend method.
Public Class ClassWithFriendMethod
    Friend Sub Test()
        Console.WriteLine("Sample Method")
    End Sub
End Class
```

<span data-ttu-id="46cd0-116">Yalnızca arkadaş olarak açıkça belirttiğiniz derlemeler `internal` (C#) veya `Friend` (Visual Basic) türlerine ve üyelerine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="46cd0-116">Only assemblies that you explicitly specify as friends can access `internal` (C#) or `Friend` (Visual Basic) types and members.</span></span> <span data-ttu-id="46cd0-117">Örneğin, *AssemblyB* , *derleme a* 'Nın arkadaşınız ve *derleme c* , *AssemblyB*'ye başvuruyorsa, *derleme c* 'nin `internal` a derlemesinde (C#) veya `Friend` (Visual Basic) türlerine erişimi yoktur. *Assembly A*</span><span class="sxs-lookup"><span data-stu-id="46cd0-117">For example, if *AssemblyB* is a friend of *Assembly A* and *Assembly C* references *AssemblyB*, *Assembly C* does not have access to `internal` (C#) or `Friend` (Visual Basic) types in *Assembly A*.</span></span>

<span data-ttu-id="46cd0-118">Derleyici, özniteliğe geçirilen arkadaş derleme adının bazı temel doğrulamasını gerçekleştirir <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> .</span><span class="sxs-lookup"><span data-stu-id="46cd0-118">The compiler performs some basic validation of the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="46cd0-119">Eğer *derlemesi bir* Friend derlemesi olarak *AssemblyB* bildirirse, doğrulama kuralları aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="46cd0-119">If *Assembly A* declares *AssemblyB* as a friend assembly, the validation rules are as follows:</span></span>

- <span data-ttu-id="46cd0-120">*Derleme A* tanımlayıcı olarak adlandırılmışsa, *AssemblyB* de tanımlayıcı adlandırılmış olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="46cd0-120">If *Assembly A* is strong named, *AssemblyB* must also be strong named.</span></span> <span data-ttu-id="46cd0-121">Özniteliğine geçirilen arkadaş derleme adı, *AssemblyB*imzalamak için kullanılan tanımlayıcı ad anahtarının derleme adından ve ortak anahtarından oluşmalıdır.</span><span class="sxs-lookup"><span data-stu-id="46cd0-121">The friend assembly name that is passed to the attribute must consist of the assembly name and the public key of the strong-name key that is used to sign *AssemblyB*.</span></span>

     <span data-ttu-id="46cd0-122">Özniteliğe geçirilen arkadaş derleme adı <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> *AssemblyB*'nin tanımlayıcı adı olamaz.</span><span class="sxs-lookup"><span data-stu-id="46cd0-122">The friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute cannot be the strong name of *AssemblyB*.</span></span> <span data-ttu-id="46cd0-123">Bütünleştirilmiş kod sürümü, kültür, mimari veya ortak anahtar belirtecini eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="46cd0-123">Don't include the assembly version, culture, architecture, or public key token.</span></span>

- <span data-ttu-id="46cd0-124">*Derleme A* tanımlayıcı adlandırılmış değilse, arkadaş derleme adı yalnızca derleme adından oluşmalıdır.</span><span class="sxs-lookup"><span data-stu-id="46cd0-124">If *Assembly A* is not strong named, the friend assembly name should consist of only the assembly name.</span></span> <span data-ttu-id="46cd0-125">Daha fazla bilgi için bkz. [nasıl yapılır: imzasız arkadaş derlemeleri oluşturma](create-unsigned-friend.md).</span><span class="sxs-lookup"><span data-stu-id="46cd0-125">For more information, see [How to: Create unsigned friend assemblies](create-unsigned-friend.md).</span></span>

- <span data-ttu-id="46cd0-126">*AssemblyB* tanımlayıcı adlandırılmış ise, proje ayarını veya komut satırı derleyici seçeneğini kullanarak *AssemblyB* için tanımlayıcı ad anahtarını belirtmeniz gerekir `/keyfile` .</span><span class="sxs-lookup"><span data-stu-id="46cd0-126">If *AssemblyB* is strong named, you must specify the strong-name key for *AssemblyB* by using the project setting or the command-line `/keyfile` compiler option.</span></span> <span data-ttu-id="46cd0-127">Daha fazla bilgi için bkz. [nasıl yapılır: imzalı arkadaş derlemeleri oluşturma](create-signed-friend.md).</span><span class="sxs-lookup"><span data-stu-id="46cd0-127">For more information, see [How to: Create signed friend assemblies](create-signed-friend.md).</span></span>

 <span data-ttu-id="46cd0-128"><xref:System.Security.Permissions.StrongNameIdentityPermission>Sınıfı, aşağıdaki farklılıklarla türleri paylaşma özelliği de sağlar:</span><span class="sxs-lookup"><span data-stu-id="46cd0-128">The <xref:System.Security.Permissions.StrongNameIdentityPermission> class also provides the ability to share types, with the following differences:</span></span>

- <span data-ttu-id="46cd0-129"><xref:System.Security.Permissions.StrongNameIdentityPermission>tek bir tür için geçerlidir, ancak bir arkadaş derleme tüm derleme için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="46cd0-129"><xref:System.Security.Permissions.StrongNameIdentityPermission> applies to an individual type, while a friend assembly applies to the whole assembly.</span></span>

- <span data-ttu-id="46cd0-130">*Bir derlemede* *AssemblyB*ile paylaşmak istediğiniz yüzlerce tür varsa, tümüne eklemeniz gerekir <xref:System.Security.Permissions.StrongNameIdentityPermission> .</span><span class="sxs-lookup"><span data-stu-id="46cd0-130">If there are hundreds of types in *Assembly A* that you want to share with *AssemblyB*, you have to add <xref:System.Security.Permissions.StrongNameIdentityPermission> to all of them.</span></span> <span data-ttu-id="46cd0-131">Bir arkadaş derleme kullanıyorsanız, yalnızca bir defa arkadaş ilişki bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="46cd0-131">If you use a friend assembly, you only need to declare the friend relationship once.</span></span>

- <span data-ttu-id="46cd0-132">Kullanırsanız <xref:System.Security.Permissions.StrongNameIdentityPermission> , paylaşmak istediğiniz türlerin ortak olarak bildirilmesini gerekir.</span><span class="sxs-lookup"><span data-stu-id="46cd0-132">If you use <xref:System.Security.Permissions.StrongNameIdentityPermission>, the types you want to share have to be declared as public.</span></span> <span data-ttu-id="46cd0-133">Bir arkadaş derleme kullanıyorsanız, paylaşılan türler `internal` (C#) veya `Friend` (Visual Basic) olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="46cd0-133">If you use a friend assembly, the shared types are declared as `internal` (C#) or `Friend` (Visual Basic).</span></span>

<span data-ttu-id="46cd0-134">Bir `internal` `Friend` Modül dosyasından ( *. netmodule* uzantılı bir dosya) bir derlemenin (C#) veya (Visual Basic) türlerine ve yöntemlerine erişme hakkında daha fazla bilgi için, bkz: [-moduleassemblyname (c#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) veya [-moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span><span class="sxs-lookup"><span data-stu-id="46cd0-134">For information about how to access an assembly's `internal` (C#) or `Friend` (Visual Basic) types and methods from a module file (a file with the *.netmodule* extension), see [-moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) or [-moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="46cd0-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46cd0-135">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [<span data-ttu-id="46cd0-136">Nasıl yapılır: imzasız arkadaş derlemeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="46cd0-136">How to: Create unsigned friend assemblies</span></span>](create-unsigned-friend.md)
- [<span data-ttu-id="46cd0-137">Nasıl yapılır: imzalı arkadaş derlemeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="46cd0-137">How to: Create signed friend assemblies</span></span>](create-signed-friend.md)
- [<span data-ttu-id="46cd0-138">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="46cd0-138">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="46cd0-139">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="46cd0-139">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="46cd0-140">Programlama kavramları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46cd0-140">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
