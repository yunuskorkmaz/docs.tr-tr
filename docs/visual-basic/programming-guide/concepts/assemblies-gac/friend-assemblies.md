---
title: Arkadaş derlemeler (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9b3d5716-e6e4-47a7-a3e9-084d7fba5c28
ms.openlocfilehash: 9b91f894f9b10c85eb322b4421fd0473335df7a3
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56748160"
---
# <a name="friend-assemblies-visual-basic"></a><span data-ttu-id="ce2b5-102">Arkadaş derlemeler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce2b5-102">Friend Assemblies (Visual Basic)</span></span>
<span data-ttu-id="ce2b5-103">A *arkadaş derleme* başka bir derlemenin erişebilen bir derleme [arkadaş](../../../../visual-basic/language-reference/modifiers/friend.md) türler ve üyeler.</span><span class="sxs-lookup"><span data-stu-id="ce2b5-103">A *friend assembly* is an assembly that can access another assembly's [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) types and members.</span></span> <span data-ttu-id="ce2b5-104">Derleme arkadaş derleme olarak belirlerseniz, artık türleri ve üyeleri edebilmeleri genel olarak diğer derlemeler tarafından erişilecek işareti yok.</span><span class="sxs-lookup"><span data-stu-id="ce2b5-104">If you identify an assembly as a friend assembly, you no longer have to mark types and members as public in order for them to be accessed by other assemblies.</span></span> <span data-ttu-id="ce2b5-105">Bu, özellikle aşağıdaki senaryolarda kullanışlıdır:</span><span class="sxs-lookup"><span data-stu-id="ce2b5-105">This is especially convenient in the following scenarios:</span></span>  
  
-   <span data-ttu-id="ce2b5-106">Birim testi sırasında test kod çalıştığında ayrı bir derleme ancak test edilen derleme üyeleri olarak işaretlenmiş erişim gerektirir. `Friend`.</span><span class="sxs-lookup"><span data-stu-id="ce2b5-106">During unit testing, when test code runs in a separate assembly but requires access to members in the assembly being tested that are marked as `Friend`.</span></span>  
  
-   <span data-ttu-id="ce2b5-107">Ne zaman bir sınıf kitaplığı geliştiriyorsanız ve kitaplığı eklemeleri ayrı derlemelerinde toplanır, ancak üye olarak işaretlenmiş var olan derlemelerde erişmesi `Friend`.</span><span class="sxs-lookup"><span data-stu-id="ce2b5-107">When you are developing a class library and additions to the library are contained in separate assemblies but require access to members in existing assemblies that are marked as `Friend`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce2b5-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ce2b5-108">Remarks</span></span>  
 <span data-ttu-id="ce2b5-109">Kullanabileceğiniz <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> belirli bir derleme için bir veya daha fazla arkadaş derlemeleri tanımlamak için öznitelik.</span><span class="sxs-lookup"><span data-stu-id="ce2b5-109">You can use the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to identify one or more friend assemblies for a given assembly.</span></span> <span data-ttu-id="ce2b5-110">Aşağıdaki örnekte <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> öznitelik bir derlemede ve derleme belirtir `AssemblyB` arkadaş derleme olarak.</span><span class="sxs-lookup"><span data-stu-id="ce2b5-110">The following example uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute in assembly A and specifies assembly `AssemblyB` as a friend assembly.</span></span> <span data-ttu-id="ce2b5-111">Bu derleme verir `AssemblyB` tüm türleri ve üyeleri bir olarak işaretlenmiş derleme erişimi `Friend`.</span><span class="sxs-lookup"><span data-stu-id="ce2b5-111">This gives assembly `AssemblyB` access to all types and members in assembly A that are marked as `Friend`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ce2b5-112">Derleme yaparken bir derleme (derleme `AssemblyB`) iç türleri veya başka bir derlemenin iç üyeleri erişir (derleme *A*), çıktı dosyası (.exe veya .dll) adı kullanarakaçıkçabelirtmenizgerekir **/out** derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="ce2b5-112">When you compile an assembly (assembly `AssemblyB`) that will access internal types or internal members of another assembly (assembly *A*), you must explicitly specify the name of the output file (.exe or .dll) by using the **/out** compiler option.</span></span> <span data-ttu-id="ce2b5-113">Bu, derleyicinin onu dış başvuruları bağlayarak zaman oluşturma derleme adı henüz oluşturmamıştır çünkü gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ce2b5-113">This is required because the compiler has not yet generated the name for the assembly it is building at the time it is binding to external references.</span></span> <span data-ttu-id="ce2b5-114">Daha fazla bilgi için [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="ce2b5-114">For more information, see [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).</span></span>  
  
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
  
 <span data-ttu-id="ce2b5-115">Arkadaş erişebilir, açıkça belirttiğiniz derlemeleri `Friend` türler ve üyeler.</span><span class="sxs-lookup"><span data-stu-id="ce2b5-115">Only assemblies that you explicitly specify as friends can access `Friend` types and members.</span></span> <span data-ttu-id="ce2b5-116">Derleme B C derleme başvuruları derleme B derleme A'ya ve arkadaş ise, örneğin, C erişimi yok `Friend` A'daki türleri</span><span class="sxs-lookup"><span data-stu-id="ce2b5-116">For example, if assembly B is a friend of assembly A and assembly C references assembly B, C does not have access to `Friend` types in A.</span></span>  
  
 <span data-ttu-id="ce2b5-117">Derleyici geçirilen friend derleme adı, bazı temel doğrulama gerçekleştirir <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="ce2b5-117">The compiler performs some basic validation of the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="ce2b5-118">Derleme *A* bildirir *B* arkadaş derleme, doğrulama kuralları aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="ce2b5-118">If assembly *A* declares *B* as a friend assembly, the validation rules are as follows:</span></span>  
  
-   <span data-ttu-id="ce2b5-119">Derleme *A* adlı derleme güçlü olduğunu *B* ayrıca strong adlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ce2b5-119">If assembly *A* is strong named, assembly *B* must also be strong named.</span></span> <span data-ttu-id="ce2b5-120">Özniteliğe geçirilir friend derleme adı, derleme adı ve derlemeyi imzalamak için kullanılan tanımlayıcı ad anahtarı ortak anahtarını oluşmalıdır *B*.</span><span class="sxs-lookup"><span data-stu-id="ce2b5-120">The friend assembly name that is passed to the attribute must consist of the assembly name and the public key of the strong-name key that is used to sign assembly *B*.</span></span>  
  
     <span data-ttu-id="ce2b5-121">Geçirilen friend derleme adı <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği olamaz derleme tanımlayıcı adı *B*: derleme sürüm, kültür, mimari veya ortak anahtar belirteci içermez.</span><span class="sxs-lookup"><span data-stu-id="ce2b5-121">The friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute cannot be the strong name of assembly *B*: do not include the assembly version, culture, architecture, or public key token.</span></span>  
  
-   <span data-ttu-id="ce2b5-122">Derleme *A* adlı friend derleme adı yalnızca derleme adını oluşmalıdır sağlam değil.</span><span class="sxs-lookup"><span data-stu-id="ce2b5-122">If assembly *A* is not strong named, the friend assembly name should consist of only the assembly name.</span></span> <span data-ttu-id="ce2b5-123">Daha fazla bilgi için [nasıl yapılır: (Visual Basic) imzasız arkadaş derlemeleri oluşturma](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="ce2b5-123">For more information, see [How to: Create Unsigned Friend Assemblies (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).</span></span>  
  
-   <span data-ttu-id="ce2b5-124">Derleme *B* adındaki, derlemenin tanımlayıcı ad anahtarı belirtmeniz gerekir güçlü olduğunu *B* proje ayarı veya komut satırı kullanarak `/keyfile` derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="ce2b5-124">If assembly *B* is strong named, you must specify the strong-name key for assembly *B* by using the project setting or the command-line `/keyfile` compiler option.</span></span> <span data-ttu-id="ce2b5-125">Daha fazla bilgi için [nasıl yapılır: (Visual Basic) imzalı arkadaş derlemeleri oluşturma](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="ce2b5-125">For more information, see [How to: Create Signed Friend Assemblies (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).</span></span>  
  
 <span data-ttu-id="ce2b5-126"><xref:System.Security.Permissions.StrongNameIdentityPermission> Sınıf türleri ile aşağıdaki farklar paylaşma olanağı da sağlar:</span><span class="sxs-lookup"><span data-stu-id="ce2b5-126">The <xref:System.Security.Permissions.StrongNameIdentityPermission> class also provides the ability to share types, with the following differences:</span></span>  
  
-   <span data-ttu-id="ce2b5-127"><xref:System.Security.Permissions.StrongNameIdentityPermission> arkadaş derleme tüm derleme için geçerli olsa da tek tek bir tür için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ce2b5-127"><xref:System.Security.Permissions.StrongNameIdentityPermission> applies to an individual type, while a friend assembly applies to the whole assembly.</span></span>  
  
-   <span data-ttu-id="ce2b5-128">Bütünleştirilmiş kodundaki türler yüzlerce varsa *A* derleme ile paylaşmak istediğiniz *B*, eklemek zorunda <xref:System.Security.Permissions.StrongNameIdentityPermission> bunların tümüne.</span><span class="sxs-lookup"><span data-stu-id="ce2b5-128">If there are hundreds of types in assembly *A* that you want to share with assembly *B*, you have to add <xref:System.Security.Permissions.StrongNameIdentityPermission> to all of them.</span></span> <span data-ttu-id="ce2b5-129">Arkadaş derleme kullanıyorsanız, yalnızca arkadaş ilişki bildirmek üzere gerekir.</span><span class="sxs-lookup"><span data-stu-id="ce2b5-129">If you use a friend assembly, you only need to declare the friend relationship once.</span></span>  
  
-   <span data-ttu-id="ce2b5-130">Kullanırsanız <xref:System.Security.Permissions.StrongNameIdentityPermission>, paylaşmak istediğiniz türleri genel olarak bildirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="ce2b5-130">If you use <xref:System.Security.Permissions.StrongNameIdentityPermission>, the types you want to share have to be declared as public.</span></span> <span data-ttu-id="ce2b5-131">Arkadaş derleme kullanırsanız, paylaşılan türü olarak bildirilmiş olan `Friend`.</span><span class="sxs-lookup"><span data-stu-id="ce2b5-131">If you use a friend assembly, the shared types are declared as `Friend`.</span></span>  
  
 <span data-ttu-id="ce2b5-132">Bir derlemenin erişim hakkında daha fazla bilgi için `Friend` türleri ve yöntemleri bir modül dosyası (bir .netmodule uzantılı), bkz. [/moduleassemblyname (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span><span class="sxs-lookup"><span data-stu-id="ce2b5-132">For information about how to access an assembly's `Friend` types and methods from a module file (a file with the .netmodule extension), see [/moduleassemblyname (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce2b5-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce2b5-133">See also</span></span>
- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [<span data-ttu-id="ce2b5-134">Nasıl yapılır: (Visual Basic) imzasız arkadaş derlemeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="ce2b5-134">How to: Create Unsigned Friend Assemblies (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)
- [<span data-ttu-id="ce2b5-135">Nasıl yapılır: (Visual Basic) imzalı arkadaş derlemeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="ce2b5-135">How to: Create Signed Friend Assemblies (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)
- [<span data-ttu-id="ce2b5-136">.NET derlemeleri</span><span class="sxs-lookup"><span data-stu-id="ce2b5-136">Assemblies in .NET</span></span>](../../../../standard/assembly/index.md)
- [<span data-ttu-id="ce2b5-137">Programlama Kavramları</span><span class="sxs-lookup"><span data-stu-id="ce2b5-137">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)
