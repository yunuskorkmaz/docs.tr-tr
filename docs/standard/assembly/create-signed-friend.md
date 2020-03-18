---
title: 'Nasıl yapılsın: İmzalı arkadaş derlemeleri oluşturma'
ms.date: 08/19/2019
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
dev_langs:
- csharp
- vb
ms.openlocfilehash: 9912fa70014a8828e994cf528644aaa7cb351fea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159500"
---
# <a name="how-to-create-signed-friend-assemblies"></a><span data-ttu-id="c2355-102">Nasıl yapılsın: İmzalı arkadaş derlemeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="c2355-102">How to: Create signed friend assemblies</span></span>
<span data-ttu-id="c2355-103">Bu örnek, güçlü adlara sahip derlemelerle arkadaş derlemelerinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c2355-103">This example shows how to use friend assemblies with assemblies that have strong names.</span></span> <span data-ttu-id="c2355-104">Her iki derlemede de güçlü bir isim lendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="c2355-104">Both assemblies must be strong named.</span></span> <span data-ttu-id="c2355-105">Bu örnekteki her iki derleme de aynı anahtarları kullansa da, iki derleme için farklı anahtarlar kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2355-105">Although both assemblies in this example use the same keys, you could use different keys for two assemblies.</span></span>  
  
## <a name="create-a-signed-assembly-and-a-friend-assembly"></a><span data-ttu-id="c2355-106">İmzalı derleme ve arkadaş derlemesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="c2355-106">Create a signed assembly and a friend assembly</span></span>  
  
