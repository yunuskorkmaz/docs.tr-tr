---
title: Arkadaş derlemeleri
ms.date: 08/20/2019
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
dev_langs:
- csharp
- vb
ms.openlocfilehash: a74d4b74ead8492028a092e090f9281231802a87
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348174"
---
# <a name="friend-assemblies"></a><span data-ttu-id="44916-102">Arkadaş derlemeleri</span><span class="sxs-lookup"><span data-stu-id="44916-102">Friend assemblies</span></span>

<span data-ttu-id="44916-103">*Arkadaş derlemesi,* başka bir derlemenin [dahili](../../csharp/language-reference/keywords/internal.md) (C#) veya [Arkadaş](../../visual-basic/language-reference/modifiers/friend.md) (Visual Basic) türlerine ve üyelerine erişebilen bir derlemedir.</span><span class="sxs-lookup"><span data-stu-id="44916-103">A *friend assembly* is an assembly that can access another assembly's [internal](../../csharp/language-reference/keywords/internal.md) (C#) or [Friend](../../visual-basic/language-reference/modifiers/friend.md) (Visual Basic) types and members.</span></span> <span data-ttu-id="44916-104">Bir derlemeyi arkadaş derlemesi olarak tanımlarsanız, diğer derlemeler tarafından erişilebilmesi için türleri ve üyeleri artık herkese açık olarak işaretlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="44916-104">If you identify an assembly as a friend assembly, you no longer have to mark types and members as public in order for them to be accessed by other assemblies.</span></span> <span data-ttu-id="44916-105">Bu, özellikle aşağıdaki senaryolarda kullanışlıdır:</span><span class="sxs-lookup"><span data-stu-id="44916-105">This is especially convenient in the following scenarios:</span></span>

- <span data-ttu-id="44916-106">Birim testi sırasında, test kodu ayrı bir derlemede çalıştığında, ancak c# `internal` veya `Friend` Visual Basic olarak işaretlenmiş olarak sınanan derlemedeki üyelere erişim gerekir.</span><span class="sxs-lookup"><span data-stu-id="44916-106">During unit testing, when test code runs in a separate assembly but requires access to members in the assembly being tested that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

- <span data-ttu-id="44916-107">Bir sınıf kitaplığı geliştirirken ve kitaplık eklemeleri ayrı derlemelerde bulunur, ancak C# veya `internal` `Friend` Visual Basic olarak işaretlenmiş varolan derlemelerde üyelere erişim gerekir.</span><span class="sxs-lookup"><span data-stu-id="44916-107">When you are developing a class library and additions to the library are contained in separate assemblies but require access to members in existing assemblies that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

## <a name="remarks"></a><span data-ttu-id="44916-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="44916-108">Remarks</span></span>

<span data-ttu-id="44916-109">Belirli bir <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> derleme için bir veya daha fazla arkadaş derlemesi tanımlamak için özniteliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44916-109">You can use the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to identify one or more friend assemblies for a given assembly.</span></span> <span data-ttu-id="44916-110">Aşağıdaki örnek, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> A Derlemesi'ndeki özniteliği kullanır ve *Derleme B'yi* arkadaş derlemesi olarak belirtir. *Assembly A*</span><span class="sxs-lookup"><span data-stu-id="44916-110">The following example uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute in *Assembly A* and specifies assembly *AssemblyB* as a friend assembly.</span></span> <span data-ttu-id="44916-111">Bu, *AssemblyB'nin* A Derlemesi'nde C# `internal` veya `Friend` Visual Basic olarak işaretlenmiş tüm tür ve üyelere erişim sağlar. *Assembly A*</span><span class="sxs-lookup"><span data-stu-id="44916-111">This gives assembly *AssemblyB* access to all types and members in *Assembly A* that are marked as `internal` in C# or `Friend` in Visual Basic.</span></span>

> [!NOTE]
> <span data-ttu-id="44916-112">*AssemblyB* *gibi, Assembly A*gibi başka bir derlemenin iç türlerine veya iç üyelerine erişecek bir derleme derlediğinizde, **-out** derleyici seçeneğini kullanarak çıktı dosyasının *(.exe* veya *.dll)* adını açıkça belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="44916-112">When you compile an assembly like *AssemblyB* that will access internal types or internal members of another assembly like *Assembly A*, you must explicitly specify the name of the output file (*.exe* or *.dll*) by using the **-out** compiler option.</span></span> <span data-ttu-id="44916-113">Derleyici, dış başvurulara bağlandığı anda oluşturduğu derlemenin adını henüz oluşturmadığından bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="44916-113">This is required because the compiler has not yet generated the name for the assembly it is building at the time it is binding to external references.</span></span> <span data-ttu-id="44916-114">Daha fazla bilgi için bkz: [-out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) [veya-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="44916-114">For more information, see [-out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span></span>

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

<span data-ttu-id="44916-115">Yalnızca açıkça arkadaş olarak belirttiğiniz derlemeler (C#) veya `internal` `Friend` (Visual Basic) türlerine ve üyelerine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="44916-115">Only assemblies that you explicitly specify as friends can access `internal` (C#) or `Friend` (Visual Basic) types and members.</span></span> <span data-ttu-id="44916-116">Örneğin, *AssemblyB Assembly* *A'nın* arkadaşıysa ve *C Derlemesi* *AssemblyB'ye*başvuruyorsa, *Derleme C'nin* A `internal` *Derlemesi'ndeki*(C#) veya `Friend` (Visual Basic) türlerine erişimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="44916-116">For example, if *AssemblyB* is a friend of *Assembly A* and *Assembly C* references *AssemblyB*, *Assembly C* does not have access to `internal` (C#) or `Friend` (Visual Basic) types in *Assembly A*.</span></span>

<span data-ttu-id="44916-117">Derleyici öznitelik geçirilen <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> arkadaş derleme adının bazı temel doğrulama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="44916-117">The compiler performs some basic validation of the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="44916-118">*A Derlemesi* *AssemblyB'yi* arkadaş derlemesi olarak bildirirse, doğrulama kuralları aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="44916-118">If *Assembly A* declares *AssemblyB* as a friend assembly, the validation rules are as follows:</span></span>

- <span data-ttu-id="44916-119">*A Derlemesi* güçlü adlandırılmışsa, *AssemblyB* de güçlü adlandırılmış olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="44916-119">If *Assembly A* is strong named, *AssemblyB* must also be strong named.</span></span> <span data-ttu-id="44916-120">Öznitelik geçirilen arkadaş derleme adı derleme adı ve *AssemblyB*imzalamak için kullanılan güçlü ad anahtarının ortak anahtarı ndan oluşmalıdır.</span><span class="sxs-lookup"><span data-stu-id="44916-120">The friend assembly name that is passed to the attribute must consist of the assembly name and the public key of the strong-name key that is used to sign *AssemblyB*.</span></span>

     <span data-ttu-id="44916-121">Özniteliğe <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> geçirilen arkadaş derleme adı *AssemblyB'nin*güçlü adı olamaz.</span><span class="sxs-lookup"><span data-stu-id="44916-121">The friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute cannot be the strong name of *AssemblyB*.</span></span> <span data-ttu-id="44916-122">Derleme sürümünü, kültürü, mimariyi veya ortak anahtar belirteci eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="44916-122">Don't include the assembly version, culture, architecture, or public key token.</span></span>

- <span data-ttu-id="44916-123">*A Derlemesi* güçlü adlandırılmış değilse, arkadaş derleme adı yalnızca derleme adından oluşmalıdır.</span><span class="sxs-lookup"><span data-stu-id="44916-123">If *Assembly A* is not strong named, the friend assembly name should consist of only the assembly name.</span></span> <span data-ttu-id="44916-124">Daha fazla bilgi için [bkz: İmzalanmamış arkadaş derlemeleri oluşturun.](create-unsigned-friend.md)</span><span class="sxs-lookup"><span data-stu-id="44916-124">For more information, see [How to: Create unsigned friend assemblies](create-unsigned-friend.md).</span></span>

- <span data-ttu-id="44916-125">*AssemblyB* güçlü adlandırılmışsa, proje ayarını veya komut satırı `/keyfile` derleyicisi seçeneğini kullanarak *AssemblyB* için güçlü ad anahtarını belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="44916-125">If *AssemblyB* is strong named, you must specify the strong-name key for *AssemblyB* by using the project setting or the command-line `/keyfile` compiler option.</span></span> <span data-ttu-id="44916-126">Daha fazla bilgi için [bkz: İmzalı arkadaş derlemeleri oluşturun.](create-signed-friend.md)</span><span class="sxs-lookup"><span data-stu-id="44916-126">For more information, see [How to: Create signed friend assemblies](create-signed-friend.md).</span></span>

 <span data-ttu-id="44916-127">Sınıf <xref:System.Security.Permissions.StrongNameIdentityPermission> ayrıca, aşağıdaki farklılıklarla türleri paylaşma olanağı da sağlar:</span><span class="sxs-lookup"><span data-stu-id="44916-127">The <xref:System.Security.Permissions.StrongNameIdentityPermission> class also provides the ability to share types, with the following differences:</span></span>

- <span data-ttu-id="44916-128"><xref:System.Security.Permissions.StrongNameIdentityPermission>tek bir tür için geçerlidir, bir arkadaş derlemesi ise tüm derleme için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="44916-128"><xref:System.Security.Permissions.StrongNameIdentityPermission> applies to an individual type, while a friend assembly applies to the whole assembly.</span></span>

- <span data-ttu-id="44916-129">*Assembly A'da* *AssemblyB*ile paylaşmak istediğiniz yüzlerce tür varsa, <xref:System.Security.Permissions.StrongNameIdentityPermission> bunların tümüne eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="44916-129">If there are hundreds of types in *Assembly A* that you want to share with *AssemblyB*, you have to add <xref:System.Security.Permissions.StrongNameIdentityPermission> to all of them.</span></span> <span data-ttu-id="44916-130">Bir arkadaş derlemesi kullanıyorsanız, arkadaş ilişkisini yalnızca bir kez bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="44916-130">If you use a friend assembly, you only need to declare the friend relationship once.</span></span>

- <span data-ttu-id="44916-131"><xref:System.Security.Permissions.StrongNameIdentityPermission>Kullanıyorsanız, paylaşmak istediğiniz türlerin herkese açık olarak bildirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="44916-131">If you use <xref:System.Security.Permissions.StrongNameIdentityPermission>, the types you want to share have to be declared as public.</span></span> <span data-ttu-id="44916-132">Bir arkadaş derlemesi kullanıyorsanız, paylaşılan `internal` türler (C#) veya `Friend` (Visual Basic) olarak bildirilir.</span><span class="sxs-lookup"><span data-stu-id="44916-132">If you use a friend assembly, the shared types are declared as `internal` (C#) or `Friend` (Visual Basic).</span></span>

<span data-ttu-id="44916-133">Bir derlemenin `internal` (C#) veya (Visual `Friend` Basic) türlerine ve yöntemlerine bir modül dosyasından *(.netmodule* uzantılı bir [dosya)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) nasıl erişilir hakkında bilgi için [bkz.](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)</span><span class="sxs-lookup"><span data-stu-id="44916-133">For information about how to access an assembly's `internal` (C#) or `Friend` (Visual Basic) types and methods from a module file (a file with the *.netmodule* extension), see [-moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) or [-moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="44916-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44916-134">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [<span data-ttu-id="44916-135">Nasıl yapilir: İmzalanmamış arkadaş derlemeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="44916-135">How to: Create unsigned friend assemblies</span></span>](create-unsigned-friend.md)
- [<span data-ttu-id="44916-136">Nasıl yapılsın: İmzalı arkadaş derlemeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="44916-136">How to: Create signed friend assemblies</span></span>](create-signed-friend.md)
- [<span data-ttu-id="44916-137">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="44916-137">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="44916-138">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="44916-138">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="44916-139">Programlama kavramları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44916-139">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
