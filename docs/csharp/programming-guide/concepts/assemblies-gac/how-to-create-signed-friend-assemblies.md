---
title: 'Nasıl yapılır: imzalı arkadaş derlemeleri (C#) oluşturma'
ms.date: 07/20/2015
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
ms.openlocfilehash: 34243a65f57f41c358439baac82a1ce169233259
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340664"
---
# <a name="how-to-create-signed-friend-assemblies-c"></a><span data-ttu-id="2d712-102">Nasıl yapılır: imzalı arkadaş derlemeleri (C#) oluşturma</span><span class="sxs-lookup"><span data-stu-id="2d712-102">How to: Create Signed Friend Assemblies (C#)</span></span>
<span data-ttu-id="2d712-103">Bu örnek güçlü adlara sahip Derlemelerle arkadaş derlemeleri kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="2d712-103">This example shows how to use friend assemblies with assemblies that have strong names.</span></span> <span data-ttu-id="2d712-104">Her iki derlemeleri strong adlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2d712-104">Both assemblies must be strong named.</span></span> <span data-ttu-id="2d712-105">Bu örnekte her iki derlemeleri aynı anahtarlar kullansa da, anahtarları farklı iki derlemeler için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2d712-105">Although both assemblies in this example use the same keys, you could use different keys for two assemblies.</span></span>  
  
### <a name="to-create-a-signed-assembly-and-a-friend-assembly"></a><span data-ttu-id="2d712-106">İmzalı bir derleme ve bir derlemeyi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="2d712-106">To create a signed assembly and a friend assembly</span></span>  
  
