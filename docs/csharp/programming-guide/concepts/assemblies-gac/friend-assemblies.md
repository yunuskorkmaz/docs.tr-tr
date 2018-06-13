---
title: Arkadaş derlemeler (C#)
ms.date: 07/20/2015
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
ms.openlocfilehash: c9265a6ce53d97f1d0b8aaeb0f1aae3b7b75f2cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33320872"
---
# <a name="friend-assemblies-c"></a><span data-ttu-id="4d6f5-102">Arkadaş derlemeler (C#)</span><span class="sxs-lookup"><span data-stu-id="4d6f5-102">Friend Assemblies (C#)</span></span>
<span data-ttu-id="4d6f5-103">A *derlemeyi* başka bir derlemenin erişebileceği bir derleme [iç](../../../../csharp/language-reference/keywords/internal.md) türleri ve üyeleri.</span><span class="sxs-lookup"><span data-stu-id="4d6f5-103">A *friend assembly* is an assembly that can access another assembly's [internal](../../../../csharp/language-reference/keywords/internal.md) types and members.</span></span> <span data-ttu-id="4d6f5-104">Derleme bir derlemeyi olarak belirlerseniz, artık işareti türleri ve bunları sırayla genel olarak üyeleri diğer derlemelerden tarafından erişilecek yok.</span><span class="sxs-lookup"><span data-stu-id="4d6f5-104">If you identify an assembly as a friend assembly, you no longer have to mark types and members as public in order for them to be accessed by other assemblies.</span></span> <span data-ttu-id="4d6f5-105">Bu özellikle aşağıdaki senaryolarda kullanışlıdır:</span><span class="sxs-lookup"><span data-stu-id="4d6f5-105">This is especially convenient in the following scenarios:</span></span>  
  
-   <span data-ttu-id="4d6f5-106">Birim testi sırasında test kodu çalıştırdığında, ayrı bir derleme ancak olarak işaretlenmiş sınanan derlemesindeki üyelerine erişimi gerektirir. `internal` .</span><span class="sxs-lookup"><span data-stu-id="4d6f5-106">During unit testing, when test code runs in a separate assembly but requires access to members in the assembly being tested that are marked as `internal` .</span></span>  
  
-   <span data-ttu-id="4d6f5-107">Ne zaman bir sınıf kitaplığı geliştirdiğiniz ve kitaplık eklemeler ayrı derlemelerde bulunan ancak olarak işaretlenmiş mevcut derlemeleri üyeler erişim gerektiren `internal` .</span><span class="sxs-lookup"><span data-stu-id="4d6f5-107">When you are developing a class library and additions to the library are contained in separate assemblies but require access to members in existing assemblies that are marked as `internal` .</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d6f5-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4d6f5-108">Remarks</span></span>  
 <span data-ttu-id="4d6f5-109">Kullanabileceğiniz <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> verilen derleme için bir veya daha fazla arkadaş derlemeleri tanımlamak için öznitelik.</span><span class="sxs-lookup"><span data-stu-id="4d6f5-109">You can use the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to identify one or more friend assemblies for a given assembly.</span></span> <span data-ttu-id="4d6f5-110">Aşağıdaki örnek kullanır <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği bir derlemede ve derleme belirten `AssemblyB` Arkadaş derlemesi olarak.</span><span class="sxs-lookup"><span data-stu-id="4d6f5-110">The following example uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute in assembly A and specifies assembly `AssemblyB` as a friend assembly.</span></span> <span data-ttu-id="4d6f5-111">Bu derleme verir `AssemblyB` tüm türleri ve üyeleri bir olarak işaretlenmiş derlemede erişim `internal`.</span><span class="sxs-lookup"><span data-stu-id="4d6f5-111">This gives assembly `AssemblyB` access to all types and members in assembly A that are marked as `internal`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4d6f5-112">Derleme zaman derleme (derleme `AssemblyB`) iç türleri veya başka bir derleme iç üyeleri erişecek (derleme *A*), kullanarakaçıkça(.exeveya.dll)çıkışdosyasınınadıbelirtmelisiniz **/out** derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="4d6f5-112">When you compile an assembly (assembly `AssemblyB`) that will access internal types or internal members of another assembly (assembly *A*), you must explicitly specify the name of the output file (.exe or .dll) by using the **/out** compiler option.</span></span> <span data-ttu-id="4d6f5-113">Derleyici henüz dış başvuruları bağlama zamanında oluşturma derleme adı üretti değil çünkü bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4d6f5-113">This is required because the compiler has not yet generated the name for the assembly it is building at the time it is binding to external references.</span></span> <span data-ttu-id="4d6f5-114">Daha fazla bilgi için bkz: [/out (C#)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="4d6f5-114">For more information, see [/out (C#)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md) .</span></span>  
  
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
  
 <span data-ttu-id="4d6f5-115">Arkadaş erişebileceği, açıkça belirttiğiniz derlemeleri `internal` türleri ve üyeleri.</span><span class="sxs-lookup"><span data-stu-id="4d6f5-115">Only assemblies that you explicitly specify as friends can access `internal` types and members.</span></span> <span data-ttu-id="4d6f5-116">Derleme B Arkadaş derlemesi ve C derleme başvurularını derleme B ise, örneğin, C erişimi yok `internal` A'daki türleri</span><span class="sxs-lookup"><span data-stu-id="4d6f5-116">For example, if assembly B is a friend of assembly A and assembly C references assembly B, C does not have access to `internal` types in A.</span></span>  
  
 <span data-ttu-id="4d6f5-117">Bazı temel doğrulama geçirilen arkadaş derleme adının derleyici gerçekleştirir <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="4d6f5-117">The compiler performs some basic validation of the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="4d6f5-118">Derleme *A* bildirir *B* arkadaş derleme olarak doğrulama kuralları aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="4d6f5-118">If assembly *A* declares *B* as a friend assembly, the validation rules are as follows:</span></span>  
  
-   <span data-ttu-id="4d6f5-119">Derleme *A* adlı, derleme güçlü olan *B* de strong adlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4d6f5-119">If assembly *A* is strong named, assembly *B* must also be strong named.</span></span> <span data-ttu-id="4d6f5-120">Özniteliğe geçirilen arkadaş derleme adı derleme adı ve derlemeyi imzalamak için kullanılan tanımlayıcı ad anahtar ortak anahtarını oluşmalıdır *B*.</span><span class="sxs-lookup"><span data-stu-id="4d6f5-120">The friend assembly name that is passed to the attribute must consist of the assembly name and the public key of the strong-name key that is used to sign assembly *B*.</span></span>  
  
     <span data-ttu-id="4d6f5-121">Geçirilir arkadaş derleme adı <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği olamaz derleme güçlü adı *B*: derleme sürüm, kültür, mimari veya ortak anahtar belirteci içermez.</span><span class="sxs-lookup"><span data-stu-id="4d6f5-121">The friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute cannot be the strong name of assembly *B*: do not include the assembly version, culture, architecture, or public key token.</span></span>  
  
-   <span data-ttu-id="4d6f5-122">Derleme *A* adlı arkadaş derleme adı yalnızca derleme adını oluşması sağlam değil.</span><span class="sxs-lookup"><span data-stu-id="4d6f5-122">If assembly *A* is not strong named, the friend assembly name should consist of only the assembly name.</span></span> <span data-ttu-id="4d6f5-123">Daha fazla bilgi için bkz: [nasıl yapılır: İmzasız arkadaş derlemeleri oluşturma (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="4d6f5-123">For more information, see [How to: Create Unsigned Friend Assemblies (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).</span></span>  
  
-   <span data-ttu-id="4d6f5-124">Derleme *B* adlı, derleme için güçlü ad anahtar belirtmelisiniz güçlü olan *B* proje ayarı veya komut satırı kullanarak `/keyfile` derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="4d6f5-124">If assembly *B* is strong named, you must specify the strong-name key for assembly *B* by using the project setting or the command-line `/keyfile` compiler option.</span></span> <span data-ttu-id="4d6f5-125">Daha fazla bilgi için bkz: [nasıl yapılır: imzalı arkadaş derlemeleri oluşturma (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="4d6f5-125">For more information, see [How to: Create Signed Friend Assemblies (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).</span></span>  
  
 <span data-ttu-id="4d6f5-126"><xref:System.Security.Permissions.StrongNameIdentityPermission> Sınıfı türleri, aşağıdaki farklarla paylaşma olanağı sağlar:</span><span class="sxs-lookup"><span data-stu-id="4d6f5-126">The <xref:System.Security.Permissions.StrongNameIdentityPermission> class also provides the ability to share types, with the following differences:</span></span>  
  
-   <span data-ttu-id="4d6f5-127"><xref:System.Security.Permissions.StrongNameIdentityPermission> bir derlemeyi tüm derlemeye uygularken tek tek bir türü için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4d6f5-127"><xref:System.Security.Permissions.StrongNameIdentityPermission> applies to an individual type, while a friend assembly applies to the whole assembly.</span></span>  
  
-   <span data-ttu-id="4d6f5-128">Derlemedeki türleri yüzlerce varsa *A* derleme paylaşmak istediğiniz *B*, eklemek zorunda <xref:System.Security.Permissions.StrongNameIdentityPermission> bunların tümüne.</span><span class="sxs-lookup"><span data-stu-id="4d6f5-128">If there are hundreds of types in assembly *A* that you want to share with assembly *B*, you have to add <xref:System.Security.Permissions.StrongNameIdentityPermission> to all of them.</span></span> <span data-ttu-id="4d6f5-129">Bir derlemeyi kullanırsanız, yalnızca arkadaş ilişki kez bildirme gerekir.</span><span class="sxs-lookup"><span data-stu-id="4d6f5-129">If you use a friend assembly, you only need to declare the friend relationship once.</span></span>  
  
-   <span data-ttu-id="4d6f5-130">Kullanırsanız <xref:System.Security.Permissions.StrongNameIdentityPermission>, paylaşmak istediğiniz türleri genel olarak bildirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="4d6f5-130">If you use <xref:System.Security.Permissions.StrongNameIdentityPermission>, the types you want to share have to be declared as public.</span></span> <span data-ttu-id="4d6f5-131">Bir derlemeyi kullanırsanız, paylaşılan türleri olarak bildirilen `internal`.</span><span class="sxs-lookup"><span data-stu-id="4d6f5-131">If you use a friend assembly, the shared types are declared as `internal`.</span></span>  
  
 <span data-ttu-id="4d6f5-132">Bir derlemenin erişim hakkında bilgi için `internal` türleri ve yöntemleri modülü dosyasından (uzantılı bir dosya .netmodule), bkz: [/moduleassemblyname (C#)](../../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="4d6f5-132">For information about how to access an assembly's `internal` types and methods from a module file (a file with the .netmodule extension), see [/moduleassemblyname (C#)](../../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d6f5-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4d6f5-133">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 <xref:System.Security.Permissions.StrongNameIdentityPermission>  
 [<span data-ttu-id="4d6f5-134">Nasıl yapılır: İmzasız arkadaş derlemeleri (C#) oluşturma</span><span class="sxs-lookup"><span data-stu-id="4d6f5-134">How to: Create Unsigned Friend Assemblies (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)  
 [<span data-ttu-id="4d6f5-135">Nasıl yapılır: imzalı arkadaş derlemeleri (C#) oluşturma</span><span class="sxs-lookup"><span data-stu-id="4d6f5-135">How to: Create Signed Friend Assemblies (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)  
 [<span data-ttu-id="4d6f5-136">Derlemeler ve Genel Derleme Önbelleği (C#)</span><span class="sxs-lookup"><span data-stu-id="4d6f5-136">Assemblies and the Global Assembly Cache (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="4d6f5-137">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4d6f5-137">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
