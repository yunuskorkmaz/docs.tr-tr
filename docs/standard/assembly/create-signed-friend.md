---
title: 'Nasıl yapılır: imzalı arkadaş derlemeleri oluşturma'
description: Bu makalede, friend derlemelerinin tanımlayıcı adlara sahip Derlemelerle nasıl kullanılacağı gösterilmektedir. .NET güvenliği hakkındaki bilgileri içerir.
ms.date: 08/19/2019
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
dev_langs:
- csharp
- vb
ms.openlocfilehash: b6176afed44e32911a37a0d753cea2bae7d8554e
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378538"
---
# <a name="how-to-create-signed-friend-assemblies"></a><span data-ttu-id="d5c98-104">Nasıl yapılır: imzalı arkadaş derlemeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="d5c98-104">How to: Create signed friend assemblies</span></span>
<span data-ttu-id="d5c98-105">Bu örnek, friend derlemelerinin tanımlayıcı adlara sahip Derlemelerle nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d5c98-105">This example shows how to use friend assemblies with assemblies that have strong names.</span></span> <span data-ttu-id="d5c98-106">Her iki derlemenin de tanımlayıcı adlandırılmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d5c98-106">Both assemblies must be strong named.</span></span> <span data-ttu-id="d5c98-107">Bu örnekteki her iki derleme de aynı anahtarları kullanmasına karşın, iki derleme için farklı anahtarlar kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5c98-107">Although both assemblies in this example use the same keys, you could use different keys for two assemblies.</span></span>  
  
## <a name="create-a-signed-assembly-and-a-friend-assembly"></a><span data-ttu-id="d5c98-108">İmzalı derleme ve arkadaş derleme oluşturma</span><span class="sxs-lookup"><span data-stu-id="d5c98-108">Create a signed assembly and a friend assembly</span></span>  
  
1. <span data-ttu-id="d5c98-109">Bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="d5c98-109">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="d5c98-110">Anahtar oluşturma ve ortak anahtarını görüntüleme için tanımlayıcı ad aracı ile aşağıdaki komut dizisini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d5c98-110">Use the following sequence of commands with the Strong Name tool to generate a keyfile and to display its public key.</span></span> <span data-ttu-id="d5c98-111">Daha fazla bilgi için bkz. [sn. exe (tanımlayıcı ad aracı)](../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="d5c98-111">For more information, see [Sn.exe (Strong Name tool)](../../framework/tools/sn-exe-strong-name-tool.md).</span></span>  
  
    1. <span data-ttu-id="d5c98-112">Bu örnek için bir tanımlayıcı ad anahtarı oluşturun ve *FriendAssemblies. snk*dosyasında depolayın:</span><span class="sxs-lookup"><span data-stu-id="d5c98-112">Generate a strong-name key for this example and store it in the file *FriendAssemblies.snk*:</span></span>  
  
         `sn -k FriendAssemblies.snk`  
  
    2. <span data-ttu-id="d5c98-113">Ortak anahtarı *FriendAssemblies. snk* konumundan ayıklayın ve *FriendAssemblies. PublicKey*dosyasına yerleştirin:</span><span class="sxs-lookup"><span data-stu-id="d5c98-113">Extract the public key from *FriendAssemblies.snk* and put it into *FriendAssemblies.publickey*:</span></span>  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3. <span data-ttu-id="d5c98-114">*FriendAssemblies. PublicKey*dosyasında depolanan ortak anahtarı görüntüle:</span><span class="sxs-lookup"><span data-stu-id="d5c98-114">Display the public key stored in the file *FriendAssemblies.publickey*:</span></span>  
  
         `sn -tp FriendAssemblies.publickey`  
  
3. <span data-ttu-id="d5c98-115">Aşağıdaki kodu içeren *friend_signed_A* adlı bir C# veya Visual Basic dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d5c98-115">Create a C# or Visual Basic file named *friend_signed_A* that contains the following code.</span></span> <span data-ttu-id="d5c98-116">Kod, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> *friend_signed_B* bir Friend derlemesi olarak bildirmek için özniteliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d5c98-116">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare *friend_signed_B* as a friend assembly.</span></span>  

   <span data-ttu-id="d5c98-117">Tanımlayıcı ad aracı her çalıştığında yeni bir ortak anahtar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d5c98-117">The Strong Name tool generates a new public key every time it runs.</span></span> <span data-ttu-id="d5c98-118">Bu nedenle, aşağıdaki örnekte gösterildiği gibi aşağıdaki koddaki ortak anahtarı yeni oluşturduğunuz ortak anahtarla değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="d5c98-118">Therefore, you must replace the public key in the following code with the public key you just generated, as shown in the following example.</span></span>  

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

4. <span data-ttu-id="d5c98-119">Aşağıdaki komutu kullanarak *friend_signed_A* derleyin ve imzalayın.</span><span class="sxs-lookup"><span data-stu-id="d5c98-119">Compile and sign *friend_signed_A* by using the following command.</span></span>  

   ```csharp
   csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
   ```  

   ```vb
   Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
   ```  

