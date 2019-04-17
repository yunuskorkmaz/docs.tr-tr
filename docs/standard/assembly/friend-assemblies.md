---
title: Arkadaş derlemeler (C#)
ms.date: 03/03/2019
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
ms.openlocfilehash: 770eb70a5350d7d26e03cb4e605b442100da2a53
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59614031"
---
# <a name="friend-assemblies"></a><span data-ttu-id="2e15e-102">Arkadaş derlemeleri</span><span class="sxs-lookup"><span data-stu-id="2e15e-102">Friend assemblies</span></span>

<span data-ttu-id="2e15e-103">A *arkadaş derleme* başka bir derlemenin erişebilen bir derleme [iç](../../csharp/language-reference/keywords/internal.md) (içinde C# veya [arkadaş](../../visual-basic/language-reference/modifiers/friend.md) Visual Basic'te) türler ve üyeler.</span><span class="sxs-lookup"><span data-stu-id="2e15e-103">A *friend assembly* is an assembly that can access another assembly's [internal](../../csharp/language-reference/keywords/internal.md) (in C# or [Friend](../../visual-basic/language-reference/modifiers/friend.md) in Visual Basic) types and members.</span></span> <span data-ttu-id="2e15e-104">Derleme arkadaş derleme olarak belirlerseniz, artık türleri ve üyeleri edebilmeleri genel olarak diğer derlemeler tarafından erişilecek işareti yok.</span><span class="sxs-lookup"><span data-stu-id="2e15e-104">If you identify an assembly as a friend assembly, you no longer have to mark types and members as public in order for them to be accessed by other assemblies.</span></span> <span data-ttu-id="2e15e-105">Bu, özellikle aşağıdaki senaryolarda kullanışlıdır:</span><span class="sxs-lookup"><span data-stu-id="2e15e-105">This is especially convenient in the following scenarios:</span></span>

- <span data-ttu-id="2e15e-106">Birim testi sırasında test kod çalıştığında ayrı bir derleme ancak olarak işaretlenmiş test edilen derleme üyelerine erişim gerektirir. `internal` içinde C# veya `Friend` Visual Basic'te.</span><span class="sxs-lookup"><span data-stu-id="2e15e-106">During unit testing, when test code runs in a separate assembly but requires access to members in the assembly being tested that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

- <span data-ttu-id="2e15e-107">Ne zaman bir sınıf kitaplığı geliştiriyorsanız ve kitaplığı eklemeleri ayrı derlemelerinde toplanır, ancak üye olarak işaretlenmiş var olan derlemelerde erişmesi `internal` içinde C# veya `Friend` Visual Basic'te.</span><span class="sxs-lookup"><span data-stu-id="2e15e-107">When you are developing a class library and additions to the library are contained in separate assemblies but require access to members in existing assemblies that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

## <a name="remarks"></a><span data-ttu-id="2e15e-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2e15e-108">Remarks</span></span>

<span data-ttu-id="2e15e-109">Kullanabileceğiniz <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> belirli bir derleme için bir veya daha fazla arkadaş derlemeleri tanımlamak için öznitelik.</span><span class="sxs-lookup"><span data-stu-id="2e15e-109">You can use the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to identify one or more friend assemblies for a given assembly.</span></span> <span data-ttu-id="2e15e-110">Aşağıdaki örnekte <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> öznitelik bir derlemede ve derleme belirtir `AssemblyB` arkadaş derleme olarak.</span><span class="sxs-lookup"><span data-stu-id="2e15e-110">The following example uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute in assembly A and specifies assembly `AssemblyB` as a friend assembly.</span></span> <span data-ttu-id="2e15e-111">Bu derleme verir `AssemblyB` tüm türleri ve üyeleri bir olarak işaretlenmiş derleme erişim `internal` içinde C# veya `Friend` Visual Basic'te.</span><span class="sxs-lookup"><span data-stu-id="2e15e-111">This gives assembly `AssemblyB` access to all types and members in assembly A that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

> [!NOTE]
> <span data-ttu-id="2e15e-112">Derleme yaparken bir derleme (derleme `AssemblyB`) iç türleri veya başka bir derlemenin iç üyeleri erişir (derleme *A*), çıktı dosyası (.exe veya .dll) adı kullanarakaçıkçabelirtmenizgerekir **/out** derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="2e15e-112">When you compile an assembly (assembly `AssemblyB`) that will access internal types or internal members of another assembly (assembly *A*), you must explicitly specify the name of the output file (.exe or .dll) by using the **/out** compiler option.</span></span> <span data-ttu-id="2e15e-113">Bu, derleyicinin onu dış başvuruları bağlayarak zaman oluşturma derleme adı henüz oluşturmamıştır çünkü gereklidir.</span><span class="sxs-lookup"><span data-stu-id="2e15e-113">This is required because the compiler has not yet generated the name for the assembly it is building at the time it is binding to external references.</span></span> <span data-ttu-id="2e15e-114">Daha fazla bilgi için [/out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) veya [/out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="2e15e-114">For more information, see [/out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [/out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="2e15e-115">C#</span><span class="sxs-lookup"><span data-stu-id="2e15e-115">C#</span></span>](#tab/csharp)

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

# <a name="visual-basictabvb"></a>[<span data-ttu-id="2e15e-116">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2e15e-116">Visual Basic</span></span>](#tab/vb)

```vb
Imports System.Runtime.CompilerServices
Imports System
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

---

<span data-ttu-id="2e15e-117">Arkadaş erişebilir, açıkça belirttiğiniz derlemeleri `internal` (içinde C# veya `Friend` Visual Basic'te) türler ve üyeler.</span><span class="sxs-lookup"><span data-stu-id="2e15e-117">Only assemblies that you explicitly specify as friends can access `internal` (in C# or `Friend` in Visual Basic) types and members.</span></span> <span data-ttu-id="2e15e-118">Derleme B C derleme başvuruları derleme B derleme A'ya ve arkadaş ise, örneğin, C erişimi yok `internal` (içinde C# veya `Friend` Visual Basic'te) A'daki türleri</span><span class="sxs-lookup"><span data-stu-id="2e15e-118">For example, if assembly B is a friend of assembly A and assembly C references assembly B, C does not have access to `internal` (in C# or `Friend` in Visual Basic) types in A.</span></span>

<span data-ttu-id="2e15e-119">Derleyici geçirilen friend derleme adı, bazı temel doğrulama gerçekleştirir <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="2e15e-119">The compiler performs some basic validation of the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="2e15e-120">Derleme *A* bildirir *B* arkadaş derleme, doğrulama kuralları aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="2e15e-120">If assembly *A* declares *B* as a friend assembly, the validation rules are as follows:</span></span>

- <span data-ttu-id="2e15e-121">Derleme *A* adlı derleme güçlü olduğunu *B* ayrıca strong adlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2e15e-121">If assembly *A* is strong named, assembly *B* must also be strong named.</span></span> <span data-ttu-id="2e15e-122">Özniteliğe geçirilir friend derleme adı, derleme adı ve derlemeyi imzalamak için kullanılan tanımlayıcı ad anahtarı ortak anahtarını oluşmalıdır *B*.</span><span class="sxs-lookup"><span data-stu-id="2e15e-122">The friend assembly name that is passed to the attribute must consist of the assembly name and the public key of the strong-name key that is used to sign assembly *B*.</span></span>

     <span data-ttu-id="2e15e-123">Geçirilen friend derleme adı <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği olamaz derleme tanımlayıcı adı *B*: derleme sürüm, kültür, mimari veya ortak anahtar belirteci içermez.</span><span class="sxs-lookup"><span data-stu-id="2e15e-123">The friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute cannot be the strong name of assembly *B*: do not include the assembly version, culture, architecture, or public key token.</span></span>

- <span data-ttu-id="2e15e-124">Derleme *A* adlı friend derleme adı yalnızca derleme adını oluşmalıdır sağlam değil.</span><span class="sxs-lookup"><span data-stu-id="2e15e-124">If assembly *A* is not strong named, the friend assembly name should consist of only the assembly name.</span></span> <span data-ttu-id="2e15e-125">Daha fazla bilgi için [nasıl yapılır: İmzasız arkadaş derlemeleri oluşturma (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md) veya [nasıl yapılır: (Visual Basic) imzasız arkadaş derlemeleri oluşturma](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="2e15e-125">For more information, see [How to: Create Unsigned Friend Assemblies (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md) or [How to: Create Unsigned Friend Assemblies (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).</span></span>

- <span data-ttu-id="2e15e-126">Derleme *B* adındaki, derlemenin tanımlayıcı ad anahtarı belirtmeniz gerekir güçlü olduğunu *B* proje ayarı veya komut satırı kullanarak `/keyfile` derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="2e15e-126">If assembly *B* is strong named, you must specify the strong-name key for assembly *B* by using the project setting or the command-line `/keyfile` compiler option.</span></span> <span data-ttu-id="2e15e-127">Daha fazla bilgi için [nasıl yapılır: İmzalı arkadaş derlemeleri oluşturma (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md) veya [nasıl yapılır: (Visual Basic) imzalı arkadaş derlemeleri oluşturma](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="2e15e-127">For more information, see [How to: Create Signed Friend Assemblies (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md) or [How to: Create Signed Friend Assemblies (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).</span></span>

 <span data-ttu-id="2e15e-128"><xref:System.Security.Permissions.StrongNameIdentityPermission> Sınıf türleri ile aşağıdaki farklar paylaşma olanağı da sağlar:</span><span class="sxs-lookup"><span data-stu-id="2e15e-128">The <xref:System.Security.Permissions.StrongNameIdentityPermission> class also provides the ability to share types, with the following differences:</span></span>

- <span data-ttu-id="2e15e-129"><xref:System.Security.Permissions.StrongNameIdentityPermission> arkadaş derleme tüm derleme için geçerli olsa da tek tek bir tür için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="2e15e-129"><xref:System.Security.Permissions.StrongNameIdentityPermission> applies to an individual type, while a friend assembly applies to the whole assembly.</span></span>

- <span data-ttu-id="2e15e-130">Bütünleştirilmiş kodundaki türler yüzlerce varsa *A* derleme ile paylaşmak istediğiniz *B*, eklemek zorunda <xref:System.Security.Permissions.StrongNameIdentityPermission> bunların tümüne.</span><span class="sxs-lookup"><span data-stu-id="2e15e-130">If there are hundreds of types in assembly *A* that you want to share with assembly *B*, you have to add <xref:System.Security.Permissions.StrongNameIdentityPermission> to all of them.</span></span> <span data-ttu-id="2e15e-131">Arkadaş derleme kullanıyorsanız, yalnızca arkadaş ilişki bildirmek üzere gerekir.</span><span class="sxs-lookup"><span data-stu-id="2e15e-131">If you use a friend assembly, you only need to declare the friend relationship once.</span></span>

- <span data-ttu-id="2e15e-132">Kullanırsanız <xref:System.Security.Permissions.StrongNameIdentityPermission>, paylaşmak istediğiniz türleri genel olarak bildirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="2e15e-132">If you use <xref:System.Security.Permissions.StrongNameIdentityPermission>, the types you want to share have to be declared as public.</span></span> <span data-ttu-id="2e15e-133">Arkadaş derleme kullanırsanız, paylaşılan türü olarak bildirilmiş olan `internal` (içinde C# veya `Friend` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="2e15e-133">If you use a friend assembly, the shared types are declared as `internal` (in C# or `Friend` in Visual Basic).</span></span>

<span data-ttu-id="2e15e-134">Bir derlemenin erişim hakkında daha fazla bilgi için `internal` (içinde C# veya `Friend` Visual Basic'te) türleri ve yöntemleri bir modül dosyası (bir .netmodule uzantılı), bkz. [/moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) veya [/moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span><span class="sxs-lookup"><span data-stu-id="2e15e-134">For information about how to access an assembly's `internal` (in C# or `Friend` in Visual Basic) types and methods from a module file (a file with the .netmodule extension), see [/moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) or [/moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2e15e-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e15e-135">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [<span data-ttu-id="2e15e-136">Nasıl yapılır: İmzasız arkadaş derlemeleri oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="2e15e-136">How to: Create Unsigned Friend Assemblies (C#)</span></span>](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)
- [<span data-ttu-id="2e15e-137">Nasıl yapılır: (Visual Basic) imzasız arkadaş derlemeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="2e15e-137">How to: Create Unsigned Friend Assemblies (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)
- [<span data-ttu-id="2e15e-138">Nasıl yapılır: İmzalı arkadaş derlemeleri oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="2e15e-138">How to: Create Signed Friend Assemblies (C#)</span></span>](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)
- [<span data-ttu-id="2e15e-139">Nasıl yapılır: (Visual Basic) imzalı arkadaş derlemeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="2e15e-139">How to: Create Signed Friend Assemblies (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)
- [<span data-ttu-id="2e15e-140">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="2e15e-140">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="2e15e-141">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2e15e-141">C# Programming Guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="2e15e-142">Programlama Kavramları</span><span class="sxs-lookup"><span data-stu-id="2e15e-142">Programming Concepts</span></span>](../../visual-basic/programming-guide/concepts/index.md)
