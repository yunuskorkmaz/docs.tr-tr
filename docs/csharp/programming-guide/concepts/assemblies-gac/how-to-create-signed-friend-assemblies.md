---
title: 'Nasıl yapılır: imzalı arkadaş derlemeleri (C#) oluşturma'
ms.date: 07/20/2015
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
ms.openlocfilehash: 8f310055db6899bf315310efc22b67bca2c4500f
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43874867"
---
# <a name="how-to-create-signed-friend-assemblies-c"></a><span data-ttu-id="9e0d4-102">Nasıl yapılır: imzalı arkadaş derlemeleri (C#) oluşturma</span><span class="sxs-lookup"><span data-stu-id="9e0d4-102">How to: Create Signed Friend Assemblies (C#)</span></span>
<span data-ttu-id="9e0d4-103">Bu örnek, arkadaş derlemeleri tanımlayıcı adlara sahip derlemeler ile kullanma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9e0d4-103">This example shows how to use friend assemblies with assemblies that have strong names.</span></span> <span data-ttu-id="9e0d4-104">İki derleme tanımlayıcı ada gerekir.</span><span class="sxs-lookup"><span data-stu-id="9e0d4-104">Both assemblies must be strong named.</span></span> <span data-ttu-id="9e0d4-105">Bu örnekte iki derleme, aynı anahtarları kullanmak olsa da, anahtarları farklı iki derlemeler için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e0d4-105">Although both assemblies in this example use the same keys, you could use different keys for two assemblies.</span></span>  
  
### <a name="to-create-a-signed-assembly-and-a-friend-assembly"></a><span data-ttu-id="9e0d4-106">İmzalı bir derleme ve arkadaş derleme oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="9e0d4-106">To create a signed assembly and a friend assembly</span></span>  
  