1.  <span data-ttu-id="2d712-107">Bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="2d712-107">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="2d712-108">Aşağıdaki komut dizisi tanımlayıcı ad aracı ile bir keyfile oluşturmak ve ortak anahtar görüntülemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="2d712-108">Use the following sequence of commands with the Strong Name tool to generate a keyfile and to display its public key.</span></span> <span data-ttu-id="2d712-109">Daha fazla bilgi için bkz: [Sn.exe (tanımlayıcı ad aracı)](https://msdn.microsoft.com/library/k5b5tt23).</span><span class="sxs-lookup"><span data-stu-id="2d712-109">For more information, see [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23).</span></span>  
  
    1.  <span data-ttu-id="2d712-110">Bu örnek için bir tanımlayıcı ad anahtar oluştur ve FriendAssemblies.snk dosyada saklayabilir:</span><span class="sxs-lookup"><span data-stu-id="2d712-110">Generate a strong-name key for this example and store it in the file FriendAssemblies.snk:</span></span>  
  
         `sn -k FriendAssemblies.snk`  
  
    2.  <span data-ttu-id="2d712-111">Ortak anahtar FriendAssemblies.snk ayıklayın ve FriendAssemblies.publickey koyun:</span><span class="sxs-lookup"><span data-stu-id="2d712-111">Extract the public key from FriendAssemblies.snk and put it into FriendAssemblies.publickey:</span></span>  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3.  <span data-ttu-id="2d712-112">FriendAssemblies.publickey dosyasında depolanan genel anahtarını görüntüleyin:</span><span class="sxs-lookup"><span data-stu-id="2d712-112">Display the public key stored in the file FriendAssemblies.publickey:</span></span>  
  
         `sn -tp FriendAssemblies.publickey`  
  
3.  <span data-ttu-id="2d712-113">Adlı bir C# dosyası oluşturun `friend_signed_A` aşağıdaki kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="2d712-113">Create a C# file named `friend_signed_A` that contains the following code.</span></span> <span data-ttu-id="2d712-114">Kod kullanan <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> friend_signed_B Arkadaş derlemesi olarak bildirmek için öznitelik.</span><span class="sxs-lookup"><span data-stu-id="2d712-114">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare friend_signed_B as a friend assembly.</span></span>  
  
     <span data-ttu-id="2d712-115">Tanımlayıcı ad aracı her çalıştığında yeni bir ortak anahtar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2d712-115">The Strong Name tool generates a new public key every time it runs.</span></span> <span data-ttu-id="2d712-116">Bu nedenle, aşağıdaki örnekte gösterildiği gibi az önce oluşturulan, ortak anahtar ile aşağıdaki kodu ortak anahtar değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="2d712-116">Therefore, you must replace the public key in the following code with the public key you just generated, as shown in the following example.</span></span>  
  
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
  
4.  <span data-ttu-id="2d712-117">Derleme ve friend_signed_A aşağıdaki komutu kullanarak oturum açın.</span><span class="sxs-lookup"><span data-stu-id="2d712-117">Compile and sign friend_signed_A by using the following command.</span></span>  
  
    ```csharp  
    csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
    ```  
  
5.  <span data-ttu-id="2d712-118">Adlı bir C# dosyası oluşturma `friend_signed_B` ve aşağıdaki kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="2d712-118">Create a C# file that is named `friend_signed_B` and contains the following code.</span></span> <span data-ttu-id="2d712-119">Friend_signed_A friend_signed_B arkadaş derleme olarak belirttiğinden friend_signed_B kodda erişebilirsiniz `internal` türleri ve friend_signed_A üyelerinden.</span><span class="sxs-lookup"><span data-stu-id="2d712-119">Because friend_signed_A specifies friend_signed_B as a friend assembly, the code in friend_signed_B can access `internal` types and members from friend_signed_A.</span></span> <span data-ttu-id="2d712-120">Dosya şu kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="2d712-120">The file contains the following code.</span></span>  
  
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
  
6.  <span data-ttu-id="2d712-121">Derleme ve friend_signed_B aşağıdaki komutu kullanarak oturum açın.</span><span class="sxs-lookup"><span data-stu-id="2d712-121">Compile and sign friend_signed_B by using the following command.</span></span>  
  
    ```csharp  
    csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
    ```  
  
     <span data-ttu-id="2d712-122">Derleyici tarafından üretilen derlemenin adını geçirilen arkadaş derleme adı eşleşmelidir <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="2d712-122">The name of the assembly generated by the compiler must match the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="2d712-123">Çıkış derlemesi (.exe veya .dll) adını kullanarak açıkça belirtmeniz gerekir `/out` derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="2d712-123">You must explicitly specify the name of the output assembly (.exe or .dll) by using the `/out` compiler option.</span></span>  <span data-ttu-id="2d712-124">Daha fazla bilgi için bkz: [/out (C# Derleyici Seçenekleri)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="2d712-124">For more information, see [/out (C# Compiler Options)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md).</span></span>  
  
7.  <span data-ttu-id="2d712-125">Friend_signed_B.exe dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2d712-125">Run the friend_signed_B.exe file.</span></span>  
  
     <span data-ttu-id="2d712-126">Program "Class1.Test" dizesi yazdırır.</span><span class="sxs-lookup"><span data-stu-id="2d712-126">The program prints the string "Class1.Test".</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="2d712-127">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="2d712-127">.NET Framework Security</span></span>  
 <span data-ttu-id="2d712-128">Arasındaki benzerlikler vardır <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği ve <xref:System.Security.Permissions.StrongNameIdentityPermission> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2d712-128">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="2d712-129">Ana fark <xref:System.Security.Permissions.StrongNameIdentityPermission> kodu, belirli bir bölüme çalıştırmak için güvenlik izinleri ancak talep <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği denetler görünürlüğünü `internal` türleri ve üyeleri.</span><span class="sxs-lookup"><span data-stu-id="2d712-129">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal` types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d712-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2d712-130">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [<span data-ttu-id="2d712-131">Derlemeler ve Genel Derleme Önbelleği (C#)</span><span class="sxs-lookup"><span data-stu-id="2d712-131">Assemblies and the Global Assembly Cache (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="2d712-132">Arkadaş derlemeler (C#)</span><span class="sxs-lookup"><span data-stu-id="2d712-132">Friend Assemblies (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 [<span data-ttu-id="2d712-133">Nasıl yapılır: İmzasız arkadaş derlemeleri (C#) oluşturma</span><span class="sxs-lookup"><span data-stu-id="2d712-133">How to: Create Unsigned Friend Assemblies (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)  
 [<span data-ttu-id="2d712-134">/keyfile</span><span class="sxs-lookup"><span data-stu-id="2d712-134">/keyfile</span></span>](../../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [<span data-ttu-id="2d712-135">Sn.exe (Tanımlayıcı Ad Aracı)</span><span class="sxs-lookup"><span data-stu-id="2d712-135">Sn.exe (Strong Name Tool)</span></span>](https://msdn.microsoft.com/library/k5b5tt23)  
 [<span data-ttu-id="2d712-136">Kesin Adlandırılmış Bütünleştirilmiş Kodlar Oluşturma ve Kullanma</span><span class="sxs-lookup"><span data-stu-id="2d712-136">Creating and Using Strong-Named Assemblies</span></span>](../../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 [<span data-ttu-id="2d712-137">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2d712-137">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