1. <span data-ttu-id="c2355-107">Bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="c2355-107">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="c2355-108">Bir anahtar dosyası oluşturmak ve ortak anahtarını görüntülemek için Güçlü Ad aracıyla aşağıdaki komut sırasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="c2355-108">Use the following sequence of commands with the Strong Name tool to generate a keyfile and to display its public key.</span></span> <span data-ttu-id="c2355-109">Daha fazla bilgi için [Bkz. Sn.exe (Güçlü Ad aracı)](../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="c2355-109">For more information, see [Sn.exe (Strong Name tool)](../../framework/tools/sn-exe-strong-name-tool.md).</span></span>  
  
    1. <span data-ttu-id="c2355-110">Bu örnek için güçlü bir ad anahtarı oluşturun ve *FriendAssemblies.snk*dosyasında saklayın:</span><span class="sxs-lookup"><span data-stu-id="c2355-110">Generate a strong-name key for this example and store it in the file *FriendAssemblies.snk*:</span></span>  
  
         `sn -k FriendAssemblies.snk`  
  
    2. <span data-ttu-id="c2355-111">*FriendAssemblies.snk* gelen ortak anahtarı ayıklayın ve *FriendAssemblies.publickey*içine koymak:</span><span class="sxs-lookup"><span data-stu-id="c2355-111">Extract the public key from *FriendAssemblies.snk* and put it into *FriendAssemblies.publickey*:</span></span>  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3. <span data-ttu-id="c2355-112">*FriendAssemblies.publickey*dosyasında depolanan ortak anahtarı görüntüleyin:</span><span class="sxs-lookup"><span data-stu-id="c2355-112">Display the public key stored in the file *FriendAssemblies.publickey*:</span></span>  
  
         `sn -tp FriendAssemblies.publickey`  
  
3. <span data-ttu-id="c2355-113">Aşağıdaki kodu içeren *friend_signed_A* adlı bir C# veya Visual Basic dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c2355-113">Create a C# or Visual Basic file named *friend_signed_A* that contains the following code.</span></span> <span data-ttu-id="c2355-114">Kod, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> *friend_signed_B* arkadaş derlemesi olarak bildirmek için özniteliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="c2355-114">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare *friend_signed_B* as a friend assembly.</span></span>  

   <span data-ttu-id="c2355-115">Güçlü Ad aracı her çalıştığında yeni bir ortak anahtar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c2355-115">The Strong Name tool generates a new public key every time it runs.</span></span> <span data-ttu-id="c2355-116">Bu nedenle, aşağıdaki koddaki ortak anahtarı, aşağıdaki örnekte gösterildiği gibi, oluşturduğunuz ortak anahtarla değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c2355-116">Therefore, you must replace the public key in the following code with the public key you just generated, as shown in the following example.</span></span>  

   ```csharp  
   // friend_signed_A.cs  
   // Compile with:
   // csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
   using System.Runtime.CompilerServices;  

   [assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")]  
   class Class1  
   {  
       public void Test()  
       {  
           System.Console.WriteLine("Class1.Test");  
           System.Console.ReadLine();  
       }  
   }  
   ```  

   ```vb  
   ' friend_signed_A.vb  
   ' Compile with:
   ' Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
   Imports System.Runtime.CompilerServices  

   <Assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")>
   Public Class Class1  
       Public Sub Test()  
           System.Console.WriteLine("Class1.Test")  
           System.Console.ReadLine()  
       End Sub  
   End Class  
   ```  

4. <span data-ttu-id="c2355-117">Aşağıdaki komutu kullanarak *friend_signed_A* derve imzalayın.</span><span class="sxs-lookup"><span data-stu-id="c2355-117">Compile and sign *friend_signed_A* by using the following command.</span></span>  

   ```csharp
   csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
   ```  

   ```vb
   Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
   ```  

5. <span data-ttu-id="c2355-118">Aşağıdaki kodu içeren *friend_signed_B* adlı bir C# veya Visual Basic dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c2355-118">Create a C# or Visual Basic file named *friend_signed_B* that contains the following code.</span></span> <span data-ttu-id="c2355-119">*friend_signed_A* *friend_signed_B* bir arkadaş derlemesi olarak belirttiğinden, *friend_signed_B'daki* `Friend` kod (C#) veya (Visual Basic) türlerine ve *friend_signed_A'dan*üyelere erişebilir. `internal`</span><span class="sxs-lookup"><span data-stu-id="c2355-119">Because *friend_signed_A* specifies *friend_signed_B* as a friend assembly, the code in *friend_signed_B* can access `internal` (C#) or `Friend` (Visual Basic) types and members from *friend_signed_A*.</span></span> <span data-ttu-id="c2355-120">Dosya aşağıdaki kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="c2355-120">The file contains the following code.</span></span>  

   ```csharp  
   // friend_signed_B.cs  
   // Compile with:
   // csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
   public class Program  
   {  
       static void Main()  
       {  
           Class1 inst = new Class1();  
           inst.Test();  
       }  
   }  
   ```  

   ```vb  
   ' friend_signed_B.vb  
   ' Compile with:
   ' Vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
   Module Sample  
       Public Sub Main()  
           Dim inst As New Class1  
           inst.Test()  
       End Sub  
   End Module  
   ```  

6. <span data-ttu-id="c2355-121">Aşağıdaki komutu kullanarak *friend_signed_B* derleyip imzalayın.</span><span class="sxs-lookup"><span data-stu-id="c2355-121">Compile and sign *friend_signed_B* by using the following command.</span></span>  

   ```csharp
   csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
   ```  

   ```vb
   vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
   ```  

   <span data-ttu-id="c2355-122">Derleyici tarafından oluşturulan derlemenin adı öznitelik geçirilen <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> arkadaş derleme adı eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="c2355-122">The name of the assembly generated by the compiler must match the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="c2355-123">`-out` Derleyici seçeneğini kullanarak çıktı derlemesinin *(.exe* veya *.dll)* adını açıkça belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c2355-123">You must explicitly specify the name of the output assembly (*.exe* or *.dll*) by using the `-out` compiler option.</span></span> <span data-ttu-id="c2355-124">Daha fazla bilgi için bkz: [-out (C# derleyici seçenekleri)](../../csharp/language-reference/compiler-options/out-compiler-option.md) veya [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="c2355-124">For more information, see [-out (C# compiler options)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span></span>  

7. <span data-ttu-id="c2355-125">*friend_signed_B.exe* dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c2355-125">Run the *friend_signed_B.exe* file.</span></span>  

   <span data-ttu-id="c2355-126">Program string **Class1.Test**çıktıları .</span><span class="sxs-lookup"><span data-stu-id="c2355-126">The program outputs the string **Class1.Test**.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="c2355-127">.NET güvenlik</span><span class="sxs-lookup"><span data-stu-id="c2355-127">.NET security</span></span>  
 <span data-ttu-id="c2355-128">Öznitelik ve <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> <xref:System.Security.Permissions.StrongNameIdentityPermission> sınıf arasında benzerlikler vardır.</span><span class="sxs-lookup"><span data-stu-id="c2355-128">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="c2355-129">Temel fark, <xref:System.Security.Permissions.StrongNameIdentityPermission> kodun belirli bir bölümünü çalıştırmak için güvenlik izinleri talep <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> edebilirken, `internal` öznitelik (C#) veya (Visual Basic) türlerinin ve `Friend` üyelerinin görünürlüğünü denetler.</span><span class="sxs-lookup"><span data-stu-id="c2355-129">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal` (C#) or `Friend` (Visual Basic) types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2355-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2355-130">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="c2355-131">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="c2355-131">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="c2355-132">Arkadaş meclisleri</span><span class="sxs-lookup"><span data-stu-id="c2355-132">Friend assemblies</span></span>](friend.md)
- [<span data-ttu-id="c2355-133">Nasıl yapilir: İmzalanmamış arkadaş derlemeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="c2355-133">How to: Create unsigned friend assemblies</span></span>](create-unsigned-friend.md)
- [<span data-ttu-id="c2355-134">-keyfile (C#)</span><span class="sxs-lookup"><span data-stu-id="c2355-134">-keyfile (C#)</span></span>](../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)
- [<span data-ttu-id="c2355-135">-keyfile (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2355-135">-keyfile (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/keyfile.md)
- [<span data-ttu-id="c2355-136">Sn.exe (Güçlü Ad aracı)</span><span class="sxs-lookup"><span data-stu-id="c2355-136">Sn.exe (Strong Name tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="c2355-137">Tanımlayıcı adlı derlemeler oluşturma ve kullanma</span><span class="sxs-lookup"><span data-stu-id="c2355-137">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
- [<span data-ttu-id="c2355-138">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c2355-138">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="c2355-139">Programlama kavramları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2355-139">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