5. <span data-ttu-id="d5c98-120">Aşağıdaki kodu içeren *friend_signed_B* adlı bir C# veya Visual Basic dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d5c98-120">Create a C# or Visual Basic file named *friend_signed_B* that contains the following code.</span></span> <span data-ttu-id="d5c98-121">*Friend_signed_A* bir arkadaş derleme olarak *friend_signed_B* belirttiğinden *friend_signed_B* kodu, `internal` friend_signed_A Visual Basic (C#) veya `Friend` () türlerine ve üyelerine erişebilir. *friend_signed_A*</span><span class="sxs-lookup"><span data-stu-id="d5c98-121">Because *friend_signed_A* specifies *friend_signed_B* as a friend assembly, the code in *friend_signed_B* can access `internal` (C#) or `Friend` (Visual Basic) types and members from *friend_signed_A*.</span></span> <span data-ttu-id="d5c98-122">Dosya aşağıdaki kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="d5c98-122">The file contains the following code.</span></span>  

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

6. <span data-ttu-id="d5c98-123">Aşağıdaki komutu kullanarak *friend_signed_B* derleyin ve imzalayın.</span><span class="sxs-lookup"><span data-stu-id="d5c98-123">Compile and sign *friend_signed_B* by using the following command.</span></span>  

   ```csharp
   csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
   ```  

   ```vb
   vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
   ```  

   <span data-ttu-id="d5c98-124">Derleyici tarafından oluşturulan derlemenin adı özniteliğe geçirilen arkadaş derleme adıyla eşleşmelidir <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> .</span><span class="sxs-lookup"><span data-stu-id="d5c98-124">The name of the assembly generated by the compiler must match the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="d5c98-125">Derleyici seçeneğini kullanarak çıkış derlemesinin adını (*. exe* veya *. dll*) açıkça belirtmeniz gerekir `-out` .</span><span class="sxs-lookup"><span data-stu-id="d5c98-125">You must explicitly specify the name of the output assembly (*.exe* or *.dll*) by using the `-out` compiler option.</span></span> <span data-ttu-id="d5c98-126">Daha fazla bilgi için bkz. [-Out (C# derleyici seçenekleri)](../../csharp/language-reference/compiler-options/out-compiler-option.md) veya [-Out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="d5c98-126">For more information, see [-out (C# compiler options)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span></span>  

7. <span data-ttu-id="d5c98-127">*Friend_signed_B. exe* dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d5c98-127">Run the *friend_signed_B.exe* file.</span></span>  

   <span data-ttu-id="d5c98-128">Program **Class1. test**dizesini çıktı.</span><span class="sxs-lookup"><span data-stu-id="d5c98-128">The program outputs the string **Class1.Test**.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="d5c98-129">.NET güvenliği</span><span class="sxs-lookup"><span data-stu-id="d5c98-129">.NET security</span></span>  
 <span data-ttu-id="d5c98-130">Özniteliği ve sınıfı arasında benzerlikler vardır <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> <xref:System.Security.Permissions.StrongNameIdentityPermission> .</span><span class="sxs-lookup"><span data-stu-id="d5c98-130">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="d5c98-131">Temel fark, <xref:System.Security.Permissions.StrongNameIdentityPermission> kodun belirli bir bölümünü çalıştırmak için güvenlik izinleri talep edebilir, ancak <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> öznitelik `internal` (C#) veya `Friend` (Visual Basic) türlerinin görünürlüğünü ve üyelerini denetler.</span><span class="sxs-lookup"><span data-stu-id="d5c98-131">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal` (C#) or `Friend` (Visual Basic) types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5c98-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5c98-132">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="d5c98-133">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="d5c98-133">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="d5c98-134">Arkadaş derlemeleri</span><span class="sxs-lookup"><span data-stu-id="d5c98-134">Friend assemblies</span></span>](friend.md)
- [<span data-ttu-id="d5c98-135">Nasıl yapılır: imzasız arkadaş derlemeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="d5c98-135">How to: Create unsigned friend assemblies</span></span>](create-unsigned-friend.md)
- [<span data-ttu-id="d5c98-136">-keyfile (C#)</span><span class="sxs-lookup"><span data-stu-id="d5c98-136">-keyfile (C#)</span></span>](../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)
- [<span data-ttu-id="d5c98-137">-keyfile (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5c98-137">-keyfile (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/keyfile.md)
- [<span data-ttu-id="d5c98-138">Sn. exe (tanımlayıcı ad aracı)</span><span class="sxs-lookup"><span data-stu-id="d5c98-138">Sn.exe (Strong Name tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="d5c98-139">Tanımlayıcı adlı derlemeler oluşturma ve kullanma</span><span class="sxs-lookup"><span data-stu-id="d5c98-139">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
- [<span data-ttu-id="d5c98-140">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d5c98-140">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="d5c98-141">Programlama kavramları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5c98-141">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
