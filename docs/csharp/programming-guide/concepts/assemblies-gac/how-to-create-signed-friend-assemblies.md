---
title: 'Nasıl yapılır: Imzalı arkadaş derlemeleri oluşturma (C#)'
ms.date: 07/20/2015
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
ms.openlocfilehash: 7715726a200150b044fb8e97216fa02d0e784838
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595933"
---
# <a name="how-to-create-signed-friend-assemblies-c"></a><span data-ttu-id="5d828-102">Nasıl yapılır: Imzalı arkadaş derlemeleri oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="5d828-102">How to: Create Signed Friend Assemblies (C#)</span></span>
<span data-ttu-id="5d828-103">Bu örnek, friend derlemelerinin tanımlayıcı adlara sahip Derlemelerle nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5d828-103">This example shows how to use friend assemblies with assemblies that have strong names.</span></span> <span data-ttu-id="5d828-104">Her iki derlemenin de tanımlayıcı adlandırılmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5d828-104">Both assemblies must be strong named.</span></span> <span data-ttu-id="5d828-105">Bu örnekteki her iki derleme de aynı anahtarları kullanmasına karşın, iki derleme için farklı anahtarlar kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d828-105">Although both assemblies in this example use the same keys, you could use different keys for two assemblies.</span></span>  
  
### <a name="to-create-a-signed-assembly-and-a-friend-assembly"></a><span data-ttu-id="5d828-106">İmzalı derleme ve arkadaş derleme oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="5d828-106">To create a signed assembly and a friend assembly</span></span>  
  