1.  <span data-ttu-id="9e0d4-107">Bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="9e0d4-107">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="9e0d4-108">Aşağıdaki komut dizisi, tanımlayıcı ad aracı ile bir keyfile oluşturur ve ortak anahtarını görüntülemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="9e0d4-108">Use the following sequence of commands with the Strong Name tool to generate a keyfile and to display its public key.</span></span> <span data-ttu-id="9e0d4-109">Daha fazla bilgi için [Sn.exe (tanımlayıcı ad aracı)](../../../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="9e0d4-109">For more information, see [Sn.exe (Strong Name Tool)](../../../../framework/tools/sn-exe-strong-name-tool.md).</span></span>  
  
    1.  <span data-ttu-id="9e0d4-110">Bu örnek için bir tanımlayıcı ad anahtar oluşturun ve FriendAssemblies.snk dosyasında depolar:</span><span class="sxs-lookup"><span data-stu-id="9e0d4-110">Generate a strong-name key for this example and store it in the file FriendAssemblies.snk:</span></span>  
  
         `sn -k FriendAssemblies.snk`  
  
    2.  <span data-ttu-id="9e0d4-111">FriendAssemblies.snk ortak anahtarı ayıklar ve FriendAssemblies.publickey yerleştirin:</span><span class="sxs-lookup"><span data-stu-id="9e0d4-111">Extract the public key from FriendAssemblies.snk and put it into FriendAssemblies.publickey:</span></span>  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3.  <span data-ttu-id="9e0d4-112">FriendAssemblies.publickey dosyasında depolanan ortak anahtarı görüntüler:</span><span class="sxs-lookup"><span data-stu-id="9e0d4-112">Display the public key stored in the file FriendAssemblies.publickey:</span></span>  
  
         `sn -tp FriendAssemblies.publickey`  
  
3.  <span data-ttu-id="9e0d4-113">Adlı bir C# dosyası oluşturma `friend_signed_A` , aşağıdaki kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="9e0d4-113">Create a C# file named `friend_signed_A` that contains the following code.</span></span> <span data-ttu-id="9e0d4-114">Kod <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> friend_signed_B arkadaş derleme olarak bildirmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="9e0d4-114">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare friend_signed_B as a friend assembly.</span></span>  
  
     <span data-ttu-id="9e0d4-115">Tanımlayıcı ad aracı, her çalıştığında yeni bir ortak anahtar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9e0d4-115">The Strong Name tool generates a new public key every time it runs.</span></span> <span data-ttu-id="9e0d4-116">Bu nedenle, aşağıdaki örnekte gösterildiği gibi ürettiğiniz, ortak anahtar ile ortak anahtar aşağıdaki kodu değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="9e0d4-116">Therefore, you must replace the public key in the following code with the public key you just generated, as shown in the following example.</span></span>  
  
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
  
4.  <span data-ttu-id="9e0d4-117">Derleme ve aşağıdaki komutu kullanarak friend_signed_A imzalayın.</span><span class="sxs-lookup"><span data-stu-id="9e0d4-117">Compile and sign friend_signed_A by using the following command.</span></span>  
  
    ```csharp  
    csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
    ```  
  
5.  <span data-ttu-id="9e0d4-118">Adlı bir C# dosyası oluşturma `friend_signed_B` ve aşağıdaki kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="9e0d4-118">Create a C# file that is named `friend_signed_B` and contains the following code.</span></span> <span data-ttu-id="9e0d4-119">Friend_signed_A friend_signed_B arkadaş derleme olarak belirttiğinden friend_signed_B kodda erişip `internal` türleri ve üyeleri friend_signed_A.</span><span class="sxs-lookup"><span data-stu-id="9e0d4-119">Because friend_signed_A specifies friend_signed_B as a friend assembly, the code in friend_signed_B can access `internal` types and members from friend_signed_A.</span></span> <span data-ttu-id="9e0d4-120">Dosya, aşağıdaki kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="9e0d4-120">The file contains the following code.</span></span>  
  
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
  
6.  <span data-ttu-id="9e0d4-121">Derleme ve aşağıdaki komutu kullanarak friend_signed_B imzalayın.</span><span class="sxs-lookup"><span data-stu-id="9e0d4-121">Compile and sign friend_signed_B by using the following command.</span></span>  
  
    ```csharp  
    csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
    ```  
  
     <span data-ttu-id="9e0d4-122">Geçirilen friend derleme adı derleyici tarafından oluşturulan bütünleştirilmiş kodun adı eşleşmelidir <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="9e0d4-122">The name of the assembly generated by the compiler must match the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="9e0d4-123">Çıktı derlemesine (.exe veya .dll) adını kullanarak açıkça belirtmeniz gerekir `/out` derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="9e0d4-123">You must explicitly specify the name of the output assembly (.exe or .dll) by using the `/out` compiler option.</span></span>  <span data-ttu-id="9e0d4-124">Daha fazla bilgi için [/out (C# Derleyici Seçenekleri)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="9e0d4-124">For more information, see [/out (C# Compiler Options)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md).</span></span>  
  
7.  <span data-ttu-id="9e0d4-125">Friend_signed_B.exe dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9e0d4-125">Run the friend_signed_B.exe file.</span></span>  
  
     <span data-ttu-id="9e0d4-126">Program "Class1.Test" dize yazdırır.</span><span class="sxs-lookup"><span data-stu-id="9e0d4-126">The program prints the string "Class1.Test".</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="9e0d4-127">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="9e0d4-127">.NET Framework Security</span></span>  
 <span data-ttu-id="9e0d4-128">Arasındaki benzerlikler vardır <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği ve <xref:System.Security.Permissions.StrongNameIdentityPermission> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9e0d4-128">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="9e0d4-129">Ana fark <xref:System.Security.Permissions.StrongNameIdentityPermission> ise kod, belirli bir bölümünü çalıştırmak için güvenlik izinleri talep <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği denetimleri görünürlüğünü `internal` türler ve üyeler.</span><span class="sxs-lookup"><span data-stu-id="9e0d4-129">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal` types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e0d4-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9e0d4-130">See Also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
- [<span data-ttu-id="9e0d4-131">Derlemeler ve Genel Derleme Önbelleği (C#)</span><span class="sxs-lookup"><span data-stu-id="9e0d4-131">Assemblies and the Global Assembly Cache (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
- [<span data-ttu-id="9e0d4-132">Arkadaş derlemeler (C#)</span><span class="sxs-lookup"><span data-stu-id="9e0d4-132">Friend Assemblies (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
- [<span data-ttu-id="9e0d4-133">Nasıl yapılır: İmzasız arkadaş derlemeleri (C#) oluşturma</span><span class="sxs-lookup"><span data-stu-id="9e0d4-133">How to: Create Unsigned Friend Assemblies (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)  
- [<span data-ttu-id="9e0d4-134">/keyfile</span><span class="sxs-lookup"><span data-stu-id="9e0d4-134">/keyfile</span></span>](../../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)  
- [<span data-ttu-id="9e0d4-135">Sn.exe (Tanımlayıcı Ad Aracı)</span><span class="sxs-lookup"><span data-stu-id="9e0d4-135">Sn.exe (Strong Name Tool)</span></span>](../../../../framework/tools/sn-exe-strong-name-tool.md)  
- [<span data-ttu-id="9e0d4-136">Kesin Adlandırılmış Bütünleştirilmiş Kodlar Oluşturma ve Kullanma</span><span class="sxs-lookup"><span data-stu-id="9e0d4-136">Creating and Using Strong-Named Assemblies</span></span>](../../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
- [<span data-ttu-id="9e0d4-137">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9e0d4-137">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