1. <span data-ttu-id="5d828-107">Bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="5d828-107">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="5d828-108">Anahtar oluşturma ve ortak anahtarını görüntüleme için tanımlayıcı ad aracı ile aşağıdaki komut dizisini kullanın.</span><span class="sxs-lookup"><span data-stu-id="5d828-108">Use the following sequence of commands with the Strong Name tool to generate a keyfile and to display its public key.</span></span> <span data-ttu-id="5d828-109">Daha fazla bilgi için bkz. [sn. exe (tanımlayıcı ad aracı)](../../../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="5d828-109">For more information, see [Sn.exe (Strong Name Tool)](../../../../framework/tools/sn-exe-strong-name-tool.md).</span></span>  
  
    1. <span data-ttu-id="5d828-110">Bu örnek için bir tanımlayıcı ad anahtarı oluşturun ve FriendAssemblies. snk dosyasında depolayın:</span><span class="sxs-lookup"><span data-stu-id="5d828-110">Generate a strong-name key for this example and store it in the file FriendAssemblies.snk:</span></span>  
  
         `sn -k FriendAssemblies.snk`  
  
    2. <span data-ttu-id="5d828-111">Ortak anahtarı FriendAssemblies. snk konumundan ayıklayın ve FriendAssemblies. PublicKey dosyasına yerleştirin:</span><span class="sxs-lookup"><span data-stu-id="5d828-111">Extract the public key from FriendAssemblies.snk and put it into FriendAssemblies.publickey:</span></span>  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3. <span data-ttu-id="5d828-112">FriendAssemblies. publickey dosyasında depolanan ortak anahtarı görüntüle:</span><span class="sxs-lookup"><span data-stu-id="5d828-112">Display the public key stored in the file FriendAssemblies.publickey:</span></span>  
  
         `sn -tp FriendAssemblies.publickey`  
  
3. <span data-ttu-id="5d828-113">Aşağıdaki kodu C# içeren adlı `friend_signed_A` bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5d828-113">Create a C# file named `friend_signed_A` that contains the following code.</span></span> <span data-ttu-id="5d828-114">Kod, friend_signed_B bir <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Friend derlemesi olarak bildirmek için özniteliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="5d828-114">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare friend_signed_B as a friend assembly.</span></span>  
  
     <span data-ttu-id="5d828-115">Tanımlayıcı ad aracı her çalıştığında yeni bir ortak anahtar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5d828-115">The Strong Name tool generates a new public key every time it runs.</span></span> <span data-ttu-id="5d828-116">Bu nedenle, aşağıdaki örnekte gösterildiği gibi aşağıdaki koddaki ortak anahtarı yeni oluşturduğunuz ortak anahtarla değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="5d828-116">Therefore, you must replace the public key in the following code with the public key you just generated, as shown in the following example.</span></span>  
  
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
  
4. <span data-ttu-id="5d828-117">Aşağıdaki komutu kullanarak friend_signed_A derleyin ve imzalayın.</span><span class="sxs-lookup"><span data-stu-id="5d828-117">Compile and sign friend_signed_A by using the following command.</span></span>  
  
    ```csharp  
    csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
    ```  
  
5. <span data-ttu-id="5d828-118">Adlı`friend_signed_B` bir C# dosya oluşturun ve aşağıdaki kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="5d828-118">Create a C# file that is named `friend_signed_B` and contains the following code.</span></span> <span data-ttu-id="5d828-119">Friend_signed_A, bir Friend derlemesi olarak friend_signed_B belirttiğinden, friend_signed_B içindeki kod friend_signed_A 'deki türlere `internal` ve üyelere erişebilir.</span><span class="sxs-lookup"><span data-stu-id="5d828-119">Because friend_signed_A specifies friend_signed_B as a friend assembly, the code in friend_signed_B can access `internal` types and members from friend_signed_A.</span></span> <span data-ttu-id="5d828-120">Dosya aşağıdaki kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="5d828-120">The file contains the following code.</span></span>  
  
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
  
6. <span data-ttu-id="5d828-121">Aşağıdaki komutu kullanarak friend_signed_B derleyin ve imzalayın.</span><span class="sxs-lookup"><span data-stu-id="5d828-121">Compile and sign friend_signed_B by using the following command.</span></span>  
  
    ```csharp  
    csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
    ```  
  
     <span data-ttu-id="5d828-122">Derleyici tarafından oluşturulan derlemenin adı <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliğe geçirilen arkadaş derleme adıyla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="5d828-122">The name of the assembly generated by the compiler must match the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="5d828-123">`/out` Derleyici seçeneğini kullanarak çıkış derlemesinin adını (. exe veya. dll) açıkça belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5d828-123">You must explicitly specify the name of the output assembly (.exe or .dll) by using the `/out` compiler option.</span></span>  <span data-ttu-id="5d828-124">Daha fazla bilgi için bkz. [/OutC# (derleyici seçenekleri)](../../../language-reference/compiler-options/out-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="5d828-124">For more information, see [/out (C# Compiler Options)](../../../language-reference/compiler-options/out-compiler-option.md).</span></span>  
  
7. <span data-ttu-id="5d828-125">Friend_signed_B. exe dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5d828-125">Run the friend_signed_B.exe file.</span></span>  
  
     <span data-ttu-id="5d828-126">Program, "Class1. test" dizesini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="5d828-126">The program prints the string "Class1.Test".</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="5d828-127">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="5d828-127">.NET Framework Security</span></span>  
 <span data-ttu-id="5d828-128"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Özniteliği<xref:System.Security.Permissions.StrongNameIdentityPermission> ve sınıfı arasında benzerlikler vardır.</span><span class="sxs-lookup"><span data-stu-id="5d828-128">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="5d828-129">Temel fark <xref:System.Security.Permissions.StrongNameIdentityPermission> , kodun belirli bir bölümünü çalıştırmak için güvenlik izinleri talep edebilir, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> ancak `internal` öznitelik türlerin ve üyelerin görünürlüğünü denetler.</span><span class="sxs-lookup"><span data-stu-id="5d828-129">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal` types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d828-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d828-130">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="5d828-131">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="5d828-131">Assemblies in .NET</span></span>](../../../../standard/assembly/index.md)
- [<span data-ttu-id="5d828-132">Arkadaş Bütünleştirilmiş Kodları</span><span class="sxs-lookup"><span data-stu-id="5d828-132">Friend Assemblies</span></span>](../../../../standard/assembly/friend-assemblies.md)
- [<span data-ttu-id="5d828-133">Nasıl yapılır: Imzasız arkadaş derlemeleri oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="5d828-133">How to: Create Unsigned Friend Assemblies (C#)</span></span>](./how-to-create-unsigned-friend-assemblies.md)
- [<span data-ttu-id="5d828-134">/keyfile</span><span class="sxs-lookup"><span data-stu-id="5d828-134">/keyfile</span></span>](../../../language-reference/compiler-options/keyfile-compiler-option.md)
- [<span data-ttu-id="5d828-135">Sn.exe (Tanımlayıcı Ad Aracı)</span><span class="sxs-lookup"><span data-stu-id="5d828-135">Sn.exe (Strong Name Tool)</span></span>](../../../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="5d828-136">Kesin Adlandırılmış Bütünleştirilmiş Kodlar Oluşturma ve Kullanma</span><span class="sxs-lookup"><span data-stu-id="5d828-136">Creating and Using Strong-Named Assemblies</span></span>](../../../../framework/app-domains/create-and-use-strong-named-assemblies.md)
- [<span data-ttu-id="5d828-137">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5d828-137">C# Programming Guide</span></span>](../../index.md)
